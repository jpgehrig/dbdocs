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

- **[Prev Class](OXQEntityResolverFactory.md)**
- **[Next Class](OXQExpression.md)**

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

## **Class OXQEntityResolverRequestOptions**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQEntityResolverRequestOptions**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class OXQEntityResolverRequestOptions
      extends java.lang.Object

  **Additional options for use when [`resolving an entity`](OXQEntityResolver.md).**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQEntityResolver`](OXQEntityResolver.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                             |
    |-------------------|---------------------------------------------------------------------------------------------------|
    | `static int`      | `NO_TIMEOUT`<br>The timeout value that will be returned by `getTimeout()` if there is no timeout. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                |
    |-------------------|---------------------------------------|
    | `abstract int`    | `getTimeout``()`<br>Gets the timeout. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NO_TIMEOUT

          public static final int NO_TIMEOUT

      The timeout value that will be returned by `getTimeout()` if there is no timeout.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getTimeout

          public abstract int getTimeout()

      Gets the timeout. When possible, the entity resolver should fail when the time taken exceeds the timeout value.
      Returns:
      the timeout value in milliseconds. If the value is equal to `NO_TIMEOUT`, there is no timeout

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

- **[Prev Class](OXQEntityResolverFactory.md)**
- **[Next Class](OXQExpression.md)**

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
