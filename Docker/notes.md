## Docker Images Notes
####  Alpine
1. "rc-update: not found" appears on "docker build ." at "RUN rc-update"
    <details>
       <summary>Cause</summary>
        Image alpine:latest does have rc installed by default.
    </details>
    
    <details>
    <summary>Solution</summary>
        Install openrc by running the following command: '''apk add openrc'''
    </details>


