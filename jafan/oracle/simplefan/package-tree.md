Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Hierarchy For Package oracle.simplefan

Package Hierarchies:

- [All Packages](../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - java.util.EventObject (implements java.io.Serializable)
    - oracle.simplefan.[FanEvent](FanEvent.md)
      - oracle.simplefan.[LoadAdvisoryEvent](LoadAdvisoryEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[NodeDownEvent](NodeDownEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[NodeUpEvent](NodeUpEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[ServiceDownEvent](ServiceDownEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[ServiceUpEvent](ServiceUpEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
  - oracle.simplefan.[FanManager](FanManager.md)
  - oracle.simplefan.[ServiceDownEvent.ServiceMemberEvent](ServiceDownEvent.ServiceMemberEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
  - oracle.simplefan.[ServiceUpEvent.ServiceMemberEvent](ServiceUpEvent.ServiceMemberEvent.md) (implements java.lang.Cloneable, java.io.Serializable)

## Interface Hierarchy

- java.util.EventListener
  - oracle.simplefan.[FanEventListener](FanEventListener.md)
    - oracle.simplefan.[FanUpEventListener](FanUpEventListener.md)
- oracle.simplefan.[FanSubscription](FanSubscription.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.simplefan.[ServiceDownEvent.EventKind](ServiceDownEvent.EventKind.md)
    - oracle.simplefan.[ServiceDownEvent.Reason](ServiceDownEvent.Reason.md)
    - oracle.simplefan.[LoadAdvisoryEvent.LoadStatus](LoadAdvisoryEvent.LoadStatus.md)
    - oracle.simplefan.[ServiceUpEvent.EventKind](ServiceUpEvent.EventKind.md)
    - oracle.simplefan.[ServiceUpEvent.Reason](ServiceUpEvent.Reason.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
