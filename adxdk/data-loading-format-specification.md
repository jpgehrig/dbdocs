A description is given of version 1.0 of the Data Loading Format (DLF), which is the standard format for describing translated messages and seed data loaded into the database by the TransX utility.

**Related Topics**

- [Using the TransX Utility](using-TransX-utility.md)

### 23.1 Introduction to DLF

DLF defines a standard format for loading data with the TransX utility. It is intended to supersede loading data with SQL scripts. DLF provides these advantages:

- Format validation. Validation reduces errors during the translation and loading processes.

- Ease of use. The user does not have to maintain the character encoding of each data file to correspond with the language used in the data file.

DLF is based on the XML 1.0 specification.

**Note:**

TransX runs as the authenticated user. Be sure to review your data files, and load data files only from a trusted source.

#### 23.1.1 Naming Conventions for DLF

This section describes the naming conventions used in this document.

##### 23.1.1.1 Elements and Attributes

Naming conventions for elements and attributes that are used in this document are described.

- Standard English letters

- Lowercase letters only

- Hyphen (-) may be used for concatenation

- Attribute names must be consistently defined throughout

- Industry-standard terminology must be followed wherever possible

##### 23.1.1.2 Values

Values are case-sensitive except for some attribute values used for column names. All predefined attribute values are lowercase. No element values are defined by this specification.

##### 23.1.1.3 File Extensions

No file extension is recommended by this specification. A future version of this specification may recommend that documents use an extension that conforms with an 8.3 standard.

### 23.2 General Structure of DLF

Data Loading Format is XML, so it begins with an XML declaration. After the XML declaration comes the DLF document itself, enclosed within element `<table>`.

A DLF document is composed of these required sections:

- The `<lookup-key>` element contains a list of column names that determine whether existing rows in the database are duplicates of the rows in the data set definition included in the `<dataset>` element.

- The `<columns>` element contains metadata about the `<dataset>` element such as the names, data types, and attributes of columns.

- The `<dataset>` element contains a `<row>` element for each row, which in turn contains a `<col>` element that corresponds to a piece of data that is loaded in a database column. In this way a DLF document looks similar to the familiar tabular format in printing data in the database and allows easy editing.

DLF provides one optional section, which is enclosed within a `<translation>` element. This section may precede the required sections.

In addition, DLF provides information about TransX utility processing. Such information includes but is not limited to this:

- The `<query>` element is used to retrieve the value to be loaded to the column from a SQL query.

- The `sequence` attribute is used to retrieve the value to be loaded to the column from a sequence object in the database.

- The `constant` attribute is used to specify a constant value to the column.

- The `language` attribute is used to specify the language identifier to be loaded to the column.

#### 23.2.1 Tree Structure of DLF

The possible structure of a DLF document is shown as a tree. Each element is represented as `<element_name>`, where `element_name` is the name of an element. Attributes have no markup. Each element and attribute is followed by notation indicating its possible occurrence.

Table 23-1 describes the occurrence notation.

Table 23-1 Notation for Occurrence of Attributes and Elements

| Symbol    | Meaning                    |
|:----------|:---------------------------|
| 1         | one                        |
| \+        | one or more                |
| ?         | zero or one                |
| \*        | zero or more               |
| (a\|b\|c) | exactly one of a, b, and c |

Example 23-1 shows the tree structure of a DLF document. The elements are described in Elements in DLF. The attributes are described in Attributes in DLF.

Example 23-1 DLF Tree Structure

    <table>1
     |
     +---- lang?
     |
     +---- space?
     |
     +---- normalize-langtag?
     |
     +---- <translation>?
     |     |
     |     +---- <target>+
     |     |     |
     |     |     +---- <language ID>
     |     |
     |     +---- <restype>+
     |           |
     |           +---- name1
     |           |
     |           +---- expansion?
     |
     +---- <lookup-key>1
     |     |
     |     +---- <column>*
     |           |
     |           +---- name1
     |
     +---- <columns>1
     |     |
     |     +---- <column>+
     |           |
     |           +---- name1
     |           |
     |           +---- type1
     |           |
     |           +---- translate?
     |           |
     |           +---- translation-note?
     |           |
     |           +---- constant?
     |           |
     |           +---- language?
     |           |
     |           +---- sequence?
     |           |
     |           +---- virtual?
     |           |
     |           +---- useforupdate?
     |           |
     |           +---- maxsize?
     |           |
     |           +---- size-unit?
     |           |
     |           +---- restype?
     |           |
     |           +---- space?
     |           |
     |           +---- (<query>|<sql>)?
     |                 |
     |                 +---- text1
     |                 |
     |                 +---- <parameter>*
     |                       |
     |                       +---- id1
     |                       |
     |                       +---- (col|constant)1
     |                       |
     |                       +---- translate?
     |                       |
     |                       +---- trans-key?
     |                       |
     |                       +---- translation-note?
     |
     |
     +---- <dataset>1
           |
           +---- <row>+
                 |
                 +---- space?
                 |
                 +---- <col>*
                       |
                       +---- space?
                       |
                       +---- name1
                       |
                       +---- trans-key?
                       |
                       +---- translation-note?
                       |
                       +---- <the text element for the data>

### 23.3 DLF Specifications

Topics here include XML declarations, entity references, elements, and attributes in DLF.

#### 23.3.1 XML Declaration in DLF

The Extensible Markup Language (XML) declaration starts an XML entity. It indicates the XML version.

It can also declare the encoding of the file, as in this example:

    <?xml version="1.0" encoding="iso-8859-1" ?>

As in all XML files, the default encoding for a DLF file is assumed to be either 8-bit encoding of Unicode (UTF-8), which is a superset of the 7-bit ASCII character set, or 16-bit encoding of Unicode (UTF-16), which is conceptually 2-byte Universal Character Set (UCS-2) with surrogate pairs for code points above 65,535. Thus, for these character sets, the encoding declaration is not necessary. Furthermore, all XML parsers support these character sets. If the encoding is UTF-16, then the first character of the file must be the Unicode Byte-Order-Mark, \#xFEFF, which indicates the endianness of the file.

Other character sets supported by Oracle XML parsers include all Oracle character sets and commonly used Internet Assigned Numbers Authority (IANA) character set and Java encodings. The names of these character sets can be found in the parser documentation. You must declare these with encoding declarations if the document does not have an external source of encoding information such as from the execution environment or the network protocol. Therefore, Oracle recommends that you use a Unicode character encoding so that you can dispense with the encoding declaration. The recommended practice is to encode the document in UTF-8 and use this declaration:

    <?xml version="1.0" ?>

#### 23.3.2 Entity References in DLF

XML predefines five entity references: `&lt;`, `&gt;`, `&amp;`, `&apos;`, and `&quot;`.You must use entity references `&lt;` and `&amp;` in place of the characters they reference.

Table 23-2 Entity References

| Entity Reference | Meaning                                   |
|:-----------------|:------------------------------------------|
| `&lt;`           | Less than sign (`<`)                      |
| `&gt; `          | Greater than sign (`>`)                   |
| `&amp;`          | Ampersand (`&`)                           |
| `&apos;`         | Apostrophe or single quotation mark (`'`) |
| `&quot;`         | Straight, double quotation mark (`"`)     |

#### 23.3.3 Elements in DLF

Categories of DLF elements are described.

The DLF elements shown in Example 23-1 are divided into the categories described in Table 23-3. Attributes are shared among them. The attributes are described in Attributes in DLF.

Table 23-3 DLF Elements

| Type of Element         | Tag                                                        |
|:------------------------|:-----------------------------------------------------------|
| Top-Level Table Element | `<table>`                                                  |
| Translation Elements    | `<target>`, `<restype>`                                    |
| Lookup Key Elements     | `<lookup-key>`, `<column>`                                 |
| Metadata Elements       | `<columns>`, `<column>`, `<query>`, `<sql>`, `<parameter>` |
| Data Elements           | `<dataset>`, `<row>`, `<col>`                              |

##### 23.3.3.1 Top-Level Table Element

The top-level table element is described.

Table 23-4 Top-Level Table Element

| Tag       | Description                                                                        | Required Attributes | Optional Attributes                  | Contents                                                                                                                                 |
|:----------|:-----------------------------------------------------------------------------------|:--------------------|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| \<table\> | Corresponds to a single table. It encloses all the other elements of the document. | `name`              | `lang`, `space`, `normalize-langtag` | The order of the elements within `<table>` is:<br>1. `<translation>` (optional)<br>2. `<lookup-key>`<br>3. `<columns>`<br>4. `<dataset>` |

##### 23.3.3.2 Translation Elements

The translation elements are described.

Table 23-5 Translation Elements

| Tag             | Description                                                | Required Attributes | Optional Attributes | Contents                                                               |
|:----------------|:-----------------------------------------------------------|:--------------------|:--------------------|:-----------------------------------------------------------------------|
| `<translation>` | Contains generic information pertinent to translation.     | None                | None                | Zero or more `<target>` elements and zero or more `<restype>` elements |
| `<target>`      | Specifies a language to which this document is translated. | None                | None                | A language identifier as defined by \[IETFRFC1766\]                    |
| `<restype>`     | Declares a type of resource.                               | `name`              | `expansion`         | Empty element                                                          |

##### 23.3.3.3 Lookup Key Elements

The lookup key elements are described.

Table 23-6 Lookup Key Elements

| Tag            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Required Attributes | Optional Attributes | Contents                         |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|:--------------------|:---------------------------------|
| \<lookup-key\> | Contains the `<column>` element(s) based on which the TransX recognizes the rows as identical or duplicate.                                                                                                                                                                                                                                                                                                                                                 | `name`              | None                | Zero or more `<column>` elements |
| \<column\>     | A `<column>` element under `<lookup-key>` element indicates a column to be used to recognize the rows as identical or duplicate. Columns with the same values in specified column(s) are considered duplicate, regardless of the values in the other column(s). A lookup key `<column>` must have corresponding `<col>`umns in the `<dataset>` section or be declared as a `<column>` with a constant expression or a `<query>` in the `<columns>` section. | `name`              | None                | Empty element                    |

##### 23.3.3.4 Metadata Elements

The metadata elements are described.

Table 23-7 Metadata Elements

| Tag           | Description                                                                                                                                                                                                                                                | Required Attributes                                                                                                                                 | Optional Attributes                                                                                            | Contents                                 |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------|:-----------------------------------------|
| \<columns\>   | Contains data about the data to be loaded.                                                                                                                                                                                                                 | None                                                                                                                                                | None                                                                                                           | One or more `<column>` elements          |
| \<column\>    | Specifies a column that corresponds to `<col>` elements under the `<dataset>` element. After a `<column>` is defined the corresponding `<col>` element must appear in every `<row>` unless the column has the `sequence`, `constant` or `query` attribute. | `name`, , `type` in either order.<br>The recommended sequence is `name`, `type`, then optional attributes.                                          | `translate`, `constant`, `sequence`, `virtual`, `useforupdate`, `maxsize`, `size-unit`, `restype` in any order | Zero or one `<query>` or `<sql>` element |
| \<query\>     | Specifies a SQL query whose result is used to fill in the column to which this element belongs.                                                                                                                                                            | text                                                                                                                                                | None                                                                                                           | Zero or more `<parameter>` elements      |
| \<sql\>       | Specifies a SQL statement whose result, if any, is used to fill in the column to which this element belongs.                                                                                                                                               | text                                                                                                                                                | None                                                                                                           | Zero or more `<parameter>` elements      |
| \<parameter\> | Specifies a parameter of a `<query>` element.                                                                                                                                                                                                              | `id` and either `col` or `constant`.<br>If `col` is specified, the referenced column cannot have the `query`, `constant`, or `sequence` attributes. | `translate`, `trans-key`                                                                                       | Empty                                    |

##### 23.3.3.5 Data Elements

The data elements are `<dataset>`, `<row>`, and `<col>`.

Table 23-8 describes the data elements.

Table 23-8 Data Elements

| Tag         | Description                                                                                                                                                                              | Required Attributes | Optional Attributes | Contents                      |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|:--------------------|:------------------------------|
| `<dataset>` | Contains data to be loaded into the database.                                                                                                                                            | None                | None                | One or more `<row>` elements  |
| `<row>`     | Contains data about the data to be loaded `<dataset>` element.                                                                                                                           | None                | None                | Zero or more `<col>` elements |
| `<col>`     | Specifies an instance of a piece of data to be loaded to a database column, or for a virtual column, a piece of data to be used to get an actual data to be loaded to a database column. | `name`              | `trans-key`         | Data for use by applications  |

#### 23.3.4 Attributes in DLF

The various attributes used in the DLF elements are listed. An attribute is never specified more than once for each element. Along with some of the attributes are the recommended attribute values. Values for these attributes are case-sensitive.

Table 23-9 Attributes

| Type of Attribute        | Attributes                                                                                                                                                                                   |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DLF Attributes           | `name`, `type`, `translate`, `constant`, `sequence`, `virtual`, `useforupdate`, `maxsize`, `size-unit`, `restype`, `text`, `id`, `col`, `trans-key`, `translation-note`, `normalize-langtag` |
| XML Namespace Attributes | `xml:space`                                                                                                                                                                                  |

##### 23.3.4.1 DLF Attributes

The DLF attributes are described. These attributes are shared among the DLF elements.

Table 23-10 DLF Attributes

| Attribute           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Value Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Default Value                      | Used by Elements                   |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------|:-----------------------------------|
| `lang`              | Specifies the language of the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | This is equivalent to the `xml:lang` attribute.<br>The values of the attribute are language identifiers as defined by \[IETFRFC4646\].<br>This attribute does not affect data loading operation in any way.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | None; if absent, `"en"` is assumed | `<table>`                          |
| `normalize-langtag` | Specifies how to normalize the case of language tag.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | "`none`", "`standard`", "`uppercase`" or "`lowercase`".<br>The meanings are:<br>`none`—no normalization. the values in the language column on DLF are used as they are<br>`standard`—the style as recommended by the standards<br>\* lowercase for the 2 letter language code<br>\* uppercase for the 2 letter country code<br>\* titlecase for the 4 letter script code<br>\* lowercase for others<br>`uppercase`—uppercase everything<br>`lowercase`—lowercase everything                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | none                               | `<table>`                          |
| `space`             | Specifies how white spaces (ASCII spaces, tabs and line-breaks) are treated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | `"default"` or `"preserve"`<br>The value `"default"` signals that applications' default white-space processing modes are acceptable; the value `"preserve"` indicates the intent that applications preserve all white space. If this intent is declared at the root table element, it is considered to apply to all string data elements in the whole document. If declared at column level, it is considered to apply to the specified column of every row. If this attribute is declared in the `<dataset>` section, the intent applies only to the immediate text data. Declaration at the document or column level may be overridden with another instance of the space attribute.                                                                                                                                                                                                                                                                                                                                                                        | `"default"`                        | `<table>`, `<column>`, `<col>`     |
| `name`              | Specifies the name of an object such as table, column, restype, and so forth.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | String: This is a database table name for the `<table>` element, and a column name for the `<column>` or `<col>` element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Not applicable                     | `<table>`, `<column>`, `<col>`     |
| `type`              | The data type of a column in the data set. This attribute specifies the kind of text contained in the `<col>` element in the data set. Depending on this type, TransX may apply different processes to the data.<br>Because implicit data type conversion is provided by XSU and Java Database Connectivity (JDBC), TransX does not do its own parsing based on this type information. It uses this attribute to choose appropriate intermediate data types in Java for columns of `date` or `dateTime` type, in which case the standard date formats are accepted. | String: possible values are `"number"`, `"string"`, `"date"`, `"dateTime"` or `"binary"`.<br>The lexical representation of a value of number type must be supplied in the SQL language syntax, no matter what the current locale is. The SQL syntax uses no digit grouping separator (usually comma), but uses a dot as the decimal separator (usually dot).For the binary data type, the data value specified in a text field between the `col` tags indicates the name of a file that contains the actual binary data. Raw data cannot be embedded in the text field.For the other data types (`string`, `date`, and `dateTime`) the representation is constrained by the corresponding types in the XML Schema specification.For simplicity, DLF accepts only standard date formats of XML Schema in the form "CCYY-MM-DDThh:mm:ss" (dateTime) or "CCYY-MM-DD" (date). No other date format is recognized.<br>TransX uses this attribute for:<br>• Bind virtual columns to parameters of a query<br>• Bind the result of a query to a corresponding column | Not applicable                     | `<column>`                         |
| `translate`         | Indicates whether to translate the text of this column or parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Either `"yes"` or `"no"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `"no"`                             | `<column>`, `<parameter>`          |
| `constant`          | Specifies a constant value for this column or parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | The value of this column for every row                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Not applicable                     | `<column>`, `<parameter>`          |
| `language`          | Specifies language identifier for this column                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Language identifier or a placeholder. "%x" gets the value from the `xml:lang` attribute of the root table element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Not applicable                     | `<column>`                         |
| `sequence`          | Specifies a sequence in the database used to fill in the value for this column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | String: The name of a sequence in the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Not applicable                     | `<column>`                         |
| `virtual`           | Indicates that this column provides data used to construct another piece of data, which in turn is loaded into the database. A virtual column does not exist in the database. It is typically used to provide a value of a parameter in a query. A virtual column cannot be a lookup-key column. A virtual column with a query throws the result away.                                                                                                                                                                                                              | Either `"yes"` or `"no"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `"no"`                             | `<column>`                         |
| `useforupdate`      | Indicates whether to use the value of this column for the update when uploading seed data. This attribute has no effect unless TransX is in the mode to update duplicate rows. A virtual column cannot have this attribute set to `yes`.                                                                                                                                                                                                                                                                                                                            | Either `"yes"` or `"no"`. If this attribute is set to `"no"`, then the value of the column remains unchanged on the update operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | `"yes"`                            | `<column>`                         |
| `maxsize`           | Specifies the maximum size for the data for this column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Numeric value in the unit specified by the `size-unit` attribute. If this attribute is set and the `size-unit` is not set, the size is assumed to be in characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | None                               | `<column>`                         |
| `size-unit`         | Specifies the unit of size specified in the `maxsize` attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Units. Recommended values are `"char"` for characters, `"byte"` for bytes.<br>For supplemental characters, they take two `"char"` units.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | `"char"`                           | `<column>`                         |
| `restype`           | Indicates the type of data contained in this column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | A resource type. The value must match with the name of a `<restype>` element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | None                               | `<column>`                         |
| `expansion`         | Indicates the maximum size up to which translated strings are allowed to become longer for this type of resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                   | A numeric value in percentage of increase.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | `0%`                               | ` <restype>`                       |
| `text`              | Specifies a SQL query statement to get a value to put in the column to which the query belongs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | A SQL statement. Zero or more parameters can be specified with an identifier preceded by a colon. The statement returns a single row of a single value. Any excessive result is discarded.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Not applicable                     | `<query>`                          |
| `id`                | Specifies a placeholder used in a SQL query statement with parameters. The value of the column specified by the sibling `col` attribute is associated as a parameter to the query.                                                                                                                                                                                                                                                                                                                                                                                  | String: an identifier that appears in the text attribute of the parent query element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Empty string                       | `<parameter>`                      |
| `col`               | Specifies a column to be associated with a placeholder in the query specified by the sibling id attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                          | String: a column name. The column must be other than the column this attribute is a part of.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Not applicable                     | `<parameter>`                      |
| `trans-key`         | Specifies a key for translation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | String: a translation key. The value must be unique in a translation domain.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Not applicable                     | `<col>`, `<parameter>`             |
| `translation-note`  | Specifies notes for translation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | String: Translation notes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Not applicable                     | `<col>`, `<column>`, `<parameter>` |

##### 23.3.4.2 XML Namespace Attributes

The XML namespace attributes are described.

Table 23-11 XML Namespace Attributes

| Attribute   | Description                                                                 | Value Description                                                                                                                                                                                                                                                                                                                                                                                                                            | Default Value  | Used by Elements |
|:------------|:----------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------|:-----------------|
| `xml:space` | Specifies how white space (ASCII spaces, tabs and line-breaks) are treated. | `"default"` or `"preserve"`<br>The value `"default"` signals that applications' default white space processing modes are acceptable for this element; the value `"preserve"` indicates the intent that applications preserve all the white space. This declared intent is considered to apply to all elements within the content of the element where it is specified, unless overridden with another instance of the `xml:space` attribute. | `"default"`    | None             |
| `xml:lang`  | Specifies the language of the content.                                      | A language tag defined by RFC 4646.                                                                                                                                                                                                                                                                                                                                                                                                          | Not applicable | `table`          |

### 23.4 DLF Examples

Topics here include minimal, typical, and localized DLF documents.

#### 23.4.1 Minimal DLF Document

A minimal DLF document is presented.

Example 23-2 Minimal DLF Document

    <?xml version="1.0" ?>
    <table name="dual">
     <lookup-key/>
     <columns>
      <column name="DUMMY" type="string">
     </columns>
     <dataset>
      <row>
       <col name="DUMMY">X</col>
      </row>
     </dataset>
    </table>

#### 23.4.2 Typical DLF Document

A sample DLF document that contains seed data for table `CLK_STATUS_L` is presented.

Example 23-3 Sample DLF Document

    <!--
      - $Header: $
      -
      - Copyright (c) 2001 Oracle Corporation. All Rights Reserved.
      -
      - NAME
      -   status.xml - Seed file for the CLK_STATUS_L table
      -
      - DESCRIPTION
      -   This file contains seed data for the Status level table.
      -
      - NOTES
      -
      - MODIFIED   (MM/DD/YY)
      -   dchiba    06/11/01 - Adaption to enhancements of data loading tool
      -   dchiba    05/23/01 - Adaption to generic data loading tool
      -   rbolsius  05/07/01 - Created
      -->

    <table name="clk_status_l" xml:space="preserve">
      <lookup-key>
        <!--column name="status_id" /-->
        <column name="status_code" />
      </lookup-key>

      <columns>
        <column name="status_id"          type="number" sequence="clk_status_seq" useforupdate="no"/>
        <column name="status_code"        type="number" />
        <column name="status_name"        type="string" translate="yes" />
        <column name="status_description" type="string" translate="yes" />
        <column name="version_created"    type="number" constant="0" />
        <column name="version_updated"    type="number" constant="0" />
        <column name="status_type_code"   type="string" virtual="yes" />
        <column name="status_type_id"     type="number" >
          <query text="select status_type_id from clk_status_type_l where status_type_code = :1" >
            <parameter id="1" col="status_type_code" />
          </query>
        </column>
      </columns>

      <dataset>

        <row>
          <col name="status_code" >100</col>
          <col name="status_name" trans-key="stts-name-1" >Continue</col>
          <col name="status_description" trans-key="stts-desc-1" >
            The client should continue with its request.</col>
          <col name="status_type_code" >INFO</col>
        </row>

        <row>
          <col name="status_code" >101</col>
          <col name="status_name" trans-key="stts-name-2" >Switching Protocols</col>
          <col name="status_description" trans-key="stts-desc-2" >
            The server understands and is willing to comply with the client's
            request (via the Upgrade message header field) for a change in the
            application protocol being used on this connection.</col>
          <col name="status_type_code" >INFO</col>
        </row>

        <row>
          <col name="status_code" >200</col>
          <col name="status_name" trans-key="stts-name-3" >OK</col>
          <col name="status_description" trans-key="stts-desc-3" >
            The request has succeeded.</col>
          <col name="status_type_code" >SUCCESS</col>
        </row>

        <row>
          <col name="status_code" >201</col>
          <col name="status_name" trans-key="stts-name-4" >Created</col>
          <col name="status_description" trans-key="stts-desc-4" >
            The request has been fulfilled and resulted in a new resource being
            created.</col>
          <col name="status_type_code" >SUCCESS</col>
        </row>

        <row>
          <col name="status_code" >202</col>
          <col name="status_name" trans-key="stts-name-5" >Accepted</col>
          <col name="status_description" trans-key="stts-desc-5" >
            The request has been accepted for processing, but the processing has
            not been completed.</col>
          <col name="status_type_code" >SUCCESS</col>
        </row>

        <row>
          <col name="status_code" >203</col>
          <col name="status_name" trans-key="stts-name-6" >Non-Authoritative Information</col>
          <col name="status_description" trans-key="stts-desc-6" >
            The returned metainformation in the entity-header is not the
            definitive set as available from the origin server, but is gathered
            from a local or a third-party copy.</col>
          <col name="status_type_code" >SUCCESS</col>
        </row>

        <row>
          <col name="status_code" >204</col>
          <col name="status_name" trans-key="stts-name-7" >No Content</col>
          <col name="status_description" trans-key="stts-desc-7" >
            The server has fulfilled the request but does not need to return an
            entity-body, and might want to return updated metainformation.</col>
          <col name="status_type_code" >SUCCESS</col>
        </row>

        <!-- ... -->

      </dataset>
    </table>

#### 23.4.3 Localized DLF Document

An example of elements and attributes for localization is shown.

Example 23-4 DLF with Localization

    <?xml version="1.0"?>
    <table name="table_name" xml:lang="en" xml:space="preserve">

    <translation>
    <target>ar</target>
    <target>bs</target>
    <target>es</target>
    <restype name="alt" expansion="50%"/>
    <restype name="foo" expansion="50%"/>
    <restype name="bar" expansion="30%"/>
    </translation>

    <lookup-key><column name="resid" /></lookup-key>

    <columns>
    <column name="resid" type="number" sequence="seq_foo" useforupdate="no"/>
    <column name="image" type="binary"/>
    <column name="alt_text" type="string" translate="yes" maxsize="30"
            size-unit="byte" restype="alt"/>

    </columns>

    <dataset>
    <col name="image">foo1.gif</col>
    <col name="alt_text">Hello world</col>
    </dataset>

    </table>
