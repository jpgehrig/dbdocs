Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Hierarchy For All Packages

Package Hierarchies:

- [oracle.simplefan](oracle/simplefan/package-tree.md),
- [oracle.simplefan.impl](oracle/simplefan/impl/package-tree.md)

## Class Hierarchy

- java.lang.Object
  - java.util.EventObject (implements java.io.Serializable)
    - oracle.simplefan.[FanEvent](oracle/simplefan/FanEvent.md)
      - oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[NodeDownEvent](oracle/simplefan/NodeDownEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[NodeUpEvent](oracle/simplefan/NodeUpEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
      - oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
  - oracle.simplefan.[FanManager](oracle/simplefan/FanManager.md)
    - oracle.simplefan.impl.[FanManager](oracle/simplefan/impl/FanManager.md)
  - oracle.simplefan.[ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) (implements java.lang.Cloneable, java.io.Serializable)
  - oracle.simplefan.[ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) (implements java.lang.Cloneable, java.io.Serializable)

## Interface Hierarchy

- java.util.EventListener
  - oracle.simplefan.[FanEventListener](oracle/simplefan/FanEventListener.md)
    - oracle.simplefan.[FanUpEventListener](oracle/simplefan/FanUpEventListener.md)
- oracle.simplefan.[FanSubscription](oracle/simplefan/FanSubscription.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.simplefan.[ServiceDownEvent.EventKind](oracle/simplefan/ServiceDownEvent.EventKind.md)
    - oracle.simplefan.[ServiceDownEvent.Reason](oracle/simplefan/ServiceDownEvent.Reason.md)
    - oracle.simplefan.[LoadAdvisoryEvent.LoadStatus](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md)
    - oracle.simplefan.[ServiceUpEvent.EventKind](oracle/simplefan/ServiceUpEvent.EventKind.md)
    - oracle.simplefan.[ServiceUpEvent.Reason](oracle/simplefan/ServiceUpEvent.Reason.md)

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
