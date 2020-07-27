## CLOVA Home Extensionメッセージ {#ClovaHomeExtMessage}
CLOVA Home Extensionメッセージは、IoTデバイスを制御するExtensionがCEKと情報のやり取りをする際、専用で使用するメッセージ仕様です。ここでは、CLOVA Home Extensionメッセージの[メッセージフォーマット](#ClovaHomeExtMessageFormat)と[インターフェース](#ClovaHomeExtInterface)について説明します。

### メッセージフォーマット {#ClovaHomeExtMessageFormat}

CLOVA Home Extensionメッセージは、`header`フィールドと`payload`で構成されます。リクエストメッセージとレスポンスメッセージの両方に共通します。そのうち、`payload`は、使用された[インターフェース](#ClovaHomeExtInterface)によって構成が異なることがあります。ここでは、CLOVA Home Extensionメッセージの共通フォーマットについて説明します。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>CLOVA Home Extensionメッセージは、リクエストメッセージとレスポンスメッセージの2種類があります。CEKがExtensionに渡すリクエストメッセージは、`XxxxRequest`のような名前を持ちます。ExtensionからCEKに返すレスポンスメッセージは、`XxxxConfirmation`または`XxxxResponse`のような名前を持ちます。また、エラーが発生しても正常にHTTPレスポンス(200 OK)を返す必要があり、その際、レスポンスメッセージは`XxxxError`のような名前で返される必要があります。</p>
</div>

#### Message structure
{% raw %}
```json
{
  "header": {
    "messageId": {{string}},
    "namespace": {{string}},
    "name": {{string}},
    "payloadVersion": {{string}}
  },
  "payload": {{object}}
}
```
{% endraw %}


#### Message fields
| フィールド名            | データ型 | フィールドの説明             | Optional |
| ----------------------- | -------- | ---------------------------- | :------: |
| `header`                | object   | メッセージのヘッダー         | <!-- --> |
| `header.messageId`      | string   | メッセージID(UUID)。個別メッセージを区別するために、CLOVAで作成された識別子です。 | <!-- --> |
| `header.name`           | string   | メッセージのAPI名            | <!-- --> |
| `header.namespace`      | string   | このフィールドは`"ClovaHome"`に固定されます | <!-- --> |
| `header.payloadVersion` | string   | `header.name`に明示されたCLOVA Home Extensionメッセージのバージョン。このバージョンによって、`payload`フィールドの構成が異なることがあります。 | <!-- --> |
| `payload`               | object   | `header.name`に指定された[インターフェース](#ClovaHomeExtInterface)によって、payloadオブジェクトの構成とフィールド値が異なります。 | <!-- --> |

#### Message example
{% raw %}
```json
例1：DiscoverAppliancesRequest - リクエストメッセージ
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

例2：DiscoverAppliancesResponse - レスポンスメッセージ
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
        "additionalApplianceDetails": {
        }
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
        "additionalApplianceDetails": {
        }
      }
    ]
  }
}

例3：IncrementTargetTemperatureConfirmation - レスポンスメッセージ
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 25.0
    },
    "previousState": {
      "targetTemperature": {
        "value": 22.0
      }
    }
  }
}

例4：TargetOffLineError - エラーレスポンスメッセージ
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```
{% endraw %}

#### 次の項目も参照してください。
* [CLOVA Home Extensionを作成する](/CEK/Guides/Build_Clova_Home_Extension.md)
* [インターフェース](#ClovaHomeExtInterface)

### インターフェース {#ClovaHomeExtInterface}
CLOVA Home Extensionメッセージのインターフェースは、次のようなものがあります。

* インターフェース
  * [Discoveryインターフェース](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md)
  * [Controlインターフェース](/CEK/References/ClovaHomeInterface/Control_Interfaces.md)
  * [Errorインターフェース](/CEK/References/ClovaHomeInterface/Error_Interfaces.md)

* 共有オブジェクト
  * [共有オブジェクト](/CEK/References/ClovaHomeInterface/Shared_Objects.md)
