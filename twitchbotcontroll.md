needed:
indipendant bots w8 for order. get order and respond. get signal to send message and stop watching¨
sendBotId(username)
watchUser(url)
gotMessage(username)
sendChat(msg)
stopWatching()
heartbeat(username)

server: 
addActiveBot
removeActiveBot
GetUsername
sendChat
heartbeat
arr of botjson

alt 1 
websocket
get message and send order and payload
either uniq per bot or botmanager
alt 2 
pub sub
alt 3
pool database/api
lock table to avoid double write/messanging
