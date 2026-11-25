Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OracleRepositoryConfiguration.md)**
- **[Next Class](OracleSession.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**oracle.jcr**

## **Class OracleRepositoryFactory**

- **java.lang.Object**

- - **oracle.jcr.OracleRepositoryFactory**

<!-- -->

- **All Implemented Interfaces:**
  **javax.naming.spi.ObjectFactory**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleRepositoryFactory creates OracleRepository objects.**
  **An OracleRepository is the entry point to a content repository. Each OracleRepository object encapsulates an OracleRepositoryConfiguration which describes how that OracleRepository operates against the underlying content repository. There is a different OracleRepositoryConfiguration implementation for each type of content repository. For example, an XDBRepositoryConfiguration encapsulates the JDBC OracleDataSource by which an OracleRepository connects to an XML DB repository.**

  **
  **

      public class OracleRepositoryFactory
      extends java.lang.Object
      implements javax.naming.spi.ObjectFactory

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                           |
    |-----------------------------------------------------------------------|
    | `OracleRepositoryFactory``()`<br>Deprecated. <br>Default constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                                                               |
    |----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`OracleRepository`](OracleRepository.md) | `createOracleRepository``()`<br>Deprecated. <br>Creates a default OracleRepository.                                                                                                                                                                  |
    | `static `[`OracleRepository`](OracleRepository.md) | `createOracleRepository``(`[`OracleRepositoryConfiguration`](OracleRepositoryConfiguration.md)` repositoryConfiguration)`<br>Deprecated. <br>Creates an OracleRepository using the specified OracleRepositoryConfiguration.                          |
    | `java.lang.Object`                                 | `getObjectInstance``(java.lang.Object obj, javax.naming.Name name, javax.naming.Context nameCtx, java.util.Hashtable environment)`<br>Deprecated. <br>JNDI factory method to create an object using the location or reference information specified. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OracleRepositoryFactory

          public OracleRepositoryFactory()

      Deprecated. 
      Default constructor.

  <!-- -->

  - ### Method Detail

    - #### createOracleRepository

          public static OracleRepository createOracleRepository()
                                                         throws RepositoryException

      Deprecated. 
      Creates a default OracleRepository.
      This method dynamically constructs an OracleRepositoryConfiguration and uses it to create an OracleRepository. The system property named `oracle.jcr.OracleRepositoryConfiguration` must be set to the fully-qualified class name of the OracleRepositoryConfiguration.

      The configuration of the selected OracleRepositoryConfiguration implementation may be influenced by additional system properties. For details, refer to the Javadoc of that class. If required, the OracleRepository may be further configured by calling its `getRepositoryConfiguration` method to get the OracleRepositoryConfiguration object and then calling the appropriate configuration methods on that OracleRepositoryConfiguration implementation.

      Returns:
      the repository

      Throws:
      [`RepositoryException`](../../javax/jcr/RepositoryException.md) - if the operation fails

    <!-- -->

    - #### createOracleRepository

          public static OracleRepository createOracleRepository(OracleRepositoryConfiguration repositoryConfiguration)
                                                         throws RepositoryException

      Deprecated. 
      Creates an OracleRepository using the specified OracleRepositoryConfiguration.
      Parameters:
      `repositoryConfiguration` - the repository configuration; required

      Returns:
      the repository

      Throws:
      [`RepositoryException`](../../javax/jcr/RepositoryException.md) - if the operation fails

    <!-- -->

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

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OracleRepositoryConfiguration.md)**
- **[Next Class](OracleSession.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
