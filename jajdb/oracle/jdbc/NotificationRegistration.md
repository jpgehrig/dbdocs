Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NotificationRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionIdEventListener.md)
- [Next Class](NotificationRegistration.RegistrationState.md)

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

oracle.jdbc

## Interface NotificationRegistration

- All Known Subinterfaces:
  [AQNotificationRegistration](aq/AQNotificationRegistration.md), [DatabaseChangeRegistration](dcn/DatabaseChangeRegistration.md)

  ------------------------------------------------------------------------



      public interface NotificationRegistration

  This interface is extended by oracle.jdbc.aq.AQNotificationRegistration and oracle.jdbc.dcn.DatabaseChangeRegistration.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                      |
    |-------------------|------------------------------------------------------------------------------------------------|
    | `static class `   | [`NotificationRegistration.RegistrationState`](NotificationRegistration.RegistrationState.md)  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                       | Method and Description                                                     |
    |---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDatabaseName``()`                                                      |
    | [`Exception`](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)   | `getRegistrationException``()`<br>Gets any registration related exception. |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true) | `getRegistrationOptions``()`                                               |
    | [`NotificationRegistration.RegistrationState`](NotificationRegistration.RegistrationState.md)           | `getState``()`<br>Returns the state of this registration.                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getUserName``()`                                                          |

<!-- -->

- - ### Method Detail

    - #### getRegistrationOptions

          Properties getRegistrationOptions()

    <!-- -->

    - #### getDatabaseName

          String getDatabaseName()

    <!-- -->

    - #### getUserName

          String getUserName()

    <!-- -->

    - #### getState

          NotificationRegistration.RegistrationState getState()

      Returns the state of this registration. The returned value can be either `RegistrationState.ACTIVE` or `RegistrationState.CLOSED`.

    <!-- -->

    - #### getRegistrationException

          Exception getRegistrationException()

      Gets any registration related exception. The notification registration happens on a background thread. Therefore any error that occurs during the registration creation won't be thrown on the main user thread (for example an SSL error). This method can be called to get such errors.
      Returns:
      Registration exception if any otherwise null.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NotificationRegistration.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionIdEventListener.md)
- [Next Class](NotificationRegistration.RegistrationState.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
