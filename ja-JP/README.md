# このドキュメントについて
このドキュメントは、ClovaのCEKプラットフォームの開発ガイドおよびAPIリファレンスを提供します。対象となる読者は、CICを使用してClovaのサービスと連携するデバイスまたはアプリを開発するクライアント開発者と、CEKを使用したオンラインコンテンツおよびサービスの提供を希望するExtension開発者です。

LINE株式会社（以下、当社といいます）は、Clova事務局としてスキルの審査やスキルストアの運営を行います。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Clovaは、現在も開発が進められています。このドキュメントの内容は随時変更される可能性があります。</p>
</div>

## お問い合わせ
このドキュメントに関するお問い合わせや開発時のご質問の際にはこちらをご利用ください。
Clovaの質問には`Clova`や`CEK`のタグをご利用ください。
<a href="https://www.line-community.me/questions" target="_blank">LINE developers community > Q&A</a>

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
      <td>v3.1.5</td><td>2019/08/15</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home Extensionを作成する</a> 更新（<a href="/CEK/Guides/Build_Clova_Home_Extension.md#ProvideSceneDiscovery">SceneDiscovery機能を提供する</a> 追加）</li>
          <li><a href="/CEK/References/CEK_API_ClovaHome.md">Clova Home Extension APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#discovery">Discovery</a> 更新</li>
            <ul>
              <li><a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesRequest">DiscoverScenesRequest</a> 追加</li>
              <li><a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverScenesResponse">DiscoverScenesResponse</a> 追加</li>
            </ul>
          </ul>
          <ul>
            <li><a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control</a> 更新</li>
            <ul>
              <li><a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ActionSceneConfirmation">ActionSceneConfirmation</a> 追加</li>
              <li><a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ActionSceneRequest">ActionSceneRequest</a> 追加</li>
            </ul>
          </ul>
          <ul>
            <li><a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">共有オブジェクト</a> 更新</li>
            <ul>
              <li><a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#SceneInfoObject">SceneInfoObject </a> 追加</li>
            </ul>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.4</td><td>2019/07/19</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Link_Messaging_API.md">Custom ExtensionとLINEを連携する</a> 更新（LINE公式アカウントの設定例を追加）</li>
          <li><a href="/CEK/References/CEK_API_ClovaHome.md">Clova Home Extension APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">共有オブジェクト</a> 更新</li>
            <ul>
              <li><a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a> 更新（WATERBOILERの運転モードに"washing" 追加）</li>
              <li><a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a> 更新（actionsNeededUserConfirmationの説明を追加）</li>
            </ul>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.3</td><td>2019/06/12</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a> 更新</li>
          <ul>
            <li><a href="/Design/Design_Guideline_For_Extension.md#BuiltinSlotType">ビルトインスロットタイプ</a> 更新（新規ビルトインスロットタイプ 追加）</li>
            <li><a href="/Design/Design_Guideline_For_Extension.md#DecideSoundOutputType">応答タイプを決める</a> 更新（音源のリソースに関する注意を追加）</li>
          </ul>
          <li><a href="/CEK/Tutorials/Introduction.md">チュートリアル</a> 更新（LINE Developersの<a href="https://developers.line.biz/ja/docs/clova-extensions-kit/" target="_blank">Clova Extensions Kitチュートリアル</a>へのリンクを追加）</li>
          <li><a href="/CEK/Guides/Build_Custom_Extension.md">Custom Extensionを作成する</a> 更新（<a href="/CEK/Guides/Build_Custom_Extension.md#ProvideAudioContent">オーディオコンテンツを提供する</a>に音源のリソースに関する注意を追加）</li>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#BuiltinSlotType">ビルトインスロットタイプ</a> 更新</li>
            <ul>
              <li><a href="/CEK/References/CEK_API.md#Location">地域・都市名を取得する</a></li>
              <li><a href="/CEK/References/CEK_API.md#Time">日時・時間を取得する</a></li>
              <li><a href="/CEK/References/CEK_API.md#Number">数値を取得する</a>（<a href="/CEK/References/CEK_API.md#ClovaWholeNumber">CLOVA.WHOLE_NUMBER</a> 追加）</li>
              <li><a href="/CEK/References/CEK_API.md#Unit">単位を取得する</a>（<a href="/CEK/References/CEK_API.md#ClovaUnit">CLOVA.UNIT</a>、<a href="/CEK/References/CEK_API.md#ClovaUnitCurrency">CLOVA.UNIT_CURRENCY</a> 追加）</li>
              <li><a href="/CEK/References/CEK_API.md#NumberUnit">数値と単位を取得する</a>（<a href="/CEK/References/CEK_API.md#ClovaNumber">CLOVA.NUMBER</a>、<a href="/CEK/References/CEK_API.md#ClovaGenericNumber">CLOVA.GENERIC_NUMBER</a>、<a href="/CEK/References/CEK_API.md#ClovaMoney">CLOVA.MONEY</a> 追加）</li>
            </ul>
          </ul>
          <li><a href="/CEK/References/CEK_API.md">Extensionを登録する</a> 更新（<a href="/DevConsole/Guides/CEK/Register_Extension.md#AddBuiltinSlotType">ビルトインスロットタイプを追加する</a> 更新）</li>
          <li><a href="https://clova-developers.line.biz/#/updatehistory/">アップデート履歴</a> 追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.2</td><td>2019/04/25</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a> 更新</li>
          <ul>
            <li><a href="/Design/Design_Guideline_For_Extension.md#BuiltinIntent">ビルトインインテント</a> 更新（Clova.FallbackIntent 追加）</li>
            <li><a href="/Design/Design_Guideline_For_Extension.md#BuiltinSlotType">ビルトインスロットタイプ</a> 更新（CLOVA.DATETIME_RECENT 追加）</li>
          </ul>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#BuiltinIntent">ビルトインインテント</a> 更新（<a href="/CEK/References/CEK_API.md#ClovaFallbackIntent">Clova.FallbackIntent</a> 追加）</li>
            <li><a href="/CEK/References/CEK_API.md#BuiltinSlotType">ビルトインスロットタイプ</a> 更新（<a href="/CEK/References/CEK_API.md#ClovaDatetimeRecent">CLOVA.DATETIME_RECENT</a> 追加）</li>
          </ul>
          <li><a href="/CEK/References/CEK_API.md">Extensionを登録する</a> 更新（<a href="/DevConsole/Guides/CEK/Register_Extension.md#AddBuiltinIntent">ビルトインインテントを追加する</a> 更新）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.1</td><td>2019/04/08</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a> 更新</li>
          <ul>
            <li><a href="/Design/Design_Guideline_For_Extension.md#BuiltinIntent">ビルトインインテント</a>更新（Clova.NextIntent、Clova.PauseIntent、Clova.PreviousIntent、Clova.ResumeIntentを追加）</li>
            <li><a href="/Design/Design_Guideline_For_Extension.md#AudioPlayer">オーディオコンテンツ再生タイプ</a> 更新（ユーザーシナリオに一時停止/再生再開の例を追加）</li>
          </ul>
          <li><a href="/CEK/Guides/Build_Custom_Extension.md#ProvideAudioContent">オーディオコンテンツを提供する</a> 更新（<a href="/CEK/Guides/Build_Custom_Extension.md#ControlAudioPlayback">オーディオコンテンツの再生をコントロールする</a> 追加）</li>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新（<a href="/CEK/References/CEK_API.md#BuiltinIntent">ビルトインインテント</a> 更新）</li>
          <li><a href="/DevConsole/Guides/CEK/Test_Extension.md#TestInteractionModel">対話モデルをテストする</a> 更新（AudioPlayer使用時のテスト機能の動作について注記を追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.0</td><td>2019/03/28</td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/CEK/Test_Extension.md">Extensionをテストする</a> 更新</li>
          <ul>
            <li>テスト画面のUI変更に対応</li>
            <li>テストモードの追加（<a href="/DevConsole/Guides/CEK/Test_Extension.md#InteractionModelTestMode">対話モデルテストモード</a>、<a href="/DevConsole/Guides/CEK/Test_Extension.md#ScenarioTestMode">シナリオテストモード</a>）</li>
          </ul>
          <li><a href="/Resources/Sound_Library.md">Sound Library</a> 追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.0.1</td><td>2019/01/24</td>
      <td>
        <ul>
          <li>Xperia Ear DuoのAudioPlayer対応開始</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.0.0</td><td>2019/01/22</td>
      <td>
        <ul>
          <li><a href="https://clova-developers.line.biz" target="_blank">Clova Developer Center β</a>のUI変更に対応</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.0.1</td><td>2019/01/15</td>
      <td>
        <ul>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#ClovaDatetime">CLOVA.DATETIME</a> 更新（フィールド名およびフィールドの説明を修正）</li>
            <li><a href="/CEK/References/CEK_API.md#ClovaDuration">CLOVA.DURATION</a> 更新（フィールド名およびフィールドの説明を修正）</li>
          </ul>
          <li><a href="/DevConsole/Guides/CEK/Remove_Extension.md">Extensionを削除および中止する</a> 更新（<a href="/DevConsole/Guides/CEK/Remove_Extension.md#RemoveExtensionInService">サービス中のExtensionを削除する</a>際の連絡先メールアドレスを変更）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.0.0</td><td>2018/11/20</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home Extension</a> 追加</li>
          <ul>
            <li><a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home Extension を作成する</a> 更新（<a href="/CEK/CEK_Overview.md">Clova Extensions Kit</a>より章を移動）</li>
            <li><a href="/CEK/References/CEK_API_ClovaHome.md">Clova Home Extension API のリファレンス</a> 追加</li>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.2.2</td><td>2018/11/15</td>
      <td>
        <ul>
          <li><a href="https://clova-developers.line.biz/">Clova Developer Center β</a> URL変更</li>
          <li><a href="https://developers.line.biz/">LINE Developers</a> URL変更</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.2.1</td><td>2018/11/08</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a> 更新（<a href="/Design/Design_Guideline_For_Extension.md#DefineSubInvocationName">呼び出し名（サブ）を定義する</a> 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.2.0</td><td>2018/10/11</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Handle_ClovaSkill_EventRequest.md">ユーザーの利用開始および停止を処理する</a> 追加</li>
          <li><a href="/DevConsole/Guides/CEK/Use_Analytics.md">Clova Analyticsを使用する</a> 追加</li>
          <li><a href="/CEK/Guides/Build_Custom_Extension.md#ReturnCustomExtensionResponse">Custom Extensionレスポンスを返す</a> 更新（タイムアウト値の説明 追加）</li>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新（<a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">レスポンスメッセージ</a> タイムアウト値の説明 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.10</td><td>2018/09/20</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a> 更新（<a href="/Design/Design_Guideline_For_Extension.md#CustomSlotType">カスタムスロットタイプ</a> 同義語登録数の上限の説明 追加）</li>
          <li><a href="/DevConsole/Guides/CEK/Register_Extension.md#RegisterInteractionModel">対話モデルを登録する</a> 更新</li>
          <ul>
            <li><a href="/DevConsole/Guides/CEK/Register_Extension.md#AddCustomSlotType">カスタムスロットタイプ</a> 同義語の登録数上限の説明を追加</li>
            <li><a href="/DevConsole/Guides/CEK/Register_Extension.md#AddCustomIntent">カスタムインテント</a> サンプル発話の登録数上限の説明を追加</li>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.9</td><td>2018/09/07</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Go">CEK SDK for Go</a> 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.8</td><td>2018/08/29</td>
      <td>
        <ul>
          <li><a href="/CEK/References/CEK_API.md">CEK APIのリファレンス</a> 更新</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#InteractionModel">対話モデル</a> 追加</li>
            <li>ビルトインスロットタイプ（<a href="/CEK/References/CEK_API.md#ClovaDatetime">CLOVA.DATETIME</a>、<a href="/CEK/References/CEK_API.md#ClovaDuration">CLOVA.DURATION</a>）の説明 追加</li>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.7</td><td>2018/08/24</td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md">Extensionを配布する</a> 更新（<a href="/DevConsole/Guides/CEK/Deploy_Extension.md#DeployInSkillStore">スキルストアに表示される</a> 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.6</td><td>2018/08/09</td>
      <td>
        <ul>
          <li><a href="/Glossary.md">用語および略語</a> 更新（語順変更、用語追加）</li>
          <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Java">CEK SDK for Java</a> 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.5</td><td>2018/08/03</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Python">CEK SDK for Python</a> 追加）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.4</td><td>2018/08/02</td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md#InputReviewInfo">配布情報を入力する</a> 更新（検索キーワードについての説明を追加、スキルストアの画像を更新）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.3</td><td>2018/07/27</td>
      <td>
        <ul>
          <li><a href="/CEK/Guides/Clova_CEK_SDK.md">Clova Extensions Kitソフトウェア開発キット</a> 更新（<a href="/CEK/Guides/Clova_CEK_SDK.md#SDK_For_Kotlin">CEK SDK for Kotlin</a> 追加）</li>
          <li><a href="/Design/Design_Guideline_For_Extension.md#InvocationNameRequirement" target="_blank">スキル名/呼び出し名の要件</a> 更新（Clovaの呼び名を「ねぇClova」に統一）</li>
          <li><a href="/DevConsole/Guides/CEK/Register_Extension.md#InputSkillInfo" target="_blank">Extensionの基本情報を入力する</a> 更新（「提供者について」の説明を追加）</li>
          <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md#InputReviewInfo" target="_blank">配布情報を入力する</a> 更新（「代表サンプル発話」の入力例を追加）</li>
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
