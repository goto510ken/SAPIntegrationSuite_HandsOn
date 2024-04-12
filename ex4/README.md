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
