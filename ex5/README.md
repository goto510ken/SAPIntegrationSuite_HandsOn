# 演習5: ODataアダプターを用いたSAPシステムへの連携

## 目的
本演習ではiFlow からS/4HANAシステムを呼出して製品データを取得します。このS/4HANAの呼出しは、S/4HANAの持つさまざまなインターフェースを利用することが出来ますが、今回の演習ではOdata方式のWwebサービス(SAP Integration SuiteでAPIとして事前設定済み)を利用します。具体的には以下の内容を実施します。
1. Content Modifier を用いてPayload 内のProduct IDを取得してExchange Property として設定
2. S/4HANAを呼び出す(ODataサービスのケース)を呼び出す設定
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

2. ### メニューから`Message Transformers`の中から`Content Modifier`を選択して、Integration Flow 内の`Message Mapping`とEnd を結ぶ線上に配置してください。
  
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

## まとめ
