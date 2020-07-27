<!-- tags: ClovaHome -->

## SceneDiscovery機能を提供する {#ProvideSceneDiscovery}

ユーザーがIoTサービスを有効にすると、クライアントアプリ、またはクライアントデバイスとペアリングするアプリで、ユーザーアカウントに登録されているシーンのリストを提供する事ができます。CLOVA Home Extensionは、CEKから[`DiscoverScenesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesRequest)メッセージを受け取ります（HTTPリクエスト）。CLOVA Home Extensionは、受け取ったユーザーアカウントのアクセストークンを使用して、IoTサービスからユーザーアカウントに登録されているシーンのリストを取得し、そのリストを[`DiscoverScenesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesResponse)メッセージで応答する必要があります（HTTPレスポンス）。CEKとCLOVA Home Extensionの間でやり取りするメッセージについての詳細は、[CLOVA Home Extensionメッセージ](/CEK/References/CEK_API_ClovaHome.md#ClovaHomeExtMessage)を参照してください。

![](/CEK/Assets/Images/CEK_Clova_Home_Extension_Sequence_Diagram_2.png)

以下は、CLOVA Home Extensionが受け取る[`DiscoverScenesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesRequest)メッセージのサンプルです。
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

このメッセージを受信すると、CLOVA Home Extensionは受け取ったアクセストークンを使用してユーザーアカウントを特定し、そのアカウントに登録されているシーンのリストを[`DiscoverScenesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesResponse)メッセージで返すことが可能です。シーンごとに、シーンの識別子および名前などの情報が含まれます。

以下は、CLOVA Home Extensionが`DiscoverScenesResponse`メッセージでCEKに応答するサンプルです。

{% raw %}
```json
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
