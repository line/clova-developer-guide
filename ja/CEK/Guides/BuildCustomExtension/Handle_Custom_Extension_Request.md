## Custom Extensionリクエストを処理する {#HandleCustomExtensionRequest}
Custom ExtensionはCEKから[Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)形式のユーザーリクエストを受信します(HTTPSリクエスト)。Custom Extensionは通常、次のようにリクエストを処理し、レスポンスする必要があります。

![](/CEK/Resources/Images/CEK_Custom_Extension_Sequence_Diagram.png)

このようなユーザーのリクエストは一度で終わるリクエストの場合もありますが、次のように文脈が維持される必要のあるマルチターン対話の場合もあります。

![](/CEK/Resources/Images/CEK_Custom_Extension_Multi-turn_Sequence_Diagram.png)

そのため、ユーザーのリクエストを3つのタイプに分類しています。Custom Extensionの開発者は、リクエストのタイプに応じて適切に処理する必要があります。
3つのリクエストタイプと、各リクエストタイプのユーザーの発話パターンは次のとおりです。

| リクエストタイプ | ユーザーの発話パターン | サンプル発話 |
|---------|--------------|---------|
|[LaunchRequest](#HandleLaunchRequest) | _[Extensionの呼び出し名]_ + 「起動して/開いて/実行して」 | 「ピザボットを起動して」 |
| [IntentRequest](#HandleIntentRequest)| (`LaunchRequest`タイプのリクエストを受け付けた状態で) _[Extensionごとに登録したコマンド]_ | (ピザボット起動状態で)「注文を確認して」 |
| [SessionEndedRequest](#HandleSessionEndedRequest) | (`LaunchRequest`タイプのリクエストを受け付けた状態で)「終了して/終了/やめて」 | 「(ピザボットを)終了して」 |

<div class="note">
<p><strong>メモ</strong></p>
<p><a href="/CEK/References/CEK_API.html#CustomExtEventRequest"><code>EventRequest</code></a>は、ユーザの発話の有無に関わらず、デバイスの状態が変化したときにExtensionに送信されるメッセージです。これらのイベントは、デバイスの状態を取得したり、状態変化したことを検知することに利用できます。また、Extensionが<a href="/CEK/Guides/Build_Custom_Extension.html#ProvideAudioContent">オーディオコンテンツを提供する</a>際にも使用されます。ここでは、オーディオコンテンツ再生時の<code>EventRequest</code>については説明しません。</p>
</div>

### LaunchRequestの処理 {#HandleLaunchRequest}
[`LaunchRequest`タイプ](/CEK/References/CEK_API.md#CustomExtLaunchRequest)のリクエストは、ユーザーが特定のExtensionを使用すると宣言したことを示す際に使用されます。例えば、ユーザーが「ピザボットを起動して」や「ピザボットを開いて」のように指示した場合、CEKはピザの宅配サービスを提供するExtensionに`LaunchRequest`タイプのリクエストを渡します。このタイプのリクエストを渡されたExtensionは、ユーザーの次のリクエストも受信できるように準備している必要があります。

LaunchRequestタイプのメッセージは、`request.type`フィールドに`"LaunchRequest"`の値を持ち、`request`フィールドにユーザーの発話の解析情報を含めていません。Extensionの開発者は、このメッセージを受信した場合、事前の準備事項を処理するか、ユーザーにサービスを提供する準備ができたという[レスポンスメッセージ](#ReturnCustomExtensionResponse)を返します。

このメッセージを受信してから[`SessionEndedRequest`タイプ](#HandleSessionEndedRequest)のリクエストメッセージを受信するまで、[`IntentRequest`タイプ](#HandleIntentRequest)のリクエストメッセージを受信し、`session.sessionId`フィールドは前のメッセージと同じ値を持ちます。

次は`LaunchRequest`タイプのリクエストメッセージのサンプルです。

{% raw %}
```json
{
  "version": "1.0",
  "session": {
    "new": true,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.example.extension.pizzabot"
      },
      "user": {
        "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "LaunchRequest"
  }
}
```
{% endraw %}

上記のサンプルで、各フィールドの意味は次のとおりです。

* `version`：使用しているCustom Extensionメッセージフォーマットのバージョンです。現在のバージョンはv1.0です。
* `session`：**新しいセッションです**。新しいセッションで使用されるセッションのIDとユーザーの情報(ID、アクセストークン)が含まれています。
* `context`：クライアントデバイスの情報です。デバイスのIDとデフォルトユーザーの情報が含まれています。
* `request`：`LaunchRequest`タイプのリクエストです。対象Extensionの使用を開始することを示します。ユーザーの発話の解析情報はありません。

### IntentRequestの処理 {#HandleIntentRequest}

[`IntentRequest`タイプのリクエスト](/CEK/References/CEK_API.md#CustomExtIntentRequest)は、あらかじめ定義した[対話モデル](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)に従って、CEKがExtensionにユーザー発話のリクエストを送信する際に使用されます。例えば、ユーザーが「ピザボットを起動して」と発話してサービスを開始した後に、「ピザを頼んで」と指示した時に、CEKはピザの宅配サービスを提供するExtensionに`IntentRequest`タイプのリクエストを渡します。

IntentRequestタイプのリクエストは、`request.type`フィールドに`"IntentRequest"`の値を持ちます。呼び出されたインテントの名前と、解析されたユーザーの発話情報は、`request.intent`フィールドから確認できます。このフィールドを分析してユーザーのリクエストを処理してから、[レスポンスメッセージ](#ReturnCustomExtensionResponse)を返します。

次は`IntentRequest`タイプのリクエストメッセージのサンプルです。

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
    "System": {
      "application": {
        "applicationId": "com.example.extension.pizzabot"
      },
      "user": {
        "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
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

上記のサンプルで、各フィールドの意味は次のとおりです。

* `version`：使用しているCustom Extensionメッセージフォーマットのバージョンです。現在のバージョンはv1.0です。
* `session`: **既存のセッションに続くユーザーのリクエストです**。既存セッションのIDとユーザーの情報(ID、アクセストークン)が含まれています。
* `context`：クライアントデバイスの情報です。デバイスのIDとデフォルトユーザーの情報が含まれています。
* `request`: `IntentRequest`タイプのリクエストです。`"OrderPizza"`という名前で登録された[インテント](/Design/Design_Guideline_For_Extension.md#Intent)を呼び出しています。該当するインテントが必要とする情報として`"pizzaType"`という[スロット](/Design/Design_Guideline_For_Extension.md#Slot)が一緒に渡されます。そのスロットは`"ペパロニ"`という値を持っています。

<div class="note">
  <p><strong>メモ</strong></p>
  <p><code>IntentRequest</code>タイプのリクエストは、<code>LaunchRequest</code>タイプのリクエストと関係なく、新しいセッションを開始してリクエストを処理することができます。</p>
</div>

### SessionEndedRequestの処理 {#HandleSessionEndedRequest}

[`SessionEndedRequest`タイプのリクエスト](/CEK/References/CEK_API.md#CustomExtSessionEndedRequest)は、ユーザーが特定のモードやCustom Extensionの使用を中断すると宣言したことを示す際に使用されます。ユーザーが「終了して」「やめて」などのように指示した場合、クライアントはExtensionの使用を中断し、CEKは対話サービスを提供するExtensionに`SessionEndedRequest`タイプのリクエストを渡します。

`SessionEndedRequest`タイプのメッセージは`request.type`フィールドに`"SessionEndedRequest"`の値を持ち、`LaunchRequest`タイプと同じく`request`フィールドにユーザーの発話の解析情報は含まれません。Extensionの開発者は、サービス終了時の後処理を実施してください。

次は`SessionEndedRequest`タイプのリクエストメッセージのサンプルです。


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
    "System": {
      "application": {
        "applicationId": "com.example.extension.pizzabot"
      },
      "user": {
        "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "SessionEndedRequest"
  }
}
```
{% endraw %}

上記のサンプルで、各フィールドの意味は次のとおりです。

* `version`：使用しているCustom Extensionメッセージフォーマットのバージョンです。現在のバージョンはv1.0です。
* `session`: **既存のセッションに続くユーザーのリクエストです**。既存セッションのIDとユーザーの情報(ID、アクセストークン)が含まれています。
* `context`：クライアントデバイスの情報です。デバイスのIDとデフォルトユーザーの情報が含まれています。
* `request`: `SessionEndedRequest`タイプのリクエストです。対象Extensionの使用を中断することを示します。ユーザーの発話の解析情報はありません。

<div class="danger">
  <p><strong>注意</strong></p>
  <p>CEKが<code>SessionEndedRequest</code>タイプのリクエストをExtensionに送信した瞬間から、CEKはそのExtensionからの応答をすべて無視します。</p>
</div>
