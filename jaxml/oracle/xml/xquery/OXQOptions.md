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

- **[Prev Class](OXQJavaResolverFactory.md)**
- **[Next Class](OXQPreparedExpression.md)**

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

## **Interface OXQOptions**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQOptions

  **Exposes the contents of zero or more [XQuery option declarations](http://www.w3.org/TR/xquery/#id_option_declaration).**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQFunctionMetaData.getOptions()`](OXQFunctionMetaData.md), [`OXQConnection.createOptions()`](OXQConnection.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                  | Field and Description                                                                                                                                                     |
    |------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static javax.xml.namespace.QName` | `OPTION_FUNCTION_DETERMINISTIC`<br>The name of the option declaration that specifies whether an external function is deterministic or not.                                |
    | `static javax.xml.namespace.QName` | `OPTION_FUNCTION_INLINE`<br>The name of the option declaration that specifies whether a [user defined function](https://www.w3.org/TR/xquery-30/#dt_udf) will be inlined. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                               |
    |-------------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `void`                        | `declareOption``(javax.xml.namespace.QName name, java.lang.String value)`<br>Declares an XQuery option.              |
    | `javax.xml.namespace.QName[]` | `getOptionNames``()`<br>Returns the names of the option declarations.                                                |
    | `java.lang.String`            | `getOptionValue``(javax.xml.namespace.QName optionName)`<br>Returns the content of the specified option declaration. |

<!-- -->

- - ### Field Detail

    - #### OPTION_FUNCTION_DETERMINISTIC

          static final javax.xml.namespace.QName OPTION_FUNCTION_DETERMINISTIC

      The name of the option declaration that specifies whether an external function is deterministic or not.
      Supported values are:
      - "true" - determenistic,
      - "false" - non-determenistic (default)

    <!-- -->

    - #### OPTION_FUNCTION_INLINE

          static final javax.xml.namespace.QName OPTION_FUNCTION_INLINE

      The name of the option declaration that specifies whether a [user defined function](https://www.w3.org/TR/xquery-30/#dt_udf) will be inlined.
      - "true" - inline the function if possible (default)
      - "false" - do not inline the function

      When used in a query or library module, the value of this option declaration only applies to the function declaration that immediately follows it (if any)

  <!-- -->

  - ### Method Detail

    - #### declareOption

          void declareOption(javax.xml.namespace.QName name,
                             java.lang.String value)
                      throws XQException

      Declares an XQuery option.
      Parameters:
      `name` - option name

      `value` - option value (if `null` then an existing option is undeclared)

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if option name is `null`

    <!-- -->

    - #### getOptionNames

          javax.xml.namespace.QName[] getOptionNames()

      Returns the names of the option declarations.
      Returns:
      the names of the option declarations

    <!-- -->

    - #### getOptionValue

          java.lang.String getOptionValue(javax.xml.namespace.QName optionName)

      Returns the content of the specified option declaration.
      Parameters:
      `optionName` - the name of the option declaration

      Returns:
      the content of the option declaration

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

- **[Prev Class](OXQJavaResolverFactory.md)**
- **[Next Class](OXQPreparedExpression.md)**

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
