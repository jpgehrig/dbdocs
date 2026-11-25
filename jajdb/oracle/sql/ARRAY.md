Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ARRAY.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ANYDATA.md)
- [Next Class](ArrayDescriptor.md)

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

oracle.sql

## Class ARRAY

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.ARRAY

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Array](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, [OracleArray](../jdbc/OracleArray.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.Array interface for declaration instead of using concrete class oracle.sql.ARRAY.


      public class ARRAY
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleArray, oracle.jdbc.internal.OracleConcreteProxy

  This class has two roles.
  - It is the Oracle implementation class for the generic JDBC Array interface.
  - It wraps the "raw bytes" of an Oracle Collection.

  Like other classes in oracle.sql. it is a value class. That is, once it is constructed the user should not change its contents. The type of the array elements is called the "Base Type" An Oracle implementation for generic JDBC Array interface. Use [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true) interface for declaration instead of using concrete class oracle.sql.ARRAY. java.sql.Array has methods declared for all opertions. For Oracle specific methods use the interface [`OracleArray`](../jdbc/OracleArray.md).
  Obtaining java.sql.Array from the ResultSet

  `java.sql.Array array = resultSet.getArray(...);`
  Creating a new java.sql.Array using factory method. [`OracleConnection.createOracleArray(java.lang.String, java.lang.Object)`](../jdbc/OracleConnection.md) should be used to create java.sql.Array. [`Connection.createArrayOf(java.lang.String, java.lang.Object[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createArrayOf_java_lang_String_java_lang_Object_A_) throws an exception since Oracle does not support creation of anonymous array type.

  `java.sql.Array array = ((oracle.jdbc.OracleConnection)connection).createOracleArray((...);`
  See Also:
  [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true), [`OracleArray`](../jdbc/OracleArray.md), [`OracleConnection.createOracleArray(java.lang.String, java.lang.Object)`](../jdbc/OracleConnection.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                          | Field and Description                 |
    |--------------------------------------------|---------------------------------------|
    | `static int`                               | `ACCESS_FORWARD`<br>Deprecated. <br>  |
    | `static int`                               | `ACCESS_REVERSE`<br>Deprecated. <br>  |
    | `static int`                               | `ACCESS_UNKNOWN`<br>Deprecated. <br>  |
    | `protected oracle.jdbc.driver.OracleArray` | `target`<br>Deprecated. <br>          |

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ARRAY``(`[`ArrayDescriptor`](ArrayDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Deprecated. <br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                     |
    |------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `dump``()`<br>Deprecated. <br>Create a string which show the contents of this Array and of all its component parts.                                                                                                                                                                                                                                                        |
    | `void`                                                                                               | `free``()`<br>Deprecated. <br>Currently does nothing.                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                | `getAccessDirection``()`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                                              |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `getArray``()`<br>Deprecated. <br>Implements Array interface method Retrieve the contents of the SQL array designated by the object.                                                                                                                                                                                                                                       |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `getArray``(long index, int count)`<br>Deprecated. <br>Implements Array interface method Like getArray() above, but returns an array containing a slice of the SQL array, beginning with the given index and containing up to count successive elements of the SQL array.                                                                                                  |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `getArray``(long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Implements Array interface method Like getArray() above, but returns an array containing a slice of the SQL array, beginning with the given index and containing up to count successive elements of the SQL array. |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `getArray``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Implements Array interface method Retrieve the contents of the SQL array designated by this object.                                                                                                                                       |
    | `boolean`                                                                                            | `getAutoBuffering``()`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                            | `getAutoIndexing``()`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                | `getBaseType``()`<br>Deprecated. <br>Implements Array interface method Determine the code, from java.sql.Types, of the type of the elements of the array.                                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getBaseTypeName``()`<br>Deprecated. <br>Implements Array interface method Returns the SQL type name of the elements in the array designated by this `Array` object.                                                                                                                                                                                                       |
    | [`Datum`](Datum.md)`[]`                                                                              | `getDatumArray``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                    |
    | [`ArrayDescriptor`](ArrayDescriptor.md)                                                              | `getDescriptor``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                   |
    | `double[]`                                                                                           | `getDoubleArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                  |
    | `double[]`                                                                                           | `getDoubleArray``(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                             |
    | `float[]`                                                                                            | `getFloatArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                   |
    | `float[]`                                                                                            | `getFloatArray``(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                              |
    | `int[]`                                                                                              | `getIntArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                     |
    | `int[]`                                                                                              | `getIntArray``(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<?,?>`     | `getJavaMap``()`<br>Deprecated. <br>Implements Array interface method Retrieves the contents of the SQL associative array designated by the object.                                                                                                                                                                                                                        |
    | `long[]`                                                                                             | `getLongArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                    |
    | `long[]`                                                                                             | `getLongArray``(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                               |
    | `int`                                                                                                | `getNumElems``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                      |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `getObjArray``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                      |
    | [`Datum`](Datum.md)`[]`                                                                              | `getOracleArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                  |
    | [`Datum`](Datum.md)`[]`                                                                              | `getOracleArray``(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                             |
    | [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)                                                | `getOracleMetaData``()`<br>Deprecated. <br>Return the type data for this object                                                                                                                                                                                                                                                                                            |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `getResultSet``()`<br>Deprecated. <br>Implements Array interface method Returns a result set that contains the elements of the array designated by this `Array` object.                                                                                                                                                                                                    |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `getResultSet``(long index, int count)`<br>Deprecated. <br>Implements Array interface method Returns a result set holding the elements of the subarray that starts at index `index` and contains up to `count` successive elements.                                                                                                                                        |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `getResultSet``(long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Implements Array interface method Returns a result set holding the elements of the subarray that starts at index `index` and contains up to `count` successive elements.                                       |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `getResultSet``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Implements Array interface method Returns a result set that contains the elements of the array designated by this `Array` object and uses the given `map` to map the array elements.                                                  |
    | `short[]`                                                                                            | `getShortArray``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                   |
    | `short[]`                                                                                            | `getShortArray``(long index, int count)`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getSQLTypeName``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                  |
    | `oracle.jdbc.driver.OracleArray`                                                                     | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                            | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                           |
    | `int`                                                                                                | `length``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                               | `setAutoBuffering``(boolean enable)`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setAutoIndexing``(boolean enable)`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                               | `setAutoIndexing``(boolean enable, int direction)`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                               | `setNullObjArray``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `stringValue``()`<br>Deprecated. <br>Convert to a String representation of the datum object                                                                                                                                                                                                                                                                                |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `toJdbc``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                                                          |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `toJdbc``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                           |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getJavaSqlConnection`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getJavaSqlConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Field Detail

    - #### ACCESS_FORWARD

          public static final int ACCESS_FORWARD

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ACCESS_REVERSE

          public static final int ACCESS_REVERSE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ACCESS_UNKNOWN

          public static final int ACCESS_UNKNOWN

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### target

          protected oracle.jdbc.driver.OracleArray target

      Deprecated. 

  <!-- -->

  - ### Constructor Detail

    - #### ARRAY

          public ARRAY(ArrayDescriptor type,
                       Connection conn,
                       Object elements)
                throws SQLException

      Deprecated. 
      Constructor.
      Parameters:
      `type` - an ArrayDescriptor describing the SQL Type

      `elements` - the contents of the array. These objects will be converted to raw bytes of the appropriate SQL Type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleArray getTarget()

      Deprecated. 

    <!-- -->

    - #### getBaseTypeName

          public String getBaseTypeName()
                                 throws SQLException

      Deprecated. 
      Implements Array interface method Returns the SQL type name of the elements in the array designated by this `Array` object. If the elements are a built-in type, it returns the database-specific type name of the elements. If the elements are a user-defined type (UDT), this method returns the fully-qualified SQL type name.
      Specified by:
      [`getBaseTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getBaseTypeName__) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Returns:
      a `String` that is the database-specific name for a built-in base type or the fully-qualified SQL type name for a base type that is a UDT

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while attempting to access the type name

    <!-- -->

    - #### getBaseType

          public int getBaseType()
                          throws SQLException

      Deprecated. 
      Implements Array interface method Determine the code, from java.sql.Types, of the type of the elements of the array.
      Specified by:
      [`getBaseType`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getBaseType__) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Returns:
      the type code of the elements of the array.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true), `OracleTypes`

    <!-- -->

    - #### getArray

          public Object getArray()
                          throws SQLException

      Deprecated. 
      Implements Array interface method Retrieve the contents of the SQL array designated by the object. Use the type-map associated with the connection for customizations of the type-mappings.
      Specified by:
      [`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray__) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Returns:
      a Java array containing the ordered elements of the SQL array designated by this object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getJavaMap

          public Map<?,?> getJavaMap()
                              throws SQLException

      Deprecated. 
      Implements Array interface method Retrieves the contents of the SQL associative array designated by the object.
      Specified by:
      [`getJavaMap`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      a Java Map containing the ordered elements of the SQL associative array designated by this object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getArray

          public Object getArray(Map map)
                          throws SQLException

      Deprecated. 
      Implements Array interface method Retrieve the contents of the SQL array designated by this object. Use the given map for type-map customizations.
      Specified by:
      [`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_java_util_Map_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `map` - contains mapping of SQL type names to Java classes

      Returns:
      a Java array containing the ordered elements of the SQL array designated by this object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getArray

          public Object getArray(long index,
                                 int count)
                          throws SQLException

      Deprecated. 
      Implements Array interface method Like getArray() above, but returns an array containing a slice of the SQL array, beginning with the given index and containing up to count successive elements of the SQL array. Use the type-map associated with the connection for customizations of the type-mappings.
      Specified by:
      [`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_long_int_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `index` - the array-index of the first element to retrieve

      `count` - the number of successive SQL array elements to retrieve

      Returns:
      an array containing up to count elements of the SQL array, beginning with element index.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getArray

          public Object getArray(long index,
                                 int count,
                                 Map map)
                          throws SQLException

      Deprecated. 
      Implements Array interface method Like getArray() above, but returns an array containing a slice of the SQL array, beginning with the given index and containing up to count successive elements of the SQL array. Use the given map for type-map customizations.
      Specified by:
      [`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getArray_long_int_java_util_Map_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `index` - the array-index of the first element to retrieve

      `count` - the number of successive SQL array elements to retrieve

      `map` - contains mapping of SQL user-defined types to classes

      Returns:
      an array containing up to count elements of the SQL array, beginning with element index.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getResultSet

          public ResultSet getResultSet()
                                 throws SQLException

      Deprecated. 
      Implements Array interface method Returns a result set that contains the elements of the array designated by this `Array` object. If appropriate, the elements of the array are mapped using the connection's type map; otherwise, the standard mapping is used.
      The result set contains one row for each array element, with two columns in each row. The second column stores the element value; the first column stores the index into the array for that element (with the first array element being at index 1). The rows are in ascending order corresponding to the order of the indices.

      Specified by:
      [`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet__) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Returns:
      a [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) object containing one row for each of the elements in the array designated by this `Array` object, with the rows in ascending order based on the indices.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while attempting to access the array

    <!-- -->

    - #### getResultSet

          public ResultSet getResultSet(Map map)
                                 throws SQLException

      Deprecated. 
      Implements Array interface method Returns a result set that contains the elements of the array designated by this `Array` object and uses the given `map` to map the array elements. If the base type of the array does not match a user-defined type in `map`, the standard mapping is used instead.
      The result set contains one row for each array element, with two columns in each row. The second column stores the element value; the first column stores the index into the array for that element (with the first array element being at index 1). The rows are in ascending order corresponding to the order of the indices.

      Specified by:
      [`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_java_util_Map_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `map` - contains mapping of SQL user-defined types to classes in the Java(tm) programming language

      Returns:
      a `ResultSet` object containing one row for each of the elements in the array designated by this `Array` object, with the rows in ascending order based on the indices.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while attempting to access the array

    <!-- -->

    - #### getResultSet

          public ResultSet getResultSet(long index,
                                        int count)
                                 throws SQLException

      Deprecated. 
      Implements Array interface method Returns a result set holding the elements of the subarray that starts at index `index` and contains up to `count` successive elements. This method uses the connection's type map to map the elements of the array if the map contains an entry for the base type. Otherwise, the standard mapping is used.
      The result set has one row for each element of the SQL array designated by this object, with the first row containing the element at index `index`. The result set has up to `count` rows in ascending order based on the indices. Each row has two columns: The second column stores the element value; the first column stroes the index into the array for that element.

      Specified by:
      [`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_long_int_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `index` - the array index of the first element to retrieve; the first element is at index 1

      `count` - the number of successive SQL array elements to retrieve

      Returns:
      a `ResultSet` object containing up to `count` consecutive elements of the SQL array designated by this `Array` object, starting at index `index`.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while attempting to access the array

    <!-- -->

    - #### getResultSet

          public ResultSet getResultSet(long index,
                                        int count,
                                        Map map)
                                 throws SQLException

      Deprecated. 
      Implements Array interface method Returns a result set holding the elements of the subarray that starts at index `index` and contains up to `count` successive elements. This method uses the `Map` object `map` to map the elements of the array unless the base type of the array does not match a user-defined type in `map`, in which case it uses the standard mapping.
      The result set has one row for each element of the SQL array designated by this object, with the first row containing the element at index `index`. The result set has up to `count` rows in ascending order based on the indices. Each row has two columns: The second column stores the element value; the first column stroes the index into the array for that element.

      Specified by:
      [`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#getResultSet_long_int_java_util_Map_) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Parameters:
      `index` - the array index of the first element to retrieve; the first element is at index 1

      `count` - the number of successive SQL array elements to retrieve

      `map` - the `Map` object that contains the mapping of SQL type names to classes in the Java(tm) programming language

      Returns:
      a `ResultSet` object containing up to `count` consecutive elements of the SQL array designated by this `Array` object, starting at index `index`.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while attempting to access the array

    <!-- -->

    - #### getOracleArray

          public Datum[] getOracleArray()
                                 throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns an oracle.sql.XXX instead of whatever result.getObject would have returned.
      Returns:
      an array of Datum.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### length

          public int length()
                     throws SQLException

      Deprecated. 
      Oracle extension. Get array size.
      Specified by:
      [`length`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      the number of elements in the array.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getOracleArray

          public Datum[] getOracleArray(long index,
                                        int count)
                                 throws SQLException

      Deprecated. 
      Oracle extension. Like getOracleArray, but returns a slice.
      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSQLTypeName

          public String getSQLTypeName()
                                throws SQLException

      Deprecated. 
      Oracle extension. Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.
      Specified by:
      [`getSQLTypeName`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      the fully-qualified type name of the SQL collection type for which this `Array` object is the generic representation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getOracleMetaData

          public OracleTypeMetaData getOracleMetaData()
                                               throws SQLException

      Deprecated. 
      Return the type data for this object
      Specified by:
      [`getOracleMetaData`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      type metadata

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      11.2.0.3.0

    <!-- -->

    - #### getDescriptor

          public ArrayDescriptor getDescriptor()
                                        throws SQLException

      Deprecated. 
      Oracle extension. Return the ArrayDescriptor object that contains the type information.
      Returns:
      the type descriptor

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Oracle extension. Returns the JDBC representation of the datum object
      Specified by:
      `toJdbc` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`toJdbc`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### toJdbc

          public Object toJdbc(Map map)
                        throws SQLException

      Deprecated. 
      Oracle extension. Consults the map to determine what class to convert to, and then uses toClass
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class jClass)

      Deprecated. 
      Oracle extension. Determines if datum object can be converted to a particular class
      Specified by:
      `isConvertibleTo` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `jClass` - Class to convert to

      Returns:
      true, if conversion to cls is permitted false, if conversion to cls is not permitted

    <!-- -->

    - #### getIntArray

          public int[] getIntArray()
                            throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns a int\[\].
      Specified by:
      [`getIntArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      an array of int.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getIntArray

          public int[] getIntArray(long index,
                                   int count)
                            throws SQLException

      Deprecated. 
      Oracle extension. Like getIntArray, but returns a slice.
      Specified by:
      [`getIntArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDoubleArray

          public double[] getDoubleArray()
                                  throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns a double\[\].
      Specified by:
      [`getDoubleArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      an array of double.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDoubleArray

          public double[] getDoubleArray(long index,
                                         int count)
                                  throws SQLException

      Deprecated. 
      Oracle extension. Like getDoubleArray, but returns a slice.
      Specified by:
      [`getDoubleArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getShortArray

          public short[] getShortArray()
                                throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns a short\[\].
      Specified by:
      [`getShortArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      an array of short.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getShortArray

          public short[] getShortArray(long index,
                                       int count)
                                throws SQLException

      Deprecated. 
      Specified by:
      [`getShortArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLongArray

          public long[] getLongArray()
                              throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns a long\[\].
      Specified by:
      [`getLongArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      an array of long.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLongArray

          public long[] getLongArray(long index,
                                     int count)
                              throws SQLException

      Deprecated. 
      Oracle extension. Like getLongArray, but returns a slice.
      Specified by:
      [`getLongArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFloatArray

          public float[] getFloatArray()
                                throws SQLException

      Deprecated. 
      Oracle extension. Analogous to getArray except that it always returns a float\[\].
      Specified by:
      [`getFloatArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Returns:
      an array of float.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFloatArray

          public float[] getFloatArray(long index,
                                       int count)
                                throws SQLException

      Deprecated. 
      Oracle extension. Like getFloatArray, but returns a slice.
      Specified by:
      [`getFloatArray`](../jdbc/OracleArray.md) in interface [`OracleArray`](../jdbc/OracleArray.md)

      Parameters:
      `index` - the index of the first element to be returned

      `count` - the number of elements to be returned.

      Returns:
      an array containing count elements starting at index

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setAutoBuffering

          public void setAutoBuffering(boolean enable)
                                throws SQLException

      Deprecated. 
      Performance hint. Sets this array's auto-buffering mode. If a array is in auto-buffering mode, then the array will keep a local copy of all its elements. Then the next access to the same elements will return a cloned copy. Otherwise, type conversion for each element is required. By default, a ARRAY is NOT in auto-buffering mode.
      Parameters:
      `enable` - - true enables auto-buffering; false disables auto-buffering

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `getAutoBuffering()`

    <!-- -->

    - #### getAutoBuffering

          public boolean getAutoBuffering()
                                   throws SQLException

      Deprecated. 
      Performance hint. Get the current auto-buffering state.
      Returns:
      the current state of auto-buffering

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `setAutoBuffering(boolean)`

    <!-- -->

    - #### setAutoIndexing

          public void setAutoIndexing(boolean enable,
                                      int direction)
                               throws SQLException

      Deprecated. 
      Performance hint. Sets this array's auto-indexing mode. If a array is in auto-indexing mode, then the array will maintain a index table for array elements to fasten repeatedly access to the same elements or different elementes in the ARRAY. The second argument gives this array a hint as to the direction in which the elements will be accessed. Available direction values are ARRAY.ACCESS_FORWARD, ARRAY.ACCESS_REVERSE, and ARRAY.ACCESS_UNKNOWN.
      Parameters:
      `enable` - - true enables auto-indexing; false disables auto-indexing

      `direction` - - overwrite default access direction.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### setAutoIndexing

          public void setAutoIndexing(boolean enable)
                               throws SQLException

      Deprecated. 
      Performance hint. Sets this array's auto-indexing mode. If a array is in auto-indexing mode, then the array will maintain a index table for array elements to fasten repeatedly access to the same elements or different elementes in the ARRAY. By default, access direction is set to ARRAY.ACCESS_UNKNOWN.
      Parameters:
      `enable` - - true enables auto-indexing; false disables auto-indexing

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### getAutoIndexing

          public boolean getAutoIndexing()
                                  throws SQLException

      Deprecated. 
      Performance hint. Get the current auto-indexing state.
      Returns:
      the current state of auto-indexing

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `oracle.sql.ARRAY#setAutoIndexinging(boolean)`, `oracle.sql.ARRAY#setAutoIndexinging(boolean, int)`

    <!-- -->

    - #### getAccessDirection

          public int getAccessDirection()
                                 throws SQLException

      Deprecated. 
      Performance hint. Get the access direction value.
      Returns:
      the current access direction

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `oracle.sql.ARRAY#setAutoIndexinging(boolean)`, `oracle.sql.ARRAY#setAutoIndexinging(boolean, int)`

    <!-- -->

    - #### dump

          public String dump()
                      throws SQLException

      Deprecated. 
      Create a string which show the contents of this Array and of all its component parts.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue()
                             throws SQLException

      Deprecated. 
      Description copied from class: [`Datum`](Datum.md)
      Convert to a String representation of the datum object
      Specified by:
      `stringValue` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      String representation of the datum object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### free

          public void free()
                    throws SQLException

      Deprecated. 
      Currently does nothing.
      Specified by:
      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true#free__) in interface [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNumElems

          public int getNumElems()

      Deprecated. 

    <!-- -->

    - #### getDatumArray

          public Datum[] getDatumArray()

      Deprecated. 

    <!-- -->

    - #### getObjArray

          public Object getObjArray()

      Deprecated. 

    <!-- -->

    - #### setNullObjArray

          public void setNullObjArray()

      Deprecated. 

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ARRAY.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ANYDATA.md)
- [Next Class](ArrayDescriptor.md)

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
