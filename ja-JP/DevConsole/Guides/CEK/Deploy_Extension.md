# Extensionを配布する
[Custom Extension](/CEK/Guides/Build_Custom_Extension.md)を[Clova Developer Centerに登録](/DevConsole/Guides/CEK/Register_Extension.md)すると、登録したExtensionをClovaサービスに配布できます。Extensionを配布すると、エンドユーザーが **{{ book.DevConsole.ManageExtensions }}** から選んで使用することができます。

Extensionの配布は、通常、次の順で行われます。

* [配布情報を入力する](#InputDeploymentInfo)
* [プライバシーポリシーおよびコンプライアンス情報を入力する](#InputComplianceInfo)
* [審査をリクエストする](#RequestExtensionSubmission)
* [スキルが公開される](#DeployInSkillStore)

## 配布情報を入力する {#InputDeploymentInfo}

Clova Developer Centerで[Extensionを登録](/DevConsole/Guides/CEK/Register_Extension.md)し、[対話モデルを登録](/DevConsole/Guides/CEK/Register_Interaction_Model.md)すると、配布情報の入力が可能になります。Extensionのメニュー画面で **{{ book.DevConsole.cek_publishing }}** を選択してください。

![](/DevConsole/Resources/Images/DevConsole-Deployment_Info_Menu.png)

次のように配布情報を入力します。

![](/DevConsole/Resources/Images/DevConsole-Input_Deployment_Info.png)

Extensionをユーザーに説明するための情報として、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** メニュー(スキルストア)でユーザーに提供されます。次の情報を入力する必要があります。

* **{{ book.DevConsole.cek_category }}**：Extensionのカテゴリです。ユーザーがカテゴリごとにExtensionを探したり、検索する際に利用されます。
* **{{ book.DevConsole.cek_test_instructions }}**：[Extensionの審査](#RequestExtensionSubmission)プロセスでClova事務局がExtensionを確認する際、必要とされる参考情報です。エンドユーザーには表示されません。案内に従って作成します。
* **サービスを提供する国および地域**：現在、日本でのみExtensionを配布できます。
* **{{ book.DevConsole.cek_full_skill_desc }}**：**{{ book.DevConsole.ExtensionPage }}** でユーザーに提供するExtensionの説明です。案内に従って作成します。
* **{{ book.DevConsole.cek_example_phrases }}**：ユーザーがExtensionをどのように使用できるかを示す例です。**{{ book.DevConsole.ExtensionPage }}** に表示されます。なお、1番目の例は **{{ book.DevConsole.StoreHome }}** にも表示されるため、「〜を起動して」「〜を開いて」など、スキルを起動するフレーズを含めて登録してください。（例：ねぇClova、ピザボットを起動して）
* **{{ book.DevConsole.cek_keywords }}**：ユーザーが特定のキーワードでExtensionを検索する際に、その検索結果にExtensionが含まれるように設定します（カンマ区切りで5つまで登録可能）。スキルストアの検索機能の検索対象になります。
{% if book.language !== "ja" %}
* **{{ book.DevConsole.cek_small_icon }}**：小サイズ(108x108ピクセル)のExtensionのアイコンファイルです。**{{ book.DevConsole.ManageExtensions }}** と **{{ book.DevConsole.ExtensionPage }}** に表示されます。
{% endif %}
* **{{ book.DevConsole.cek_large_icon }}**：スキルストアおよびClovaアプリで表示されるExtensionのアイコンファイルです。512x512ピクセルの円形もしくは正方形で作成してください。
* **対象デバイス** : Extensionが動作するClovaデバイスを選択します。チェックを外したデバイスからはスキルを呼び出すことができません。

このように入力された情報は、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** で次のように表示されます。

| {{ book.DevConsole.StoreHome }} | {{ book.DevConsole.ExtensionPage }} |
| ------------------------------- | ----------------------------------- |
| ![Extension List](/DevConsole/Resources/Images/DevConsole-Store_UI_Example-Extension_Store_Home.png) | ![Extension Details](/DevConsole/Resources/Images/DevConsole-Store_UI_Example-Extension_Page.png) |

<div class="note">
  <p><strong>メモ</strong></p>
  <p><strong>{{ book.DevConsole.ExtensionPage }}</strong>に表示される一部の情報には、登録されている<a href="/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo">Extensionの基本情報</a>が使用されます。</p>
</div>

## プライバシーポリシーおよびコンプライアンス情報を入力する {#InputComplianceInfo}

Extensionの配布に必要な情報を入力する最後の段階です。プライバシーポリシーおよびコンプライアンス関連の情報を入力します。Extensionの登録メニューで **{{ book.DevConsole.cek_privacy }}** を選択します。

![](/DevConsole/Resources/Images/DevConsole-Policy_Menu.png)

以下のように情報を入力します。

![](/DevConsole/Resources/Images/DevConsole-Input_Policy.png)

* **{{ book.DevConsole.cek_allow_purchase }}**：Extensionを使用する際、ユーザーが決済をしたり支払いをする場面がある場合、**{{ book.DevConsole.cek_yes }}** を選択します。
* **{{ book.DevConsole.cek_use_personal_info }}**：Extensionがユーザーの個人情報を取得する場合、**{{ book.DevConsole.cek_yes }}** を選択します。
* **{{ book.DevConsole.cek_privacy_policy_url }}**：Extensionが個人情報を取得する場合、それに関するプライバシーポリシーを提供するページを入力します。Extension説明ページの一番下に表示されます。
* **{{ book.DevConsole.cek_terms_of_use }}**：Extensionに関する免責条項を提供するページを入力します。プライバシーポリシーのURLと同じく、Extension説明ページの一番下に表示されます。

**{{ book.DevConsole.cek_privacy_policy_url }}** と **{{ book.DevConsole.cek_terms_of_use }}** に入力された内容は、**{{ book.DevConsole.ExtensionPage }}** で次のように表示されます。

![](/DevConsole/Resources/Images/DevConsole-Store_UI_Example-Extension_Policy.png)

## 審査をリクエストする {#RequestExtensionSubmission}

Extensionの[配布情報](#InputDeploymentInfo)と[プライバシーポリシーおよびコンプライアンス情報](#InputComplianceInfo)まで入力すると、登録したExtensionの審査をリクエストできます。Clova事務局は、登録されたExtensionの情報、実際の動作確認と適合性などを審査します。

Extensionの審査をリクエストするには、登録したExtensionのリストで **{{ book.DevConsole.cek_request_submit }}** メニューをクリックします。

![](/DevConsole/Resources/Images/DevConsole-Submit_Extension_1.png)

または[プライバシーポリシーおよびコンプライアンス情報](#InputComplianceInfo)を入力する画面の一番下にある **{{ book.DevConsole.cek_request_submit }}** ボタンをクリックして、リクエストすることもできます。

![](/DevConsole/Resources/Images/DevConsole-Submit_Extension_2.png)

**{{ book.DevConsole.cek_request_submit }}** をクリックすると、以下のように審査のリクエストに関する情報をClova事務局に送信できます。

![](/DevConsole/Resources/Images/DevConsole-Submission_Request_Message.png)

<div class="danger">
  <p><strong>注意</strong></p>
  <p>審査中には、Extensionの情報と対話モデルを修正できません。</p>
</div>

スキル審査は、スキルストアへ反映する前に、Clova事務局にて実施します。もし、[ユーザーアカウントの連携](/CEK/Guides/Link_User_Account.md)が必要なサービスの場合は、[配布情報を入力](#InputDeploymentInfo)する際に、テスト用のアカウント名およびパスワードを **{{ book.DevConsole.cek_test_instructions }}** 欄に入力していただく必要があります。

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

![](/DevConsole/Resources/Images/DevConsole-Cancel_Submission.png)

審査を通過しなかった場合、Extensionの **{{ book.DevConsole.cek_status }}** が **{{ book.DevConsole.cek_status_rejected }}** に変更されます。これは **{{ book.DevConsole.cek_status_dev }}** と同じステータスで、再び審査をリクエストできます。

![](/DevConsole/Resources/Images/DevConsole-Extension_Submission_Rejected.png)

その際、**{{ book.DevConsole.cek_message }}** の **{{ book.DevConsole.cek_view }}** メニューをクリックすると、審査のフィードバックを確認できます。

![](/DevConsole/Resources/Images/DevConsole-Show_Submission_Feedback.png)

## スキルが公開される {#DeployInSkillStore}

審査を通過すると、Clova Developer Centerのスキル設定画面に **{{ book.DevConsole.cek_status_prd }}** として表示されます。

![](/DevConsole/Resources/Images/DevConsole-Extension_List_Version_Status.png)

エンドユーザーは、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** の **スキルリスト** からスキルを選択し、**{{ book.DevConsole.ExtensionPage }}** に表示される **利用開始** ボタンをタップすることでスキルを利用することができます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>自分が開発したスキルは、Clovaアプリ上では審査通過後も<strong>現在テスト中のスキル</strong>の欄に表示されますのでご注意ください。</p>
</div>
