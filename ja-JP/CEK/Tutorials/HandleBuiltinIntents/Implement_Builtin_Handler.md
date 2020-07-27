サンプルサイコロExtensionがビルトインインテントを処理できるように、コードを変更する必要があります。

ここでは、基本的な処理方法を説明するために、「ガイド」ビルトインインテントのみ扱います。
「ガイド」ビルトインインテントは、ユーザーが「使い方を教えて」「ヘルプ」のようなフレーズを発する際に送信され、`Clova.GuideIntent`という名前を使用します。

このビルトインインテントを処理するために、以下のように[1番目のチュートリアル](/CEK/Tutorials/Build_Simple_Extension.md)のリポジトリを再使用します。
次のようにローカルリポジトリにアクセスして、`tutorial2`ブランチに切り替えます。

{% raw %}
```bash
cd /path/to/your_sample_dice_directory
git fetch
git checkout tutorial2
```
{% endraw %}

サンプルサイコロExtensionは、`clova/index.js`ファイルの`intentRequest()`でヘルプのリクエストを処理します。

{% raw %}
```javascript
intentRequest(cekResponse) {
  const intent = this.request.intent.name

  switch (intent) {
    ...
    case 'Clova.GuideIntent':
    default:
      cekResponse.setSimpleSpeechText('サイコロを1つ振って、と言ってみてください。')
  }
  ...
}
```
{% endraw %}

上記のコードのように、CLOVAからのリクエストメッセージからインテントを抽出し、その名前が`Clova.GuideIntent`の場合、「サイコロを1つ振って」と話すように案内します。

