## CLOVAデバイスでテストする {#DeviceTest}

対話モデルの動作確認はCLOVAデバイスからも可能です。審査提出前にCLOVAデバイスからも動作確認をしてください。例えば、"りんご"という発話の表記には、林檎、リンゴ、りんごといったバリエーションがあります。サンプル発話やスロットの設定をする際には発話がどのような表記で対話モデルに入力されるのかを確認してください。

音声での入力がどのようなテキストに認識されるのかを確認するためのツールが、発話履歴テストツールです。
発話履歴ツールを開くには、登録済みのスキルのリストから任意のスキルの **{{ book.DevConsole.cek_edit }}** メニューを選択して設定画面を開き、左メニューの **{{ book.DevConsole.cek_interaction_model }}** をクリックします。そして **{{ book.DevConsole.cek_edit_interaction_model }}** ボタンをクリックして **{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** を開き、メニューの左下にある **{{ book.DevConsole.cek_device_test }}** をクリックします。

![](/DevConsole/Assets/Images/DevConsole-DeviceTest_Menu.png)

この画面では、CLOVA Developer Centerへのログインで使用したものと同じアカウントでログインしたCLOVAデバイスからの発話履歴を表示することができます。

発話の取得を開始するには、**{{ book.DevConsole.cek_builder_device_test_start_button }}** ボタンを押してください。ログ取得を開始してからCLOVAデバイスに向けて話しかけられた発話履歴のみを表示することができます。また、画面を閉じた場合には発話履歴を閲覧することはできませんので、発話を確認するにはツールを開いてから、毎回 **{{ book.DevConsole.cek_builder_device_test_start_button }}** ボタンを押してください。

![](/DevConsole/Assets/Images/DevConsole-DeviceTest_StartTest.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>CLOVAデバイスでテストできるのは、公開状態が<strong>{{ book.DevConsole.cek_status_dev }}</strong>のバージョンです。また、審査申請を行って公開状態が<strong>{{ book.DevConsole.cek_status_reviewing }}</strong>となっている場合は、テスト対象は<strong>{{ book.DevConsole.cek_status_reviewing }}</strong>バージョンとなります。公開状態の違いについては、<a href="https://clova-developers.line.biz/guide/DevConsole/Guides/CEK/Update_Extension.md" target="_blank">Extensionをアップデートする</a>を参照してください。</p>
</div>
