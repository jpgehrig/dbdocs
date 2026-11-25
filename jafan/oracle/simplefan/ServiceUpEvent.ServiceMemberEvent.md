Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](ServiceUpEvent.Reason.md)
- Next Class

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.simplefan

## Class ServiceUpEvent.ServiceMemberEvent

- java.lang.Object

- - oracle.simplefan.ServiceUpEvent.ServiceMemberEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  <!-- -->

  Enclosing class:
  [ServiceUpEvent](ServiceUpEvent.md)

  ------------------------------------------------------------------------



      public abstract static class ServiceUpEvent.ServiceMemberEvent
      extends java.lang.Object
      implements java.lang.Cloneable, java.io.Serializable

  The service member event that reflects the status change of a service on a particular instance (and node). When a service member is reported DOWN, all connections to that instance should be closed as invalid. When a service member is reported UP, new connections may be established to that instance.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ServiceMemberEvent``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description |
    |-----------------------------|------------------------|
    | `abstract java.lang.String` | `getInstanceName``()`  |
    | `abstract java.lang.String` | `getNodeName``()`      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ServiceMemberEvent

          public ServiceMemberEvent()

  <!-- -->

  - ### Method Detail

    - #### getInstanceName

          public abstract java.lang.String getInstanceName()

    <!-- -->

    - #### getNodeName

          public abstract java.lang.String getNodeName()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](ServiceUpEvent.Reason.md)
- Next Class

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
