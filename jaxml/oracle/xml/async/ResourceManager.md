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

- **[Prev Class](DOMBuilderListener.md)**
- **[Next Class](XSLTransformer.md)**

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

**oracle.xml.async**

## **Class ResourceManager**

- **java.lang.Object**

- - **oracle.xml.async.ResourceManager**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class ResourceManager
      extends java.lang.Object

  **Simple semaphore that maintains access to fixed number of logical resources.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `ResourceManager``(int size)`<br>The ResourceManager constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                             |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `activeFound``()`<br>Checks if any of the logical resources being managed are in active use                                        |
    | `void`            | `getResource``()`<br>If the number of resources available for use is nonzero, the method decreases the number of resources by one. |
    | `void`            | `releaseResource``()`<br>Releases a resource.                                                                                      |
    | `void`            | `sleep``(int i)`<br>Allows usage of Thread.sleep() without try/catch                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ResourceManager

          public ResourceManager(int size)

      The ResourceManager constructor
      Parameters:
      `size` - - the number of resources to manage

  <!-- -->

  - ### Method Detail

    - #### getResource

          public void getResource()

      If the number of resources available for use is nonzero, the method decreases the number of resources by one. Otherwise, it waits until a resource is released & it becomes available for use.

    <!-- -->

    - #### releaseResource

          public void releaseResource()

      Releases a resource. When this method is called, the number of resources avialable is increased by one.

    <!-- -->

    - #### activeFound

          public boolean activeFound()

      Checks if any of the logical resources being managed are in active use
      Returns:
      `true` - if one or more resource is in use `false` - if none of the resources are in use

    <!-- -->

    - #### sleep

          public void sleep(int i)

      Allows usage of Thread.sleep() without try/catch

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

- **[Prev Class](DOMBuilderListener.md)**
- **[Next Class](XSLTransformer.md)**

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
