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

- **[Prev Class](LoadingMode.md)**
- **Next Class**

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

**oracle.xml.transx**

## **Interface TransX**

-

  ------------------------------------------------------------------------

  **
  **

      public interface TransX

  **TransX Utility API**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                          |
    |-------------------|-----------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Help reclaim used resources.                                                                     |
    | `int`             | `load``(java.io.InputStream in)`<br>Load a dataset.                                                             |
    | `int`             | `load``(java.io.Reader rd)`<br>Load a dataset.                                                                  |
    | `int`             | `load``(java.lang.String file)`<br>Load a dataset.                                                              |
    | `int`             | `load``(java.net.URL url)`<br>Load a dataset on a URL.                                                          |
    | `void`            | `open``(java.sql.Connection conn)`<br>Start a data loading session.                                             |
    | `void`            | `open``(java.lang.String constr, java.lang.String user, java.lang.String pwd)`<br>Start a data loading session. |
    | `void`            | `setLoadingMode``(int mode)`<br>Set the operation mode on duplicates.                                           |
    | `void`            | `setNormalizeLangTag``(int casingStyle)`<br>Set the normalization form for the language identifier.             |
    | `void`            | `setPreserveWhitespace``(boolean flag)`<br>Tell the loader to treat whitespaces to be significant.              |
    | `void`            | `setValidationMode``(boolean flag)`<br>Set the validation mode.                                                 |
    | `java.io.Reader`  | `unload``(java.lang.String table, java.lang.String[] columns)`<br>Unload a dataset.                             |
    | `void`            | `unload``(java.lang.String table, java.lang.String[] columns, java.io.Writer out)`<br>Unload a dataset.         |
    | `boolean`         | `validate``(java.lang.String file)`<br>Validate a dataset on a file.                                            |
    | `boolean`         | `validate``(java.net.URL url)`<br>Validate a dataset on a URL.                                                  |

<!-- -->

- - ### Method Detail

    - #### open

          void open(java.lang.String constr,
                    java.lang.String user,
                    java.lang.String pwd)
             throws java.sql.SQLException

      Start a data loading session. This methods establishs a database connection to the given JDBC URL to be used for subsequent load() call(s).
      Parameters:
      `constr` - a database url of the form `jdbc:Oracle:<driver_type>:@[additional_parameters]`

      `user` - the database user on whose behalf the connection is being made

      `pwd` - the user's password

      Throws:
      `java.sql.SQLException`

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`, `close()`

    <!-- -->

    - #### open

          void open(java.sql.Connection conn)

      Start a data loading session. This methods establishs a database connection to the given JDBC URL to be used for subsequent load() call(s).
      Parameters:
      `conn` - - The sql connection to open

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`, `close()`

    <!-- -->

    - #### load

          int load(java.lang.String file)
            throws java.lang.Exception

      Load a dataset.
      Parameters:
      `file` - - filename of a DLF formatted document

      Returns:
      the total number of inserted and/or updated rows

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### load

          int load(java.io.InputStream in)
            throws java.lang.Exception

      Load a dataset.
      Parameters:
      `in` - - inputstream of a DLF formatted document

      Returns:
      the total number of inserted and/or updated rows

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### load

          int load(java.io.Reader rd)
            throws java.lang.Exception

      Load a dataset.
      Parameters:
      `rd` - - Reader of a DLF formatted document

      Returns:
      the total number of inserted and/or updated rows

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### load

          int load(java.net.URL url)
            throws java.lang.Exception

      Load a dataset on a URL. A database connection must have been established by a preceding call to open().
      Parameters:
      `url` - a URL

      Returns:
      the total number of inserted and/or updated rows

      Throws:
      `java.lang.Exception`

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### unload

          java.io.Reader unload(java.lang.String table,
                                java.lang.String[] columns)
                         throws java.lang.Exception

      Unload a dataset. A database connection must have been established by a preceding call to open().
      Parameters:
      `table` - a table name

      `columns` - column names, means \* when null

      Returns:
      the dataset in XML

      Throws:
      `java.lang.Exception`

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`, `load(java.lang.String)`

    <!-- -->

    - #### unload

          void unload(java.lang.String table,
                      java.lang.String[] columns,
                      java.io.Writer out)
               throws java.lang.Exception

      Unload a dataset. A database connection must have been established by a preceding call to open().
      Parameters:
      `table` - a table name

      `columns` - column names, means \* when null

      `out` - a Writer to write the dataset in XML to

      Throws:
      `java.lang.Exception`

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`, `load(java.lang.String)`

    <!-- -->

    - #### close

          void close()
              throws java.sql.SQLException

      Help reclaim used resources. This method should be called after loading is complete.
      Throws:
      `java.sql.SQLException`

      See Also:
      `open(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### setLoadingMode

          void setLoadingMode(int mode)

      Set the operation mode on duplicates. In the case when there are one or more existing rows in the database whose values in the key columns are the same as those in the dataset to be loaded, the loader (1)skips duplicate rows, (2)updates them or (3)throws an exception, depending on the current loading mode specified by this method. The loader by default skips duplicates. i.e. The flag is SKIP.
      Parameters:
      `mode` - a loading mode

      See Also:
      [`LoadingMode`](LoadingMode.md)

    <!-- -->

    - #### setNormalizeLangTag

          void setNormalizeLangTag(int casingStyle)

      Set the normalization form for the language identifier.
      The normalize-langtag attribute specifies the form of normalization to be applied to the language identifier. The valid values are as follows:

      - none - no normalization. the values on DLF are loaded as they are. This is the default value.
      - standard - the style as recommended by the standards
        - lowercase for the 2 letter language code
        - uppercase for the 2 letter country code
        - titlecase for the 4 letter script code (e.g. "Hant" for Traditional Chinese)
        - lowercase for others (that we rarely use)
      - uppercase - uppercase everything
      - lowercase - lowercase everything

      Parameters:
      `casingStyle` - normalization form

      See Also:
      [`LangTag`](LangTag.md)

    <!-- -->

    - #### setPreserveWhitespace

          void setPreserveWhitespace(boolean flag)

      Tell the loader to treat whitespaces to be significant. The flag is false by default: If this call is not made or if false is passed to the flag argument, the loader ignores the type of whitespace characters in the dataset and load them as space characters. Consecutive whitespace characters in the dataset are treated as one space character.
      Parameters:
      `flag` - true for exceptions, false otherwise.

    <!-- -->

    - #### setValidationMode

          void setValidationMode(boolean flag)

      Set the validation mode. The flag is true by default: If this call is not made or if true is passed to the flag argument, the loader performs validation of the dataset format against the canonical schema definition on each load() call. The validation mode should be disabled only if the dataset has already been validated.
      Parameters:
      `flag` - determines whether the loader should be validating

      See Also:
      `validate(java.lang.String)`

    <!-- -->

    - #### validate

          boolean validate(java.lang.String file)
                    throws java.lang.Exception

      Validate a dataset on a file. Once the dataset has been validated, the validation mode can safely be disabled.
      The instance document does not have to be opened for validation.

      Parameters:
      `file` - a file name

      Returns:
      true if successfully validated, false otherwise

      Throws:
      `java.lang.Exception`

      See Also:
      `setValidationMode(boolean)`, `validate(java.lang.String)`

    <!-- -->

    - #### validate

          boolean validate(java.net.URL url)
                    throws java.lang.Exception

      Validate a dataset on a URL. Once the dataset has been validated, the validation mode can safely be disabled.
      The instance document does not have to be opened for validation.

      Parameters:
      `url` - a URL string

      Returns:
      true if successfully validated, false otherwise

      Throws:
      `java.lang.Exception`

      See Also:
      `validate(java.lang.String)`

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

- **[Prev Class](LoadingMode.md)**
- **Next Class**

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
