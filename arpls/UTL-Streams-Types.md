## 296 UTL Streams Types

`UTL Streams Types` describe abstract types used with Oracle XML functionality.

Four abstract PL/SQL streams are introduced and defined within the '`SYS`' schema. The streams may be referenced by `PUBLIC` and are described in the following sections.

This chapter contains the following topics:

- Security Model

- Summary of UTL Binary Streams Types

**See Also:**

For more information, see [Oracle XML DB Developer's Guide](../adxdb/PLSQL-APIs-for-XMLType.md)

### 296.1 UTL Streams Types Security Model

`EXECUTE` on UTL Streams Types is granted to `PUBLIC.`

### 296.2 Summary of UTL Binary Streams Types

This table lists the `UTL Binary Streams Types` and briefly describes them.

Table 296-1 UTL Streams Types

| Type                           | Description                       |
|:-------------------------------|:----------------------------------|
| UTL_BINARYINPUTSTREAM Type     | Reads bytes and closes a stream.  |
| UTL_BINARYOUTPUTSTREAM Type    | Writes bytes and closes a stream. |
| UTL_CHARACTERINPUTSTREAM Type  | Reads chars and closes a stream.  |
| UTL_CHARACTEROUTPUTSTREAM Type | Writes chars and closes a stream. |

#### 296.2.1 UTL_BINARYINPUTSTREAM Type

This type is similar to `java`.`io`.`InputStream` in that it can only read and close a stream.

##### Syntax

    CREATE OR REPLACE TYPE Utl_BinaryInputStream AS OBJECT (

       MEMBER FUNCTION available (
            self    IN OUT NOCOPY  Utl_BinaryInputStream)
         RETURN INTEGER,

       MEMBER FUNCTION read (                                  -- #1
          self      IN OUT NOCOPY  Utl_BinaryInputStream,
          numBytes  IN             INTEGER DEFAULT 1)
        RETURN RAW,

      MEMBER PROCEDURE read (                                  -- #2
         self       IN OUT NOCOPY   Utl_BinaryInputStream,
         bytes      IN OUT NOCOPY  RAW,
         numBytes   IN OUT         INTEGER),

      MEMBER PROCEDURE read (                                  -- #3
         self       IN OUT NOCOPY   Utl_BinaryInputStream,
         bytes      IN OUT NOCOPY   RAW,
         offset     IN INTEGER,
         numBytes   IN OUT          INTEGER),

      member function close (
         self       In Out Nocopy   Utl_BinaryInputStream)

     ) NOT FINAL;

##### Attributes

Table 296-2 UTL_BINARYINPUTSTREAM Type Member Subprograms

| Member Subprogram | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AVAILABLE`       | Returns the number of bytes available to be read                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `READ`            | • \#1 - Reads the number of bytes specified by `numBytes` (default is 1) and returns the bytes as a `RAW`. If there are no remaining bytes a value of `NULL` is returned.<br>• \#2 - Reads the number of bytes specified in `numBytes` into the parameter bytes. Additionally, the actual number of bytes read is returned in parameter `numBytes`. If this parameter is set to 0 then there are no more bytes to be read.<br>• \#3 - Reads the number of bytes specified in `numBytes` into the parameter bytes, beginning at the offset specified by parameter offset. The actual number of bytes read is returned in parameter `numBytes`. If this value is 0, then there are no additional bytes to be read. |
| `CLOSE`           | Releases all resources held on the node to support the stream                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

#### 296.2.2 UTL_BINARYOUTPUTSTREAM Type

This type is similar to `java.io.OutputStream` in that it can only write and close a stream.

##### Syntax

    CREATE OR REPLACE TYPE Utl_BinaryOutputStream AS OBJECT (

      MEMBER FUNCTION write (                                  -- #1
           self       IN OUT NOCOPY   sys.utl_BinaryOutputStream,
           bytes      IN              RAW,
           numBytes   IN              INTEGER DEFAULT 1)
      RETURN INTEGER,

      MEMBER PROCEDURE write (                                  -- #2
           self       IN OUT NOCOPY  sys.utl_BinaryOutputStream,
           bytes      IN NOCOPY      RAW,
           numBytes   IN OUT         INTEGER),

      MEMBER PROCEDURE write (                                  -- #3
           self       IN OUT NOCOPY  utl_BinaryOutputStream,        bytes      IN NOCOPY      RAW,
           offset     IN             INTEGER,
           numBytes   IN OUT         INTEGER),

      MEMBER PROCEDURE flush (
           self       IN OUT NOCOPY  utl_BinaryOutputStream),

      MEMBER PROCEDURE close (
           self       IN OUT NOCOPY utl_BinaryOutputStream)

     ) NOT FINAL;

##### Attributes

Table 296-3 UTL_BINARYOUTPUTSTREAM Type Member Subprograms

| Member Subprogram | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `WRITE`           | • \#1 - Writes the number of bytes specified by `numBytes` (default is 1) from `RAW` into the stream. The actual number of bytes written is returned.<br>• \#2 - Writes the number of bytes specified in parameter `numBytes` from parameter bytes to the stream. The actual number of bytes written is returned in parameter `numBytes`.<br>• \#3 - Writes the number of bytes specified by `numBytes` to the stream, beginning at the offset specified by parameter offset. The actual number of bytes written is returned in parameter `numBytes`. |
| `FLUSH`           | Insures that any buffered bytes are copied to the node destination                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `CLOSE`           | Frees all resources associated with the stream                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

#### 296.2.3 UTL_CHARACTERINPUTSTREAM Type

This type is similar to `java`.`io`.`Reader` in that it can only read characters (chars) and close a stream.

##### Syntax

    CREATE OR REPLACE TYPE Utl_CharacterInputStream AS OBJECT (

       MEMBER FUNCTION available (
           self       IN OUT NOCOPY   utl_CharacterInputStream)
       RETURN INTEGER,

       MEMBER FUNCTION read (                                   -- #1
           self       IN OUT NOCOPY   utl_CharacterInputStream,
           numChars   IN              INTEGER DEFAULT 1,
           lineFeed   IN              BOOLEAN DEFAULT FALSE)
       RETURN VARCHAR2,

       MEMBER PROCEDURE read (                                  -- #2
           self       IN OUT NOCOPY    utl_CharacterInputStream,
           chars      IN OUT NOCOPY    VARCHAR2,
           numChars   IN OUT           INTEGER,
           lineFeed   IN BOOLEAN DEFAULT FALSE),

       MEMBER PROCEDURE read (                                  -- #3
           self       IN OUT NOCOPY   utl_CharacterInputStream,
           chars      IN OUT NOCOPY    VARCHAR2,
           offset     IN               INTEGER,
           numChars   IN OUT           INTEGER,
           lineFeed   IN               BOOLEAN DEFAULT FALSE),

       MEMBER PROCEDURE close (
          self       IN OUT NOCOPY    utl_CharacterInputStream)
    ) NOT FINAL;

##### Attributes

Table 296-4 UTL_CHARACTERINPUTSTREAM Type Member Subprograms

| Member Subprogram | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AVAILABLE`       | Returns the number of bytes available to be read                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `READ`            | • \#1 - Returns the number of characters remaining to be read<br>• \#2 - Reads the number of characters specified by `numChars` (default value is 1) and returns the characters as a `VARCHAR2`. If the value of `lineFeed` is true (default value is `FALSE`) then the reading stops if a linefeed character is found. If there are no remaining characters a value of `NULL` is returned.<br>• \#3 - Reads reads the number of characters specified by parameter `numChars` into the parameter chars. Additionally, the actual number of characters read is returned in parameter `numChars`. If this value is 0, then there are no more characters to be read. If the value of `lineFeed` is `TRUE` (default is `FALSE`), then reading stops if a linefeed character is encountered. |
| `CLOSE`           | Releases all resources held by the stream                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

#### 296.2.4 UTL_CHARACTEROUTPUTSTREAM Type

This type is similar to `java`.`io`.`Reader` in that it can only read characters (chars) and close a stream.

##### Syntax

    CREATE OR REPLACE TYPE utl_CharacterOutputStream  AS OBJECT (

     MEMBER FUNCTION write (                                  -- #1
         self      IN OUT NOCOPY   utl_CharacterOutputStream,
         chars     IN              VARCHAR2,
         numChars  IN              INTEGER DEFAULT 1,
         lineFeed  IN              BOOLEAN DEFAULT FALSE)
      RETURN INTEGER,

     MEMBER PROCEDURE write (                                  -- #2
         self      IN OUT NOCOPY   utl_CharacterOutputStream,
         chars     IN OUT NOCOPY   VARCHAR2,
         numChars  IN OUT          INTEGER,
         lineFeed  IN              BOOLEAN DEFAULT FALSE),

     member procedure write (                                  -- #3
         self     IN OUT NOCOPY    utl_CharacterOutputStream,
         chars    IN  NOCOPY       varchar2,
         offset   IN               integer,
         numChars IN OUT           integer,
        lineFeed  IN               boolean default false),

     MEMBER PROCEDURE flush (
         self     IN OUT NOCOPY    utl_CharacterOutputStream),

    MEMBER PROCEDURE close (
         self     IN OUT NOCOPY utl_CharacterOutputStream)

     ) NOT FINAL;

##### Attributes

Table 296-5 UTL_CHARACTEROUTPUTSTREAM Type Member Subprograms

| Member Subprogram | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `WRITE`           | • \#1 - Writes the number of characters specified by `numChars` (default is 1) from parameter chars into the stream and returns the actual number of characters written. If the value of `lineFeed` is TRUE (default is `FALSE`) a `lineFeed` character is inserted after the last character.<br>• \#2 - writes the number of characters specified by parameter `numChars`, from parameter `chars` into the stream. The actual number of characters written is returned in parameter `numChars`. If the value of `lineFeed` is true (default is `FALSE`) a `lineFeed` character is inserted after the last character.<br>• \#3 - Writes the number of characters specified by parameter `numChars`, from parameter `chars`, beginning at `offset` specified by parameter offset. The actual number of characters written is returned in parameter `numChars`. If the value of `lineFeed` is true (default is `FALSE`) a `lineFeed` character is inserted after the last character . |
| `FLUSH`           | Copies all characters that may be contained within buffers to the node value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CLOSE`           | Releases all resources held by the stream                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
