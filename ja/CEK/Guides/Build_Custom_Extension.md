# Custom Extensionを作成する

Custom Extensionとは、Clovaが基本的に提供している機能やサービスではなく、開発者が任意に拡張した機能や、外部のサービスを提供するExtensionです。例えば、ウェブ検索やニュースクリッピングなどのサービスだけでなく、ユーザーアカウント認証の必要な音楽、ショッピング、金融などの外部サービスを提供することができます。Custom Extensionは、解析されたユーザーの発話情報をCEKから受け取り、その内容を処理して、サービスの処理結果を返す必要があります。

このドキュメントでは、Custom Extensionを作成する際の準備事項と、Custom ExtensionがCEKとどのようなメッセージのやり取りをして、どのように動作する必要があるかについて、次の内容を説明します。

* [準備事項](#Preparation)
* [Custom Extensionリクエストを処理する](#HandleCustomExtensionRequest)
   * [`LaunchRequest`リクエストを処理する](#HandleLaunchRequest)
   * [`IntentRequest`リクエストを処理する](#HandleIntentRequest)
   * [`SessionEndedRequest`リクエストを処理する](#HandleSessionEndedRequest)
* [Custom Extensionレスポンスを返す](#ReturnCustomExtensionResponse)
* [マルチターン対話をする](#DoMultiturnDialog)
* [オーディオコンテンツを提供する](#ProvideAudioContent)

<div class="danger">
 <p><strong>注意</strong></p>
 <p>Custom Extensionは、現時点ではClova WAVEでは動作確認することができません。</p>
</div>

{% include "/CEK/Guides/BuildCustomExtension/Preparation.md" %}

{% include "/CEK/Guides/BuildCustomExtension/Handle_Custom_Extension_Request.md" %}

{% include "/CEK/Guides/BuildCustomExtension/Return_Custom_Extension_Response.md" %}

{% include "/CEK/Guides/BuildCustomExtension/Do_Multiturn_Dialog.md" %}

{% include "/CEK/Guides/BuildCustomExtension/Provide_Audio_Content.md" %}
