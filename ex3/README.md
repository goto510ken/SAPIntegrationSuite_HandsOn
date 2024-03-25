# 演習3:  最単純なIntegration Flow (iFlow) の作成と動作トレース

## 目的
本ワークショップではSAP Integration Suite での単純なIntegration Flow (以下、iFlow) を作成します。本演習では以下の内容を実施します。
1. SAP Integration Suit パッケージおよびiFlow の作成
2. 最単純なiFlow のステップ作成とディプロイ
3. iFlow のトレース (デバック)してプロセス終了時のメッセージ内部のコンテンツの確認

<img src="images/3-Intro.png" alt="table" width="100%">

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

 3. 開いたDesign ページの右上にある`Create`ボタンを押してください。

    <img src="images/3-1-3.png" alt="table" width="100%">


 4. Package 作成ページのパラメータに以下のように入力して、`Save`ボタンを押してください。

    |パラメータ|入力項目|
    |--|--|
    |Name:|`Integration Suite hands on package for xx` *`xx`については講師から`指定された数字に数字に置き換え`てください。|
    |Technical Name:|Nameを入力すると自動的に入力されます。`そのまま`にしてください。|
    |Short Description|`SAP Integration Suite hands on workshop package for xx` *`xx`については講師から`指定された数字に数字に置き換え`てください。|
   
    <img src="images/3-1-4.png" alt="table" width="100%">
 
 5. 作成したPackage の画面が開いたら、`Artifacts`タブを選択してください。さらにArtifacts リストの上にある`Add` → `Integration Flow` を選択してください。 
    
    <img src="images/3-1-5.png" alt="table" width="100%">
    
 6. 開いたポップアップ画面のパラメータに以下のように入力した後に、`Add and Open in Editor`ボタンを押してください。

    |パラメータ|入力項目|
    |--|--|
    |ラジオボタン`Create`|チェック *`デフォルト`のまま|
    |Name:|`Integration Flow for xx` *`xx`については講師から`指定された数字に数字に置き換え`てください。|
    |ID:|Nameを入力すると自動的に入力されます。`そのまま`にしてください。| 
    |Runtime Profile:|Cloud Integration *`デフォルト`のまま|
    
    <img src="images/3-1-6.png" alt="table" width="60%">
    
       最終的に、Integration Flow が作成され、Editorが開いた状態になります。
    
    <img src="images/3-1-6-1.png" alt="table" width="100%">
    
</details>

ステップ2: 最単純なiFlow の作成とディプロイ 
<details>
<summary>内容を開く</summary>

 1. Integration Flow のEditor画面の右上にある`Edit`ボタンを押して、編集モードに変更してください。。
    
    <img src="images/3-2-1.png" alt="table" width="100%">
    

 2. メニューから編集メニューにある`Event`の中から`Timer`イベント*を選択して、Integration Prcess 内の Sart とEnd を結ぶ線上に配置してください。　* `Timerイベントは一番下にあるので、見つからなら場合は、Event自体をスクロールすると表示されます。`
    
    <img src="images/3-2-2.png" alt="table" width="40%">
    
     以下、Timer イベントをIntegration Prcess 内の Sart とEnd を結ぶ線上に配置した状態。
    <img src="images/3-2-2-1.png" alt="table" width="100%">

 3. Timer イベントを選択したままの状態で、画面右下の`Restore`ボタンを押します。
    
    <img src="images/3-2-3.png" alt="table" width="100%">

 4. 画面下部に表示されたTimer イベントのプロパティが表示されます。こちらの`General`タブおよび`Scheduler`タブの値を以下のように変更してください。

    `General`タブ
    |パラメータ|入力項目|
    |--|--|
    |Name:|Start Timer|
    
    <img src="images/3-2-4.png" alt="table" width="100%">

    `Scheduler`タブ
    |パラメータ|入力項目|
    |--|--|
    |ラジオボタン `Run Once`|チェック *`デフォルト`のまま|
    
    <img src="images/3-2-4-1.png" alt="table" width="100%">

    >Time イベントのその他のパラメータの意味などは、SAP Help の[こちら](https://help.sap.com/docs/cloud-integration/sap-cloud-integration/define-timer-start-event)をご確認ください。

 
 6.
    
    <img src="images/3-2-5.png" alt="table" width="100%">
    
 7.
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

</details>

## まとめ
本演習では、最単純なiFlow を作成することで、フローを作成する際に必要な手順を理解することが出来ます。
