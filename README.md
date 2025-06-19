# bluesky-pds-railway-template

[日本語版 / Japanese version](README_ja.md)

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/template/xBNJ1u?referralCode=mveF9L)

This repository is for explaining how to use the [Bluesky PDS](https://railway.com/template/xBNJ1u?referralCode=mveF9L) template.

This is an unofficial template. The environment variable settings used here are based on the official installation script:

https://github.com/bluesky-social/pds/blob/main/installer.sh

If you have any questions, please contact [@mkizka.dev](https://bsky.app/profile/mkizka.dev).

## Usage

1. Click "Deploy on Railway"
1. Click "Deploy Now"
1. Enter Environment variables and click "Deploy"
1. Once deployment is complete, go to PDS "Settings" → "Public Networking" and register the domain you want to use. The domain must match the `PDS_HOSTNAME` environment variable. Example:
   | Domain         | Port |
   | -------------- | ---- |
   | example.com    | 3000 |
   | *.example.com  | 3000 |

1. Use Cloudflare or another DNS provider to set up CNAME records for your domain. For details, see [Railway documentation](https://docs.railway.com/guides/public-networking#custom-domains).


## How to Create an Account

There are several ways to create an account on PDS.

### Command Line (pdsadmin)

You can create an account by running the following commands. You need the [railway CLI](https://docs.railway.com/guides/cli).

```
$ git clone https://github.com/bluesky-social/pds  
$ cd pds  
$ vim ./pdsadmin/account.sh # Comment out lines 6 and 7 that reference pds.env
$ railway link # Select the generated project
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

### Command Line (curl)

You can also send requests directly to the endpoints used by pdsadmin with curl instead of using pdsadmin.

See https://atproto.wiki/en/wiki/pds#running-bluesky-pds-with-railway for details.

### Web Tool

You can use the following tool that I created:

https://mkizka.github.io/pdsadmin-web/ 

Repository is [here](https://github.com/mkizka/pdsadmin-web). Log in with the `PDS_HOSTNAME` of your created PDS and the auto-generated `PDS_ADMIN_PASSWORD` to create a new account.

You can also issue invitation codes using the web tool and create accounts at https://bsky.app.
