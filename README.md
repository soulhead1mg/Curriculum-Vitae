# オープン職務経歴書

職務経歴書というよりはスキルシート（2019/02/20現在）

## 基本情報

|key|value|
|---|-----|
|Name|---|
|Birth|1981/03/03|
|Family|既婚・子あり|
|Location|京都府|
|Blog|---|
|Twitter|[@soulhead](https://twitter.com/soulhead)|
|Qiita|[@soulhead](https://qiita.com/soulhead)|
|SlideShare|---|
|Speakerdeck|---|

- 製造業の社内SEをやっています

## スキル

### OS

- FreeBSD
  - 4.4～8.2ぐらいの世代をトータル200台ぐらい運用していました
  - 負荷試験や高負荷サービスでTIME_WAITの残存時間を短くするカーネルパラメーターをいじったり、カーネルソースを魔改造したことも（2度とやれる気はしない）
  - サーバからのインターネット接続が許可されていない環境のため、セットアップはpackageかソースをダウンロードして、自前で依存関係の解決を行っていました（portsはあまり使ったことがない）
  - 特技：コンパイル
- Linux
  - CentOS4あたり
  - 最新版を触ると、ifconfigがなくて戸惑う
  - RedHat,Ubuntu,Debian,OpenSuSEなどに遭遇することも稀にある
  - 作法の違いを使い分けられないので、毎回Google先生頼み
  - フォルダーごとの使用量を調べるときのスマートなオプションが覚えられず、こんなコマンドを叩いている ``du -hs `ls` ``
- WindowsServer
  - 現在、メインで面倒を見ているサーバ
  - とくに何もすることがない？
- Solaris
  - 8～10あたり
  - Netscape Directory Serverで使っていた
  - 10のレガシーコンテナーに8の環境を延命させた（実作業はやってない）

### サーバサイド

- HTTP
  - Apache
    - 1.3～2.1のあたりを主に運用
    - 1.3のEOLにより、2.1への載せ替えを100台ぐらい実施
    - 独自の認証モジュールが実装されており、そのモジュールの改造を行ったこともある
  - Nginx
    - Apacheでは、バーチャルホストで1つのサーバに複数のWEB(PHP)システムを稼働させており、Nginxでも同じ構成を作ろうとしたが、PHP実行パスの宣言あたりで苦戦して諦めた（Nginxがではじめた初期の頃の話）
    - 1つのWEBシステム程度では、稼働させられる（現在、ほそぼそと運用中）
  - IIS
    - WindowsでPHPという指定があった時に環境構築を行った
  - Squid
    - 古いバージョンで稼働していたため、遅い、最新のHTTPSサイトが見えない等のクレームがあり、バージョンアップの支援を行った
- RDB
  - PostgreSQL
    - 7.1～8.4のあたりを主に運用
    - 7.1から8.2あたりへのマイグレーションがいい思い出。一足飛びに上げられなかったので、段階的に上げていった
    - slow queryの抽出、explain、SQLの修正とパフォーマンス改善に取り組んだ
  - MySQL
    - Zabbixのアプライアンスなどに含まれており、仕方なく使用した
  - SQLServer
    - パッケージソフトのDBがこれだったため運用中
  - Oracle
    - 8～9のあたり
    - ORA-XXXXというエラーに怯えてた
    - 表領域の拡張とか本当にこのやり方で合ってるのか不安がいっぱいだった
- LDAP
  - OpenLDAP
    - 1～2.2のあたりを主に運用
    - ヘビーに使う環境（ユーザエントリ8万件、全エントリ100万件以上）だったため、かなり鍛えられたと思う
    - サーバの移行、レプリカの作成
    - LDAPのベンチマーク
  - Netscape Directory Server
    - OpenLDAPより検索性能が高いということで愛用されていた
    - 名前が何度も変更になった、いまは何という名前なんだっけ？
    - レプリカの作成が異様に早くて楽でした
  - ActiveDirectory
    - ID管理という面で利用
    - コンピューターの管理、GPO方面は雰囲気しかわかりません
- MAIL
  - postfix
    - 20,000人規模のメール配送サーバの運用
    - 社外送信向けのメールをフックして、セキュリティ対策を施す仕組みを作る、運用する
    - メールログの読み方、SMTPプロトコル、メールの仕様に詳しくなった
  - dovecot
    - セキュリティ対策を施す仕組みを開発する時に、テスト用の配送環境が必要となり、その時に構築
- DNS
  - BIND
    - レコード登録の日常作業
    - サーバ移設に伴うバージョンアップ、DNSSECが標準となり移行、環境構築に四苦八苦
    - SPFレコードについて新しく学ぶ
  - unbound
    - FreeBSDの標準が変更されたので、キャッシュサーバ程度の用途で運用
- DHCP
  - ISC-DHCP
    - サーバ移設に伴うバージョンアップで遭遇
    - 情報資産管理の仕組みと連動させて、固定IPを払い出す設定を作り込むPHPプログラムを作成
    - PostgreSQL、PHPのネットワーク関数の便利さに感動する
- 仮想化、コンテナー
  - VMWare
    - ESXに名前が変わったぐらいでそこそこの規模で導入された
    - 主にそこにのる仮想サーバの運用を担当
    - ツールを使わず`dump`、`dd`のコマンドを駆使してP2Vを20台ぐらい実施
  - Docker
    - 自主勉で触った程度
    - データの永続化をどこで行うのかが活用、設計のポイントだなと思った
- 監視
  - Nagios
    - 400台ぐらいのサーバを監視するサービスのために構築
    - エージェントレスで監視結果を一覧で見やすいという点で採用
    - 実際の運用作業はパートナーさんが行うので、設定用の専用WEBツールを自作した
  - Zabbix
    - いまの現場では、監視といえばZabbixという感じ
    - Nagios検討時から進化しているなと、とくにAutoDIscoveryの機能

### 言語

- プログラミング言語
  - PHP
    - フレームワークなしにWEBシステムをガリガリ作ってました
  - PHP(CakePHP)
    - フレームワークブームの時に採用
    - 周囲からは謎の実装を持ち込まれると、メンテナンスが属人化するのでやめてくれと言われる
    - フレームワークのメリットを布教できなかった
  - C
    - 学生時代はロボット制御のプログラムをC言語で書いていました
    - 仕事では、Apacheのモジュール開発で使用
  - JAVA
    - JAVAで書かれたWEBアプリの問い合わせ対応で仕様を確認するためにclassファイルからデコンパイルしてソースを読むことはやりました
    - スクラッチからの開発、コンパイル、ビルドの経験はない
  - Perl
    - 学生時代に2chのスレッドをスクレイピングし、まとめページを自動生成するプログラムを作ったことがある
  - Ruby
    - 複数ファイルに出力されたログファイルを1つのファイルに集約したくて、fluentdを導入
    - fluentdの標準では、ファイル名を固定にできなかったので、ファイル名を固定にするプラグインを自作した。この時に使用
    - fluentdを入れたことでRuby実行環境が整ったので、GoogleDrive、spreadsheetにデータを自動アップロードするプログラムを作成した
  - JavaScript
    - ajaxと言っていた頃に使っていたのが最後の記憶です
    - モダンな部分のキャッチアップ、実践が圧倒的に不足
  - JavaScript(jQuery)
    - 既存WEBシステムのサーバサイドのコードを大きく変えずに見た目、機能を加えたい時、サーバ側に簡単なAPIを作り、jQueryで取得、画面を変更という裏技？的な逃げ方で使っていた
  - HTML
    - HTML5について、しっかり追いかけたことはないが、いままでの延長でどうにかなるだろうと思っている
  - CSS
    - べた書き程度はできると思う
    - トランスパイルやビルドで生成する手法はまだ使ったことがない
  - シェルスクリプト
    - 一番得意な部分かもしれない
    - bashの組み込み変数は得意じゃない
    - ワンライナーで書き上げるのが好き
  - SQL
    - 必要な情報を取得する分には困らない
    - 分析、集計を求められるとちょっと苦手
    - EXPLAINもなんとなく読める
- 日本語
  - ネイティブ
  - 「お前の話は、何が言いたいかわかりにくい！」と嫁になじられる
- 英語
  - かんたんな日常会話ができる？（実戦経験ほぼなし）
  - インド拠点からの電話でワタワタする

### クラウド

業務では使う機会がない。
環境を作るぐらいは、オンプレの延長でできるだろうと思っている。

- AWS
  - AlexaDayに行くため、アカウントを作った
- Azure
  - AzureADを評価したくてアカウントを作った
- GCP
  - 会社のメールがGoogleなので、その流れで活用しようかと思い準備した

### その他

- ID管理
  - IDライフサイクル管理を担う仕組みを2社で担当
  - 1社目では、上流からのデータ入手、プロビジョニングデータの生成、プロビジョニング処理とすべての工程を2名で内製開発、運用しており、そのうちの1名だった
  - 1社目で、組織におけるアカウント作成のルール、ポリシー、思想のようなものをすり込まれる
  - 2社目は、パッケージ製品を使っており、その運用を1人で担当
  - 前職の思想をもとに、アカウント生成に睨みをきかせている
  - プロビジョニング先の仕様変更などのリクエストに対して、改修リクエストを開発保守パートナーに投げる役目
- 認証、認可
  - 2社目で深く学習した
  - アプリ担当にID管理がカバーする範囲、認証、認可の役割分担について布教活動を行っている（アプリ担当のID管理のイメージにすべてが含まれている雰囲気があるので）
  - SAML、OAuth、OpenIDConnectの認証、認可の連携、方式をもっと活用していきたい
- 証明書、認証局
  - 証明書、認証局の関係など大きなイメージを説明できる（と思う）
  - 証明書取得の手順（CSRを作るとか）から、サーバへの設定までやれる
  - 自己署名の認証局を作ったり、クロスルート証明書といった変わった構成を作って運用している
- Proxy、PAC
  - 社内からインターネットを閲覧させる時に使っているやつ
  - SaaSサービスはこっちのプロキシ、それ以外はあっちのプロキシといったプロキシ制御をPACで書いている
  - PACのデバッグをChromeでできると最近知って、ちょとはかどる
  - HTTPSの復号を行うプロキシと、行わないプロキシの2種類を運用している
  - 復号を行うタイプのプロキシでアクセスできない時、「SSLのハンドシェイク部分に問題があって、暗号スイートが対応してないんじゃない」と言ったりできる

## 強み

- インプリメンテーション

  作成したプログラムをサーバに乗せただけでは、システムはユーザまで届かないと思っています。ユーザに届けるためには、ネットワークの疎通、DNS、プロキシ、メールを送信するためには、SMTP、外部システムと連携するためには、サーバ間通信といろいろ環境に応じた調整ごとが必要です。さまざまな要素技術の実装や運用経験があるため、システムをユーザに届けるための不足部分をつなぎ合わせるのが得意です。さらにプログラム開発もやっていたので、プログラム側からのつなぎ合わせの調整もやれると思っています。

- サーバ/システムの読解力

  いままでに300台近い多種多様のサーバ、システムを扱ってきました。与えられる情報は、IPとログイン情報だけということが多かったです。そのため、ログインさえできればOS種別や起動プロセスからどういった機能が動いているサーバなのか、問題がどこにあるのか、エラーが出ているのかなど、情報を読み取り運用できます。

## やったことはないが興味があるもの

- Firebase+Vue.js
- サーバ脆弱性診断ツール
- DNSエントリーのGit管理

## 職務経歴

### 2014/08 - : 製造業（ユーザ数3,000人～20,000人）の社内SE

### 2005/04 - 2014/07 : 製造業（ユーザ数20,000人）の社内SE
