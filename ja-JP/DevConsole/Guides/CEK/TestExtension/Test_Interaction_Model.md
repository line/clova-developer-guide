## 対話モデルをビルドする {#BuildInteractionModel}

[対話モデルの登録](/DevConsole/Guides/CEK/Register_Extension.md#RegisterInteractionModel)が完了したら、対話モデルの[テスト](#TestInteractionModel)を行うことができますが、事前にビルドが必要です。作成した対話モデルは次のようにビルドすることができます。

<ol>
  <li>登録済みのスキルのリストから、ビルドするスキルの<strong>{{ book.DevConsole.cek_edit }}</strong>メニューをクリックします。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Analytics_Console_Home.png" />
  <li>左のメニューから、<strong>{{ book.DevConsole.cek_interaction_model }}</strong>メニューをクリックします。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Interaction_Model_Menu.png" />
  <li><strong>{{ book.DevConsole.cek_edit_interaction_model }}</strong>ボタンをクリックして、{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}を開きます。</li>
  <li><strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>画面で、左上にある<strong>{{ book.DevConsole.cek_builder_menu_build }}</strong>ボタンをクリックすると、対話モデルのビルドが開始されます。対話モデルのサイズなどによって、数分かかることがあります。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Build_Interaction_Model.png" />
</ol>

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ビルド中に<strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>内で他のメニューに移動しても、ビルドはキャンセルされません。ビルドが開始されてからも、自由にメニューを移動することができます。</p>
</div>

## 対話モデルをテストする {#TestInteractionModel}

[対話モデルのビルド](#BuildInteractionModel)が完了すると、テストができるようになります。テスト方法は次のとおりです。

<ol>
  <li>上部タブメニューで<strong>テスト</strong>をクリックすると、<strong>テスト</strong>画面が表示されます。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Test_Menu.png" />
  <li><strong>{{ book.DevConsole.cek_builder_test_expression_title }}</strong>フィールドにテストする発話を入力し、<strong>{{ book.DevConsole.cek_builder_test_request_test }}</strong>ボタンをクリックします。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Test_Utterance_Example.png" />
</ol>

テストを実行すると、次のようなテスト結果が出力されます。各項目について返却された内容を確認してください。

* **{{ book.DevConsole.cek_builder_test_service_response }}** 項目から、[登録したCustom Extension](/DevConsole/Guides/CEK/Register_Extension.md)が正しく応答しているか確認します。
* **{{ book.DevConsole.cek_builder_test_intent_result }}** 項目と **{{ book.DevConsole.cek_builder_test_slot_result }}** 項目から、インテントとスロットが正しく認識されているか確認します。
* **{{ book.DevConsole.cek_builder_test_request_json }}** 項目から、CEKがCustom Extensionに送る[リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)を確認します。**{{ book.DevConsole.cek_builder_test_test_again }}** ボタンをクリックすると、再度リクエストを送信し、テストすることができます。
* **{{ book.DevConsole.cek_builder_test_response_json }}** 項目から、登録したCustom Extensionが正しく[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返しているか確認します。

![](/DevConsole/Resources/Images/DevConsole-Test_Result.png)
