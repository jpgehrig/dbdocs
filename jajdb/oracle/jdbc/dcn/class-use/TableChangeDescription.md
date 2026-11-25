Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TableChangeDescription.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.dcn.TableChangeDescription

- **Packages that use [TableChangeDescription](../TableChangeDescription.md)**

  | Package         | Description                                                                                                                     |
  |-----------------|---------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc.dcn | This package is an Oracle JDBC extension that provides interfaces to access the Database Change Notification feature of Oracle. |

- - ### Uses of [TableChangeDescription](../TableChangeDescription.md) in [oracle.jdbc.dcn](../package-summary.md)

    **Methods in [oracle.jdbc.dcn](../package-summary.md) that return [TableChangeDescription](../TableChangeDescription.md)**

    | Modifier and Type                                                       | Method and Description                                                                                                                                                                                                             |
    |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`TableChangeDescription`](../TableChangeDescription.md)`[]` | DatabaseChangeEvent.[`getTableChangeDescription`](../DatabaseChangeEvent.md)`()`<br>For object change (`EVENT_TYPE_OBJCHANGE`) kind of events, this method returns the description of the changes for each table that was changed. |
    | [`TableChangeDescription`](../TableChangeDescription.md)`[]`            | QueryChangeDescription.[`getTableChangeDescription`](../QueryChangeDescription.md)`()`<br>Returns the table level change description of this query result.                                                                         |
    | [`TableChangeDescription`](../TableChangeDescription.md)`[]`            | QueryChangeDescription.[`getTableChangeDescription`](../QueryChangeDescription.md)`()`<br>Returns the table level change description of this query result.                                                                         |
    | `abstract `[`TableChangeDescription`](../TableChangeDescription.md)`[]` | DatabaseChangeEvent.[`getTableChangeDescription`](../DatabaseChangeEvent.md)`()`<br>For object change (`EVENT_TYPE_OBJCHANGE`) kind of events, this method returns the description of the changes for each table that was changed. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TableChangeDescription.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
