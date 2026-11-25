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

- **[Prev Class](OXQFunctionEvaluator.md)**
- **[Next Class](OXQHttpResolverFactory.md)**

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

## **Interface OXQFunctionMetaData**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQFunctionMetaData

  **Function metadata used when [`resolving`](OXQEntityResolver.md) an external function. This is made available to the [`entity resolver`](OXQEntityResolver.md) as a locator extension (see [`OXQEntityLocator.getExtension()`](OXQEntityLocator.md)) when the entity kind is [`EXTERNAL_FUNCTION`](OXQEntityKind.md). [`External function`](OXQFunctionEvaluator.md) implementations may also access the function metadata using method [`OXQFunctionContext.getMetaData()`](OXQFunctionContext.md).**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQEntityLocator.getExtension()`](OXQEntityLocator.md), [`OXQEntityKind.EXTERNAL_FUNCTION`](OXQEntityKind.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                   | Method and Description                                                                        |
    |---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
    | [`OXQAnnotation`](OXQAnnotation.md)`[]`                             | `getAnnotations``()`<br>The XQuery annotations of the XQuery function declaration.            |
    | `javax.xml.namespace.QName`                                         | `getName``()`<br>Gets the function name.                                                      |
    | [`OXQOptions`](OXQOptions.md)                                       | `getOptions``()`<br>The XQuery option declarations preceding the XQuery function declaration. |
    | [`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)`[]` | `getParameterTypes``()`<br>Gets the types of the function parameters.                         |
    | [`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)     | `getReturnType``()`<br>Gets the return type of the function.                                  |

<!-- -->

- - ### Method Detail

    - #### getName

          javax.xml.namespace.QName getName()

      Gets the function name.
      Returns:
      the name of the function

    <!-- -->

    - #### getParameterTypes

          XQSequenceType[] getParameterTypes()

      Gets the types of the function parameters.
      Returns:
      the parameter types

    <!-- -->

    - #### getReturnType

          XQSequenceType getReturnType()

      Gets the return type of the function.
      Returns:
      the function return type

    <!-- -->

    - #### getOptions

          OXQOptions getOptions()

      The XQuery option declarations preceding the XQuery function declaration. This includes any user-defined option declarations.
      Returns:
      the option declarations

    <!-- -->

    - #### getAnnotations

          OXQAnnotation[] getAnnotations()

      The XQuery annotations of the XQuery function declaration. This includes any user-defined annotations.
      Returns:
      the annotations

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

- **[Prev Class](OXQFunctionEvaluator.md)**
- **[Next Class](OXQHttpResolverFactory.md)**

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
