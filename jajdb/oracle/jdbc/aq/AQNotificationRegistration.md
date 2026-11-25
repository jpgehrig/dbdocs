Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQNotificationListener.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.jdbc.aq

## Interface AQNotificationRegistration

- All Superinterfaces:
  [NotificationRegistration](../NotificationRegistration.md)

  ------------------------------------------------------------------------



      public interface AQNotificationRegistration
      extends NotificationRegistration

  This class represents your interest in being notified when a new message is enqueued in a particular queue. This feature is called AQ asynchronous notification.
  You retrieve an instance or multiple instances of this class by calling the method `registerAQNotification` on the connection.

  Code example:

           Properties globalOptions = new Properties();
           // Here we register our interest into one single-consumer
           // queue called "SCOTT.MY_RAW_QUEUE" which needs to be properly
           // created and started:
           String[] queueNameArr = new String[1];
           queueNameArr[0] = "SCOTT.MY_RAW_QUEUE";
           Properties[] opt = new Properties[1];
           opt[0] = new Properties();
           // we want to retrieve the payload within the notification:
           opt[0].setProperty(OracleConnection.NTF_AQ_PAYLOAD,"true");
           // 'conn' is a valid instance of OracleConnection:
           AQNotificationRegistration[] regArr
             = conn.registerAQNotification(queueNameArr,opt,globalOptions);
           AQNotificationRegistration reg = regArr[0];
           // listener is an instance of AQNotificationListener:
           reg.addListener(listener);


<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[NotificationRegistration](../NotificationRegistration.md)

      [`NotificationRegistration.RegistrationState`](../NotificationRegistration.RegistrationState.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                          | `addListener``(`[`AQNotificationListener`](AQNotificationListener.md)` listener)`                                                                                                                      |
    | `void`                                                                                          | `addListener``(`[`AQNotificationListener`](AQNotificationListener.md)` listener, `[`Executor`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/Executor.html?is-external=true)` e)`  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getQueueName``()`<br>Returns the name of the queue for which we have register our interest in being notified.                                                                                         |
    | `void`                                                                                          | `removeListener``(`[`AQNotificationListener`](AQNotificationListener.md)` listener)`                                                                                                                   |

    - ### Methods inherited from interface oracle.jdbc.[NotificationRegistration](../NotificationRegistration.md)

      [`getDatabaseName`](../NotificationRegistration.md)`, `[`getRegistrationException`](../NotificationRegistration.md)`, `[`getRegistrationOptions`](../NotificationRegistration.md)`, `[`getState`](../NotificationRegistration.md)`, `[`getUserName`](../NotificationRegistration.md)

<!-- -->

- - ### Method Detail

    - #### addListener

          void addListener(AQNotificationListener listener)
                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### addListener

          void addListener(AQNotificationListener listener,
                           Executor e)
                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### removeListener

          void removeListener(AQNotificationListener listener)
                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getQueueName

          String getQueueName()

      Returns the name of the queue for which we have register our interest in being notified.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQNotificationListener.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
