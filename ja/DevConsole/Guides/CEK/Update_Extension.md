# Extensionをアップデートする

Extensionが審査を通過し、配布が承認されると、そのExtensionは **{{ book.DevConsole.cek_status_prd }}** 状態になります。Clova Developer Centerはその際、次のようにExtensionの2つのバージョンを作成します。

* **{{ book.DevConsole.cek_status_prd }}** バージョン：現在、**{{ book.DevConsole.cek_status_prd }}** 状態のExtensionの元の情報を持つバージョンです。Extension情報の照会のみできます。
* **{{ book.DevConsole.cek_status_dev }}** バージョン：配布されたExtensionの元の情報をコピーして作成されたバージョンです。Extensionをアップデートする際に使用されます。

![](/DevConsole/Resources/Images/DevConsole-Extension_List_After_Submission.png)

**{{ book.DevConsole.cek_status_prd }}** バージョンのExtensionは、現在サービス中の内容を反映しているため、修正することができません。Extensionをアップデートするには、コピーされた **{{ book.DevConsole.cek_status_dev }}** バージョンを使用します。Extensionに次の項目に該当するアップデート事項がある場合、**{{ book.DevConsole.cek_status_dev }}** バージョンのExtensionに反映後、再び審査をリクエストします。
* [基本情報](/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo)
* [サーバーとの連携情報](/DevConsole/Guides/CEK/Register_Extension.md#SetServerConnection)
* [対話モデル](/DevConsole/Guides/CEK/Register_Interaction_Model.md)
* [配布情報](/DevConsole/Guides/CEK/Deploy_Extension.md)

審査を通過すると、**{{ book.DevConsole.cek_status_prd }}** バージョンから、アップデートが反映された **{{ book.DevConsole.cek_status_dev }}** バージョンに置き換えられます。その後、**{{ book.DevConsole.cek_status_prd }}** バージョンのExtensionをコピーし、**{{ book.DevConsole.cek_status_dev }}** バージョンのExtensionが生成されます。

以下の図は、Clova Developer CenterでExtensionがアップデートされる仕組みを示します。

![](/DevConsole/Resources/Images/DevConsole-Branch_Chart_For_Extension_Update.png)
