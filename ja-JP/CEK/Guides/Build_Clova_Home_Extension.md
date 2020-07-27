# CLOVA Home Extensionを作成する

CLOVA Home Extensionは、外部のIoTサービスを利用して、家庭内のIoTデバイスに遠隔操作機能を提供するExtensionです。CLOVA Home Extensionは、ユーザーが操作できるIoTデバイスの情報をCEKに提供する必要があります。また、CEKからIoTデバイス操作のリクエストを受け取り、それを処理して結果を返す必要があります。以下の図は、CLOVA Home Extensionの仕組みを示しています。

![](/CEK/Assets/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

{% include book.ClovaHome.restricted_note %}

CLOVA Home Extensionを作成する際の事前準備と、Custom ExtensionがCEKとどのようなメッセージをやり取りし、どのように動作するかについて説明します。

CLOVA Home Extensionの開発者は、次の内容を知っておく必要があります。

* [準備事項](#Preparation)
* [Discovery機能を提供する](#ProvideDeviceDiscovery)
* [CLOVA Home Extensionリクエストを処理する](#HandleClovaHomeExtensionRequest)
* [CLOVA Home Extensionレスポンスを返す](#ReturnClovaHomeExtensionResponse)
* [リクエストメッセージを検証する](#RequestMessageValidation)


{% include 'BuildClovaHomeExtension/Preparation.md' %}

{% include 'BuildClovaHomeExtension/Provide_Device_Discovery.md' %}

{% include 'BuildClovaHomeExtension/Provide_Scene_Discovery.md' %}

{% include 'BuildClovaHomeExtension/Handle_Clova_Home_Extension_Request.md'  %}

{% include 'BuildClovaHomeExtension/Return_Clova_Home_Extension_Response.md'  %}

{% include "BuildCustomExtension/Validating_Request_Message.md" %}

{% include book.ClovaHome.restricted_note %}
