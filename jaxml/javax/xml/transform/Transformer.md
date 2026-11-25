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

- **[Prev Class](Templates.md)**
- **[Next Class](TransformerConfigurationException.md)**

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

## **Class Transformer**

- **java.lang.Object**

- - **javax.xml.transform.Transformer**

<!-- -->

- **Direct Known Subclasses:**
  **[JXTransformer](../../../oracle/xml/jaxp/JXTransformer.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class Transformer
      extends java.lang.Object

  **An instace of this abstract class can transform a source tree into a result tree.**
  **An instance of this class can be obtained with the `TransformerFactory.newTransformer` method. This instance may then be used to process XML from a variety of sources and write the transformation output to a variety of sinks.**

  **An object of this class may not be used in multiple threads running concurrently. Different Transformers may be used concurrently by different threads.**

  **A Transformer may be used multiple times. Parameters and output properties are preserved across transformations.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                              | Method and Description                                                                                                                        |
    |------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract void`                                | `clearParameters``()`<br>Clear all parameters set with setParameter.                                                                          |
    | `abstract `[`ErrorListener`](ErrorListener.md) | `getErrorListener``()`<br>Get the error event handler in effect for the transformation.                                                       |
    | `abstract java.util.Properties`                | `getOutputProperties``()`<br>Get a copy of the output properties for the transformation.                                                      |
    | `abstract java.lang.String`                    | `getOutputProperty``(java.lang.String name)`<br>Get an output property that is in effect for the transformation.                              |
    | `abstract java.lang.Object`                    | `getParameter``(java.lang.String name)`<br>Get a parameter that was explicitly set with setParameter or setParameters.                        |
    | `abstract `[`URIResolver`](URIResolver.md)     | `getURIResolver``()`<br>Get an object that will be used to resolve URIs used in document(), etc.                                              |
    | `abstract void`                                | `setErrorListener``(`[`ErrorListener`](ErrorListener.md)` listener)`<br>Set the error event listener in effect for the transformation.        |
    | `abstract void`                                | `setOutputProperties``(java.util.Properties oformat)`<br>Set the output properties for the transformation.                                    |
    | `abstract void`                                | `setOutputProperty``(java.lang.String name, java.lang.String value)`<br>Set an output property that will be in effect for the transformation. |
    | `abstract void`                                | `setParameter``(java.lang.String name, java.lang.Object value)`<br>Add a parameter for the transformation.                                    |
    | `abstract void`                                | `setURIResolver``(`[`URIResolver`](URIResolver.md)` resolver)`<br>Set an object that will be used to resolve URIs used in document().         |
    | `abstract void`                                | `transform``(`[`Source`](Source.md)` xmlSource, `[`Result`](Result.md)` outputTarget)`<br>Process the source tree to the output result.       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### transform

          public abstract void transform(Source xmlSource,
                                         Result outputTarget)
                                  throws TransformerException

      Process the source tree to the output result.
      Parameters:
      `xmlSource` - The input for the source tree.

      `outputTarget` - The output target.

      Throws:
      [`TransformerException`](TransformerException.md) - If an unrecoverable error occurs during the course of the transformation.

    <!-- -->

    - #### setParameter

          public abstract void setParameter(java.lang.String name,
                                            java.lang.Object value)

      Add a parameter for the transformation.
      Pass a qualified name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For example, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      Parameters:
      `name` - The name of the parameter, which may begin with a namespace URI in curly braces ({}).

      `value` - The value object. This can be any valid Java object. It is up to the processor to provide the proper object coersion or to simply pass the object on for use in an extension.

    <!-- -->

    - #### getParameter

          public abstract java.lang.Object getParameter(java.lang.String name)

      Get a parameter that was explicitly set with setParameter or setParameters.
      This method does not return a default parameter value, which cannot be determined until the node context is evaluated during the transformation process.

      Returns:
      A parameter that has been set with setParameter, or null if a parameter with the given name was not found.

    <!-- -->

    - #### clearParameters

          public abstract void clearParameters()

      Clear all parameters set with setParameter.

    <!-- -->

    - #### setURIResolver

          public abstract void setURIResolver(URIResolver resolver)

      Set an object that will be used to resolve URIs used in document().
      If the resolver argument is null, the URIResolver value will be cleared, and the default behavior will be used.

      Parameters:
      `resolver` - An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### getURIResolver

          public abstract URIResolver getURIResolver()

      Get an object that will be used to resolve URIs used in document(), etc.
      Returns:
      An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### setOutputProperties

          public abstract void setOutputProperties(java.util.Properties oformat)
                                            throws java.lang.IllegalArgumentException

      Set the output properties for the transformation. These properties will override properties set in the Templates with xsl:output.
      If argument to this function is null, any properties previously set are removed, and the value will revert to the value defined in the templates object.

      Pass a qualified property key name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For example, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      Parameters:
      `oformat` - A set of output properties that will be used to override any of the same properties in affect for the transformation.

      Throws:
      `java.lang.IllegalArgumentException` - if any of the argument keys are not recognized and are not namespace qualified.

      See Also:
      [`OutputKeys`](OutputKeys.md), `Properties`

    <!-- -->

    - #### getOutputProperties

          public abstract java.util.Properties getOutputProperties()

      Get a copy of the output properties for the transformation.
      The properties returned should contain properties set by the user, and properties set by the stylesheet, and these properties are "defaulted" by default properties specified by [section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output). The properties that were specifically set by the user or the stylesheet should be in the base Properties list, while the XSLT default properties that were not specifically set should be the default Properties list. Thus, getOutputProperties().getProperty(String key) will obtain any property in that was set by `setOutputProperty(java.lang.String, java.lang.String)`, `setOutputProperties(java.util.Properties)`, in the stylesheet, *or* the default properties, while getOutputProperties().get(String key) will only retrieve properties that were explicitly set by `setOutputProperty(java.lang.String, java.lang.String)`, `setOutputProperties(java.util.Properties)`, or in the stylesheet.

      Note that mutation of the Properties object returned will not effect the properties that the transformation contains.

      If any of the argument keys are not recognized and are not namespace qualified, the property will be ignored. In other words the behaviour is not orthogonal with setOutputProperties.

      Returns:
      A copy of the set of output properties in effect for the next transformation.

      See Also:
      [`OutputKeys`](OutputKeys.md), `Properties`

    <!-- -->

    - #### setOutputProperty

          public abstract void setOutputProperty(java.lang.String name,
                                                 java.lang.String value)
                                          throws java.lang.IllegalArgumentException

      Set an output property that will be in effect for the transformation.
      Pass a qualified property name as a two-part string, the namespace URI enclosed in curly braces ({}), followed by the local name. If the name has a null URL, the String only contain the local name. An application can safely check for a non-null URI by testing to see if the first character of the name is a '{' character.

      For example, if a URI and local name were obtained from an element defined with \<xyz:foo xmlns:xyz="http://xyz.foo.com/yada/baz.html"/\>, then the qualified name would be "{http://xyz.foo.com/yada/baz.html}foo". Note that no prefix is used.

      The Properties object that was passed to `setOutputProperties(java.util.Properties)` won't be effected by calling this method.

      Parameters:
      `name` - A non-null String that specifies an output property name, which may be namespace qualified.

      `value` - The non-null string value of the output property.

      Throws:
      `java.lang.IllegalArgumentException` - If the property is not supported, and is not qualified with a namespace.

      See Also:
      [`OutputKeys`](OutputKeys.md)

    <!-- -->

    - #### getOutputProperty

          public abstract java.lang.String getOutputProperty(java.lang.String name)
                                                      throws java.lang.IllegalArgumentException

      Get an output property that is in effect for the transformation. The property specified may be a property that was set with setOutputProperty, or it may be a property specified in the stylesheet.
      Parameters:
      `name` - A non-null String that specifies an output property name, which may be namespace qualified.

      Returns:
      The string value of the output property, or null if no property was found.

      Throws:
      `java.lang.IllegalArgumentException` - If the property is not supported.

      See Also:
      [`OutputKeys`](OutputKeys.md)

    <!-- -->

    - #### setErrorListener

          public abstract void setErrorListener(ErrorListener listener)
                                         throws java.lang.IllegalArgumentException

      Set the error event listener in effect for the transformation.
      Parameters:
      `listener` - The new error listener.

      Throws:
      `java.lang.IllegalArgumentException` - if listener is null.

    <!-- -->

    - #### getErrorListener

          public abstract ErrorListener getErrorListener()

      Get the error event handler in effect for the transformation.
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

- **[Prev Class](Templates.md)**
- **[Next Class](TransformerConfigurationException.md)**

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
