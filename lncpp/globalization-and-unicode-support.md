This chapter describes OCCI support for multibyte and Unicode charactersets.

This chapter contains these topics:

- Overview of Globalization and Unicode Support

- Specifying Charactersets

- Data Types for Globalization and Unicode Support

- About Using Objects and OTT Support

### 9.1 Overview of Globalization and Unicode Support

OCCI now enables application development in all Oracle supported multibyte and Unicode charactersets. The `UTF16` encoding of Unicode is fully supported. Application programs can specify their charactersets when the OCCI Environment is created. OCCI interfaces that take character string arguments (such as SQL statements, user names, error messages, object names, and so on) have been extended to handle data in any characterset. Character data from relational tables or objects can be in any characterset. OCCI can be used to develop multi-lingual, global and Unicode applications.

### 9.2 Specifying Charactersets

OCCI applications must specify the client characterset and client national characterset when initializing the OCCI Environment. The client characterset specifies the characterset for all SQL statements, object/user names, error messages, and data of all `CHAR` data type (`CHAR`, `VARCHAR2`, `LONG`) columns/attributes. The client national characterset specifies the characterset for data of all `NCHAR` data type (`NCHAR`, `NVARCHAR2`) columns/attributes.

A new `createEnvironment()` interface that takes the client characterset and client national characterset is now provided. This allows OCCI applications to set characterset information dynamically, independent of the `NLS_LANG` and `NLS_CHAR` initialization parameter.

Note that if an application specifies `OCCIUTF16` as the client characterset (first argument), then the application should use only the `UTF16` interfaces of OCCI. These interfaces take `UString` argument types.

The charactersets in the OCCI Environment are client-side only. They indicate the charactersets the OCCI application uses to interact with Oracle. The database characterset and database national characterset are specified when the database is created. Oracle converts all data from the client characterset/national characterset to the database characterset/national characterset before the server processes the data.

Example 9-1 How to Use Globalization and Unicode Support

    Environment *env = Environment:createEnvironment("JA16SJIS","UTF8");

This statement creates an OCCI `Environment` with `JA16SJIS` as the client characterset and `UTF8` as the client national characterset.

Any valid Oracle characterset name (except `AL16UTF16`) can be passed to `createEnvironment()`. An OCCI specific string `OCCIUTF16` (in uppercase) can be passed to specify `UTF16` as the characterset.

    Environment *env = Environment::createEnvironment("OCCIUTF16","OCCIUTF16");
    Environment *env = Environment::createEnvironment("US7ASCII", "OCCIUTF16");

### 9.3 Data Types for Globalization and Unicode Support

The data types used for supporting globalization and use of unicode include:

- Using the UString Data Type

- Using Multibyte and UTF16 data

- Using CLOB and NCLOB Data Types

#### 9.3.1 Using the UString Data Type

`UString` is a data type that enables applications and the OCCI library to pass and receive Unicode data in `UTF-16` encoding. `UString` is templated from the C++ `STL basic_string `with Oracle's `utext` data type.

    typedef basic_string<utext> UString;

Oracle's `utext` data type is a 2 byte short data type and represents Unicode characters in the UTF-16 encoding. A Unicode character's codepoint can be represented in 1 `utext` or 2 `utext`s (2 or 4 bytes). Characters from European and most Asian scripts are represented in a single utext. Supplementary characters defined in the Unicode 3.1 standard are represented with 2 `utext` elements.

In Microsoft Windows platforms, `UString` is equivalent to the C++ standard `wstring` data type. This is because the `wchar_t` data type is type defined to a 2 byte `short` in these platforms, which is same as Oracle's `utext`, allowing applications to use a `wstring` type variable where a `UString` would be normally required. Consequently, applications can also pass wide-character string literals, created by prefixing the literal with the letter 'L', to OCCI Unicode APIs.

OCCI applications should use the `UString` data type for data in `UTF16` characterset

Example 9-2 Using wstring Data Type

    //bind Unicode data using wstring data type
    //binding the Euro symbol, UTF16 codepoint 0x20AC
    wchar_t eurochars[] = {0x20AC,0x00};
    wstring eurostr(eurochars);
    stmt->setUString(1,eurostr);

    //Call the Unicode version of createConnection by
    //passing widechar literals
    Connection *conn = Connection(L"HR",L"password",L"");

#### 9.3.2 Using Multibyte and UTF16 data

For data in multibyte charactersets like `JA16SJIS` and `UTF8`, applications should use the C++ `string` type. The existing OCCI APIs that take `string` arguments can handle data in any multibyte characterset. Due to the use of `string `type, OCCI supports only byte length semantics for multibyte characterset `strings`.

Example 9-3 Binding UTF8 Data Using the string Data Type

    //bind UTF8 data
    //binding the Euro symbol, UTF8 codepoint : 0xE282AC
    char eurochars[] = {0xE2,0x82,0xAC,0x00};
    string eurostr(eurochars)
    stmt->setString(1,eurostr);//use the string interface

For Unicode data in the `UTF16` characterset, the OCCI specific data type: `UString` and the `OCCI UTF16` interfaces must be used.

Example 9-4 Binding UTF16 Data Using the UString Data Type

    //bind Unicode data using UString data type
    //binding the Euro symbol, UTF16 codepoint 0x20AC
    utext eurochars[] = {0x20AC,0x00};
    UString eurostr(eurochars);
    stmt->setUString(1,eurostr);//use the UString interface

#### 9.3.3 Using CLOB and NCLOB Data Types

Oracle provides the `CLOB` and `NCLOB` data types for storing and processing large amounts of character data. `CLOB`s represent data in the database characterset and `NCLOB`s represent data in the database national characterset. `CLOB`s and `NCLOB`s can be used as column types in relational tables and as attributes in object types.

The OCCI `Clob` class is used to work with both `CLOB` and `NCLOB` data types. If the database type is `NCLOB`, then the `Clob` set `CharSetForm()` method should be called with `OCCI_SQLCS_NCHAR` before reading/writing from the `LOB`.

The OCCI `Clob` class has support for multibyte and UTF16 charactersets. By default, the `Clob` interfaces assume the data is encoded in the client-side characterset (for both `CLOB`s and `NCLOB`s). To specify a different characterset or to specify the client-side national characterset for a `NCLOB`, call the `setCharSetId()` or `setCharSetIdUString()` methods with the appropriate characterset. The OCCI specific string 'OCCIUTF16' can be passed to indicate UTF16 as the characterset.

To read or write data in multibyte charactersets, use the existing read and write interfaces that take a char buffer. New overloaded interfaces that take utext buffers for `UTF16` data have been added to the [Clob Class](clob-class.md) as `read()`, `write()` and `writeChunk()` methods. The arguments and return values for these methods are either bytes or characters, depending on the characterset of the LOB.

Example 9-5 Using CLOB and NCLOB Data Types

    //client characterset - ZHT16BIG5, national characterset - UTF16
    Environment *env = Environment::createEnvironment("ZHT16BIG5","OCCIUTF16");...
    Clob nclobvar;
    //for NCLOBs, must call setCharSetForm method.
    nclobvar.setCharSetForm(OCCI_SQLCS_NCHAR);...
    //if reading/writing data in UTF16 for this NCLOB, still must
    //explicitly call setCharSetId
    nclobvar.setCharSetId("OCCIUTF16")


### 9.4 About Using Objects and OTT Support

Multibyte and `UTF16` charactersets are supported for handling character data in object attributes. All `CHAR` data type (`CHAR` or `VARCHAR2`) attributes hold data in the client-side characterset, while all `NCHAR` data type (`NCHAR` or `NVARCHAR2`) attributes hold data in the client-side national characterset. A member variable of `UString` data type represents an attribute in `UTF16` characterset.

**See Also:**

- [OCCI Application Programming Interface](occi-application-programing-interface.md): two new versions of [operator new()](pobject-class.md) that have been added to the [PObject Class](pobject-class.md) for object support

- [Object Type Translator Utility](object-type-translator-utility.md): a new [UNICODE](object-type-translator-utility.md) parameter that has been added for OTT utility support.
