# SAP Integration Suite ハンズオンワークショップ - Integration 概要理解編
## 目的
SAP Integration Suite を初めて使用するITプロフェッショナルに以下の内容を理解いただくこと。
1. SAP Business Technology Platform (BTP) Trial Edition および含まれる`SAP Integration Suite のプロビジョニング`
2. SAP Integration Suite の`各種ツールの目的および利用方法`
3. SAP Integration Suite での`プロセスフローの作成(iFlow)の作成方法`
4. `SFTPアダプター`によるファイル連携および`CSV <-> XML形式への変換`
5. `メッセージマッピング`の方法
6. `SAP システムへのアクセス`方法(ODataアダプターの利用)
7. iFlow の`トレース`方法
8. `Integration Flow Design Guideline` の確認方法
   
## 前提
- 利用環境は`SAP Business Technologyy Platform (BTP) Trial edition` のIntegration Suiteの利用を前提としています。
- SFTP サーバーは弊社で準備したものを利用します。こちらの`アクセス方法などは別途`よりご連絡させて頂きます。
- 本ハンズオンで作成されるIntegration Flowは、`SAP Integration Suite の機能を理解することを目的`にしています。従って実際の業務プロセスでの利用を想定していません。またハンズオンの進め方も`最単純なIntegration Flow を作成し、少しづつ拡張するアプローチ`を採用しています。
  
## 対象者
- `ITプロフェッショナル`を想定 (これまでSAPシステム連携を行ったことがある、もしくは類似のEAIもしくはETLツールの利用経験があれば尚可)
  
## コンテンツ
### 1. プレゼンテーション
### 2. ハンズオン

|演習|
|-------------------|
| [演習1: SAP Business Technology Platform (BTP) Trial Edition でのSAP Integration Suite プロビジョニング](ex1/README.md)
| [演習2: SAP Integration SuiteでのSFTPサーバーの設定](ex2/README.md)
| [演習3: 最初のIntegration Flow (iFlow) の作成と動作トレース](ex3/README.md)
| [演習4: SFTPアダプターの利用によるファイル連携](ex4/README.md)
| [演習5: Message Mapping の利用](ex5/README.md)
| [演習6: ODataアダプターを用いたSAPシステムへの連携](ex6/README.md)
| [演習7: データ出力のデータフォーマットの変換](ex7/README.md)
| [演習8: SFTPアダプターを用いたファイルポーリングの方法](ex8/README.md)
| [演習9: 次のステップに向けて ~ Integration Flow Design Guidelineの確認](ex9/README.md)
