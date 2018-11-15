# Custom ExtensionとLINEを連携する

ユーザーがCustom Extensionで発話した内容を元に、LINEのボットからメッセージを送ったり、LINEのボットで設定した情報を元にCustom Extensionでの発話内容を変更することができます。例えば、住所など、音声で全てを入力させることが困難な文字列をLINEボットで設定し、その内容を元にスキルの挙動を変えることができます。

このドキュメントでは、次の内容について説明します。
* [利用条件](#Conditions)
* [利用方法](#Settings)

## 利用条件 {#Conditions}

Custom ExtensionとLINEの連携を実施するには、以下の条件を満たしている必要があります。

1. Messaging APIを利用していること  
  * 公式アカウントの場合は、API型であること
  * LINE@の場合は、webhookを用いてメッセージのやり取りを実現していること

  LINE@の場合は、[LINE@マネージャー](https://admin-official.line.me/)の アカウント設定 > **Messaging API設定** の画面で、以下のように設定されているかを確認します。  
  - **webhookを送信** → 利用する
  - **自動応答メッセージ** → 利用しない  
  ![](/CEK/Resources/Images/CEK_Messaging_API_LineManager.png)

  設定方法については、こちらのドキュメントもご確認ください。  
  [LINE Developers ドキュメント > Messaging API > ボットを作成する](https://developers.line.biz/ja/docs/messaging-api/building-bot/)

2. ユーザーがボットを友だち追加していること  
  ユーザーがスキルを利用していても、LINE上で友達になっていないボットからのメッセージを受け取ることはできません。

3. 同じサービス提供者から提供するCustom Extensionとボットであること  
  例えば、ある会社がピザ宅配サービスと旅行代理店サービスを提供している場合、ピザ宅配スキルと旅行代理店ボットでユーザーの紐付けをすることはできません。Custom Extensionとボットの不適切な紐付けが発見された場合は、当該のCustom Extensionを停止します。あらかじめご了承ください。

4. ユーザーが該当のボットからメッセージが来ると理解できること  
  例えば、"旅行代理店ボットからLINEを送信します。よろしいですか？"とユーザーにボットの名称を伝えて、ユーザーがスキルとの会話によってメッセージがきたということが理解できるようなフローにしてください。万が一、ユーザーが意図しないタイミングや、意図していないボットからのメッセージが送信される場合には、該当のCustom Extensionを停止します。予めご了承ください。

## 利用方法 {#Settings}

まず、ボットのチャネルとスキルのチャネルを同一のプロバイダー配下に作成してください。異なるプロバイダー配下に作成されている場合には連携することができません。
同一のプロバイダー配下にチャネルを発行すると、Custom ExtensionのuserIdと、ボットのMessaging APIのuserIdに同じIDが渡ってきます。

そのため、例えばCustom Extensionで受け取った発話を元に、LINEのボットからメッセージを送信したい場合には以下2つのAPIを利用してください。
* Custom Extensionのリクエスト  

  [CEK APIリファレンス > Custom Extensionメッセージ > リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)  
  Message fieldsの`session.user.userId`​がユーザー識別子です。

* Messaging APIのPush API  

  [LINE Developers ドキュメント > Messaging API > APIリファレンス > 共通プロパティ](https://developers.line.biz/ja/docs/messaging-api/reference/#anchor-ff6d9a0f9685bb1dfdde749b9044d243cadd542e)  
  送信元ユーザーの`userId`がユーザー識別子です。​Custom Extensionの`session.user.userId`​をご利用ください。  

つまり、以下のようなコードになります。
```js
const line = require('@line/bot-sdk');

const client = new line.Client({
  channelAccessToken: '<channel access token>'
});

const message = {
  type: 'text',
  text: 'Hello World!'
};

client.pushMessage(request.​session.user.userId​​​, message)
  .then(() => {
    ...
  })
  .catch((err) => {
    // error handling
  });​
```
Messaging APIのプッシュメッセージの詳細な仕様については、こちらをご確認ください。  
[LINE Developers ドキュメント > Messaging API > APIリファレンス > プッシュメッセージを送る](https://developers.line.biz/ja/docs/messaging-api/reference/#anchor-0c00cb0f42b970892f7c3382f92620dca5a110fc)
​
