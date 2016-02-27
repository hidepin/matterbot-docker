# matterbot-dockerfile

### cmd

```
docker run -e MATTERMOST_ENDPOINT='/hubot/incoming' \
-e MATTERMOST_INCOME_URL='http://xxx.xxx.xxx/hooks/xxxxxxxxxxxxxxxxxxxxx' \
-e MATTERMOST_TOKEN='xxxxxxxxxxxxxxxxxxxx' \
-e MATTERMOST_HUBOT_USERNAME='matterbot' \
--name "matterbot" \
-p 8080:8080 \
 -v /opt/matterbot/scripts:/home/hubot/matterbot/scripts \
 -d hidepin/matterbot:1.0
```