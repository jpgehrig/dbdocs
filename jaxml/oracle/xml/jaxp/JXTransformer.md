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

- **[Prev Class](JXSAXTransformerFactory.md)**
- **Next Class**

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

**oracle.xml.jaxp**

## **Class JXTransformer**

- **java.lang.Object**

- - **[javax.xml.transform.Transformer](../../../javax/xml/transform/Transformer.md)**

  - - **oracle.xml.jaxp.JXTransformer**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class JXTransformer
      extends Transformer

  **An instance of this class transforms a Source into a Result.**
  **An instance of this class can be obtained with the `TransformerFactory.newTransformer` method. This instance may then be used to process XML from a variety of sources and write the transformation output to a variety of sinks.**

  **An object of this class may not be used in multiple threads running concurrently. Different Transformers may be used concurrently by different threads.**

  **A Transformer may be used multiple times. Parameters and output properties are preserved across transformations.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                |
    |------------------------------------------------------------------------------------------------------------|
    | `JXTransformer``()`<br>Default constructor                                                                 |
    | `JXTransformer``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` templates)`<br>Constructor is based on |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                           | `clearParameters``()`<br>Clear all parameters set with setParameter.                                                                                                                                                                                         |
    | [`ErrorListener`](../../../javax/xml/transform/ErrorListener.md) | `getErrorListener``()`<br>Get the error event handler in effect for the transformation.                                                                                                                                                                      |
    | `java.util.Properties`                                           | `getOutputProperties``()`<br>Get a copy of the output properties for the transformation.                                                                                                                                                                     |
    | `java.lang.String`                                               | `getOutputProperty``(java.lang.String name)`<br>Get an output property that is in effect for the transformation.                                                                                                                                             |
    | `oracle.xml.xslt.OutputURIResolver`                              | `getOutputURIResolver``()`                                                                                                                                                                                                                                   |
    | `java.lang.Object`                                               | `getParameter``(java.lang.String name)`<br>Get a parameter that was explicitly set with setParameter or setParameters.                                                                                                                                       |
    | [`URIResolver`](../../../javax/xml/transform/URIResolver.md)     | `getURIResolver``()`<br>Get an object that will be used to resolve URIs used in document(), etc.                                                                                                                                                             |
    | `void`                                                           | `setErrorListener``(`[`ErrorListener`](../../../javax/xml/transform/ErrorListener.md)` listener)`<br>Set the error event listener in effect for the transformation.                                                                                          |
    | `void`                                                           | `setGenerate_Output_Escaping_PIs``(boolean bool)`<br>By default, When Oracle JAXP XSLT transformer transforms an XML into a Result, it does not generate Result.PI_DISABLE_OUTPUT_ESCAPING and Result.PI_ENABLE_OUTPUT_ESCAPING PIs based on the stylesheet. |
    | `void`                                                           | `setOutputProperties``(java.util.Properties oformat)`<br>Set the output properties for the transformation.                                                                                                                                                   |
    | `void`                                                           | `setOutputProperty``(java.lang.String name, java.lang.String value)`<br>Set an output property that will be in effect for the transformation.                                                                                                                |
    | `void`                                                           | `setOutputURIResolver``(oracle.xml.xslt.OutputURIResolver resolver)`                                                                                                                                                                                         |
    | `void`                                                           | `setParameter``(java.lang.String name, java.lang.Object value)`<br>Add a parameter for the transformation.                                                                                                                                                   |
    | `void`                                                           | `setURIResolver``(`[`URIResolver`](../../../javax/xml/transform/URIResolver.md)` resolver)`<br>Set an object that will be used to resolve URIs used in document().                                                                                           |
    | `void`                                                           | `transform``(`[`Source`](../../../javax/xml/transform/Source.md)` source, `[`Result`](../../../javax/xml/transform/Result.md)` result)`<br>Process the source tree to the output result.                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JXTransformer

          public JXTransformer()

      Default constructor

    <!-- -->

    - #### JXTransformer

          public JXTransformer(XSLStylesheet templates)

      Constructor is based on
      Parameters:
      `templates` - a XSLStylesheet or Templates

  <!-- -->

  - ### Method Detail

    - #### setGenerate_Output_Escaping_PIs

          public void setGenerate_Output_Escaping_PIs(boolean bool)

      By default, When Oracle JAXP XSLT transformer transforms an XML into a Result, it does not generate Result.PI_DISABLE_OUTPUT_ESCAPING and Result.PI_ENABLE_OUTPUT_ESCAPING PIs based on the stylesheet. If user does want to include these two PIs in his/her output Result, s/he can enable it by calling setGenerate_Output_Escaping_PIs(true);
      Parameters:
      `bool` - : false if disable generating the PIs (default) true if enable generating the PIs

    <!-- -->

    - #### transform

          public void transform(Source source,
                                Result result)
                         throws TransformerException

      Process the source tree to the output result.
      Specified by:
      [`transform`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `source` - The input for the source tree.

      `result` - The output target.

      Throws:
      [`TransformerException`](../../../javax/xml/transform/TransformerException.md) - If an unrecoverable error occurs during the course of the transformation.

    <!-- -->

    - #### setParameter

          public void setParameter(java.lang.String name,
                                   java.lang.Object value)

      Add a parameter for the transformation.
      Pass a qualified name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For example, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      Specified by:
      [`setParameter`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `name` - Name of the parameter, which may begin with a namespace URI in curly braces ({}).

      `value` - The value object. This can be any valid Java object. It is up to the processor to provide the proper object coersion or to simply pass the object on for use in an extension.

    <!-- -->

    - #### getParameter

          public java.lang.Object getParameter(java.lang.String name)

      Get a parameter that was explicitly set with setParameter or setParameters.
      Specified by:
      [`getParameter`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `name` - A parameter name

      This method does not return a default parameter value, which cannot be determined until the node context is evaluated during the transformation process.

      Returns:
      A parameter that has been set with setParameter, or null if a parameter with the given name was not found.

    <!-- -->

    - #### clearParameters

          public void clearParameters()

      Clear all parameters set with setParameter.
      Specified by:
      [`clearParameters`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

    <!-- -->

    - #### setURIResolver

          public void setURIResolver(URIResolver resolver)

      Set an object that will be used to resolve URIs used in document(). currently, we do not support URIResolver in document() fuction
      If the resolver argument is null, the URIResolver value will be cleared, and the default behavior will be used.

      Specified by:
      [`setURIResolver`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `resolver` - An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### setOutputURIResolver

          public void setOutputURIResolver(oracle.xml.xslt.OutputURIResolver resolver)

    <!-- -->

    - #### getURIResolver

          public URIResolver getURIResolver()

      Get an object that will be used to resolve URIs used in document(), etc.
      Specified by:
      [`getURIResolver`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Returns:
      An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### getOutputURIResolver

          public oracle.xml.xslt.OutputURIResolver getOutputURIResolver()

    <!-- -->

    - #### setOutputProperties

          public void setOutputProperties(java.util.Properties oformat)

      Set the output properties for the transformation. These properties will override properties set in the Templates with \<xsl:output\>.
      If argument to this function is null, any properties previously set are removed, and the value will revert to the value defined in the templates object.

      Pass a qualified property key name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For ex, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      Specified by:
      [`setOutputProperties`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `oformat` - A set of output properties that will be used to override any of the same properties in affect for the transformation.

      Throws:
      `java.lang.IllegalArgumentException` - if any of the argument keys are not recognized and are not namespace qualified.

      See Also:
      [`OutputKeys`](../../../javax/xml/transform/OutputKeys.md), `Properties`

    <!-- -->

    - #### getOutputProperties

          public java.util.Properties getOutputProperties()

      Get a copy of the output properties for the transformation.
      The properties returned should contain properties set by the user, and properties set by the stylesheet, and these properties are "defaulted" by default properties specified by [section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output). The properties that were specifically set by the user or the stylesheet should be in the base Properties list, while the XSLT default properties that were not specifically set should be the default Properties list. Thus, getOutputProperties().getProperty(String key) will obtain any property in that was set by `setOutputProperty(java.lang.String, java.lang.String)`, `setOutputProperties(java.util.Properties)`, in the stylesheet, *or* the default properties, while getOutputProperties().get(String key) will only retrieve properties that were explicitly set by `setOutputProperty(java.lang.String, java.lang.String)`, `setOutputProperties(java.util.Properties)`, or in the stylesheet.

      Note that mutation of the Properties object returned will not effect the properties that the transformation contains.

      If any of the argument keys are not recognized and are not namespace qualified, the property will be ignored. In other words the behaviour is not orthogonal with setOutputProperties.

      Specified by:
      [`getOutputProperties`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Returns:
      A copy of the set of output properties in effect for the next transformation.

      See Also:
      [`OutputKeys`](../../../javax/xml/transform/OutputKeys.md), `Properties`

    <!-- -->

    - #### setOutputProperty

          public void setOutputProperty(java.lang.String name,
                                        java.lang.String value)

      Set an output property that will be in effect for the transformation.
      Pass a qualified property name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For ex, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      The Properties object that was passed to `setOutputProperties(java.util.Properties)` won't be effected by calling this method.

      Specified by:
      [`setOutputProperty`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `name` - A non-null String that specifies an output property name, which may be namespace qualified.

      `value` - The non-null string value of the output property.

      Throws:
      `java.lang.IllegalArgumentException` - If the property is not supported, and is not qualified with a namespace.

      See Also:
      [`OutputKeys`](../../../javax/xml/transform/OutputKeys.md)

    <!-- -->

    - #### getOutputProperty

          public java.lang.String getOutputProperty(java.lang.String name)

      Get an output property that is in effect for the transformation. The property specified may be a property that was set with setOutputProperty, or it may be a property specified in the stylesheet.
      Specified by:
      [`getOutputProperty`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `name` - A non-null String that specifies an output property name, which may be namespace qualified.

      Returns:
      The string value of the output property, or null if no property was found.

      Throws:
      `java.lang.IllegalArgumentException` - If the property is not supported.

      See Also:
      [`OutputKeys`](../../../javax/xml/transform/OutputKeys.md)

    <!-- -->

    - #### setErrorListener

          public void setErrorListener(ErrorListener listener)

      Set the error event listener in effect for the transformation.
      Specified by:
      [`setErrorListener`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Parameters:
      `listener` - The new error listener.

      Throws:
      `java.lang.IllegalArgumentException` - if listener is null.

    <!-- -->

    - #### getErrorListener

          public ErrorListener getErrorListener()

      Get the error event handler in effect for the transformation.
      Specified by:
      [`getErrorListener`](../../../javax/xml/transform/Transformer.md) in class [`Transformer`](../../../javax/xml/transform/Transformer.md)

      Returns:
      The current error handler, which should never be null.

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

- **[Prev Class](JXSAXTransformerFactory.md)**
- **Next Class**

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
