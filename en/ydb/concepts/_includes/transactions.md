---
sourcePath: en/ydb/ydb-docs-core/en/core/concepts/_includes/transactions.md
---
# {{ ydb-short-name }} transactions and queries

This section describes the specifics of YQL implementation for {{ ydb-short-name }} transactions.

## Query language {#query-language}

The main tool for creating, modifying, and managing data in {{ ydb-short-name }} is a declarative query language called YQL. YQL is an SQL dialect that can be considered a database interaction standard. {{ ydb-short-name }} also supports a set of special RPCs useful in managing a tree schema or a cluster, for instance.

## Transaction modes {#modes}

By default, {{ ydb-short-name }} transactions are performed in *Serializable* mode. It provides the strictest [isolation level](https://en.wikipedia.org/wiki/Isolation_(database_systems)#Serializable) for custom transactions. This mode guarantees that the result of successful parallel transactions is equal to their specific execution sequence, while there are no [read anomalies](https://en.wikipedia.org/wiki/Isolation_(database_systems)#Read_phenomena) for successful transactions.

If consistency or freshness requirement for data read by a transaction can be relaxed, a user can take advantage of execution modes with lower guarantees:

* *Online Read-Only*. Each of the reads in the transaction reads data that is most recent at the time of its execution. The consistency of retrieved data depends on the *allow_inconsistent_reads* setting:
    * *false* (consistent reads). In this mode, each individual read returns consistent data, but no consistency between different reads is guaranteed. Reading the same table range twice may return different results.
    * *true* (inconsistent reads). In this mode, even data from separately taken reads may contain inconsistent results.
* *Stale Read Only*. Data reads in a transaction return results with a possible delay (fractions of a second). Each individual read returns consistent data, but no consistency between different reads is guaranteed.

The transaction execution mode is specified in its settings when creating the transaction.

## YQL language {#language-yql}

The constructs implemented in YQL can be divided into two classes: [data definition language (DDL)](https://en.wikipedia.org/wiki/Data_definition_language) and [data manipulation language (DML)](https://en.wikipedia.org/wiki/Data_manipulation_language).

For more information about supported YQL constructs, see the [YQL documentation](../../yql/reference/index.md).

Listed below are the features and limitations of YQL support in {{ ydb-short-name }}, which might not be obvious at first glance and are worth noting:

* Multi-statement transactions (transactions made up of a sequence of YQL statements) are supported. Transactions may interact with client software, or in other words, client interactions with the database might look as follows: `BEGIN; make a SELECT; analyze the SELECT results on the client side; ...; make an UPDATE; COMMIT`. We should note that if the transaction body is fully formed before accessing the database, it will be processed more efficiently.
* {{ ydb-short-name }} does not support transactions that combine DDL and DML queries. The conventional notion [ACID](https://ru.wikipedia.org/wiki/ACID) of a transactions is applicable specifically to DML queries, that is, queries that change data. DDL queries must be idempotent, meaning repeatable if an error occurs. If you need to manipulate a schema, each manipulation is transactional, while a set of manipulations is not.
* The version of YQL in {{ ydb-short-name }} uses the [Optimistic Concurrency Control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control) mechanism. Optimistic locking is applied to entities affected during a transaction. When the transaction is complete, the mechanism verifies that the locks have not been invalidated. For the user, locking optimism means that when transactions are competing with one another, the one that finishes first wins. Competing transactions fail with the `Transaction locks invalidated` error.
* All changes made during the transaction accumulate in the database server memory and are committed when the transaction completes. If the locks are not invalidated, all the changes accumulated are committed atomically, but if at least one lock is invalidated, none of the changes are committed. The above model involves certain restrictions: changes made by a single transaction must fit inside available memory, and a transaction "doesn't see" its changes.

A transaction should be formed in such a way so that the first part of the transaction only reads data, while the second part of the transaction only changes data. The query structure then looks as follows:

```yql
       SELECT ...;
       ....
       SELECT ...;
       UPDATE/REPLACE/DELETE ...;
       COMMIT;
```

For more information about YQL support in {{ ydb-short-name }}, see the [YQL documentation](../../yql/reference/index.md).

## Distributed transactions {#distributed-tx}

A database table in {{ ydb-short-name }} can be sharded by the range of the primary key values. Different table shards can be served by different distributed database servers (including ones in different locations). They can also move independently between servers to enable rebalancing or ensure shard operability if servers or network equipment goes offline.

{{ ydb-short-name }} supports distributed transactions. Distributed transactions are transactions that affect more than one shard of one or more tables. They require more resources and take more time. While point reads and writes may take up to 10 ms in 99 percentile, distributed transactions typically take from 20 to 500 ms.

