# 演習4: Message Mapping の利用

## 目的
本演習ではiFlow 内のMessage のBody 部分に格納されているPayload を加工します。具体的には以下の内容を実施します。
1. Converter 機能を利用してCSV形式のデータをXML形式のデータに変換
2. Message Mapping 機能を利用して異なる項目にデータをマッピング
3. iFlow を実行して、トレース(デバック)してプロセス終了時のMessage内のPayload がXML形式で格納されていることを確認

<img src="images/4-Intro.png" alt="table" width="100%">

>本演習で作成したiFlow は次のようなステップで実行されます。
>1. ディプロイ時に`タイマーでプロセス開始`
>2. プロセス内部で`ダミーのCSV形式データ`を設定
>3. ダミーデータをCSV形式からXML形式に変換*
>4. Message 内部でデータをマッピングして、異なる項目にデータをマッピング(項目`ProductIdentifier`から項目`ProductID`へ)*
>5. ダミーデータをMessage内のPayload にデータを変換して`XML形式で格納`しプロセスを終了*
>   
>*本演習で拡張した結果として追加もしくは変更されたステップ

## 手順

## ステップ1: Converter 機能を利用してCSV形式のデータをXML形式のデータに変換
<details>
<summary>内容を開く</summary>

1. ### Integration Flow のDesigner 画面のタブに戻ります。そしてIntegration Flow のEditor画面の右上にある`Edit`ボタンを押して、編集モードに変更してください。。

   <img src="images/4-1-1.png" alt="table" width="100%">

2. ### メニューから編集メニューにある`Message Transformers`の中から`Converter`→`CSV to XML Converter`を選択して、Integration Prcess 内の `Set Dummy Data` とEnd を結ぶ線上に配置してください。

   <img src="images/4-1-2.png" alt="table" width="100%">

   以下、`CSV to XML Converter`を選択して、Integration Prcess 内の `Set Dummy Data` とEnd を結ぶ線上に配置した状態
   
   <img src="images/4-1-3.png" alt="table" width="100%">

3. ### (もしもプロパティパネルが隠れている場合は)`CSV to XML Converter`を選択したままの状態で、画面右下の`Restore`ボタンを押します。

   <img src="images/4-1-4.png" alt="table" width="100%">

4. ### 画面かぶに表示された`CSV to XML Converter`のプロパティが表示されます。こちらの`General` タブおよび`Processing` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`CSV To XML Converter`|

     <img src="images/4-1-5.png" alt="table" width="100%">   
   
    `Processing`タブ
    |パラメータ|入力項目|
    |--|--|
    |XML Schema:|`Select`ボタンを押して、開いたポップアップ画面左下の`Upload from File System`ボタンを押して、ファイル`Product_sender.xsd`をアップロードしてください。|
    |Path to Target Element in XSD:|`/Product`|
    |Record Marker in CSV:|`空白`|
    |Field Separator in CSV:|`Comma(,)`|
    |Exclude First Line Header:|`チェック`|
    |Configure CSV Headers to match:|`XSD Elements` *デフォルトのまま|

    <img src="images/4-1-6.png" alt="table" width="100%">

    >CSV to XML Converter のその他のパラメータの意味などは、SAP Help の[こちら](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/configure-csv-to-xml-converter)をご確認ください。
      
6.  
7. 
8. 
   




</details>

