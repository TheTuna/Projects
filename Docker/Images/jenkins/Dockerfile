FROM jenkins/jenkins:lts-jdk17
ENV REFRESHED_AT 2025-02-01
USER root
RUN apt update; apt install -y sudo
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
RUN mkdir -p /certs/client
RUN chown -R jenkins:jenkins /certs/client
USER jenkins
COPY --chown=jenkins:jenkins certs/* /certs/client/
RUN chmod 400 /certs/client/*
RUN jenkins-plugin-cli --plugins "junit git git-client ssh-slaves greenballs \
chucknorris ws-cleanup"
