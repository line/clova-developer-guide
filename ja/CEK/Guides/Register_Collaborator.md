# 複数のユーザーでExtensionの編集・テストを行う

複数のユーザーが共同でExtensionの編集・テストを行うには、Extensionを作成したオーナーが、他のユーザーに権限を付与する必要があります。具体的には、[LINE Developers](https://developers.line.me/)に開発者として登録が完了しているユーザーに対して権限を付与することが可能です。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>LINE Developersの開発者アカウントの登録については、<a href="https://developers.line.me/ja/docs/line-login/getting-started/">LINE Developers のドキュメント</a>の<strong>2. 開発者として登録する(初回ログイン時のみ)</strong>を参照してください。</p>
</div>

## 権限の種類 {#RoleType}

付与できる権限は、以下の通りです。
* Admin権限
* テスター権限

ユーザーを **Admin** として登録すると、以下を実行できます。
* [LINE Developersコンソール](https://developers.line.me/console/)でチャネルを管理する（基本設定、権限管理、テスター管理）
* [Clova Developer Center β](https://clova-developers.line.me/)でスキルを開発する（基本情報の修正、配布情報の修正、対話モデルの修正）
* Clovaデバイスでの動作検証

ユーザーを **テスター** として登録すると、以下を実行できます。
* Clovaデバイスでの動作検証

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Adminおよびテスターを登録した後、Extensionをテストできるようになるまでに少し時間がかかる場合があります。追加されない場合、時間をあけてから、再度確認してください。</p>
</div>

## 権限を管理する {#ManageRole}

ユーザーへの権限の追加・削除は、以下の手順で実施します。

1. [Admin権限を追加する](#AssignAdminRight)
2. [Admin権限を削除する](#RemoveAdminRight)
3. [テスターを追加する](#RegisterTester)
4. [テスターを削除する](#RemoveTester)

### 1. Admin権限を追加する {#AssignAdminRight}

Admin権限は、次の手順で付与します。

1. [LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. 共同で開発したいスキルが含まれるプロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

3. **権限管理** タブをクリックし、**追加** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Privilege_Tab.png)

4. **プロバイダーの権限者の一覧から登録**、**メールアドレス一括登録**、**メールアドレスで個別登録** のいずれかを選択し、Admin権限を付与するユーザーのアカウントを入力します。  
  ここでは **メールアドレスで個別登録** を例に説明します。追加したいユーザーのアカウント（LINE Developersへのログインに使用しているメールアドレス）を入力フォームに入力し、 **確認** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Add_Address.png)

5. **登録** ボタンをクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Add_Confirm.png)

6. 招待されたユーザーがメールに含まれる **招待を承諾する** リンクをクリックし、LINE Developersにログインすると、Admin権限の付与が完了します。  
![](/CEK/Resources/Images/CEK_Admin_Invitation_Email.png)

7. **権限管理** タブを再度クリックすると、テスターが追加されたことを確認できます。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Admin_List.png)


### 2. Admin権限を削除する {#RemoveAdminRight}

1. Admin権限を持つユーザーが[LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

3. **権限管理** タブをクリックし、Admin権限を削除したいユーザーのメールアドレスの右に表示されている **編集** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Admin_LineDev_Admin_Tab.png)

4. 名前の左に表示されたごみ箱のアイコンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Admin_LineDev_Edit_Button.png)

5. 確認画面が表示されたら、**削除** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Admin_LineDev_Confirm.png)



### 3.テスターを登録する {#RegisterTester}

テスターは、次の手順で登録します。

1. Admin権限を持つユーザーが[LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. テストするスキルが含まれるプロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

4. **テスター管理** タブをクリックし、**追加** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Tab.png)

5. **プロバイダーの権限者の一覧から登録**、**メールアドレス一括登録**、**メールアドレス個別登録** のいずれかを選択し、テスターのアカウントを入力します。  
  ここでは **メールアドレス個別登録** を例に説明します。テスターのアカウント（LINE Developersへのログインに使用しているメールアドレス）を入力フォームに入力し、 **確認** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Address.png)

6. **登録** ボタンをクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Confirm.png)

7. 招待されたユーザーが、メールに含まれる **招待を承諾する** リンクをクリックし、LINE Developersにログインすると、テスター登録が完了します。  
![](/CEK/Resources/Images/CEK_Test_Invitation_Email.png)

8. **テスター管理** タブを再度クリックすると、テスターが追加されたことを確認できます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_List.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Admin権限を持つユーザーは、自動的にテスターとなりますので、あらためてテスターとして追加する必要はありません。</p>
</div>

### 4. テスターを削除する {#RemoveTester}

テスターを削除する方法は、以下の2通りです。

* [Admin権限を持つユーザーがテスターを削除する](#RemoveByAdmin)
* [テスターをやめる](#QuitTester)

#### Admin権限を持つユーザーがテスターを削除する  {#RemoveByAdmin}

1. Admin権限を持つユーザーが[LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

3. **テスター管理** タブをクリックし、削除したいテスターのメールアドレスの右に表示されている **編集** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_LineDev_Tester_Tab.png)

4. 名前の左に表示されたごみ箱のアイコンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_LineDev_Edit_Button.png)

5. 確認画面が表示されたら、**削除** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_LineDev_Confirm.png)


#### テスターをやめる {#QuitTester}

1. テスターが[LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Remove_Tester_LineDev_Provider_List.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_LineDev_Skill_List.png)

3.  **テスターをやめる** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_Quit_Tester.png)

4. 確認画面が表示されたら **やめる** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Remove_Tester_Quit_Confirm.png)
