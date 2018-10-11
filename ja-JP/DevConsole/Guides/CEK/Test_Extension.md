# 対話モデルをテストする

登録したExtensionと対話モデルは、配布する前にテストすることができます。次の項目を確認して、Extensionと対話モデルをテストします。

* (Custom Extension専用)[対話モデルをビルドする](#BuildInteractionModel)
* (Custom Extension専用)[対話モデルをテストする](#TestInteractionModel)

## 対話モデルをビルドする {#BuildInteractionModel}

Custom Extensionを配布する場合、先に[対話モデルを登録](/DevConsole/Guides/CEK/Register_Interaction_Model.md)しておく必要があります。また、対話モデルの[テスト](#TestInteractionModel)や実行には、ビルドが必要です。作成した対話モデルは次のようにビルドすることができます。

<ol>
  <li>登録したExtensionのリストから、ビルドする対話モデルの<strong>{{ book.DevConsole.cek_edit }}</strong>メニューをクリックします。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Interaction_Model_Menu.png" />
  <li><strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>画面で、左上にある<strong>{{ book.DevConsole.cek_builder_menu_build }}</strong>ボタンをクリックすると、対話モデルのビルドが開始されます。対話モデルのサイズなどによって、3~5分ぐらいかかることがあります。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Build_Interaction_Model.png" />
</ol>

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ビルド中に<strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>内で他のメニューに移動しても、ビルドはキャンセルされません。ビルドが開始されてからも、自由にメニューを移動したり、内容を編集したりできます。</p>
</div>

## 対話モデルをテストする {#TestInteractionModel}

[対話モデルのビルド](#BuildInteractionModel)が完了すると、テストができるようになります。テスト方法は次のとおりです。

<ol>
  <li>左側のナビゲーションで<strong>{{ book.DevConsole.cek_test }}</strong>メニューをクリックします。メニューをクリックすると、<strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_test }}</strong>画面が表示されます。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Test_Menu.png" />
  <li><strong>{{ book.DevConsole.cek_builder_test_expression_title }}</strong>フィールドにテストする発話を入力し、<strong>{{ book.DevConsole.cek_builder_test_request_test }}</strong>ボタンをクリックします。</li>
  <img src="/DevConsole/Resources/Images/DevConsole-Test_Utterance_Example.png" />
</ol>

テストを実行すると、次のようなテスト結果が出力されます。各項目について返却された内容を確認してください。

* **{{ book.DevConsole.cek_builder_test_service_response }}**項目から、[登録したCustom Extension](/DevConsole/Guides/CEK/Register_Extension.md)が正しく応答しているか確認します。
* **{{ book.DevConsole.cek_builder_test_intent_result }}**項目と**{{ book.DevConsole.cek_builder_test_slot_result }}**項目から、インテントとスロットが正しく認識されているか確認します。
* **{{ book.DevConsole.cek_builder_test_request_json }}**項目から、CEKがCustom Extensionに送る[リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)に異常がないか確認します。JSONファイルを修正してから**{{ book.DevConsole.cek_builder_test_test_again }}**ボタンをクリックすると、再度テストできます。
* **{{ book.DevConsole.cek_builder_test_response_json }}**項目から、登録したCustom Extensionが正しく[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返しているか確認します。

![](/DevConsole/Resources/Images/DevConsole-Test_Result.png)

