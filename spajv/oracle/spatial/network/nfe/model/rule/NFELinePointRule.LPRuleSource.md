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

- [Prev Class](NFELinePointRule.md)
- [Next Class](NFERuleInstance.md)

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

## Enum NFELinePointRule.LPRuleSource

- java.lang.Object

- - java.lang.Enum\<NFELinePointRule.LPRuleSource\>

  - - oracle.spatial.network.nfe.model.rule.NFELinePointRule.LPRuleSource

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<NFELinePointRule.LPRuleSource\>

  <!-- -->

  Enclosing class:
  [NFELinePointRule](NFELinePointRule.md)

  ------------------------------------------------------------------------



      public static enum NFELinePointRule.LPRuleSource
      extends java.lang.Enum<NFELinePointRule.LPRuleSource>

  Defines different sources where a line-point could be created

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                        |
    |------------------------------------------------------|
    | `LLRULE`<br>The rule was created by a line-line rule |
    | `USER`<br>The rule was created by a user             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                       |
    |------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `int`                                    | `getOrdinal``()`                                                                                             |
    | `static NFELinePointRule.LPRuleSource`   | `valueOf``(int value)`                                                                                       |
    | `static NFELinePointRule.LPRuleSource`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static NFELinePointRule.LPRuleSource[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### USER

          public static final NFELinePointRule.LPRuleSource USER

      The rule was created by a user

    <!-- -->

    - #### LLRULE

          public static final NFELinePointRule.LPRuleSource LLRULE

      The rule was created by a line-line rule

  <!-- -->

  - ### Method Detail

    - #### values

          public static NFELinePointRule.LPRuleSource[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (NFELinePointRule.LPRuleSource c : NFELinePointRule.LPRuleSource.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static NFELinePointRule.LPRuleSource valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

    <!-- -->

    - #### getOrdinal

          public int getOrdinal()

    <!-- -->

    - #### valueOf

          public static NFELinePointRule.LPRuleSource valueOf(int value)

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

- [Prev Class](NFELinePointRule.md)
- [Next Class](NFERuleInstance.md)

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
