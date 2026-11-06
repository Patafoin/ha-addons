# Changelog

## 0.10.0

- Payment due date: a transaction can have an optional `due_date` (null by default: nothing changes for it). `GET /transactions?due_before=…` lists the transactions due by that date (combine with `state=0` for the unpaid ones).
- Scheduled transactions: optional `due_days`; each generated transaction gets a due date of its date + `due_days` days (0 = same day). Empty by default: no due date.

## 0.9.0

- Bulk categorize: `POST /transactions/categorize` changes the category, class and/or payee of several transactions at once, by id.
- Category, class and payee are no longer locked by reconciliation: changing them on a reconciled transaction (single or bulk) no longer requires un-reconciling it first, since none of them affects a balance.

## 0.8.0

- Account currency: `currency` (ISO 4217, e.g. EUR, USD, GBP) can now be set when creating or updating an account; defaults to EUR when not given.
- A transfer (direct or scheduled) between two accounts of different currencies is refused: the app never converts between currencies.

## 0.7.0

- Default account: one account can be marked as the default; it is preselected wherever an account is chosen.
- Security: a file attachment is only shown in the browser for safe types (PDF, PNG, JPEG, GIF, WebP, plain text); any other type (HTML, SVG…) is downloaded instead, so it can no longer run script in Home Assistant.
- Security: attachment links must start with `http://` or `https://`.
- Security: requests over 14 MiB are refused (413) before being read into memory.
- Fix: a file attachment whose name has non-Latin characters (e.g. `€`) could not be opened.
- The interactive documentation (`/docs`, `/redoc`, `/openapi.json`) is now off by default, as it is readable without a token. Turn on the new **docs** option to browse it.

## 0.6.2

- Attachments on a transaction: a link, or a file (10 MiB max, stored in the database). Used by the My Bank integration 0.13.6+.

## 0.6.1

- Fix: the **api_token** option was ignored (the options file is only readable before the server drops root privileges). It now works, and clearing the option revokes the token.
- Tested on Home Assistant OS 18.3 with Home Assistant 2026.10.0.

## 0.6.0

- First release as a Home Assistant add-on.
- The add-on creates its own access token and announces itself to Home Assistant: the My Bank integration is discovered and configured without typing a URL or a token.
- Data (`my_bank.sqlite`) and nightly backups live in the add-on `/data` folder, so they are part of Home Assistant backups; a consistent SQLite snapshot is taken right before each Home Assistant backup.
