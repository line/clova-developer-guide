## 対話モデルを登録する {#RegisterInteractionModel}

CEKがExtensionにユーザーのリクエストを送る際、ユーザーの発話をどう解析し、どんな形式で送るかを決めるために、あらかじめ[対話モデルを定義](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)する必要があります。対話モデルは、[Custom Extension](/CEK/Guides/Build_Custom_Extension.md)に渡されるリクエストを標準化したスキーマです。

対話モデルを登録するには、左メニューの **{{ book.DevConsole.cek_interaction_model }}** をクリックします。

![](/DevConsole/Assets/Images/DevConsole-Interaction_Model_Menu.png)

**{{ book.DevConsole.cek_edit_interaction_model }}** ボタンをクリックすると、**{{ book.DevConsole.cek_builder_header_title_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** 画面が表示されます。

![](/DevConsole/Assets/Images/DevConsole-Interaction_Model_Dashboard.png)

Extensionを設計するための[対話モデル](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)は、次の順で登録していきます。

1. [ビルトインスロットタイプを追加する](#AddBuiltinSlotType)
2. [カスタムスロットタイプを追加する](#AddCustomSlotType)
3. [ビルトインインテントを追加する](#AddBuiltinIntent)
4. [カスタムインテントを追加する](#AddCustomIntent)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>カスタムインテントを追加してから必要なスロットタイプを追加することもできますが、CLOVA Developer Centerの提供するUIの特性上、先にスロットタイプを追加してからインテントを追加することをお勧めします。</p>
</div>

### ビルトインスロットタイプを追加する {#AddBuiltinSlotType}

サービスを提供するExtensionがどの[ビルトインスロットタイプ](/Design/Design_Guideline_For_Extension.md#Slot)を使用するか決めたら、そのExtensionの対話モデルにビルトインスロットタイプを追加する必要があります。例えば、ピザの宅配Extensionを作成する場合、ユーザーの発話に、ピザの数量に関する情報の表現が含まれることが予想されます。従って、この場合は数量に関するビルトインスロットタイプを使用する必要があり、次の手順でExtensionに追加します。

<ol>
  <li><strong>{{ book.DevConsole.cek_builder_list_title_slottype }}</strong>パネル、または左側のサイドメニューの<strong>{{ book.DevConsole.cek_builder_list_title_slottype }}</strong>内にある<strong>{{ book.DevConsole.cek_builder_select_slottype_builtin }}</strong>の右に表示された<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックします。</li>
  <li>使用したいビルトインスロットタイプのカテゴリーをクリックします。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Built-in_Slot_Type_1.png" />
  <li>リストが展開されたら、必要なビルトインスロットタイプにチェックを入れ、ウィンドウ右上の<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Built-in_Slot_Type_2.png" />
</ol>

すると、**{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** 画面の **{{ book.DevConsole.cek_builder_list_title_slottype }}** パネルに、次のようにビルトインスロットタイプが追加されたことを確認できます。

![](/DevConsole/Assets/Images/DevConsole-Added_Built-in_Slot_Type.png)

### カスタムスロットタイプを追加する {#AddCustomSlotType}

次に、Extensionで使用する[カスタムスロットタイプ](/Design/Design_Guideline_For_Extension.md#Slot)を定義します。[ビルトインスロットタイプを追加する](#AddBuiltinSlotType)時と同様に、ピザの宅配Extensionを作成すると仮定します。この場合、ユーザーの発話の中で、ピザの種類に当たる部分をカスタムスロットタイプとして定義することができます。以下の表のような代表語と同義語を持つ、「PIZZA_TYPE」というカスタムスロットタイプを追加してみます。

| 代表語                     | 同義語                     |
| -------------------------- | -------------------------- |
| ペパロニ                   | ペパロニピザ               |
| バーベキュー               | バーベキューピザ、BBQピザ  |
| チーズ                     | チーズピザ                 |
| 野菜                       | 野菜ピザ、ベジピザ、ベジタリアンピザ |
| シュリンプゴールドクラスト | シュリンプゴールドクラストピザ、シュリンプゴルクラピザ、シュリンプゴルクラ |

次の順でカスタムスロットタイプを追加します。

<ol>
  <li><strong>{{ book.DevConsole.cek_builder_list_title_slottype }}</strong>パネル、または左側のサイドメニューの<strong>{{ book.DevConsole.cek_builder_list_title_slottype }}</strong>内にある<strong>カスタムスロットタイプ</strong>の右に表示された<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックします。</li>
  <li><strong>{{ book.DevConsole.cek_builder_new_slottype_title }}</strong>の入力フィールドに、追加するカスタムスロットタイプの名前を入力し、<strong>{{ book.DevConsole.cek_create }}</strong>ボタンをクリックします。カスタムスロットタイプが生成されると、そのカスタムスロットタイプの詳細を確認できる画面が表示されます。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Slot_Type_1.png" />
  <li><strong>{{ book.DevConsole.cek_builder_slottype_dictionary_title }}</strong>の入力フィールドに代表語を入力し、<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックして代表語を追加します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Slot_Type_2.png" />
  <li>追加した代表語に、同義語や類義語を追加します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Slot_Type_3.png" />
  <li>最後に、右上の<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
</ol>

右の<strong>ダッシュボード</strong>メニューで**{{ book.DevConsole.cek_interaction_model }}：{{ book.DevConsole.cek_builder_header_title_dashboard }}** に移動すると、カスタムスロットタイプが追加されたことを確認できます。

![](/DevConsole/Assets/Images/DevConsole-Added_Custom_Slot_Type.png)

定義するカスタムスロットタイプに大量の情報を入力する必要がある場合、TSV(タブ区切りの値、.tsv)形式のファイルをアップロードすることもできます。TSVファイルの各行の1番目の値が代表語となります。それに続くタブ区切りの値は、その代表語の同義語または類義語になります。次は、「PIZZA_TYPE」というカスタムスロットタイプの定義を、TSV形式で表現したものです。

```
ペパロニ             ペパロニピザ
バーベキュー          バーベキューピザ　　　   BBQピザ
チーズ　　　　　　　　 チーズピザ
野菜　　　　　　      野菜ピザ　　　　　　　　ベジピザ　　　　　　　　ベジタリアンピザ
シュリンプゴールドクラスト　　シュリンプゴールドクラストピザ　　シュリンプゴルクラピザ　　シュリンプゴルクラ
```

CLOVA Developer Centerには、以下のように **アップロード** ボタンと **ダウンロード** ボタンがあります。**アップロード** ボタンをクリックすると、あらかじめTSVファイルで定義したカスタムスロットタイプをアップロードできます。**ダウンロード** ボタンをクリックすると、現在作成中のカスタムスロットタイプをTSV形式でダウンロードできます。

![](/DevConsole/Assets/Images/DevConsole-Custom_Slot_Upload_and_Download_Button.png)

現在、1つのスロットタイプ毎に、代表語と同義語を合わせて20万件登録することが可能です。TSVファイルをアップロードする場合、登録できる件数は同様に20万件となります。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>すでにカスタムスロットタイプに辞書が登録されている状態でTSVファイルをアップロードすると、既存のデータが削除され、TSVファイルのデータに置き換えられます。既存データを削除しないようにするには、事前に既存データをダウンロードし、追加分と合わせたTSVファイルを作成してアップロードしてください。</p>
</div>

### ビルトインインテントを追加する {#AddBuiltinIntent}

CLOVAプラットフォームでは共通したユーザーリクエストのカテゴリを決め、それを共有して利用するために[ビルトインインテント](/Design/Design_Guideline_For_Extension.md#Intent)が提供されています。例えば、頻繁に発生すると予想されるユーザーの肯定・否定の返事や、キャンセルなどのリクエストを、インテントとしてあらかじめ定義したものです。
ビルトインインテントは次の手順でExtensionに追加します。

<ol>
  <li><strong>{{ book.DevConsole.cek_builder_list_title_intent }}</strong>パネル、または左側のサイドメニューの<strong>{{ book.DevConsole.cek_builder_list_title_intent }}</strong>内にある<strong>{{ book.DevConsole.cek_builder_select_intent_builtin }}</strong>の右に表示された<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックします。</li>
  <li>必要なビルトインインテントにチェックを入れ、右上の<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Built-in_Intent.png" />
</ol>

デフォルトで選択されているビルトインインテントは以下のとおりです。

![](/DevConsole/Assets/Images/DevConsole-Built-in_Intent_List.png)

すべてのExtensionは、[**Clova.GuideIntent**](/CEK/References/CEK_API.md#ClovaGuideIntent) に対応する必要があります。それ以外のビルトインインテントについては、必要に応じて選択し対応してください。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>今後、Extensionごとに必要なビルトインインテントのみ使用できるように変更される予定です。</p>
</div>

### カスタムインテントを追加する {#AddCustomIntent}
Extensionが使用する[ビルトインスロットタイプ](#AddBuiltinSlotType)と[カスタムスロットタイプ](#AddCustomSlotType)を追加したら、次はカスタムインテントを追加します。続けて、ピザを注文するユーザーのリクエストを仮定します。次の順で「OrderPizza」という名前のインテントを追加します。

<ol>
  <li><strong>{{ book.DevConsole.cek_builder_list_title_intent }}</strong>パネルか、左側のサイドメニューの<strong>{{ book.DevConsole.cek_builder_list_title_intent }}</strong>メニュー内の<strong>カスタムインテント</strong>の右に表示された<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックします。</li>
  <li><strong>{{ book.DevConsole.cek_builder_new_intent }}</strong>の入力フィールドに、追加するカスタムインテントの名前を入力し、<strong>{{ book.DevConsole.cek_create }}</strong>ボタンをクリックします。カスタムインテントが生成されると、そのカスタムインテントの詳細を確認する画面が表示されます。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Intent_1.png" />
  <li><strong>{{ book.DevConsole.cek_builder_intent_slot_title }}</strong>の入力フィールドに、追加するスロットの名前を入力し、右の<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックしてスロットを追加します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Intent_2.png" />
  <li>スロットを追加し、そのスロットのタイプを指定します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Intent_3.png" />
  <li>次に、<strong>{{ book.DevConsole.cek_builder_intent_expression_title }}</strong>にサンプル発話を入力し、右の<img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" />ボタンをクリックしてそのサンプル発話を追加します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Intent_4.png" />
  <li>追加したサンプル発話で、スロットとして処理される部分をドラッグしてスロットを指定します。</li>
  <img src="/DevConsole/Assets/Images/DevConsole-Add_Custom_Intent_5.png" />
  <li>ステップ5、6を繰り返して、インテントにサンプル発話を必要なだけ追加します。</li>
  <li>最後に、右上の<strong>{{ book.DevConsole.cek_save }}</strong>ボタンをクリックします。</li>
</ol>

<div class="note">
  <p><strong>メモ</strong></p>
  <p>スロットタイプとスロット名は、集合の名前、または複数の値を代入できるような抽象的な名前である必要があります。</p>
</div>

現在、登録できるサンプル発話の上限は、1つのインテントあたり2000件です。ただし、単純にサンプル発話の登録件数が多いほど認識率が上がるというものではなく、例えばスロットの値は同じで語尾だけ変化させたサンプル発話を多数登録した場合は、逆にパフォーマンスが低下することがあります。
サンプル発話を作成する際の注意点については、[サンプル発話](/Design/Design_Guideline_For_Extension.md#UtteranceExample)を参照してください。

カスタムスロットタイプと同じく、TSV(タブ区切りの値、.tsv)形式のファイルをアップロードして定義することもできます。TSVファイルは、インテントのスロットを定義する部分と、サンプル発話を列挙する部分の2つに分けられます。インテントのスロット定義がファイルの先頭にあり、`[INTENT SLOT]`ヘッダの次の行でスロットが列挙されます。タブで区切られた最初の列はインテントで使用されるスロットの名前で、2番目の列はスロットタイプです。

インテントのサンプル発話の列挙がそれに続きます。`[INTENT EXPRESSION]`ヘッダの次の行でサンプル発話が列挙されます。サンプル発話でスロットを区別するためには、該当する表現をスロット名のタグで囲う必要があります。以下は、インテントを定義したTSVファイルの例です。

```
[INTENT SLOT]
pizzaType	PIZZA_TYPE
pizzaAmount	CLOVA.NUMBER

[INTENT EXPRESSION]
<pizzaType>ペパロニ</pizzaType><pizzaAmount>2枚</pizzaAmount>注文して。
<pizzaType>BBQピザ</pizzaType><pizzaAmount>2枚</pizzaAmount>出前取ってくれる?
<pizzaType>コンビネーションピザ</pizzaType><pizzaAmount>2つ</pizzaAmount>頼んで。
<pizzaType>シュリンプゴルクラ</pizzaType><pizzaAmount>1個</pizzaAmount>お願い。
...
```

CLOVA Developer Centerは、以下のように**アップロード**ボタンと**ダウンロード**ボタンが利用可能です。**アップロード** ボタンをクリックすると、あらかじめTSVファイルで定義したカスタムインテントをアップロードできます。**ダウンロード** ボタンをクリックすると、現在作成しているカスタムインテントをTSV形式でダウンロードできます。

![](/DevConsole/Assets/Images/DevConsole-Utterance_Example_Upload_and_Download_Button.png)

<div class="note">
  <p><strong>メモ</strong></p>
  <p>すでにサンプル発話が登録されている状態でTSVファイルをアップロードすると、既存のデータが削除され、TSVファイルのデータに置き換えられます。既存データを削除しないようにするには、事前に既存データをダウンロードし、追加分と合わせたTSVファイルを作成してアップロードしてください。</p>
</div>

<div class="danger">
  <p><strong>注意</strong></p>
  <p>1つの対話モデルでは、インテントに関わらず、スロットタイプに同じ名前を宣言することをお勧めします。例えば、「OrderPizza」インテントで、ピザの種類(「PIZZA_TYPE」)に関するスロット名を「pizzaType」にしたとすると、他のインテントで同じスロットタイプを宣言する際、同じく「pizzaType」にする必要があります。ただし、「東京から大阪まで時間がどれぐらいかかるか教えて」のように、「東京」と「大阪」が同じスロットタイプであっても、目的によって区別される必要のある場合、スロット名を区別して作成します。</p>
</div>

これまで、1つのインテントを対話モデルに追加する方法を説明しました。この方法を繰り返し、Extensionに必要なインテントを追加していくことで対話モデルが完成されます。

![](/DevConsole/Assets/Images/DevConsole-Added_Interaction_Model.png)
