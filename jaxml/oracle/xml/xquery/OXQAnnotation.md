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
- **[Next Class](OXQCloseable.md)**

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

## **Interface OXQAnnotation**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQAnnotation

  **Models an [XQuery function annotation](http://www.w3.org/TR/xquery-30/#id_annotations).**
  **See Also:**
  **[`OXQFunctionMetaData.getAnnotations()`](OXQFunctionMetaData.md), [`OXQConnection.createAnnotation(QName, XQSequence)`](OXQConnection.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                       | Method and Description                                 |
    |---------------------------------------------------------|--------------------------------------------------------|
    | `javax.xml.namespace.QName`                             | `getName``()`<br>Returns the name of the annotation.   |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) | `getValue``()`<br>Returns the value of the annotation. |

<!-- -->

- - ### Method Detail

    - #### getName

          javax.xml.namespace.QName getName()

      Returns the name of the annotation.
      Returns:
      the name of the annotation

    <!-- -->

    - #### getValue

          XQSequence getValue()

      Returns the value of the annotation. If the annotation has no value, the the empty sequence will be returned.
      Returns:
      the value of the annotation

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
- **[Next Class](OXQCloseable.md)**

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
