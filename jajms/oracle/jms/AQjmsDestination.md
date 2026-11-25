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

- [Prev Class](AQjmsConsumer.md)
- [Next Class](AQjmsDestinationFactory.md)

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

oracle.jms

## Class AQjmsDestination

- java.lang.Object

- - oracle.jms.AQjmsDestination

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [Destination](../../javax/jms/Destination.md), [Queue](../../javax/jms/Queue.md), [TemporaryQueue](../../javax/jms/TemporaryQueue.md), [TemporaryTopic](../../javax/jms/TemporaryTopic.md), [Topic](../../javax/jms/Topic.md)

  ------------------------------------------------------------------------



      public class AQjmsDestination
      extends java.lang.Object
      implements Queue, Topic, java.io.Serializable, TemporaryQueue, TemporaryTopic

  This is an Oracle class which implements `javax.jms.Queue`, `javax.jms.Topic` and `java.io.Serializable`.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                                                                     |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `alter``(`[`Session`](../../javax/jms/Session.md)` session, `[`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)` destinationProperty)`<br>Alters the properties of the queue/topic.                                                                                                                                 |
    | `void`             | `alterPropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.Double duration, java.lang.String nextTime, java.lang.Double latency)`<br>Alters the propagation schedule between the topic and the destination database.                                           |
    | `void`             | `alterPropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.String destQueue, java.lang.Double duration, java.lang.String nextTime, java.lang.Double latency)`<br>alter propapagation schedule between the topic and the destination database                   |
    | `void`             | `delete``()`<br>Delete this temporary destination and make it unusable for further operations.                                                                                                                                                                                                                             |
    | `void`             | `disablePropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination)`<br>Disables the propagation schedule.                                                                                                                                                                      |
    | `void`             | `disablePropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.String destQueue)`<br>disable propapagation schedule                                                                                                                                              |
    | `void`             | `drop``(`[`Session`](../../javax/jms/Session.md)` session)`<br>Drops the queue/topic, which is stoppped earlier to disable the queue/topic for both enqueuing and dequeuing.                                                                                                                                               |
    | `void`             | `enablePropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination)`<br>Enables the propagation schedule.                                                                                                                                                                        |
    | `void`             | `enablePropagationSchedule``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.String destQueue)`<br>enable propapagation schedule                                                                                                                                                |
    | `java.lang.String` | `getCompleteName``()`<br>Gets the complete name of the queue/topic in the form "\[schema.\]name".                                                                                                                                                                                                                          |
    | `java.lang.String` | `getCompleteTableName``()`<br>Gets the complete name of the queue table of the queue/topic in the form "\[schema.\]name".                                                                                                                                                                                                  |
    | `java.lang.String` | `getQueueName``()`<br>Gets the name of the queue.                                                                                                                                                                                                                                                                          |
    | `java.lang.String` | `getQueueOwner``()`<br>Gets the owner of the queue.                                                                                                                                                                                                                                                                        |
    | `java.lang.String` | `getTopicName``()`<br>Gets the name of the topic.                                                                                                                                                                                                                                                                          |
    | `java.lang.String` | `getTopicOwner``()`<br>Gets the schema of the topic.                                                                                                                                                                                                                                                                       |
    | `void`             | `grantQueuePrivilege``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String privilege, java.lang.String grantee, boolean grantOption)`<br>Grants enqueue or dequeue privilege on the queue to a database user.                                                                                              |
    | `void`             | `grantTopicPrivilege``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String privilege, java.lang.String grantee, boolean grantOption)`<br>Grants a topic privilege.                                                                                                                                         |
    | `void`             | `revokeQueuePrivilege``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String privilege, java.lang.String grantee)`<br>Revokes a queue privilege.                                                                                                                                                            |
    | `void`             | `revokeTopicPrivilege``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String privilege, java.lang.String grantee)`<br>Revokes a topic privilege.                                                                                                                                                            |
    | `void`             | `schedulePropagation``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.util.Date startTime, java.lang.Double duration, java.lang.String nextTime, java.lang.Double latency)`<br>Schedules propagation from the topic for the given destination database.                             |
    | `void`             | `schedulePropagation``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.String destQueue, java.util.Date startTime, java.lang.Double duration, java.lang.String nextTime, java.lang.Double latency)`<br>Schedule propapagation from the topic for the given destination database |
    | `void`             | `start``(`[`Session`](../../javax/jms/Session.md)` session, boolean enqueue, boolean dequeue)`<br>Starts the queue/topic for enqueue or dequeue or both.                                                                                                                                                                   |
    | `void`             | `start``(`[`Session`](../../javax/jms/Session.md)` session, boolean enqueue, boolean dequeue, boolean autonomous)`<br>Starts the queue/topic for enqueue or dequeue or both.                                                                                                                                               |
    | `void`             | `stop``(`[`Session`](../../javax/jms/Session.md)` session, boolean enqueue, boolean dequeue, boolean wait)`<br>Stops the queue/topic for enqueue or dequeue or both.                                                                                                                                                       |
    | `void`             | `stop``(`[`Session`](../../javax/jms/Session.md)` session, boolean enqueue, boolean dequeue, boolean wait, boolean autonomous)`<br>Stops the queue/topic for enqueue or dequeue or both.                                                                                                                                   |
    | `java.lang.String` | `toString``()`<br>Gets the queue/topic as a string, in the form "\[schema.\]name".                                                                                                                                                                                                                                         |
    | `void`             | `unschedulePropagation``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination)`<br>Unschedules propagation between the topic and the specified destination.                                                                                                                                     |
    | `void`             | `unschedulePropagation``(`[`Session`](../../javax/jms/Session.md)` session, java.lang.String destination, java.lang.String destQueue)`<br>Unschedule propapagation between the topic and the specified destination                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getQueueName

          public java.lang.String getQueueName()
                                        throws JMSException

      Gets the name of the queue.
      Specified by:
      [`getQueueName`](../../javax/jms/Queue.md) in interface [`Queue`](../../javax/jms/Queue.md)

      Returns:
      the name of the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue is not a single consumer queue.

    <!-- -->

    - #### getTopicName

          public java.lang.String getTopicName()
                                        throws JMSException

      Gets the name of the topic.
      Specified by:
      [`getTopicName`](../../javax/jms/Topic.md) in interface [`Topic`](../../javax/jms/Topic.md)

      Returns:
      the name of the topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue is not a multi consumer queue (topic).

    <!-- -->

    - #### getQueueOwner

          public java.lang.String getQueueOwner()
                                         throws JMSException

      Gets the owner of the queue.
      Returns:
      the schema of the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the schema could not be retrieved.

    <!-- -->

    - #### getTopicOwner

          public java.lang.String getTopicOwner()
                                         throws JMSException

      Gets the schema of the topic.
      Returns:
      the schema of the topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the schema could not be retrieved.

    <!-- -->

    - #### getCompleteName

          public java.lang.String getCompleteName()

      Gets the complete name of the queue/topic in the form "\[schema.\]name".
      Returns:
      the complete name of the queue/topic

    <!-- -->

    - #### getCompleteTableName

          public java.lang.String getCompleteTableName()

      Gets the complete name of the queue table of the queue/topic in the form "\[schema.\]name".
      Returns:
      the complete name of the queue/topic's queue table

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Gets the queue/topic as a string, in the form "\[schema.\]name".
      Specified by:
      [`toString`](../../javax/jms/Queue.md) in interface [`Queue`](../../javax/jms/Queue.md)

      Specified by:
      [`toString`](../../javax/jms/Topic.md) in interface [`Topic`](../../javax/jms/Topic.md)

      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      the queue/topic as a string

    <!-- -->

    - #### start

          public void start(Session session,
                            boolean enqueue,
                            boolean dequeue)
                     throws JMSException

      Starts the queue/topic for enqueue or dequeue or both.
      The start operation is not performed as an autonomous transaction.

      Parameters:
      `session` - the jms session

      `enqueue` - whether enqueue should be enabled

      `dequeue` - whether dequeue should be enabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue/topic could not be started.

    <!-- -->

    - #### start

          public void start(Session session,
                            boolean enqueue,
                            boolean dequeue,
                            boolean autonomous)
                     throws JMSException

      Starts the queue/topic for enqueue or dequeue or both.
      Parameters:
      `session` - the jms session

      `enqueue` - whether enqueue should be enabled

      `dequeue` - whether dequeue should be enabled

      `autonomous` - whether the start operation should be performed as an autonomous transaction

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue/topic could not be started.

    <!-- -->

    - #### stop

          public void stop(Session session,
                           boolean enqueue,
                           boolean dequeue,
                           boolean wait)
                    throws JMSException

      Stops the queue/topic for enqueue or dequeue or both.
      The stop operation is not performed as an autonomous transaction.

      Parameters:
      `session` - the jms session

      `enqueue` - whether enqueue should be disabled

      `dequeue` - whether dequeue should be disabled

      `wait` - whether to wait for pending transactions on the queue/topic to complete

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue/topic could not be stopped.

    <!-- -->

    - #### stop

          public void stop(Session session,
                           boolean enqueue,
                           boolean dequeue,
                           boolean wait,
                           boolean autonomous)
                    throws JMSException

      Stops the queue/topic for enqueue or dequeue or both.
      Parameters:
      `session` - the jms session

      `enqueue` - whether enqueue should be disabled

      `dequeue` - whether dequeue should be disabled

      `wait` - whether to wait for pending transactions on the queue/topic to complete

      `autonomous` - whether the stop operation should be performed as an autonomous transaction

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue/topic could not be stopped.

    <!-- -->

    - #### alter

          public void alter(Session session,
                            AQjmsDestinationProperty destinationProperty)
                     throws JMSException

      Alters the properties of the queue/topic.
      Parameters:
      `session` - the jms session

      `destinationProperty` - the new properties of the queue/topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the properties could not be altered.

    <!-- -->

    - #### drop

          public void drop(Session session)
                    throws JMSException

      Drops the queue/topic, which is stoppped earlier to disable the queue/topic for both enqueuing and dequeuing.
      Parameters:
      `session` - the jms session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue/topic could not be dropped.

    <!-- -->

    - #### schedulePropagation

          public void schedulePropagation(Session session,
                                          java.lang.String destination,
                                          java.util.Date startTime,
                                          java.lang.Double duration,
                                          java.lang.String nextTime,
                                          java.lang.Double latency)
                                   throws JMSException

      Schedules propagation from the topic for the given destination database.
      Parameters:
      `session` - the JMS session

      `destination` - the dblink of the remote database for which propagation is being scheduled. A `null` string means that propagation will be scheduled for all subscribers in the local database of the topic

      `startTime` - the time propagation must be started

      `duration` - the duration of propagation

      `nextTime` - the next time propagation must be done

      `latency` - the latency in seconds that can be tolerated (Latency is the difference between the time a message was enqueued and the time it was propagated.)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if propagation could not be scheduled.

    <!-- -->

    - #### schedulePropagation

          public void schedulePropagation(Session session,
                                          java.lang.String destination,
                                          java.lang.String destQueue,
                                          java.util.Date startTime,
                                          java.lang.Double duration,
                                          java.lang.String nextTime,
                                          java.lang.Double latency)
                                   throws JMSException

      Schedule propapagation from the topic for the given destination database
      Parameters:
      `session` - the JMS session

      `destination` - the dblink of the remote database for which propagation is being scheduled. A null string means that propagation will be scheduled for all subscribers in the local database of the topic

      `destQueue` - the name of the target queue

      `startTime` - the time propagation must be started

      `duration` - the duration of propagation

      `nextTime` - the next time propagation must be done

      `latency` - the latency in seconds that can be tolerated latency is the difference between the time a message was enqueued and the time it was propagated

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if propagation could not be scheduled

    <!-- -->

    - #### unschedulePropagation

          public void unschedulePropagation(Session session,
                                            java.lang.String destination)
                                     throws JMSException

      Unschedules propagation between the topic and the specified destination.
      Parameters:
      `session` - the jms session

      `destination` - the dblink of the destination database for which propagation must be unscheduled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if propagation could not be unscheduled.

    <!-- -->

    - #### unschedulePropagation

          public void unschedulePropagation(Session session,
                                            java.lang.String destination,
                                            java.lang.String destQueue)
                                     throws JMSException

      Unschedule propapagation between the topic and the specified destination
      Parameters:
      `session` - the jms session

      `destination` - the dblink of the destination database for which propagation must be unscheduled

      `destQueue` - the name of the target queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if propagation oculd not be unscheduled

    <!-- -->

    - #### alterPropagationSchedule

          public void alterPropagationSchedule(Session session,
                                               java.lang.String destination,
                                               java.lang.Double duration,
                                               java.lang.String nextTime,
                                               java.lang.Double latency)
                                        throws JMSException

      Alters the propagation schedule between the topic and the destination database.
      Parameters:
      `session` - the jms session

      `destination` - the dblink of the destination database

      `duration` - the new duration

      `nextTime` - the new next-time for propagation

      `latency` - the new latency

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the schedule could not be altered.

    <!-- -->

    - #### alterPropagationSchedule

          public void alterPropagationSchedule(Session session,
                                               java.lang.String destination,
                                               java.lang.String destQueue,
                                               java.lang.Double duration,
                                               java.lang.String nextTime,
                                               java.lang.Double latency)
                                        throws JMSException

      alter propapagation schedule between the topic and the destination database
      Parameters:
      `session` - the jms session

      `destination` - the dblink of the destination database

      `destQueue` - the name of the target queue

      `duration` - the new duration

      `nextTime` - the new nextTime for propagation

      `latency` - the new latency

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the schedule could not be altered

    <!-- -->

    - #### enablePropagationSchedule

          public void enablePropagationSchedule(Session session,
                                                java.lang.String destination)
                                         throws JMSException

      Enables the propagation schedule.
      Parameters:
      `session` - the JMS session

      `destination` - the dblink of the destination database

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the propagation could not be enabled.

    <!-- -->

    - #### enablePropagationSchedule

          public void enablePropagationSchedule(Session session,
                                                java.lang.String destination,
                                                java.lang.String destQueue)
                                         throws JMSException

      enable propapagation schedule
      Parameters:
      `session` - the JMS session

      `destination` - the dblink of the destination database

      `destQueue` - the name of the target queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the propagation could not be enabled

    <!-- -->

    - #### disablePropagationSchedule

          public void disablePropagationSchedule(Session session,
                                                 java.lang.String destination)
                                          throws JMSException

      Disables the propagation schedule.
      Parameters:
      `session` - the jms session

      `destination` - the dblink to the destination database

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the propagation schedule could not be disabled.

    <!-- -->

    - #### disablePropagationSchedule

          public void disablePropagationSchedule(Session session,
                                                 java.lang.String destination,
                                                 java.lang.String destQueue)
                                          throws JMSException

      disable propapagation schedule
      Parameters:
      `session` - the jms session

      `destination` - the dblink to the destination database

      `destQueue` - the name of the target queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the propagation schedule could not be disabled

    <!-- -->

    - #### grantQueuePrivilege

          public void grantQueuePrivilege(Session session,
                                          java.lang.String privilege,
                                          java.lang.String grantee,
                                          boolean grantOption)
                                   throws JMSException

      Grants enqueue or dequeue privilege on the queue to a database user.
      Parameters:
      `session` - the jms session

      `privilege` - the privilege (`"ENQUEUE"` or `"DEQUEUE"</code">)`

      `grantee`` - the user being granted the privilege`

      `grantOption` - whether the grantee can grant the privilege to others

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the privilege could not be granted.

    <!-- -->

    - #### grantTopicPrivilege

          public void grantTopicPrivilege(Session session,
                                          java.lang.String privilege,
                                          java.lang.String grantee,
                                          boolean grantOption)
                                   throws JMSException

      Grants a topic privilege.
      Parameters:
      `session` - the jms session

      `privilege` - the privilege (`"ENQUEUE"` or `"DEQUEUE"</code">) being granted`

      `grantee`` - the database user being granted the privilege`

      `grantOption` - whether the grantee can grant the privilege to other users

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the privilege could not be granted.

    <!-- -->

    - #### revokeQueuePrivilege

          public void revokeQueuePrivilege(Session session,
                                           java.lang.String privilege,
                                           java.lang.String grantee)
                                    throws JMSException

      Revokes a queue privilege.
      Parameters:
      `session` - the jms session

      `privilege` - the privilege (`"ENQUEUE"` or `"DEQUEUE"</code">) being revoked`

      `grantee`` - the database user from whom the privilege is being revoked`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the privilege could not be revoked.

    <!-- -->

    - #### revokeTopicPrivilege

          public void revokeTopicPrivilege(Session session,
                                           java.lang.String privilege,
                                           java.lang.String grantee)
                                    throws JMSException

      Revokes a topic privilege.
      Parameters:
      `session` - the jms session

      `privilege` - the privilege (`"ENQUEUE"` or `"DEQUEUE"</code">) being revoked`

      `grantee`` - the database user from whom the privilege is being revoked`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the privilege could not be revoked.

    <!-- -->

    - #### delete

          public void delete()
                      throws JMSException

      Delete this temporary destination and make it unusable for further operations.
      Specified by:
      [`delete`](../../javax/jms/TemporaryQueue.md) in interface [`TemporaryQueue`](../../javax/jms/TemporaryQueue.md)

      Specified by:
      [`delete`](../../javax/jms/TemporaryTopic.md) in interface [`TemporaryTopic`](../../javax/jms/TemporaryTopic.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to delete the temporary queue due to some internal error.

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

- [Prev Class](AQjmsConsumer.md)
- [Next Class](AQjmsDestinationFactory.md)

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
