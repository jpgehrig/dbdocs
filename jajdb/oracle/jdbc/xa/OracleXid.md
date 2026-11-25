Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXid.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAResource.md)
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

oracle.jdbc.xa

## Class OracleXid

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.xa.OracleXid

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Xid](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)

  ------------------------------------------------------------------------



      public class OracleXid
      extends Object
      implements Xid, Serializable

  The OracleXid class:
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `MAXBQUALSIZE`        |
    | `static int`      | `MAXGTRIDSIZE`        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                             |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXid``(int fId, byte[] gId, byte[] bId)`<br>OracleXid() -- The constructor that constructs an OracleXid with given formatId, global transacrion Id and branch qualifier.                                          |
    | `OracleXid``(int fId, byte[] gId, byte[] bId, byte[] context)`<br>OracleXid() -- The constructor that constructs an OracleXid with given formatId, global transacrion Id and branch qualifier, and transaction context. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                              |
    |---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                         | `equals``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` xid)`                   |
    | `byte[]`                                          | `getBranchQualifier``()`<br>getBranchQualifier() -- Obtain the txn branch qualifier of the XID                                      |
    | `protected oracle.jdbc.internal.OracleConnection` | `getConnectionDuringExceptionHandling``()`<br>Compares the given transaction identifiers with this.                                 |
    | `int`                                             | `getFormatId``()`<br>getFormatId() -- Obtain the format identifier part of the Xid.                                                 |
    | `byte[]`                                          | `getGlobalTransactionId``()`<br>getGlobalTransactionId() -- Obtain the global txn id of the XID                                     |
    | `int`                                             | `hashCode``()`                                                                                                                      |
    | `static boolean`                                  | `isLocalTransaction``(`[`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)` xid)`  |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### MAXGTRIDSIZE

          public static final int MAXGTRIDSIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MAXBQUALSIZE

          public static final int MAXBQUALSIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleXid

          public OracleXid(int fId,
                           byte[] gId,
                           byte[] bId)
                    throws XAException

      OracleXid() -- The constructor that constructs an OracleXid with given formatId, global transacrion Id and branch qualifier.
      Parameters:
      `fId` - format ID

      `gId` - global transaction ID (no copy performed)

      `bId` - branch Qualifier (no copy performed)

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - if the size of gId or bId is more than 64 bytes

    <!-- -->

    - #### OracleXid

          public OracleXid(int fId,
                           byte[] gId,
                           byte[] bId,
                           byte[] context)
                    throws XAException

      OracleXid() -- The constructor that constructs an OracleXid with given formatId, global transacrion Id and branch qualifier, and transaction context.
      Parameters:
      `fId` - format ID

      `gId` - global transaction ID (no copy performed)

      `bId` - branch Qualifier (no copy performed)

      `context` - transation context (no copy performed)

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) - if the size of gId or bId is more than 64 bytes

  <!-- -->

  - ### Method Detail

    - #### getFormatId

          public int getFormatId()

      getFormatId() -- Obtain the format identifier part of the Xid.
      Specified by:
      [`getFormatId`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true#getFormatId__) in interface [`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)

      Returns:
      Format identifier. 0 means the OSI CCR format.

    <!-- -->

    - #### getGlobalTransactionId

          public byte[] getGlobalTransactionId()

      getGlobalTransactionId() -- Obtain the global txn id of the XID
      Specified by:
      [`getGlobalTransactionId`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true#getGlobalTransactionId__) in interface [`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)

      Returns:
      A byte array containing the global transaction identifier.

    <!-- -->

    - #### getBranchQualifier

          public byte[] getBranchQualifier()

      getBranchQualifier() -- Obtain the txn branch qualifier of the XID
      Specified by:
      [`getBranchQualifier`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true#getBranchQualifier__) in interface [`Xid`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true)

      Returns:
      A byte array containing the branch qualifier of the transaction.

    <!-- -->

    - #### isLocalTransaction

          public static final boolean isLocalTransaction(Xid xid)

    <!-- -->

    - #### equals

          public boolean equals(Object xid)

      Overrides:
      [`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      [`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Compares the given transaction identifiers with this. If the format is different or any byte in the global transaction if or the branch qualifier differs from this, then false is returned. public boolean equals(Object obj) { if(obj==this) return true; OracleXid xid =null; try { xid = (OracleXid)obj; } catch(ClassCastException e){ return false; } if(formatId != xid.getFormatId()) return false; byte\[\] gtridB = xid.getGlobalTransactionId(); byte\[\] bqualB = xid.getBranchQualifier(); if(gtrid != gtridB){ if( (gtrid == null && gtridB != null) \|\| (gtridB == null && gtrid != null) ) return false; if(gtridB!=null){ if(gtridB.length != gtrid.length) return false; for(int i=0;i\<gtrid.length;i++){ if(gtridB\[i\] != gtrid\[i\]) return false; } } } if(bqual != bqualB){ if( ( bqualB == null && bqual != null) \|\| (bqual == null && bqualB != null) ) return false; if(bqualB!=null){ if(bqualB.length != bqual.length) return false; for(int i=0;i\<bqualB.length;i++){ if(bqualB\[i\] != bqual\[i\]) return false; } } } return true; } public int hashCode() { int ret = formatId; int temp = 0; for(int i=0;i\<gtrid.length/4;i++){ temp = (int)gtrid\[i\] + ((int)(gtrid\[i+1\]\<\<8))&0xff00 + ((int)(gtrid\[i+2\]\<\<16))&0xff0000 + ((int)(gtrid\[i+3\]\<\<24))&0xff000000; ret += temp; } for(int i=0;i\<bqual.length/4;i++){ temp = (int)bqual\[i\] + ((int)(bqual\[i+1\]\<\<8))&0xff00 + ((int)(bqual\[i+2\]\<\<16))&0xff0000 + ((int)(bqual\[i+3\]\<\<24))&0xff000000; ret += temp; } return ret; }

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXid.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAResource.md)
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
