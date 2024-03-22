# 演習3: SAP Integration Suiteでの SFTPサーバーの設定

## 目的
本ワークショップではSAP Integration Suite での単純なIntegration Flow (iFlow) を作成します。本演習では以下の内容を実施します。
1. SAP Integration Suit パッケージおよびiFlow の作成
2. 単純なIntegration Flow (iFlow) の作成とディプロイ
3. SFTPサーバーへアクセスして出力された結果の確認
4. iFlow のトレース方法 

<img src="images/3-intro.png" alt="table" width="100%">

>本演習で作成したIntegration Flow (iFlow) は次のようなステップで実行されます。
>1.ディプロイ時に`タイマーでプロセス開始`
>2.プロセス内部で`ダミーのCSV形式データ`を設定
>3.ダミーデータを`SFTPサーバーにCSVファイルとして出力`してプロセス終了

## 手順

ステップ1: 
<details>
<summary>内容を開く</summary>

 1. Integration Suiteにアクセスします。
    
    <img src="images/3-1-1.png" alt="table" width="100%">
    
    >Integration Suite へは、URL はhttps://`ご利用のIntegration Suite のアドレス`/shell/home でアクセス出来ます。
    

 2. メニューから`Design` → `Integrations and APIs`を選択します。
    
    <img src="images/3-1-2.png" alt="table" width="40%">

 3. 

    <img src="images/3-1-3.png" alt="table" width="100%">


 5. 

    <img src="images/3-1-4.png" alt="table" width="100%">
 
 7.
    
    <img src="images/3-1-5.png" alt="table" width="100%">
    
 8.
    <img src="images/2-1-6.png" alt="table" width="100%">
    
</details>

ステップ2: 
<details>
<summary>内容を開く</summary>

 1. Integration Suiteにアクセスします。
    
    <img src="images/3-1-1.png" alt="table" width="100%">
    
    >Integration Suite へは、URL はhttps://`ご利用のIntegration Suite のアドレス`/shell/home でアクセス出来ます。
    

 2. メニューから`Monitor` → `Integrations and APIs`を選択します。
    
    <img src="images/3-1-2.png" alt="table" width="40%">

 3. 
    
    <img src="images/3-1-3.png" alt="table" width="100%">


 4. 
    
    <img src="images/3-1-4.png" alt="table" width="100%">
 
 5.
    
    <img src="images/3-1-5.png" alt="table" width="100%">
    
 6.
    <img src="images/2-1-6.png" alt="table" width="100%">
    
</details>



