# 複数のユーザーでExtensionの編集・テストを行う

複数のユーザーが共同でExtensionの編集・テストを行うには、Extensionを作成したオーナーが、他のユーザーに権限を付与する必要があります。具体的には、[LINE Developers](https://developers.line.biz/)に開発者として登録が完了しているユーザーに対して権限を付与することが可能です。

<div class="note">
  <p><strong>メモ</strong></p>
    <p>LINE Developersの開発者アカウントの登録については、<a href="https://developers.line.biz/ja/docs/messaging-api/getting-started/#%E3%83%81%E3%83%A3%E3%83%8D%E3%83%AB%E3%81%AE%E4%BD%9C%E6%88%90">LINE Developers のドキュメント</a>の<strong>1. コンソールにログインする</strong>と<strong>2. 開発者として登録する(初回ログイン時のみ)</strong>を参照してください。</p>
</div>


## 権限の種類 {#RoleType}

他のユーザーに付与できる権限の種類は次のとおりです。

| 権限の種類 | 実行できること                                               |
| ---------- | ------------------------------------------------------------ |
| Admin      | <ul><li><a href="https://developers.line.biz/console/">LINE Developersコンソール</a>でチャネルを管理する（基本設定、権限管理、テスター管理）</li><li><a href="https://clova-developers.line.biz/">Clova Developer Center β</a>でスキルを開発する（基本情報の修正、配布情報の修正、対話モデルの修正）</li><li>Clovaデバイスでの動作検証</li></ul> |
| Tester     | <ul><li>Clovaデバイスでの動作検証</li></ul>                  |

<div class="note">
  <p><strong>メモ</strong></p>
  <p>AdminおよびTesterを登録した後、Extensionをテストできるようになるまでに少し時間がかかる場合があります。追加されない場合、時間をあけてから、再度確認してください。</p>
</div>

## 権限を管理する {#ManageRole}

ユーザーへの権限の追加・削除は、以下の手順で実施します。

- [権限を追加する](#AddUser)
- [権限を編集する](#EditRoll)
- [権限を削除する](#DeleteUser)


### 権限を追加する {#AddUser}

AdminおよびTester権限は、次の手順で追加します。

1. [LINE Developersコンソール](https://developers.line.biz/console/)に接続し、**プロバイダー** を表示します。
![](/CEK/Assets/Images/CEK_LineDev_Provider_List.png)

2. 共同で開発したいスキルが含まれるプロバイダーを選択し、当該の **Clovaスキル** をクリックします。
![](/CEK/Assets/Images/CEK_LineDev_Channel_List.png)

3. **権限設定** タブをクリックし、**メールで招待**をクリックします。
![](/CEK/Assets/Images/CEK_LineDev_Admin_Privilege_Tab.png)

4. **メールアドレス**に権限を付与したいユーザーのメールアドレス（LINE Developersへのログインに使用しているメールアドレス）を入力し、**権限**のドロップダウンリスト**でAdmin**または**Tester**を選択します。**招待メールを送信**をクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Assets/Images/CEK_LineDev_Add_Address.png)

5. 招待されたユーザーがメールに含まれる **招待を承諾する** リンクをクリックし、LINE Developersにログインすると、権限の付与が完了します。
![](/CEK/Assets/Images/CEK_LineDev_Invitation_Email.png)

6. **権限設定** タブを再度クリックすると、ユーザーが追加されたことを確認できます。
![](/CEK/Assets/Images/CEK_LineDev_User_List.png)

### 権限を編集する {#EditRoll}

AdminからTester、またはTesterからAdminへ権限の種類を変更する場合は、次の手順で実施します。

1. [LINE Developersコンソール](https://developers.line.biz/console/)に接続し、**プロバイダー** を表示します。
![](/CEK/Assets/Images/CEK_LineDev_Provider_List.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。
![](/CEK/Assets/Images/CEK_LineDev_Channel_List.png)

3. **権限設定** タブを開き、**リスト**からチェックボックスで権限を変更したいユーザーを選択して、**編集**ボタンをクリックします。
![](/CEK/Assets/Images/CEK_LineDev_Select_User_To_Change.png)

4. **権限**のドロップダウンリストで権限の種類を選択し、**更新**ボタンをクリックします。
![](/CEK/Assets/Images/CEK_LineDev_Change_User_Type.png)


### 権限を削除する {#DeleteUser}

権限を削除する方法は、以下の2通りです。

* [Admin権限を持つユーザーが削除する](#DeleteByAdmin)
* [Testerを辞める](#QuitTester)

#### Admin権限を持つユーザーが削除する {#DeleteByAdmin}

1. Admin権限を持つユーザーが[LINE Developersコンソール](https://developers.line.biz/console/)に接続します。  
![](/CEK/Assets/Images/CEK_LineDev_Provider_List.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Channel_List.png)

3. **権限設定** タブを開き、**リスト**からチェックボックスで削除したいユーザーを選択して **選択したデータを削除** ボタンをクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Select_User_To_Delete.png)

4. 確認画面が表示されたら、**OK**をクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Delete_User_Confirm.png)


#### Testerを辞める {#QuitTester}

1. Tester権限を持つユーザーが[LINE Developersコンソール](https://developers.line.biz/console/)に接続します。  
![](/CEK/Assets/Images/CEK_LineDev_Provider_List_2.png)

2. プロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Channel_List_2.png)

3. **辞める** ボタンをクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Quit_Tester.png)

4. 確認画面が表示されたら、**OK** をクリックします。  
![](/CEK/Assets/Images/CEK_LineDev_Quit_Tester_Confirm.png)
