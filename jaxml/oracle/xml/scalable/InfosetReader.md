Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](FilePageManager.md)**
- **[Next Class](InfosetReader.Offset.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.scalable**

## **Interface InfosetReader**

- **All Superinterfaces:**
  **java.lang.Cloneable**

  ------------------------------------------------------------------------

  **
  **

      public interface InfosetReader
      extends java.lang.Cloneable

  **The InfosetReader interface allows forward, read-only random access to XML. It is designed to be the lowest level and most efficient way to read XML data.**
  **The InfosetReader is designed to iterate over XML using next() and hasNext(). The data can be accessed using methods such as getEventType(), getQName(), getLocalName() and getData(), etc.**

  **The next() method causes the reader to read the next event.**

  **The event type can be determined using getEventType(). The events used are same as defined in JSR-173 (StAX API).**

  **The following table describes which methods are valid in what state. If a method is called in an invalid state the method will throw a java.lang.IllegalStateException.**

  **The parser has two optional features**

  - **Namespace resolution - The namespace resolution includes prefix to namespace resolution, and the reverse resolution.**
  - **Random Access - The random access is supported using getOffset() and seek() functions. The support for this feature can be tested using seekSupported()**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type   | Interface and Description                                                                                                      |
    |---------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`InfosetReader.Offset`](InfosetReader.Offset.md)<br>For opague object representing the current position/offset in the reader. |

  <!-- -->

  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                          |
    |-------------------|----------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ATTRIBUTE`<br>Indicates an event is an attribute                                                              |
    | `static int`      | `CDATA`<br>Indicates an event is a CDATA section                                                               |
    | `static int`      | `CHARACTERS`<br>Indicates an event is characters                                                               |
    | `static int`      | `COMMENT`<br>Indicates an event is a comment                                                                   |
    | `static int`      | `DTD`<br>Indicates an event is a DTD                                                                           |
    | `static int`      | `END_DOCUMENT`<br>Indicates an event is an end document                                                        |
    | `static int`      | `END_ELEMENT`<br>Indicates an event is an end element                                                          |
    | `static int`      | `END_ENTITY`<br>Indicates an event is the end of a resolved entity                                             |
    | `static int`      | `ENTITY_REFERENCE`<br>Indicates an event is an entity reference                                                |
    | `static int`      | `NAMESPACE`<br>Indicates an event is a namepsace                                                               |
    | `static int`      | `PROCESSING_INSTRUCTION`<br>Indicates an event is a processing instruction                                     |
    | `static int`      | `SPACE`<br>Indicates an event is a space, events are only reported as SPACE if they are ignorable white space. |
    | `static int`      | `START_DOCUMENT`<br>Indicates an event is a start document                                                     |
    | `static int`      | `START_ELEMENT`<br>Indicates an event is a start element                                                       |
    | `static int`      | `START_ENTITY`<br>Indicates an event is the start of a resolved entity                                         |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                                                                                           |
    |---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                | `clone``()`<br>Clone the reader                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                            | `close``()`<br>Frees any resources associated with this InfosetReader.                                                                                                                                                                                                                                                                                                                           |
    | `java.lang.String`                                | `getAttribute``(javax.xml.namespace.QName attr)`<br>Returns the attribute value of the current element with the given name Valid only if the current event is START_ELEMENT                                                                                                                                                                                                                      |
    | `char[]`                                          | `getData``()`<br>Return the data corresponding to the current event.                                                                                                                                                                                                                                                                                                                             |
    | `int`                                             | `getDataLength``()`<br>Returns the length of the sequence of characters for this event within the text character array.                                                                                                                                                                                                                                                                          |
    | `int`                                             | `getDataStart``()`<br>Returns the offset into the text character array where the first character (of this text event) is stored.                                                                                                                                                                                                                                                                 |
    | [`DTD`](../parser/v2/DTD.md)                      | `getDoctype``()`<br>Gets the DTD associated with the XML data.                                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                                | `getEncoding``()`<br>Get the xml encoding declared on the xml declaration Returns null if none was declared                                                                                                                                                                                                                                                                                      |
    | `int`                                             | `getEventFlags``()`<br>Get flags specific to the event                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                             | `getEventType``()`<br>Returns an integer code that indicates the type of the event the cursor is pointing to.                                                                                                                                                                                                                                                                                    |
    | `java.lang.String`                                | `getNamespaceURI``(java.lang.String prefix)`<br>Get Namespace URI bound to a prefix in the current scope.                                                                                                                                                                                                                                                                                        |
    | [`InfosetReader.Offset`](InfosetReader.Offset.md) | `getOffset``()`<br>Returns an opaque object representing the current position/offset in the reader.                                                                                                                                                                                                                                                                                              |
    | `java.lang.String`                                | `getPrefix``(java.lang.String namespaceURI)`<br>Get prefix bound to Namespace URI in the current scope.                                                                                                                                                                                                                                                                                          |
    | `int`                                             | `getPrimitiveTypeId``()`<br>Get the primitive type of the element This is valid at START_ELEMENT                                                                                                                                                                                                                                                                                                 |
    | `javax.xml.namespace.QName`                       | `getQName``()`<br>Get the name of the current event type This is valid at START_ELEMENT, END_ELEMENT, PROCESSING_INSTRUCTION, START_ENTITY, ENTITY_REFERENCE, END_ENTITY events                                                                                                                                                                                                                  |
    | `java.lang.String`                                | `getStandalone``()`<br>Get the xml standalone declared on the xml declaration Returns null if none was declared                                                                                                                                                                                                                                                                                  |
    | [`BinaryStream`](BinaryStream.md)                 | `getStream``()`<br>Returns an opaque object representing the current binary stream                                                                                                                                                                                                                                                                                                               |
    | `javax.xml.namespace.QName`                       | `getTypeName``()`<br>Get the type name of the element.                                                                                                                                                                                                                                                                                                                                           |
    | `java.lang.String`                                | `getValue``()`<br>Return the data corresponding to the current event.                                                                                                                                                                                                                                                                                                                            |
    | `java.lang.String`                                | `getVersion``()`<br>Get the xml version declared on the xml declaration Returns null if none was declared                                                                                                                                                                                                                                                                                        |
    | `boolean`                                         | `hasNext``()`<br>Returns true if there are more parsing events and false if there are no more events.                                                                                                                                                                                                                                                                                            |
    | `boolean`                                         | `isGlobal``()`<br>Is the current element based on global element decl?                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                         | `isNilled``()`<br>Is the element nillable?                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                         | `isNSResolutionSupported``()`<br>Checks if Namespace resolution supported                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                         | `isSeekSupported``()`<br>Checks if seek is supported                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                            | `()`<br>Get next parsing event This method will throw an IllegalStateException if it is called after hasNext() returns false.                                                                                                                                                                                                                                                                    |
    | [`InfosetReader.Offset`](InfosetReader.Offset.md) | `offsetFromBytes``(byte[] buf, int start)`<br>Create offset from a byte representation in the byte buffer starting at 'start' index.                                                                                                                                                                                                                                                             |
    | `byte`                                            | `offsetToBytes``(`[`InfosetReader.Offset`](InfosetReader.Offset.md)` offset, byte[] buf, int start)`<br>Write a byte representation of the Offset into the byte buffer starting at 'start' index.                                                                                                                                                                                                |
    | `long`                                            | `offsetToLong``()`<br>Returns a long representing the current position/offset in the reader.                                                                                                                                                                                                                                                                                                     |
    | `void`                                            | `seek``(`[`InfosetReader.Offset`](InfosetReader.Offset.md)` offset)`<br>Seek to a position in the reader represented by the Offset.                                                                                                                                                                                                                                                              |
    | `void`                                            | `seek``(long offset)`<br>Seek to a position in the reader represented by the long Offset.                                                                                                                                                                                                                                                                                                        |
    | `void`                                            | `skip``()`<br>Skip this parsing event and the complete subtree This method has different behavior (as compared `next()`) only when the current event is START_DOCUMENT or START_ELEMENT The getEventType will return END_DOCUMENT or END_ELEMENT, skipping the content of the document or element This method will throw an IllegalStateException if it is called after hasNext() returns false. |

<!-- -->

- - ### Field Detail

    - #### START_ELEMENT

          static final int START_ELEMENT

      Indicates an event is a start element
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### END_ELEMENT

          static final int END_ELEMENT

      Indicates an event is an end element
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROCESSING_INSTRUCTION

          static final int PROCESSING_INSTRUCTION

      Indicates an event is a processing instruction
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CHARACTERS

          static final int CHARACTERS

      Indicates an event is characters
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMMENT

          static final int COMMENT

      Indicates an event is a comment
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SPACE

          static final int SPACE

      Indicates an event is a space, events are only reported as SPACE if they are ignorable white space. Otherwise they are reported as CHARACTERS.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### START_DOCUMENT

          static final int START_DOCUMENT

      Indicates an event is a start document
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### END_DOCUMENT

          static final int END_DOCUMENT

      Indicates an event is an end document
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENTITY_REFERENCE

          static final int ENTITY_REFERENCE

      Indicates an event is an entity reference
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE

          static final int ATTRIBUTE

      Indicates an event is an attribute
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DTD

          static final int DTD

      Indicates an event is a DTD
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CDATA

          static final int CDATA

      Indicates an event is a CDATA section
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NAMESPACE

          static final int NAMESPACE

      Indicates an event is a namepsace
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### START_ENTITY

          static final int START_ENTITY

      Indicates an event is the start of a resolved entity
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### END_ENTITY

          static final int END_ENTITY

      Indicates an event is the end of a resolved entity
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### isNSResolutionSupported

          boolean isNSResolutionSupported()

      Checks if Namespace resolution supported

    <!-- -->

    - #### getNamespaceURI

          java.lang.String getNamespaceURI(java.lang.String prefix)

      Get Namespace URI bound to a prefix in the current scope.

      Parameters:
      `prefix` - prefix to look up

      Returns:
      Namespace URI bound to prefix in the current scope or null is namespace resolution is not supported

    <!-- -->

    - #### getPrefix

          java.lang.String getPrefix(java.lang.String namespaceURI)

      Get prefix bound to Namespace URI in the current scope.

      Parameters:
      `namespaceURI` - URI of Namespace to lookup

      Returns:
      prefix bound to Namespace URI in current context

    <!-- -->

    - #### isSeekSupported

          boolean isSeekSupported()

      Checks if seek is supported

    <!-- -->

    - #### getStream

          BinaryStream getStream()

      Returns an opaque object representing the current binary stream
      Returns:
      BinaryStream or null if the InfosetReader is not associated with a BinaryStream

    <!-- -->

    - #### getOffset

          InfosetReader.Offset getOffset()

      Returns an opaque object representing the current position/offset in the reader. The Offset object can be used to seek to this position using the seek() function
      Returns:
      Offset or null if seek is not support

    <!-- -->

    - #### seek

          void seek(InfosetReader.Offset offset)

      Seek to a position in the reader represented by the Offset. This function will throw UnsupportedOperationException if seek is supported
      Parameters:
      `offset` - indicating amount to seek

    <!-- -->

    - #### offsetToLong

          long offsetToLong()

      Returns a long representing the current position/offset in the reader. The Offset object can be used to seek to this position using the seek() function throws UnsupportedOperationException if long offset is not supported
      Returns:
      long offset

    <!-- -->

    - #### seek

          void seek(long offset)

      Seek to a position in the reader represented by the long Offset. This function will throw UnsupportedOperationException if such seek is not supported
      Parameters:
      `offset` - - indicating amount to seek

    <!-- -->

    - #### offsetToBytes

          byte offsetToBytes(InfosetReader.Offset offset,
                             byte[] buf,
                             int start)

      Write a byte representation of the Offset into the byte buffer starting at 'start' index.
      Parameters:
      `offset` - - offset to be converted to bytes

      `buf` - - byte array to write into

      `start` - - start index

      Returns:
      number of bytes written, or -1 if buffer size is not sufficient

    <!-- -->

    - #### offsetFromBytes

          InfosetReader.Offset offsetFromBytes(byte[] buf,
                                               int start)

      Create offset from a byte representation in the byte buffer starting at 'start' index.
      Parameters:
      `buf` - - byte array to read from

      `start` - - start index

      Returns:
      offset - offset converted from bytes in buf or null if bytes in the buf are invalid

    <!-- -->

    - #### getEventType

          int getEventType()

      Returns an integer code that indicates the type of the event the cursor is pointing to.
      Returns:
      event type at current cursor location

    <!-- -->

    - #### hasNext

          boolean hasNext()

      Returns true if there are more parsing events and false if there are no more events. This method will return false if the current state of the InfosetReader is END_DOCUMENT
      Returns:
      true if there are more events, false otherwise

    <!-- -->

    - #### next

          void next()

      Get next parsing event This method will throw an IllegalStateException if it is called after hasNext() returns false.
      Throws:
      `java.lang.IllegalStateException` - if this is called when hasNext() returns false

    <!-- -->

    - #### skip

          void skip()

      Skip this parsing event and the complete subtree This method has different behavior (as compared `next()`) only when the current event is START_DOCUMENT or START_ELEMENT The getEventType will return END_DOCUMENT or END_ELEMENT, skipping the content of the document or element This method will throw an IllegalStateException if it is called after hasNext() returns false.
      Throws:
      `java.lang.IllegalStateException` - if this is called when hasNext() returns false

    <!-- -->

    - #### getEncoding

          java.lang.String getEncoding()

      Get the xml encoding declared on the xml declaration Returns null if none was declared
      Returns:
      the XML encoding or null

    <!-- -->

    - #### getVersion

          java.lang.String getVersion()

      Get the xml version declared on the xml declaration Returns null if none was declared
      Returns:
      the XML version or null

    <!-- -->

    - #### getStandalone

          java.lang.String getStandalone()

      Get the xml standalone declared on the xml declaration Returns null if none was declared
      Returns:
      the XML standalone or null

    <!-- -->

    - #### getDoctype

          DTD getDoctype()

      Gets the DTD associated with the XML data. Returns null, if no DTD
      Returns:
      dtd

    <!-- -->

    - #### getQName

          javax.xml.namespace.QName getQName()

      Get the name of the current event type This is valid at START_ELEMENT, END_ELEMENT, PROCESSING_INSTRUCTION, START_ENTITY, ENTITY_REFERENCE, END_ENTITY events
      Returns:
      qname

    <!-- -->

    - #### getTypeName

          javax.xml.namespace.QName getTypeName()

      Get the type name of the element. This is valid at START_ELEMENT
      Returns:
      qname

    <!-- -->

    - #### getPrimitiveTypeId

          int getPrimitiveTypeId()

      Get the primitive type of the element This is valid at START_ELEMENT
      Returns:
      type id

    <!-- -->

    - #### isGlobal

          boolean isGlobal()

      Is the current element based on global element decl? This is valid at START_ELEMENT
      Returns:
      boolean

    <!-- -->

    - #### isNilled

          boolean isNilled()

      Is the element nillable? This is valid at START_ELEMENT
      Returns:
      boolean

    <!-- -->

    - #### getAttribute

          java.lang.String getAttribute(javax.xml.namespace.QName attr)

      Returns the attribute value of the current element with the given name Valid only if the current event is START_ELEMENT
      Returns:
      Attribute value

    <!-- -->

    - #### getValue

          java.lang.String getValue()

      Return the data corresponding to the current event.
      Returns:
      string

    <!-- -->

    - #### getData

          char[] getData()

      Return the data corresponding to the current event. The starting offset of the data is returned by getDataStart, and the length is returned by getDataLength.
      Returns:
      char array

    <!-- -->

    - #### getDataStart

          int getDataStart()

      Returns the offset into the text character array where the first character (of this text event) is stored.
      Throws:
      `java.lang.IllegalStateException` - if this state is not a valid data state.

    <!-- -->

    - #### getDataLength

          int getDataLength()

      Returns the length of the sequence of characters for this event within the text character array.
      Throws:
      `java.lang.IllegalStateException` - if this state is not a valid data state.

    <!-- -->

    - #### getEventFlags

          int getEventFlags()

      Get flags specific to the event

    <!-- -->

    - #### close

          void close()

      Frees any resources associated with this InfosetReader.

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clone the reader

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](FilePageManager.md)**
- **[Next Class](InfosetReader.Offset.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
