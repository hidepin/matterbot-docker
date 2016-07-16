FROM alpine:3.3
MAINTAINER Hidetoshi Imai <hidepin@gmail.com>

RUN apk add --update nodejs ansible sshpass tzdata \
&& cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
&& echo "Asia/Tokyo" >  /etc/timezone \
&& npm install -g npm \
&& npm install -g yo generator-hubot \
&& adduser hubot -D

ENV HOME /home/hubot
USER hubot
WORKDIR /home/hubot

RUN mkdir matterbot \
&& cd matterbot \
&& yo hubot --adapter mattermost --name matterbot --owner matterbot --description mattermost

WORKDIR /home/hubot/matterbot
CMD ["-a", "mattermost"]
ENTRYPOINT ["./bin/hubot"]

EXPOSE 8080
