<!-- tags: ClovaHome -->

## CLOVA Home Extensionリクエストを処理する {#HandleClovaHomeExtensionRequest}

ユーザーは、「照明をつけて」などのように、IoTデバイスの操作をCLOVAにリクエストします(HTTPリクエスト)。クライアントは[Discovery機能](#ProvideDeviceDiscovery)を利用して確保したデバイスのリストと、デバイスごとに許可されている動作を確認して、ユーザーからのIoTデバイス操作のリクエストが処理できるものなのか検証します。検証されたユーザーのリクエストは、CEKを介してCLOVA Home Extensionに渡されます。その際、[CLOVA Home Extensionメッセージ](/CEK/References/CEK_API_ClovaHome.md#ClovaHomeExtMessage)を使用します。

「照明をつけて」のようなリクエストは、以下のように[`TurnOnRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOnRequest)メッセージで送信されます。

{% raw %}
```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "TurnOnRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    }
  }
}
```
{% endraw %}

受け取ったリクエストメッセージを分析して、IoTサービスが提供するURIにユーザーからのIoTデバイス操作のリクエストを送信します。リクエストを送信する際、受け取ったアクセストークンを使用します。
