# Changelog

## 0.6.2

- Attachments on a transaction: a link, or a file (10 MiB max, stored in the database). Used by the My Bank integration 0.13.6+.

## 0.6.1

- Fix: the **api_token** option was ignored (the options file is only readable before the server drops root privileges). It now works, and clearing the option revokes the token.
- Tested on Home Assistant OS 18.3 with Home Assistant 2026.10.0.

## 0.6.0

- First release as a Home Assistant add-on.
- The add-on creates its own access token and announces itself to Home Assistant: the My Bank integration is discovered and configured without typing a URL or a token.
- Data (`my_bank.sqlite`) and nightly backups live in the add-on `/data` folder, so they are part of Home Assistant backups; a consistent SQLite snapshot is taken right before each Home Assistant backup.
