<!-- tags: ClovaHome -->

{% include book.ClovaHome.restricted_note %}

# Error

CLOVA Home ExtensionがCEKにエラーを返す際に使用されるインターフェースです。以下のエラーメッセージを使用できます。

| メッセージ            | タイプ         | 説明                                |
| --------------------- | -------------- | ----------------------------------- |
| [`ActionTemporarilyBlockedError`](#ActionTemporarilyBlockedError) | Error Response | リクエストが短時間に複数回行われた際など、機器およびユーザー安全のためリクエストをキャンセルした場合、CEKにこのメッセージをレスポンスをとして返します。 |
| [`ConditionsNotMetError`](#ConditionsNotMetError)  | Error Response | エンドポイントが動作するための特定の条件(ステータス)が満たされていない場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`DeviceFailureError`](#DeviceFailureError) | Error Response | エンドポイントに障害が発生した場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`DriverInternalError`](#DriverInternalError) | Error Response | 内部エラーが発生した場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`ExpiredAccessTokenError`](#ExpiredAccessTokenError) | Error Response | [アカウント連携](/CEK/Guides/Link_User_Account.md)の際、[認可サーバー](/CEK/Guides/Link_User_Account.md#BuildAuthServer)から発行されたアクセストークンが期限切れである場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`InvalidAccessTokenError`](#InvalidAccessTokenError) | Error Response | ユーザーが使用中のアクセストークンに対する権限を解除した場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`NoSuchTargetError`](#NoSuchTargetError) | Error Response | エンドポイントが存在しない場合、このメッセージをレスポンスとして返します。 |
| [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError) | Error Response | エンドポイントの現在のモードでサポートされていないディレクティブを受信した場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`TargetOfflineError`](#TargetOfflineError) | Error Response | エンドポイントがオフラインになっているため、アクセスできなかったことを示します。 |
| [`UnsupportedOperationError`](#UnsupportedOperationError) | Error Response | エンドポイントでサポートされないリクエストを示します。       |
| [`ValueNotFoundError`](#ValueNotFoundError) | Error Response | エンドポイントが測定値や状態値を測定したりまたは保存したりすることができず、リクエストされた値を提供できない場合、CEKにこのメッセージをレスポンスとして返します。 |
| [`ValueNotSupportedError`](#ValueNotSupportedError)  | Error Response | エンドポイントが対応していない値の設定がリクエストされた場合に、CEKにこのメッセージをレスポンスとして返します。 |
| [`ValueOutOfRangeError`](#ValueOutOfRangeError) | Error Response | エンドポイントが処理できる範囲外の値を設定しようとするリクエストを示します。 |

<div class="note">
<p><strong>メモ</strong></p>
<p>エラーメッセージの種類は追加される予定です。</p>
</div>

## ActionTemporarilyBlockedError {#ActionTemporarilyBlockedError}
リクエストが短時間に複数回行われた際など、機器およびユーザー安全のためリクエストをキャンセルした場合、CEKにこのメッセージをレスポンスをとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "ActionTemporarilyBlockedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

## ConditionsNotMetError {#ConditionsNotMetError}
エンドポイントが動作するための特定の条件(ステータス)が満たされていない場合、CEKにこのメッセージをレスポンスとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

| フィールド名 | データ型 | フィールドの説明                        | Optional |
| ------------ | -------- | --------------------------------------- | :------: |
| `state`      | string   | 満たされていない条件や状態を表す値。このフィールドはユーザーにTTSとして再生されるので、ユーザーにとってわかりやすい言葉で作成される必要があります。以下のように、ユーザーに現在の状況をレポートします。<pre><code>{デバイス}の{state}状態ではサポートしていない機能です。確認してから、再度試してください。</code></pre> | <!-- --> |

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "ConditionsNotMetError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "state": "省電力モード"
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## DeviceFailureError {#DeviceFailureError}
エンドポイントに障害が発生した場合、CEKにこのメッセージをレスポンスとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "DeviceFailureError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DriverInternalError`](#DriverInternalError)
* [`TargetOfflineError`](#TargetOfflineError)

## DriverInternalError {#DriverInternalError}
内部エラーが発生した場合、CEKにこのメッセージをレスポンスとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "DriverInternalError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DeviceFailureError`](#DeviceFailureError)
* [`TargetOfflineError`](#TargetOfflineError)

## ExpiredAccessTokenError {#ExpiredAccessTokenError}
[アカウント連携](/CEK/Guides/Link_User_Account.md)の際、[認可サーバー](/CEK/Guides/Link_User_Account.md#BuildAuthServer)から発行されたアクセストークンが期限切れである場合、CEKにこのメッセージをレスポンスとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "1abd6113-4a36-47c3-851e-bee3254fe183",
    "namespace": "ClovaHome",
    "name": "ExpiredAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`InvalidAccessTokenError`](#InvalidAccessTokenError)

## InvalidAccessTokenError {#InvalidAccessTokenError}
ユーザーが使用中のアクセストークンに対する権限を解除した場合、CEKにこのメッセージをレスポンスとして返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "b8ac8b45-9fb9-4dc4-97ca-d55e9fc1ff8f",
    "namespace": "ClovaHome",
    "name": "InvalidAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)

## NoSuchTargetError {#NoSuchTargetError}
エンドポイントが存在しない場合、CEKにこのメッセージをレスポンスとして返します。例えば、ユーザーがIoTサービスから特定のデバイスを削除したが、そのことがCLOVAアプリにまだ反映されていない状態でそのデバイスの操作をリクエストされた場合、このメッセージを返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "d458e46c-6827-4940-9340-a7a9d427d7ab",
    "namespace": "ClovaHome",
    "name": "NoSuchTargetError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ConditionsNotMetError`](#ConditionsNotMetError)
* [`TargetOfflineError`](#TargetOfflineError)

## NotSupportedInCurrentModeError {#NotSupportedInCurrentModeError}
エンドポイントの現在のモードでサポートされていないディレクティブを受信した場合、CEKにこのメッセージをレスポンスとして返します。例えば、エアコンの場合、除湿モードで動作している間は温度を調節できない製品があります。そのタイプのエアコンを使用しているユーザーが除湿モードで温度調節をリクエストした場合、このメッセージを返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "f321b946-b593-4279-a840-8e5af5a00146",
    "namespace": "ClovaHome",
    "name": "NotSupportedInCurrentModeError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`UnsupportedOperationError`](#UnsupportedOperationError)

## TargetOfflineError {#TargetOfflineError}
エンドポイントがオフラインになっているため、アクセスできなかったことを示します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DeviceFailureError`](#DeviceFailureError)
* [`DriverInternalError`](#DriverInternalError)

## UnsupportedOperationError {#UnsupportedOperationError}

エンドポイントでサポートされないリクエストを示します。ユーザーがエンドポイントでサポートされていない動作をリクエストした場合、CEKはすぐユーザーに有効な範囲外のリクエストであることを伝えます。ただし、`SetMode`のような動作は、CLOVA Home Extensionが[SetModeRequest](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest)メッセージを受信して`mode`フィールドの値を確認するまで、範囲内の動作かどうかを判断できません。もし、CLOVA Home Extensionがメッセージを受信し、サポートされていないモードである場合、エラーレスポンスを返す必要があります。その際、`UnsupportedOperationError`メッセージをCEKに返します。

例えば、ユーザーのサーモスタット(`"THERMOSTAT"`タイプ)が`SetMode`動作をサポートし、スリープモード(`"sleep"`)、外出モード(`"away"`)をサポートしている場合を仮定します。その場合、ユーザーがそのデバイスに冷房モード(`"cool"`)を設定するようにリクエストすると、CLOVA Home Extensionは`UnsupportedOperationError`メッセージをCEKに返す必要があります。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "e9a77ef6-748b-4f9b-aa3e-c14ece3fa726",
    "namespace": "ClovaHome",
    "name": "UnsupportedOperationError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## ValueNotFoundError {#ValueNotFoundError}
エンドポイントが測定値や状態値を測定したりまたは保存したりすることができず、リクエストされた値を提供できない場合、CEKにこのメッセージをレスポンスとして返します。例えば、エアコンは、現在の温度などの値をデフォルトで提供する必要がありますが、欠陥や一時的な故障によって温度を測定できず、値を提供できないことがあります。このメッセージは、そのような状況で使用できます。

### Payload fields
なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "57109b11-ee04-45df-9dd2-c979bc8608ea",
    "namespace": "ClovaHome",
    "name": "ValueNotFoundError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)


## ValueNotSupportedError {#ValueNotSupportedError}
エンドポイントが対応していない値の設定がリクエストされた場合に、CEKにこのメッセージをレスポンスとして返します。
例えば、1℃単位の温度設定しか対応していないエアコンに対して「26.5℃にして」のような1℃未満の単位での温度設定がリクエストされた場合や、テレビについて、設定されていないチャンネルがリクエストされた場合なおで使用できます。

### Payload fields
なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "57109b11-ee04-45df-9dd2-c979bc8608ea",
    "namespace": "ClovaHome",
    "name": "ValueNotSupportedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)


## ValueOutOfRangeError {#ValueOutOfRangeError}
エンドポイントが処理できる範囲外の値を設定しようとするリクエストを受け取った場合、CEKにこのメッセージをレスポンスとして返します。例えば、エアコンが18から28までの設定温度の値をサポートしていて、ユーザーが16や30などの値を設定するようにリクエストした場合、このメッセージが返されます。`payload`にエンドポイントが処理できる最大値と最小値を含める必要があります。

### Payload fields

| フィールド名   | データ型 | フィールドの説明                     | Optional |
| -------------- | -------- | ------------------------------------ | :------: |
| `maximumValue` | number   | エンドポイントでサポートされる最大値 | <!-- --> |
| `minimumValue` | number   | エンドポイントでサポートされる最小値 | <!-- --> |

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* `payload`に入力された値は、ユーザーに設定値の有効範囲を案内する際に使用できます。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "ValueOutOfRangeError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "minimumValue":18.0,
    "maximumValue":30.0
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ValueNotFoundError`](#ValueNotFoundError)
