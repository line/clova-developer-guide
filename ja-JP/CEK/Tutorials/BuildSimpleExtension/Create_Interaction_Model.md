<a href="{{ book.DeveloperConsoleURL }}" target="_blank">Clova Developer Center</a>で対話モデルを登録します。

対話モデルに保存する情報は[インテント](/Design/Design_Guideline_For_Extension.md#Intent)と[スロット](/Design/Design_Guideline_For_Extension.md#Slot)です。インテントは入力されたフレーズを解析してExtensionサーバーに渡す情報で、スロットはそのインテントの解析に必要な情報です。

サンプルサイコロは、ユーザーからサイコロの数の指定なしにサイコロを振るようにリクエストされると、デフォルトで1つのサイコロを振ります。ここでは、このように1つのサイコロを振るという指示を処理する、簡単な対話モデルを使用することにします。サイコロの数を収集しないため、スロットを持たないインテントを1つ登録することになります。

### 新規のカスタムインテントを作成する
ここでは、サイコロを振れというリクエストに対し、1つのサイコロを振る、簡単なインテントを作成します。

1. 設定画面の左メニューから、**{{ book.DevConsole.cek_interaction_model }}** を選択します。
2. **{{ book.DevConsole.cek_edit_interaction_model }}** ボタンをクリックし、**{{ book.DevConsole.cek_builder_header_title_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** 画面を表示します。
3. **{{ book.DevConsole.cek_builder_list_title_intent }}**の右側にある<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
4. **{{ book.DevConsole.cek_builder_new_intent }}**の下の入力ウィンドウに「ThrowDiceIntent」と名前を入力します。
5. Enterキーを押すか、または入力ウィンドウの右側にある**{{ book.DevConsole.cek_builder_new_intent_create }}**ボタンをクリックします。

	<img src="/CEK/Resources/Images/CEK_Tutorial_NewIntent.png" style=" max-width:800px;" />

	<div class="danger">
		<p><strong>注意</strong></p>
		<p>インテント名の大文字・小文字の区別に注意します。</p>
	</div>

### サンプル発話のリストに文章を入力する
ここでは、ユーザーが発する文章のうち、どんなものをインテントとして処理するか指定します。サンプル発話の数は多ければ多いほど良いですが、このチュートリアルでは1つだけ入力します。
1. **{{ book.DevConsole.cek_builder_intent_expression_title }}**に「サイコロを振って」と入力します。
2. Enterキーを押すか、または<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
3. すべてのサンプル発話を入力して、**{{ book.DevConsole.cek_save }}**をクリックします。

	<img src="/CEK/Resources/Images/CEK_Tutorial_SpeechExample.png" style=" max-width:800px; margin-top:10px; margin-bottom:10px;" />

### ビルドおよびテストする
対話モデルが入力された通りに動作するか確認するために、対話モデルをビルドしてテストします。

1. **{{ book.DevConsole.cek_builder_header_title_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** 画面の左上にある**{{ book.DevConsole.cek_builder_menu_build}}**ボタンをクリックします。

	<div class="note">
		<p><strong>メモ</strong></p>
		<p>ビルドには数分かかります。ビルドが開始されると<strong>{{ book.DevConsole.cek_builder_menu_build_in_progress }}</strong>に変わり、ビルドが完了すると<strong>{{ book.DevConsole.cek_builder_menu_build}}</strong>に戻ります。</p>
	</div>

2. ビルドが完了すると、**{{ book.DevConsole.cek_builder_menu_build}}**ボタンの下にある**{{ book.DevConsole.cek_test }}**メニューをクリックします。

3. **{{ book.DevConsole.cek_builder_test_expression_title }}**にテストする文章を入力します。例えば、「サイコロを振って」と入力します。
4. Enterキーを押すか、または**{{ book.DevConsole.cek_builder_test_request_test }}**ボタンをクリックします。
5. **{{ book.DevConsole.cek_builder_test_result_title }}**の**{{ book.DevConsole.cek_builder_test_intent_result }}**項目に「ThrowDiceIntent」と表示されるか確認します。

	<img src="/CEK/Resources/Images/CEK_Tutorial_Test.png" style="max-width:800px;"/>

	<div class="note">
		<p><strong>メモ</strong></p>
		<p>ステップ2で、外部からアクセスできるExtensionサーバーのURLを登録していない場合、<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>は「応答がありません。(undefined)」と表示されます。</p>
	</div>
