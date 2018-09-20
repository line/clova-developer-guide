## HTTPメッセージ {#HTTPMessage}
CEKとExtensionが通信する際、HTTP/1.1を使用して基本的なHTTPSリクエストとHTTPSレスポンスをやり取りします。CEKとExtensionが通信する際、HTTPメッセージのボディには、JSON形式のメッセージが含まれます。ここでは、CEKとExtensionがやり取りするHTTPメッセージの構成について説明します。

* [HTTPヘッダー](#HTTPHeader)
  * [リクエストメッセージの検証](#RequestMessageValidation)
* [HTTPボディ](#HTTPBody)

### HTTPヘッダー {#HTTPHeader}
CEKがExtensionに解析されたユーザーの発話情報を渡す際、HTTPリクエストを使用します。その際、HTTPリクエストのヘッダーは、次のように構成されます。

{% raw %}
```
POST /APIpath HTTP/1.1
Host: YOUR_EXTENSION_ENDPOINT
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK：{{ SignatureCEK }}
```
{% endraw %}

* HTTP/1.1バージョンでHTTP通信し、POSTメソッドを使用します。
* Hostとリクエストパスは、Extensionの開発者があらかじめ定義したURIに設定されます。
* リクエストボディのデータはJSON形式で、UTF-8エンコーディングを使用します。
* `SignatureCEK`フィールドとRSA公開鍵を使用して、[Clovaから送信されたリクエストかどうかを検証](#RequestMessageValidation)することができます。

逆に、ExtensionがClovaに処理結果を返す際、HTTPレスポンスを使用します。その際のHTTPレスポンスヘッダーは、以下のように設定をしてください。
{% raw %}
```
HTTP/1.1 200 OK
Content-Type: application/json;charset-UTF-8
```
{% endraw %}
* CEKから渡されたHTTPリクエストに対するレスポンスとして、処理結果を返します。
* ボディのデータはJSON形式で、UTF-8エンコーディングを使用します。

#### リクエストメッセージの検証 {#RequestMessageValidation}

ExtensionがCEKからHTTPリクエストを受信するとき、そのリクエストが第三者ではなく、Clovaから送信された信頼できるリクエストかどうかを検証する必要があります。検証の方法については、[リクエストメッセージを検証する](/CEK/Guides/Build_Custom_Extension.md#RequestMessageValidation)を参照してください。

### HTTPボディ {#HTTPBody}
リクエストメッセージとレスポンスメッセージのボディはJSON形式で、解析されたユーザーの発話情報や、Extensionの処理結果が含まれています。それぞれのメッセージの構成は、使用するExtensionの種類によって異なります。メッセージ構成の詳細については、[Custom Extensionメッセージ](#CustomExtMessage)を参照してください。
