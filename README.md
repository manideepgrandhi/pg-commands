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
- **Security (v2).** 40 items in 6 categories: roles & users, audits, connections & SSL, row-level security, auditing & logging, and extras. Each has the SQL or command, its purpose, a "watch out" note and Copy, and you can search and filter them. RDS/Aurora differences are flagged: `rds_superuser`, `rds.force_ssl`, pgaudit via the parameter group, and pg_authid/pg_hba not being readable there.
- **Security role builder.** Generates a read-only or read-write role script (idempotent CREATE ROLE, grants, default privileges, an optional login user and a verification query) for any role, database and schemas.
- **Sample data (v2).** A `demo` schema (customers, products, categories, orders, order_items) with PKs, FKs, CHECKs, indexes and JSONB. It loads data three ways (hand-written INSERTs, generate_series with configurable row counts, and `\copy` from a downloadable CSV) and has 12 practice queries: joins, GROUP BY/HAVING, window functions, CTEs, a recursive CTE, JSONB with a GIN index, EXPLAIN ANALYZE, a transaction with ROLLBACK, and upsert. Use **Download demo.sql** or *Copy all*, then run `psql -d mydb -v ON_ERROR_STOP=1 -f demo.sql`. The cleanup step (`DROP SCHEMA demo CASCADE`) is included but commented out.
- **Connection profiles.** Saves name, host, port, user and database in localStorage, never passwords. You can export and import them as JSON.

Every builder combination, recipe, security item that can run locally, role builder script and the full demo script (10k rows) was run against a local PostgreSQL 17 server with the PG17 client tools.

## Also see
[pg-dump-wrapper](https://github.com/manideepgrandhi/pg-dump-wrapper): wrapper scripts for logged, scheduled pg_dump and psql runs.

![Security](screenshots/desktop-security.png)

<img src="screenshots/mobile.png" alt="Mobile view" width="300">
