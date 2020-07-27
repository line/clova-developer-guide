<!-- tags: ClovaHome -->

{% include book.ClovaHome.restricted_note %}

# Discovery

ユーザーアカウントに登録されているIoTデバイス・シーンのリストを確認する際に使用されるインターフェースです。

| メッセージ                    | タイプ   | 説明                              |
| ----------------------------- | -------- | --------------------------------- |
| [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)   | Request  | ユーザーが登録したIoTデバイスのリストをCLOVA Home Extensionにリクエストします。 |
| [`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse) | Response | [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)メッセージに対するレスポンスです。ユーザーが登録したIoTデバイスのリストをCEKに返します。 |
| [`DiscoverScenesRequest`](#DiscoverScenesRequest)   | Request  | ユーザーが登録したシーンのリストをCLOVA Home Extensionにリクエストします。 |
| [`DiscoverScenesResponse`](#DiscoverScenesResponse) | Response | [`DiscoverScenesRequest`](#DiscoverScenesRequest)メッセージに対するレスポンスです。ユーザーが登録したシーンのリストをCEKに返します。 |

## DiscoverAppliancesRequest {#DiscoverAppliancesRequest}
ユーザーが登録したデバイスのリストをCLOVA Home Extensionにリクエストします。このリクエストに対するレスポンスとして、[`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse)メッセージを使用する必要があります。

### Payload fields

| フィールド名  | データ型 | フィールドの説明                       | Optional |
| ------------- | -------- | -------------------------------------- | :------: |
| `accessToken` | string   | CLOVA Home Extensionのアクセストークン | <!-- --> |

### Message example

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

### 次の項目も参照してください。
* [`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse)

## DiscoverAppliancesResponse {#DiscoverAppliancesResponse}
ユーザーが登録したデバイスのリストをCEKに返します。このメッセージは、[`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)メッセージに対するレスポンスとして使用します。

### Payload fields

| フィールド名             | データ型 | フィールドの説明            | Optional |
| ------------------------ | -------- | --------------------------- | :------: |
| `customCommands[]`       | [CustomCommandInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#CustomCommandInfoObject) array | ユーザーアカウントに登録されているカスタムコマンドのリストを持つオブジェクト配列 | <!-- --> |
| `discoveredAppliances[]` | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) array | ユーザーアカウントに登録されているデバイスを説明するオブジェクト配列 | <!-- --> |

### 備考
IoTサービスを提供する際、ユーザーアカウントに登録されているデバイスのリストを提供する必要があります。

### Message example

{% raw %}
```json
// サンプル：DiscoverAppliancesResponseメッセージで使用されたサンプル
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "customCommands": [
      {
        "name": "おはよう",
        "actions": [
          {
            "applianceId": "device-001",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      },
      {
        "name": "おやすみ",
        "actions": [
          {
            "applianceId": "device-0011",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      }
    ],
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
          "actionsNeededUserConfirmation": [
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {}
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
          "actionsNeededUserConfirmation": [
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM",
        "tags": ["勉強", "ブラウンの部屋", "おでかけの際に電源をオフにするデバイス"]
      }
    ]
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)



## DiscoverScenesRequest {#DiscoverScenesRequest}
ユーザーが登録したシーンのリストをCLOVA Home Extensionにリクエストします。このリクエストに対するレスポンスとして、[`DiscoverScenesResponse`](#DiscoverScenesResponse)メッセージを使用する必要があります。

### Payload fields

| フィールド名  | データ型 | フィールドの説明                       | Optional |
| ------------- | -------- | -------------------------------------- | :------: |
| `accessToken` | string   | CLOVA Home Extensionのアクセストークン | <!-- --> |

### Message example

{% raw %}
```json
{
    "header": {
        "messageId": "8ddd7f05-7703-4cb4-a6dd-93c209c6647b",
        "name": "DiscoverScenesRequest",
        "namespace": "ClovaHome",
        "payloadVersion": "1.0"
    },
    "payload": {
        "accessToken": "92ebcb67fe33"
    }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DiscoverScenesResponse`](#DiscoverScenesResponse)

## DiscoverScenesResponse {#DiscoverScenesResponse}
ユーザーが登録したシーンのリストをCEKに返します。このメッセージは、[`DiscoverScenesRequest`](#DiscoverScenesRequest)メッセージに対するレスポンスとして使用します。

### Payload fields

| フィールド名             | データ型 | フィールドの説明            | Optional |
| ------------------------ | -------- | --------------------------- | :------: |
| `discoveredScenes[]`     | [SceneInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SceneInfoObject) array | ユーザーアカウントに登録されているシーンを説明するオブジェクト配列 | <!-- --> |

### 備考
IoTサービスを提供する際、ユーザーアカウントに登録されているシーンのリストを提供する必要があります。

### Message example

{% raw %}
```json
// サンプル：DiscoverScenesResponseメッセージで使用されたサンプル
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverScenesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredScenes": [
      {
        "sceneId": "scene-001",
        "sceneName": "おはよう",
        "needsUserConfirmation" : true,
        "additionalSceneDetails": {}
      },
      {
        "sceneId": "scene-002",
        "sceneName": "おやすみ",
        "needsUserConfirmation" : false,
        "additionalSceneDetails": {}
      }
    ]
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DiscoverScenesRequest`](#DiscoverScenesRequest)
