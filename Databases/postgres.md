# Postgres

In PostgreSQL, the auto-increment counter doesn’t get updated if an ID is provided in the insert statement, which seems to lead to odd behaviour when using Laravel factories or copy from statements to populate tables. The issue can be resolved by running something like `SELECT setval('users_id_seq', max(id)) FROM users;`

It is possible to perform recursive queries in Postgres using the`WITH RECURSIVE` function.
