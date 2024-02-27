FROM alpine:latest
RUN apk update && apk upgrade
RUN mkdir -p /opt/prometheus/database
WORKDIR /opt/prometheus
RUN wget https://github.com/prometheus/prometheus/releases/download/v2.47.2/prometheus-2.47.2.linux-armv7.tar.gz
RUN tar xzvf prometheus-2.47.2.linux-armv7.tar.gz
RUN mv /opt/prometheus/prometheus-2.47.2.linux-armv7/promtool /usr/sbin
RUN mv /opt/prometheus/prometheus-2.47.2.linux-armv7/prometheus /usr/sbin
RUN mv /opt/prometheus/prometheus-2.47.2.linux-armv7/consoles /opt/prometheus
RUN mv /opt/prometheus/prometheus-2.47.2.linux-armv7/console_libraries /opt/prometheus
RUN rm prometheus-2.47.2.linux-armv7.tar.gz
EXPOSE 9090
#ADD prometheus.yml /etc/prometheus/
ENTRYPOINT [ "/usr/sbin/prometheus" ]
CMD [ "--config.file=/etc/prometheus/prometheus.yml","--storage.tsdb.path=/opt/prometheus/database", "--storage.tsdb.retention.time=10d","--web.enable-lifecycle", \
"--web.console.libraries=/opt/prometheus/console_libraries", "--web.console.templates=opt/prometheus/consoles"]