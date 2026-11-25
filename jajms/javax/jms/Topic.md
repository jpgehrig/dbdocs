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

- [Prev Class](TextMessage.md)
- [Next Class](TopicConnection.md)

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

## Interface Topic

- All Superinterfaces:
  [Destination](Destination.md)

  <!-- -->

  All Known Subinterfaces:
  [TemporaryTopic](TemporaryTopic.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsDestination](../../oracle/jms/AQjmsDestination.md)

  ------------------------------------------------------------------------



      public interface Topic
      extends Destination

  A `Topic` object encapsulates a provider-specific topic name. It is the way a client specifies the identity of a topic to JMS API methods. For those methods that use a `Destination` as a parameter, a `Topic` object may used as an argument . For example, a Topic can be used to create a `MessageConsumer` and a `MessageProducer` by calling:
  - `Session.CreateConsumer(Destination destination)`
  - `Session.CreateProducer(Destination destination)`

  Many publish/subscribe (pub/sub) providers group topics into hierarchies and provide various options for subscribing to parts of the hierarchy. The JMS API places no restriction on what a `Topic` object represents. It may be a leaf in a topic hierarchy, or it may be a larger part of the hierarchy.

  The organization of topics and the granularity of subscriptions to them is an important part of a pub/sub application's architecture. The JMS API does not specify a policy for how this should be done. If an application takes advantage of a provider-specific topic-grouping mechanism, it should document this. If the application is installed using a different provider, it is the job of the administrator to construct an equivalent topic architecture and create equivalent `Topic` objects.

  See Also:
  [`Session.createConsumer(Destination)`](Session.md), [`Session.createProducer(Destination)`](Session.md), [`TopicSession.createTopic(String)`](TopicSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                            |
    |--------------------|-------------------------------------------------------------------|
    | `java.lang.String` | `getTopicName``()`<br>Gets the name of this topic.                |
    | `java.lang.String` | `toString``()`<br>Returns a string representation of this object. |

<!-- -->

- - ### Method Detail

    - #### getTopicName

          java.lang.String getTopicName()
                                 throws JMSException

      Gets the name of this topic.
      Clients that depend upon the name are not portable.

      Returns:
      the topic name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider implementation of `Topic` fails to return the topic name due to some internal error.

    <!-- -->

    - #### toString

          java.lang.String toString()

      Returns a string representation of this object.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      the provider-specific identity values for this topic

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

- [Prev Class](TextMessage.md)
- [Next Class](TopicConnection.md)

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
