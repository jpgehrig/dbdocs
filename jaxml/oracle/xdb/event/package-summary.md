Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../dom/package-summary.md)**
- **[Next Package](../servlet/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package oracle.xdb.event**

**Provides the classes needed for Oracle Oracle XML Database Repository Events framework.**

**See: Description**

- **Interface Summary**

  | Interface                                                   | Description                  |
  |-------------------------------------------------------------|------------------------------|
  | [XDBRepositoryEventListener](XDBRepositoryEventListener.md) | Interface for Java handlers. |

- **Class Summary**

  | Class                                             | Description                                                                                             |
  |---------------------------------------------------|---------------------------------------------------------------------------------------------------------|
  | [XDBBasicEventListener](XDBBasicEventListener.md) | An example class to show how application writers can create there own event listeners.                  |
  | [XDBEvent](XDBEvent.md)                           | This class stores the information about the event that is fired.                                        |
  | [XDBHandler](XDBHandler.md)                       | This class stores information about handlers defined in resource configuration.                         |
  | [XDBHandlerList](XDBHandlerList.md)               | This class is used to store and manage the list of `XDBHandler` objects.                                |
  | [XDBLink](XDBLink.md)                             | This class stores information about the link of a resource.                                             |
  | [XDBPath](XDBPath.md)                             | This class stores information about the path of a resource                                              |
  | [XDBRenderStream](XDBRenderStream.md)             | This class is used by the `XDBRepositoryEvent` class by `getOutputStream` and `setRenderStream` methods |
  | [XDBRepositoryEvent](XDBRepositoryEvent.md)       | This class stores information about the repository event that is fired.                                 |

- **Exception Summary**

  | Exception                                                       | Description                                           |
  |-----------------------------------------------------------------|-------------------------------------------------------|
  | [XDBInvalidOperationException](XDBInvalidOperationException.md) | The exception thrown when an operation is not allowed |

## **Package oracle.xdb.event Description**

**Provides the classes needed for Oracle Oracle XML Database Repository Events framework. These classes are to be used to write JAVA event handler code.**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../dom/package-summary.md)**
- **[Next Package](../servlet/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
