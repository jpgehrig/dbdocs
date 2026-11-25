No changes have been made in Oracle OLAP DML Reference in this release. For information on changes in earlier releases, see the following topics.

### Changes in Oracle OLAP in Oracle Database 12c Release 2 (12.2)

The following change is in Oracle OLAP DML Reference for Oracle Database 12c Release 2 (12.2):

- The OBJ function has the new keyword CHANGEDPAGES, which returns the number of pages in the analytic workspace that have changed since the last update.

Also, Active Data Guard (ADG) read-only active standby instances now support read-only OLAP applications. An active standby instance must have real-time apply operating.

You can now offload to ADG active standby instances applications that query CUBE_TABLE and OLAP_TABLE functions that use dynamic abstract data types (ADTs). The initial ADT creation triggers a request to create it on the ADG primary. Real-time apply propagates the new ADT to the active standby instance, which allows the query to run after a short delay. If the ADT fails to appear on the standby in a reasonable time, then an error condition occurs.

### Changes in Oracle OLAP in Oracle Database 12c Release 2 (12.1)

The following are changes in Oracle OLAP DML Reference for Oracle Database 12c Release 1 (12.1).

- New Features

- Other Changes

#### New Features

The following features are new in this release:

- Increased maximum line length

  The maximum line length of text has changed from 4,000 to 32,767.

  See the descriptions of TEXT and NTEXT in [Text Data Types](data-types-operators-and-expressions.md), and the [EXTCOLS](olap-dml-functions-a-k.md), [INSCOLS](olap-dml-functions-a-k.md), [JOINBYTES](olap-dml-functions-a-k.md), [JOINCOLS](olap-dml-functions-a-k.md), [REMCOLS](olap-dml-functions-l-z.md), and [REPLCOLS](olap-dml-functions-l-z.md) functions.

#### Other Changes

The following are additional changes in the release:

- Performance enhancement

  A new highly compact storage format for valuesets.

  See the NOORDER keyword of [DEFINE VALUESET](olap-dml-commands-a-g.md).

- Changes in statements

  The following statements have been changed in the OLAP DML in Oracle Database 12c:

  - [DEFINE VALUESET](olap-dml-commands-a-g.md)
  - [EXTCOLS](olap-dml-functions-a-k.md)
  - [INSCOLS](olap-dml-functions-a-k.md)
  - [JOINBYTES](olap-dml-functions-a-k.md)
  - [JOINCOLS](olap-dml-functions-a-k.md)
  - [REMCOLS](olap-dml-functions-l-z.md)
  - [REPLCOLS](olap-dml-functions-l-z.md)
