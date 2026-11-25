Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](OLAPIIllegalStateException.md)
- [Next Class](UnsupportedOperationException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi

## Class OLAPIRuntimeException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - oracle.olapi.OLAPIRuntimeException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](HasLocalizedMessage.md)

  <!-- -->

  Direct Known Subclasses:
  [BatchedException](BatchedException.md), [BuildWarningsException](data/source/BuildWarningsException.md), [CommitException](transaction/CommitException.md), [CommitWarningsException](transaction/CommitWarningsException.md), [CursorLockException](data/source/CursorLockException.md), [DataProviderMismatchException](data/source/DataProviderMismatchException.md), [DeploymentException](metadata/deployment/DeploymentException.md), [DuplicateMetadataIDException](metadata/DuplicateMetadataIDException.md), [ExpressServerException](../express/ExpressServerException.md), [IncorrectDataValueException](data/source/IncorrectDataValueException.md), [IncrementalChangeException](transaction/IncrementalChangeException.md), [InvalidMetadataException](metadata/InvalidMetadataException.md), [MetadataFactoryException](metadata/MetadataFactoryException.md), [MetadataModificationException](metadata/MetadataModificationException.md), [MetadataRenameNotSupportedException](metadata/MetadataRenameNotSupportedException.md), [MetadataUpdateNotSupportedException](metadata/MetadataUpdateNotSupportedException.md), [NotPreparedException](transaction/NotPreparedException.md), [ServerVersionException](data/source/ServerVersionException.md), [SyntaxException](syntax/SyntaxException.md), [TaskInterruptedException](../express/TaskInterruptedException.md), [TransactionalObjectInvalidException](transaction/TransactionalObjectInvalidException.md), [TransactionTypeUnavailableException](transaction/TransactionTypeUnavailableException.md), [UnexpectedException](../express/UnexpectedException.md), [UnmatchedInputsException](data/source/UnmatchedInputsException.md), [UnsupportedOperationException](UnsupportedOperationException.md), [WriteLockException](transaction/WriteLockException.md)

  ------------------------------------------------------------------------



      public abstract class OLAPIRuntimeException
      extends java.lang.RuntimeException
      implements HasLocalizedMessage

  A common superclass for all Oracle OLAP Java API runtime exceptions.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                         |
    |----------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`   | `getLocalizedMessage``()`<br>Gets a message in the language specified by the default `java.util.Locale`.                       |
    | `java.lang.String`   | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a message in the language specified by the `java.util.Locale` object. |
    | `java.lang.String[]` | `getParameters``()`                                                                                                            |
    | `java.lang.String`   | `toString``()`<br>Gets the message for this `OLAPIRuntimeException`.                                                           |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage(java.util.Locale locale)

      Gets a message in the language specified by the `java.util.Locale` object.
      Specified by:
      [`getLocalizedMessage`](HasLocalizedMessage.md) in interface [`HasLocalizedMessage`](HasLocalizedMessage.md)

      Parameters:
      `locale` - The `Locale` object that specifies the language for the message.

      Returns:
      A `String` that has the message in the specified language.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage()

      Gets a message in the language specified by the default `java.util.Locale`.
      Overrides:
      `getLocalizedMessage` in class `java.lang.Throwable`

      Returns:
      A `String` that has the message in the language of the default `Locale`.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Gets the message for this `OLAPIRuntimeException`.
      Overrides:
      `toString` in class `java.lang.Throwable`

      Returns:
      A `String` that has the message for this `OLAPIRuntimeException`.

    <!-- -->

    - #### getParameters

          public java.lang.String[] getParameters()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](OLAPIIllegalStateException.md)
- [Next Class](UnsupportedOperationException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
