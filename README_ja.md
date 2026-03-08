# bluesky-pds-railway-template

[English version / 英語版](README.md)

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/xBNJ1u?referralCode=mveF9L)

このリポジトリは、[Bluesky PDS](https://railway.com/template/xBNJ1u?referralCode=mveF9L)テンプレートの使い方を説明するためのものです。

これは非公式のテンプレートです。ここで使用されている環境変数の設定は、公式のインストールスクリプトに基づいています

https://github.com/bluesky-social/pds/blob/main/installer.sh

ご質問がある場合は、[@mkizka.dev](https://bsky.app/profile/mkizka.dev) までお問い合わせください。

## 使い方

1. 「Deploy on Railway」をクリック
1. 「Deploy Now」をクリック
1. Environment variables を入力して「Deploy」をクリック
1. デプロイが完了したらPDSの「Settings」→「Public Networking」に移動し、使用したいドメインを登録します。ドメインは `PDS_HOSTNAME` 環境変数と一致させる必要があります。例：
   | ドメイン | ポート |
   | -------------- | ---- |
   | example.com | 3000 |
   | \*.example.com | 3000 |

1. Cloudflareまたは他のDNSプロバイダーを使用して、ドメインのCNAMEレコードを設定します。詳しくは[Railwayのドキュメント](https://docs.railway.com/guides/public-networking#custom-domains)を参照してください。

## アカウントの作成方法

PDSにアカウントを作成するにはいくつかの方法があります。いずれの方法でも以下の環境変数が必要です。

- `PDS_HOSTNAME` ... テンプレートに入力した値
- `PDS_ADMIN_PASSWORD` ... デプロイ後に自動生成された値。Railway上でPDSの「Variables」から確認できます。

### コマンドライン(goat)

[goat](https://github.com/bluesky-social/goat)を使用してコマンドラインからアカウントを作成できます。goatはBluesky公式のAT Protocol用CLIツールです。

まず[bluesky-social/pds](https://github.com/bluesky-social/pds?tab=readme-ov-file#goat-cli)の手順に従ってgoatコマンドをインストールします。

その後、以下のコマンドでアカウントを作成できます。

```
$ goat pds admin account create \
    --pds-host https://${PDS_HOSTNAME} \
    --admin-password ${PDS_ADMIN_PASSWORD} \
    --handle ハンドル.${PDS_HOSTNAME} \
    --email あなたのメールアドレス \
    --password あなたのパスワード
```

ハンドルは`PDS_HOSTNAME`のサブドメインである必要があります。(例：alice.example.com)

### コマンドライン(curl)

goatの代わりに、curlで直接APIリクエストを送ることも可能です。

https://atproto.wiki/en/wiki/pds#running-bluesky-pds-with-railway を参照して招待コードを発行し、https://bsky.app でアカウントを作成出来ます。

### Webツール

コマンドラインに慣れていない場合は、私が作成した以下のツールが利用できます。

https://mkizka.github.io/pdsadmin-web/

リポジトリは[こちら](https://github.com/mkizka/pdsadmin-web)。`PDS_HOSTNAME`と`PDS_ADMIN_PASSWORD`でログインして新しいアカウントを作成してください。
