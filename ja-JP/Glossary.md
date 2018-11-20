# 用語および略語

<div class="note">
  <p><strong>メモ</strong></p>
  <p>このページは随時更新されます。</p>
</div>

### CEK
[Clova Extensions Kit](#CEK)の略語

### CIC
[Clova Interface Connect](#CIC)の略語

### Clova {#Clova}
[Clova](https://clova.line.me/)は、{{ book.TargetServiceForClientAuth }}が開発およびサービスを提供しているAIプラットフォームです。ユーザーの音声を認識し、それを解析して、ユーザーの希望する情報やサービスを提供します。サードパーティの開発者は、Clovaの持つ技術を活用して、AIサービスを提供するデバイスまたは家電製品を製作できます。また、Clovaを利用して、保有しているコンテンツやサービスを提供することもできます。

### Clova Developer Center {#ClovaDeveloperCenter}
Clovaプラットフォームと連携するクライアントデバイス、または[Clova Extension](#ClovaExtension)を開発する開発者に次の内容を提供する<a target="_blank" href="{{ book.DeveloperConsoleURL }}">Webツール</a>です。
* クライアントデバイスの登録およびクライアントの認証情報を提供(今後サービス予定)
* Clova Extensionの[登録](/DevConsole/Guides/CEK/Register_Extension.md)および[配布](/DevConsole/Guides/CEK/Deploy_Extension.md)
* [対話モデルの登録](/DevConsole/Guides/CEK/Register_Interaction_Model.md)
* Clovaサービスに関する[統計資料の提供](/DevConsole/Guides/CEK/Use_Analytics.md)

### Clova Extension {#ClovaExtension}
音楽、ショッピング、金融などの外部のサービス(サードパーティサービス)、または家庭のIoTデバイスの制御など、Clovaの機能を拡張して、ユーザーに様々な経験を提供するWebアプリケーションです。通常、Extensionと呼ばれます。Clovaプラットフォームは、現在次のClova Extensionをサポートおよび提供しています。エンドユーザーには、「スキル」という表現で提供されます。
* [Custom Extension](#CustomExtension)
* [Clova Home Extension](#ClovaHomeExtension)

### Clova Extensions Kit(CEK) {#CEK}
Clova Extensionを開発および配布する際に、必要なツールとインターフェースを提供するプラットフォームです。[ClovaとExtensionのコミュニケーション](/CEK/CEK_Overview.md)をサポートしています。

### Clova Home Extension {#ClovaHomeExtension}
IoTデバイス制御サービスを提供するためのExtensionです。詳細については、[Clova Home Extensionを作成する](/CEK/Guides/Build_Clova_Home_Extension.md)ドキュメントを参照してください。

### Clova Home Extensionメッセージ {#ClovaHomeExtMessage}
IoTデバイスを制御する[Clova Home Extension](#ClovaHomeExtension)が[Clova Extensions Kit](#CEK)と情報のやり取りをする際、専用で使用するメッセージです。詳細については、[Clova Home Extensionメッセージ](/CEK/References/CEK_API_ClovaHome.md#ClovaHomeExtMessage)ドキュメントを参照してください。

### Clova Interface Connect(CIC) {#CIC}
AIアシスタントサービスを提供するコンピュータ/モバイルアプリ、モバイルデバイスまたは家電製品などのクライアントに、Clovaとの連携ができるインターフェースを提供するプラットフォームです。

### Clovaアプリ {#ClovaApp}
{{ book.OrientedService }}が開発し、iOSおよびAndroidプラットフォームで配布するモバイルアプリです。Clovaに指示を与えるだけでなく、クライアントデバイスを登録し、管理できるアプリです。

### Custom Extension {#CustomExtension}
任意の拡張された機能を提供する[Extension](#ClovaExtension)です。Custom Extensionを利用すると、音楽、ショッピング、金融など、外部サービスの機能を提供できます。詳細については、[Custom Extensionを作成する](/CEK/Guides/Build_Custom_Extension.md)ドキュメントを参照してください。

### Custom Extensionメッセージ {#CustomExtMessage}
[Clova Extensions Kit](#CEK)と[Custom Extension](#CustomExtension)が情報のやり取りをする際に使用するメッセージです。詳細については、[Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)ドキュメントを参照してください。

### Discovery機能 {#Discovery}
ユーザーアカウントに登録されたIoTデバイスのリストをクライアントデバイスに提供する機能です。詳細については、[Discoveryを提供する](/CEK/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery)ドキュメントを参照してください。

### Extension {#Extension}
[Clova Extension](#ClovaExtension)の別名

### Extensionページ {#ExtensionPage}
[スキルストアホーム](#SkillStoreHome)で特定のExtensionを選択すると表示されるページです。Extensionに関する詳しい説明が提供されます。

### HTTP/2 {#HTTP2}
HTTPのバージョンの1つです。[SPDY](https://en.wikipedia.org/wiki/SPDY)に基づき、インターネット技術タスクフォース(IETF)において開発されています。1997年にRFC 2068として規定されたHTTP/1.1をバージョンアップしたものであり、2014年12月にProposed Standard(標準への提唱)として制定され、2015年2月17日にIESGで正式な仕様として承認されました。2015年5月に<a href="https://tools.ietf.org/html/rfc7540" target="_blank">RFC 7540</a>として公開されました。

### IntentRequest {#IntentRequest}
ユーザーのリクエストを解析した結果([インテント](#Intent))を[Custom Extension](#CustomExtension)に送る際に使用されるリクエストメッセージタイプです。詳細については、[Custom Extensionリクエストを処理する](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest)ドキュメントを参照してください。

### LaunchRequest {#LaunchRequest}
ユーザーが特定のモードまたは特定の[Custom Extension](#CustomExtension)を使用すると宣言したことを知らせるために送るリクエストメッセージです。詳細については、[Custom Extensionリクエストを処理する](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest)ドキュメントを参照してください。

### OAuth 2.0
アクセス権限を委任するためのオープンスタンダードです。インターネットのユーザーが他のウェブサービスやアプリケーションのユーザーアカウントにアクセスできる権限を付与する規約です。Clovaプラットフォームでは、クライアントが[Clovaアクセストークン](#ClovaAccessToken)を取得したり、ユーザーが特定のExtensionを使用する際、自身の[アカウントを連携](/CEK/Guides/Link_User_Account.md)するために使用されます。詳細については、[https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749)を参照してください。

### SessionEndedRequest {#SessionEndedRequest}
ユーザーが特定のモードまたは特定の[Custom Extension](#CustomExtension)の使用を中止すると宣言した際に送られるリクエストメッセージです。詳細については、[Custom Extensionリクエストを処理する](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest)ドキュメントを参照してください。

### アカウント連携 {#AccountLinking}
[Extension](#ClovaExtension)がユーザーのアカウント認証を必要とする外部サービスを提供する際に使用されます。詳細については、[ユーザーアカウントを連携する](/CEK/Guides/Link_User_Account.md)ドキュメントを参照してください。

### インテント {#Intent}
Clova Extensionが処理するユーザーの意図を区分したカテゴリです。カスタムインテントとビルトインインテントの2種類があります。[Custom Extension](#CustomExtension)を実装する前に、まずインテントの集合である[対話モデル](#InteractionModel)を定義する必要があります。詳細については、[対話モデルを定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)ドキュメントを参照してください。

### スキル {#Skill}
Clovaが提供する拡張機能のことをいいます。スキルをユーザーに提供するには、[Clova Extension](#ClovaExtension)を開発する必要があります。

### スキルストア {#SkillStore}
[Extension](#ClovaExtension)をユーザーに提供するために構築されたプラットフォームです。

### スキルストアホーム {#SkillStoreHome}
[スキルストア](#SkillStore)に登録されたExtensionが表示されるページです。[Clovaアプリ](#ClovaApp)の設定メニューからアクセスします。

### スロット {#Slot}
[インテント](#Intent)に宣言されたリクエストを処理する際に必要な情報です。インテントを定義するとき、共に定義する必要があります。Clovaはユーザーのリクエストを解析して、スロットに該当する情報を抽出します。詳細については、[対話モデルを定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)ドキュメントを参照してください。

### セッションID {#SessionID}
[Extension](#ClovaExtension)がユーザーリクエストのコンテクストを区分するためのセッション識別子です。通常、1回で終わるユーザーリクエストはそのたびにセッションIDが変わりますが、特定のモードや連続的な(マルチターン)ユーザーリクエストの場合、同じセッションIDを持ちます。このセッションIDは、[Clova Extensions Kit](#CEK)がExtensionにユーザーのリクエストを渡すとき生成されます。セッションIDが維持されるのは、[LaunchRequest](#LaunchRequest)のようなリクエストを受け取ったか、またはExtensionが必要に応じて`response.shouldEndSession`フィールドを`false`に設定した場合です。詳細については、[Custom Extensionを作成する](/CEK/Guides/Build_Custom_Extension.md)ドキュメントを参照してください。

### 対話モデル {#InteractionModel}
[Custom Extension](#CustomExtension)が音声から認識されたユーザーのリクエストをExtensionに送るために、標準化したフォーマット(JSON)に変換するルールを指定したものです。詳細については、[対話モデルを定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)ドキュメントを参照してください。

### ビルトインスキル {#BuiltinSkill}
Clovaデバイスに標準で搭載されているスキルで、ミュージック、LINE送受信、LINE無料通話、天気、ニュース、アラーム・タイマーなどがあります。詳細については、[Clova > Clovaのスキル](https://clova.line.me/clova-ai/) を参照してください。

### ユーザーのサンプル発話 {#UserUtteranceExample}

ユーザーのリクエスト発話がどのように入力されるかを例で表現したリストです。[インテント](#Intent)ごとに複数の例を定義できます。また、例には[スロット](#Slot)が表示されます。詳細については、[対話モデルを定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)ドキュメントを参照してください。
