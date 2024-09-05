<!-- omit in toc -->
# PostgreSQL

<!-- omit in toc -->
## Table of contents

- [Clone a database](#clone-a-database)
- [References](#references)

## Clone a database

```sql
CREATE DATABASE newdb WITH TEMPLATE originaldb OWNER dbuser;
```

To disconnect all other users from the database, you can use this query:

```sql
SELECT
  pg_terminate_backend(pg_stat_activity.pid)
FROM
  pg_stat_activity
WHERE
  pg_stat_activity.datname = 'originaldb'
  AND pid <> pg_backend_pid();
```

## References

- <https://www.yellowduck.be/posts/creating-a-copy-of-a-database-in-postgresql>
