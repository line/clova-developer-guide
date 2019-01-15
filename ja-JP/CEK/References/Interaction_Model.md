## 対話モデル {#InteractionModel}

[対話モデル](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)は、ユーザーのリクエストをサービスの提供に必要な標準形式(JSON)に変換するルールを定義したものです。

CEKでは、あらかじめ次の情報が定義されています。

* [ビルトインインテント](#BuiltinIntent)
* [ビルトインスロットタイプ](#BuiltinSlotType)

### ビルトインインテント {#BuiltinIntent}

ビルトインインテントは、Clovaプラットフォームが一部の共通したユーザーリクエストのカテゴリーを決め、それを共有するために宣言した仕様です。頻繁に発生するインテントとして、次のようなリクエストがあらかじめ定義されています。

| インテント           | 意図                       | ユーザーのサンプル発話 |
| -------------------- | -------------------------- | ---------------------- |
| `Clova.CancelIntent` | 対話キャンセルのリクエスト | キャンセル             |
| `Clova.GuideIntent`  | ヘルプのリクエスト         | 使い方を教えて         |
| `Clova.YesIntent`    | 肯定の返事(はい、Yes)      | はい                   |
| `Clova.NoIntent`     | 否定の返事(いいえ、No)     | いいえ                 |

### ビルトインスロットタイプ {#BuiltinSlotType}

ビルトインスロットタイプは、あらかじめ定義されている情報のタイプで、主に時間、場所、数量などの定義を準備しています。Clovaでは、次のようなビルトインスロットタイプを提供しています。

| ビルトインスロットタイプ | 説明                                              |
| ------------------------ | ------------------------------------------------- |
| `CLOVA.DATETIME`         | 日付や時刻表現を提供します。(例："1日"、"10分30秒"、"午前9時"、"1時間前"、"12時"、"正午"、"2017年8月4日") |
| `CLOVA.DURATION`         | 期間の表現を提供します。(例："1秒間"、"1分間"、"1時間"、"1週間"、"1日間"、"一ヶ月"、"1年間") |
| `CLOVA.MONEY`            | 数字+通貨単位を提供します。(例:"四千円"、"1ドル") |
| `CLOVA.NUMBER`           | 数字表現を提供します。(例:"7"人、"一"つ、"30"歳、"8"個) |
| `CLOVA.RELATIVETIME`     | 相対的な時間表現を提供します。(例:"これから"、"後で"、"しばらく後"、"今"、"さっき") |
| `CLOVA.UNIT`             | 数字＋助数詞表現を提供します。(例: "113坪"、"100メガ"、"25マイル") |
| `CLOVA.ORDER`            | 順序表現を提供します。(例:"次"、"前")             |
| `CLOVA.JP_ADDRESS_KEN`   | 国内の行政地域のうち、都道府県名を提供します。(例:"東京都"、"京都府"、"福岡県"、"北海道") |
| `CLOVA.JP_ADDRESS_SHI`   | 国内の行政地域のうち、市町村名を提供します。(例:"武蔵野市"、"奥多摩町"、"小笠原村") |
| `CLOVA.JP_ADDRESS_KU`    | 国内の行政地域のうち、東京特別区（23区）名と行政区名を提供します。(例:"新宿区"、"中村区"、"淀川区") |
| `CLOVA.WORLD_COUNTRY`    | 世界の国名に相当する表現を提供します。(例:"カナダ"、"日本"、"大韓民国"、"フランス") |
| `CLOVA.WORLD_CITY`       | 世界の都市名表現を提供します。(例:"ワシントンD.C."、 "ローマ") |
| `CLOVA.CURRENCY`         | 通貨単位を提供します。(例:"円"、"ドル")           |
| `CLOVA.OFFICIALDATE`     | 公休日を提供します。(例:"元日"、"成人の日")       |

ここでは次のビルトインスロットタイプの構成について説明します。  
※ 説明は今後も追加される予定です。

* [`CLOVA.DATETIME`](#ClovaDatetime)
* [`CLOVA.DURATION`](#ClovaDuration)


#### CLOVA.DATETIME {#ClovaDatetime}

日付や時刻の表現を[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)の拡張形式に変換して提供します。現在の日付またはそれより先の日時を返します。
「朝」「夕方」などの時間細分や季節の定義については、[備考](#Remarks)を参照してください。

##### Object structure
{% raw %}
```json
"slots": {
  {{slotName}}:{
    "name": {{slotName}},
    "value": {{string}},
    "valueType": {{string}}
  }
}
```
{% endraw %}

##### Object fields
| フィールド名           | データ型 | フィールドの説明 | Optional |
| ---------------------- | -------- | ---------------- | :------: |
| `slots`                | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.DATETIMEスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)拡張形式に変換された日付・時刻 | <!-- --> |
| `slots.{slotName}.valueType` | string   | ユーザーのリクエストを解析した日付・時刻情報によって値が異なります。<ul><li>`TIME`：時刻</li><li>`DATE`：日付</li><li>`DATETIME`：日付と時刻</li><li>`TIME.INTERVAL`：時刻の範囲</li><li>`DATE.INTERVAL`：日付の範囲</li><li>`DATETIME.INTERVAL`：日時の範囲</li></ul> | <!-- --> |

##### Object example
※ 発話日付・時刻が「2018年8月10日（金）午前9時」、スロット名を"TravelDate"と定義した場合
{% raw %}
```json
//例1: 「3時」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "03:00:00",
    "valueType": "TIME"
  }
}

//例2: 「2018年8月10日」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2018-08-10",
    "valueType": "DATE"
  }
}

//例3: 「2018年8月10日3時」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2018-08-10T03:00:00+09:00",
    "valueType": "DATETIME"
  }
}

//例4: 「朝」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "06:00:00/09:00:00",
    "valueType": "TIME.INTERVAL"
  }
}

//例5: 「秋」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2018-09-01/2018-11-30",
    "valueType": "DATE.INTERVAL"
  }
}

//例6: 「明日の昼」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2018-08-11T11:00:00+09:00/2018-08-09T13:00:00+09:00",
    "valueType": "DATE.INTERVAL"
  }
}
```
{% endraw %}

##### 備考 {#Remarks}

**時間細分の定義**

| 時間細分 | 期間の表現       | 開始時間 | 終了時間 |
| -------- | ---------------- | -------- | -------- |
| 未明     | 未明、深夜       | 00:00:00 | 03:00:00 |
| 明け方   | 明け方           | 03:00:00 | 06:00:00 |
| 朝       | 朝               | 06:00:00 | 09:00:00 |
| 昼前     | 昼前、お昼前     | 09:00:00 | 12:00:00 |
| 昼       | 昼、お昼、昼頃   | 11:00:00 | 13:00:00 |
| 昼過ぎ   | 昼過ぎ、お昼過ぎ | 12:00:00 | 15:00:00 |
| 夕方     | 夕方             | 15:00:00 | 18:00:00 |
| 午前     | 午前             | 00:00:00 | 12:00:00 |
| 午後     | 午後             | 12:00:00 | 24:00:00 |
| 日中     | 日中             | 09:00:00 | 18:00:00 |
| 夜       | 夜、晩           | 18:00:00 | 24:00:00 |

**季節の定義**

| 季節の表現 | 開始日付 | 終了日付  |
| ---------- | -------- | --------- |
| 春         | 3月1日   | 5月31日   |
| 夏         | 6月1日   | 8月31日   |
| 秋         | 9月1日   | 11月30日  |
| 冬         | 12月1日  | 2月28日 ※ |

※ 閏年の場合は2月29日

#### CLOVA.DURATION {#ClovaDuration}

`CLOVA.DURATION`は、継続時間を表す発話を、[ISO 8601 Duration](https://en.wikipedia.org/wiki/ISO_8601#Durations)形式の値に変換します。

* ISO 8601 Duration：PnYnMnDTnHnMnS

各値の意味は以下のとおりです。

|            | 説明                                                 | 例    | 意味    |
| ---------- | ---------------------------------------------------- | ----- | ------- |
| P          | 期間であることを示し、継続時間表現の先頭に置かれます |       |<!-- --> |
| Y          | 年を示します                                         | P3Y   | 3年間   |
| M（T以前） | 月を示します                                         | P5M   | 5ヶ月間 |
| D          | 日を示します                                         | P10D  | 10日間  |
| T          | それ以後の値が時間要素であることを示します           | PT23M | 23分間  |
| H          | 時間を示します                                       | PT12H | 12時間  |
| M（T以後） | 分を示します                                         | PT5M  | 5分間   |
| S          | 秒を示します                                         | PT34S | 34秒間  |

##### Object structure
{% raw %}
```json
"slots": {
  "slotName": {
    "name": {{slotName}},
    "value": {{string}}
  }
}
```
{% endraw %}

##### Object fields
| フィールド名           | データ型 | フィールドの説明 | Optional |
| ---------------------- | -------- | ---------------- | :------: |
| `slots`                | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`       | object   | CLOVA.DURATIONスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`  | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value` | string   | [ISO 8601 Duration](https://en.wikipedia.org/wiki/ISO_8601#Durations)形式に変換した値 | <!-- --> |

##### Object example
※ スロット名を"TravelPeriod"と定義した場合
{% raw %}
```json
//例1: 「5日間」と発話した場合
"slots": {
  "TravelPeriod": {
    "name": "TravelPeriod",
    "value": "P5D"
  }
}

//例2: 「34分間」と発話した場合
"slots": {
  "TravelPeriod": {
    "name": "TravelPeriod",
    "value": "PT34M"
  }
}

//例3: 「2時間5分25秒」と発話した場合
"slots": {
  "TravelPeriod": {
    "name": "TravelPeriod",
    "value": "PT2H5M25S"
  }
}
```
{% endraw %}
