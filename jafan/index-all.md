Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
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

A C F G H L N O R S V 

## A

[addListener(FanEventListener)](oracle/simplefan/FanSubscription.md) - Method in interface oracle.simplefan.[FanSubscription](oracle/simplefan/FanSubscription.md)
Adds a listener.

## C

[close()](oracle/simplefan/FanSubscription.md) - Method in interface oracle.simplefan.[FanSubscription](oracle/simplefan/FanSubscription.md)
Closes this subscription.

[configure(Properties)](oracle/simplefan/FanManager.md) - Method in class oracle.simplefan.[FanManager](oracle/simplefan/FanManager.md)
Configures the event daemon.

[configure(Properties)](oracle/simplefan/impl/FanManager.md) - Method in class oracle.simplefan.impl.[FanManager](oracle/simplefan/impl/FanManager.md)
Configures the event daemon.

## F

[FanEvent](oracle/simplefan/FanEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
This abstract class supports three types of FAN events: service events, node down events, and load advisory (RLB) events.

[FanEventListener](oracle/simplefan/FanEventListener.md) - Interface in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[FanManager](oracle/simplefan/FanManager.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
An instance of this class is used to manage access to FAN events.

[FanManager](oracle/simplefan/impl/FanManager.md) - Class in [oracle.simplefan.impl](oracle/simplefan/impl/package-summary.md)
 

[FanManager()](oracle/simplefan/impl/FanManager.md) - Constructor for class oracle.simplefan.impl.[FanManager](oracle/simplefan/impl/FanManager.md)
 

[FanSubscription](oracle/simplefan/FanSubscription.md) - Interface in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[FanUpEventListener](oracle/simplefan/FanUpEventListener.md) - Interface in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

## G

[getCardinality()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
 

[getDatabaseUniqueName()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getDatabaseUniqueName()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
 

[getDatabaseUniqueName()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
 

[getDrainTimeout()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
 

[getIncarnation()](oracle/simplefan/NodeDownEvent.md) - Method in class oracle.simplefan.[NodeDownEvent](oracle/simplefan/NodeDownEvent.md)
 

[getIncarnation()](oracle/simplefan/NodeUpEvent.md) - Method in class oracle.simplefan.[NodeUpEvent](oracle/simplefan/NodeUpEvent.md)
 

[getInstance()](oracle/simplefan/FanManager.md) - Static method in class oracle.simplefan.[FanManager](oracle/simplefan/FanManager.md)
Gets an instance of the concrete implementation class.

[getInstanceInternal()](oracle/simplefan/impl/FanManager.md) - Static method in class oracle.simplefan.impl.[FanManager](oracle/simplefan/impl/FanManager.md)
Get an instance of the concrete implementation class.

[getInstanceName()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getInstanceName()](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md)
 

[getInstanceName()](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md)
 

[getKind()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
Service down events can be member down, composite down, or both.

[getKind()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
Service up events can be member up, composite up, or both.

[getLoadStatus()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getNodeName()](oracle/simplefan/NodeDownEvent.md) - Method in class oracle.simplefan.[NodeDownEvent](oracle/simplefan/NodeDownEvent.md)
 

[getNodeName()](oracle/simplefan/NodeUpEvent.md) - Method in class oracle.simplefan.[NodeUpEvent](oracle/simplefan/NodeUpEvent.md)
 

[getNodeName()](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md)
 

[getNodeName()](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md)
 

[getPercent()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getReason()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
 

[getReason()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
 

[getServiceMemberEvent()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
Return the service member subevent information if this is a service member event.

[getServiceMemberEvent()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
Return the service member subevent information if this is a service member event.

[getServiceName()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getServiceName()](oracle/simplefan/ServiceDownEvent.md) - Method in class oracle.simplefan.[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md)
 

[getServiceName()](oracle/simplefan/ServiceUpEvent.md) - Method in class oracle.simplefan.[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md)
 

[getServiceQuality()](oracle/simplefan/LoadAdvisoryEvent.md) - Method in class oracle.simplefan.[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md)
 

[getTimestamp()](oracle/simplefan/FanEvent.md) - Method in class oracle.simplefan.[FanEvent](oracle/simplefan/FanEvent.md)
Returns the time the event occurred.

## H

[handleEvent(ServiceDownEvent)](oracle/simplefan/FanEventListener.md) - Method in interface oracle.simplefan.[FanEventListener](oracle/simplefan/FanEventListener.md)
Handle the event.

[handleEvent(NodeDownEvent)](oracle/simplefan/FanEventListener.md) - Method in interface oracle.simplefan.[FanEventListener](oracle/simplefan/FanEventListener.md)
Handle the event.

[handleEvent(LoadAdvisoryEvent)](oracle/simplefan/FanEventListener.md) - Method in interface oracle.simplefan.[FanEventListener](oracle/simplefan/FanEventListener.md)
Handle the event.

[handleEvent(ServiceUpEvent)](oracle/simplefan/FanUpEventListener.md) - Method in interface oracle.simplefan.[FanUpEventListener](oracle/simplefan/FanUpEventListener.md)
This method handles ServiceUpEvents.

[handleEvent(NodeUpEvent)](oracle/simplefan/FanUpEventListener.md) - Method in interface oracle.simplefan.[FanUpEventListener](oracle/simplefan/FanUpEventListener.md)
This method handles NodeUpEvents.

## L

[LoadAdvisoryEvent](oracle/simplefan/LoadAdvisoryEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
This FAN event provides advice that directs load balancing for subscribers.

[LoadAdvisoryEvent.LoadStatus](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md) - Enum in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

## N

[NodeDownEvent](oracle/simplefan/NodeDownEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
The event posted when a node goes down.

[NodeUpEvent](oracle/simplefan/NodeUpEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
The event posted when a node gets UP.

[NodeUpEvent(Object, Date)](oracle/simplefan/NodeUpEvent.md) - Constructor for class oracle.simplefan.[NodeUpEvent](oracle/simplefan/NodeUpEvent.md)
 

## O

[oracle.simplefan](oracle/simplefan/package-summary.md) - package oracle.simplefan
Provides easy access to Oracle Fast Application Notification (FAN) events.

[oracle.simplefan.impl](oracle/simplefan/impl/package-summary.md) - package oracle.simplefan.impl
 

## R

[removeListener(FanEventListener)](oracle/simplefan/FanSubscription.md) - Method in interface oracle.simplefan.[FanSubscription](oracle/simplefan/FanSubscription.md)
Removes a listener.

## S

[ServiceDownEvent](oracle/simplefan/ServiceDownEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
A container that can hold both kinds of service events.

[ServiceDownEvent.EventKind](oracle/simplefan/ServiceDownEvent.EventKind.md) - Enum in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[ServiceDownEvent.Reason](oracle/simplefan/ServiceDownEvent.Reason.md) - Enum in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
The service member event that reflects the status change of a service on a particular instance (and node).

[ServiceMemberEvent()](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md) - Constructor for class oracle.simplefan.[ServiceDownEvent.ServiceMemberEvent](oracle/simplefan/ServiceDownEvent.ServiceMemberEvent.md)
 

[ServiceMemberEvent()](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) - Constructor for class oracle.simplefan.[ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md)
 

[ServiceUpEvent](oracle/simplefan/ServiceUpEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
A container that can hold both kinds of service events.

[ServiceUpEvent.EventKind](oracle/simplefan/ServiceUpEvent.EventKind.md) - Enum in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[ServiceUpEvent.Reason](oracle/simplefan/ServiceUpEvent.Reason.md) - Enum in [oracle.simplefan](oracle/simplefan/package-summary.md)
 

[ServiceUpEvent.ServiceMemberEvent](oracle/simplefan/ServiceUpEvent.ServiceMemberEvent.md) - Class in [oracle.simplefan](oracle/simplefan/package-summary.md)
The service member event that reflects the status change of a service on a particular instance (and node).

[subscribe(Properties)](oracle/simplefan/FanManager.md) - Method in class oracle.simplefan.[FanManager](oracle/simplefan/FanManager.md)
Creates a FanSubscription that retrieves FAN events using ONS.

[subscribe(Properties)](oracle/simplefan/impl/FanManager.md) - Method in class oracle.simplefan.impl.[FanManager](oracle/simplefan/impl/FanManager.md)
Creates a FanSubscription that retrieves FAN events using ONS.

## V

[valueOf(String)](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md) - Static method in enum oracle.simplefan.[LoadAdvisoryEvent.LoadStatus](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md)
Returns the enum constant of this type with the specified name.

[valueOf(String)](oracle/simplefan/ServiceDownEvent.EventKind.md) - Static method in enum oracle.simplefan.[ServiceDownEvent.EventKind](oracle/simplefan/ServiceDownEvent.EventKind.md)
Returns the enum constant of this type with the specified name.

[valueOf(String)](oracle/simplefan/ServiceDownEvent.Reason.md) - Static method in enum oracle.simplefan.[ServiceDownEvent.Reason](oracle/simplefan/ServiceDownEvent.Reason.md)
Returns the enum constant of this type with the specified name.

[valueOf(String)](oracle/simplefan/ServiceUpEvent.EventKind.md) - Static method in enum oracle.simplefan.[ServiceUpEvent.EventKind](oracle/simplefan/ServiceUpEvent.EventKind.md)
Returns the enum constant of this type with the specified name.

[valueOf(String)](oracle/simplefan/ServiceUpEvent.Reason.md) - Static method in enum oracle.simplefan.[ServiceUpEvent.Reason](oracle/simplefan/ServiceUpEvent.Reason.md)
Returns the enum constant of this type with the specified name.

[values()](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md) - Static method in enum oracle.simplefan.[LoadAdvisoryEvent.LoadStatus](oracle/simplefan/LoadAdvisoryEvent.LoadStatus.md)
Returns an array containing the constants of this enum type, in the order they are declared.

[values()](oracle/simplefan/ServiceDownEvent.EventKind.md) - Static method in enum oracle.simplefan.[ServiceDownEvent.EventKind](oracle/simplefan/ServiceDownEvent.EventKind.md)
Returns an array containing the constants of this enum type, in the order they are declared.

[values()](oracle/simplefan/ServiceDownEvent.Reason.md) - Static method in enum oracle.simplefan.[ServiceDownEvent.Reason](oracle/simplefan/ServiceDownEvent.Reason.md)
Returns an array containing the constants of this enum type, in the order they are declared.

[values()](oracle/simplefan/ServiceUpEvent.EventKind.md) - Static method in enum oracle.simplefan.[ServiceUpEvent.EventKind](oracle/simplefan/ServiceUpEvent.EventKind.md)
Returns an array containing the constants of this enum type, in the order they are declared.

[values()](oracle/simplefan/ServiceUpEvent.Reason.md) - Static method in enum oracle.simplefan.[ServiceUpEvent.Reason](oracle/simplefan/ServiceUpEvent.Reason.md)
Returns an array containing the constants of this enum type, in the order they are declared.

A C F G H L N O R S V 

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
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
