Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQMessage.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQFactory.md)
- [Next Class](AQMessageProperties.md)

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

oracle.jdbc.aq

## Interface AQMessage

-

  ------------------------------------------------------------------------



      public interface AQMessage

  A message is the unit that is enqueued or dequeued. An AQMessage object holds both its content, or payload, and its properties. This class provides methods to get and set message properties and the payload.
  See Also:
  `AQFactory.createAQMessage`

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                           |
    |-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ANYDATA`](../../sql/ANYDATA.md)                                                               | `getANYDATAPayload``()`<br>Retrieves the payload as an ANYDATA.                                                                                  |
    | `byte[]`                                                                                        | `getMessageId``()`<br>Gets the id (16 bytes) of this message.                                                                                    |
    | [`AQMessageProperties`](AQMessageProperties.md)                                                 | `getMessageProperties``()`<br>Gets the AQMessageProperties that goes with this AQMessage.                                                        |
    | `byte[]`                                                                                        | `getPayload``()`<br>Retrieves the payload in its linearized form.                                                                                |
    | `byte[]`                                                                                        | `getPayloadTOID``()`<br>Retrieves the TOID of the payload.                                                                                       |
    | [`RAW`](../../sql/RAW.md)                                                                       | `getRAWPayload``()`<br>Retrieves the payload as a RAW.                                                                                           |
    | [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)  | `getStructPayload``()`<br>Retrieves the payload as java.sql.Struct                                                                               |
    | [`STRUCT`](../../sql/STRUCT.md)                                                                 | `getSTRUCTPayload``()`<br>Retrieves the payload as an ADT.                                                                                       |
    | `oracle.xdb.XMLType`                                                                            | `getXMLTypePayload``()`<br>Retrieves the payload as an XMLType.                                                                                  |
    | `boolean`                                                                                       | `isANYDATAPayload``()`<br>Returns true if the payload type is ANYDATA and false otherwise.                                                       |
    | `boolean`                                                                                       | `isRAWPayload``()`<br>Returns trus if the payload type is RAW and false otherwise.                                                               |
    | `boolean`                                                                                       | `isSTRUCTPayload``()`<br>Returns true if the payload is a STRUCT (in other words if the payload is an object) and false otherwise.               |
    | `boolean`                                                                                       | `isXMLTypePayload``()`<br>Returns trus if the payload type is XMLType and false otherwise.                                                       |
    | `void`                                                                                          | `setPayload``(`[`ANYDATA`](../../sql/ANYDATA.md)` payload)`<br>Sets an ANYDATA payload.                                                          |
    | `void`                                                                                          | `setPayload``(byte[] payload)`<br>Sets a RAW payload.                                                                                            |
    | `void`                                                                                          | `setPayload``(byte[] payload, byte[] tdo)`<br>Sets the payload in its linearized form.                                                           |
    | `void`                                                                                          | `setPayload``(`[`RAW`](../../sql/RAW.md)` payload)`<br>Sets a RAW payload.                                                                       |
    | `void`                                                                                          | `setPayload``(`[`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)` payload)`<br>Sets an ADT payload. |
    | `void`                                                                                          | `setPayload``(`[`STRUCT`](../../sql/STRUCT.md)` payload)`<br>Sets an ADT payload.                                                                |
    | `void`                                                                                          | `setPayload``(oracle.xdb.XMLType xmlt)`<br>Sets an XMLType payload.                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`<br>Returns the String description of this message.                                                                                |

<!-- -->

- - ### Method Detail

    - #### getMessageId

          byte[] getMessageId()
                       throws SQLException

      Gets the id (16 bytes) of this message.
      There are enqueue and dequeue options to retrieve the id of a message after enqueue or dequeue.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMessageProperties

          AQMessageProperties getMessageProperties()
                                            throws SQLException

      Gets the AQMessageProperties that goes with this AQMessage.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(byte[] payload)
                   throws SQLException

      Sets a RAW payload.
      Sets the payload payload type to "RAW" and stores the given payload but doesn't make a copy.

      Calling this method is the equivalent of:

                // payloadInBytes being the byte[] array
                RAW rawPayload = new RAW(payloadInBytes);
                message.setPayload(rawPayload);


      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(byte[] payload,
                          byte[] tdo)
                   throws SQLException

      Sets the payload in its linearized form.
      This method lets you set the payload in its linearized form. You need to provide the correpondant OID of the Type Descriptor Object. This is useful in the case where you have your own pickler.

      For example, given that the linearized form of a RAW instance is the bytes themselves, the following code:

            message.setPayload(payloadInBytes);

      is the same as
            message.setPayload(payloadInBytes,TypeDescriptor.RAWTOID);

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(Struct payload)
                   throws SQLException

      Sets an ADT payload.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(STRUCT payload)
                   throws SQLException

      Sets an ADT payload.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(ANYDATA payload)
                   throws SQLException

      Sets an ANYDATA payload.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(RAW payload)
                   throws SQLException

      Sets a RAW payload.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setPayload

          void setPayload(oracle.xdb.XMLType xmlt)
                   throws SQLException

      Sets an XMLType payload.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPayload

          byte[] getPayload()
                     throws SQLException

      Retrieves the payload in its linearized form.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPayloadTOID

          byte[] getPayloadTOID()

      Retrieves the TOID of the payload.

    <!-- -->

    - #### getSTRUCTPayload

          STRUCT getSTRUCTPayload()
                           throws SQLException

      Retrieves the payload as an ADT.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStructPayload

          Struct getStructPayload()
                           throws SQLException

      Retrieves the payload as java.sql.Struct
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isSTRUCTPayload

          boolean isSTRUCTPayload()
                           throws SQLException

      Returns true if the payload is a STRUCT (in other words if the payload is an object) and false otherwise.
      If the payload is q STRUCT, you should use `getSTRUCTPayload()` to get its value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getANYDATAPayload

          ANYDATA getANYDATAPayload()
                             throws SQLException

      Retrieves the payload as an ANYDATA.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isANYDATAPayload

          boolean isANYDATAPayload()
                            throws SQLException

      Returns true if the payload type is ANYDATA and false otherwise.
      If the payload type is ANYDATA, you should use `getANYDATAPayload()` to get its content.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRAWPayload

          RAW getRAWPayload()
                     throws SQLException

      Retrieves the payload as a RAW.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isRAWPayload

          boolean isRAWPayload()
                        throws SQLException

      Returns trus if the payload type is RAW and false otherwise.
      If the payload type is RAW, you should use `getRAWPayload()` to get its content.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getXMLTypePayload

          oracle.xdb.XMLType getXMLTypePayload()
                                        throws SQLException

      Retrieves the payload as an XMLType.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isXMLTypePayload

          boolean isXMLTypePayload()
                            throws SQLException

      Returns trus if the payload type is XMLType and false otherwise.
      If the payload type is XMLType, you should use `getXMLTypePayload()` to get its content.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toString

          String toString()

      Returns the String description of this message.
      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQMessage.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQFactory.md)
- [Next Class](AQMessageProperties.md)

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
