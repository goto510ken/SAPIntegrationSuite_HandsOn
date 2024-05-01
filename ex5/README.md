# 演習5: ODataアダプターを用いたSAPシステムへの連携

## 目的
本演習ではiFlow からS/4HANAシステムを呼出して製品データを取得します。このS/4HANAの呼出しは、S/4HANAの持つさまざまなインターフェースを利用することが出来ますが、今回の演習ではOdata方式のWwebサービス(SAP Integration SuiteでAPIとして事前設定済み)を利用します。具体的には以下の内容を実施します。
1. Content Modifier を用いてPayload 内のProduct IDを取得してExchange Property として設定
2. S/4HANAを呼び出す(ODataサービスのケース)を呼び出す設定
3. iFlow をトレース(デバック)付き実行して、プロセス終了時のMessage内のPayload にS/4HANAから取得した製品データが格納されていることを確認

<img src="images/4-Intro.png" alt="table" width="100%">

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

## まとめ
