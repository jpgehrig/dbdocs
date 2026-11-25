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

- **[Prev Class](OXQSerializationParameters.md)**
- **[Next Class](OXQStackTraceVariable.md)**

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

**oracle.xml.xquery**

## **Interface OXQStackTraceElement**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQStackTraceElement

  **Provides contextual information about query processing to an XQuery debugger client.**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQDebugListener`](OXQDebugListener.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                            |
    |---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                                        | `getModuleLocationURI``()`<br>Gets the location of the current module, or `null` if not available.                                                |
    | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)         | `getStaticContext``()`<br>Gets a read-only view of the static context at this execution point, or `null` if not available.                        |
    | [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) | `getXQView``()`<br>Returns the [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) instance corresponding to this instance. |

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQStackTraceElement getXQView()

      Returns the [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) instance corresponding to this instance.
      Returns:
      the [`XQStackTraceElement`](../../../javax/xml/xquery/XQStackTraceElement.md) instance

    <!-- -->

    - #### getModuleLocationURI

          java.lang.String getModuleLocationURI()

      Gets the location of the current module, or `null` if not available.
      Returns:
      the location or `null` if not available

    <!-- -->

    - #### getStaticContext

          XQStaticContext getStaticContext()

      Gets a read-only view of the static context at this execution point, or `null` if not available.
      Returns:
      the static context or `null` if not available

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

- **[Prev Class](OXQSerializationParameters.md)**
- **[Next Class](OXQStackTraceVariable.md)**

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
