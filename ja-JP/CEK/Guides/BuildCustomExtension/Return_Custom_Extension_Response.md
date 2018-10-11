## Custom Extensionレスポンスを返す {#ReturnCustomExtensionResponse}
[リクエストメッセージを処理](#HandleCustomExtensionRequest)すると、CEKに[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返す必要があります(HTTPレスポンス)。リクエストメッセージのタイプによって異なる内容を返すこともありますが、レスポンスメッセージの構造に大差はありません。以下は、LaunchRequestタイプのリクエスト(「ピザボットを起動して」というユーザーリクエスト)を処理した後に返したレスポンスメッセージです。

{% raw %}
```json
{
  "version": "1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ja",
          "value": "こんにちは。ピザボットです。どういったご用件ですか"
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": false
  }
}
```
{% endraw %}

各フィールドは、次のような意味を持ちます。

* `version`：使用しているCustom Extensionメッセージフォーマットのバージョンです。現在のバージョンはv1.0です。
* `response.outputSpeech`：ユーザーが日本語で「こんにちは。ピザボットです。どういったご用件ですか」の文章を話すように設定します。
* `response.card`：クライアントの画面に表示するデータがありません。コンテンツテンプレート形式のデータで、クライアントの画面に表示するコンテンツをこのフィールドで渡すことができます。
* `response.shouldEndSession`：セッションを終了せず、引き続きユーザーの入力を受け付けるかを管理します。このフィールドの値がtrueの場合、[`SessionEndedRequest`](#HandleSessionEndedRequest)リクエストを受け取る前に、Extensionからセッションを終了できます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>
    <ul>
      <li><code>response.directives</code>フィールドはExtensionがCEKに渡すディレクティブです。<code>response.directives</code>フィールドで使用するディレクティブは、現在、主にオーディオコンテンツを提供するために使用されます。</li>
      <li>Extensionサーバーのレスポンスは8秒以内に返却するよう実装してください。時間内にCEKにレスポンスメッセージが渡されない場合は対話が終了します。対話の終了後に返却されたレスポンスは実行されません。</li>
    </ul>
  </p>
</div>

次のように、場合によって複数の文章を出力するようにレスポンスメッセージを作成することができます。あるいは、インターネット上のオーディオファイルを再生するようにレスポンスメッセージを作成することもできます。

{% raw %}
```json
{
  "version": "1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SpeechList",
      "values": [
        {
          "type": "PlainText",
          "lang": "ja",
          "value": "歌を歌ってみます。"
        },
        {
          "type": "URL",
          "lang": "" ,
          "value": "https://example.com/song.mp3"
        }
      ]
    },
    "card": {},
    "directives": [],
    "shouldEndSession": true
  }
}
```
{% endraw %}

各`response.outputSpeech`フィールドの説明は、次のとおりです。

* `response.outputSpeech.type`：複文タイプ(SpeechList)の音声情報です。
* `response.outputSpeech.values[0]`：テキスト形式の音声情報です。日本語で「歌を歌ってみます」と発話するように設定されています。
* `response.outputSpeech.values[1]`：URL形式の音声情報です。`value`フィールドに入力されたURLのファイルを再生するように設定されています。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>単文や複文タイプの音声情報の他に、画面を持たないデバイスのような詳しい内容をGUIで表現できないクライアントデバイスのために、複合タイプ(SpeechSet)の音声情報もサポートしています。詳細については、Custom Extensionメッセージの<a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">レスポンスメッセージ</a>を参照してください。</p>
</div>

音声出力だけでなく、クライアントデバイスの画面やクライアントアプリの画面にデータを出力する必要がある場合、次のように`response.card`フィールドにコンテンツテンプレートに合わせて表示するコンテンツを設定します。

{% raw %}
```json
{
  "version": "1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ja",
          "value": "ブラウンの画像です"
      }
    },
    "card": {
      "type": "ImageText",
      "imageUrl": {
        "type": "url",
        "value": ""
      },
      "mainText": {
        "type": "string",
        "value": "LINE Friendsのブラウンです"
      },
      "referenceText": {
        "type": "string",
        "value": "Clova検索結果"
      },
      "referenceUrl": {
        "type": "url",
        "value": "DUMMY_REFERENCE_URL"
      },
      "subTextList": [
        {
          "type": "string",
          "value": "LINE Friends"
        }
      ],
      "thumbImageType": {
        "type": "string",
        "value": "キャラクター"
      },
      "thumbImageUrl": {
        "type": "url",
        "value": "DUMMY_IMAGE_URL"
      }
    },
    "directives": [],
    "shouldEndSession": true
  }
}
```
{% endraw %}

<div class="danger">
  <p><strong>注意</strong></p>
  <p>日本では現在、cardをサポートしておりません。</p>
</div>
