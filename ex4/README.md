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
>4. Message 内部でデータをマッピングして、異なる項目にデータをマッピング(例: 項目`ProductIdentifier`から項目`ProductID`へ)*
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
   
   <img src="images/4-1-2-1.png" alt="table" width="100%">

3. ### (もしもプロパティパネルが隠れている場合は)`CSV to XML Converter`を選択したままの状態で、画面右下の`Restore`ボタンを押します。

   <img src="images/4-1-3.png" alt="table" width="100%">

4. ### 画面下部に表示された`CSV to XML Converter`のプロパティが表示されます。こちらの`General` タブおよび`Processing` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`CSV To XML Converter`|

     <img src="images/4-1-4.png" alt="table" width="100%">   
   
    `Processing`タブ
    |パラメータ|入力項目|
    |--|--|
    |XML Schema:|`Select`ボタンを押して、開いたポップアップ画面左下の`Upload from File System`ボタンを押して、ファイル`Product_sender.xsd`をアップロードしてください。|
    |Path to Target Element in XSD:|`/Product`|
    |Record Marker in CSV:|`空白`|
    |Field Separator in CSV:|`Comma(,)`|
    |Exclude First Line Header:|`チェック`|
    |Configure CSV Headers to match:|`XSD Elements` *デフォルトのまま|

    <img src="images/4-1-4-1.png" alt="table" width="100%">

    >CSV to XML Converter のその他のパラメータの意味などは、SAP Help の[こちら](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/configure-csv-to-xml-converter)をご確認ください。
      
5. ### 画面右上にある`Save`ボタンを押して、作成してものを保存してください。

   <img src="images/4-1-5.png" alt="table" width="100%">

</details>

## ステップ2: Message Mapping 機能を利用して異なる項目にデータをマッピング
<details>
<summary>内容を開く</summary>   

1. ### メニューから編集メニューにある`Mapping` の中から`Message Mapping`を選択してIntegration Process内の `CSV to XML Converter` とEnd を結ぶ線上に配置してください。 

   <img src="images/4-2-1.png" alt="table" width="100%">
   
   以下、`Message Mapping`を選択して、Integration Prcess 内の `CSV to XML Converter` とEnd を結ぶ線上に配置した状態
   
   <img src="images/4-2-1-1.png" alt="table" width="100%">

2. ### もしもプロパティパネルが隠れている場合は)`Message Mapping`を選択したままの状態で、画面右下の`Restore`ボタンを押します。

   <img src="images/4-2-2.png" alt="table" width="100%">

3. ### 画面下部に表示された`Message Mapping`のプロパティが表示されます。こちらの`General` タブの値を以下のように設定してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|`Message Mapping`|

     <img src="images/4-2-3.png" alt="table" width="100%">   

4. ### Integration Process 内の`Messasge Mapping`を選択してメニューから`Create`を選択してください。

   <img src="images/4-2-4.png" alt="table" width="100%"> 

5. ### 開いたポップアップ画面`Create Message Mapping`でNameを`xsd_mapping_xx`と入力して`Create`ボタンを押してください。(*xxについては講師から指定された数字に数字に置き換えてください。)

   <img src="images/4-2-5.png" alt="table" width="100%"> 

6. ### 結果として表示された`xsd_mapping_xx`(*xxについては講師から指定された数字に数字に置き換えてください。)左右に表示されたStructure のうち`左側の`Structureの上にある`Add source message`ボタンを押してください。

   <img src="images/4-2-6.png" alt="table" width="100%">
   
7. ### 開いたポップアップ画面`Select Source Message`の左下にある`Upload from File System`ボタンを押して、`Product_sender.xsd`をアップロードしてください。結果として受信側のデータ構造がXML形式(CSV形式をステップ1でXML形式に変更したデータ構造に対応)で取り込まれます。これによってXML形式に変換されたデータを取り込みます。

   <img src="images/4-2-7.png" alt="table" width="100%">

   以下、受信側のデータ構造がXML形式で取り込まれた状態。

   <img src="images/4-2-7-1.png" alt="table" width="100%">

8. 左右に表示されたStructure のうち`右側の`Structureの上にある`Add source message`ボタンを押してください。

   <img src="images/4-2-8.png" alt="table" width="100%">
   
9. ### 開いたポップアップ画面`Select Source Message`の左下にある`Upload from File System`ボタンを押して、`ProductSet_receiver.xsd`をアップロードしてください。結果として送信側のデータ構造がXML形式で取り込まれます。これによってXML形式でデータを出力することができます。

   <img src="images/4-2-9.png" alt="table" width="100%">

   以下、受信側のデータ構造がXML形式で取り込まれた状態。

   <img src="images/4-2-9-1.png" alt="table" width="100%">

10. ### 左側のStructure の`Product`を選択して、`矢印のついたアイコン`から線をひっぱり出して、右側のStructure の`ProductSet`の下にある`Product`まで引っ張ってください。

   <img src="images/4-2-10.png" alt="table" width="100%"> 

11. ### 右上の２段目にある右から２つ目のアイコン(`Ab`と表記されているアイコン)を押してくだいさい。結果として、左右のStructure にある同じ名前のそれぞれの項目が自動的にマッピングされます。

   <img src="images/4-2-11.png" alt="table" width="100%"> 

12. 左右のStructure で項目名が異なるが、同じ項目は１つ１つ手動でマッピングできます。ここでは左側のStructure の`ProductIdentifier`と右側のStructureの`ProductID`をマッピングします。まず左側のStructure の`ProductIdentifier`を選択して、`矢印のついたアイコン`から線をひっぱり出して、右側のStructure の`ProductID`まで引っ張ってください。

   <img src="images/4-2-12.png" alt="table" width="100%"> 
    

</details>





