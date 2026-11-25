Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package oracle.express

  - ## Class [oracle.express.ErrorDescription](oracle/express/ErrorDescription.md) extends java.lang.Object implements Serializable

    - ## Serialized Fields

      - #### \_errorDescriptionStruct

            oracle.express.idl.ExpressModule.ErrorDescriptionStruct _errorDescriptionStruct

         

  - ## Class [oracle.express.ErrorStack](oracle/express/ErrorStack.md) extends java.lang.Object implements Serializable

    - ## Serialized Fields

      - #### \_e

            oracle.express.idl.ExpressModule.ExpressException _e

         

      - #### \_errorDescriptions

            java.util.List<E> _errorDescriptions

         

  - ## Class [oracle.express.ExpressServerException](oracle/express/ExpressServerException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### \_errorStack

            ErrorStack _errorStack

         

      - #### \_sqlExcpt

            java.sql.SQLException _sqlExcpt

  - ## Class [oracle.express.ObjectClosedException](oracle/express/ObjectClosedException.md) extends [OLAPIIllegalStateException](oracle/olapi/OLAPIIllegalStateException.md) implements Serializable

  - ## Class [oracle.express.TaskInterruptedException](oracle/express/TaskInterruptedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.express.UnexpectedException](oracle/express/UnexpectedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.express.olapi.data.full

  - ## Class [oracle.express.olapi.data.full.UnknownServerVersionException](oracle/express/olapi/data/full/UnknownServerVersionException.md) extends java.lang.RuntimeException implements Serializable

- ## Package oracle.express.spl

  - ## Class [oracle.express.spl.NAValueException](oracle/express/spl/NAValueException.md) extends java.lang.Exception implements Serializable

- ## Package oracle.olapi

  - ## Class [oracle.olapi.ArraySet](oracle/olapi/ArraySet.md) extends java.util.ArrayList implements Serializable

  - ## Class [oracle.olapi.BatchedException](oracle/olapi/BatchedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_Errors

            java.util.List<E> m_Errors

        INSTANCE MEMBERS

      - #### m_Warnings

            java.util.List<E> m_Warnings

      - #### m_IsWarning

            boolean m_IsWarning

  - ## Class [oracle.olapi.OLAPIException](oracle/olapi/OLAPIException.md) extends java.lang.Exception implements Serializable

  - ## Class [oracle.olapi.OLAPIIllegalStateException](oracle/olapi/OLAPIIllegalStateException.md) extends java.lang.IllegalStateException implements Serializable

  - ## Class [oracle.olapi.OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) extends java.lang.RuntimeException implements Serializable

  - ## Class [oracle.olapi.UnsupportedOperationException](oracle/olapi/UnsupportedOperationException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.olapi.data.cursor

  - ## Class [oracle.olapi.data.cursor.CursorManagerUpdateEvent](oracle/olapi/data/cursor/CursorManagerUpdateEvent.md) extends java.util.EventObject implements Serializable

    - ## Serialized Fields

      - #### \_id

            int _id

         

  - ## Class [oracle.olapi.data.cursor.IncorrectDataTypeException](oracle/olapi/data/cursor/IncorrectDataTypeException.md) extends java.lang.RuntimeException implements Serializable

  - ## Class [oracle.olapi.data.cursor.NoDataAvailableException](oracle/olapi/data/cursor/NoDataAvailableException.md) extends java.lang.RuntimeException implements Serializable

  - ## Class [oracle.olapi.data.cursor.NotSpecifiedException](oracle/olapi/data/cursor/NotSpecifiedException.md) extends java.lang.RuntimeException implements Serializable

  - ## Class [oracle.olapi.data.cursor.PositionOutOfBoundsException](oracle/olapi/data/cursor/PositionOutOfBoundsException.md) extends java.lang.IndexOutOfBoundsException implements Serializable

  - ## Class [oracle.olapi.data.cursor.SpecificationUpdateNeededException](oracle/olapi/data/cursor/SpecificationUpdateNeededException.md) extends java.lang.RuntimeException implements Serializable

  - ## Class [oracle.olapi.data.cursor.StructureUpdatedException](oracle/olapi/data/cursor/StructureUpdatedException.md) extends java.lang.RuntimeException implements Serializable

- ## Package oracle.olapi.data.source

  - ## Class [oracle.olapi.data.source.BuildWarningsException](oracle/olapi/data/source/BuildWarningsException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_BaseException

            java.lang.Exception m_BaseException

  - ## Class [oracle.olapi.data.source.CursorLockException](oracle/olapi/data/source/CursorLockException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.data.source.DataProviderMismatchException](oracle/olapi/data/source/DataProviderMismatchException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.data.source.IncorrectDataValueException](oracle/olapi/data/source/IncorrectDataValueException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.data.source.ServerVersionException](oracle/olapi/data/source/ServerVersionException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.data.source.UnmatchedInputsException](oracle/olapi/data/source/UnmatchedInputsException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.olapi.metadata

  - ## Class [oracle.olapi.metadata.DuplicateMetadataIDException](oracle/olapi/metadata/DuplicateMetadataIDException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_ID

            java.lang.String m_ID

  - ## Class [oracle.olapi.metadata.InvalidMetadataException](oracle/olapi/metadata/InvalidMetadataException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.metadata.MetadataFactoryException](oracle/olapi/metadata/MetadataFactoryException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.metadata.MetadataModificationException](oracle/olapi/metadata/MetadataModificationException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.metadata.MetadataRenameNotSupportedException](oracle/olapi/metadata/MetadataRenameNotSupportedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.metadata.MetadataUpdateNotSupportedException](oracle/olapi/metadata/MetadataUpdateNotSupportedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.olapi.metadata.deployment

  - ## Class [oracle.olapi.metadata.deployment.DeploymentException](oracle/olapi/metadata/deployment/DeploymentException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.olapi.metadata.mdm

  - ## Class [oracle.olapi.metadata.mdm.MdmInvalidValueException](oracle/olapi/metadata/mdm/MdmInvalidValueException.md) extends java.lang.RuntimeException implements Serializable

- ## Package oracle.olapi.session

  - ## Class oracle.olapi.session.BranchActiveException extends java.lang.Object implements Serializable

- ## Package oracle.olapi.syntax

  - ## Class [oracle.olapi.syntax.SyntaxException](oracle/olapi/syntax/SyntaxException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

- ## Package oracle.olapi.transaction

  - ## Class [oracle.olapi.transaction.ActiveSubtransactionsException](oracle/olapi/transaction/ActiveSubtransactionsException.md) extends [OLAPIIllegalStateException](oracle/olapi/OLAPIIllegalStateException.md) implements Serializable

    - ## Serialized Fields

      - #### \_transactions

            java.util.List<E> _transactions

         

  - ## Class [oracle.olapi.transaction.CommitException](oracle/olapi/transaction/CommitException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_BaseException

            java.lang.Exception m_BaseException

  - ## Class [oracle.olapi.transaction.CommitWarningsException](oracle/olapi/transaction/CommitWarningsException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_BaseException

            java.lang.Exception m_BaseException

  - ## Class [oracle.olapi.transaction.IncrementalChangeException](oracle/olapi/transaction/IncrementalChangeException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### m_BaseException

            java.lang.Exception m_BaseException

  - ## Class [oracle.olapi.transaction.NotCommittableException](oracle/olapi/transaction/NotCommittableException.md) extends [OLAPIException](oracle/olapi/OLAPIException.md) implements Serializable

  - ## Class [oracle.olapi.transaction.NotPreparedException](oracle/olapi/transaction/NotPreparedException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### \_transaction

            Transaction _transaction

         

  - ## Class [oracle.olapi.transaction.TransactionalObjectInvalidException](oracle/olapi/transaction/TransactionalObjectInvalidException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.transaction.TransactionInactiveException](oracle/olapi/transaction/TransactionInactiveException.md) extends [OLAPIIllegalStateException](oracle/olapi/OLAPIIllegalStateException.md) implements Serializable

    - ## Serialized Fields

      - #### \_transaction

            Transaction _transaction

         

  - ## Class [oracle.olapi.transaction.TransactionTypeUnavailableException](oracle/olapi/transaction/TransactionTypeUnavailableException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

  - ## Class [oracle.olapi.transaction.WriteLockException](oracle/olapi/transaction/WriteLockException.md) extends [OLAPIRuntimeException](oracle/olapi/OLAPIRuntimeException.md) implements Serializable

    - ## Serialized Fields

      - #### \_state

            MetadataState _state

         

      - #### \_transaction

            Transaction _transaction

         

      - #### \_activeTransaction

            Transaction _activeTransaction

         

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)
