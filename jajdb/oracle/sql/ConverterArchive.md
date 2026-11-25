Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConverterArchive.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ConcreteProxyUtil.md)
- [Next Class](CustomDatum.md)

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

## Class ConverterArchive

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.ConverterArchive

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConverterArchive
      extends Object

  This class allows a program to serialize an object and put it into a regular file or archive it into a zip file. It also allows a program to extract the object from the file for usage. It is used by the GSS package to create dynamically loadable data files. It is made public so programs from other packages can utilize this to created dynamically loable data files.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ConverterArchive``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    |-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                          | `closeArchiveforInsert``()`                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                          | `closeArchiveforRead``()`                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                          | `insertObj``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` entryName)`<br>entryName is the name of the obj inside the zip file, include directory                                                                                                                                                       |
    | `void`                                                                                          | `insertObjtoFile``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` directory, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` filename, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`                                                                                                                |
    | `void`                                                                                          | `insertSingleObj``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` zipName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` entryName)`<br>entryName is the name of the obj inside the zip file, include directory zipName is the name of the zip file. |
    | `void`                                                                                          | `openArchiveforInsert``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` zipName)`                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                          | `openArchiveforRead``()`                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `readObj``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` entryName)`                                                                                                                                                                                                                                                                                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `readObj``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` zipName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` entryName)`<br>entryName is the name of the obj inside the zip file, include directory zipName is the name of the zip file.                                                                                                                |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### ConverterArchive

          public ConverterArchive()

  <!-- -->

  - ### Method Detail

    - #### openArchiveforInsert

          public void openArchiveforInsert(String zipName)

      Parameters:
      `zipName` - is the name of the zip file. May include directory

    <!-- -->

    - #### closeArchiveforInsert

          public void closeArchiveforInsert()

    <!-- -->

    - #### insertObj

          public void insertObj(Object obj,
                                String entryName)

      entryName is the name of the obj inside the zip file, include directory

    <!-- -->

    - #### insertSingleObj

          public void insertSingleObj(String zipName,
                                      Object obj,
                                      String entryName)
                               throws IOException

      entryName is the name of the obj inside the zip file, include directory zipName is the name of the zip file. May include directory
      Throws:
      [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    <!-- -->

    - #### insertObjtoFile

          public void insertObjtoFile(String directory,
                                      String filename,
                                      Object obj)
                               throws IOException

      Throws:
      [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    <!-- -->

    - #### openArchiveforRead

          public void openArchiveforRead()

    <!-- -->

    - #### closeArchiveforRead

          public void closeArchiveforRead()

    <!-- -->

    - #### readObj

          public Object readObj(String entryName)

    <!-- -->

    - #### readObj

          public Object readObj(String zipName,
                                String entryName)

      entryName is the name of the obj inside the zip file, include directory zipName is the name of the zip file. May include directory

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConverterArchive.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ConcreteProxyUtil.md)
- [Next Class](CustomDatum.md)

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
