Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ANYDATA.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](ARRAY.md)

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

## Class ANYDATA

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.ANYDATA

<!-- -->

- All Implemented Interfaces:
  oracle.jdbc.internal.ObjectData, [OracleData](../jdbc/OracleData.md), [ORAData](ORAData.md)

  ------------------------------------------------------------------------



      public class ANYDATA
      extends Object
      implements ORAData, OracleData

  This class is the Java mapping of the SYS.ANYDATA SQL type. Instances of this type are self-descriptive. They contain a type description as well the actual content (also called the embedded object).
  You can construct an ANYDATA instance from a Datum instance using `ANYDATA.convertDatum(Datum)`. The following example shows how to construct an ANYDATA instance that encapsulates a NUMBER:

        NUMBER num = new NUMBER(12345);
        ANYDATA anydt = ANYDATA.convertDatum(num);


  The `ANYDATA.convertDatum(Datum)` method is the java equivalent of the PLSQL `ConvertXXX` procedures. In the previous example we could also have used PLSQL to construct the ANYDATA instance and retrieve it in Java:
        // conn being a JDBC connection
        Statement stmt = conn.createStatement();
        ResultSet rs = stmt.executeQuery("select ANYDATA.ConvertNUMBER(12345) from dual");
        ANYDATA anydt = null;
        if(rs.next())
          anydt = (ANYDATA)rs.getObject(1);


  The public method `getTypeDescriptor()` returns an instance of `TypeDescriptor` which provides a description of the type. To retrieve the actual data, use `accessDatum()` which returns an instance of `Datum`. To know what to cast it to, use the type description. For example:

        Statement stmt = conn.createStatement();
        ResultSet rs = stmt.executeQuery("select anydatacol from foo");
        while(rs.next())
        {
          ANYDATA anydt = (ANYDATA)rs.getObject(1);
          System.out.println(anydt.stringValue());
          TypeDescriptor typedesc = anydt.getTypeDescriptor();
          Datum embeddedDatum = anydt.accessDatum();
          if(typedesc.getTypeCode() == TypeDescriptor.TYPECODE_DATE)
          {
            // the embedded object is a DATE:
            DATE datedatum = (DATE)embeddedDatum;
            // etc.
          }
          else if(typedesc.getTypeCode() == TypeDescriptor.TYPECODE_NUMBER)
          {
            // the embedded object is a NUMBER
            NUMBER numberdatum = (NUMBER)embeddedDatum;
            // etc.
          }
        }


<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Datum`](Datum.md)                                                                             | `accessDatum``()`<br>Returns the embedded object.                                                                                                                                         |
    | `static ANYDATA`                                                                                | `convertDatum``(`[`Datum`](Datum.md)` datum)`<br>Constructs an ANYDATA instance from any instance of `Datum`.                                                                             |
    | `protected oracle.jdbc.internal.OracleConnection`                                               | `getConnectionDuringExceptionHandling``()`                                                                                                                                                |
    | `byte[]`                                                                                        | `getData``()`<br>Returns the linearized form of the embedded object value.                                                                                                                |
    | [`TypeDescriptor`](TypeDescriptor.md)                                                           | `getTypeDescriptor``()`<br>Returns the type description of this ANYDATA instance.                                                                                                         |
    | `boolean`                                                                                       | `isNull``()`<br>Returns true if the data part of this ANYDATA instance is null and false otherwise.                                                                                       |
    | `boolean`                                                                                       | `isREF``()`<br>Returns true if the embedded object is a REF and false otherwise.                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `stringValue``()`<br>Returns a string representation of this ANYDATA.                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `stringValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` _connection)`<br>Returns a string representation of this ANYDATA. |
    | [`Datum`](Datum.md)                                                                             | `toDatum``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract an oracle.sql.Datum object.                            |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `toJDBCObject``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract a jdbc Object.                                    |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Method Detail

    - #### toDatum

          public Datum toDatum(Connection c)
                        throws SQLException

      Description copied from interface: [`ORAData`](ORAData.md)
      Extract an oracle.sql.Datum object.
      This method is invoked by setORAData() to extract a Datum. The implementation of this method must return the correct type of Datum.

      Although most implementation will ignore the connection, it is occassionally needed. For example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Specified by:
      [`toDatum`](ORAData.md) in interface [`ORAData`](ORAData.md)

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a Datum contaning the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

    <!-- -->

    - #### toJDBCObject

          public Object toJDBCObject(Connection c)
                              throws SQLException

      Description copied from interface: [`OracleData`](../jdbc/OracleData.md)
      Extract a jdbc Object.
      This method is invoked by setObject() to extract the jdbc Object. The implementation must return the jdbc Object that correctly represents the underlying SQLType.

      Although most implementation will ignore the connection, it is ocassionally needed. for example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Specified by:
      [`toJDBCObject`](../jdbc/OracleData.md) in interface [`OracleData`](../jdbc/OracleData.md)

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a jdbc Object contianing the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

    <!-- -->

    - #### convertDatum

          public static ANYDATA convertDatum(Datum datum)
                                      throws SQLException

      Constructs an ANYDATA instance from any instance of `Datum`.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeDescriptor

          public TypeDescriptor getTypeDescriptor()

      Returns the type description of this ANYDATA instance.

    <!-- -->

    - #### isNull

          public boolean isNull()

      Returns true if the data part of this ANYDATA instance is null and false otherwise.

    <!-- -->

    - #### getData

          public byte[] getData()

      Returns the linearized form of the embedded object value. This method is an internal method.

    <!-- -->

    - #### isREF

          public boolean isREF()

      Returns true if the embedded object is a REF and false otherwise.

    <!-- -->

    - #### stringValue

          public String stringValue()
                             throws SQLException

      Returns a string representation of this ANYDATA. The string contains both the type code name and a string representation of the embedded object.
      For example the following code:

               String sql = "select anydata.ConvertDate(TO_DATE('Jan 15, 2006, 11:00 AM', "
                      +" 'Mon dd, YYYY, HH:MI AM')) from dual";
               Statement stmt = conn.createStatement();
               ResultSet rs = stmt.executeQuery(sql);
               rs.next();
               ANYDATA ad = (ANYDATA)rs.getObject(1);
               System.out.println(ad.stringValue());


      will print in stdout the following string:
               ANYDATA TypeCode: "TYPECODE_DATE" -  ANYDATA Value: "1/15/2006 11:0:0"


      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue(Connection _connection)
                             throws SQLException

      Returns a string representation of this ANYDATA. The string contains both the type code name and a string representation of the embedded object.
      For example the following code:

               String sql = "select anydata.ConvertTIMESTAMPTZ(TO_TIMESTAMP_TZ("
                +" TIMESTAMP'1997-06-22 08:30:00' AT TIME ZONE 'Asia/Calcutta')) from dual";
               Statement stmt = conn.createStatement();
               ResultSet rs = stmt.executeQuery(sql);
               rs.next();
               ANYDATA ad = (ANYDATA)rs.getObject(1);
               // Pass connection to the types that require connection to print
               // eg: oracle.sql.TIMESTAMPTZ, oracle.sql.TIMESTAMPLTZ
               System.out.println(ad.stringValue(conn));


      will print in stdout the following string:
               ANYDATA TypeCode: "TYPECODE_TIMESTAMP_TZ" - ANYDATA Value: "1997-6-22 21.0.0.0 Asia/Calcutta"


      Parameters:
      `_connection` - OracleConnection object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### accessDatum

          public Datum accessDatum()
                            throws SQLException

      Returns the embedded object. Use `getTypeDescripor()` to retrieve type description of this embedded object. You will then be able to cast it to the right `oracle.sql.` class.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ANYDATA.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](ARRAY.md)

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
