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

- **[Prev Class](Element.md)**
- **[Next Class](JAXBException.md)**

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

**javax.xml.bind**

## **Class JAXBContext**

- **java.lang.Object**

- - **javax.xml.bind.JAXBContext**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class JAXBContext
      extends java.lang.Object

  **The `JAXBContext` class provides the client's entry point to the JAXB API. It provides an abstraction for managing the XML/Java binding information necessary to implement the JAXB binding framework operations: unmarshal, marshal and validate. A client application obtains new instances of this class via the `newInstance(contextPath)` method.**

           JAXBContext jc = JAXBContext.newInstance( "com.acme.foo:com.acme.bar" );


  **The `contextPath` contains a list of Java package names that contain schema derived interfaces. The value of this parameter initializes the `JAXBContext` object so that it is capable of managing the schema derived interfaces.**

  > *****SPEC REQUIREMENT:** the provider must supply an implementation class containing a method with the following signature:***
  >
  >             public static JAXBContext createContext( String contextPath, ClassLoader classLoader )
  >                 throws JAXBException;
  >
  >
  > *JAXB Providers must generate a `jaxb.properties` file in each package containing schema derived classes. The property file must contain a property named `javax.xml.bind.context.factory` whose value is the name of the class that implements the `createContext` API.*
  >
  > *The class supplied by the provider does not have to be assignable to `javax.xml.bind.JAXBContext`, it simply has to provide a class that implements the `createContext` API.*

  **Unmarshalling**

  > The [`Unmarshaller`](Unmarshaller.md) class provides the client application the ability to convert XML data into a tree of Java content objects. The unmarshal method for a schema (within a namespace) allows for any global XML element declared in the schema to be unmarshalled as the root of an instance document. The `JAXBContext` object allows the merging of global elements across a set of schemas (listed in the `contextPath`). Since each schema in the schema set can belong to distinct namespaces, the unification of schemas to an unmarshalling context should be namespace independent. This means that a client application is able to unmarshal XML documents that are instances of any of the schemas listed in the `contextPath`. For example:
  >
  >             JAXBContext jc = JAXBContext.newInstance( "com.acme.foo:com.acme.bar" );
  >             Unmarshaller u = jc.createUnmarshaller();
  >             FooObject fooObj = (FooObject)u.unmarshal( new File( "foo.xml" ) ); // ok
  >             BarObject barObj = (BarObject)u.unmarshal( new File( "bar.xml" ) ); // ok
  >             BazObject bazObj = (BazObject)u.unmarshal( new File( "baz.xml" ) ); // error, "com.acme.baz" not in contextPath
  >
  >
  > The client application may also generate Java content trees explicitly rather than unmarshalling existing XML data. To do so, the application needs to have access and knowledge about each of the schema derived `ObjectFactory` classes that exist in each of java packages contained in the `contextPath`. For each schema derived java class, there will be a static factory method that produces objects of that type. For example, assume that after compiling a schema, you have a package `com.acme.foo` that contains a schema derived interface named `PurchaseOrder`. In order to create objects of that type, the client application would use the factory method like this:
  >
  >            com.acme.foo.PurchaseOrder po =
  >                com.acme.foo.ObjectFactory.createPurchaseOrder();
  >
  >
  > Once the client application has an instance of the the schema derived object, it can use the mutator methods to set content on it.
  >
  > For more information on the generated `ObjectFactory` classes, see Section 4.2 *Java Package* of the specification.
  >
  > ***SPEC REQUIREMENT:** the provider must generate a class in each package that contains all of the necessary object factory methods for that package named ObjectFactory as well as the static `newInstance( javaContentInterface )` method*

  **Marshalling**

  > The [`Marshaller`](Marshaller.md) class provides the client application the ability to convert a Java content tree back into XML data. There is no difference between marshalling a content tree that is created manually using the factory methods and marshalling a content tree that is the result an `unmarshal` operation. Clients can marshal a java content tree back to XML data to a `java.io.OutputStream` or a `java.io.Writer`. The marshalling process can alternatively produce SAX2 event streams to a registered `ContentHandler` or produce a DOM Node object.
  >
  > Here is a simple example that unmarshals an XML document and then marshals it back out:
  >
  >             JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >
  >             // unmarshal from foo.xml
  >             Unmarshaller u = jc.createUnmarshaller();
  >             FooObject fooObj = (FooObject)u.unmarshal( new File( "foo.xml" ) );
  >
  >             // marshal to System.out
  >             Marshaller m = jc.createMarshaller();
  >             m.marshal( fooObj, System.out );
  >

  **Validation**

  > There are three varieties of validation available to JAXB client applications:
  >
  > > Unmarshal-time Validation
  > > Validation performed on the XML data as it is being unmarshalled into a Java content tree
  > >
  > > On-Demand Validation
  > > Validation performed on the Java content tree in memory
  > >
  > > Fail-Fast Validation
  > > Validation of Java property constraints at runtime when client applications invoke the setter methods of the generated classes
  >
  > See: [Validator javadocs](Validator.md) for a more detailed definition of the different type of validation.
  >
  > Although unmarshal-time validation and on-demand validation are very similar, they are completely orthogonal operations with no dependencies on each other. Client applications are free to use one, both, or neither types of validation.
  >
  > Validation errors and warnings encountered during the unmarshal and validate operations are reported to the client application via a callback error handler interface ([`ValidationEventHandler`](ValidationEventHandler.md)) that receives [`ValidationEvent`](ValidationEvent.md) objects. The `ValidationEvent` objects contain information about the error or warning encountered. JAXB allows a few diffent methods of handling validation events which are described in more detail in the [Validator javadoc](Validator.md).

  **JAXB Runtime Binding Framework Compatibility**

  > Since the JAXB Specification does not define a common runtime system, a JAXB client application must not attempt to mix runtime objects (`JAXBContext, Marshaller`, etc. ) from different providers. This does not mean that the client application isn't portable, it simply means that a client has to use a runtime system provided by the same provider that was used to compile the schema.

  Since:
  JAXB1.0

  See Also:
  [`Marshaller`](Marshaller.md), [`Unmarshaller`](Unmarshaller.md), [`Validator`](Validator.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                 |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `JAXB_CONTEXT_FACTORY`<br>The name of the property that contains the name of the class capable of creating new `JAXBContext` objects. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                              |
    |----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`Marshaller`](Marshaller.md)     | `createMarshaller``()`<br>Create a `Marshaller` object that can be used to convert a java content tree into XML data.               |
    | `abstract `[`Unmarshaller`](Unmarshaller.md) | `createUnmarshaller``()`<br>Create an `Unmarshaller` object that can be used to convert XML data into a java content tree.          |
    | `abstract `[`Validator`](Validator.md)       | `createValidator``()`<br>Create a `Validator` object that can be used to validate a java content tree against its source schema.    |
    | `static JAXBContext`                         | `newInstance``(java.lang.String contextPath)`<br>Obtain a new instance of a `JAXBContext` class.                                    |
    | `static JAXBContext`                         | `newInstance``(java.lang.String contextPath, java.lang.ClassLoader classLoader)`<br>Obtain a new instance of a `JAXBContext` class. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### JAXB_CONTEXT_FACTORY

          public static final java.lang.String JAXB_CONTEXT_FACTORY

      The name of the property that contains the name of the class capable of creating new `JAXBContext` objects.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### newInstance

          public static JAXBContext newInstance(java.lang.String contextPath)
                                         throws JAXBException

      Obtain a new instance of a `JAXBContext` class.

      This is a convenience method for the `newInstance` method. It uses the context class loader of the current thread. To specify the use of a different class loader, either set it via the `Thread.setContextClassLoader()` api or use the `newInstance` method.

      Throws:
      [`JAXBException`](JAXBException.md)

    <!-- -->

    - #### newInstance

          public static JAXBContext newInstance(java.lang.String contextPath,
                                                java.lang.ClassLoader classLoader)
                                         throws JAXBException

      Obtain a new instance of a `JAXBContext` class.

      The client application must supply a context path which is a list of colon (':', \u003A) separated java package names that contain schema derived classes. The JAXB provider will ensure that each package on the context path has a `jaxb.properties` file which contains a value for the `javax.xml.bind.context.factory` property and that all values resolve to the same provider.

      If there are any global XML element name collisions across the various packages listed on the `contextPath`, a `JAXBException` will be thrown. Mixing generated classes from multiple JAXB Providers in the same context path will also result in a `JAXBException` being thrown.

      Parameters:
      `contextPath` - list of java package names that contain schema derived classes

      `classLoader` - This class loader will be used to locate the implementation classes.

      Returns:
      a new instance of a `JAXBContext`

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while creating the `JAXBContext`, such as an ambiguity among global elements contained in the contextPath, failure to locate a value for the context factory property, or mixing schema derived packages from different providers on the same contextPath.

    <!-- -->

    - #### createUnmarshaller

          public abstract Unmarshaller createUnmarshaller()
                                                   throws JAXBException

      Create an `Unmarshaller` object that can be used to convert XML data into a java content tree.
      Returns:
      an `Unmarshaller` object

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while creating the `Unmarshaller` object

    <!-- -->

    - #### createMarshaller

          public abstract Marshaller createMarshaller()
                                               throws JAXBException

      Create a `Marshaller` object that can be used to convert a java content tree into XML data.
      Returns:
      a `Marshaller` object

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while creating the `Marshaller` object

    <!-- -->

    - #### createValidator

          public abstract Validator createValidator()
                                             throws JAXBException

      Create a `Validator` object that can be used to validate a java content tree against its source schema.
      Returns:
      a `Validator` object

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while creating the `Validator` object

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

- **[Prev Class](Element.md)**
- **[Next Class](JAXBException.md)**

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
