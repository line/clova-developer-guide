# サンプルのExtension

Clovaでサービス提供中の一部のExtensionを紹介します。簡単なアクションを行うExtensionで、Extensionを開発する際に役立ちます。

* [サイコロ遊び(Dice drawer)](#DiceDrawer)

## サイコロ遊び(Dice drawer) {#DiceDrawer}

サイコロ遊びは、ユーザーのリクエストに対し、仮想のサイコロを振って、出目の合計を返すExtensionです。

### 特徴
* ユーザーはサイコロを何個振るか選択できます。このExtensionの対話モデルには、サイコロの数に該当する値がスロットとして定義されています。
* 振るサイコロの数が1つか、または2つ以上かによって応答として返す表現が異なります。
* Node.jsで実装されています。

### GitHubリポジトリ
[{{ book.GitHubBaseURLforExtensionExample }}/clova-extension-sample-dice]({{ book.GitHubBaseURLforExtensionExample }}/clova-extension-sample-dice)


