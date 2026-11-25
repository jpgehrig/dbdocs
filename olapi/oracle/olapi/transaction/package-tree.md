Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev](../syntax/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.olapi.transaction

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.olapi.[OLAPIException](../OLAPIException.md) (implements oracle.olapi.[HasLocalizedMessage](../HasLocalizedMessage.md))
        - oracle.olapi.transaction.[NotCommittableException](NotCommittableException.md)
      - java.lang.RuntimeException
        - java.lang.IllegalStateException
          - oracle.olapi.[OLAPIIllegalStateException](../OLAPIIllegalStateException.md) (implements oracle.olapi.[HasLocalizedMessage](../HasLocalizedMessage.md))
            - oracle.olapi.transaction.[ActiveSubtransactionsException](ActiveSubtransactionsException.md)
            - oracle.olapi.transaction.[TransactionInactiveException](TransactionInactiveException.md)
        - oracle.olapi.[OLAPIRuntimeException](../OLAPIRuntimeException.md) (implements oracle.olapi.[HasLocalizedMessage](../HasLocalizedMessage.md))
          - oracle.olapi.transaction.[CommitException](CommitException.md)
          - oracle.olapi.transaction.[CommitWarningsException](CommitWarningsException.md)
          - oracle.olapi.transaction.[IncrementalChangeException](IncrementalChangeException.md)
          - oracle.olapi.transaction.[NotPreparedException](NotPreparedException.md)
          - oracle.olapi.transaction.[TransactionalObjectInvalidException](TransactionalObjectInvalidException.md)
          - oracle.olapi.transaction.[TransactionTypeUnavailableException](TransactionTypeUnavailableException.md)
          - oracle.olapi.transaction.[WriteLockException](WriteLockException.md)

## Interface Hierarchy

- oracle.olapi.transaction.[Transaction](Transaction.md)
- oracle.olapi.transaction.[TransactionProvider](TransactionProvider.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev](../syntax/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)
