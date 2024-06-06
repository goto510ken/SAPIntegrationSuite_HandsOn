# 演習8: SFTPアダプターの利用によるファイル出力への変更

## 目的
iFlow の構築の総仕上げとして、出力データをCSVファイルとしてSFTPサーバーに出力します。こちらではIntegration Suite の持つSFTP Reciever Adapter の機能を利用します。具体的には以下の内容を実施します。
1. SFTP Reciever Adapter の実装
2. トレースの準備およびディプロイ
3. プロセスの実施とプロセス結果の確認

<img src="images/8-Intro.png" alt="table" width="100%">

>本演習で作成したiFlow は次のようなステップで実行されます。
>1. ディプロイ後にSFTPサーバーにCSVファイルをアップロード
>2. SFTP Sender Adapter がSFTP を一定間隔でポーリングし、ファイルの存在があればプロセスを開始
>3. ファイルからのデータをCSV形式からXML形式に変換
>4. Message 内部でデータをマッピングして、異なる項目にデータをマッピング(例: 項目ProductIdentifierから項目ProductIDへ)
>5. Payload 内のProductIDを取得してExchange Property として設定
>6. Exchange Property として設定したProductIDを利用して、この製品に関するデータをS/4HANAシステムからODataを利用して取得
>7. S/4HANAシステムから取得した製品データをMessage内のPayload に格納しプロセスを終了
>8. S/4HANAから取得したデータをXML形式からCSV形式に変換
>9. `SFTPサーバーに出力されたCSVファイルの確認`*
>   
>*本演習で拡張した結果として追加もしくは変更されたステップ


