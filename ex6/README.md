# 演習6: データ出力のデータフォーマットの変換

## 目的
本演習ではiFlow からS/4HANAシステムから取得した製品データのデータ形式を変換します。こちらではIntegration Suite に組み込まれている`XML to CSV Converter`を利用します。具体的には以下の内容を実施します。
1. XML to CSV Converter を用いてS/4HANAから取得した製品データ形式をXML形式からCSV形式に変換
2. iFlow をトレース(デバック)付き実行して、プロセス終了時のMessage内のPayload にS/4HANAから取得した製品データがCSV形式に変換されていることを確認
<img src="images/6-Intro.png" alt="table" width="100%">

>本演習で作成したiFlow は次のようなステップで実行されます。
>1. ディプロイ時にタイマーでプロセス開始
>2. プロセス内部でダミーのCSV形式データを設定
>3. ダミーデータをCSV形式からXML形式に変換*
>4. Message 内部でデータをマッピングして、異なる項目にデータをマッピング(例: 項目ProductIdentifierから項目ProductIDへ)
>5. Payload 内のProductIDを取得してExchange Property として設定
>6. Exchange Property として設定したProductIDを利用して、この製品に関するデータをS/4HANAシステムからODataを利用して取得
>7. S/4HANAシステムから取得した製品データをMessage内のPayload に格納しプロセスを終了`
>8. `S/4HANAから取得したデータをXML形式からCSV形式に変換` *
>   
>*本演習で拡張した結果として追加もしくは変更されたステップ

## 手順

## まとめ
本演習では、S/4HANAから取得したデータの形式をXML形式からCSV形式に変換する方法をご紹介しました。
