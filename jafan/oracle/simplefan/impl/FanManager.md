Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev Class
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

oracle.simplefan.impl

## Class FanManager

- java.lang.Object

- - [oracle.simplefan.FanManager](../FanManager.md)

  - - oracle.simplefan.impl.FanManager

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FanManager
      extends FanManager

  Since:
  release specific (what release of product did this appear in)

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/impl/FanManager.java /main/5 2015/09/09 23:06:27 vidnayak Exp \$

  Author:
  dsurber

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `FanManager``()`            |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                      |
    |--------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | `void`                                     | `configure``(java.util.Properties props)`<br>Configures the event daemon.                                   |
    | `static FanManager`                        | `getInstanceInternal``()`<br>Get an instance of the concrete implementation class.                          |
    | [`FanSubscription`](../FanSubscription.md) | `subscribe``(java.util.Properties props)`<br>Creates a FanSubscription that retrieves FAN events using ONS. |

    - ### Methods inherited from class oracle.simplefan.[FanManager](../FanManager.md)

      [`getInstance`](../FanManager.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FanManager

          public FanManager()

  <!-- -->

  - ### Method Detail

    - #### getInstanceInternal

          public static final FanManager getInstanceInternal()

      Get an instance of the concrete implementation class.
      Returns:
      An instance of the concrete class.

    <!-- -->

    - #### configure

          public final void configure(java.util.Properties props)

      Configures the event daemon. Calling this method is optional. If called, it must be called only once and it must be called before any calls to subscribe. The argument is not captured. If not called, the event daemon must be configured using some other mechanism, specific to the daemon used. The only supported daemon is ONS in the initial release.
      Specified by:
      [`configure`](../FanManager.md) in class [`FanManager`](../FanManager.md)

      Parameters:
      `props` - Properties that configure the event daemon.

      Throws:
      `java.lang.IllegalArgumentException` - if the props are unrecognized.

      `java.lang.IllegalStateException` - if it has been called previously or if subscribe has been called previously.

    <!-- -->

    - #### subscribe

          public final FanSubscription subscribe(java.util.Properties props)

      Creates a FanSubscription that retrieves FAN events using ONS. The argument is not captured. The return value is retained.
      Specified by:
      [`subscribe`](../FanManager.md) in class [`FanManager`](../FanManager.md)

      Parameters:
      `props` - Properties that define the events to retrieve.

      Returns:
      a FanSubscription for the specified events.

      Throws:
      `java.lang.IllegalArgumentException` - if the properties do not specify a valid subscription.

      `java.lang.IllegalStateException` - if the daemon is not properly initialized.

      `java.security.AccessControlException` - if the caller does not have oracle.ons.SubscribePermission.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- Prev Class
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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
