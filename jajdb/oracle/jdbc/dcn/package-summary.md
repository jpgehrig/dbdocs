Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../datasource/package-summary.md)
- [Next Package](../pool/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.dcn

This package is an Oracle JDBC extension that provides interfaces to access the Database Change Notification feature of Oracle.

See: Description

- **Interface Summary**

  | Interface                                                   | Description                                                                                            |
  |-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
  | [DatabaseChangeListener](DatabaseChangeListener.md)         | The listener interface for receiving Database Change Notification (DCN) events.                        |
  | [DatabaseChangeRegistration](DatabaseChangeRegistration.md) |                                                                                                        |
  | [QueryChangeDescription](QueryChangeDescription.md)         | This interface describes a query result change.                                                        |
  | [RowChangeDescription](RowChangeDescription.md)             | This interface describes the row level information that can be retrieved from a database change event. |
  | [TableChangeDescription](TableChangeDescription.md)         | This interface describes a database change at the table level.                                         |

- **Class Summary**

  | Class                                         | Description                                                                                                              |
  |-----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
  | [DatabaseChangeEvent](DatabaseChangeEvent.md) | Once you have registered your interest into certain objects in the database, you get notified when these objects change. |

- **Enum Summary**

  | Enum                                                                                          | Description |
  |-----------------------------------------------------------------------------------------------|-------------|
  | [DatabaseChangeEvent.AdditionalEventType](DatabaseChangeEvent.AdditionalEventType.md)         |             |
  | [DatabaseChangeEvent.EventType](DatabaseChangeEvent.EventType.md)                             |             |
  | [QueryChangeDescription.QueryChangeEventType](QueryChangeDescription.QueryChangeEventType.md) |             |
  | [RowChangeDescription.RowOperation](RowChangeDescription.RowOperation.md)                     |             |
  | [TableChangeDescription.TableOperation](TableChangeDescription.TableOperation.md)             |             |

## Package oracle.jdbc.dcn Description

This package is an Oracle JDBC extension that provides interfaces to access the Database Change Notification feature of Oracle.

Since:
11*i*

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../datasource/package-summary.md)
- [Next Package](../pool/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
