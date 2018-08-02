# このドキュメントについて
このドキュメントは、ClovaのCICとCEKプラットフォームの開発ガイドおよびAPIリファレンスを提供します。対象となる読者は、CICを使用してClovaのサービスと連携するデバイスまたはアプリを開発するクライアント開発者と、CEKを使用したオンラインコンテンツおよびサービスの提供を希望するExtension開発者です。

LINE株式会社（以下、当社といいます）は、Clova事務局としてスキルの審査やスキルストアの運営を行います。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Clovaは、現在も開発が進められています。このドキュメントの内容は随時変更される可能性があります。</p>
</div>

## お問い合わせ
ドキュメントの内容に関するお問い合わせは、指定のClova提携担当者までお願いします。

## ドキュメントのバージョンおよび変更履歴

このドキュメントのバージョンは{{ book.DocVersion }}で、変更履歴は次のとおりです。

<table>
  <thead>
    <tr>
      <th style="width:10%">バージョン</th><th style="width:15%">配布日時</th><th style="width:75%">履歴</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>v1.1.4</td><td>2018/08/02</td>
    <td>
      <ul>
        <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md#InputDeploymentInfo">配布情報を入力する</a> 更新（検索キーワードについての説明を追加、スキルストアの画像を更新）</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>v1.1.3</td><td>2018/07/27</td>
    <td>
      <ul>
        <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Kotlin">CEK SDK for Kotlin</a> 追加）</li>
        <li><a href="/Design/Design_Guideline_For_Extension.md#InvocationNameRequirement" target="_blank">スキル名/呼び出し名の要件</a> 更新（Clovaの呼び名を「ねぇClova」に統一）</li>
        <li><a href="/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo" target="_blank">Extensionの基本情報を入力する</a> 更新（「提供者について」の説明を追加）</li>
        <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md#InputDeploymentInfo" target="_blank">配布情報を入力する</a> 更新（「代表サンプル発話」の入力例を追加）</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>v1.1.2</td><td>2018/07/26</td>
    <td>
      <ul>
        <li>Clova WAVEのCustom Extension対応開始</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>v1.1.1</td><td>2018/07/25</td>
    <td>
      <ul>
        <li><a href="/CEK/Guides/Register_Collaborator.md">複数のユーザーでExtensionの編集・テストを行う</a> 更新（<a href="/CEK/Guides/Register_Collaborator.md#RemoveAdminRight">Admin権限を削除する</a> 追加）</li>
        <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Elixir">CEK SDK for Elixir</a> 追加）</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>v1.1.0</td><td>2018/07/19</td>
    <td>
      <ul>
        <li><a href="/CEK/Guides/Register_Collaborator.md">複数のユーザーでExtensionの編集・テストを行う</a> 追加</li>
        <li><a href="/CEK/Examples/Extension_Examples.md">サンプルのExtension</a> 追加</li>
        <li><a href="/DevConsole/Guides/CEK/Update_Extension.md">Extensionをアップデートする</a> 追加</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>v1.0.0</td><td>2018/07/12</td>
    <td>
      <ul>
        <li>初版リリース</li>
      </ul>
    </td>
  </tr>
  </tbody>
</table>
