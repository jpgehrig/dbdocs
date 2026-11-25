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

- **[Prev Class](OXQStackTraceVariable.md)**
- **[Next Class](OXQView.md)**

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

## **Interface OXQStaticContext**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQStaticContext

  **Extensions to [`javax.xml.xquery.XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md).**
  **Use method [`OXQView.getStaticContext(XQStaticContext)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQStaticContext ctx = con.getStaticContext();
       OXQStaticContext octx = OXQView.getStaticContext(ctx);
       ...


  **Since:**
  **12.1**

  **See Also:**
  **[`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                                                                                                                                                |
    |-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                            | `declareFunction``(javax.xml.namespace.QName name, `[`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)`[] parameterTypes, `[`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)` returnType, `[`OXQOptions`](OXQOptions.md)` options)`<br>Declares an external function.                                                      |
    | `void`                                                            | `declareFunction``(javax.xml.namespace.QName name, `[`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)`[] parameterTypes, `[`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)` returnType, `[`OXQOptions`](OXQOptions.md)` options, `[`OXQAnnotation`](OXQAnnotation.md)`[] annotations)`<br>Declares an external function. |
    | `void`                                                            | `declareImport``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind, java.lang.String namespace, java.lang.String... locations)`<br>Declares that a schema or module should be imported.                                                                                                                                                                |
    | `void`                                                            | `declareVariable``(javax.xml.namespace.QName name, `[`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)` type)`<br>Declares an external variable.                                                                                                                                                                                         |
    | `int`                                                             | `getBindingTypeCheckMode``()`<br>Gets the type checking mode for external variable bindings.                                                                                                                                                                                                                                                          |
    | [`OXQDecimalFormat`](OXQDecimalFormat.md)                         | `getDecimalFormat``(javax.xml.namespace.QName name)`<br>Gets an `OXQDecimalFormat` instance representing the the values for all decimal format properties.                                                                                                                                                                                            |
    | [`OXQEntityResolver`](OXQEntityResolver.md)                       | `getEntityResolver``()`<br>Gets the [`OXQEntityResolver`](OXQEntityResolver.md) instance to be used during query processing.                                                                                                                                                                                                                          |
    | [`OXQFunctionMetaData`](OXQFunctionMetaData.md)`[]`               | `getFunctions``()`<br>Gets the definitions of all external functions declared in this context.                                                                                                                                                                                                                                                        |
    | `java.lang.String[]`                                              | `getImportLocations``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind, java.lang.String namespace)`<br>Gets the locations of a schema or module import.                                                                                                                                                                                              |
    | `java.lang.String[]`                                              | `getImportNamespaces``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind)`<br>Gets the target namespaces of all schema or module imports currently declared.                                                                                                                                                                                           |
    | `java.lang.String`                                                | `getModuleURI``()`<br>Gets the module URI, if set in the static context, else the empty string.                                                                                                                                                                                                                                                       |
    | `int`                                                             | `getProcessingMode``()`<br>Gets the processing mode.                                                                                                                                                                                                                                                                                                  |
    | [`OXQSerializationParameters`](OXQSerializationParameters.md)     | `getSerializationParameters``()`<br>Gets an `OXQSerializationParameters` instance representing the the values for all serialization parameters.                                                                                                                                                                                                       |
    | `javax.xml.namespace.QName[]`                                     | `getVariableNames``()`<br>Gets the names of all external variables declared in this context.                                                                                                                                                                                                                                                          |
    | [`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md)   | `getVariableType``(javax.xml.namespace.QName name)`<br>Gets the type of an external variable declared in this context.                                                                                                                                                                                                                                |
    | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) | `getXQView``()`<br>Returns the [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) instance corresponding to this instance.                                                                                                                                                                                                             |
    | `void`                                                            | `setBindingTypeCheckMode``(int mode)`<br>Sets the type checking mode for external variable bindings.                                                                                                                                                                                                                                                  |
    | `void`                                                            | `setDecimalFormat``(javax.xml.namespace.QName name, `[`OXQDecimalFormat`](OXQDecimalFormat.md)` format)`<br>Adds a decimal format to this static context.                                                                                                                                                                                             |
    | `void`                                                            | `setEntityResolver``(`[`OXQEntityResolver`](OXQEntityResolver.md)` resolver)`<br>Sets an [`OXQEntityResolver`](OXQEntityResolver.md) instance to be used during query processing.                                                                                                                                                                     |
    | `void`                                                            | `setModuleURI``(java.lang.String moduleUri)`<br>Sets the module URI in the static context.                                                                                                                                                                                                                                                            |
    | `void`                                                            | `setProcessingMode``(int mode)`<br>Sets the processing mode.                                                                                                                                                                                                                                                                                          |
    | `void`                                                            | `setSerializationParameters``(`[`OXQSerializationParameters`](OXQSerializationParameters.md)` params)`<br>Sets the serialization parameters for this static context.                                                                                                                                                                                  |
    | `void`                                                            | `undeclareFunction``(javax.xml.namespace.QName name, int parameterCount)`<br>Undeclares a previously declared external function.                                                                                                                                                                                                                      |
    | `void`                                                            | `undeclareVariable``(javax.xml.namespace.QName name)`<br>Undeclares a previously declared external variable.                                                                                                                                                                                                                                          |

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQStaticContext getXQView()

      Returns the [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md) instance corresponding to this instance.
      Returns:
      the static context

    <!-- -->

    - #### getBindingTypeCheckMode

          int getBindingTypeCheckMode()

      Gets the type checking mode for external variable bindings.
      Returns:
      the type checking mode, either [`OXQConstants.BINDING_TYPE_CHECK_MODE_PRIME`](OXQConstants.md) or [`OXQConstants.BINDING_TYPE_CHECK_MODE_FULL`](OXQConstants.md)

    <!-- -->

    - #### setBindingTypeCheckMode

          void setBindingTypeCheckMode(int mode)
                                throws XQException

      Sets the type checking mode for external variable bindings. When set to [`OXQConstants.BINDING_TYPE_CHECK_MODE_PRIME`](OXQConstants.md), the XQuery processor assumes that the number of items bound to an external variable matches the type quantifier specified in the variable declaration and does not attempt to verify this assumption. By default, the processor will verify the type quantifier which can block streaming evaluation in some cases.

      For example, consider the following query:
      `  declare variable $arg as element();`
      `  $arg[1]`

      Consider what happens if we bind `(, <b/>)` to this variable (a sequence of two elements). The binding mode is `BINDING_TYPE_CHECK_MODE_FULL`, this will result in a runtime error because "`as element()`" indicates there should be exactly 1 element bound to the variable. On the other hand, the binding mode is `BINDING_TYPE_CHECK_MODE_PRIME`, the XQuery processor will only ensure that the binding is an element but will not attempt to verify that there is exactly one element. The default value is [`OXQConstants.BINDING_TYPE_CHECK_MODE_FULL`](OXQConstants.md).

      Note, the relaxed type checking behavior used in mode `BINDING_TYPE_CHECK_MODE_PRIME` does not conform to the XQuery 1.0 standard.

      Parameters:
      `mode` - the type checking mode. Must be either [`OXQConstants.BINDING_TYPE_CHECK_MODE_PRIME`](OXQConstants.md) or [`OXQConstants.BINDING_TYPE_CHECK_MODE_FULL`](OXQConstants.md)

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - the specified mode is different from [`OXQConstants.BINDING_TYPE_CHECK_MODE_PRIME`](OXQConstants.md) or [`OXQConstants.BINDING_TYPE_CHECK_MODE_FULL`](OXQConstants.md)

      See Also:
      `getBindingTypeCheckMode()`

    <!-- -->

    - #### getProcessingMode

          int getProcessingMode()

      Gets the processing mode. In some cases, it may be useful to validate and analyze a query without any need to execute it. In such cases, the *processing mode* can be set to [`OXQConstants.PROCESSING_STATIC_ANALYSIS_ONLY`](OXQConstants.md) to disable query optimization and plan generation. When in this mode, queries may not be executed. When the processing mode is [`OXQConstants.PROCESSING_FULL`](OXQConstants.md), queries may be prepared and executed. The default value is [`OXQConstants.PROCESSING_FULL`](OXQConstants.md).
      Returns:
      the processing mode. Must be either [`OXQConstants.PROCESSING_STATIC_ANALYSIS_ONLY`](OXQConstants.md) or [`OXQConstants.PROCESSING_FULL`](OXQConstants.md)

    <!-- -->

    - #### setProcessingMode

          void setProcessingMode(int mode)
                          throws XQException

      Sets the processing mode.
      Parameters:
      `mode` - the processing mode. Must be either [`OXQConstants.PROCESSING_STATIC_ANALYSIS_ONLY`](OXQConstants.md) or [`OXQConstants.PROCESSING_FULL`](OXQConstants.md)

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - the specified mode is different from `OXQConstants.PROCESSING_STATIC_ANALYSIS_ONLY` or `OXQConstants.PROCESSING_FULL`

      See Also:
      `getProcessingMode()`

    <!-- -->

    - #### getModuleURI

          java.lang.String getModuleURI()

      Gets the module URI, if set in the static context, else the empty string.
      Returns:
      the module URI, if set, else the empty string. Cannot be `null`

      See Also:
      `setModuleURI(String)`

    <!-- -->

    - #### setModuleURI

          void setModuleURI(java.lang.String moduleUri)
                     throws XQException

      Sets the module URI in the static context. If `moduleUri` is the empty string then the module URI setting will be cleared. The module URI will be used in error messages related to the main module. For example, by default a type error message in the main module might look something like the following:
      `line 10, column 11: XPTY0004: Invalid static type ...`

      If the module URI is set to `"file:/myquery.xq"`, the error message would instead look something like:
      `file:/myquery.xq, line 10, column 11: XPTY0004: Invalid static type ...`

      Parameters:
      `moduleUri` - the new moduleUri, or the empty string to make it undefined. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a `null` module uri is specified, or given uri is not absolute

    <!-- -->

    - #### getEntityResolver

          OXQEntityResolver getEntityResolver()

      Gets the [`OXQEntityResolver`](OXQEntityResolver.md) instance to be used during query processing.
      Returns:
      the entity resolver instance

    <!-- -->

    - #### setEntityResolver

          void setEntityResolver(OXQEntityResolver resolver)

      Sets an [`OXQEntityResolver`](OXQEntityResolver.md) instance to be used during query processing.
      Parameters:
      `resolver` - the entity resolver to use

      See Also:
      [`OXQConnection.createEntityResolverFactory(Class)`](OXQConnection.md), [`OXQEntityResolverFactory`](OXQEntityResolverFactory.md)

    <!-- -->

    - #### declareImport

          void declareImport(OXQEntityKind entityKind,
                             java.lang.String namespace,
                             java.lang.String... locations)
                      throws XQException

      Declares that a schema or module should be imported.
      Parameters:
      `entityKind` - must be either [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      `namespace` - the target namespace of the schema or module

      `locations` - the location hints

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `namespace` is `null`, or if any element of `locations` is `null`, or if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      See Also:
      `getImportLocations(OXQEntityKind, String)`, `getImportNamespaces(OXQEntityKind)`, [XQuery Schema Import Feature](http://www.w3.org/TR/xquery/#dt_schema_import), [XQuery Module Import](http://www.w3.org/TR/xquery/#id_module_import)

    <!-- -->

    - #### getImportNamespaces

          java.lang.String[] getImportNamespaces(OXQEntityKind entityKind)
                                          throws XQException

      Gets the target namespaces of all schema or module imports currently declared.
      Parameters:
      `entityKind` - must be either [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      Returns:
      an array of the target namespaces. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      See Also:
      `declareImport(OXQEntityKind,String,String...)`, `getImportLocations(OXQEntityKind,String)`

    <!-- -->

    - #### getImportLocations

          java.lang.String[] getImportLocations(OXQEntityKind entityKind,
                                                java.lang.String namespace)
                                         throws XQException

      Gets the locations of a schema or module import.
      Parameters:
      `entityKind` - must be either [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      `namespace` - the target namespace of the schema to get the location hints for

      Returns:
      an array of the schema locations. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `namespace` is `null` or unknown or if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      See Also:
      `declareImport(OXQEntityKind,String,String...)`, `getImportNamespaces(OXQEntityKind)`

    <!-- -->

    - #### declareVariable

          void declareVariable(javax.xml.namespace.QName name,
                               XQSequenceType type)
                        throws XQException

      Declares an external variable.
      Parameters:
      `name` - variable name. Cannot be `null`

      `type` - variable type. If `null` is specified then defaults to `item()*`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if name is `null`

    <!-- -->

    - #### getVariableNames

          javax.xml.namespace.QName[] getVariableNames()

      Gets the names of all external variables declared in this context.
      Returns:
      an array of the variable names. Cannot be `null`

    <!-- -->

    - #### getVariableType

          XQSequenceType getVariableType(javax.xml.namespace.QName name)
                                  throws XQException

      Gets the type of an external variable declared in this context.
      Parameters:
      `name` - The name of the variable. Cannot be `null`

      Returns:
      type of the variable. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if variable name is `null` or unknown

    <!-- -->

    - #### undeclareVariable

          void undeclareVariable(javax.xml.namespace.QName name)
                          throws XQException

      Undeclares a previously declared external variable.
      Parameters:
      `name` - variable name. Cannot be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if name is `null`, or the variable is unknown

    <!-- -->

    - #### declareFunction

          void declareFunction(javax.xml.namespace.QName name,
                               XQSequenceType[] parameterTypes,
                               XQSequenceType returnType,
                               OXQOptions options)
                        throws XQException

      Declares an external function.
      Parameters:
      `name` - function name. Cannot be `null`

      `parameterTypes` - types of parameters. Cannot be `null`

      `returnType` - output type. If `null` is specified then defaults to `item()*`

      `options` - additional options. May be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if function name is `null` or any of parameter types is `null`

      See Also:
      [`OXQConnection.createOptions()`](OXQConnection.md)

    <!-- -->

    - #### declareFunction

          void declareFunction(javax.xml.namespace.QName name,
                               XQSequenceType[] parameterTypes,
                               XQSequenceType returnType,
                               OXQOptions options,
                               OXQAnnotation[] annotations)
                        throws XQException

      Declares an external function.
      Parameters:
      `name` - function name. Cannot be `null`

      `parameterTypes` - types of parameters. Cannot be `null`

      `returnType` - output type. If `null` is specified then defaults to `item()*`

      `options` - additional options. May be `null`

      `annotations` - function annotations. May be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if function name is `null` or any of parameter types is `null`

      See Also:
      [`OXQConnection.createOptions()`](OXQConnection.md), [`OXQConnection.createAnnotation(QName, javax.xml.xquery.XQSequence)`](OXQConnection.md), [`OXQFunctionMetaData`](OXQFunctionMetaData.md)

    <!-- -->

    - #### getFunctions

          OXQFunctionMetaData[] getFunctions()

      Gets the definitions of all external functions declared in this context.
      Returns:
      an array containing function definitions. Cannot be `null`

    <!-- -->

    - #### undeclareFunction

          void undeclareFunction(javax.xml.namespace.QName name,
                                 int parameterCount)
                          throws XQException

      Undeclares a previously declared external function.
      Parameters:
      `name` - function name. Cannot be `null`

      `parameterCount` - number of parameters

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `name` is `null`, or the function is unknown

    <!-- -->

    - #### getSerializationParameters

          OXQSerializationParameters getSerializationParameters()

      Gets an `OXQSerializationParameters` instance representing the the values for all serialization parameters. The returned instance is a copy so `setSerializationParameters(OXQSerializationParameters)` must be used to change the serialization parameters of this static context.
      Returns:
      the serialization parameters

    <!-- -->

    - #### setSerializationParameters

          void setSerializationParameters(OXQSerializationParameters params)
                                   throws XQException

      Sets the serialization parameters for this static context.
      Parameters:
      `params` - the serialization parameters. May not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `params` is `null`

    <!-- -->

    - #### getDecimalFormat

          OXQDecimalFormat getDecimalFormat(javax.xml.namespace.QName name)

      Gets an `OXQDecimalFormat` instance representing the the values for all decimal format properties. The returned instance is a copy so `setDecimalFormat(QName, OXQDecimalFormat)` must be used to change the serialization parameters of this static context.
      Parameters:
      `name` - the name that maps to a decimal format, use null to get the unnamed decimal format.

      Returns:
      the decimal format

    <!-- -->

    - #### setDecimalFormat

          void setDecimalFormat(javax.xml.namespace.QName name,
                                OXQDecimalFormat format)
                         throws XQException

      Adds a decimal format to this static context.
      Parameters:
      `name` - decimal format name.

      `format` - the decimal format. May not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `format` is `null`

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

- **[Prev Class](OXQStackTraceVariable.md)**
- **[Next Class](OXQView.md)**

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
