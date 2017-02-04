FROM alpine:latest
MAINTAINER Hidetoshi Imai <hidepin@gmail.com>

RUN apk add --update nodejs ansible sshpass tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    echo "Asia/Tokyo" >  /etc/timezone && \
    npm install -g npm && \
    npm install -g yo generator-hubot && \
    adduser hubot -D

ARG MATTERMOST_HUBOT_USERNAME=matterbot
ENV HOME=/home/hubot \
    MATTERMOST_HUBOT_USERNAME=${MATTERMOST_HUBOT_USERNAME}
USER hubot
WORKDIR /home/hubot

RUN mkdir matterbot && \
    cd matterbot && \
    yo hubot --adapter mattermost --name ${MATTERMOST_HUBOT_USERNAME} --owner ${MATTERMOST_HUBOT_USERNAME} --description matterbot && \
    rm hubot-scripts.json && \
    sed -i.org '/hubot-heroku-keepalive/d' external-scripts.json

WORKDIR /home/hubot/matterbot
CMD ["-a", "mattermost"]
ENTRYPOINT ["./bin/hubot"]

EXPOSE 8080
