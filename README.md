# pg-commands

**Live:** https://manideepgrandhi.github.io/pg-commands/

A daily-driver page for PostgreSQL client commands: **pg_dump**, **pg_restore** and **psql** (PostgreSQL 13–17).
It's one self-contained `index.html` with no build step, no CDNs and no server, so it works offline. Everything stays in your browser.

![Desktop](screenshots/desktop.png)

## Features
- **Command builder.** Tabs for pg_dump, pg_restore and psql, with grouped options and an explanation for each one. The command updates live with correct shell quoting, and has Copy, Reset and multi-line buttons.
- **Validation as you type.** It warns about `-j` without `-Fd`, `--single-transaction` with `-j`, `--clean` without `--if-exists`, `--if-exists` without `--clean`, compression with `-Ft`, a plain `.sql` file given to pg_restore, schema-qualified `pg_restore -t`, and scripts run without `ON_ERROR_STOP`. A **red banner** appears when the restore target host or database name contains `prod`.
- **`\copy` helper.** Turns a query into a client-side CSV export with `HEADER`.
- **27 recipes.** Each has the command, its purpose and a "watch out" note, with Copy and *Load into builder*. You can search them and filter by tool.
- **Connection profiles.** Saves name, host, port, user and database in localStorage, never passwords. You can export and import them as JSON.

Every builder combination and recipe was run against a local PostgreSQL 17 server with the PG17 client tools.

## Also see
[pg-dump-wrapper](https://github.com/manideepgrandhi/pg-dump-wrapper): wrapper scripts for logged, scheduled pg_dump and psql runs.

<img src="screenshots/mobile.png" alt="Mobile view" width="300">
