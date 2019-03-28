# Extensionを削除および中止する

審査をリクエストする前のExtensionは、[LINE Developersコンソール](https://developers.line.biz/console/)で削除が可能です。
ただし、以下の状態にあるExtensionはすぐに削除することはできません。

* Extensionが審査を受けている場合
* Extensionがサービス中の場合

ここでは、以下のケースにおけるExtensionの削除および中止方法を説明します。

1. [審査をリクエストする前に削除する](#RemoveExtensionBeforeReview)
2. [審査中のExtensionを削除する](#RemoveExtensionUnderReview)
3. [サービス中のExtensionを削除する](#RemoveExtensionInService)

## 1. 審査をリクエストする前に削除する {#RemoveExtensionBeforeReview}

審査をリクエストする前のExtensionは、LINE Developersコンソールで削除が可能です。

1. [LINE Developersコンソール](https://developers.line.biz/console/)にログインします。

2. **プロバイダーリスト** から、削除したいスキルが含まれるプロバイダーを選択します。  
![](/DevConsole/Assets/Images/DevConsole-LineDev_Provider_List.png)  

3. 削除したい **Clovaスキル** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-LineDev_Channel_List.png)  

4. 画面右上の<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-LineDev_Dot_Menu.png" /> をクリックし、**このチャネルを削除** を選択します。  
![](/DevConsole/Assets/Images/DevConsole-LineDev_Channel_Remove.png)  

5. 確認画面が表示されたら、**削除** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-LineDev_Channel_Remove_Confirm.png)  


## 2. 審査中のExtensionを削除する {#RemoveExtensionUnderReview}

Extensionが審査中の場合は、審査をキャンセルすると削除できるようになります。

1. Clova Developer Center βにログインします。

2. **スキル設定** または **スキルを開発する** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-Entering_CEK_Menu.png)

3. **審査をキャンセル** をクリックし、リクエストをキャンセルします。  
![](/DevConsole/Assets/Images/DevConsole-Cancel_Submission.png)

4. 上記 [1. 審査をリクエストする前に削除する](#RemoveExtensionBeforeReview)の手順でExtensionを削除します。


## 3. サービス中のExtensionを削除する {#RemoveExtensionInService}
Extensionが審査を通過し、サービスが開始されている場合には、サービスを一度中止の状態にすることで削除できるようになります。サービスを中止すると、Extensionは **{{ book.DevConsole.cek_status_dev }}** 状態に戻ります。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>サービス中のExtensionを中止する際にはClova事務局の確認が必要で、webから中止の申請はできません。
  <p>中止する際は、停止を申請する理由を記載し<a href="mailto:{{ book.ExtensionAdminEmail }}">{{ book.ExtensionAdminEmail }}</a>までご連絡ください。</p>
</div>
