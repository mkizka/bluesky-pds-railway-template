# bluesky-pds-railway-template

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/template/xBNJ1u?referralCode=mveF9L)

このリポジトリは、このテンプレートの使い方を説明するためのものです。

これは非公式のテンプレートです。ここで使用されている環境変数の設定は、公式のインストールスクリプトに基づいています

https://github.com/bluesky-social/pds/blob/main/installer.sh

ご質問がある場合は、[@mkizka.dev](https://bsky.app/profile/mkizka.dev) までお問い合わせください。

## 使い方

1. 「Deploy on Railway」をクリック
1. 「Deploy Now」をクリック
1. Environment variables を入力して「Deploy」をクリック
1. デプロイが完了したらPDSの「Settings」→「Public Networking」に移動し、使用したいドメインを登録します。ドメインは `PDS_HOSTNAME` 環境変数と一致させる必要があります。例：
   | ドメイン        | ポート |
   | -------------- | ---- |
   | example.com    | 3000 |
   | *.example.com  | 3000 |

1. Cloudflareまたは他のDNSプロバイダーを使用して、ドメインのCNAMEレコードを設定します。詳しくは[Railwayのドキュメント](https://docs.railway.com/guides/public-networking#custom-domains)を参照してください。


## アカウントの作成方法

PDSにアカウントを作成するにはいくつかの方法があります。

### Webツール

私が作成した以下のツールが利用できます。

https://mkizka.github.io/pdsadmin-web/ 

作成したPDSの`PDS_HOSTNAME`と、自動生成された `PDS_ADMIN_PASSWORD`でログインして新しいアカウントを作成してください。

招待コードを発行し、https://bsky.app でアカウントを作成することも出来ます。

### コマンドライン

以下のコマンドを実行してアカウントを作成することも出来ます。[railway CLI](https://docs.railway.com/guides/cli)が必要です。

```
$ git clone https://github.com/bluesky-social/pds  
$ cd pds  
$ vim ./pdsadmin/account.sh # pds.envを参照している6行目と7行目をコメントアウト
$ railway link # 生成されたプロジェクトを選択
> Select a workspace: your-workspace  
> Select a project: your-project  
> Select an environment: production  
> Select a service: pds  
$ railway run bash ./pdsadmin/account.sh create  
Enter an email address (e.g. alice@example.com): example@example.com  
Enter a handle (e.g. alice.example.com): alice.example.com  

Account created successfully!  
-----------------------------  
Handle   : alice.example.com  
DID      : did:plc:xxxxxxxxxx  
Password : xxxxxxxxxx  
-----------------------------  
Save this password, it will not be displayed again.
```
