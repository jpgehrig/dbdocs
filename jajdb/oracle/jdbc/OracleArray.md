Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleArray.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NotificationRegistration.RegistrationState.md)
- [Next Class](OracleBfile.md)

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

oracle.jdbc

## Interface OracleArray

- All Superinterfaces:
  [Array](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [ARRAY](../sql/ARRAY.md)

  ------------------------------------------------------------------------



      public interface OracleArray
      extends Array

  This interface defines the Oracle extensions to the standard JDBC interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true).
  Generally any new code should avoid the direct use of the class [`ARRAY`](../sql/ARRAY.md). For variable declarations use the interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true) or this interface as required. For creating a `OracleArray` use [`OracleConnection.createOracleArray(java.lang.String, java.lang.Object)`](OracleConnection.md).

  Since:
  11.2.0.3.0

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                | Method and Description                                                                                                               |
    |--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `double[]`                                                                                       | `getDoubleArray``()`<br>Oracle extension.                                                                                            |
    | `double[]`                                                                                       | `getDoubleArray``(long index, int count)`<br>Oracle extension.                                                                       |
    | `float[]`                                                                                        | `getFloatArray``()`<br>Oracle extension.                                                                                             |
    | `float[]`                                                                                        | `getFloatArray``(long index, int count)`<br>Oracle extension.                                                                        |
    | `int[]`                                                                                          | `getIntArray``()`<br>Oracle extension.                                                                                               |
    | `int[]`                                                                                          | `getIntArray``(long index, int count)`<br>Oracle extension.                                                                          |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<?,?>` | `getJavaMap``()`<br>Analogous to getArray except that it returns indices and elements of the SQL associative array as java.util.Map. |
    | `long[]`                                                                                         | `getLongArray``()`<br>Oracle extension.                                                                                              |
    | `long[]`                                                                                         | `getLongArray``(long index, int count)`<br>Oracle extension.                                                                         |
    | [`OracleTypeMetaData`](OracleTypeMetaData.md)                                                    | `getOracleMetaData``()`<br>Oracle extension.                                                                                         |
    | `short[]`                                                                                        | `getShortArray``()`<br>Oracle extension.                                                                                             |
    | `short[]`                                                                                        | `getShortArray``(long index, int count)`                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `getSQLTypeName``()`<br>Oracle extension.                                                                                            |
    | `int`                                                                                            | `length``()`<br>Oracle extension.                                                                                                    |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)  | `toJdbc``()`<br>Oracle extension.                                                                                                    |

    - ### Methods inherited from interface java.sql.[Array](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#free__)`, `[`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray__)`, `[`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_long_int_)`, `[`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_long_int_java_util_Map_)`, `[`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_java_util_Map_)`, `[`getBaseType`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getBaseType__)`, `[`getBaseTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getBaseTypeName__)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet__)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_long_int_)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_long_int_java_util_Map_)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_java_util_Map_)

<!-- -->

- - ### Method Detail

    - #### getOracleMetaData

          OracleTypeMetaData getOracleMetaData()
                                        throws SQLException

      Oracle extension. Get the SQL ARRAY type metadata for the type of this object.
      Returns:
      metadata for this object's type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

    <!-- -->

    - #### length

          int length()
              throws SQLException

      Oracle extension. Get array size.
      Returns:
      the number of elements in the array.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSQLTypeName

          String getSQLTypeName()
                         throws SQLException

      Oracle extension. Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.
      Returns:
      the fully-qualified type name of the SQL collection type for which this `Array` object is the generic representation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### toJdbc

          Object toJdbc()
                 throws SQLException

      Oracle extension. Returns the JDBC representation of the datum object
      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### getIntArray

          int[] getIntArray()
                     throws SQLException

      Oracle extension. Analogous to getArray except that it always returns a int\[\].
      Returns:
      an array of int.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getIntArray

          int[] getIntArray(long index,
                            int count)
                     throws SQLException

      Oracle extension. Like getIntArray, but returns a slice.
      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDoubleArray

          double[] getDoubleArray()
                           throws SQLException

      Oracle extension. Analogous to getArray except that it always returns a double\[\].
      Returns:
      an array of double.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDoubleArray

          double[] getDoubleArray(long index,
                                  int count)
                           throws SQLException

      Oracle extension. Like getDoubleArray, but returns a slice.
      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getShortArray

          short[] getShortArray()
                         throws SQLException

      Oracle extension. Analogous to getArray except that it always returns a short\[\].
      Returns:
      an array of short.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getShortArray

          short[] getShortArray(long index,
                                int count)
                         throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLongArray

          long[] getLongArray()
                       throws SQLException

      Oracle extension. Analogous to getArray except that it always returns a long\[\].
      Returns:
      an array of long.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLongArray

          long[] getLongArray(long index,
                              int count)
                       throws SQLException

      Oracle extension. Like getLongArray, but returns a slice.
      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFloatArray

          float[] getFloatArray()
                         throws SQLException

      Oracle extension. Analogous to getArray except that it always returns a float\[\].
      Returns:
      an array of float.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFloatArray

          float[] getFloatArray(long index,
                                int count)
                         throws SQLException

      Oracle extension. Like getFloatArray, but returns a slice.
      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getJavaMap

          Map<?,?> getJavaMap()
                       throws SQLException

      Analogous to getArray except that it returns indices and elements of the SQL associative array as java.util.Map. For non SQL associative array types (such as VARRAY or NESTED TABLE) this method returns null.
      Returns:
      a Map containing indices and elements of the SQL associative array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleArray.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NotificationRegistration.RegistrationState.md)
- [Next Class](OracleBfile.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
