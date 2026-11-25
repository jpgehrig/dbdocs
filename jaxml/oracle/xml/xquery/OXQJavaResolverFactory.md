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

- **[Prev Class](OXQItemAccessor.md)**
- **[Next Class](OXQOptions.md)**

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

## **Interface OXQJavaResolverFactory**

- **All Superinterfaces:**
  **[OXQEntityResolverFactory](OXQEntityResolverFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQJavaResolverFactory
      extends OXQEntityResolverFactory

  **The factory interface for creating entity resolvers for external functions implemented in Java.**
  **The entity resolver created by this factory responds to the following entity kind requests: [`OXQEntityKind.EXTERNAL_FUNCTION`](OXQEntityKind.md) and [`OXQEntityKind.MODULE`](OXQEntityKind.md).**

  **1. The entity resolver will respond to an [`OXQEntityKind.EXTERNAL_FUNCTION`](OXQEntityKind.md) request by returning a Java `Class` or `Method` based on the option declaration `OPTION_BINDING`. `OPTION_BINDING` must be set to a value of the form `package.Class#method(Type1,Type2,...)`, where**

  - **`package.Class` is a fully qualified name of a Java Class which either extends [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md), or contains a static Java Method which will be mapped to this function.**
  - **`method` Optional: name of a static method in the specified Java Class. If not specified then the XQuery function's local name is used.**
  - **`Type1,Type2,...` Optional: parameter types of the Java Method. If not specified then a mapping from XQuery parameters is used.**

  **Examples:**
        (: using a Java Class that extends OXQFunctionEvaluator :)
        declare option ora-java:binding = "example.MyFunctionImpl";
        declare function local:my-fn() as xs:int external;

        (: using static Java Method with complete "ora-java:binding" value :)
        declare option ora-java:binding = "java.lang.Math#min(int,int)";
        declare function local:my-min($x as xs:int, $y as xs:int) as xs:int external;

        (: implicit parameter types :)
        declare option ora-java:binding = "java.lang.Math#min";
        declare function local:my-min($x as xs:int, $y as xs:int) as xs:int external;

        (: implicit method name and parameter types :)
        declare option ora-java:binding = "java.lang.Math";
        declare function local:min($x as xs:int, $y as xs:int) as xs:int external;


  2\. The entity resolver will also respond to a [`OXQEntityKind.MODULE`](OXQEntityKind.md) request with a [`namespace`](OXQEntityLocator.md) in the form `java:package.Class`, where `package.Class` is a fully qualified name of a Java class to be imported as an XQuery module.

  Example:
        import module math = "java:java.lang.Math";
        math:max(1, 2)


  Since:
  12.1

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                  | Field and Description                                                   |
    |------------------------------------|-------------------------------------------------------------------------|
    | `static javax.xml.namespace.QName` | `OPTION_BINDING`<br>Name of the option that specifies the Java binding. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                 |
    |-------------------------|------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.ClassLoader` | `getClassLoader``()`<br>Returns the class loader that will be used for loading Java classes by this resolver.          |
    | `void`                  | `setClassLoader``(java.lang.ClassLoader classLoader)`<br>Assigns the class loader to be used for loading Java classes. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQEntityResolverFactory](OXQEntityResolverFactory.md)

      [`createResolver`](OXQEntityResolverFactory.md)

<!-- -->

- - ### Field Detail

    - #### OPTION_BINDING

          static final javax.xml.namespace.QName OPTION_BINDING

      Name of the option that specifies the Java binding. See this class' documentation for more details.

  <!-- -->

  - ### Method Detail

    - #### setClassLoader

          void setClassLoader(java.lang.ClassLoader classLoader)

      Assigns the class loader to be used for loading Java classes. By default the class loader that loaded `OXQJavaResolverFactory` is used.
      Parameters:
      `classLoader` - class loader instance. Cannot be `null`

    <!-- -->

    - #### getClassLoader

          java.lang.ClassLoader getClassLoader()

      Returns the class loader that will be used for loading Java classes by this resolver.
      Returns:
      class loader

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

- **[Prev Class](OXQItemAccessor.md)**
- **[Next Class](OXQOptions.md)**

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
