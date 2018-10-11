サンプルサイコロExtensionで、ヘルプをリクエストするビルトインインテントが正しく処理するかテストする必要があります。

[1番目のチュートリアル](/CEK/Tutorials/Build_Simple_Extension.md)のように、2つのテスト方法があります。1つは、Clova Developer Centerで対話モデルの動作を確認する方法です。もう1つは、Clovaデバイスで実際の動作を確認する方法です。
このチュートリアルでは、対話モデルの動作のみ確認します。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ビルトインインテントは、対話モデルに明示的に登録しなくても動作します。
  今後、Extensionごとに必要なビルトインインテントのみ選択して登録できるように変更される予定です。</p>
</div>

次の順で、サンプルサイコロExtensionがヘルプのリクエストを正しく処理するか確認します。
1. <a href="{{ book.DeveloperConsoleURL }}" target="_blank">Clova Developer Center</a>に接続します。
2. サンプルサイコロの**{{ book.DevConsole.cek_interaction_model }}**項目の**{{ book.DevConsole.cek_edit}}**ボタンをクリックします。
3. 左側のメニューリストで**{{ book.DevConsole.cek_test }}**メニューをクリックします。
4. **{{ book.DevConsole.cek_builder_test_expression_title }}**にヘルプをリクエストするフレーズを入力します。例えば、「使い方を教えて」と入力します。
5. Enterキーを押すか、または**{{ book.DevConsole.cek_builder_test_request_test }}**ボタンをクリックします。
6. **{{ book.DevConsole.cek_builder_test_result_title }}**の**{{ book.DevConsole.cek_builder_test_intent_result }}**項目に「Clova.GuideIntent」と表示されるか確認します。

	<img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Intent_Test.png" style="max-width:800px;"/>

  <div class="note">
    <p><strong>メモ</strong></p>
    <p>外部からアクセスできるExtensionサーバーのURLを登録していない場合、<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>は「応答がありません。(undefined)」と表示されます。</p>
	</div>
