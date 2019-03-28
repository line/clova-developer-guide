# Extensionを登録する

LINE Developersコンソールで[チャネルを作成](/DevConsole/Guides/CEK/Create_Channel.md)すると、**Clova Developer Center β** に遷移し、次の画面が開きます。ここで必要な情報を入力し、Extensionの登録を完了させます。  
![](/DevConsole/Assets/Images/DevConsole-New_Extension.png)

Extensionの登録は、通常、次の順で行われます。

<ol>
  <li><a href="#AgreeTermsOfUse">利用規約およびLINE User Data Policyに同意する</a></li>
  <li><a href="#InputSkillInfo">Extensionの基本情報を入力する</a></li>
  <li><a href="#RegisterInteractionModel">対話モデルを登録する</a></li>
    <ul>
      <li><a href="#AddBuiltinSlotType">ビルトインスロットタイプを追加する</a></li>
      <li><a href="#AddCustomSlotType">カスタムスロットタイプを追加する</a></li>
      <li><a href="#AddBuiltinIntent">ビルトインインテントを追加する</a></li>
      <li><a href="#AddCustomIntent">カスタムインテントを追加する</a></li>
    </ul>
  <li><a href="#SetDevConfiguration">開発設定を行う</a>
    <ul>
      <li><a href="#SetServerConnection">サーバー設定を行う</a></li>
      <li><a href="#SetAccountLinking">アカウント連携を設定する</a></li>
    </ul>
  </li>
  <li><a href="#SetUserConfiguration">ユーザー設定を行う</a>
    <ul>
      <li><a href="#InputSkillStoreInfo">スキルストアの情報を入力する</a></li>
      <li><a href="#InputComplianceInfo">個人情報の保護および規約の設定を行う</a></li>
    </ul>
  </li>
</ol>

## 利用規約およびLINE User Data Policyに同意する {#AgreeTermsOfUse}

Extensionを登録するには、Clova Extensions Kit利用規約とLINE User Data Policyに同意する必要があります。それぞれの項目にチェックを入れ、**スキル開発を始める** をクリックします。  
![](/DevConsole/Assets/Images/DevConsole-Agree_Terms_of_Use_and_Collecting_Personal_Info.png)

{% include "/DevConsole/Guides/CEK/RegisterExtension/Skill_Information.md" %}

{% include "/DevConsole/Guides/CEK/RegisterExtension/Interaction_Model.md" %}

{% include "/DevConsole/Guides/CEK/RegisterExtension/Dev_Configuration.md" %}

{% include "/DevConsole/Guides/CEK/RegisterExtension/User_Configuration.md" %}
