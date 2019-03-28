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
2. **スキル設定** または **スキルを開発する** をクリックし、登録済みのスキルのリストを表示します。
3. サンプルサイコロの管理欄の **{{ book.DevConsole.cek_edit}}** ボタンをクリックします。
4. 上部タブメニューで **{{ book.DevConsole.cek_builder_test_title }}** メニューをクリックします。
5. テスト画面左下の入力フィールドに、ヘルプをリクエストするフレーズを入力します。例えば、「使い方を教えて」と入力します。
6. Enterキーを押すか、または **{{ book.DevConsole.cek_builder_test_request_test }}** ボタンをクリックします。
7. **{{ book.DevConsole.cek_builder_test_result_title }}** の **{{ book.DevConsole.cek_builder_test_intent_result }}** 項目に「Clova.GuideIntent」と表示されるか確認します。

	<img src="/CEK/Assets/Images/CEK_Tutorial_Builtin_Intent_Test.png" style="max-width:800px;"/>

  <div class="note">
    <p><strong>メモ</strong></p>
    <p>外部からアクセスできるExtensionサーバーのURLを登録していない場合、左側のチャットウィンドウ内に<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>として<strong>"エラーが発生しました。詳細は[サービス応答]欄をご確認ください。"</strong>と表示されます。</p>
	</div>
