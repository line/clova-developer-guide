# Custom ExtensionとLINEを連携する

ユーザーがCustom Extensionで発話した内容を元に、LINEのボットからメッセージを送ったり、LINEのボットで設定した情報を元にCustom Extensionでの発話内容を変更することができます。例えば、住所など、音声で全てを入力させることが困難な文字列をLINEボットで設定し、その内容を元にスキルの挙動を変えることができます。

このドキュメントでは、次の内容について説明します。
* [利用条件](#Conditions)
* [利用方法](#Settings)

## 利用条件 {#Conditions}

Custom ExtensionとLINEの連携を実施するには、以下の条件を満たしている必要があります。

**1. Messaging APIを利用していること**  

* 公式アカウント（2018年12月からの新プラン）の場合は、**応答モード** が"Bot"で、**Webhook** の利用が"オン"になっていること
* 旧プランの場合は、API型公式アカウントであること

  [LINE Official Account Manager](https://manager.line.biz/)で当該のアカウントを選択し、設定 > **応答設定** の画面で、以下のように設定されているかを確認します。
  - **応答モード** → Bot
  - **応答メッセージ** → オフ
  - **Webhook** → オン  
  ![](/CEK/Assets/Images/CEK_Messaging_API_OA_Manager.png)

* LINE@の場合は、Webhookを用いてメッセージのやり取りを実現していること

  [LINE@マネージャー](https://admin-official.line.me/)の アカウント設定 > **Messaging API設定** の画面で、以下のように設定されているかを確認します。  
  - **Webhookを送信** → 利用する
  - **自動応答メッセージ** → 利用しない  
  ![](/CEK/Assets/Images/CEK_Messaging_API_LineManager.png)

  設定方法については、こちらのドキュメントもご確認ください。  
  [LINE Developers ドキュメント > Messaging API > ボットを作成する](https://developers.line.biz/ja/docs/messaging-api/building-bot/)

**2. ユーザーがボットを友だち追加していること**

  ユーザーがスキルを利用していても、LINE上で友だちになっていないボットからのメッセージを受け取ることはできません。

**3. 同じサービス提供者から提供するCustom Extensionとボットであること**

  Custom Extensionとボットのサービス提供者は同じでなければなりません。例えば、ある企業が複数のサービスを運営している場合、別々のサービスのスキルとボットのユーザーを紐付けをすることはできません。

  * 正しい例："ピザ宅配スキル"と"ピザ宅配ボット"を連携する
  * 間違った例："ピザ宅配スキル"と"旅行代理店ボット"を連携する

  Custom Extensionとボットの不適切な紐付けが発見された場合は、当該のCustom Extensionを停止します。あらかじめご了承ください。

**4. ユーザーが当該のボットからメッセージが来ると理解できること**

  例えば、「旅行代理店ボットからLINEを送信しました」とユーザーにメッセージの送信元となるボットの名称を伝えて、ユーザーがスキルとの会話によってメッセージがきたということが理解できるようなフローにしてください。万が一、ユーザーが意図しないタイミングや、意図していないボットからのメッセージが送信される場合には、当該のCustom Extensionを停止します。あらかじめご了承ください。

## 利用方法 {#Settings}

まず、LINE Developersコンソールで、同一のプロバイダー配下にボットのチャネル（Messaging APIチャネル）とCustom Extensionのチャネル（Clovaスキルチャネル）を作成してください。異なるプロバイダー配下に作成されている場合には連携することができません。
同一のプロバイダー配下にチャネルを発行すると、Custom ExtensionのuserIdと、ボットのMessaging APIのuserIdに同じIDが渡ってきます。

そのため、例えばCustom Extensionで受け取った発話を元に、LINEのボットからメッセージを送信したい場合には以下2つのAPIを利用してください。
* **Custom Extensionのリクエスト**  

  [CEK APIリファレンス > Custom Extensionメッセージ > リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)  
  Message fieldsの`session.user.userId`​がユーザー識別子です。

* **Messaging APIのPush API**  

  [LINE Developers ドキュメント > Messaging API > APIリファレンス > 共通プロパティ](https://developers.line.biz/ja/reference/messaging-api/#common-properties)  
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
[LINE Developers ドキュメント > Messaging API > APIリファレンス > プッシュメッセージを送る](https://developers.line.biz/ja/reference/messaging-api/#send-push-message)
​
