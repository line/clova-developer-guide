# CEKの概要
このドキュメントでは、Clova Extensions Kit(以下、CEK)について説明します。Extensionの開発者は、このドキュメントから、CEKとは何で、どのような仕組みで動作するかを理解できます。また、ここではCEKに関するガイドとリファレンスも提供されます。

## CEKとは? {#WhatisCEK}
CEKは、Clova Extension(以下、Extension)を開発および配布する際に必要なツールとインターフェースを提供するプラットフォームです。ClovaプラットフォームとExtension間のデータの送受信をサポートします。Extensionは、音楽、ショッピングなどの外部のサービス(サードパーティサービス)、または家庭のIoTデバイスの制御など、Clovaの機能を拡張して、ユーザーに様々な体験を提供するWebアプリケーションです。

![](/CEK/Assets/Images/CEK_Concept_Diagram.png)

CEKは次の機能を提供します。
* [対話モデル](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)の管理([Clova Developer Center](/DevConsole/ClovaDevConsole_Overview.md)で使用可能)
* ClovaとExtension間のインターフェース

## CEKの仕組み {#CEKInteractionStructure}
Clovaは、CICから入力されたユーザーの発話を認識し、CEKを介して、あらかじめ[登録された対話モデル](/DevConsole/Guides/CEK/Register_Extension.md#RegisterInteractionModel)を参照してユーザーの発話を解析します。CEKは解析されたユーザーの発話をExtensionに渡し、Extensionはユーザーリクエストの処理結果をレスポンスとして返す必要があります。その際、すでに定義されたメッセージフォーマットに合わせてメッセージのやり取りをします。CEKとExtensionは<a href="https://tools.ietf.org/html/rfc2616" target="_blank">HTTP/1.1</a>で通信します。

ClovaプラットフォームとExtensionのデータフローは以下のようになります。

![](/CEK/Assets/Images/CEK_Interaction_Structure.png)


## Extensionの種類 {#ExtensionType}
Clovaプラットフォームは、次の2種類のExtensionをサポートおよび提供しています。

* [Custom Extension](/CEK/Guides/Build_Custom_Extension.md)：サードパーティが機能を新しく提供することができるExtensionです。Custom Extensionを利用すると、音楽、ショッピングなど、外部サービスの機能を提供できます。
* [Clova Home Extension](/CEK/Guides/Build_Clova_Home_Extension.md)：IoTデバイス制御サービスを提供するExtensionです。
