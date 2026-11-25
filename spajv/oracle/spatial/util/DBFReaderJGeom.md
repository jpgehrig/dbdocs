Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](CustomCrsExport.md)
- [Next Class](DBFReaderJGeom.CharacterColumn.md)

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

oracle.spatial.util

## Class DBFReaderJGeom

- java.lang.Object

- - oracle.spatial.util.DBFReaderJGeom

<!-- -->

-

  ------------------------------------------------------------------------



      public class DBFReaderJGeom
      extends java.lang.Object

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                  |
    |-------------------|------------------------------------------------------------------------|
    | `static class `   | [`DBFReaderJGeom.CharacterColumn`](DBFReaderJGeom.CharacterColumn.md)  |
    | `static class `   | [`DBFReaderJGeom.DateColumn`](DBFReaderJGeom.DateColumn.md)            |
    | `static class `   | [`DBFReaderJGeom.LogicalColumn`](DBFReaderJGeom.LogicalColumn.md)      |
    | `static class `   | [`DBFReaderJGeom.NumericColumn`](DBFReaderJGeom.NumericColumn.md)      |
    | `static class `   | [`DBFReaderJGeom.RecordColumn`](DBFReaderJGeom.RecordColumn.md)        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                 |
    |-------------------------------------------------------------------------------------------------------------|
    | `DBFReaderJGeom``()`                                                                                        |
    | `DBFReaderJGeom``(java.lang.String name)`<br>construct an object out of the specified shapefile's DBF file. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                   |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `closeDBF``()`<br>close this dbfile.                                                                                                     |
    | `java.lang.String` | `getFieldData``(int ith, byte[] rec)`<br>get the value string for the ith field in the given record.                                     |
    | `int`              | `getFieldLength``(int nth)`<br>return the length of the specified field.                                                                 |
    | `java.lang.String` | `getFieldName``(int ith)`<br>returns the name for the ith field of records in this file.                                                 |
    | `byte`             | `getFieldType``(int ith)`<br>get the type for the ith field in a record.                                                                 |
    | `byte[]`           | `getRecord``(int nth)`<br>retrieve the nth record in the file.                                                                           |
    | `int`              | `numFields``()`<br>return the number of fields in each record                                                                            |
    | `int`              | `numRecords``()`<br>return the number of records in the DBF file.                                                                        |
    | `void`             | `openDBF``(java.lang.String name)`<br>Given a DBF file's name, open the file and read the header info.                                   |
    | `void`             | `print``()`<br>nicely print out the general information of this shapefile.                                                               |
    | `void`             | `readCodePage``(java.lang.String name)`<br>Given a DBF file's name, open the (optional) .cpg file and read the character encoding value. |
    | `int`              | `recordSize``()`<br>return the record size in the DBF file                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DBFReaderJGeom

          public DBFReaderJGeom()

    <!-- -->

    - #### DBFReaderJGeom

          public DBFReaderJGeom(java.lang.String name)
                         throws java.io.IOException

      construct an object out of the specified shapefile's DBF file.
      Throws:
      `java.io.IOException`

  <!-- -->

  - ### Method Detail

    - #### readCodePage

          public void readCodePage(java.lang.String name)
                            throws java.io.IOException

      Given a DBF file's name, open the (optional) .cpg file and read the character encoding value. Use this value in GetFieldData() to explicitly set the character set.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### openDBF

          public void openDBF(java.lang.String name)
                       throws java.io.IOException

      Given a DBF file's name, open the file and read the header info. Records can be read afterwards.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### closeDBF

          public void closeDBF()
                        throws java.io.IOException

      close this dbfile.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### numRecords

          public int numRecords()

      return the number of records in the DBF file.

    <!-- -->

    - #### numFields

          public int numFields()

      return the number of fields in each record

    <!-- -->

    - #### recordSize

          public int recordSize()

      return the record size in the DBF file

    <!-- -->

    - #### getRecord

          public byte[] getRecord(int nth)

      retrieve the nth record in the file. return the pointer to the beginning of the record. the recordDeform method can be called on this pointer to interpret individual fields.

    <!-- -->

    - #### getFieldData

          public java.lang.String getFieldData(int ith,
                                               byte[] rec)

      get the value string for the ith field in the given record. This is an ascii representation of this field's actual value. For fields with type 'I' or 'N', Use atoi() or strtod() accordingly to convert the returned string into an integer or double. Null is returned if something is wrong (e.g., invalid field index). bug-9852192: explicitly set codePage if .cpg file available

    <!-- -->

    - #### getFieldLength

          public int getFieldLength(int nth)

      return the length of the specified field.

    <!-- -->

    - #### getFieldName

          public java.lang.String getFieldName(int ith)

      returns the name for the ith field of records in this file.

    <!-- -->

    - #### getFieldType

          public byte getFieldType(int ith)

      get the type for the ith field in a record. returns a single character the meaning of which is defined as below:

                  'C': character

                  'D': Date (8 digits: YYYYMMDD)

                  'F': Floating point binary numeric: -. 0 1 2 3 4 5 6 7 8 9

                  'G': General. All OEM characters or OLE.

                  'L': Logical: ? Y y N  n T t F f (? initially)

                  'M': Memo

                  'N': Float: - . 0 1 2 3 4 5 6 7 8 9

                  'I': Integer: - 0 1 2 3 4 5 6 7 8 9



    <!-- -->

    - #### print

          public void print()

      nicely print out the general information of this shapefile.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](CustomCrsExport.md)
- [Next Class](DBFReaderJGeom.CharacterColumn.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
