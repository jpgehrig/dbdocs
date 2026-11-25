Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](FanEventListener.md)
- [Next Class](FanSubscription.md)

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

oracle.simplefan

## Class FanManager

- java.lang.Object

- - oracle.simplefan.FanManager

<!-- -->

- Direct Known Subclasses:
  [FanManager](impl/FanManager.md)

  ------------------------------------------------------------------------



      public abstract class FanManager
      extends java.lang.Object

  An instance of this class is used to manage access to FAN events. FAN events are available only when using Oracle Real Application Clusters (Oracle RAC). This package provides simplified access to a subset of the FAN events. The supported events are:
  - Load Balancing Advisory
  - Service Member Down
  - Service Composite Down
  - Node Down

  This subset of events is suitable for implementing a JDBC connection cache that takes advantage of Oracle RAC capabilities.
  The current implementation of this package depends on the Oracle ONS message transport mechanism. You must configure your system, servers, and clients to use ONS before you can use this package. Future versions may use other transport mechanisms and so require different configuration values.

  An instance of this class can optionally be configured once. If it is configured, it must be configured before any subscriptions are created. If it is not configured, then ONS must be configured using the \$ORACLE_HOME/conf/opmn/ons.config file. Instructions for configuring ONS can be found in the Oracle JDBC Developer's Guide chapter on Fast Connection Failover.

  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/FanManager.java /main/3 2014/12/10 09:50:33 tzhou Exp \$

  Author:
  dsurber

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                      |
    |----------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | `abstract void`                                    | `configure``(java.util.Properties props)`<br>Configures the event daemon.                                   |
    | `static FanManager`                                | `getInstance``()`<br>Gets an instance of the concrete implementation class.                                 |
    | `abstract `[`FanSubscription`](FanSubscription.md) | `subscribe``(java.util.Properties props)`<br>Creates a FanSubscription that retrieves FAN events using ONS. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getInstance

          public static final FanManager getInstance()

      Gets an instance of the concrete implementation class.
      Returns:
      An instance of the concrete class.

    <!-- -->

    - #### configure

          public abstract void configure(java.util.Properties props)

      Configures the event daemon. Calling this method is optional. If called, it must be called only once and it must be called before any calls to subscribe. The argument is not captured. If not called, the event daemon must be configured using some other mechanism, specific to the daemon used. The only supported daemon is ONS in the initial release. The following properties are supported. All are required.
      onsNodes
      A comma separated list of host:port pairs of ONS daemons with which the ONS runtime in this Java VM should communicate.

      onsWalletFile
      The path name of the ONS wallet file.

      onsWalletPassword
      The password for accessing the ONS wallet file.

      <!-- -->

      Parameters:
      `props` - Properties that configure the event daemon.

      Throws:
      `java.lang.IllegalArgumentException` - if the props are unrecognized.

      `java.lang.IllegalStateException` - if it has been called previously or if subscribe has been called previously.

      `java.security.AccessControlException` - if the caller does not have oracle.ons.CreatePermission.

    <!-- -->

    - #### subscribe

          public abstract FanSubscription subscribe(java.util.Properties props)

      Creates a FanSubscription that retrieves FAN events using ONS. The argument is not captured. The return value is retained. The following property is supported and required.
      serviceName
      The Oracle database service name for which you want to get events.

      Each call creates a new instance, even if the properties are the same. Creating multiple instances with the same properties will have unpredictable results and is not supported. As one instance can support multiple listeners, there is no reason to create multiple instances for a given set of properties.
      Parameters:
      `props` - Properties that define the events to retrieve.

      Returns:
      a FanSubscription for the specified events.

      Throws:
      `java.lang.IllegalArgumentException` - if the properties do not specify a valid subscription.

      `java.lang.IllegalStateException` - if the daemon has not been properly initialized.

      `java.security.AccessControlException` - if the caller does not have oracle.ons.SubscribePermission.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](FanEventListener.md)
- [Next Class](FanSubscription.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
