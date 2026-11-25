## 212  DBMS_XMLQUERY

`DBMS_XMLQUERY` provides database-to-`XMLType` functionality.

**Note:**

With Oracle Database 18.1 Release, the `DBMS_XMLQUERY` package is deprecated. Use `DBMS_XMLGEN` instead.

The `DBMS_XMLQUERY` package has been replaced with improved technology. While Oracle recommends you not to begin development using `DBMS_XMLQUERY`, Oracle continues to support `DBMS_XMLQUERY` for reasons of backward compatibility. Your existing applications using `DBMS_XMLQUERY` will continue to work.

**See Also:**

For more information, see [DBMS_XMLGEN](DBMS_XMLGEN.md).

This chapter contains the following topics:

- DBMS_XMLQUERY Security Model

- DBMS_XMLQUERY Constants

- Types

- Summary of DBMS_XMLQUERY Subprograms

### 212.1 DBMS_XMLQUERY Security Model

Owned by `XDB`, the `DBMS_XMLQUERY` package must be created by `SYS` or `XDB`. The `EXECUTE` privilege is granted to `PUBLIC`.

Subprograms in this package are executed using the privileges of the current user.

### 212.2 DBMS_XMLQUERY Constants

The `DBMS_XMLQUERY` package includes several constants to use when specifying parameter values.

These constants are defined in the following table.

Table 212-1 Constants of DBMS_XMLQUERY

| Constant              | Description                                                                                                                                |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `DB_ENCODING`         | Used to signal that the DB character encoding is to be used.                                                                               |
| `DEFAULT_ROWSETTAG `  | The tag name for the element enclosing the XML generated from the result set (that is, for most cases the root node tag name) -- `ROWSET`. |
| `DEFAULT_ERRORTAG `   | The default tag to enclose raised errors -- `ERROR`.                                                                                       |
| `DEFAULT_ROWIDATTR`   | The default name for the cardinality attribute of XML elements corresponding to `db.records` -- `NUM`                                      |
| `DEFAULT_ROWTAG`      | The default tag name for the element corresponding to `db. records `--` ROW`                                                               |
| `DEFAULT_DATE_FORMAT` | Default date mask `--'MM/dd/yyyy HH:mm:ss'`                                                                                                |
| `ALL_ROWS`            | Indicates that all rows are needed in the output.                                                                                          |
| `NONE`                | Used to specifies that the output should not contain any XML metadata (for example, no DTD).                                               |
| `DTD`                 | Used to specify that the generation of the DTD is desired.                                                                                 |
| `SCHEMA`              | Used to specify that the generation of the XML Schema is desired.                                                                          |
| `LOWER_CASE`          | Use lower case tag names.                                                                                                                  |
| `UPPER_CASE`          | Use upper case tag names.                                                                                                                  |

### 212.3 Types

The `DBMS_XMLQUERY` subprograms use the `ctxType` type.

Table 212-2 Types of DBMS_XMLQUERY

| Type      | Description                                                                 |
|:----------|:----------------------------------------------------------------------------|
| `ctxType` | The type of the query context handle. This is the return type of NEWCONTEXT |

### 212.4 Summary of DBMS_XMLQUERY Subprograms

This table lists the DBMS_XMLQUERY subprograms and briefly describes them.

Table 212-3 DBMS_XMLQUERY Package Subprograms

| Method                     | Description                                                                                                                                                                  |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CLOSECONTEXT               | Closes or deallocates a particular query context.                                                                                                                            |
| GETDTD                     | Generates the DTD.                                                                                                                                                           |
| GETEXCEPTIONCONTENT        | Returns the thrown exception's error code and error message.                                                                                                                 |
| GETNUMROWSPROCESSED        | Returns the number of rows processed for the query.                                                                                                                          |
| GETVERSION                 | Prints the version of the XSU in use.                                                                                                                                        |
| GETXML                     | Generates the XML document.                                                                                                                                                  |
| NEWCONTEXT                 | Creates a query context and it returns the context handle.                                                                                                                   |
| PROPAGATEORIGINALEXCEPTION | Tells the XSU that if an exception is raised, and is being thrown, the XSU should throw the very exception raised; rather then, wrapping it with an `OracleXMLSQLException`. |
| REMOVEXSLTPARAM            | Removes a particular top-level stylesheet parameter.                                                                                                                         |
| SETBINDVALUE               | Sets a value for a particular bind name.                                                                                                                                     |
| SETCOLLIDATTRNAME          | Sets the name of the id attribute of the collection element's separator tag.                                                                                                 |
| SETDATAHEADER              | Sets the XML data header.                                                                                                                                                    |
| SETDATEFORMAT              | Sets the format of the generated dates in the XML document.                                                                                                                  |
| SETENCODINGTAG             | Sets the encoding processing instruction in the XML document.                                                                                                                |
| SETERRORTAG                | Sets the tag to be used to enclose the XML error documents.                                                                                                                  |
| SETMAXROWS                 | Sets the maximum number of rows to be converted to XML.                                                                                                                      |
| SETMETAHEADER              | Sets the XML meta header.                                                                                                                                                    |
| SETRAISEEXCEPTION          | Tells the XSU to throw the raised exceptions.                                                                                                                                |
| SETRAISENOROWSEXCEPTION    | Tells the XSU to throw or not to throw an `OracleXMLNoRowsException` in the case when for one reason or another, the XML document generated is empty.                        |
| SETROWIDATTRNAME           | Sets the name of the id attribute of the row enclosing tag.                                                                                                                  |
| SETROWIDATTRVALUE          | Specifies the scalar column whose value is to be assigned to the id attribute of the row enclosing tag.                                                                      |
| SETROWSETTAG               | Sets the tag to be used to enclose the XML dataset.                                                                                                                          |
| SETROWTAG                  | Sets the tag to be used to enclose the XML element.                                                                                                                          |
| SETSKIPROWS                | Sets the number of rows to skip.                                                                                                                                             |
| SETSQLTOXMLNAMEESCAPING    | This turns on or off escaping of XML tags in the case that the SQL object name, which is mapped to a XML identifier, is not a valid XML identifier.                          |
| SETSTYLESHEETHEADER        | Sets the stylesheet header.                                                                                                                                                  |
| SETTAGCASE                 | Specified the case of the generated XML tags.                                                                                                                                |
| SETXSLT                    | Registers a stylesheet to be applied to generated XML.                                                                                                                       |
| SETXSLTPARAM               | Sets the value of a top-level stylesheet parameter.                                                                                                                          |
| USENULLATTRIBUTEINDICATOR  | Specifies weather to use an XML attribute to indicate `NULL`ness.                                                                                                            |
| USETYPEFORCOLLELEMTAG      | Tells the XSU to use the collection element's type name as the collection element tag name.                                                                                  |

#### 212.4.1 CLOSECONTEXT

This procedure closes or deallocates a particular query context

##### Syntax

    PROCEDURE CLOSECONTEXT(
    ctxHdl IN ctxType);

Table 212-4 CLOSECONTEXT Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |

#### 212.4.2 GETDTD

Generates and returns the DTD based on the SQL query used to initialize the context. The options are described in the following table.

##### Syntax

Function that generates the DTD based on the SQL query that is used to initialize the context.

    FUNCTION GETDTD(
      ctxHdl IN ctxType,
      withVer IN BOOLEAN := false)
    RETURN CLOB;

Procedure that generates the DTD based on the SQL query that is used to initialize the context. Specifies the output `CLOB` for XML document result.

    PROCEDURE GETDTD(
      ctxHdl IN ctxType,
      xDoc IN CLOB,
      withVer IN BOOLEAN := false);

##### Parameters

Table 212-5 GETDTD Subprogram Parameters

| Parameter | IN / OUT | Description                                            |
|:----------|:---------|:-------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                        |
| `withVer` | `(IN)`   | Generate the version information? `TRUE` for yes`.`    |
| `xDoc`    | `(IN)`   | `CLOB` into which to write the generated XML document. |

#### 212.4.3 GETEXCEPTIONCONTENT

`GETEXCEPTIONCONTENT` returns the thrown exception's SQL error code and error message through the procedure's `OUT` parameters.

This procedure is a work around the JVM functionality that obscures the original exception by its own exception, rendering PL/SQL unable to access the original exception content.

##### Syntax

    PROCEDURE GETEXCEPTIONCONTENT(
      ctxHdl IN ctxType,
      errNo OUT NUMBER,
      errMsg OUT VARCHAR2);

##### Parameters

Table 212-6 GETEXCEPTIONCONTENT Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `errNo`   | `(OUT)`  | Error number.   |
| `errMsg`  | `(OUT)`  | Error message.  |

#### 212.4.4 GETNUMROWSPROCESSED

Return the number of rows processed for the query.

##### Syntax

    FUNCTION GETNUMROWSPROCESSED(
    ctxHdl IN ctxType)
    RETURN NUMBER;

Table 212-7 GETNUMROWSPROCESSED Function Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |

#### 212.4.5 GETVERSION

The `GETVERSION` procedure prints the version of the XSU in use.

##### Syntax

    PROCEDURE GETVERSION();

#### 212.4.6 GETXML

`GETXML` creates the new context, executes the query, gets the XML back and closes the context. This is a convenience function. The context does not need to be explicitly opened or closed.

##### Syntax

This function uses a SQL query in string form.

    FUNCTION GETXML(
      sqlQuery IN VARCHAR2,
      metaType IN NUMBER := NONE)
    RETURN CLOB;

This function uses a SQL query in `CLOB` form.

    FUNCTION GETXML(
      sqlQuery IN CLOB,
      metaType IN NUMBER := NONE)
    RETURN CLOB;

This function generates the XML document based on a SQL query used to initialize the context.

    FUNCTION GETXML(
      ctxHdl IN ctxType,
      metaType IN NUMBER := NONE)
    RETURN CLOB;

This procedure generates the XML document based on the SQL query used to initialize the context.

    PROCEDURE GETXML(
      ctxHdl IN ctxType,
      xDoc IN CLOB,
      metaType IN NUMBER := NONE);

##### Parameters

Table 212-8 GETXML Procedure Parameters

| Parameter  | IN / OUT | Description                                            |
|:-----------|:---------|:-------------------------------------------------------|
| `ctxHdl`   | `(IN)`   | Context handle.                                        |
| `metaType` | `(IN)`   | XML metadatatype (`NONE`, `DTD`, or `SCHEMA`).         |
| `sqlQuery` | `(IN)`   | SQL query.                                             |
| `xDoc`     | `(IN)`   | `CLOB` into which to write the generated XML document. |

#### 212.4.7 NEWCONTEXT

NEWCONTEXT creates a save context and returns the context handle.

##### Syntax

    FUNCTION NEWCONTEXT(
      sqlQuery IN VARCHAR2)
    RETURN ctxType;

    FUNCTION NEWCONTEXT(
      sqlQuery IN CLOB)
    RETURN ctxType;

##### Parameters

Table 212-9 NEWCONTEXT Function Parameters

| Parameter  | IN / OUT | Description                                        |
|:-----------|:---------|:---------------------------------------------------|
| `sqlQuery` | `(IN)`   | SQL query, the results of which to convert to XML. |

#### 212.4.8 PROPAGATEORIGINALEXCEPTION

The `PROPAGATEORIGINALEXCEPTION` procedure specifies whether to throw every original exception raised or to wrap it in an `OracleXMLSQLException`.

##### Syntax

    PROCEDURE PROPAGATEORIGINALEXCEPTION(
      ctxHdl IN ctxType,
      flag IN BOOLEAN);

##### Parameters

Table 212-10 PROPAGATEORIGINALEXCEPTION Procedure Parameters

| Parameter | IN / OUT | Description                                                                              |
|:----------|:---------|:-----------------------------------------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                                                          |
| `flag`    | `(IN)`   | `TRUE` if want to propagate original exception, `FALSE` to wrap in `OracleXMLException.` |

#### 212.4.9 REMOVEXSLTPARAM

This procedure removes the value of a top-level stylesheet parameter. If no stylesheet is registered, this method is not operational.

##### Syntax

    PROCEDURE REMOVEXSLTPARAM(
    ctxHdl IN ctxType,
    name IN VARCHAR2);

Table 212-11 REMOVEXSLTPARAM Procedure Parameters

| Parameter | IN / OUT | Description                                 |
|:----------|:---------|:--------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                             |
| `name`    | `(IN)`   | Name of the top level stylesheet parameter. |

#### 212.4.10 SETBINDVALUE

This procedure sets a value for a particular bind name.

##### Syntax

    PROCEDURE SETBINDVALUE(
    ctxHdl IN ctxType,
    bindName IN VARCHAR2,
    bindValue IN VARCHAR2);

Table 212-12 SETBINDVALUE Procedure Parameters

| Parameter   | IN / OUT | Description     |
|:------------|:---------|:----------------|
| `ctxHdl`    | `(IN)`   | Context handle. |
| `bindName`  | `(IN)`   | Bind name.      |
| `bindValue` | `(IN)`   | Bind value.     |

#### 212.4.11 SETCOLLIDATTRNAME

This procedure sets the name of the id attribute of the collection element's separator tag.

Passing `NULL` or an empty string for the tag causes the row id attribute to be omitted.

##### Syntax

    PROCEDURE SETCOLLIDATTRNAME(
    ctxHdl IN ctxType,
    attrName IN VARCHAR2);

Table 212-13 SETCOLLIDATTRNAME Procedure Parameters

| Parameter  | IN / OUT | Description     |
|:-----------|:---------|:----------------|
| `ctxHdl`   | `(IN)`   | Context handle. |
| `attrName` | `(IN)`   | Attribute name. |

#### 212.4.12 SETDATAHEADER

This procedure sets the XML data header.

The data header is an XML entity that is appended at the beginning of the query-generated XML entity, the `rowset`. The two entities are enclosed by the `docTag` argument. The last data header specified is used. Passing in `NULL` for the `header` parameter unsets the data header.

##### Syntax

    PROCEDURE SETDATAHEADER(
    ctxHdl IN ctxType,
    header IN CLOB := null,
    tag IN VARCHAR2 := null);

Table 212-14 SETDATAHEADER Procedure Parameters

| Parameter | IN / OUT | Description                                         |
|:----------|:---------|:----------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                     |
| `header`  | `(IN)`   | Header.                                             |
| `tag`     | `(IN)`   | Tag used to enclose the data header and the rowset. |

#### 212.4.13 SETDATEFORMAT

This procedure sets the format of the generated dates in the XML document.

The syntax of the date format pattern, the date mask, should conform to the requirements of the `java.text.SimpleDateFormat` class. Setting the mask to `NULL` or an empty string sets the default mask -- `DEFAULT_DATE_FORMAT`.

##### Syntax

    PROCEDURE SETDATEFORMAT(
    ctxHdl IN ctxType,
    mask IN VARCHAR2);

Table 212-15 SETDATEFORMAT Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `mask`    | `(IN)`   | The date mask.  |

#### 212.4.14 SETENCODINGTAG Procedure

This procedure sets the encoding processing instruction in the XML document.

##### Syntax

    PROCEDURE SETENCODINGTAG(
    ctxHdl IN ctxType,
    enc IN VARCHAR2 := DB_ENCODING);

Table 212-16 SETENCODINGTAG Procedure Parameters

| Parameter | IN / OUT | Description          |
|:----------|:---------|:---------------------|
| `ctxHdl`  | `(IN)`   | Context handle.      |
| `enc`     | `(IN)`   | The encoding to use. |

#### 212.4.15 SETERRORTAG Procedure

This procedure sets the tag to be used to enclose the XML error documents.

##### Syntax

    PROCEDURE SETERRORTAG(
    ctxHdl IN ctxType,
    tag IN VARCHAR2);

Table 212-17 SETERRORTAG Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `tag`     | `(IN)`   | Tag name.       |

#### 212.4.16 SETMAXROWS Procedure

This procedure sets the maximum number of rows to be converted to XML. By default, there is no set maximum.

##### Syntax

    PROCEDURE SETMAXROWS (
    ctxHdl IN ctxType,
    rows IN NUMBER);

Table 212-18 SETMAXROWS Procedure Parameters

| Parameter | IN / OUT | Description                         |
|:----------|:---------|:------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                     |
| `rows`    | `(IN)`   | Maximum number of rows to generate. |

#### 212.4.17 SETMETAHEADER Procedure

This procedure sets the XML meta header.

When set, the header is inserted at the beginning of the metadata part (DTD or XMLSchema) of each XML document generated by this object. The last meta header specified is used. Passing in `NULL` for the `header` parameter unsets the meta header.

##### Syntax

    PROCEDURE SETMETAHEADER(
    ctxHdl IN ctxType,
    header IN CLOB := null);

Table 212-19 SETMETAHEADER Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `Header`  | `(IN)`   | Header.         |

#### 212.4.18 SETRAISEEXCEPTION

This procedure specifies whether to throw raised exceptions.

If this call isn't made or if `FALSE` is passed to the `flag` argument, the XSU catches the SQL exceptions and generates an XML document from the exception message.

##### Syntax

    PROCEDURE SETRAISEEXCEPTION(
    ctxHdl IN ctxType,
    flag IN BOOLEAN:=true);

Table 212-20 SETRAISEEXCEPTION Procedure Parameters

| Parameter | IN / OUT | Description                                                 |
|:----------|:---------|:------------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                             |
| `flag`    | `(IN)`   | Throw raised exceptions? `TRUE` for yes, otherwise `FALSE.` |

#### 212.4.19 SETRAISENOROWSEXCEPTION

This procedure specifies whether to throw an `OracleXMLNoRowsException` when the generated XML document is empty. By default, the exception is not thrown.

##### Syntax

    PROCEDURE SETRAISENOROWSEXCEPTION(
    ctxHdl IN ctxType,
    flag IN BOOLEAN:=false);

Table 212-21 SETRAISENOROWSEXCEPTION Procedure Parameters

| Parameter | IN / OUT | Description                                            |
|:----------|:---------|:-------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                        |
| `flag`    | `(IN)`   | Throws an `OracleXMLNoRowsException` if set to `TRUE`. |

#### 212.4.20 SETROWIDATTRNAME

This procedure sets the name of the id attribute of the row enclosing tag. Passing `NULL` or an empty string for the tag causes the row id attribute to be omitted.

##### Syntax

    PROCEDURE SETROWIDATTRNAME(
    ctxHdl IN ctxType,
    attrName IN VARCHAR2);

Table 212-22 SETROWIDATTRNAME Procedure Parameters

| Parameter  | IN / OUT | Description     |
|:-----------|:---------|:----------------|
| `ctxHdl`   | `(IN)`   | Context handle. |
| `attrName` | `(IN)`   | Attribute name. |

#### 212.4.21 SETROWIDATTRVALUE

This procedure specifies the scalar column whose value is to be assigned to the id attribute of the row enclosing tag.

Passing `NULL` or an empty string for the `colName` assigns the row count value (0, 1, 2 and so on) to the row id attribute.

##### Syntax

    PROCEDURE SETROWIDATTRVALUE(
    ctxHdl IN ctxType,
    colName IN VARCHAR2);

Table 212-23 SETROWIDATTRVALUE Procedure Parameters

| Parameter | IN / OUT | Description                                                   |
|:----------|:---------|:--------------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                               |
| `colName` | `(IN)`   | Column whose value is to be assigned to the row id attribute. |

#### 212.4.22 SETROWSETTAG

This procedure sets the tag to be used to enclose the XML dataset.

##### Syntax

    PROCEDURE SETROWSETTAG(
    ctxHdl IN ctxType,
    tag IN VARCHAR2);

Table 212-24 SETROWSETTAG Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `tag`     | `(IN)`   | Tag name.       |

#### 212.4.23 SETROWTAG

This procedure sets the tag to be used to enclose the XML element corresponding to a `db.record`.

##### Syntax

    PROCEDURE SETROWTAG(
    ctxHdl IN ctxType,
    tag IN VARCHAR2);

Table 212-25 SETROWTAG Procedure Parameters

| Parameter | IN / OUT | Description     |
|:----------|:---------|:----------------|
| `ctxHdl`  | `(IN)`   | Context handle. |
| `tag`     | `(IN)`   | Tag name.       |

#### 212.4.24 SETSKIPROWS

`SETSKIPROWS` sets the number of rows to skip. By default, 0 rows are skipped.

##### Syntax

    PROCEDURE SETSKIPROWS(
    ctxHdl IN ctxType,
    rows IN NUMBER);

Table 212-26 SETSKIPROWS Procedure Parameters

| Parameter | IN / OUT | Description                     |
|:----------|:---------|:--------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                 |
| `rows`    | `(IN)`   | Maximum number of rows to skip. |

#### 212.4.25 SETSQLTOXMLNAMEESCAPING

This procedure turns on or off escaping of XML tags in the case that the SQL object name, which is mapped to a XML identifier, is not a valid XML identifier.

##### Syntax

    PROCEDURE SETSQLTOXMLNAMEESCAPING(
    ctxHdl IN ctxType,
    flag IN BOOLEAN := true);

Table 212-27 SETSQLTOXMLNAMEESCAPING Procedure Parameters

| Parameter | IN / OUT | Description                                          |
|:----------|:---------|:-----------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                      |
| `flag`    | `(IN)`   | Turn on escaping? `TRUE` for yes, otherwise `FALSE.` |

#### 212.4.26 SETSTYLESHEETHEADER

`SETSTYLESHEETHEADER` sets the stylesheet header (the stylesheet processing instructions) in the generated XML document.

Passing `NULL` for the `uri` argument will unset the stylesheet header and the stylesheet type.

##### Syntax

    PROCEDURE SETSTYLESHEETHEADER(
    ctxHdl IN ctxType,
    uri IN VARCHAR2,
    type IN VARCHAR2 := 'text/xsl');

Table 212-28 SETSTYLESHEETHEADER Procedure Parameters

| Parameter | IN / OUT | Description                                |
|:----------|:---------|:-------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                            |
| `uri`     | `(IN)`   | Stylesheet URI.                            |
| `type`    | `(IN)`   | Stylesheet type; defaults to "`text/xsl`". |

#### 212.4.27 SETTAGCASE

`SETTAGCASE` specifies the case of the generated XML tags.

##### Syntax

    PROCEDURE SETTAGCASE(
    ctxHdl IN ctxType,
    tCase IN NUMBER);

Table 212-29 SETTAGCASE Procedure Parameters

| Parameter | IN / OUT | Description                                                                   |
|:----------|:---------|:------------------------------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                                               |
| `tCase`   | `(IN)`   | The tag's case:<br>• 0 for as are<br>• 1 for lower case<br>• 2 for upper case |

#### 212.4.28 SETXSLT

`SETXSLT` registers a stylesheet to be applied to generated XML. If a stylesheet was already registered, it is replaced by the new one. Passing `NULL` for the `uri` argument, or `NULL` or an empty string for the `stylesheet` argument, unsets the stylesheet header and type.

##### Syntax

To unregister the stylesheet, pass in `NULL` for the URI.

    PROCEDURE SETXSLT(
      ctxHdl IN ctxType,
      uri IN VARCHAR2,
      ref IN VARCHAR2 := null);

To unregister the stylesheet pass in `NULL` or an empty string for the stylesheet.

    PROCEDURE SETXSLT(
      ctxHdl IN ctxType,
      stylesheet CLOB,
      ref IN VARCHAR2 := null);

##### Parameters

Table 212-30 SETXSLT Procedure Parameters

| Parameter    | IN / OUT | Description                                     |
|:-------------|:---------|:------------------------------------------------|
| `ctxHdl`     | `(IN)`   | Context handle.                                 |
| `uri`        | `(IN)`   | Stylesheet URI.                                 |
| `stylesheet` | `(IN)`   | Stylesheet.                                     |
| `ref`        | `(IN)`   | URL to include, imported and external entities. |

#### 212.4.29 SETXSLTPARAM

`SETXSLTPARAM` sets the value of a top-level stylesheet parameter.

The parameter value is expected to be a valid XPath expression; the string literal values would therefore have to be quoted explicitly. If no stylesheet is registered, this method is not operational.

##### Syntax

    PROCEDURE SETXSLTPARAM(
    ctxHdl IN ctxType,
    name IN VARCHAR2,
    value IN VARCHAR2);

Table 212-31 SETXSLTPARAM Procedure Parameters

| Parameter | IN / OUT | Description                                       |
|:----------|:---------|:--------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                   |
| `name`    | `(IN)`   | Name of the top level stylesheet parameter.       |
| `value`   | `(IN)`   | Value to be assigned to the stylesheet parameter. |

#### 212.4.30 USENULLATTRIBUTEINDICATOR

This procedure specifies whether to use an XML attribute to indicate `NULL`ness, or to do this by omitting the particular entity in the XML document.

##### Syntax

    PROCEDURE SETNULLATTRIBUTEINDICATOR(
    ctxHdl IN ctxType,
    flag IN BOOLEAN);

Table 212-32 USENULLATTRIBUTEINDICATOR Procedure Parameters

| Parameter | IN / OUT | Description                                                             |
|:----------|:---------|:------------------------------------------------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.                                                         |
| `flag`    | `(IN)`   | Sets attribute to `NULL` if `TRUE`, omits from XML document if `FALSE`. |

#### 212.4.31 USETYPEFORCOLLELEMTAG

This procedure specifies whether to use the collection element's type name as its element tag name.

By default, the tag name for elements of a collection is the collection's tag name followed by `_item`.

##### Syntax

    PROCEDURE USETYPEFORCOLLELEMTAG(
    ctxHdl IN ctxType,
    flag IN BOOLEAN := true);

Table 212-33 USETYPEFORCOLLELEMTAG Procedure Parameters

| Parameter | IN / OUT | Description                   |
|:----------|:---------|:------------------------------|
| `ctxHdl`  | `(IN)`   | Context handle.               |
| `flag`    | `(IN)`   | Turn on use of the type name? |
