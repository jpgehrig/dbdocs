Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionAffinityCallback.AffinityPolicy.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionAffinityCallback.md)
- [Next Class](ConnectionFactoryAdapter.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

oracle.ucp

## Enum ConnectionAffinityCallback.AffinityPolicy

- java.lang.Object

- - java.lang.Enum\<ConnectionAffinityCallback.AffinityPolicy\>

  - - oracle.ucp.ConnectionAffinityCallback.AffinityPolicy

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<ConnectionAffinityCallback.AffinityPolicy\>

  <!-- -->

  Enclosing interface:
  [ConnectionAffinityCallback](ConnectionAffinityCallback.md)

  ------------------------------------------------------------------------



      public static enum ConnectionAffinityCallback.AffinityPolicy
      extends java.lang.Enum<ConnectionAffinityCallback.AffinityPolicy>

  The Enum AffinityPolicy.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                   |
    |-----------------------------------------------------------------|
    | `DATA_BASED_AFFINITY`<br>The data based affinity.               |
    | `TRANSACTION_BASED_AFFINITY`<br>The transaction based affinity. |
    | `WEBSESSION_BASED_AFFINITY`<br>The websession based affinity.   |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                    | Method and Description                                                                                       |
    |------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static ConnectionAffinityCallback.AffinityPolicy`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static ConnectionAffinityCallback.AffinityPolicy[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `clone, compareTo, equals, finalize, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### WEBSESSION_BASED_AFFINITY

          public static final ConnectionAffinityCallback.AffinityPolicy WEBSESSION_BASED_AFFINITY

      The websession based affinity.

    <!-- -->

    - #### TRANSACTION_BASED_AFFINITY

          public static final ConnectionAffinityCallback.AffinityPolicy TRANSACTION_BASED_AFFINITY

      The transaction based affinity.

    <!-- -->

    - #### DATA_BASED_AFFINITY

          public static final ConnectionAffinityCallback.AffinityPolicy DATA_BASED_AFFINITY

      The data based affinity.

  <!-- -->

  - ### Method Detail

    - #### values

          public static ConnectionAffinityCallback.AffinityPolicy[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (ConnectionAffinityCallback.AffinityPolicy c : ConnectionAffinityCallback.AffinityPolicy.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static ConnectionAffinityCallback.AffinityPolicy valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionAffinityCallback.AffinityPolicy.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionAffinityCallback.md)
- [Next Class](ConnectionFactoryAdapter.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

Copyright © 2007, 2022, Oracle and/or its affiliates.
