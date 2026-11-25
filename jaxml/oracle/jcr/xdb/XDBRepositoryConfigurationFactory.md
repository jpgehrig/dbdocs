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

- **[Prev Class](XDBRepositoryConfiguration.md)**
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

**oracle.jcr.xdb**

## **Class XDBRepositoryConfigurationFactory**

- **java.lang.Object**

- - **oracle.jcr.xdb.XDBRepositoryConfigurationFactory**

<!-- -->

- **All Implemented Interfaces:**
  **javax.naming.spi.ObjectFactory**

  ------------------------------------------------------------------------

  **Deprecated. **
  **XDBRepositoryConfigurationFactory is a JNDI ObjectFactory for XDBRepositoryConfiguration objects.**
  **
  **

      public class XDBRepositoryConfigurationFactory
      extends java.lang.Object
      implements javax.naming.spi.ObjectFactory

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                             |
    |-------------------------------------------------------------------------|
    | `XDBRepositoryConfigurationFactory``()`<br>Deprecated. <br>Constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                               |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`        | `getObjectInstance``(java.lang.Object obj, javax.naming.Name name, javax.naming.Context nameCtx, java.util.Hashtable environment)`<br>Deprecated. <br>JNDI factory method to create an object using the location or reference information specified. |
    | `static java.lang.Object` | `getXDBRepositoryConfigurationState``(`[`XDBRepositoryConfiguration`](XDBRepositoryConfiguration.md)` repositoryConfiguration)`<br>Deprecated. <br>Gets the internal state of the specified XDBRepositoryConfiguration.                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XDBRepositoryConfigurationFactory

          public XDBRepositoryConfigurationFactory()

      Deprecated. 
      Constructor.

  <!-- -->

  - ### Method Detail

    - #### getObjectInstance

          public java.lang.Object getObjectInstance(java.lang.Object obj,
                                                    javax.naming.Name name,
                                                    javax.naming.Context nameCtx,
                                                    java.util.Hashtable environment)
                                             throws java.lang.Exception

      Deprecated. 
      JNDI factory method to create an object using the location or reference information specified.
      Specified by:
      `getObjectInstance` in interface `javax.naming.spi.ObjectFactory`

      Parameters:
      `obj` - an object containing location or reference information that can be used in creating the object

      `name` - the name of the object relative to `nameCtx`, or null if no name is specified

      `nameCtx` - the context relative to which `name` is specified, or null if `name` is relative to the default initial context

      `environment` - the environment used in creating the object, or null

      Returns:
      the created object

      Throws:
      `java.lang.Exception` - if the operation fails

    <!-- -->

    - #### getXDBRepositoryConfigurationState

          public static java.lang.Object getXDBRepositoryConfigurationState(XDBRepositoryConfiguration repositoryConfiguration)

      Deprecated. 
      Gets the internal state of the specified XDBRepositoryConfiguration.
      Parameters:
      `repositoryConfiguration` - the repository configuration

      Returns:
      the state

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

- **[Prev Class](XDBRepositoryConfiguration.md)**
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
