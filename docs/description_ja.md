# RailwayでBluesky PDSをデプロイ・ホスティングする

Bluesky PDSは、分散型ソーシャルネットワークBlueskyで利用される個人用データサーバーです。ユーザーのプロフィールや投稿データを管理し、Blueskyネットワーク内の認証やデータのやりとりを担います。

使い方は https://github.com/mkizka/bluesky-pds-railway-template を確認してください。

## Bluesky PDSのホスティングについて

PDSのホスティングにはVPSでインストールスクリプトを実行する必要がありましたが、RailwayのようなPaaSではサーバー管理不要で簡単にセルフホスティングすることが出来ます。

## 主な利用ケース

- AT Protocolのリポジトリをセルフホスティングする
- Blueskyに依存しないアカウントを運用する

## Bluesky PDSホスティングの依存関係

- なし

### デプロイに必要な依存項目

- Bluesky PDS公式リポジトリ - https://github.com/bluesky-social/pds


## なぜRailwayでBluesky PDSをデプロイするのか？

Railwayはインフラストラクチャを簡単にデプロイできるプラットフォームです。Railway上でホスティングすることで、複雑な設定をせずに、垂直・水平スケールにも柔軟に対応できます。

Bluesky PDSをRailwayにデプロイすることで、最小限の負担でフルスタックアプリケーションの運用に一歩近づけます。サーバー、データベース、AIエージェントなどもRailway上でホスト可能です。
