# ユーザーアカウントを連携する
Clovaは、[Custom Extension](/CEK/Guides/Build_Custom_Extension.md)、または[Clova Home Extension](/CEK/Guides/Build_Clova_Home_Extension.md)を介して、ユーザーアカウント権限を必要とする外部サービスを提供することができます。例えば、有料コンテンツサービスの音楽ストリーミングサービスや、ショッピング、金融、ホームIoTなどのサービスをClovaと連携することができます。そのために、Clovaは外部サービスのユーザーアカウントとClovaのユーザーアカウントを連携するアカウント連携(account linking)をサポートしています。アカウント連携は[OAuth 2.0](https://tools.ietf.org/html/rfc6749)を使用して行われます。

アカウント連携は、Custom Extensionがユーザーのアカウント認証を必要とする外部サービスを提供する際に使用されます。アカウント認証を必要としない外部サービスはアカウント連携なしに提供できます。ユーザーを識別できる程度の情報を必要とするサービスは、通常、[Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)が提供する端末識別子(`context.System.device.deviceId`)とユーザーアカウント識別子(`context.System.user.userId`または`session.user.userId`)を組み合わせた値を使用します。


<div class="note">
<p><strong>メモ</strong></p>
<p>Clova Home Extensionは、必ずアカウント連携を使用する必要があります。</p>
</div>

このドキュメントでは、次の内容について説明します。
* [アカウント連携の動作について](#UnderstandAccountLinking)
* [アカウント連携を適用する](#ApplyAccountLinking)

## アカウント連携の動作について {#UnderstandAccountLinking}
アカウント連携をExtensionに適用するためには、アカウント連携の仕組みについて知る必要があります。ここでは次の内容を説明します。
* [アカウント連携を設定する](#SetupAccountLinking)
* [アカウント連携後Extensionを呼び出す](#ExtensionInvokingAfterAccountLinking)

### アカウント連携を設定する {#SetupAccountLinking}
ユーザーがアカウント認証の必要なCustom ExtensionまたはClova Home Extensionをアクティブにすると、次のようにアカウント連携の設定が開始されます。

![](/CEK/Resources/Images/CEK_Account_Linking_Setup_Sequence_Diagram.png)

1. ユーザーが特定のCustom ExtensionまたはClova Home Extensionを有効にします。

2. クライアントアプリまたはクライアントデバイスとペアリングするアプリで、外部サービスのログインページを表示します。その際、Extensionの開発者があらかじめ登録し認可サーバーの **[認証URL](#BuildAuthServer)** を使用します。

3. ユーザーがアカウントの認証を完了すると、認可コードが返されます。

4. クライアントは、受け取った認可コードをClovaに渡します。

5. Clovaは、**[アクセストークンURI](#RegisterAccountLinkingInfo)** からアクセストークンとリフレッシュトークンをリクエストします。その際、認可コードを渡し、取得したアクセストークンとリフレッシュトークンをユーザーのClovaアカウントに保存します。

6. ユーザーはアカウント認証の必要なサービスを使用できるようになります。

<div class="note">
<p><strong>メモ</strong></p>
<p>ユーザーが特定のCustom ExtensionまたはClova Home Extensionを非アクティブにした場合、ユーザーのClovaアカウントに保存されていたアクセストークンは削除されます。その後、ユーザーがそのExtensionを再びアクティブにすると、再度アカウント連携を行う必要があります。</p>
</div>

### アカウント連携後Extensionを呼び出す {#ExtensionInvokingAfterAccountLinking}
アカウント連携が完了した状態で、CEKは次の順序でExtensionを呼び出します。

1. ユーザーのリクエストを処理するために、通常どおりにExtensionを呼び出します。

2. **(アクセストークンが期限切れの場合)** リフレッシュトークンを使用して **[アクセストークンURI](#RegisterAccountLinkingInfo)** に新しいアクセストークンをリクエストします。

3. Extensionに渡すメッセージにアクセストークンを含めてユーザーのリクエストを渡します。
   * Custom Extensionの場合、`context.System.user.accessToken`と`session.user.accessToken`フィールドにアクセストークンが含まれます。
   * Clova Home Extensionの場合、`payload.accessToken`フィールドにアクセストークンが含まれます。

4. Extensionは、状況に応じて次のように応答する必要があります。
   * アクセストークンが有効の場合、ユーザーのリクエストを処理し、その結果を返す必要があります。
   * アクセストークンが無効の場合、[アカウント連携の設定](#SetupAccountLinking)に進むために結果を返す必要があります。

## アカウント連携を適用する {#ApplyAccountLinking}
開発しているExtensionにアカウント連携を適用するには、以下の項目を行う必要があります。

1. [認可サーバーを構築する](#BuildAuthServer)
2. [アカウント権限の検証を実装する](#AddValidationLogic)
3. [アカウント連携情報を登録する](#RegisterAccountLinkingInfo)

### 認可サーバーを構築する {#BuildAuthServer}

Extensionにアカウント連携を適用するには、ユーザーがアカウント認証を行うログインページと、認証後にアクセストークンを発行するサーバーを構築する必要があります。

ユーザー認証のために提供するログインページは、次の項目を満たす必要があります。
* HTTPSプロトコルでページを提供します。
* モバイル用のページをサポートします。
* ポップアップウィンドウを提供しません。
* 認証が完了すると、リダイレクトURL(`redirect_uri`)に移動します。その際、認可コードをパラメータで送信する必要があります。
* `state`パラメータをリダイレクトURL(`redirect_uri`)に引き続き送信します。


ユーザーがアカウントを認証できるようにログインUIを提供するページのアドレスを **認証URL** と呼びます。認証URLは、Clova Developer Centerで[Extensionを登録する](/DevConsole/Guides/CEK/Register_Extension.md)ときに入力します。ユーザーがExtensionの[アカウント連携を使用するように設定](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking)する際、その **認証URL** が次のパラメータと一緒に呼び出されます。

| パラメータ名   | 説明                                                                                                                                                      |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `state`         | 認証セッションの期限切れを確認する状態値この値は5分後に期限切れとなるため、ユーザーが5分以内に認証を済まさない場合、再度認証を行う必要があります。       |
| `client_id`     | Clovaが外部サービスのアクセストークンを取得するために使用するID開発者は、Clova Developer Centerであらかじめ`cliend_id`を登録しておく必要があります。     |
| `response_type` | OAuth 2.0認可グラントタイプを定義したパラメータ。`"code"`タイプを使用します。Clova Developer Centerで指定します。現在、`"code"`タイプのみサポートしています|
| `scope`         | OAuthの`scope`フィールドアクセスレベルを定義できます。Clova Developer Centerであらかじめ`scope`を登録しておく必要があります。                            |
| `redirect_uri`  |アカウント認証後にリダイレクトするURLです。`redirect_uri`の値は、Clova Developer CenterでExtensionを登録するときに、[アカウント連携を設定する](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking)から確認できます。現在、`{{ book.RedirectURLforAccountLinking }}`が使用されています。 |

<div class="note">
  <p><strong>メモ</strong></p>
  <p>パラメータの詳細については、OAuth 2.0 Authorization Frameworkの<a href="https://tools.ietf.org/html/rfc6749#section-4">Obtaining Authorization</a>を参照してください。</p>
</div>

以下は、クライアントアプリまたはクライアントデバイスとペアリングするアプリが、ログインページをリクエストするURLの例です。

<pre><code>https://example.com/login?state=qwer123
                            &client_id=clova-extension
                            &scope=listen_music%20basic_profile
                            &response_type=code
                            &redirect_uri={{ book.RedirectURLforAccountLinking }}
</code></pre>


<div class="note">
<p><strong>メモ</strong></p>
<p><code>redirect_uri</code>は、Clova Developer Centerの<a href="/DevConsole/Guides/CEK/Register_Extension.md#RedirectURI">アカウント連携を設定</a>する画面で確認できます。</p>
</div>


アカウント連携後にリダイレクトするURL(`redirect_uri`)に、次のパラメータを渡す必要があります。

| パラメータ名  | 説明                                                                                                                                                      |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `vendorId`     | Extensionの開発者に発行されたID外部サービスまたは会社を区別するために、Clova Developer Centerに登録されているIDです。`redirect_uri`にあらかじめ含まれています。 |
| `state`        | 認証セッションの期限切れを確認する状態値 **認証URL** から渡された`state`パラメータをそのまま入力します。                                                 |
| `code`         | 認可コード`response_type`の値が`"code"`の場合、このパラメータに認可コードを入力します。                                                                  |
| `token_type`   | アクセストークンのタイプ`access_token`と一緒に渡される必要があります。`"Bearer"`で固定されます。                                                         |

次は、ユーザーのアカウント認証が完了してから移動されるリダイレクトURLの例です。

<pre><code>{{ book.RedirectURLforAccountLinking }}?vendorId=YourServiceOrCompanyID
                                &state=qwer123
                                &code=nl__eCSTdsdlkjfweyuxXvnl
</code></pre>


Clovaがユーザーアカウントを連携するために認可コードを取得した場合、Clovaは再びExtensionの開発者がClova Developer Centerにあらかじめ登録した **[アクセストークンURI](#RegisterAccountLinkingInfo)** からアクセストークンをリクエストします。その際、Clovaは取得した認可コードをパラメータに送信します。認可サーバーは外部サービスのアカウント権限が付与されたアクセストークンと、アクセストークンを更新できるリフレッシュトークンを発行する必要があります。

### アカウント権限の検証を実装する {#AddValidationLogic}
アカウント連携を適用するために、Extensionの開発者はアクセストークンの有効性を検証するコードを作成する必要があります。Custom ExtensionとClova Home Extensionに渡されるExtensionメッセージは、それぞれ次のような`accessToken`フィールドを持っています。
以下のフィールドでアクセストークンを確認し、そのアクセストークンが存在していて、有効な値であるか確認する必要があります。

* Custom Extension: `context.System.user.accessToken`, `session.user.accessToken`
* Clova Home Extension: `payload.accessToken`

{% raw %}
```json
//例1：Custom Extensionメッセージの例
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

<div class="note">
  <p><strong>メモ</strong></p>
  <p>アクセストークンが存在しないか、または無効の場合、Extensionはクライアントがユーザーアカウントを再度連携するように、CEKに応答を返す必要があります。</p>
</div>


### アカウント連携情報を登録する {#RegisterAccountLinkingInfo}
認可サーバーの構築とExtensionのアカウント連携が完了すると、[Clova Developer Center](/DevConsole/ClovaDevConsole_Overview.md)に、[認可サーバーを構築する](#BuildAuthServer)で説明されている情報を登録する必要があります。Clova Developer Centerに登録されているExtensionで、以下のような[アカウント連携情報を入力](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking)します。

| フィールド名                 | 説明                                                                                                                                                                             |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `認証URL`                    | ユーザーが[アカウント認証](#SetupAccountLinking)のためにアクセスするURL                                                                                                          |
| `Client ID`                    | ユーザー[アカウント認証](#SetupAccountLinking)ページをリクエストする際に、サービスを識別するために付与したクライアントID                                                       |
| `Authorization Grant Type`     | OAuth 2.0の認可グラントタイプ。現在、Authorization code grantタイプのみサポートしています。                                                                                    |
| `Access Token URI`             | 認可コードでアクセストークンを取得するためのアドレス。Authorization code grantタイプに設定した場合、入力します。                                                               |
| `Client Secret`                | 認可コードでアクセストークンを取得する際に、 **Client ID** と一緒に渡されるクライアントシークレットのこと。Authorization code grantタイプに設定した場合、入力します。          |
| `Client Authentication Scheme` | アクセストークンURIにアクセストークンをリクエストする際に使用されるスキーム                                                                                                    |
| `Privacy Policy URL`           | サービスのプライバシーポリシーが提供されるページClovaアプリまたはペアリングアプリに表示されます。                                                                              |
