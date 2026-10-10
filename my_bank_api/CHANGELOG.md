# Changelog

## 0.6.0

- First release as a Home Assistant add-on.
- The add-on creates its own access token and announces itself to Home Assistant: the My Bank integration is discovered and configured without typing a URL or a token.
- Data (`my_bank.sqlite`) and nightly backups live in the add-on `/data` folder, so they are part of Home Assistant backups; a consistent SQLite snapshot is taken right before each Home Assistant backup.
