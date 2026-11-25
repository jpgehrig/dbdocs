Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEConnectivityRule.md)
- [Next Class](NFELineLineRule.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.rule

## Enum NFEConnectivityRule.ConnectivityRuleType

- java.lang.Object

- - java.lang.Enum\<NFEConnectivityRule.ConnectivityRuleType\>

  - - oracle.spatial.network.nfe.model.rule.NFEConnectivityRule.ConnectivityRuleType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<NFEConnectivityRule.ConnectivityRuleType\>

  <!-- -->

  Enclosing class:
  [NFEConnectivityRule](NFEConnectivityRule.md)

  ------------------------------------------------------------------------



      public static enum NFEConnectivityRule.ConnectivityRuleType
      extends java.lang.Enum<NFEConnectivityRule.ConnectivityRuleType>

  Defines connectivity rule types

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description        |
    |--------------------------------------|
    | `LINE_LINE`<br>Line-line rule type   |
    | `LINE_POINT`<br>Line-point rule type |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                       |
    |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static NFEConnectivityRule.ConnectivityRuleType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static NFEConnectivityRule.ConnectivityRuleType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### LINE_LINE

          public static final NFEConnectivityRule.ConnectivityRuleType LINE_LINE

      Line-line rule type

    <!-- -->

    - #### LINE_POINT

          public static final NFEConnectivityRule.ConnectivityRuleType LINE_POINT

      Line-point rule type

  <!-- -->

  - ### Method Detail

    - #### values

          public static NFEConnectivityRule.ConnectivityRuleType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (NFEConnectivityRule.ConnectivityRuleType c : NFEConnectivityRule.ConnectivityRuleType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static NFEConnectivityRule.ConnectivityRuleType valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEConnectivityRule.md)
- [Next Class](NFELineLineRule.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
