# Grail

## Run your app and your analytics on one database, at any scale.

Customer-facing metrics and reports run on the same database that powers your product. There's no second database to set up and no data to copy between them. No matter the scale.

Same data, same database. Your app reads rows (for example, `SELECT * FROM orders WHERE id = 1042`), your analytics scans columns (for example, `SELECT sum(amount) FROM orders`).

[Get early access](https://YOUR_DOMAIN/#access)

## The continuous engineering tax of keeping two databases in sync

Most applications end up with two databases: one to run the product, another for analytics, and a pipeline to keep them in sync. Every schema change, backfill, and broken job becomes work for your engineers, and it never stops. With Grail, it's one database: a single source of truth for your product and your analytics, at any scale, with nothing to keep in sync.

**Before:** your app sends writes to an OLTP database and analytics queries to a separate OLAP database, with an ETL/CDC pipeline copying data between them.

- 2 databases
- Data drifting out of sync
- Continuous engineering tax

**After:** your app sends both writes and analytics queries to Grail.

- 1 database
- Single source of truth
- Analytics at any scale

## Built for both, from the storage engine up

Grail runs on a custom-designed LSM storage engine in which every file holds data in both row and columnar formats. Your app's reads and writes and your analytics queries run against the same data, in the same database.

- **Row and columnar, in the same files.** Transactions use the row layout, and analytical scans use the columnar layout, so there's no second system and no conversion jobs.
- **Analytics that doesn't slow your app.** Heavy analytical queries run without dragging down transactional performance.
- **Fresh data for analytics.** Queries run on current data, not last night's batch.

## Planning your analytics stack? Start with one database.

[Get early access](https://YOUR_DOMAIN/#access)
