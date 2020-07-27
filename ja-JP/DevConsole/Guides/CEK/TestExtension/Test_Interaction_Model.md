## 対話モデルをビルドする {#BuildInteractionModel}

[対話モデルの登録](/DevConsole/Guides/CEK/Register_Extension.md#RegisterInteractionModel)が完了すると、対話モデルの[テスト](#TestInteractionModel)を行うことができますが、事前にビルドが必要です。作成した対話モデルは次のようにビルドすることができます。

<ol>
  <li>登録済みのスキルのリストから、ビルドするスキルの<strong>{{ book.DevConsole.cek_edit }}</strong>メニューをクリックします。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Analytics_Console_Home.png" />
  <li>左のメニューから、<strong>{{ book.DevConsole.cek_interaction_model }}</strong>メニューをクリックします。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Interaction_Model_Menu.png" />
  <li><strong>{{ book.DevConsole.cek_edit_interaction_model }}</strong>ボタンをクリックして、{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}を開きます。</li>
  <li><strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>画面で、左上にある<strong>{{ book.DevConsole.cek_builder_menu_build }}</strong>ボタンをクリックすると、対話モデルのビルドが開始されます。対話モデルのサイズなどによって、数分かかることがあります。ビルド中はボタンの表示が<strong>{{ book.DevConsole.cek_builder_menu_build_in_progress }}</strong>に変わります。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Build_Interaction_Model.png" />
  <li>ビルドが完了すると、ボタンの表示が<strong>{{ book.DevConsole.cek_builder_menu_build }}</strong>に戻ります。</li>
</ol>

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ビルド中に<strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>内で他のメニューに移動しても、ビルドはキャンセルされません。ビルドが開始されてからも、自由にメニューを移動することができます。</p>
</div>

## 対話モデルをテストする {#TestInteractionModel}

[対話モデルのビルド](#BuildInteractionModel)が完了すると、テストができるようになります。元のウィンドウの上部にあるタブメニューで **{{ book.DevConsole.cek_builder_test_title }}** をクリックすると、**テスト** 画面が表示されます。

テスト画面では、次の2種類のテストを実行できます。

* **[対話モデルテストモード](#InteractionModelTestMode)**：任意のインテントのサンプル発話を入力して、インテントやスロットの解析結果やExtensionへのリクエストメッセージを確認できます。
* **[シナリオテストモード](#ScenarioTestMode)**：`LaunchRequest`から`SessionEndedRequest`までの一連のシナリオをテストできます。

テスト画面の構成は次のようになっています。
![](/DevConsole/Assets/Images/DevConsole-Test_Main.png)

<ol>
  <li><strong>テスト対象</strong>：ドロップダウンリストでテストする対話モデルを選択します。
    <ul>
      <li><strong>{{ book.DevConsole.cek_status_dev }}</strong>：登録済みのスキルのリストで公開状態が<strong>{{ book.DevConsole.cek_status_dev }}</strong>のバージョン。対話モデル等の編集が可能です。</li>
      <li><strong>{{ book.DevConsole.cek_status_reviewing }}</strong>：登録済みのスキルのリストで公開状態が<strong>{{ book.DevConsole.cek_status_reviewing }}</strong>で、その時点で審査申請が完了しているバージョン。対話モデル等の編集はできません。</li>
      <li><strong>{{ book.DevConsole.cek_status_prd }}</strong>：登録済みのスキルのリストで公開状態が<strong>{{ book.DevConsole.cek_status_prd }}</strong>で、スキルストアで公開されているバージョン。対話モデル等の編集はできません。</li>
    </ul>
  <li><strong>{{ book.DevConsole.cek_test_last_build }}</strong>：選択した対話モデルを最後にビルドした日時が表示されます。この日時以後に対話モデルを編集した場合は、テストを行う前に再度<a href="#BuildInteractionModel"><strong>ビルド</strong></a>を行う必要があります。</li>
  <li><strong>テストモード切替</strong>：トグルボタンで<strong>対話モデルテスト</strong>と<strong>シナリオテスト</strong>のモード切り替えを行います。デフォルトでは対話モデルテストモードが開きます。</li>
  <li><strong>起動</strong>／<strong>終了</strong>ボタン：<strong>シナリオテスト</strong>モードで使用します。<strong>起動</strong>ボタンをクリックすると、<code>LaunchRequest</code>が送信されます。<strong>終了</strong>ボタンをクリックすると<code>SessionEndedRequest</code>が送信されます。</li>
  <li><strong>チャットウィンドウ</strong>：入力したユーザーの発話と、それに対する<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong> を、会話形式で表示します。ウィンドウの右側にユーザーの発話内容、左側に{{ book.DevConsole.cek_builder_test_service_response }}が表示されます。</li>
  <li><strong>入力フィールド</strong>：テストしたい発話の内容を入力します。</li>
</ol>

### 対話モデルテストモード {#InteractionModelTestMode}

対話モデルテストモードでは、任意のインテントのサンプル発話を入力すると、インテントやスロットの解析結果やExtensionへのリクエストメッセージを確認することができます。テスト方法は次のとおりです。
<ol>
  <li>トグルボタンで<strong>対話モデルテスト</strong>モードに切り替えます。</li>
  <li><strong>入力フィールド</strong>にテストする発話を入力します。</li>
  <li>Enterキーを押すか、または<strong>{{ book.DevConsole.cek_builder_test_request_test }}</strong>ボタンをクリックします。</li>
</ol>

テストを実行すると、次のようなテスト結果が出力されます。各項目について返却された内容を確認してください。  

![](/DevConsole/Assets/Images/DevConsole-Test_Interaction_Model_Mode.png)

* チャットウィンドウに表示される **{{ book.DevConsole.cek_builder_test_service_response }}** から、[登録したCustom Extension](/DevConsole/Guides/CEK/Register_Extension.md)が正しく応答しているか確認します。
* **{{ book.DevConsole.cek_builder_test_service_response }}** の右に表示される **読み上げ** ボタンをクリックすると、レスポンス内容を読み上げることができます。
* **{{ book.DevConsole.cek_builder_test_intent_result }}** 項目と **{{ book.DevConsole.cek_builder_test_slot_result }}** 項目から、インテントとスロットが正しく認識されているか確認します。
* **{{ book.DevConsole.cek_builder_test_request_json }}** 項目から、CEKがCustom Extensionに送る[リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)を確認します。
* **{{ book.DevConsole.cek_builder_test_response_json }}** 項目から、登録したCustom Extensionが正しく[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返しているか確認します。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>
    <ul>
      <li>対話モデルテストモードでは、入力フィールドに新しいサンプル発話を入力して送信すると、直前のテスト履歴が削除されて、最新の結果だけが表示されます。</li>
      <li>トグルボタンをクリックしてテストモードを変更すると、テスト履歴が削除されます。</li>
      <li><strong>{{ book.DevConsole.cek_builder_test_request_json }}</strong> 項目のコードは、直接編集することができます。例えばスロットの値を変更して<strong>{{ book.DevConsole.cek_builder_test_test_again }}</strong>ボタンをクリックして再度テストを行い、<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>の違いを比較するといった使い方ができます。</li>
      <li>オーディオコンテンツの再生にAudioPlayerを使用している場合は、<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>として"AudioPlayerを利用したオーディオコンテンツはCLOVAデバイスで確認してください。"と表示され、テスト画面で再生することはできません。<a href="#DeviceTest">CLOVAデバイスでテスト</a>してください。</li>
      <li>オーディオコンテンツの再生にAudioPlayerを使用している状態で、入力フィールドに「次」「前」等と入力して送信した場合、"解析されたインテント"として<code>Clova.NextIntent</code>、<code>Clova.PreviousIntent</code>が返されません。CLOVAデバイスに話しかけた場合は正しくインテントが解析されるため、「次」「前」等の発話は<a href="#DeviceTest">CLOVAデバイスでテスト</a>してください。</li>
    </ul>
  </p>
</div>

### シナリオテストモード {#ScenarioTestMode}

シナリオテストモードでは、`LaunchRequest`から`SessionEndedRequest`までの一連のシナリオ（[マルチターン対話](/CEK/Guides/Build_Custom_Extension.md#DoMultiturnDialog)）をテストできます。テスト方法は次のとおりです。

<ol>
  <li>トグルボタンで<strong>シナリオテスト</strong>モードに切り替えます。</li>
  <li><strong>起動</strong>ボタンをクリックすると、<code>LaunchRequest</code>が送信されます。チャットウィンドウには、"＜スキル名＞を起動して"と表示され、スキルが起動した際のCLOVAの応答が表示されます。</li>
  <li><strong>入力フィールド</strong>にテストするサンプル発話を入力します。</li>
  <li>Enterキーを押すか、または<strong>{{ book.DevConsole.cek_builder_test_request_test }}</strong>ボタンをクリックします。</li>
  <li>対話を続ける場合は、3～4の手順を繰り返します。</li>
  <li><strong>終了</strong>ボタンをクリックすると、<code>SessionEndedRequest</code>が送信されて、マルチターン対話が終了します。入力フィールドに「終了して」等の発話を入力て送信した場合も、<strong>終了</strong>ボタンをクリックしたときと同様の動作になります。</li>
</ol>

テストを実行すると、次のようなテスト結果が出力されます。各項目について返却された内容を確認してください。  

![](/DevConsole/Assets/Images/DevConsole-Test_Scenario_Test_Mode.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>
    <li>シナリオテストモードでは、<strong>起動</strong>ボタンをクリックした後に入力フィールドに新しいサンプル発話を入力して送信してもチャットウィンドウ内のテスト結果は削除されず、表示は増えていきます。</li>
    <li>トグルボタンをクリックしてテストモードを変更すると、すべてのテスト履歴が削除されます。</li>
    <li><strong>{{ book.DevConsole.cek_builder_test_request_json }}</strong>には、最新のサービスリクエストのみが表示されます。また、JSONの編集や、{{ book.DevConsole.cek_builder_test_test_again }}はできません。</li>
    <li><strong>終了</strong>ボタンをクリック、または「終了して」等の発話を入力して<code>SessionEndedRequest</code>が送信された場合、再度<strong>起動</strong>ボタンをクリックするまで入力フィールドにサンプル発話を入力することはできません。</li>
  </p>
</div>
