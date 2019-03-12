## Clovaデバイスでテストする {#DeviceTest}

対話モデルの動作確認はClovaデバイスからも可能です。審査提出前にClovaデバイスからも動作確認をしてください。例えば、"りんご"という発話の表記には、林檎、リンゴ、りんごといったバリエーションがあります。サンプル発話やスロットの設定をする際には発話がどのような表記で対話モデルに入力されるのかを確認してください。

音声での入力がどのようなテキストに認識されるのかを確認するためのツールが、発話履歴テストツールです。
発話履歴ツールを開くには、登録済みのスキルのリストから任意のスキルの<strong>{{ book.DevConsole.cek_edit }}</strong>メニューを選択して設定画面を開き、左メニューの<strong>{{ book.DevConsole.cek_interaction_model }}</strong>をクリックします。そして<strong>{{ book.DevConsole.cek_edit_interaction_model }}</strong>ボタンをクリックして<strong>{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}</strong>を開き、メニューの左下にある<strong>{{ book.DevConsole.cek_device_test }}</strong>をクリックします。

![](/DevConsole/Resources/Images/DevConsole-DeviceTest_Menu.png)

この画面では、Clova Developer Centerにログインしているのと同じユーザーがログインしているClovaデバイスからの発話履歴を表示することができます。
発話の取得を開始するには、<strong>{{ book.DevConsole.cek_builder_device_test_start_button }}</strong>ボタンを押してください。ログ取得を開始してからClovaデバイスに向けて話しかけられた発話履歴のみを表示することができます。また、画面を閉じた場合には発話履歴を閲覧することはできませんので、発話を確認するにはツールを開いてから、毎回 <strong>{{ book.DevConsole.cek_builder_device_test_start_button }}</strong>ボタンを押してください。

![](/DevConsole/Resources/Images/DevConsole-DeviceTest_StartTest.png)
