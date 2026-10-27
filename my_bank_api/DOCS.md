# My Bank API

Backend of the [My Bank integration](https://github.com/Patafoin/ha-my-bank): your accounts, transactions, categories, budgets and scheduled transactions, stored locally in a SQLite database. Nothing leaves your Home Assistant host.

## Installation

1. Install and start this app (called an add-on in older Home Assistant versions).
2. Home Assistant shows **New device discovered: My Bank** (Settings → Devices & services). Click **Configure**, then **Submit**.
   The app created an access token for Home Assistant on first start and passed it on: there is no URL or token to type.
3. Install the **My Bank** integration from HACS if you have not done so yet, then restart Home Assistant. The discovery appears after the restart.

## Data and backups

- The database lives in the app `/data` folder and is included in Home Assistant backups.
- Right before each Home Assistant backup, the app writes a consistent SQLite snapshot to `/data/backups`.
- It also keeps nightly snapshots there (3 a.m.): the last 14 days and the first of each month for 12 months.

## Network

The API listens on port 8000 inside the internal app network only. Home Assistant reaches it directly; nothing is published on your LAN by default.

To browse the interactive API documentation (`/docs`) or use the API from another device, set a host port in the **Network** section (for example 9931). The documentation is off by default (it is readable without a token): turn on the **docs** option and restart the app to browse it. Every API call requires a token: set the **api_token** option to a long random string of your choice, restart the app, and use it as `Authorization: Bearer <api_token>`. Home Assistant does not need it (its own token is created automatically). Clearing the option and restarting the app revokes the token.

**Never expose this port to the Internet.** Remote access goes through Home Assistant.

## Importing from MS Comptes Bancaires

The API can import the QIF and payee CSV exports of MS Comptes Bancaires (`POST /api/v1/import/ms`, dry run by default). See the [My Bank API README](https://github.com/Patafoin/my-bank-api).
