# 汎用的な意図を処理する
このチュートリアルでは、[簡単なExtensionを作成する](/CEK/Tutorials/Build_Simple_Extension.md)で作成したサンプルサイコロExtensionを利用して、「はい」「いいえ」などの汎用的な意図の表現を処理する方法について説明します。

CLOVAは、頻繁に発生するユーザーの基本的な意図表現をすべてのExtensionで共通で使用できるように、[ビルトインインテント](/Design/Design_Guideline_For_Extension.md#BuiltinIntent)としてあらかじめ定義しています。以下は、CLOVAが提供するビルトインインテントの一覧です。

| ビルトインインテントの名前 | 意図                                     | ユーザーのサンプル発話       |
| -------------------------- | ---------------------------------------- | ---------------------------- |
| Clova.CancelIntent         | 対話キャンセルのリクエスト               | キャンセル                   |
| Clova.FallbackIntent       | 予想していない発話の入力を処理するリクエスト | (予想していない発話)     |
| Clova.GuideIntent          | ヘルプのリクエスト                       | 使い方を教えて               |
| Clova.NextIntent           | 次のコンテンツをリクエストする           | 次、次の曲を再生して         |
| Clova.PauseIntent          | 再生を一時停止するようにリクエストする   | ちょっと止めて、止めて       |
| Clova.PreviousIntent       | 前のコンテンツをリクエストする           | 前、前の曲を再生して         |
| Clova.ResumeIntent         | 再生を再開するようにリクエストする       | 再生を再開して、再び再生して |
| Clova.YesIntent            | 肯定の返事(はい、Yes)                    | はい                         |
| Clova.NoIntent             | 否定の返事(いいえ、No)                   | いいえ                       |

ユーザーがヘルプや実行のキャンセルをリクエストするとき、そのリクエストを処理するために、上記の表にあるビルトインインテントを使用することができます。ビルトインインテントは名前の通り元々設定されているため、1番目のチュートリアルで行ったようにインテントやサンプル発話を登録する必要はありません。

ビルトインインテントを処理するためには、次の作業が必要です。
* ステップ1 ビルトインインテントの処理を実装する(Extensionサーバーで作業)
* ステップ2 ビルトインインテントの動作をテストする(CLOVA Developer Centerで作業)

## ステップ1 ビルトインインテントの処理を実装する {#Step1}
{% include "/CEK/Tutorials/HandleBuiltinIntents/Implement_Builtin_Handler.md" %}

## ステップ2 ビルトインインテントの動作をテストする {#Step2}
{% include "/CEK/Tutorials/HandleBuiltinIntents/Test_Builtin_Intent.md" %}

こうすることで、サンプルサイコロExtensionが、ヘルプのリクエストに応答できるようになります。
このようにExtensionサーバーが`Clova.CancelIntent`、`Clova.YesIntent`、`Clova.NoIntent`を処理するように実装すると、実行のキャンセル、肯定または否定を表すリクエストにも応答できます。
