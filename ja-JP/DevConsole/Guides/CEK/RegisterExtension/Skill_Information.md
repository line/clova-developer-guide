## Extensionの基本情報を入力する {#InputSkillInfo}

Extensionを登録する最初のステップは、登録するExtensionの基本情報を入力することです。
Extensionの基本情報は、Clova Developer CenterでExtensionを作成するための必須で最小限の情報です。Extensionの基本情報を入力し{{ book.DevConsole.cek_create }}ボタンを押下すると、スキル設定画面の登録済みスキルに表示されるようになります。ここで入力した情報は、{{ book.DevConsole.cek_id }}以外は修正可能です。

次の順でExtensionの各項目を登録します。

![](/DevConsole/Assets/Images/DevConsole-Create_New_Extension.png)
<ol>
  <li>次の項目を入力します。
    <ol>
      <li><strong>{{ book.DevConsole.cek_id }}</strong>：Extensionの一意のIDです。リバースドメインネームの形式で入力します。(例：com.example.myservice)</li>
      <li><strong>{{ book.DevConsole.cek_name }}</strong>：Extensionの名前です。スキルストアに正式名称として表示されます。</li>
      <li><strong>{{ book.DevConsole.cek_name_furigana }}</strong>：Clovaがスキルの名称を音声で読み上げるときに使用する項目で、Clovaがスキル名を正しく読み上げられない際に設定します。「生物（せいぶつ/なまもの）」や「1日（ついたち/いちにち）」のように読み方が複数ある場合や、アルファベット表記のよみがなを指定したい場合などに、ひらがな等を入力することで、スキルストアの画面上の表記を変更することなく、開発者の意図通りに発音させることができます。</li>
      <li><strong>{{ book.DevConsole.cek_invocation_name }}</strong>：ユーザーがExtensionを呼び出す際に呼ぶ名前です。保有しているサービス、会社および組織の名前を使用できますが、ユーザーにとって呼びやすい、シンプルな言葉を指定することをお勧めします。他社の名前やサービスに該当する言葉は使用できません。</li>
        <li><strong>{{ book.DevConsole.cek_additional_invocation_name }}</strong>：{{ book.DevConsole.cek_invocation_name }}は音声認識結果によって表記がゆらぐ可能性があります。Extensionを正しく呼び出すために、必須項目の{{ book.DevConsole.cek_invocation_name }}のほか、追加で4つの<strong>{{ book.DevConsole.cek_additional_invocation_name }}</strong>を設定することができます。スキルを起動しやすくするための適切な呼び出し名（サブ）を設定する方法については、<a href="/Design/Design_Guideline_For_Extension.md#DefineSubInvocationName">こちら</a>を参照してください。</li>
    </ol>
  <li>Extensionの基本情報をすべて入力したら、<strong>{{ book.DevConsole.cek_create }}</strong>ボタンをクリックします。</li>
</ol>

Extensionの登録が完了すると、作成されたExtensionの情報を編集する画面に切り替わります。ページの下にある **{{ book.DevConsole.cek_save }}** ボタンをクリックして、入力中の内容を保存することができます。**{{ book.DevConsole.cek_next }}** をクリックすると、{{ book.DevConsole.cek_interaction_model }}の登録画面に遷移します。  
![](/DevConsole/Assets/Images/DevConsole-Edit_Extension.png)

またExtensionの登録が完了すると、CEKのメニューで、登録済みのExtensionのリストを確認することもできます。各Extensionの **管理** 項目の **編集** をクリックすると、**基本情報** の登録画面に遷移します。   
![](/DevConsole/Assets/Images/DevConsole-Extension_List_After_Creation.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>呼び出し名(メイン)や呼び出し名(サブ)が反映されるまでに数分時間がかかる場合があります。</p>
</div>
