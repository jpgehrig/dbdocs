Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TableChangeDescription.TableOperation.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TableChangeDescription.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.jdbc.dcn

## Enum TableChangeDescription.TableOperation

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<TableChangeDescription.TableOperation\>

  - - oracle.jdbc.dcn.TableChangeDescription.TableOperation

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<TableChangeDescription.TableOperation\>

  <!-- -->

  Enclosing interface:
  [TableChangeDescription](TableChangeDescription.md)

  ------------------------------------------------------------------------



      public static enum TableChangeDescription.TableOperation
      extends Enum<TableChangeDescription.TableOperation>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                |
    |----------------------------------------------------------------------------------------------|
    | `ALL_ROWS`<br>The table is completely invalidated and row level information isn't available. |
    | `ALTER`<br>Alter table operation (DDL).                                                      |
    | `DELETE`<br>Delete operation (DML).                                                          |
    | `DROP`<br>Drop table opersation (DDL).                                                       |
    | `INSERT`<br>Insert operation (DML).                                                          |
    | `UPDATE`<br>Update operation (DML).                                                          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                   | Method and Description                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                                                                               | `getCode``()`<br>Implementation detail (for internal use only).                                                                                                                        |
    | `static `[`EnumSet`](http://download.oracle.com/javase/8/docs/api/java/util/EnumSet.html?is-external=true)`<TableChangeDescription.TableOperation>` | `getTableOperations``(int opcode)`<br>Implementation detail (for internal use only).                                                                                                   |
    | `static TableChangeDescription.TableOperation`                                                                                                      | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static TableChangeDescription.TableOperation[]`                                                                                                    | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### ALL_ROWS

          public static final TableChangeDescription.TableOperation ALL_ROWS

      The table is completely invalidated and row level information isn't available. If the `DCN_NOTIFY_ROWIDS` option hasn't been turned on during registration, then all events will have this `OPERATION_ALL_ROWS` flag on. It can also happen in situations where too many rows have changed and it would be too expensive for the server to send the list of them..

    <!-- -->

    - #### INSERT

          public static final TableChangeDescription.TableOperation INSERT

      Insert operation (DML).

    <!-- -->

    - #### UPDATE

          public static final TableChangeDescription.TableOperation UPDATE

      Update operation (DML).

    <!-- -->

    - #### DELETE

          public static final TableChangeDescription.TableOperation DELETE

      Delete operation (DML).

    <!-- -->

    - #### ALTER

          public static final TableChangeDescription.TableOperation ALTER

      Alter table operation (DDL).

    <!-- -->

    - #### DROP

          public static final TableChangeDescription.TableOperation DROP

      Drop table opersation (DDL).

  <!-- -->

  - ### Method Detail

    - #### values

          public static TableChangeDescription.TableOperation[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (TableChangeDescription.TableOperation c : TableChangeDescription.TableOperation.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static TableChangeDescription.TableOperation valueOf(String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      [`IllegalArgumentException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if this enum type has no constant with the specified name

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if the argument is null

    <!-- -->

    - #### getCode

          public final int getCode()

      Implementation detail (for internal use only).

    <!-- -->

    - #### getTableOperations

          public static final EnumSet<TableChangeDescription.TableOperation> getTableOperations(int opcode)

      Implementation detail (for internal use only).

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TableChangeDescription.TableOperation.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TableChangeDescription.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
