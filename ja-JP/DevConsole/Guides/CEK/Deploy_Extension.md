# Extensionを配布する
[Custom Extension](/CEK/Guides/Build_Custom_Extension.md)を[CLOVA Developer Centerに登録](/DevConsole/Guides/CEK/Register_Extension.md)すると、登録したExtensionをCLOVAサービスに配布できます。Extensionを配布すると、エンドユーザーが **{{ book.DevConsole.ManageExtensions }}** から選んで使用することができます。

Extensionの配布は、通常、次の順で行われます。

* [審査情報を入力する](#InputReviewInfo)
* [審査申請する](#RequestExtensionSubmission)
* [スキルが公開される](#DeployInSkillStore)

## 審査情報を入力する {#InputReviewInfo}
[CLOVA Developer Centerに登録](/DevConsole/Guides/CEK/Register_Extension.md)されたスキルは、CLOVA事務局による審査を受け、通過すると配布されます。その審査に必要な情報を入力します。
**登録済みスキル** リストの **管理** 項目にある **審査申請** を選択します。

![](/DevConsole/Assets/Images/DevConsole-Deployment_Info_Menu.png)

**{{ book.DevConsole.cek_review_step_setting }}** の入力ページが開いたら、次のように情報を入力します。

![](/DevConsole/Assets/Images/DevConsole-Input_Deployment_Info.png)

<ol>
  <li><strong>{{ book.DevConsole.cek_provider_type }}</strong>を選択すると、該当する入力項目が表示されます。</li>
  <li><strong>{{ book.DevConsole.cek_provider }}</strong>：Extensionを作成した主体(企業や個人)の名前、またはニックネームを入力します。{{ book.DevConsole.ManageExtensions }}に表示され、Extensionを審査する際にチェックされます。</li>
  <li><strong>{{ book.DevConsole.cek_provider_tts }}</strong>：音声で読み上げるときに発音される提供者の名称です。読み上げボタンを押して、提供者名を正しく発音できることを確認してください。</li>
  <li><strong>{{ book.DevConsole.cek_provider_email }}</strong>項目に、当社より連絡可能なメールアドレスを入力します。{{ book.DevConsole.ManageExtensions }}には表示されません。</li>
  <li>{{ book.DevConsole.cek_provider_type }}で<strong>{{ book.DevConsole.cek_provider_corporation }}</strong>を選んだ場合は、<strong>本社所在地</strong>、<strong>代表電話番号</strong>、<strong>代表者名</strong>、<strong>企業サイト</strong>項目を入力してください。こちらは審査に必要な情報であり、{{ book.DevConsole.ManageExtensions }}には表示されません。</li>
  <li><strong>{{ book.DevConsole.cek_line_bot_mid }}</strong>：<a href="https://clova-developers.line.biz/guide/CEK/Guides/Link_Messaging_API.md" target="_blank">Custom ExtensionとLINEの連携</a>を行う場合に、スキルと連動するLINEのアカウントを選択してください。ここで選択したLINEアカウントを友だち追加できるリンクがスキルストアに追加されます。</li>
  <li><strong>{{ book.DevConsole.cek_test_instructions }}</strong>：<a href="https://clova-developers.line.biz/guide/DevConsole/Guides/CEK/Deploy_Extension.md#RequestExtensionSubmission" target="_blank">Extensionの審査</a>プロセスでCLOVA事務局がExtensionを確認する際、必要とされる参考情報です。{{ book.DevConsole.ManageExtensions }}には表示されません。案内に従って作成します。</li>
  <li>**{{ book.DevConsole.cek_save }}** ボタンをクリックして、入力した内容を保存します。**{{ book.DevConsole.cek_next }}** をクリックすると、{{ book.DevConsole.cek_review_step_submit}}画面に遷移します。</li>
</ol>


## 審査申請する {#RequestExtensionSubmission}

**{{ book.DevConsole.cek_review_step_setting }}** の入力が完了すると、登録したExtensionの審査をリクエストできます。CLOVA事務局は、登録されたExtensionの情報、実際の動作確認と適合性などを審査します。

Extensionの審査をリクエストするには、左のメニューから **{{ book.DevConsole.cek_review_step_submit}}** を選択します。

![](/DevConsole/Assets/Images/DevConsole-Submit_Extension_1.png)

**{{ book.DevConsole.cek_request_submit_info }}** を入力し、注意事項のチェックボックスにチェックを入れて、**{{ book.DevConsole.cek_request_submit }}** ボタンをクリックすると審査申請が完了します。

<div class="danger">
  <p><strong>注意</strong></p>
  <p>審査中には、情報の修正はできません。</p>
</div>

スキル審査は、スキルストアへ反映する前に、CLOVA事務局にて実施します。もし、[ユーザーアカウントの連携](/CEK/Guides/Link_User_Account.md)が必要なサービスの場合は、[配布情報を入力](#InputReviewInfo)する際に、テスト用のアカウント名およびパスワードを **{{ book.DevConsole.cek_test_instructions }}** 欄に入力していただく必要があります。

Extensionを審査する際に確認する評価項目は次のとおりです。

* [ユーザーシナリオ](/Design/Design_Guideline_For_Extension.md#MakeUseCaseScenarioScript)の検証
  * 会話のコンテクストに不自然なところがないか確認します。
  * シナリオで使用される発話データに、禁止用語や差別用語などが含まれていないか確認します。
  * Extensionが[ユーザーアカウントと連携](/CEK/Guides/Link_User_Account.md)する場合、サービスに特化した部分をさらに検討することがあります。
* スキルの動作検証
  * Extensionがサービスに適切な用語を使用しているか確認します。
  * インテント、スロットなどの対話モデルを検証します。
  * Extensionの[詳細な目標](/Design/Design_Guideline_For_Extension.md#SettingGoal)に合ったサービスを提供しているか確認します。
* 配布情報の検証
  * Extensionの説明、カテゴリ、検索キーワードなどの配布情報が正しく入力されているか確認します。
  * スキルが、配布情報に入力された利用規約やプライバシーポリシーに違反していないことを確認します。

審査中に **{{ book.DevConsole.cek_cancel_review }}** メニューをクリックすると、いつでも審査のリクエストをキャンセルできます。審査のリクエストをキャンセルすると、前のステータスに戻ります。

![](/DevConsole/Assets/Images/DevConsole-Cancel_Submission.png)

審査を通過しなかった場合、Extensionの **{{ book.DevConsole.cek_status }}** が **{{ book.DevConsole.cek_status_rejected }}** に変更されます。これは **{{ book.DevConsole.cek_status_dev }}** と同じステータスで、再び審査をリクエストできます。

![](/DevConsole/Assets/Images/DevConsole-Extension_Submission_Rejected.png)

その際、**{{ book.DevConsole.cek_message }}** の **{{ book.DevConsole.cek_view }}** メニューをクリックすると、審査のフィードバックを確認できます。

![](/DevConsole/Assets/Images/DevConsole-Show_Submission_Feedback.png)

## スキルが公開される {#DeployInSkillStore}

審査を通過すると、CLOVA Developer Centerのスキル設定画面に **{{ book.DevConsole.cek_status_prd }}** として表示されます。

![](/DevConsole/Assets/Images/DevConsole-Extension_List_Version_Status.png)

エンドユーザーは、CLOVAアプリの **{{ book.DevConsole.ManageExtensions }}** の **スキルリスト** からスキルを選択し、**{{ book.DevConsole.ExtensionPage }}** に表示される **利用開始** ボタンをタップすることでスキルを利用することができます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>自分が開発したスキルは、CLOVAアプリ上では審査通過後も<strong>現在テスト中のスキル</strong>の欄に表示されますのでご注意ください。</p>
</div>
