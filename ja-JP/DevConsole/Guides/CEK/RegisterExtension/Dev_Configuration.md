## 開発設定を行う {#SetDevConfiguration}

Clova Developer Centerで[Extensionを登録](/DevConsole/Guides/CEK/Register_Extension.md)すると、サーバーやアカウント連携に関する設定が可能になります。
左メニューから **{{ book.DevConsole.cek_dev_configuration }}** を選択してください。

![](/DevConsole/Resources/Images/DevConsole-Dev_Config_Menu.png)

開発設定では次の項目を設定します。
* [サーバー設定を行う](#SetServerConnection)
* [アカウント連携を設定する](#SetAccountLinking)

### サーバー設定を行う {#SetServerConnection}

ExtensionはCEKとHTTPSで通信します。その際、CEKはExtensionにHTTPリクエストを送り、ExtensionはCEKにHTTPレスポンスを返します。CEKがExtensionにHTTPリクエストを送るためには、Clova Developer Centerでサーバーとの連携を設定する必要があります。[Extensionの基本情報を入力](#InputSkillInfo)すると、作成されたExtensionに対し、サーバーとの連携を設定できます。

Extensionのサーバーを登録するには、先にExtensionのサーバーと通信できるか確認する必要があります。次の例のように、簡単なcurlコマンドで通信状況を確認できます。

{% raw %}
```bash
$ curl "https://example.com/pizzabot" -X POST
```
{% endraw %}

次の順でサーバー設定を行います。

![](/DevConsole/Resources/Images/DevConsole-Extension_Server_Settings.png)

<ol>
  <li><strong>{{ book.DevConsole.cek_configuration }}</strong>をクリックします。</li>
  <li>ExtensionサーバーのURL(エンドポイント)を<strong>{{ book.DevConsole.cek_service_endpoint_url }}</strong>項目に入力します。
    <div class="note">
      <p><strong>メモ</strong></p>
      <p>Extensionのサーバーは、HTTPSのみ許可されます。HTTPSで443ポートに設定してください。</p>
    </div>
  </li>
  <li>ExtensionがAudioPlayerを使用する場合は、<strong>{{ book.DevConsole.cek_audioplayer }}</strong>項目で<strong>{{ book.DevConsole.cek_yes }}</strong>を選択を選択します。</li>
  <li>入力が完了したら<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
</ol>


### アカウント連携を設定する {#SetAccountLinking}

Extensionが提供するサービスのアカウントが、Clovaのユーザーアカウントとの連携を必要とする場合、[サーバーとの連携を設定する](#SetServerConnection)の内、[アカウント連携](/CEK/Guides/Link_User_Account.md)に関連情報を入力します。

次の順で、アカウント連携の設定に[必要な情報](/CEK/Guides/Link_User_Account.md#RegisterAccountLinkingInfo)を入力します。

<ol>
  <li><strong>{{ book.DevConsole.cek_dev_accountlinking }}</strong>をクリックします。</li>
    <img src="/DevConsole/Resources/Images/DevConsole-Extension_Account_Linking_Settings_1.png" />
  <li>Extensionが提供するサービスのアカウントが、Clovaのユーザーアカウントとの連携を必要とする場合、<strong>{{ book.DevConsole.cek_account_linking }}</strong>項目で<strong>{{ book.DevConsole.cek_yes }}</strong>を選択します。アカウント連携の詳細については、<a href="#SetAccountLinking">アカウント連携を設定する</a>を参照してください。</li>
  <li>ユーザーにアカウント認証UIを提供する認証URLを、<strong>{{ book.DevConsole.cek_authorization_url }}</strong>項目に入力します。ユーザーがExtensionをアクティブにすると、このページに移動します。</li>
  <li>ユーザーが自身のアカウントを即座に設定できるようにする場合には、<strong>{{ book.DevConsole.cek_configuration_url }}</strong>項目にアカウント設定ページのURLを入力します。</li>
  <li><strong>{{ book.DevConsole.cek_privacy_policy_url }}</strong>項目に、Extensionが提供するサービスのプライバシーポリシーが提供されるURLを入力します。このページの内容は、後ほどストアで表示されます。</li>
  <li><strong>{{ book.DevConsole.cek_authorization_url }}</strong>または<strong>{{ book.DevConsole.cek_privacy_policy_url }}</strong>で提供するページが別のドメインから必要なリソースを読み込む場合、<strong>{{ book.DevConsole.cek_domain_list }}</strong>項目に必要なドメインを追加します。</li>
  <li>アカウント連携の際に発行されるアクセストークンのスコープをあらかじめ定義している場合、<strong>{{ book.DevConsole.cek_scope }}</strong>項目に定義したスコープを追加します。</li>
    <img src="/DevConsole/Resources/Images/DevConsole-Extension_Account_Linking_Settings_2.png" />
  <li>現在、<strong>{{ book.DevConsole.cek_authorization_grant_type }}</strong>は<strong>認可コード承認</strong>のみサポートしています。</li>
  <li><strong>{{ book.DevConsole.cek_access_token_uri }}</strong>項目に、サービスのアクセストークンを発行できるURLを入力します。</li>
  <li><strong>{{ book.DevConsole.cek_refresh_token_uri }}</strong>項目に、サービスのアクセストークンを更新できるURLを入力します。</li>
  <li>ユーザーアカウント認証を行う際、HTTPリクエストに必要な<strong>{{ book.DevConsole.cek_client_id }}</strong>を入力します。クライアントIDは、<a href="/CEK/Guides/Link_User_Account.md#BuildAuthServer">認証サーバーを構築</a>する際に生成した値です。</li>
  <li>サービスのアクセストークンを取得した後、HTTPリクエストの送信に必要な<strong>{{ book.DevConsole.cek_client_secret }}</strong>を入力します。クライアントシークレットは、<a href="/CEK/Guides/Link_User_Account.md#BuildAuthServer">認証サーバーを構築</a>する際に生成した値です。</li>
  <li><strong>{{ book.DevConsole.cek_client_authentication_scheme }}</strong>は、次のうち認可サーバーのインターフェースの実装に適した値を設定します。
    <ul>
      <li><strong>HTTP Basic(Recommended)</strong>：サービスのアクセストークンを取得するために、資格情報がヘッダーに入力される場合</li>
      <li><strong>Credentials in request body</strong>：サービスのアクセストークンを取得するため、資格情報がボディーに入力される場合</li>
    </ul>
  </li>
  <li>入力が完了したら<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
</ol>

<div id="RedirectURI" class="note">
  <p><strong>メモ</strong></p>
  <p>アカウント認証を済ませた後、クライアントがリダイレクトされるURLは<code>{{ book.RedirectURLforAccountLinking }}</code>で、<strong>{{ book.DevConsole.cek_redirect_urls }}</strong>項目で確認できます。</strong></p>
  <img src="/DevConsole/Resources/Images/DevConsole-Redirect_URL_for_Extension_Account_Linking.png" />
</div>
