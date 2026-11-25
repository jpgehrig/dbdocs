Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeListener.md)
- [Next Class](QueryChangeDescription.md)

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

oracle.jdbc.dcn

## Interface DatabaseChangeRegistration

- All Superinterfaces:
  [NotificationRegistration](../NotificationRegistration.md)

  ------------------------------------------------------------------------



      public interface DatabaseChangeRegistration
      extends NotificationRegistration

  Since:
  11.1

  See Also:
  `oracle.jdbc.OracleStatement.setDatabaseChangeRegistration(oracle.jdbc.dcn.DatabaseChangeRegistration)`

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[NotificationRegistration](../NotificationRegistration.md)

      [`NotificationRegistration.RegistrationState`](../NotificationRegistration.RegistrationState.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                   | Method and Description                                                                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                              | `addListener``(`[`DatabaseChangeListener`](DatabaseChangeListener.md)` listener)`<br>Register a listener with this registration.                                                                                                                     |
    | `void`                                                                                              | `addListener``(`[`DatabaseChangeListener`](DatabaseChangeListener.md)` listener, `[`Executor`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/Executor.html?is-external=true)` e)`<br>Register a listener with this registration. |
    | `long`                                                                                              | `getRegId``()`<br>Returns the registration id provided by the database.                                                                                                                                                                              |
    | `int`                                                                                               | `getRegistrationId``()`<br>Deprecated. <br>This method is deprecated in 11.2. Use `getRegId()` instead.                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getTables``()`<br>Returns the name of the tables associated with this registration.                                                                                                                                                                 |
    | `void`                                                                                              | `removeListener``(`[`DatabaseChangeListener`](DatabaseChangeListener.md)` listener)`<br>Remove a listener from the list of registered listeners.                                                                                                     |

    - ### Methods inherited from interface oracle.jdbc.[NotificationRegistration](../NotificationRegistration.md)

      [`getDatabaseName`](../NotificationRegistration.md)`, `[`getRegistrationException`](../NotificationRegistration.md)`, `[`getRegistrationOptions`](../NotificationRegistration.md)`, `[`getState`](../NotificationRegistration.md)`, `[`getUserName`](../NotificationRegistration.md)

<!-- -->

- - ### Method Detail

    - #### getRegistrationId

          int getRegistrationId()

      Deprecated. This method is deprecated in 11.2. Use `getRegId()` instead.
      Returns the registration id provided by the database. this is the value as the value contained in column 'regid' in table 'USER_CHANGE_NOTIFICATION_REGS'.

    <!-- -->

    - #### getRegId

          long getRegId()

      Returns the registration id provided by the database. this is the value as the value contained in column 'regid' in table 'USER_CHANGE_NOTIFICATION_REGS'.

    <!-- -->

    - #### getTables

          String[] getTables()

      Returns the name of the tables associated with this registration.

    <!-- -->

    - #### addListener

          void addListener(DatabaseChangeListener listener)
                    throws SQLException

      Register a listener with this registration. The listener will be notified when an even occurs. You can register multiple listeners with this registration. The order in which they will be registered isn't guaranteed and may vary.
      Note that the listener's code will be executed in the thread owned by the driver.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### addListener

          void addListener(DatabaseChangeListener listener,
                           Executor e)
                    throws SQLException

      Register a listener with this registration. The listener will be notified when an even occurs. You can register multiple listeners with this registration. The order in which they will be registered isn't guaranteed and may vary.
      This method lets you control which thread will execute the listener's code when an event occurs by specifying an executor. You can provide your own executor which can for example use a pool of threads.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### removeListener

          void removeListener(DatabaseChangeListener listener)
                       throws SQLException

      Remove a listener from the list of registered listeners.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeListener.md)
- [Next Class](QueryChangeDescription.md)

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
