# 演習5: ODataアダプターを用いたSAPシステムへの連携

## 目的
本演習ではiFlow からS/4HANAシステムを呼出して製品データを取得します。このS/4HANAの呼出しは、さまざまな種類のインターフェースを利用することが出来ますが、今回の演習ではOData方式のWwebサービス(SAP Integration SuiteでAPIとして事前設定済み)を利用します。具体的には以下の内容を実施します。
1. Content Modifier を用いてPayload 内のProduct IDを取得してExchange Property として設定
2. S/4HANA(ODataサービスを利用)を呼び出す設定
3. iFlow をトレース(デバック)付き実行して、プロセス終了時のMessage内のPayload にS/4HANAから取得した製品データが格納されていることを確認

<img src="images/5-Intro.png" alt="table" width="100%">

>本演習で作成したiFlow は次のようなステップで実行されます。
>1. ディプロイ時にタイマーでプロセス開始
>2. プロセス内部でダミーのCSV形式データを設定
>3. ダミーデータをCSV形式からXML形式に変換*
>4. Message 内部でデータをマッピングして、異なる項目にデータをマッピング(例: 項目ProductIdentifierから項目ProductIDへ)
>5. `Payload 内のProductIDを取得してExchange Property として設定`*
>6. `Exchange Property として設定したProductIDを利用して、この製品に関するデータをS/4HANAシステムからODataを利用して取得`*
>7. `S/4HANAシステムから取得した製品データをMessage内のPayload に格納しプロセスを終了`*
>   
>*本演習で拡張した結果として追加もしくは変更されたステップ

## 手順

## ステップ1: Content Modifier を用いてPayload 内のProduct IDを取得してExchange Property として設定
<details>
<summary>内容を開く</summary>

1. ### Integration Flow のDesigner 画面のタブに戻ります。そしてIntegration Flow のEditor画面の右上にある`Edit`ボタンを押して、編集モードに変更してください。
  
   <img src="images/5-1-1.png" alt="table" width="100%">

2. ### メニューにある`Message Transformers`の中から`Content Modifier`を選択して、Integration Flow 内の`Message Mapping`とEnd を結ぶ線上に配置してください。
  
   <img src="images/5-1-2.png" alt="table" width="100%">

   以下、`Content Modifier`を選択して, Integration Process 内の`Message Mapping` とEnd を結ぶ線上に配置した状態

   <img src="images/5-1-2-1.png" alt="table" width="100%">
   
3. ### (もしもプロパティパネルが隠れている場合は)`Content Modifier`を選択したままの状態で、画面右下の`Restore`ボタンを押します。

   <img src="images/5-1-3.png" alt="table" width="100%">

4. ### 画面下部に表示された`Content Modifier`のプロパティが表示されます。こちらの`General` タブおよび`Exchange Property` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`add Exchange Property "ProductID"`|

     <img src="images/5-1-4.png" alt="table" width="100%">   
   
    `Exchange Property`タブ
    |パラメータ|入力項目|
    |--|--|
    |Action:|`Create`を選択|
    |Name:|`ProductID`|
    |Source Type:|`XPath`を選択|
    |Source Value:|`//ProductID`|
    |Data Type:|`java.lang.String`　*大文字小文字は別の文字として判断されますので、必ずご確認ください。|
    
    <img src="images/5-1-4-1.png" alt="table" width="100%">

    >Content Modifier のその他のパラメータの意味などは、SAP Help の[こちら](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/define-content-modifier)をご確認ください。

5. ### 画面右上にある`Save`ボタンを押して作成してものを保存してください。
  
   <img src="images/5-1-5.png" alt="table" width="100%">

</details>

## ステップ2: S/4HANA(ODataサービスを利用)を呼び出す設定
<details>
<summary>内容を開く</summary>

1. ### メニューにある`Call`の中にある`Extranal Call` → `Request Reply`を選択してIntegration Process内の`add Exchange Property "ProductID"`とEnd を結ぶ線上に配置してください。
  
   <img src="images/5-2-1.png" alt="table" width="100%">

   以下、`Request Reply`を選択して、Integration Process 内の`add Exchange Property "ProductID"`とEnd を結ぶ線上に配置した状態

   <img src="images/5-2-1-1.png" alt="table" width="100%">

2. ### (もしもプロパティパネルが隠れている場合は)`Request Reply`を選択したままの状態で、画面右下の`Restore`ボタンを押します。
   
   <img src="images/5-2-2.png" alt="table" width="100%">

3. ### 画面下部に表示された`Request Reply`のプロパティが表示されます。こちらの`General` タブおよび`Processing` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`call S/4HANA System with ODATA API`|

     <img src="images/5-2-3.png" alt="table" width="100%">   

4. ### メニューにある`Participant`の中にある`Receiver`を選択して`call S/4HANA System with ODATA API`の真下あたりに配置してください。
  
   <img src="images/5-2-4.png" alt="table" width="100%">

5. ### (もしもプロパティパネルが隠れている場合は)`Receiver`を選択したままの状態で、画面右下の`Restore`ボタンを押します。
   
   <img src="images/5-2-5.png" alt="table" width="100%">

6. ### 画面下部に表示された`Receiver`のプロパティが表示されます。こちらの`General` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`S4HANA` * 空白は不可|

     <img src="images/5-2-6.png" alt="table" width="100%">

7. ### Integration Process 内の`call S/4HANA System with ODATA API`を選択してメニューから`Connector`を選択して`S4HANA`に接続してください。
  
   <img src="images/5-2-7.png" alt="table" width="100%">

   接続された状態は以下のようになり、ポップアップ画面が開きます。

   <img src="images/5-2-7-1.png" alt="table" width="100%">

   ポップアップ画面では`Adapter Type`を設定する画面になります。ここでは`OData` → `OData V2`を選択します。

   <img src="images/5-2-7-2.png" alt="table" width="100%">

   最終的には、以下のよう`call S/4HANA with ODATA API`と`S4HANA`が接続されます。
   
   <img src="images/5-2-7-3.png" alt="table" width="100%">

</details>

## まとめ
