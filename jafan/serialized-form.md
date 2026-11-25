Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
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

# Serialized Form

- ## Package oracle.simplefan

  - ## Class [oracle.simplefan.FanEvent](oracle/simplefan/FanEvent.md) extends java.util.EventObject implements Serializable

    - ## Serialized Fields

      - #### timestamp

            java.util.Date timestamp

  - ## Class [oracle.simplefan.LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md) extends [FanEvent](oracle/simplefan/FanEvent.md) implements Serializable

  - ## Class [oracle.simplefan.NodeDownEvent](oracle/simplefan/NodeDownEvent.md) extends [FanEvent](oracle/simplefan/FanEvent.md) implements Serializable

  - ## Class [oracle.simplefan.NodeUpEvent](oracle/simplefan/NodeUpEvent.md) extends [FanEvent](oracle/simplefan/FanEvent.md) implements Serializable

  - ## Class [oracle.simplefan.ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md) extends [FanEvent](oracle/simplefan/FanEvent.md) implements Serializable

  - ## Class [oracle.simplefan.ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) extends java.lang.Object implements Serializable

  - ## Class [oracle.simplefan.ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md) extends [FanEvent](oracle/simplefan/FanEvent.md) implements Serializable

  - ## Class [oracle.simplefan.ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) extends java.lang.Object implements Serializable

- ## Package oracle.simplefan.impl

  - ## Class oracle.simplefan.impl.ServiceDownEvent.ServiceMemberEvent extends [ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) implements Serializable

    - ## Serialized Fields

      - #### instanceName

            java.lang.String instanceName

      - #### nodeName

            java.lang.String nodeName

  - ## Class oracle.simplefan.impl.ServiceUpEvent.ServiceMemberEvent extends [ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) implements Serializable

    - ## Serialized Fields

      - #### instanceName

            java.lang.String instanceName

      - #### nodeName

            java.lang.String nodeName

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
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
