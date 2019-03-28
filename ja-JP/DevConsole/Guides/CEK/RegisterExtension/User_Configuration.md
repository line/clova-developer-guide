## ユーザー設定を行う {#SetUserConfiguration}

Clova Developer Centerで[Extensionを登録](/DevConsole/Guides/CEK/Register_Extension.md)すると、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** に表示する情報の入力が可能になります。
左メニューから **{{ book.DevConsole.cek_user_configuration }}** を選択してください。

![](/DevConsole/Assets/Images/DevConsole-User_Config_Menu.png)

ユーザー設定では次の項目を設定します。
* [スキルストア](#InputSkillStoreInfo)
* [個人情報の保護および規約](#SetAccountLinking)

### スキルストアの情報を入力する {#InputSkillStoreInfo}

Extensionをユーザーに説明するための情報として、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** でユーザーに提供されます。次の順で情報を入力します。

![](/DevConsole/Assets/Images/DevConsole-Input_Skill_Store_Info.png)

1. **{{ book.DevConsole.cek_category }}**：Extensionのカテゴリです。ユーザーがカテゴリごとにExtensionを探したり、検索する際に利用されます。(今後サービス予定)
2. **{{ book.DevConsole.cek_countries_region }}**：現在、日本でのみExtensionを配布できます。
<!--
3. **{{ book.DevConsole.cek_short_skill_desc }}**：音声でスキルを説明するためのテキストです。
-->
3. **{{ book.DevConsole.cek_full_skill_desc }}**：**{{ book.DevConsole.ExtensionPage }}** でユーザーに提供するExtensionの説明です。案内に従って作成します。
4. **{{ book.DevConsole.cek_example_phrases }}**：ユーザーがExtensionをどのように使用できるかを示す例です。**{{ book.DevConsole.ExtensionPage }}** に表示されます。なお、1番目の例は **{{ book.DevConsole.StoreHome }}** にも表示されるため、「〜を起動して」「〜を開いて」など、スキルを起動するフレーズを含めて登録してください。（例：ねぇClova、ピザボットを起動して）
5. **{{ book.DevConsole.cek_keywords }}**：ユーザーが特定のキーワードでExtensionを検索する際に、その検索結果にExtensionが含まれるように設定します（カンマ区切りで5つまで登録可能）。スキルストアの検索機能の検索対象になります。
6. **{{ book.DevConsole.cek_large_icon }}**：スキルストアおよびClovaアプリで表示されるExtensionのアイコンファイルです。512x512ピクセルの円形もしくは正方形で作成してください。
7. **{{ book.DevConsole.cek_supported_clients }}** : Extensionが動作するClovaデバイスを選択します。チェックを外したデバイスからはスキルを呼び出すことができません。
8. **{{ book.DevConsole.cek_save }}** ボタンをクリックして、入力した内容を保存します。**{{ book.DevConsole.cek_next }}** をクリックすると、{{ book.DevConsole.cek_privacy }}の設定画面に遷移します。

このように入力された情報は、Clovaアプリの **{{ book.DevConsole.ManageExtensions }}** で次のように表示されます。

| {{ book.DevConsole.StoreHome }} | {{ book.DevConsole.ExtensionPage }} |
| :-----------------------------: | :---------------------------------: |
| ![Extension List](/DevConsole/Assets/Images/DevConsole-Store_UI_Example-Extension_Store_Home.png) | ![Extension Details](/DevConsole/Assets/Images/DevConsole-Store_UI_Example-Extension_Page.png) |

<div class="note">
  <p><strong>メモ</strong></p>
  <p><strong>{{ book.DevConsole.ExtensionPage }}</strong>に表示される一部の情報には、登録されている<a href="/DevConsole/Guides/CEK/Register_Extension.md#InputSkillInfo">Extensionの基本情報</a>が使用されます。</p>
</div>

### 個人情報の保護および規約の設定を行う {#InputComplianceInfo}

Extensionの配布に必要な情報を入力する最後の段階です。プライバシーポリシーおよびコンプライアンス関連の情報を入力します。Extensionの登録メニューで **{{ book.DevConsole.cek_privacy }}** を選択します。

![](/DevConsole/Assets/Images/DevConsole-Policy_Menu.png)

次のように情報を入力します。

![](/DevConsole/Assets/Images/DevConsole-Input_Policy.png)

1. **{{ book.DevConsole.cek_allow_purchase }}**：Extensionを使用する際、ユーザーが決済をしたり支払いをする場面がある場合、**{{ book.DevConsole.cek_yes }}** を選択します。
2. **{{ book.DevConsole.cek_use_personal_info }}**：Extensionがユーザーの個人情報を取得する場合、**{{ book.DevConsole.cek_yes }}** を選択します。
3. **{{ book.DevConsole.cek_privacy_policy_url }}**：Extensionが個人情報を取得する場合、それに関するプライバシーポリシーを提供するページを入力します。Extension説明ページの一番下に表示されます。
4. **{{ book.DevConsole.cek_terms_of_use }}**：Extensionに関する免責条項を提供するページのURLを入力します。プライバシーポリシーのURLと同じく、Extension説明ページの一番下に表示されます。
5. **{{ book.DevConsole.cek_save }}** ボタンをクリックして、入力した内容を保存します。**{{ book.DevConsole.cek_next }}** をクリックすると、テスト画面に遷移します。

**{{ book.DevConsole.cek_privacy_policy_url }}** と **{{ book.DevConsole.cek_terms_of_use }}** に入力された内容は、**{{ book.DevConsole.ExtensionPage }}** で次のように表示されます。

![](/DevConsole/Assets/Images/DevConsole-Store_UI_Example-Extension_Policy.png)
