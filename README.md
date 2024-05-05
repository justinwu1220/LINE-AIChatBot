# LINE-AIChatBot
基於JAVA Spring Boot 、 LINE Developer Messaging API 、 OpenAI API 實現的 Line AI 聊天機器人

此聊天機器人為基礎版本，進階版請前往 : <https://github.com/justinwu1220/LINE-AIChatBot-advanced>

## 技術
- LineBot :
  - 使用LINE Developer建立機器人
- JAVA :
  - Spring Boot: MVC架構實作機器人後端程式
- 第三方 api :
  - 串接OpenAI API 實現ai回覆訊息
 
## 功能
輸入任意文字訊息，可得到ai回覆

<img src="https://github.com/justinwu1220/LINE-AIChatBot/blob/main/img/S__4399116.jpg" width="300"> <img src="https://github.com/justinwu1220/LINE-AIChatBot/blob/main/img/S__4399119.jpg" width="300">

## 如何使用
#### 建立帳號
* 進入: <https://manager.line.biz> 建立chatbot的帳號
* 按照步驟建立channel
* 記下Basic settings中的Channel secret，以及Messaging API中的Channel access token
* 到Auto-reply messages中，disable自動回應訊息，啟動Webhook
  
####  OpenAI API
* 進入: <https://openai.com/index/openai-api>
* 創建帳號並取得openAi api key
  
#### Git clone 程式
在LINE-AIChatBot/src/main/resources/application.properties中
* 新增line.bot.channel-token和line.bot.channel-secret
* 新增openAi.api.key
```properties
spring.application.name=LINE-AIChatBot

server.port=8080

line.bot.channel-token=yourToken
line.bot.channel-secret=yourSecret
line.bot.handler.enabled=true
line.bot.handler.path=/callback

openAi.api.key=yourApiKey
openAi.api.url=https://api.openai.com/v1/chat/completions

```
* 執行SpringBoot程式

#### ngrok
* 使用ngrok建立一個臨時的https網址(接收Line Bot Webhook 需要https協定)
* 下載ngrok，並解壓縮
* 打開檔案，並輸入指令
```
ngrok http 8080
```
* 把ngrok中拿到的網址後面加上/callback
* 將網址貼在Messaging API底下的Webhook URL，同時開啟Use webhook
* 按下Verify，確定是否出現Success(需先執行SpringBoot程式)

#### 運行
* 確定出現Success
* 加入Line bot好友
* 傳送訊息查看是否得到回覆
