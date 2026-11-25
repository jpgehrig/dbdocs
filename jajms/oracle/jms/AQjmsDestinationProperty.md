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

- [Prev Class](AQjmsDestinationFactory.md)
- [Next Class](AQjmsException.md)

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

## Class AQjmsDestinationProperty

- java.lang.Object

- - oracle.AQ.AQQueueProperty

  - - oracle.jms.AQjmsDestinationProperty

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class AQjmsDestinationProperty
      extends oracle.AQ.AQQueueProperty

  This is an Oracle class which extends `oracle.jms.AQQueueProperty`. Oracle® Database Advanced Queuing specific queue properties.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.AQ.AQQueueProperty

      `EXCEPTION_QUEUE, INFINITE, NORMAL_QUEUE, type`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AQjmsDestinationProperty``()`<br>Constructor - initializes object with default destination properties.                                                                                                    |
    | `AQjmsDestinationProperty``(oracle.AQ.AQQueueProperty aqProp)`<br>Constructor - initializes object with a combination of default destination properties and properties provided by the `aqProp` parameter. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.AQ.AQQueueProperty

      `getComment, getMaxRetries, getQueueType, getRetentionTime, getRetryInterval, isSharded, setComment, setMaxRetries, setMaxRetries, setQueueType, setRetentionTime, setRetentionTime, setRetryInterval, setRetryInterval, setSharded, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsDestinationProperty

          public AQjmsDestinationProperty()

      Constructor - initializes object with default destination properties.

    <!-- -->

    - #### AQjmsDestinationProperty

          public AQjmsDestinationProperty(oracle.AQ.AQQueueProperty aqProp)

      Constructor - initializes object with a combination of default destination properties and properties provided by the `aqProp` parameter.
      Parameters:
      `aqProp` - provides the following properties:

      - `QueueType`
      - `MaxRetries`
      - `RetryInterval`
      - `RetentionTime`
      - `Comment`

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

- [Prev Class](AQjmsDestinationFactory.md)
- [Next Class](AQjmsException.md)

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
