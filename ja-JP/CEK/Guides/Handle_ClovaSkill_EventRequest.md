# ユーザーの利用開始および停止を処理する

開発したスキルが審査を通過して配布が完了すると、スキルストアに掲載されユーザーが利用できるようになります。
ユーザーは一度利用開始したスキルを、スキルストアから **利用停止** ボタンで無効化することができます。
開発者は利用開始後に取得したデータを、利用停止時に削除する必要があります。

スキルの利用開始や利用停止は、[`EventRequest`のリクエストタイプ](/CEK/References/CEK_API.md#CustomExtEventRequest)の`SkillEnabled`や`SkillDisabled`としてExtensionにに伝えられます。

ここでは、`EventRequest`を利用してスキルの有効化/無効化を検知する方法を説明します。

## スキルが利用開始された場合 {#SkillEnabled}

ユーザーがスキルを利用開始すると、Clovaには次のようなリクエストメッセージが送信されます。

{% raw %}
```json
// 例1: スキルを利用開始したとき

"request": {
  "type": "EventRequest",
  "requestId": "f09874hiudf-sdf-4wku-flksdjfo4hjsdf",
  "timestamp": "2018-06-11T09:19:23Z",
  "event" : {
    "namespace":"ClovaSkill",
    "name":"SkillEnabled",
    "payload": null
  }
}
```
{% endraw %}

* `event.namespace`はスキルが有効か無効かを示す名前空間で、値は`"ClovaSkill"`に固定されます。
* スキルを利用開始したときの`event.name`は`"SkillEnabled"`になります

ユーザの初期設定が必要である場合は、この`EventRequest`を受け取ったときに実行してください。

## スキルが利用停止された場合 {#SkillDisabled}

ユーザーがスキルを利用停止すると、`request`オブジェクトのフィールドは次のようになります。

{% raw %}
```json
// 例2: スキルを利用停止したとき

"request": {
  "type": "EventRequest",
  "requestId": "f09874hiudf-sdf-4wku-flksdjfo4hjsdf",
  "timestamp": "2018-06-19T11:37:21Z",
  "event" : {
    "namespace":"ClovaSkill",
    "name":"SkillDisabled",
    "payload": null
  }
}
```
{% endraw %}

* `event.namespace`はスキルが有効か無効かを示す名前空間で、値は`"ClovaSkill"`に固定されます。
* スキルを利用停止したときの`event.name`は`"SkillDisabled"`になります。

このリクエストを受け取った際には、スキルを通して得たユーザー情報を必ず削除してください。

なお、ユーザーがスキルストアでアプリを利用停止すると、ユーザーのClovaアカウントに保存されていたアクセストークンが削除され、アカウント連携は自動的に解除されます。
