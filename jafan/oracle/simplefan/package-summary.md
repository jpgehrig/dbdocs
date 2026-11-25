Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev Package
- [Next Package](impl/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Package oracle.simplefan

Provides easy access to Oracle Fast Application Notification (FAN) events.

See: Description

- **Interface Summary**

  | Interface                                   | Description |
  |---------------------------------------------|-------------|
  | [FanEventListener](FanEventListener.md)     |             |
  | [FanSubscription](FanSubscription.md)       |             |
  | [FanUpEventListener](FanUpEventListener.md) |             |

- **Class Summary**

  | Class                                                                         | Description                                                                                                               |
  |-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
  | [FanEvent](FanEvent.md)                                                       | This abstract class supports three types of FAN events: service events, node down events, and load advisory (RLB) events. |
  | [FanManager](FanManager.md)                                                   | An instance of this class is used to manage access to FAN events.                                                         |
  | [LoadAdvisoryEvent](LoadAdvisoryEvent.md)                                     | This FAN event provides advice that directs load balancing for subscribers.                                               |
  | [NodeDownEvent](NodeDownEvent.md)                                             | The event posted when a node goes down.                                                                                   |
  | [NodeUpEvent](NodeUpEvent.md)                                                 | The event posted when a node gets UP.                                                                                     |
  | [ServiceDownEvent](ServiceDownEvent.md)                                       | A container that can hold both kinds of service events.                                                                   |
  | [ServiceDownEvent.ServiceMemberEvent](ServiceDownEvent.ServiceMemberEvent.md) | The service member event that reflects the status change of a service on a particular instance (and node).                |
  | [ServiceUpEvent](ServiceUpEvent.md)                                           | A container that can hold both kinds of service events.                                                                   |
  | [ServiceUpEvent.ServiceMemberEvent](ServiceUpEvent.ServiceMemberEvent.md)     | The service member event that reflects the status change of a service on a particular instance (and node).                |

- **Enum Summary**

  | Enum                                                            | Description |
  |-----------------------------------------------------------------|-------------|
  | [LoadAdvisoryEvent.LoadStatus](LoadAdvisoryEvent.LoadStatus.md) |             |
  | [ServiceDownEvent.EventKind](ServiceDownEvent.EventKind.md)     |             |
  | [ServiceDownEvent.Reason](ServiceDownEvent.Reason.md)           |             |
  | [ServiceUpEvent.EventKind](ServiceUpEvent.EventKind.md)         |             |
  | [ServiceUpEvent.Reason](ServiceUpEvent.Reason.md)               |             |

## Package oracle.simplefan Description

Provides easy access to Oracle Fast Application Notification (FAN) events. FAN events are produced by Oracle Real Application Cluster (RAC) clusters to communicate significant changes in cluster state. This package provides easy access to a subset of FAN messages. The subset is sufficient to satisfy most user needs while the simple API hides the full complexity of the complete FAN event mechanism.

This package supports four FAN events.

Load Balancing Advisory
contain information that aids distributing work

Service Member Down
reports than one member instance of a service is down

Service Composite Down
reports that all member instances of a service are down

Node Down
reports that a node (host) is down

*ons.config*

    localport=4100
    remoteport=4200
    loglevel=3
    nodes=myhost.myco.com:6200

## Related Documentation

For overviews, tutorials, examples, guides, and tool documentation, please see:

- Oracle Database JDBC Developer's Guide

Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev Package
- [Next Package](impl/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
