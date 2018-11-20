<!-- tags: ClovaHome -->

## Discovery機能を提供する {#ProvideDeviceDiscovery}

ユーザーがIoTサービスを有効にすると、クライアントアプリ、またはクライアントデバイスとペアリングするアプリで、ユーザーアカウントに登録されているIoTデバイスのリストを提供する必要があります。Clova Home Extensionは、CEKから[`DiscoverAppliancesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest)メッセージを受け取ります(HTTPリクエスト)。Clova Home Extensionは、受け取ったユーザーアカウントのアクセストークンを使用して、IoTサービスからユーザーアカウントに登録されているデバイスのリストを取得し、そのリストを[`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)メッセージで応答する必要があります(HTTPレスポンス)。CEKとClova Home Extensionの間でやり取りするメッセージについての詳細は、[Clova Home Extensionメッセージ](/CEK/References/CEK_API_ClovaHome.md#ClovaHomeExtMessage)を参照してください。

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Sequence_Diagram.png)

以下は、Clova Home Extensionが受け取る[`DiscoverAppliancesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest)メッセージのサンプルです。
{% raw %}
```json
{
    "header": {
        "messageId": "8ddd7f05-7703-4cb4-a6dd-93c209c6647b",
        "name": "DiscoverAppliancesRequest",
        "namespace": "ClovaHome",
        "payloadVersion": "1.0"
    },
    "payload": {
        "accessToken": "92ebcb67fe33"
    }
}
```
{% endraw %}

このメッセージを受信すると、Clova Home Extensionは受け取ったアクセストークンを使用してユーザーアカウントを特定し、そのアカウントに登録されているデバイスのリストを[`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)メッセージで返す必要があります。デバイスごとに、デバイスの識別子および名前、デバイスのタイプ、アクセスできるかどうか(オンラインか否か)、そしてサポートする動作(`actions`)などの情報が含まれます。

以下は、Clova Home Extensionが`DiscoverAppliancesResponse`メッセージでCEKに応答するサンプルです。

{% raw %}
```json
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "スマート照明",
        "version": "v1.0",
        "friendlyName": "リビングの照明",
        "friendlyDescription": "スマートフォンで制御できる照明",
        "isIr": false,
        "isReachable": true,
          "actions": [
            "DecrementBrightness",
            "HealthCheck",
            "IncrementBrightness",
            "SetBrightness",
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {},
        "location": ""
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "スマートコンセント",
        "version": "v1.0",
        "friendlyName": "キッチンのコンセント",
        "friendlyDescription": "節電コンセント",
        "isIr": false,
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM"
      }
    ]
  }
}
```
{% endraw %}
