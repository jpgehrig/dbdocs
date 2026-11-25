Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](DeliveryMode.md)
- [Next Class](ExceptionListener.md)

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

javax.jms

## Interface Destination

- All Known Subinterfaces:
  [Queue](Queue.md), [TemporaryQueue](TemporaryQueue.md), [TemporaryTopic](TemporaryTopic.md), [Topic](Topic.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsDestination](../../oracle/jms/AQjmsDestination.md)

  ------------------------------------------------------------------------



      public interface Destination

  A `Destination` object encapsulates a provider-specific address. The JMS API does not define a standard address syntax. Although a standard address syntax was considered, it was decided that the differences in address semantics between existing message-oriented middleware (MOM) products were too wide to bridge with a single syntax.
  Since `Destination` is an administered object, it may contain provider-specific configuration information in addition to its address.

  The JMS API also supports a client's use of provider-specific address names.

  `Destination` objects support concurrent use.

  A `Destination` object is a JMS administered object.

  JMS administered objects are objects containing configuration information that are created by an administrator and later used by JMS clients. They make it practical to administer the JMS API in the enterprise.

  Although the interfaces for administered objects do not explicitly depend on the Java Naming and Directory Interface (JNDI) API, the JMS API establishes the convention that JMS clients find administered objects by looking them up in a JNDI namespace.

  An administrator can place an administered object anywhere in a namespace. The JMS API does not define a naming policy.

  It is expected that JMS providers will provide the tools an administrator needs to create and configure administered objects in a JNDI namespace. JMS provider implementations of administered objects should implement the `javax.naming.Referenceable` and `java.io.Serializable` interfaces so that they can be stored in all JNDI naming contexts. In addition, it is recommended that these implementations follow the JavaBeans<sup>TM</sup> design patterns.

  This strategy provides several benefits:

  - It hides provider-specific details from JMS clients.
  - It abstracts JMS administrative information into objects in the Java programming language ("Java objects") that are easily organized and administered from a common management console.
  - Since there will be JNDI providers for all popular naming services, JMS providers can deliver one implementation of administered objects that will run everywhere.

  An administered object should not hold on to any remote resources. Its lookup should not use remote resources other than those used by the JNDI API itself.

  Clients should think of administered objects as local Java objects. Looking them up should not have any hidden side effects or use surprising amounts of local resources.

  See Also:
  [`Queue`](Queue.md), [`Topic`](Topic.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](DeliveryMode.md)
- [Next Class](ExceptionListener.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
