Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ShardingMetadata.SubKeyMetadata.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ShardingMetadata.ShardingType.md)
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

oracle.jdbc.pool

## Class ShardingMetadata.SubKeyMetadata

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.pool.ShardingMetadata.SubKeyMetadata

<!-- -->

- All Implemented Interfaces:
  [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<ShardingMetadata.SubKeyMetadata\>

  <!-- -->

  Enclosing class:
  [ShardingMetadata](ShardingMetadata.md)

  ------------------------------------------------------------------------



      public static class ShardingMetadata.SubKeyMetadata
      extends Object
      implements Comparable<ShardingMetadata.SubKeyMetadata>

  Holds the shard sub key metadata information extracted from the database.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SubKeyMetadata``(int index, `[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` dataType, int charSet)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                             |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `compareTo``(ShardingMetadata.SubKeyMetadata o)`<br>Method used to defined natural ordering for the sub key column info based on the column index. |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### SubKeyMetadata

          public SubKeyMetadata(int index,
                                SQLType dataType,
                                int charSet)

      Parameters:
      `index` - column index of the subkey

      `dataType` - type of the subkey to be constructed

      `charSet` - character set of the subkey in the database

  <!-- -->

  - ### Method Detail

    - #### compareTo

          public int compareTo(ShardingMetadata.SubKeyMetadata o)

      Method used to defined natural ordering for the sub key column info based on the column index.
      Specified by:
      [`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true#compareTo_T_) in interface [`Comparable`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)`<ShardingMetadata.SubKeyMetadata>`

      Parameters:
      `o` - SubKeyMetadata to which this object is to be compared.

      Returns:
      -1, 0 or 1 as this metadata is less than, equal to, or greater than the metadata that is passed in as a method parameter

      See Also:
      [`Comparable.compareTo(java.lang.Object)`](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true#compareTo_T_)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ShardingMetadata.SubKeyMetadata.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ShardingMetadata.ShardingType.md)
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

Copyright © 2008, 2022, Oracle and/or its affiliates.
