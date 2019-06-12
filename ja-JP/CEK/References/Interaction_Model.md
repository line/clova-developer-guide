# 対話モデル {#InteractionModel}

[対話モデル](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)は、ユーザーのリクエストをサービスの提供に必要な標準形式(JSON)に変換するルールを定義したものです。

CEKでは、あらかじめ次の情報が定義されています。

* [ビルトインインテント](#BuiltinIntent)
* [ビルトインスロットタイプ](#BuiltinSlotType)

## ビルトインインテント {#BuiltinIntent}

ビルトインインテントは、Clovaプラットフォームが一部の共通したユーザーリクエストのカテゴリーを決め、それを共有するために宣言した仕様です。頻繁に発生するインテントとして、次のようなリクエストがあらかじめ定義されています。

| インテント             | 意図                                     | ユーザーのサンプル発話       |
| ---------------------- | ---------------------------------------- | ---------------------------- |
| `Clova.CancelIntent`   | 対話キャンセルのリクエスト               | キャンセル                   |
| `Clova.FallbackIntent` | 予想していない発話の入力を処理するリクエスト | (予想していない発話)     |
| `Clova.GuideIntent`    | ヘルプのリクエスト                       | 使い方を教えて               |
| `Clova.NextIntent`     | 次のコンテンツをリクエストする           | 次、次の曲を再生して         |
| `Clova.PauseIntent`    | 再生を一時停止するようにリクエストする   | ちょっと止めて、止めて       |
| `Clova.PreviousIntent` | 前のコンテンツをリクエストする           | 前、前の曲を再生して         |
| `Clova.ResumeIntent`   | 再生を再開するようにリクエストする       | 再生を再開して、再び再生して |
| `Clova.YesIntent`      | 肯定の返事(はい、Yes)                    | はい                         |
| `Clova.NoIntent`       | 否定の返事(いいえ、No)                   | いいえ                       |

ここでは次のビルトインインテントについて説明します。  
※ 説明は今後も追加される予定です。

* [`Clova.FallbackIntent`](#ClovaFallbackIntent)
* [`Clova.GuideIntent`](#ClovaGuideIntent)

### Clova.FallbackIntent {#ClovaFallbackIntent}

予想していない発話の入力を処理するリクエストです。`Clova.FallbackIntent`は選択項目で、必要に応じて実装します。

Extensionを開発する際は、Extensionとユーザーがどのような対話をするかをあらかじめ予想して対話モデルを設定します。しかしユーザーは、予想していない発話、つまり他のどのインテントとも一致しない発話をすることがあります。このような発話が入力された場合に分類されるのが`Clova.FallbackIntent`です。

`Clova.FallbackIntent`が選択されているとき、"ピザを注文するスキル"の場合は以下のような対話が考えられます。

| 発話の主体 | サンプル発話                                   |
| ---------- | ---------------------------------------------- |
| ユーザー   | ピザボットを起動して。                         |
| Extension  | ピザボットへようこそ。何を注文しますか?        |
| ユーザー   | 明日の天気はどう？<br>(この発話はピザボットのどのインテントとも一致しないため、Extensionに`Clova.FallbackIntent`を送信する) |
| Extension  | ピザボットはその質問にはお答えできませんが、おいしいピザを注文することができます。何を注文しますか？<br>(`Clova.FallbackIntent`を受けて、ユーザーに正しい発話をするように促すレスポンスを返す) |

なお、`Clova.FallbackIntent`を選択している場合と、選択していない場合では動作が異なります。

* **Clova.FallbackIntentを選択している場合**：予想していない発話は`Clova.FallbackIntent`に分類され、「使い方を教えて」というように明示的にヘルプをリクエストした場合は[`Clova.GuideIntent`](#ClovaGuideIntent)に分類されます。
* **Clova.FallbackIntentを選択していない場合**：予想していない発話と、ヘルプのリクエストは、いずれも[`Clova.GuideIntent`](#ClovaGuideIntent)に分類されます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>
    <ul>
    <li><code>Clova.FallbackIntent</code>はデフォルトでは選択されていません。使用する際は<strong>{{ book.DevConsole.cek_builder_header_title_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>を開き、<strong>{{ book.DevConsole.cek_builder_select_intent_builtin }}</strong>の右に表示された<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックして<strong>{{ book.DevConsole.cek_builder_header_title_interaction_model }}：ビルトインインテントを追加</strong>画面を開きます。チェックボックスにチェックを入れ、<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックすると有効になります。</li>
    <li><code>Clova.FallbackIntent</code>は選択項目のため、すでに作成済みのスキルに必ずしも追加する必要はありません。あとから<code>Clova.FallbackIntent</code>を追加した場合は、対話モデルを再度ビルドしてください。</li>
  </p>
</div>

#### 次の項目も参照してください。
* [`Clova.GuideIntent`](#ClovaGuideIntent)

### Clova.GuideIntent {#ClovaGuideIntent}

ヘルプのリクエストです。`Clova.GuideIntent`は実装必須の項目で、すべてのExtensionが対応する必要があります。

`Clova.GuideIntent`は、ユーザーが「使い方を教えて」「ヘルプ」等の発話をした場合に送信されます。Extensionは`Clova.GuideIntent`が含まれるリクエストメッセージを受け取ったら、使い方などを説明するように実装します。

なお、[`Clova.FallbackIntent`](#ClovaFallbackIntent)を選択している場合と、選択していない場合では動作が異なります。

* **[Clova.FallbackIntent](#ClovaFallbackIntent)を選択している場合**：予想していない発話は[`Clova.FallbackIntent`](#ClovaFallbackIntent)に分類され、「使い方を教えて」というように明示的にヘルプをリクエストした場合は`Clova.GuideIntent`に分類されます。
* **[Clova.FallbackIntent](#ClovaFallbackIntent)を選択していない場合**：予想していない発話と、ヘルプのリクエストは、いずれも`Clova.GuideIntent`に分類されます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p><code>Clova.GuideIntent</code>はデフォルトで選択されています。また、開発者が選択を解除することはできません。</p>
</div>

#### 次の項目も参照してください。
* [`Clova.FallbackIntent`](#ClovaFallbackIntent)

## ビルトインスロットタイプ {#BuiltinSlotType}

ビルトインスロットタイプは、あらかじめ定義されている情報のタイプで、主に時間、場所、数量などの定義を準備しています。Clovaでは、次のようなカテゴリーのビルトインスロットタイプを提供しています。

* [地域・都市名を取得する](#Location)
* [日時・時間を取得する](#Time)
* [数値を取得する](#Number)
* [単位を取得する](#Unit)
* [数値と単位を取得する](#NumberUnit)

### 地域・都市名を取得する {#Location}

国内の行政地域、世界の国名、世界の都市名を表現する次のようなビルトインスロットタイプを提供しています。

| ビルトインスロットタイプ | 説明                            | ユーザーのサンプル発話 |
| ------------------------ | ------------------------------- | ---------------------- |
| `CLOVA.JP_ADDRESS_KEN`   | 国内の行政地域のうち、都道府県名を提供します | "東京都"、"京都府"、"福岡県"、"北海道" |
| `CLOVA.JP_ADDRESS_SHI`   | 国内の行政地域のうち、市町村名を提供します   | "武蔵野市"、"奥多摩町"、"小笠原村"     |
| `CLOVA.JP_ADDRESS_KU`    | 国内の行政地域のうち、東京特別区（23区）名と行政区名を提供します | "新宿区"、"中村区"、"淀川区" |
| `CLOVA.WORLD_COUNTRY`    | 世界の国名に相当する表現を提供します         | "カナダ"、"日本"、"大韓民国"、"フランス" |
| `CLOVA.WORLD_CITY`       | 世界の都市名表現を提供します | "ワシントンD.C."、 "ローマ" |

### 日時・時間を取得する {#Time}

日付や時刻、期間、相対的な時間、順序、休日など、時間に関連するスロットタイプを提供しています。

| ビルトインスロットタイプ | 説明                            | ユーザーのサンプル発話 |
| ------------------------ | ------------------------------- | ---------------------- |
| `CLOVA.DATETIME`         | 日付や時刻表現を提供します。現在の日付またはそれより先の日時を返します。 | "1日"、"10分30秒"、"午前9時"、"1時間前"、"12時"、"正午"、"2017年8月4日" |
| `CLOVA.DATETIME_RECENT`  | 日付や時刻表現を提供します。現在の日付またはそれより前の日時を返します。 | "火曜日"、"7月29日"、"7月" |
| `CLOVA.DURATION`         | 期間の表現を提供します       | "1秒間"、"1分間"、"1時間"、"1週間"、"1日間"、"一ヶ月"、"1年間" |
| `CLOVA.OFFICIALDATE`     | 公休日を提供します           | "元日"、"成人の日"     |
| `CLOVA.ORDER`            | 順序表現を提供します         | "次"、"前"              |
| `CLOVA.RELATIVETIME`     | 相対的な時間表現を提供します | "これから"、"後で"、"しばらく後"、"今"、"さっき" |

ここでは次のビルトインスロットタイプの構成について説明します。  
※ 説明は今後も追加される予定です。

* [`CLOVA.DATETIME`](#ClovaDatetime)
* [`CLOVA.DATETIME_RECENT`](#ClovaDatetimeRecent)
* [`CLOVA.DURATION`](#ClovaDuration)

#### CLOVA.DATETIME {#ClovaDatetime}

日付や時刻の表現を[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)の拡張形式に変換して提供します。現在の日付またはそれより先の日時を返します。

「朝」「夕方」などの時間細分や季節の定義については、[備考](#Remarks)を参照してください。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>1つのインテントで<a href="#ClovaDatetime"><code>CLOVA.DATETIME</code></a>と<a href="#ClovaDatetimeRecent"><code>CLOVA.DATETIME_RECENT</code></a>を同時に使用することはできません。</p>
  <p>また、1つのExtensionの中で<a href="#ClovaDatetime"><code>CLOVA.DATETIME</code></a>と<a href="#ClovaDatetimeRecent"><code>CLOVA.DATETIME_RECENT</code></a>を同時に使用すると対話モデルの分析精度に影響を与えるため、同時使用は避けてください。</p>
</div>

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
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
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

//例7: 「火曜日」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2018-08-14",
    "valueType": "DATE"
  }
}

//例8: 「7月29日」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2019-07-29",
    "valueType": "DATE"
  }
}

//例9: 「7月」と発話した場合
"slots": {
  "TravelDate": {
    "name": "TravelDate",
    "value": "2019-07-01/2019-07-31",
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

##### 次の項目も参照してください。
* [`CLOVA.DATETIME_RECENT`](#ClovaDatetimeRecent)

#### CLOVA.DATETIME_RECENT {#ClovaDatetimeRecent}

日付や時刻の表現を[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)の拡張形式に変換して提供します。現在の日付またはそれより前の日時を返します。

各フィールドの構成は基本的に[`CLOVA.DATETIME`](#ClovaDatetime)と同じです。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>1つのインテントで<a href="#ClovaDatetime"><code>CLOVA.DATETIME</code></a>と<a href="#ClovaDatetimeRecent"><code>CLOVA.DATETIME_RECENT</code></a>を同時に使用することはできません。</p>
  <p>また、1つのExtensionの中で<a href="#ClovaDatetime"><code>CLOVA.DATETIME</code></a>と<a href="#ClovaDatetimeRecent"><code>CLOVA.DATETIME_RECENT</code></a>を同時に使用すると対話モデルの分析精度に影響を与えるため、同時利用は避けてください。</p>
</div>

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
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.DATETIME_RECENTスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)拡張形式に変換された日付・時刻 | <!-- --> |
| `slots.{slotName}.valueType` | string   | ユーザーのリクエストを解析した日付・時刻情報によって値が異なります。<ul><li>`TIME`：時刻</li><li>`DATE`：日付</li><li>`DATETIME`：日付と時刻</li><li>`TIME.INTERVAL`：時刻の範囲</li><li>`DATE.INTERVAL`：日付の範囲</li><li>`DATETIME.INTERVAL`：日時の範囲</li></ul> | <!-- --> |

##### Object example
※ 発話日付・時刻が「2018年8月10日（金）午前9時」、スロット名を"QuoteDate"と定義した場合
{% raw %}
```json
//例1: 「3時」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "03:00:00",
    "valueType": "TIME"
  }
}

//例2: 「2018年8月10日」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-08-10",
    "valueType": "DATE"
  }
}

//例3: 「2018年8月10日3時」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-08-10T03:00:00+09:00",
    "valueType": "DATETIME"
  }
}

//例4: 「朝」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "06:00:00/09:00:00",
    "valueType": "TIME.INTERVAL"
  }
}

//例5: 「秋」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2017-09-01/2017-11-30",
    "valueType": "DATE.INTERVAL"
  }
}

//例6: 「明日の昼」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-08-11T11:00:00+09:00/2018-08-09T13:00:00+09:00",
    "valueType": "DATE.INTERVAL"
  }
}

//例7: 「火曜日」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-08-07",
    "valueType": "DATE"
  }
}

//例8: 「7月29日」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-07-29",
    "valueType": "DATE"
  }
}

//例9: 「7月」と発話した場合
"slots": {
  "QuoteDate": {
    "name": "QuoteDate",
    "value": "2018-07-01/2018-07-31",
    "valueType": "DATE.INTERVAL"
  }
}
```
{% endraw %}

##### 次の項目も参照してください。
* [`CLOVA.DATETIME`](#ClovaDatetime)

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
| フィールド名             | データ型 | フィールドの説明 | Optional |
| ------------------------ | -------- | ---------------- | :------: |
| `slots`                  | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
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

### 数値を取得する {#Number}

数値を表現する次のスロットタイプ提供しています。

| ビルトインスロットタイプ | 説明              | ユーザーのサンプル発話 | 出力される値 |
| ------------------------ | ----------------- | ---------------------- |------------- |
| [`CLOVA.WHOLE_NUMBER`](#ClovaWholeNumber) | 0と正の整数、数字で構成された文字列の表現を提供します | 0123 4567<br>２３４５（全角数字）<br>五百六十七（漢数字） | 01234567<br>2345<br>567 |

対話モデルの[カスタムインテントを登録する](/CEK/Register_Extension.md#AddCustomIntent)際にスロットを指定するときは、次の図のようにサンプル発話の **数字** の部分を選択します。  
![](/CEK/Assets/Images/CEK_API_Interaction_Model_Clova_Unit_1.png)

ここでは次のビルトインスロットタイプの構成について説明します。  

* [`CLOVA.WHOLE_NUMBER`](#ClovaWholeNumber)

#### CLOVA.WHOLE_NUMBER {#ClovaWholeNumber}

`CLOVA.WHOLE_NUMBER`は、0および正の整数、数字で構成された文字列の表現を提供します。

なお、[`CLOVA.NUMBER`](#ClovaNumber)を使用すると、`CLOVA.WHOLE_NUMBER`の表現に加えて、負の数値や小数を表現することができます。必要に応じて`CLOVA.WHOLE_NUMBER`と[`CLOVA.NUMBER`](#ClovaNumber)を使い分けてください。

##### Object structure
{% raw %}
```json
"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}}
    }
}
```
{% endraw %}

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.WHOLE_NUMBERスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | 数値 | <!-- --> |

##### Object example
※ スロット名を"streetAddress"と定義した場合
{% raw %}
```json
//例: 「五百六十七（ごひゃくろくじゅうなな）」と発話した場合
"slots": {
    "streetAddress":{
        "name": "streetAddress",
        "value": "567"
    }
}
```
{% endraw %}

##### 次の項目も参照してください。
* [`CLOVA.NUMBER`](#ClovaNumber)

### 単位を取得する {#Unit}

各種の単位を表現する次のようなビルトインスロットタイプを提供しています。

| ビルトインスロットタイプ | 説明              | ユーザーのサンプル発話 | 出力される値 |
| ------------------------ | ----------------- | ---------------------- |------------- |
| [`CLOVA.UNIT`](#ClovaUnit) | `CLOVA.UNIT_XXXX`の単位表現をすべて含む | 5冊 | 冊 |
| `CLOVA.UNIT_GENERAL` | 一般な助数詞（単位）を提供します<br>（例：個、枚、本、台、体、回、件、軒、つ、号、冊、杯、カップ、人、匹、頭、階、歳、才、食、席、位、箱、袋、ケース、缶） | 3個 | 個 |
| `CLOVA.UNIT_AREA` | 面積を表す単位を提供します | 30平方メートル | 平方メートル |
| [`CLOVA.UNIT_CURRENCY`](#ClovaUnitCurrency) | [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)の通貨名コードを提供します | 30000ユーロ | EUR |
| `CLOVA.UNIT_INFORMATION` | データの単位を提供します | 16bit | ビット |
| `CLOVA.UNIT_LENGTH` | 長さ・距離を表す単位を提供します | 35マイル | マイル |
| `CLOVA.UNIT_RATIO` | 割合・比率を表す単位を提供します | 13％ | パーセント |
| `CLOVA.UNIT_SPEED` | 速度を表す単位を提供します | 30メートル毎秒 | メートル毎秒 |
| `CLOVA.UNIT_TEMPERATURE` | 温度を表す単位を提供します | 18℃ | 度 |
| `CLOVA.UNIT_VOLUME` | 体積・容積を表す単位を提供します | 50ミリリットル | ミリリットル |
| `CLOVA.UNIT_WEIGHT` | 重量を表す単位を提供します | 12キログラム | キログラム |

対話モデルの[カスタムインテントを登録する](/CEK/Register_Extension.md#AddCustomIntent)際にスロットを指定するときは、次の図のようにサンプル発話の **単位** の部分を選択します。  
![](/CEK/Assets/Images/CEK_API_Interaction_Model_Clova_Unit_3.png)

ここでは次のビルトインスロットタイプの構成について説明します。  
※ 説明は今後も追加される予定です。

* [`CLOVA.UNIT`](#ClovaUnit)
* [`CLOVA.UNIT_CURRENCY`](#ClovaUnitCurrency)

#### CLOVA.UNIT {#ClovaUnit}

`CLOVA.UNIT`は、`CLOVA.UNIT_`で始まるスロットタイプ名で取り扱うすべての単位表現を提供します。ユーザーがどの単位表現を発話するかをあらかじめ限定しない場合は、`CLOVA.UNIT`を使用します。

また、「50キロ」という発話に対して、**距離** と **重量** のどちらを示すのかを明確にする必要がある場合は、`CLOVA.UNIT_WEIGHT`や`CLOVA.UNIT_LENGTH`を使用してください。

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.UNITスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | 単位に相当する文字列 | <!-- --> |

##### Object structure
{% raw %}
```json

"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}}
    }
}
```
{% endraw %}

##### Object example
※ スロット名を"sidedishAmount"と定義した場合
{% raw %}
```json
//例1: 「2箱」と発話した場合
"slots": {
    "sidedishAmount":{
        "name": "sidedishAmount",
        "value": "箱"
    }
}

//例2: 「5本」と発話した場合
"slots": {
    "sidedishAmount":{
        "name": "sidedishAmount",
        "value": "本"
    }
}
```
{% endraw %}

<div class="note">
  <p><strong>メモ</strong></p>
  <p>従来の<code>CLOVA.UNIT</code>は数値と単位の組み合わせを提供していましたが、改修にともなって<strong>単位のみ</strong>を提供するように仕様が変更されました。</p>
  <p>そのため、すでに作成済みのExtensionで<code>CLOVA.UNIT</code>を使用していた場合は、対話モデルの設定を変更して再ビルドする必要があります。詳細については<a href="https://clova-developers.line.biz/#/updatehistory/" target="_blank">こちら</a>を参照してください。</p>
</div>

#### CLOVA.UNIT_CURRENCY {#ClovaUnitCurrency}

`CLOVA.UNIT_CURRENCY`は、通貨単位を表す発話を、[ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)の通貨名コードに変換します。

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.UNIT_CURRENCYスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)の通貨名コード | <!-- --> |

##### Object structure
{% raw %}
```json

"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}}
    }
}
```
{% endraw %}

##### Object example
※ スロット名を"roomCharge"と定義した場合
{% raw %}
```json
//例: 「60000ウォン」と発話した場合
"slots": {
    "roomCharge":{
        "name": "roomCharge",
        "value": "KRW"
    }
}
```
{% endraw %}

<div class="note">
  <p><strong>メモ</strong></p>
  <p>従来の<code>CLOVA.CURRENCY</code>が廃止され、<a href="#ClovaUnitCurrency"><code>CLOVA.UNIT_CURRENCY</code></a>に名称変更されました。仕様の変更はありません。</p>
  <p>なお、すでに作成済みのExtensionで<code>CLOVA.CURRENCY</code>を使用していた場合は、システムの内部で自動的に<code>CLOVA.UNIT_CURRENCY</code>に名称が変換されるため、対話モデルを再ビルドする必要があります。</p>
  <p>詳細については<a href="https://clova-developers.line.biz/#/updatehistory/" target="_blank">こちら</a>を参照してください。</p>
</div>

### 数値と単位を取得する {#NumberUnit}

数値と単位の組み合わせによる表現について、次のようなビルトインスロットタイプを提供しています。

| ビルトインスロットタイプ | 説明              | ユーザーのサンプル発話 | 出力される値 |
| ------------------------ | ----------------- | ---------------------- |------------- |
| [`CLOVA.NUMBER`](#ClovaNumber) | 数値<br>または<br>数値 + 単位 | 1234個 | ※ スロットの選択範囲によって異なる<br><ul><li>"1234"個と選択した場合：value = "1234"</li><li>"1234個"と選択した場合：value = "1234", unit="個"</li><ul> |
| [`CLOVA.GENERIC_NUMBER`](#ClovaGenericNumber) | 数値 + `CLOVA.UNIT_GENERAL` | 三杯 | value="3", unit="杯" |
| `CLOVA.AREA` | 数値 + `CLOVA.UNIT_AREA` | 20坪 | value="20" unit="坪" |
| `CLOVA.INFORMATION` | 数値 + `CLOVA.UNIT_INFORMATION` | 6ギガバイト | value="6", unit="ギガバイト" |
| `CLOVA.LENGTH` | 数値 + `CLOVA.UNIT_LENGTH` | 2.2キロメートル | value="2.2", unit="キロメートル" |
| [`CLOVA.MONEY`](#ClovaMoney) | 数値 + `CLOVA.UNIT_CURRENCY` | 88円 | value="88", unit="JPY" |
| `CLOVA.RATIO` | 数値 + `CLOVA.UNIT_RATIO` | 100倍	 | 	value="100", unit="倍" |
| `CLOVA.SPEED` | 数値 + `CLOVA.UNIT_SPEED` | 75キロメートル毎時<br>分速800メートル | value="75", unit="キロメートル毎時"<br>value="800", unit="メートル毎分" |
| `CLOVA.VOLUME` | 数値 + `CLOVA.UNIT_VOLUME` | 5リットル | value="5", unit="リットル" |
| `CLOVA.WEIGHT` | 数値 + `CLOVA.UNIT_WEIGHT` | 30mg | value="30", unit="ミリグラム" |
| `CLOVA.TEMPERATURE` | 数値 + `CLOVA.UNIT_TEMPERATUR` | 36.5℃ | value="36.5", unit="度" |

対話モデルの[カスタムインテントを登録する](/CEK/Register_Extension.md#AddCustomIntent)際にスロットを指定するときは、次の図のようにサンプル発話の **数字と単位** をまとめて選択します（[`CLOVA.NUMBER`](#ClovaNumber)のみ選択のやり方に例外があります）。  
![](/CEK/Assets/Images/CEK_API_Interaction_Model_Clova_Unit_2.png)

ここでは次のビルトインスロットタイプの構成について説明します。  
※ 説明は今後も追加される予定です。

* [`CLOVA.NUMBER`](#ClovaNumber)
* [`CLOVA.GENERIC_NUMBER`](#ClovaGenericNumber)
* [`CLOVA.MONEY`](#ClovaMoney)

#### CLOVA.NUMBER {#ClovaNumber}

`CLOVA.NUMBER`は、数値と単位の組み合わせによる発話を、**数値のみ**、または **数値と単位** に変換します。数値については、0および正の整数のほか、負の数値や小数を表現することができます。

対話モデルの[カスタムインテントを登録する](/CEK/Register_Extension.md#AddCustomIntent)際に、サンプル発話のどの部分をスロットとして処理するかをドラッグして選択する必要があります。`CLOVA.NUMBER`の場合は、このときに選択する範囲によって取得する値が異なります。

例えば、「ペパロニピザを2枚注文して」というサンプル発話について、**"2"** という数字部分のみを選択した場合は、数値だけが出力されます。  
![](/CEK/Assets/Images/CEK_API_Interaction_Model_Clova_Unit_1.png)

**"2枚"** のように数値と単位をまとめて選択した場合は、数値と単位がそれぞれ出力されます。  
![](/CEK/Assets/Images/CEK_API_Interaction_Model_Clova_Unit_2.png)

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.NUMBERスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | 数値 | <!-- --> |
| `slots.{slotName}.unit`      | string   | 単位に相当する文字列。スロットとして数字部分のみを選択した場合は出力されません。 | Optional |

##### Object structure
{% raw %}
```json
"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}}
    }
}

or

"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}},
        "unit": {{string}}
    }
}
```
{% endraw %}

##### Object example
※ スロット名を"pizzaAmount"と定義し、「2枚」と発話した場合
{% raw %}
```json
//例1: スロットの選択範囲を"2"とした場合
"slots": {
    "pizzaAmount":{
        "name": "pizzaAmount",
        "value": "2"
    }
}

//例2: スロットの選択範囲を"2枚"とした場合
"slots": {
    "pizzaAmount":{
        "name": "pizzaAmount",
        "value": "2",
        "unit": "枚"
    }
}
```
{% endraw %}

<div class="note">
  <p><strong>メモ</strong></p>
  <p>従来の<code>CLOVA.NUMBER</code>は<strong>数値のみ</strong>を提供していましたが、改修にともなって<strong>数値のみ</strong>、または<strong>数値と単位</strong>を提供するように仕様が変更されました。</p>
  <p>そのため、すでに作成済みのExtensionで<code>CLOVA.NUMBER</code>を使用していた場合は、対話モデルの設定を変更して再ビルドする必要があります。詳細については<a href="https://clova-developers.line.biz/#/updatehistory/" target="_blank">こちら</a>を参照してください。</p>
</div>

#### CLOVA.GENERIC_NUMBER {#ClovaGenericNumber}

`CLOVA.GENERIC_NUMBER`は、数値と一般的な単位の組み合わせによる発話を、数値と単位に変換します。

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.NUMBERスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | 数値 | <!-- --> |
| `slots.{slotName}.unit`      | string   | 単位に相当する文字列 | <!-- --> |

##### Object structure
{% raw %}
```json
"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}},
        "unit": {{string}}
    }
}
```
{% endraw %}

##### Object example
※ スロット名を"sidedishAmount"と定義した場合
{% raw %}
```json
//例1: 「2箱」と発話した場合
"slots": {
    "sidedishAmount":{
        "name": "sidedishAmount",
        "value": "2",
        "unit": "箱"
    }
}

//例2: 「5本」と発話した場合
"slots": {
    "sidedishAmount":{
        "name": "sidedishAmount",
        "value": "5",
        "unit": "本"
    }
}
```
{% endraw %}


#### CLOVA.MONEY {#ClovaMoney}

`CLOVA.MONEY`は、数値と通貨名の組み合わせによる発話を、数値と[ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)の通貨名コードに変換します。  

##### Object fields
| フィールド名                 | データ型 | フィールドの説明 | Optional |
| ---------------------------- | -------- | ---------------- | :------: |
| `slots`                      | object   | Extensionがインテントを処理する際に要求される情報(スロット)が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}`           | object   | CLOVA.NUMBERスロットの情報が保存されたオブジェクト | <!-- --> |
| `slots.{slotName}.name`      | string   | 開発者が定義したスロット名 | <!-- --> |
| `slots.{slotName}.value`     | string   | 数値 | <!-- --> |
| `slots.{slotName}.unit`      | string   | [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)の通貨名コード | <!-- --> |

##### Object structure
{% raw %}
```json
"slots": {
    {{string}}:{
        "name": {{string}},
        "value": {{string}},
        "unit": {{string}}
    }
}
```
{% endraw %}

##### Object example
※ スロット名を"roomCharge"と定義した場合
{% raw %}
```json
//例1: 「1万円」と発話した場合
"slots": {
    "roomCharge":{
        "name": "roomCharge",
        "value": "10000",
        "unit": "JPY"
    }
}

//例2: 「200ユーロ」と発話した場合
"slots": {
    "roomCharge":{
        "name": "roomCharge",
        "value": "200",
        "unit": "EUR"
    }
}
```
{% endraw %}

<div class="note">
  <p><strong>メモ</strong></p>
  <p>従来の<code>CLOVA.MONEY</code>は<strong>数値のみ</strong>を提供していましたが、改修にともなって<strong>数値</strong>と<strong>単位</strong>を分けて出力するように仕様が変更されました。</p>
  <p>そのため、すでに作成済みのExtensionで<code>CLOVA.MONEY</code>を使用していた場合は、対話モデルの設定を変更して再ビルドする必要があります。詳細については<a href="https://clova-developers.line.biz/#/updatehistory/" target="_blank">こちら</a>を参照してください。</p>
</div>
