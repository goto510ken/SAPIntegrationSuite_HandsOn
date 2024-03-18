# 演習2.SFTPサーバーの設定

## 目的
本ワークショップではクラウド環境でのファイル連携の方法としてSFTP サーバーを利用します。本演習では以下の内容を実施します。
- クライアント側でのSFTPサーバーへのアクセスの確認
- SFTPサーバーをSAP Integration Suite と連携できるようにするための設定

<img src="images/9-intro.png" alt="table" width="100%">

>Integration Flow Design Guidelne: SOPA→iDoc 連携のプロセスを確実に一度実施するフロー(Sender がリトライに未対応の場合)


## 手順

ステップ1: クライアントPCからのSFTPサーバーへのアクセスの確認
<details>
<summary>内容を開く</summary>

 1. 
    
    <img src="images/2-1-1.png" alt="table" width="100%">
    
 2. 
    
    <img src="images/2-1-2.png" alt="table" width="40%">

 3. 
    
    <img src="images/2-1-3.png" alt="table" width="100%">

 4. 
    
    <img src="images/2-1-4.png" alt="table" width="100%">

</details>

ステップ2: Itengration SuiteでのSFTPサーバーの設定
<details>
<summary>内容を開く</summary>

 1. Integration Suiteにアクセスします。
    
    <img src="images/2-2-1.png" alt="table" width="100%">
    
    >Integration Suite へは、URL はhttps://`ご利用のIntegration Suite のアドレス`/shell/home でアクセス出来ます。
    

 2. 
    
    <img src="images/2-1-2.png" alt="table" width="40%">

 3. 
    
    <img src="images/2-1-3.png" alt="table" width="100%">

 4. 
    
    <img src="images/2-1-4.png" alt="table" width="100%">

</details>

## まとめ
上記の設定を行うことで、SAP Integration Suite とSFTPサーバーが連携できるようになります。以降の演習ではこちらの設定を用いてSFTPサーバーとSAP Integration Suite の間でファイル連携を行います。
