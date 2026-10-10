# Patafoin Home Assistant apps (add-ons)

[![Open your Home Assistant instance and show the add app repository dialog with this repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FPatafoin%2Fha-addons)

| App | Description |
|---|---|
| [My Bank API](my_bank_api/) | Personal finance backend for the [My Bank](https://github.com/Patafoin/ha-my-bank) integration |

## Installation

Settings → Apps → Install app → ⋮ → Repositories → add `https://github.com/Patafoin/ha-addons`, or use the button above.

Recent Home Assistant versions call them **apps**; older versions call them **add-ons** (Settings → Add-ons → Add-on store). Requires Home Assistant OS or a Supervised installation.

The app uses the multi-architecture image `ghcr.io/patafoin/my-bank-api`, built from the [my-bank-api](https://github.com/Patafoin/my-bank-api) repository.
