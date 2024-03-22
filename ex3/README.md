# 演習3:  最単純なIntegration Flow (iFlow) の作成と動作トレース

## 目的
本ワークショップではSAP Integration Suite での単純なIntegration Flow (以下、iFlow) を作成します。本演習では以下の内容を実施します。
1. SAP Integration Suit パッケージおよびiFlow の作成
2. 最単純なiFlow のステップ作成とディプロイ
3. iFlow のトレース (デバック)してプロセス終了時のメッセージ内部のコンテンツの確認

<img src="images/3-intro.png" alt="table" width="100%">

>本演習で作成したiFlow は次のようなステップで実行されます。
>1.ディプロイ時に`タイマーでプロセス開始`
>2.プロセス内部で`ダミーのCSV形式データ`を設定
>3.ダミーデータをメッセージ内に格納しプロセスを終了

## 手順

ステップ1: SAP Integration Suit パッケージおよびiFlow の作成
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
    <img src="images/3-1-6.png" alt="table" width="100%">
    
</details>

ステップ2: 最単純なiFlow の作成とディプロイ 
<details>
<summary>内容を開く</summary>

 1. Integration Suiteにアクセスします。
    
    <img src="images/3-2-1.png" alt="table" width="100%">
    

 2. メニューから`Monitor` → `Integrations and APIs`を選択します。
    
    <img src="images/3-2-2.png" alt="table" width="40%">

 3. 
    
    <img src="images/3-2-3.png" alt="table" width="100%">

 4. 
    
    <img src="images/3-2-4.png" alt="table" width="100%">
 
 5.
    
    <img src="images/3-2-5.png" alt="table" width="100%">
    
 6.
    <img src="images/3-2-6.png" alt="table" width="100%">
    
</details>

ステップ3: iFlow のトレース (デバック) してプロセス終了時のメッセージ内部のコンテンツの確認
<details>
<summary>内容を開く</summary>

 1. Integration Suiteにアクセスします。
    
    <img src="images/3-4-1.png" alt="table" width="100%">
    

 2. メニューから`Monitor` → `Integrations and APIs`を選択します。
    
    <img src="images/3-4-2.png" alt="table" width="40%">

 3. 
    
    <img src="images/3-4-3.png" alt="table" width="100%">

 4. 
    
    <img src="images/3-4-4.png" alt="table" width="100%">
 
 5.
    
    <img src="images/3-4-5.png" alt="table" width="100%">
    
 6.
    <img src="images/3-4-6.png" alt="table" width="100%">
