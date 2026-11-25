Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolLifeCycleState.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolException.md)
- [Next Class](UniversalConnectionPoolStatistics.md)

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

## Class UniversalConnectionPoolLifeCycleState

- java.lang.Object

- - oracle.ucp.UniversalConnectionPoolLifeCycleState

<!-- -->

-

  ------------------------------------------------------------------------



      public class UniversalConnectionPoolLifeCycleState
      extends java.lang.Object

  Type-safe Life Cycle values for the connection pool. A connection pool has a lifecycle. The connection pool only hands out connections when it is in a started state. A connection pool has the following lifecycle states:
  - *Starting* Indicates that the connection pool's start method has been called and it is in the process of starting up.
  - *Started* Indicates that the connection pool has been started and is ready to hand out connections.
  - *Stopping* Indicates that the connection pool is in the process of stopping.
  - *Stopped* Indicates that the connection pool is stopped.
  - *Failed* Indicates that the connection pool has encountered failures during starting, stopping, or execution.

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                              | Field and Description                                                            |
    |------------------------------------------------|----------------------------------------------------------------------------------|
    | `static UniversalConnectionPoolLifeCycleState` | `LIFE_CYCLE_FAILED`<br>Connection pool has failed.                               |
    | `static java.lang.String`                      | `LIFE_CYCLE_FAILED_DESC`                                                         |
    | `static UniversalConnectionPoolLifeCycleState` | `LIFE_CYCLE_RUNNING`<br>Connection pool is started and can hand out connections. |
    | `static java.lang.String`                      | `LIFE_CYCLE_RUNNING_DESC`                                                        |
    | `static UniversalConnectionPoolLifeCycleState` | `LIFE_CYCLE_STARTING`<br>Connection pool is starting up.                         |
    | `static java.lang.String`                      | `LIFE_CYCLE_STARTING_DESC`                                                       |
    | `static UniversalConnectionPoolLifeCycleState` | `LIFE_CYCLE_STOPPED`<br>Connection pool is stopped.                              |
    | `static java.lang.String`                      | `LIFE_CYCLE_STOPPED_DESC`                                                        |
    | `static UniversalConnectionPoolLifeCycleState` | `LIFE_CYCLE_STOPPING`<br>Connection pool is stopping.                            |
    | `static java.lang.String`                      | `LIFE_CYCLE_STOPPING_DESC`                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                              |
    |--------------------|---------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object lifeCycleState)`<br>Determines equality. |
    | `protected int`    | `getState``()`<br>Returns the pool life cycle state.                |
    | `java.lang.String` | `toString``()`<br>Returns the pool lifecycle description.           |

    - ### Methods inherited from class java.lang.Object

      `clone, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LIFE_CYCLE_STARTING_DESC

          public static final java.lang.String LIFE_CYCLE_STARTING_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LIFE_CYCLE_RUNNING_DESC

          public static final java.lang.String LIFE_CYCLE_RUNNING_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LIFE_CYCLE_STOPPING_DESC

          public static final java.lang.String LIFE_CYCLE_STOPPING_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LIFE_CYCLE_STOPPED_DESC

          public static final java.lang.String LIFE_CYCLE_STOPPED_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LIFE_CYCLE_FAILED_DESC

          public static final java.lang.String LIFE_CYCLE_FAILED_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LIFE_CYCLE_STARTING

          public static final UniversalConnectionPoolLifeCycleState LIFE_CYCLE_STARTING

      Connection pool is starting up.

    <!-- -->

    - #### LIFE_CYCLE_RUNNING

          public static final UniversalConnectionPoolLifeCycleState LIFE_CYCLE_RUNNING

      Connection pool is started and can hand out connections.

    <!-- -->

    - #### LIFE_CYCLE_STOPPING

          public static final UniversalConnectionPoolLifeCycleState LIFE_CYCLE_STOPPING

      Connection pool is stopping.

    <!-- -->

    - #### LIFE_CYCLE_STOPPED

          public static final UniversalConnectionPoolLifeCycleState LIFE_CYCLE_STOPPED

      Connection pool is stopped.

    <!-- -->

    - #### LIFE_CYCLE_FAILED

          public static final UniversalConnectionPoolLifeCycleState LIFE_CYCLE_FAILED

      Connection pool has failed.

  <!-- -->

  - ### Method Detail

    - #### equals

          public boolean equals(java.lang.Object lifeCycleState)

      Determines equality.
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `lifeCycleState` - The object to compare.

      Returns:
      true if this object is equal to the object passed in; otherwise, false.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Returns the pool lifecycle description.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      the pool lifecycle description.

    <!-- -->

    - #### getState

          protected int getState()

      Returns the pool life cycle state.
      Returns:
      the pool life cycle state.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolLifeCycleState.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolException.md)
- [Next Class](UniversalConnectionPoolStatistics.md)

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
