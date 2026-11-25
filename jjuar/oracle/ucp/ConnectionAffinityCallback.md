Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionAffinityCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](AbandonedConnectionTimeoutCallback.md)
- [Next Class](ConnectionAffinityCallback.AffinityPolicy.md)

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

oracle.ucp

## Interface ConnectionAffinityCallback

-

  ------------------------------------------------------------------------



      public interface ConnectionAffinityCallback

  The callback interface for the Oracle RAC affinity features. Oracle RAC affinity features allow related connection requests to be directed to the same Oracle RAC instance within a certain period of time, in order to achieve better overall performance. UCP supports two Oracle RAC affinity policies: *transaction-based affinity* and *web-session-based affinity*.
  Transaction-based affinity allows applications to group connection requests to the same Oracle RAC instance based on their semantical correlation. Connection requests within the same distributed transaction are directed to the same Oracle RAC instance when possible.

  Web-session affinity directs connection requests originated by the same Web-session to the same Oracle RAC instance when possible.

  This interface allows the Universal Connection Pool to establish and retrieve connection affinity context inside its application in order to return appropriate connections that satisfy Oracle RAC affinity requirements. The interface also allows applications to inform the pool of their choice of the connection affinity policy.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                               |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`ConnectionAffinityCallback.AffinityPolicy`](ConnectionAffinityCallback.AffinityPolicy.md)<br>The Enum AffinityPolicy. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                            |
    |---------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConnectionAffinityCallback.AffinityPolicy`](ConnectionAffinityCallback.AffinityPolicy.md) | `getAffinityPolicy``()`<br>Obtains the current affinity policy from this callback.                                                                                                |
    | `java.lang.Object`                                                                          | `getConnectionAffinityContext``()`<br>Obtains the connection affinity context object from UCP application.                                                                        |
    | `void`                                                                                      | `setAffinityPolicy``(`[`ConnectionAffinityCallback.AffinityPolicy`](ConnectionAffinityCallback.AffinityPolicy.md)` policy)`<br>Sets the affinity policy to use for this callback. |
    | `boolean`                                                                                   | `setConnectionAffinityContext``(java.lang.Object affinityContext)`<br>Sets the connection affinity context object inside UCP application.                                         |

<!-- -->

- - ### Method Detail

    - #### setConnectionAffinityContext

          boolean setConnectionAffinityContext(java.lang.Object affinityContext)

      Sets the connection affinity context object inside UCP application.
      Parameters:
      `affinityContext` - Connection Affinity Context object.

      Returns:
      `true` if Affinity Context is successfully set; `false` otherwise.

    <!-- -->

    - #### getConnectionAffinityContext

          java.lang.Object getConnectionAffinityContext()

      Obtains the connection affinity context object from UCP application.
      Returns:
      Connection Affinity Context object.

    <!-- -->

    - #### setAffinityPolicy

          void setAffinityPolicy(ConnectionAffinityCallback.AffinityPolicy policy)

      Sets the affinity policy to use for this callback.
      Parameters:
      `policy` - The affinity policy to use.

    <!-- -->

    - #### getAffinityPolicy

          ConnectionAffinityCallback.AffinityPolicy getAffinityPolicy()

      Obtains the current affinity policy from this callback.
      Returns:
      The affinity policy set for this callback.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionAffinityCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](AbandonedConnectionTimeoutCallback.md)
- [Next Class](ConnectionAffinityCallback.AffinityPolicy.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
