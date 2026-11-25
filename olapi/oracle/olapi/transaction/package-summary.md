Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../syntax/package-summary.md)
- [Next Package](metadataStateManager/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.olapi.transaction

Contains interfaces that define classes that are involved in transactions between Oracle OLAP and an OLAP client application and `Exception` classes that an application might encounter.

See: Description

- **Interface Summary**

  | Interface                                     | Description                                                                        |
  |-----------------------------------------------|------------------------------------------------------------------------------------|
  | [Transaction](Transaction.md)                 | An interface that represents an OLAP transaction with an Oracle Database instance. |
  | [TransactionProvider](TransactionProvider.md) | An interface that defines an OLAP transaction provider.                            |

- **Exception Summary**

  | Exception                                                                     | Description                                                                                                                                                                                                                     |
  |-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ActiveSubtransactionsException](ActiveSubtransactionsException.md)           | Indicates that the current `Transaction` has child `Transaction` objects that the application must commit or roll back before committing or rolling back the current `Transaction`.                                             |
  | [CommitException](CommitException.md)                                         | Indicates that the attempt to commit the `Transaction` failed.                                                                                                                                                                  |
  | [CommitWarningsException](CommitWarningsException.md)                         | Indicates that the attempt to commit the `Transaction` succeeded, but that there are warning messages.                                                                                                                          |
  | [IncrementalChangeException](IncrementalChangeException.md)                   | Indicates that a change that an application has made since the last interaction with the Oracle OLAP server is invalid.                                                                                                         |
  | [NotCommittableException](NotCommittableException.md)                         | Indicates that the `TransactionProvider` has determined that the query defined in the current `Transaction` is invalid and the `TransactionProvider` is therefore preventing the application from committing the `Transaction`. |
  | [NotPreparedException](NotPreparedException.md)                               | Indicates that the `TransactionProvider` has not prepared the current `Transaction` and therefore it cannot commit the `Transaction`.                                                                                           |
  | [TransactionalObjectInvalidException](TransactionalObjectInvalidException.md) | Indicates that the `TransactionalObject` is not valid in the current `Transaction`.                                                                                                                                             |
  | [TransactionInactiveException](TransactionInactiveException.md)               | Indicates that the current `Transaction` has already been committed or rolled back by the application and is therefore no longer active.                                                                                        |
  | [TransactionTypeUnavailableException](TransactionTypeUnavailableException.md) | Indicates that the type of the `Transaction` requested is not available.                                                                                                                                                        |
  | [WriteLockException](WriteLockException.md)                                   | Indicates that the `TransactionProvider` cannot create a write `Transaction` at this time.                                                                                                                                      |

## Package oracle.olapi.transaction Description

Contains interfaces that define classes that are involved in transactions between Oracle OLAP and an OLAP client application and `Exception` classes that an application might encounter.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../syntax/package-summary.md)
- [Next Package](metadataStateManager/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)
