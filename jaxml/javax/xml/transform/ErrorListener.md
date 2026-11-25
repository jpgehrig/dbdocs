Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](OutputKeys.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.transform**

## **Interface ErrorListener**

- **All Known Implementing Classes:**
  **[XSLProcess](../../../oracle/xml/pipeline/processes/XSLProcess.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ErrorListener

  **To provide customized error handling, implement this interface and use the setErrorListener method to register an instance of the implmentation with the Transformer. The Transformer then reports all errors and warnings through this interface.**

  **If an application does *not* register an ErrorListener, errors are reported to System.err.**

  **For transformation errors, a Transformer must use this interface instead of throwing an exception: it is up to the application to decide whether to throw an exception for different types of errors and warnings. Note however that the Transformer is not required to continue with the transformation after a call to fatalError.**

  **Transformers may use this mechanism to report XML parsing errors as well as transformation errors.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                            |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `error``(`[`TransformerException`](TransformerException.md)` exception)`<br>Receive notification of a recoverable error.          |
    | `void`            | `fatalError``(`[`TransformerException`](TransformerException.md)` exception)`<br>Receive notification of a non-recoverable error. |
    | `void`            | `warning``(`[`TransformerException`](TransformerException.md)` exception)`<br>Receive notification of a warning.                  |

<!-- -->

- - ### Method Detail

    - #### warning

          void warning(TransformerException exception)
                throws TransformerException

      Receive notification of a warning.
      Transformers can use this method to report conditions that are not errors or fatal errors. The default behaviour is to take no action.

      After invoking this method, the Transformer must continue with the transformation. It should still be possible for the application to process the document through to the end.

      Parameters:
      `exception` - The warning information encapsulated in a transformer exception.

      Throws:
      [`TransformerException`](TransformerException.md) - if the application chooses to discontinue the transformation.

      See Also:
      [`TransformerException`](TransformerException.md)

    <!-- -->

    - #### error

          void error(TransformerException exception)
              throws TransformerException

      Receive notification of a recoverable error.
      The transformer must continue to try and provide normal transformation after invoking this method. It should still be possible for the application to process the document through to the end if no other errors are encountered.

      Parameters:
      `exception` - The error information encapsulated in a transformer exception.

      Throws:
      [`TransformerException`](TransformerException.md) - if the application chooses to discontinue the transformation.

      See Also:
      [`TransformerException`](TransformerException.md)

    <!-- -->

    - #### fatalError

          void fatalError(TransformerException exception)
                   throws TransformerException

      Receive notification of a non-recoverable error.
      The transformer must continue to try and provide normal transformation after invoking this method. It should still be possible for the application to process the document through to the end if no other errors are encountered, but there is no guarantee that the output will be useable.

      Parameters:
      `exception` - The error information encapsulated in a transformer exception.

      Throws:
      [`TransformerException`](TransformerException.md) - if the application chooses to discontinue the transformation.

      See Also:
      [`TransformerException`](TransformerException.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](OutputKeys.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
