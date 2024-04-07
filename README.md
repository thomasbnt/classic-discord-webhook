[![](https://img.shields.io/badge/-Github_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/marketplace/actions/classic-discord-webhook) [![Twitter Follow](https://img.shields.io/badge/Follow%20me%20on-Twitter-1DA1F2?&logo=Twitter&style=for-the-badge)](https://twitter.com/Thomasbnt_) [![Follow @mrrobot on DEV](https://img.shields.io/badge/dev.to-%2308090A.svg?&style=for-the-badge&logo=dev.to&logoColor=white&alt=devto)](https://dev.to/mrrobot)

<div style="display: flex; align-items: center;">
  <img src="docs/classic_discord_webhook.png" width="100"  alt="Classic Discord Webhook logo"/>
  <h1 style="margin-left: auto;">Discord Webhook</h1>
</div>

## Screenshots

The standard webhook from GitHub to Discord just dumps the commit messages right into your chat, this is fine but sometimes you just want some extra information. Did the commit introduce any new issues? Did it even compile successfully? That's what this Action is for.

|                                                        Standard Webhook                                                        |                                                        New and improved Webhook                                                         |
| :----------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------: |
| ![Old webhook interface](https://user-images.githubusercontent.com/14293805/90334058-11e81900-dfcb-11ea-8de0-f01a7591254d.png) | ![New webhook interface](https://github.com/mrrobotdotapp/classic-discord-webhook/assets/14293805/f7ede24b-b902-49f4-8f89-055e9a8a0903) |

## Donate

Feel free to help [me](https://github.com/thomasbnt) for the maintenance of this project !
Thanks to all **Sponsors on GitHub** !

[![Github Sponsors](https://cdn.jsdelivr.net/gh/thomasbnt/sponsors@main/sponsors.svg)](https://github.com/sponsors/thomasbnt)

[![GitHub Sponsors](https://img.shields.io/badge/Sponsor%20me-%23EA54AE.svg?&style=for-the-badge&logo=github-sponsors&logoColor=white)](https://github.com/sponsors/thomasbnt) [![Support me on Buy Me a Coffee](https://img.shields.io/badge/Support%20me-on%20Buy%20Me%20a%20Coffee-%23FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=white)](https://www.buymeacoffee.com/thomasbnt?via=thomasbnt)

## Setup

Setup this code on your repository's `.github/workflows/` in a file like `discord-push.yml` and push the changes:

```yml
name: Discord Webhook
on: [push]
jobs:
  Discord_notification:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
      - name: Run Discord Webhook
        uses: mrrobotdotapp/classic-discord-webhook@main
        with:
          id: ${{ secrets.DISCORD_WEBHOOK_ID }}
          token: ${{ secrets.DISCORD_WEBHOOK_TOKEN }}
          #threadId: ${{ secrets.DISCORD_WEBHOOK_THREAD_ID }} # Optional
```

You can see the example file at [/.github/workflows/discord-push.yml](/.github/workflows/discord-push.yml)

## Inputs

in your **Settings > Security > Secrets and variables > Actions > Secrets** (/settings/secrets/actions) on GitHub, you need to add 2 secrets :

- `DISCORD_WEBHOOK_ID`
- `DISCORD_WEBHOOK_TOKEN`

|                                                  `DISCORD_WEBHOOK_ID`                                                  |                           `DISCORD_WEBHOOK_TOKEN`                           |                                   `DISCORD_WEBHOOK_THREAD_ID`                                   |
| :--------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------: |
| **Required** — This is the id of your Discord webhook, if you copy the webhook url, this will be the first part of it. | **Required** — Your Discord webhook token, it's the second part of the url. | Not required — if you want to send the message in a thread, you can specify the thread id here. |

> [!NOTE]
> Need more help ? [See this post on DEV](https://dev.to/mrrobot/follow-your-repository-from-discord-52ge) or [this post on my blog in French](https://thomasbnt.dev/blog/robot-discord-basique/).
> [![follow your repository from Discord - Post on DEV](https://user-images.githubusercontent.com/14293805/198847774-bd7b38e7-5b61-4723-99a1-e767babac3a5.png)](https://dev.to/mrrobot/follow-your-repository-from-discord-52ge)

### Notable documentations

[How to get Commits on GitHub](https://docs.github.com/en/rest/reference/commits#get-a-commit)
