## マルチターン対話をする {#DoMultiturnDialog}

Custom Extensionがサービスを提供したり、または動作するために必要な情報が、CEKから渡されたユーザーのリクエスト([`IntentRequest`](/CEK/Guides/Build_Custom_Extension.md#HandleIntentRequest))にすべて含まれていないことがあります。また、シングルターンの対話では、1回の発話でユーザーのリクエストを受け付けることが難しい場合もあります。その場合、Custom Extensionはユーザーから足りない情報を聞き出すために、マルチターンの対話を行うことができます。

例えば、ユーザーが「ペパロニピザを頼んで」と発話したと仮定します。それを受け、CEKは次のようなリクエストメッセージを送信します。

{% raw %}
```json
{
  "version": "1.0",
  "session": {
    "new": false,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    ...
  },
  "request": {
    "type": "IntentRequest",
    "intent": {
      "name": "OrderPizza",
      "slots": {
        "pizzaType": {
          "name": "pizzaType",
          "value": "ペパロニ"
        }
      }
    }
  }
}
```
{% endraw %}

Custom Extensionがピザの種類だけでなく、注文する数量に関する情報を必要とすることがあります。その際、[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)の`response.shouldEndSession`フィールドを`false`に設定すると、マルチターン対話で足りない情報を確認することができます。また、ユーザーが先に入力した情報を`sessionAttributes`フィールドにキー(key)-値(value)の形で保存することもできます。

以下のようにレスポンスを返すことで、ユーザーがすでにリクエストした`intent`フィールドと`pizzaType`の情報を保存するようにClovaにリクエストすることができます。また、ユーザーに数量に関する追加の情報を求めることができます。

{% raw %}
```json
{
  "version": "1.0",
  "sessionAttributes": {
    "intent": "OrderPizza",
    "pizzaType": "ペパロニ"
  },
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ja",
          "value": "何枚注文しますか?"
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": false
  }
}
```
{% endraw %}

ユーザーの応答サンプルリクエストは次のようになります。マルチターン対話において追加で送信されたメッセージの`session.new`は`false`になり、前のメッセージと同じ`session.sessionId`値を持ちます。
また、解析した結果と共に、前回のレスポンスに含まれていた`sessionAttributes`オブジェクトの情報を[リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)の`session.sessionAttributes`フィールドに含めて再送信します。Custom Extensionはこれらの受信した追加の情報を使用して次の動作を行うことができます。

{% raw %}
```json
{
  "version": "1.0",
  "session": {
    "new": false,
    "sessionAttributes": {
        "intent": "OrderPizza",
        "pizzaType": "ペパロニ"
    },
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    ...
  },
  "request": {
    "type": "IntentRequest",
    "intent": {
      "name": "AddInfo",
      "slots": {
        "pizzaAmount": {
          "name": "pizzaAmount",
          "value": "2"
        }
      }
    }
  }
}
```
{% endraw %}

<div class="danger">
  <p><strong>注意</strong></p>
  <p>Extensionが<a href="#HandleSessionEndedRequest"><code>SessionEndedRequest</code>タイプのリクエスト</a>を受信すると、マルチターンの対話は終了します。<code>SessionEndedRequest</code>タイプのリクエストを受信してからは、Extensionからどんな応答(使用終了のあいさつなど)が返されても、CEKで無視されます。</p>
</div>

<div class="danger">
  <p><strong>注意</strong></p>
  <p>日本では現在、cardをサポートしておりません。</p>
</div>
