対話モデルが正しく動作することを確認したら、審査をリクエストする前に、実際のデバイスでテストして、音声の認識と応答が想定した通りに動作するか確認する必要があります。
開発しているアカウントで初期化しているClovaデバイスからは、以下で説明するテスターIDの追加作業を実施しなくてもテストをすることができます。
別のアカウントで初期化したClovaデバイスからスキルをテストしたい場合に以下のドキュメントを参照してください。

<div class="danger">
 <p><strong>注意</strong></p>
 <p>Custom Extensionは、現時点ではClova WAVEでは動作確認することができません。</p>
</div>

### テスターIDを登録する
特定のアカウントでのみ、このExtensionを実行できるように、テスターIDを登録します。
具体的には、[LINE Developers](https://developers.line.me/)に開発者として登録が完了しているユーザーのアカウントを、テスターIDとして登録することができます。

テスターIDは、次の手順で登録します。

1. [LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. テストするスキルが含まれるプロバイダーを選択し、**Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

4. **テスター管理** タブをクリックし、**追加** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Tab.png)

5. **プロバイダーの権限者の一覧から登録**、**メールアドレス一括登録**、**メールアドレス個別登録** のいずれかを選択し、テスターのアカウントを入力します。  
  ここでは **メールアドレス個別登録** を例に説明します。テスターのアカウント（LINE Developersへのログインに使用しているメールアドレス）を入力フォームに入力し、 **確認** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Address.png)

6. **登録** ボタンをクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Confirm.png)

7. テスターが招待メールに含まれる **招待を承諾する** リンクをクリックすると、テスター登録が完了します。  
![](/CEK/Resources/Images/CEK_Test_Invitation_Email.png)

8. **テスター管理** タブを再度クリックすると、テスターが追加されたことを確認できます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_List.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>テスターIDを登録した後、Extensionをテストできるようになるまでに少し時間がかかる場合があります。追加されない場合、時間をあけてから、再度確認してください。</p>
</div>

<div class="danger">
<p><strong>注意</strong></p>
  <p>実際のデバイスでテストするには、<strong>{{ book.DevConsole.cek_skill_info }}</strong>に外部からアクセスできる実際のExtensionサーバーのURLを必ず登録する必要があります。</p></li>
</div>


Extensionが実際のデバイスでも正しく動作したら、サービスの準備は完了です。Clova Developer Centerで審査をリクエストして、Extensionを配布することができます。
