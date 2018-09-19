# TL;DR CockroachDB Documentation

- Easiest way to install on your local machine `brew install cockroach`.
- Easiest way to run on dev. `cockroach start --insecure`. 
- Just after launch, it shows you some stuff about the node, including its admin UI and connection string.
- It uses driver of Postgres, so almost everywhere you can use it.
- Hopefully, Cockroach supports SQL.
- Definition of table is a bit different than definition of Postgres.
- In order to access db by terminal, just enter `cockroach sql --insecure`
- Type `\q` to exit from SQL shell
- Supported row values are `int, float, real, boolean, decima, numeric, null,bytes, string, character, collate, auto increament, key-value, array, uuid, json, time, xml, uint, set, enum, inet` [[details]](https://www.cockroachlabs.com/docs/stable/sql-feature-support.html#row-values)
- Supported constraints are `not null, unique, primary key, check, foreign key, default value` [[details]](https://www.cockroachlabs.com/docs/stable/sql-feature-support.html#constraints)
- Transactions operators are `begin, commit, rollback, savepoint` [[details]](https://www.cockroachlabs.com/docs/stable/sql-feature-support.html#transactions)
- Supported indexes are `standard, multi-col, covering, inverted` [[details]](https://www.cockroachlabs.com/docs/stable/sql-feature-support.html#indexes)
- DB has no explicit limitation on number of column to be indexed.
- Unfortunately, it doesn't support `geospatial` indexes for now.
- Full-text indexes are not supported yet but it's planned.
- Right now, It can't apply multiple indexes on a single query but it's planned to adopt.
- Apply a function on a column in a where clause causes a full table scan, so don't use it unitl db supports prefix/experssion indexes.
- It supports `UPSERT`.
- If you need to dig into a query just add `explain` before the query. It's much more self-explanatory than mysql.
- There are five categories of constant `String literals 'hello', Numeric literals -1.63, Byte array literals b'hello', Interpreted literals INTERVAL '3 days', Named constants NULL TRUE`.
- Two simple string literals separated by a newline character are automatically concatenated together to form a single constant.
- It supports string literals containing escape sequences like in the programming language C. These are constructed by prefixing the string literal with the letter e, for example, e'hello\nworld!'
- The two differences between byte array literals and string literals with character escapes are as follows:
  * Byte array literals always have data type BYTES, whereas the data type of a string literal depends on context.
  * Byte array literals may contain invalid UTF-8 byte sequences, whereas string literals must always contain valid UTF-8 sequences.
- A `VALUES` clause defines tabular data defined by the expressions listed within parentheses (try `VALUES (1, 2, 3), (4, 5, 6);`)
