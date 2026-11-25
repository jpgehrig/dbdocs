Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLNSNode.md)**
- **[Next Class](XMLOutputStream.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Class XMLObjectInputStream**

- **java.lang.Object**

- - **java.io.InputStream**

  - - **java.io.ObjectInputStream**

    - - **oracle.xml.parser.v2.XMLObjectInputStream**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Closeable, java.io.DataInput, java.io.ObjectInput, java.io.ObjectStreamConstants, java.lang.AutoCloseable**

  ------------------------------------------------------------------------

  **
  **

      public final class XMLObjectInputStream
      extends java.io.ObjectInputStream

  **This purpose of this class is to provide compatibility for applications between different versions of the XDK for Java, with regards to *serialization* and *deserialization*. If an XML document (using the DOM model) has been serialized with a version of the XDK for Java of 11.2.0.1 or earlier, and you want to deserialize it with a version of 11.2.0.2 or later, then you may have to use this class to do so. You will know that you must do so if you encounter `java.io.InvalidClassException` during deserialization, with an error message that indicates that the `serialVersionUID` is incompatible between the `stream classdesc` and the `local class`.**

  **Serialization is typically done with `java.io.ObjectOutputStream.writeObject(doc)`; and deserialization with `java.io.ObjectInputStream.readObject()`. This class extends the standard Java class `ObjectInputStream` so as to preserve compatibility.**

  **If your application previously did deserialization by using code such as the following:**

       import java.io.* ;
       import oracle.xml.parser.v2.* ;

       InputStream is = new FileInputStream( new File( "abc.dat" ) ) ;
       ObjectInputStream ois = new ObjectInputStream( is ) ;
       Object o = ois.readObject() ;
       XMLDocument xdoc = (XMLDocument) o ;


  **and you get the `InvalidClassException` during deserialization (i.e., in the `readObject()` method); then you may have to replace the constructor for `ObjectInputStream` with `XMLObjectInputStream` in your application:**
       ObjectInputStream ois = new XMLObjectInputStream( is ) ;


<!-- -->

-
  -

    ### **Nested Class Summary**

    -

      ### **Nested classes/interfaces inherited from class java.io.ObjectInputStream**

      **`java.io.ObjectInputStream.GetField`**

  <!-- -->

  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface java.io.ObjectStreamConstants**

      **`baseWireHandle, PROTOCOL_VERSION_1, PROTOCOL_VERSION_2, SC_BLOCK_DATA, SC_ENUM, SC_EXTERNALIZABLE, SC_SERIALIZABLE, SC_WRITE_METHOD, STREAM_MAGIC, STREAM_VERSION, SUBCLASS_IMPLEMENTATION_PERMISSION, SUBSTITUTION_PERMISSION, TC_ARRAY, TC_BASE, TC_BLOCKDATA, TC_BLOCKDATALONG, TC_CLASS, TC_CLASSDESC, TC_ENDBLOCKDATA, TC_ENUM, TC_EXCEPTION, TC_LONGSTRING, TC_MAX, TC_NULL, TC_OBJECT, TC_PROXYCLASSDESC, TC_REFERENCE, TC_RESET, TC_STRING`**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                       |
    |---------------------------------------------------|
    | `XMLObjectInputStream``(java.io.InputStream in)`  |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.io.ObjectInputStream**

      **`available, close, defaultReadObject, read, read, readBoolean, readByte, readChar, readDouble, readFields, readFloat, readFully, readFully, readInt, readLine, readLong, readObject, readShort, readUnshared, readUnsignedByte, readUnsignedShort, readUTF, registerValidation, skipBytes`**

    <!-- -->

    -

      ### **Methods inherited from class java.io.InputStream**

      **`mark, markSupported, read, reset, skip`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`**

    <!-- -->

    -

      ### **Methods inherited from interface java.io.ObjectInput**

      **`read, skip`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **XMLObjectInputStream**

          public XMLObjectInputStream(java.io.InputStream in)
                               throws java.io.IOException

      **Throws:**
      **`java.io.IOException`**

      **See Also:**
      **`ObjectInputStream.ObjectInputStream(InputStream)`**

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLNSNode.md)**
- **[Next Class](XMLOutputStream.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
