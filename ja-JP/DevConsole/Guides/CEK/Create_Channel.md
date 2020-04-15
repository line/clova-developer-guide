# チャネルを作成する

Clova Developer Center βで[Extensionを登録](/DevConsole/Guides/CEK/Register_Extension.md)するには、まずLINE Developersコンソールでチャネルを作成する必要があります。チャネルの作成は、以下の手順で行います。

1. [Clova Developer Center βにログインする](#LoginClovaDevCenter)
2. [LINE Developersコンソールでチャネルを作成する](#CreateSkillChannel)

## Clova Developer Center βにログインする {#LoginClovaDevCenter}
Clova Developer Center βにログインします。

1. [Clova Developer Center β](https://clova-developers.line.biz/)ホーム画面の **ログイン** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-Console_Login.png)

2. アカウントの選択画面が表示されたら、**LINEアカウントでログイン** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-LINE_Login.png)

3. LINEアカウントへのログインに利用しているメールアドレスとパスワードを入力し、**ログイン** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-LINE_Login_2.png)

4. 同意画面が表示されたら、**同意する** をクリックします（初回ログイン時のみ）。  
![](/DevConsole/Assets/Images/DevConsole-Access_Agreement.png)

5. **スキル設定** または **スキルを開発する** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-Entering_CEK_Menu.png)

6. **LINE Developersでスキルチャネルを新規作成** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-First_Look_of_Extension_List.png)

<div class="note">
  <p><strong>メモ</strong></p>
    <p>LINE Developersの開発者アカウントの登録については、<a href="https://developers.line.biz/ja/docs/messaging-api/getting-started/#%E3%83%81%E3%83%A3%E3%83%8D%E3%83%AB%E3%81%AE%E4%BD%9C%E6%88%90">LINE Developers のドキュメント</a>の<strong>1. コンソールにログインする</strong>と<strong>2. 開発者として登録する(初回ログイン時のみ)</strong>を参照してください。</p>
</div>

## LINE Developersコンソールでチャネルを作成する {#CreateSkillChannel}

LINE Developersコンソールでチャネルを作成します。

<div class="danger">
  <p><strong>注意</strong></p>
  <p>すでにLINE公式アカウントをお持ちの場合は、チャネル発行のフローが異なります。
  お手数ですが、<a href="https://partners.line.me/ja/partner/join" target="_blank"> LINE Partners</a> よりお問い合わせください。</p>
</div>

1. LINE Developersの新規チャネル作成画面で、プロバイダーを選択します。あらかじめ作成したプロバイダーを使用する場合は、**プロバイダー**のドロップダウンリストで選択します。
![](/DevConsole/Assets/Images/DevConsole-Create_Channel_1.png)  
  新規にプロバイダーを作成する場合は、**プロバイダー**のドロップダウンリストで **新規プロバイダー作成** を選択すると入力フォームが表示されます。新しく作成するプロバイダー名を入力します。
  ![](/DevConsole/Assets/Images/DevConsole-Create_Channel_2.png)  
  <div class="note">
      <p><strong>メモ</strong></p>
      <p>プロバイダーとは、スキルを提供する組織のことです。
      ご自分の名前、あるいは企業名などを入力してください。</p>
  </div>

2. **チャネル名** を入力し、**チャネルを作成してClovaスキルに移動** ボタンをクリックします。  
![](/DevConsole/Assets/Images/DevConsole-Create_Channel_3.png)

    <div class="note">
      <p><strong>メモ</strong></p>
      <p>チャネル名は、あなたがスキルを管理するために利用します。
      Clovaで提供するサービスの名前などを入力してください。</p>
    </div>

3. チャネルの作成が完了すると、Clova Developer Center β に遷移します。
