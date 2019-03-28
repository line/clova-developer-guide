# Extensionをアップデートする

Extensionが審査を通過し、配布が承認されると、そのExtensionは **{{ book.DevConsole.cek_status_prd }}** 状態になります。Clova Developer Centerはその際、次の2つを作成します。

* **{{ book.DevConsole.cek_status_prd }}**：現在、**{{ book.DevConsole.cek_status_prd }}** 状態のExtensionの元の情報を持つバージョンです。Extension情報の照会のみできます。
* **{{ book.DevConsole.cek_status_dev }}**：配布されたExtensionの元の情報をコピーして作成されたバージョンです。Extensionをアップデートする際に使用されます。

![](/DevConsole/Assets/Images/DevConsole-Extension_List_After_Submission.png)

**{{ book.DevConsole.cek_status_prd }}** バージョンのExtensionは、現在サービス中の内容を反映しているため、修正することができません。Extensionをアップデートするには、コピーされた **{{ book.DevConsole.cek_status_dev }}** バージョンを使用します。Extensionに次の項目に該当するアップデート事項がある場合、**{{ book.DevConsole.cek_status_dev }}** バージョンのExtensionに反映後、再び審査をリクエストします。
* [基本情報](/DevConsole/Guides/CEK/Register_Extension.md#InputSkillInfo)
* [対話モデル](/DevConsole/Guides/CEK/Register_Extension.md#RegisterInteractionModel)
* [開発設定](/DevConsole/Guides/CEK/Register_Extension.md#SetDevConfiguration)
* [ユーザー設定](/DevConsole/Guides/CEK/Register_Extension.md#SetUserConfiguration)
* [審査情報](/DevConsole/Guides/CEK/Deploy_Extension.md#InputReviewInfo)

審査を通過すると、**{{ book.DevConsole.cek_status_prd }}** バージョンから、アップデートが反映された **{{ book.DevConsole.cek_status_dev }}** バージョンに置き換えられます。その後、**{{ book.DevConsole.cek_status_prd }}** バージョンのExtensionをコピーし、**{{ book.DevConsole.cek_status_dev }}** バージョンのExtensionが生成されます。

以下の図は、Clova Developer CenterでExtensionがアップデートされる仕組みを示します。

![](/DevConsole/Assets/Images/DevConsole-Branch_Chart_For_Extension_Update.png)

現在サービス中の状態を"A"とした場合、開発者が修正するバージョンと、エンドユーザーに提供されるバージョンは次のようになります。

|  審査状況  | 開発者が編集 | エンドユーザーに提供 |
| :--------: | :----------: | :------------------: |
|   審査中   |      A'      |          A           |
| 審査通過後 |      A'      |          A'          |
| 審査不通過 |      A'      |          A           |
