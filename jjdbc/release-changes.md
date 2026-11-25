This preface contains:

- Changes in Oracle Database 19c

### Changes in Oracle Database 19c

The following are changes in Oracle Database JDBC Developer's Guide for Oracle Database 19c.

#### New Features

The following features are new in this release:

- Enhancement to Application Continuity

  See [Support for Transparent Application Continuity](application-continuity.md)

- Support for Easy Connect Plus

  See [Support for Easy Connect Plus](data-sources-and-URLs.md)

- Support for token-based authentication

  See [JDBC Client-Side Security Features](client-side-security.md)

#### Deprecated Features

The following features are deprecated, and may be desupported in a future release:

- The following APIs from the `OraclePreparedStatement` and `OracleCallableStatement` classes have been deprecated as part of enhanced support for Associative Arrays:

  - `setPlsqlIndexTable`

  - `setPlsqlIndexTableAtName`

  - `registerIndexTableOutParameter`

  - `getOraclePlsqlIndexTable`

  - `getPlsqlIndexTable`

- Concrete classes in the `oracle.sql` package

  The concrete classes in the `oracle.sql` package are deprecated. Use the new JDBC interfaces instead of these classes.

  See MoS Note 1364193.1 for more information about these interfaces.

- The `oracle.jdbc.rowset` package is deprecated. Oracle recommends that you use the Standard JDBC `RowSet` package to replace this feature.

  **See Also:**

  [http://docs.oracle.com/javase/9/docs/api/javax/sql/rowset/package-summary.html](http://docs.oracle.com/javase/8/docs/api/javax/sql/rowset/package-summary.html)

- `defineColumnType` method

  Most of the variants of the `defineColumnType` method are deprecated. The supported variants are for:

  - LOB to LONG conversions

  - Configure the LOB prefetch size

  See the JDBC Javadoc for more information.

- `CONNECTION_PROPERTY_STREAM_CHUNK_SIZE` property

  See the JDBC Javadoc for more information.

- Oracle Update Batching

  Oracle update batching was deprecated in Oracle Database 12c Release 1 (12.1). Since Oracle Database 12c Release 2 (12.2), Oracle update batching is a no operation code (no-op). This means that if you implement Oracle update batching in your application, using the Oracle Database 19c JDBC driver, then the specified batch size is not set and results in a batch size of 1. With this batch setting, your application processes one row at a time. Oracle strongly recommends that you use the standard JDBC batching if you are using the Oracle Database 19c JDBC driver.

  See [Standard Update Batching](performance-extensions.md) section for more information.

- `EndToEndMetrics` related APIs

  `EndToEndMetrics` related APIs are deprecated since Oracle Database 12c release 2 (12.2).

  See [JDBC DMS Metrics](JDBC-DMS-Metrics.md) for more information.

#### Other Changes

Security Update for Native Encryption

Oracle provides a patch that you can download to address necessary security enhancements that affect native network encryption environments in Oracle Database release 11.2 and later. This patch is available in My Oracle Support note 2118136.2.

**See Also:**

[Oracle Database Security Guide](../dbseg/release-changes.md) for more information
