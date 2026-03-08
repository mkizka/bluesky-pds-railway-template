# bluesky-pds-railway-template

[日本語版 / Japanese version](README_ja.md)

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/xBNJ1u?referralCode=mveF9L)

This repository is for explaining how to use the [Bluesky PDS](https://railway.com/template/xBNJ1u?referralCode=mveF9L) template.

This is an unofficial template. The environment variable settings used here are based on the official installation script:

https://github.com/bluesky-social/pds/blob/main/installer.sh

If you have any questions, please contact [@mkizka.dev](https://bsky.app/profile/mkizka.dev).

## Usage

1. Click "Deploy on Railway"
1. Click "Deploy Now"
1. Enter Environment variables and click "Deploy"
1. Once deployment is complete, go to PDS "Settings" → "Public Networking" and register the domain you want to use. The domain must match the `PDS_HOSTNAME` environment variable. Example:
   | Domain | Port |
   | -------------- | ---- |
   | example.com | 3000 |
   | \*.example.com | 3000 |

1. Use Cloudflare or another DNS provider to set up CNAME records for your domain. For details, see [Railway documentation](https://docs.railway.com/guides/public-networking#custom-domains).

## How to Create an Account

There are several ways to create an account on PDS. All methods require the following environment variables:

- `PDS_HOSTNAME` ... The value you entered in the template
- `PDS_ADMIN_PASSWORD` ... Automatically generated value after deployment. You can check it from "Variables" of PDS on Railway.

### Command Line (goat)

You can create an account from the command line using [goat](https://github.com/bluesky-social/goat). goat is the official Bluesky CLI tool for the AT Protocol.

First, install the goat command by following the instructions at [bluesky-social/pds](https://github.com/bluesky-social/pds?tab=readme-ov-file#goat-cli).

Then, create an account with the following command.

```
$ goat pds admin account create \
    --pds-host https://${PDS_HOSTNAME} \
    --admin-password ${PDS_ADMIN_PASSWORD} \
    --handle handle.${PDS_HOSTNAME} \
    --email your-email@example.com \
    --password your-password
```

The handle must be a subdomain of `PDS_HOSTNAME`. (e.g. alice.example.com)

### Command Line (curl)

Instead of goat, you can also send API requests directly with curl.

See https://atproto.wiki/en/wiki/pds#running-bluesky-pds-with-railway to issue an invitation code and create an account at https://bsky.app.

### Web Tool

If you're not familiar with the command line, you can use the following tool that I created:

https://mkizka.github.io/pdsadmin-web/

Repository is [here](https://github.com/mkizka/pdsadmin-web). Log in with `PDS_HOSTNAME` and `PDS_ADMIN_PASSWORD` to create a new account.
