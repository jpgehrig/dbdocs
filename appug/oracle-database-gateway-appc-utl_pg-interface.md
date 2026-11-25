The Oracle Database Gateway for APPC requires the use of the RAW datatype to transfer data to and from PL/SQL without any alteration by Oracle Net. This is necessary because only the PL/SQL applications have information about the format of the data being sent to and received from the remote transaction programs. Oracle Net only has information about the systems where the PL/SQL application and the gateway server are running. If Oracle Net is allowed to perform translation on the data flowing between PL/SQL and the gateway, the data can end up in the wrong format.

Topics:

- UTL_PG Functions

- NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values

**Note:**

The IBM VS COBOL II compiler has been desupported. However, the string "`IBMVSCOBOLII`" is still used as the value of the compiler name parameter to represent any COBOL compiler you choose to use. The value `IBMVSCOBOLII` should still be used and does not create a dependency on any specific version of the compiler.

### UTL_PG Functions

The `UTL_PG` package is an extension to PL/SQL that provides a full set of functions for converting COBOL number formats into Oracle numbers and Oracle numbers into COBOL number formats.

`UTL_PG` conversion format RAWs are not portable in this release. Additionally, generation of conversion format RAWs on one system and transfer to another system is not supported.

The functions listed in this section are called in the standard PL/SQL manner:

    package_name.function_name(arguments)

Specifically for `UTL_PG` routines, this is:

    UTL_PG.function_name(arguments)

For each function listed below, the function name, arguments and their datatypes, and the return value datatype are provided. Unless otherwise specified, the parameters are `IN`, not `OUT`, parameters.

#### Common Parameters

The following `UTL_PG` functions share several similar parameters among themselves:

- `RAW_TO_NUMBER`

- `MAKE_NUMBER_TO_RAW_FORMAT`

- `MAKE_RAW_TO_NUMBER_FORMAT`

- `NUMBER_TO_RAW`

These similar parameters are described in detail in Table C-1 and then referenced only by name in subsequent tables listing the parameters for each `UTL_PG` function in this Appendix.

##### Common Input Parameters

Table C-1 describes the input parameters that are common to all of the `UTL_PG` functions:

Table C-1 Input Parameters Common to UTL_PG Function

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                       |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mask`     | is the compiler datatype mask. This is the datatype to be converted, specified in the source language of the named compiler (`compname`). This implies the internal format of the data as encoded according to the compiler and host platform.                                                                                                                                    |
| `maskopts` | is the compiler datatype mask options or `NULL`. These are additional options associated with the mask, as allowed or required, and are specified in the source language of `compname`. These can further qualify the type of conversion as necessary.                                                                                                                            |
| `envrnmnt` | is the compiler environment clause or `NULL`. These are additional options associated with the environment in which the remote data resides, as allowed or required, and is specified in the source language of` `compname. This parameter typically supplies aspects of data conversion dictated by customer standards, such as decimal point or currency symbols if applicable. |
| `compname` | is the compiler name. The only supported value is `IBMVSCOBOLII`.                                                                                                                                                                                                                                                                                                                 |
| `compopts` | is the compiler options or `NULL`.                                                                                                                                                                                                                                                                                                                                                |
| `nlslang`  | is the zoned decimal code page specified in Globalization Support format, `language_territory.charset`. This defaults to `AMERICAN_AMERICA.WE8EBCDIC37C`.                                                                                                                                                                                                                         |
| `wind`     | is the warning indicator. A Boolean indicator which controls whether conversion warning messages are to be returned in the wmsgblk `OUT` parameter.                                                                                                                                                                                                                               |
| `wmsgbsiz` | is the warning message block declared size in bytes. It is a `BINARY_INTEGER` set to the byte length of `wmsgblk`. The warning message block must be at least 512 and not more than 8192 bytes in length. When declaring `wmsgblk`, plan on approximately 512 bytes for each warning returned, depending on the nature of the requested conversion.                               |

##### Common Output Parameter

Table C-2 describes the output parameter that is common to the `UTL_PG` functions:

Table C-2 Output Parameters Common to UTL_PG Functions

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `wmsgblk` | is the warning message block. It is a RAW value which can contain multiple warnings in both full message and substituted parameter formats, if `wind` is `TRUE`. This parameter should be passed to the `WMSGCNT` function to test if warnings were issued and to `WMSG` to extract any warning that are present.<br>If `wind` is `TRUE` and no warnings are issued or if `wind` is `FALSE`, the length of `wmsgblk` is 0. This parameter does not need to be reset before each use. The warning message is documented in the [Oracle Database Error Messages ](../errmg/index.md) manual. This parameter must be allocated and passed as a parameter in all cases, regardless of how `wind` is specified. |

#### RAW_TO_NUMBER

`RAW_TO_NUMBER` converts a RAW byte-string `r` from the remote host internal format specified by `mask,` `maskopts,` `envrnmnt,` `compname,` `compopts,` and `nlslang` into an Oracle number.

Warnings are issued, if enabled, when the conversion specified conflicts with the conversion implied by the data or when conflicting format specifications are supplied.

For detailed information about the `mask,` `maskopts,` `envrnmnt,` `compname`, and `compopts` arguments, refer to "NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values".

##### Syntax

    function RAW_TO_NUMBER (r IN RAW,
     mask IN VARCHAR2,
     maskopts IN VARCHAR2,
     envrnmnt IN VARCHAR2,
     compname IN VARCHAR2,
     compopts IN VARCHAR2,
     nlslang IN VARCHAR2,
     wind IN BOOLEAN,
     wmsgbsiz IN BINARY_INTEGER,
     wmsgblk OUT RAW) RETURN NUMBER;

Where Table C-3 describes the parameters in this function:

Table C-3 RAW_TO_NUMBER Function Parameters

| Parameter  | Description                                                     |
|:-----------|:----------------------------------------------------------------|
| `r`        | is the remote host data to be converted.                        |
| `mask`     | is the compiler datatype mask.                                  |
| `maskopts` | are the compiler datatype mask options or `NULL`.               |
| `envrnmnt` | is the compiler environment clause or `NULL`.                   |
| `compname` | is the compiler name.                                           |
| `compopts` | are the compiler options or `NULL`.                             |
| `nlslang`  | is the zoned decimal code page in Globalization Support format. |
| `wind`     | is a warning indicator.                                         |
| `wmsgbsiz` | is the warning message block size in bytes.                     |
| `wmsgblk`  | is the warning message block. This is an `OUT` parameter.       |

##### Defaults and Optional Parameters

Table C-4 describes the default and optional parameters of the `RAW_TO_NUMBER` function:

Table C-4 Optional and Default Parameters of the RAW_TO_NUMBER Function

| Parameters | Description                    |
|:-----------|:-------------------------------|
| `maskopts` | null allowed, no default value |
| `envrnmnt` | null allowed, no default value |
| `compopts` | null allowed, no default value |

##### Return Value

An Oracle number corresponding in value to `r`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) for an explanation and information about how to handle it.

#### NUMBER_TO_RAW

`NUMBER_TO_RAW` converts an Oracle number `n` of declared precision and scale into a RAW byte-string in the remote host internal format specified by `mask`, `maskopts,` `envrnmnt,` `compname,` `compopts`, and `nlslang`.

Warnings are issued, if enabled, when the conversion specified conflicts with the conversion implied by the data or when conflicting format specifications are supplied.

For detailed information about the `mask,` `maskopts,` `envrnmnt,` `compname,` and `compopts` arguments, refer to"NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values".

##### Syntax

    function NUMBER_TO_RAW (n IN NUMBER,
     mask IN VARCHAR2,
     maskopts IN VARCHAR2,
     envrnmnt IN VARCHAR2,
     compname IN VARCHAR2,
     compopts IN VARCHAR2,
     nlslang IN VARCHAR2,
     wind IN BOOLEAN,
     wmsgbsiz IN BINARY_INTEGER,
     wmsgblk OUT RAW) RETURN RAW;

Where Table C-5 describes the parameters in this function:

Table C-5 NUMBER_TO_RAW Function Parameters

| Parameter  | Description                                                     |
|:-----------|:----------------------------------------------------------------|
| `n`        | is the Oracle number to be converted.                           |
| `mask`     | is the compiler datatype mask.                                  |
| `maskopts` | are the compiler datatype mask options or `NULL`.               |
| `envrnmnt` | is the compiler environment clause or `NULL`.                   |
| `compname` | is the compiler name.                                           |
| `compopts` | are the compiler options or `NULL`.                             |
| `nlslang`  | is the zoned decimal code page in Globalization Support format. |
| `wind`     | is a warning indicator`.`                                       |
| `wmsgbsiz` | is the warning message block size in bytes.                     |
| `wmsgblk`  | is the warning message block. This is an `OUT` parameter.       |

##### Defaults and Optional Parameters

Table C-6 describes the defaults and optional parameters for the `NUMBER_TO_RAW` function:

Table C-6 Defaults and Optional Parameters for NUMBER_TO_RAW Function

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `maskopts` | null allowed, no default value |
| `envrnmnt` | null allowed, no default value |
| `compopts` | null allowed, no default value |

##### Return Value

A RAW value corresponding in value to `n`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) for an explanation and information about how to handle it.

#### MAKE_RAW_TO_NUMBER_FORMAT

`MAKE_RAW_TO_NUMBER_FORMAT` makes a `RAW_TO_NUMBER` format conversion specification used to convert a RAW byte-string from the remote host internal format specified by `mask,` `maskopts,` `envrnmnt,` `compname,` `compopts,` and `nlslang` into an Oracle number of comparable precision and scale.

Warnings are issued, if enabled, when the conversion specified conflicts with the conversion implied by the data or when conflicting format specifications are supplied.

This function returns a RAW value containing the conversion format which can be passed to `UTL_PG.RAW_TO_NUMBER_FORMAT`.

For detailed information about the `mask,` `maskopts`, `envrnmnt`, `compname`, and `compopts` arguments, refer to "NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values".

##### Syntax

    function MAKE_RAW_TO_NUMBER_FORMAT (mask IN VARCHAR2,
     maskopts IN VARCHAR2,
     envrnmnt IN VARCHAR2,
     compname IN VARCHAR2,
     compopts IN VARCHAR2,
     nlslang IN VARCHAR2,
     wind IN BOOLEAN,
     wmsgbsiz IN BINARY_INTEGER,
     wmsgblk OUT RAW) RETURN RAW;

Where Table C-7 describes the parameters in this function:

Table C-7 MAKE_RAW_TO_NUMBER_FORMAT Function Parameters

| Parameter  | Description                                                     |
|:-----------|:----------------------------------------------------------------|
| `mask`     | is the compiler datatype mask.                                  |
| `maskopts` | are the compiler datatype mask options or `NULL`.               |
| `envrnmnt` | is the compiler environment clause or `NULL`.                   |
| `compname` | is the compiler name.                                           |
| `compopts` | are the compiler options or `NULL`.                             |
| `nlslang`  | is the zoned decimal code page in Globalization Support format. |
| `wind `    | is a warning indicator.                                         |
| `wmsgbsiz` | is the warning message block size in bytes.                     |
| `wmsgblk`  | is the warning message block. This is an `OUT` parameter.       |

##### Defaults and Optional Parameters

Table C-8 describes the defaults and optional parameters of the `MAKE_RAW_TO_NUMBER_FORMAT` function:

Table C-8 Default and Optional MAKE_RAW_TO_NUMBER_FORMAT Parameters

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `maskopts` | null allowed, no default value |
| `envrnmnt` | null allowed, no default value |
| `compopts` | null allowed, no default value |

##### Return Value

A `RAW(2048)` format conversion specification for `RAW_TO_NUMBER`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

#### MAKE_NUMBER_TO_RAW_FORMAT

`MAKE_NUMBER_TO_RAW_FORMAT` makes a `NUMBER_TO_RAW` format conversion specification used to convert an Oracle number of declared precision and scale to a RAW byte-string in the remote host internal format specified by `mask,` `maskopts,` `envrnmnt`, `compname`, `compopts`, and `nlslang.`

Warnings are issued, if enabled, when the conversion specified conflicts with the conversion implied by the data or when conflicting format specifications are supplied.

This function returns a RAW value containing the conversion format which can be passed to `UTL_PG.NUMBER_TO_RAW_FORMAT`. The implementation length of the result format RAW is 2048 bytes.

For detailed information about the `mask,` `maskopts,` `envrnmnt,` `compname`, and `compopts` arguments, refer to "NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values".

##### Syntax

    function MAKE_NUMBER_TO_RAW_FORMAT (mask IN VARCHAR2,
     maskopts IN VARCHAR2,
     envrnmnt IN VARCHAR2,
     compname IN VARCHAR2,
     compopts IN VARCHAR2,
     nlslang IN VARCHAR2,
     wind IN BOOLEAN,
     wmsgbsiz IN BINARY_INTEGER,
     wmsgblk OUT RAW) RETURN RAW;

Where Table C-9 describes the parameters in this function:

Table C-9 MAKE_NUMBER_TO_RAW_FORMAT Function Parameters

| Parameter  | Description                                                     |
|:-----------|:----------------------------------------------------------------|
| `mask`     | is the compiler datatype mask.                                  |
| `maskopts` | are the compiler datatype mask options or `NULL`.               |
| `envrnmnt` | is the compiler environment clause or `NULL`.                   |
| `compname` | is the compiler name.                                           |
| `compopts` | are the compiler options or `NULL`.                             |
| `nlslang`  | is the zoned decimal code page in Globalization Support format. |
| `wind`     | is a warning indicator`.`                                       |
| `wmsgbsiz` | is the warning message block size in bytes.                     |
| `wmsgblk`  | is the warning message block. This is an `OUT` parameter.       |

##### Defaults and Optional Parameters

Table C-10 describes the defaults and optional parameters for the `MAKE_NUMBER_TO_RAW_FORMAT` function:

Table C-10 Optional, Default Parameters: MAKE_NUMBER_TO_RAW_FORMAT

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `maskopts` | null allowed, no default value |
| `envrnmnt` | null allowed, no default value |
| `compopts` | null allowed, no default value |

##### Return Value

A `RAW(2048)` format conversion specification for `NUMBER_TO_RAW`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

#### RAW_TO_NUMBER_FORMAT

`RAW_TO_NUMBER_FORMAT` converts, according to the `RAW_TO_NUMBER` conversion format `r2nfmt`, a RAW byte-string `rawval` in the remote host internal format into an Oracle number.

##### Syntax

    function RAW_TO_NUMBER_FORMAT (rawval IN RAW,
     r2nfmt IN RAW) RETURN NUMBER;

where Table C-11 describes the parameters in this function:

Table C-11 RAW_TO_NUMBER_FORMAT Function Parameters

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `rawval`  | is the remote host data to be converted.                                         |
| `r2nfmt`  | is a `RAW(2048)` format specification returned from `MAKE_RAW_TO_NUMBER_FORMAT`. |

##### Defaults

None

##### Return Value

An Oracle number corresponding in value to `r`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

#### NUMBER_TO_RAW_FORMAT

`NUMBER_TO_RAW_FORMAT` converts, according to the `NUMBER_TO_RAW` conversion format `n2rfmt`, an Oracle number `numval` of declared precision and scale into a RAW byte-string in the remote host internal format.

##### Syntax

    function NUMBER_TO_RAW_FORMAT (numval IN NUMBER,
     n2rfmt IN RAW) RETURN RAW;

Where Table C-12 describes the parameters in this function:

Table C-12 NUMBER_TO_RAW_FORMAT Function Parameters

| Parameters | Description                                                                      |
|:-----------|:---------------------------------------------------------------------------------|
| `numval`   | is the Oracle number to be converted.                                            |
| `n2rfmt`   | is a `RAW(2048)` format specification returned from `MAKE_NUMBER_TO_RAW_FORMAT`. |

##### Defaults

None

##### Return Value

A RAW value corresponding in value to `n`.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

#### WMSGCNT

`WMSGCNT` tests a `wmsgblk` to determine how many warnings, if any, are present.

##### Syntax

    function WMSGCNT (wmsgblk IN RAW) RETURN BINARY_INTEGER;

Where Table C-13 describes the parameter in this function.

Table C-13 WMSGCNT Function Parameter

| Parameter | Description                                                                                                                                                                            |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `wmsgblk` | is the warning message block returned from one of the following functions:<br>• `MAKE_NUMBER_TO_RAW_FORMAT`<br>• `MAKE_RAW_TO_NUMBER_FORMAT`<br>• `NUMBER_TO_RAW`<br>• `RAW_TO_NUMBER` |

##### Defaults

None

##### Return Value

A `BINARY_INTEGER` value equal to the count of warnings present in the RAW `wmsgblk`.

Table C-14 lists possible returned values:

Table C-14 WMSGCNT Return Values

| Value | Description                                          |
|:------|:-----------------------------------------------------|
| `>0`  | indicates a count of warnings present in `wmsgblk`.  |
| `0`   | indicates that no warnings are present in `wmsgblk`. |

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

#### WMSG

`WMSG` extracts a warning message specified by `wmsgitem` from `wmsgblk`.

##### Syntax

    function WMSG (wmsgblk IN RAW,
     wmsgitem IN BINARY_INTEGER,
     wmsgno OUT BINARY_INTEGER,
     wmsgtext OUT VARCHAR2,
     wmsgfill OUT VARCHAR2) RETURN BINARY_INTEGER;

Where Table C-15 describes the parameters in this function:

Table C-15 WMSG Function Parameters

| Parameter  | Description                                                                                                                                                                                                                                                           |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `wmsgblk`  | is a RAW warning message block returned from one of the following functions:<br>• `MAKE_NUMBER_TO_RAW_FORMAT`<br>• `MAKE_RAW_TO_NUMBER_FORMAT`<br>• `NUMBER_TO_RAW`<br>• `RAW_TO_NUMBER`                                                                              |
| `wmsgitem` | is a `BINARY_INTEGER` value specifying which warning message to extract, numbered from `0` for the first warning through `n` minus 1 for the `n`th warning.                                                                                                           |
| `wmsgno`   | is an `OUT` parameter containing the `BINARY_INTEGER` (hexadecimal) value of the warning number. This value, after conversion to decimal, is documented in the [Oracle Database Error Messages ](../errmg/index.md)manual.                                            |
| `wmsgtext` | is a `VARCHAR2` `OUT` parameter value containing the fully-formatted warning message in ORA-xxxxx format, where xxxxx is the decimal warning number documented in the [Oracle Database Error Messages](../errmg/index.md) manual.                                     |
| `wmsgfill` | is a `VARCHAR2` `OUT` parameter value containing the list of warning message parameters to be substituted into a warning message in the following format:<br>warnparm1;;warnparm2;;...;;warnparmn<br>where each warning parameter is delimited by a double semicolon. |

##### Defaults

None

##### Return Value

A `BINARY_INTEGER` value containing a status return code.

A return code of "0" indicates that `wmsgno`, `wmsgtext`, and `wmsgfill` are assigned and valid.

##### Error and Warning Messages

If you receive an ORA-xxxx error or warning message, refer to the [Oracle Database Error Messages](../errmg/index.md) guide for an explanation and information about how to handle it.

Table C-16 describes the error messages you could receive:

Table C-16 WMSG Function Errors

| Error | Description                                                                                                                                                           |
|:------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-1`  | indicating the warning specified by` wmsgitem` was not found in `wmsgblk`.                                                                                            |
| `-2`  | indicating an invalid message block.                                                                                                                                  |
| `-3`  | indicating `wmsgblk `is too small to contain the warning associated with `wmsgitem`. A partial or no warning message might be present for this particular `wmsgitem`. |
| `-4`  | indicating there are too many substituted warning parameters.                                                                                                         |

### NUMBER_TO_RAW and RAW_TO_NUMBER Argument Values

This table lists the valid values for the format arguments for `NUMBER_TO_RAW` and `RAW_TO_NUMBER` and related functions. Following are examples of some valid COBOL picture masks. Any valid COBOL picture mask may be used. Refer to the appropriate IBM COBOL programming guides for an explanation of COBOL picture masks.

    mask: COBOL picture mask

      PIC  9(n)         where 1 <= n   <= 18
      PIC S9(n)         where 1 <= n   <= 18
      PIC  9(n)V9(s)    where 1 <= n+s <= 18
      PIC S9(n)V9(s)    where 1 <= n+s <= 18
      PIC S9999999V99
      PIC V99999
      PIC SV9(5)
      PIC  999.00
      PIC  99/99/99
      PIC  ZZZ.99
      PIC  PPP99
      PIC +999.99
      PIC  999.99+
      PIC -999.99
      PIC  999.99-
      PIC $$$$$,$$$.99
      PIC $9999.99DB
      PIC $9999.99CR

    maskopts: COBOL picture mask options

      COMP
      USAGE IS COMP
      USAGE IS COMPUTATIONAL
      COMP-3
      USAGE IS COMP-3
      USAGE IS COMPUTATIONAL-3
      COMP-4
      USAGE IS COMP-4
      USAGE IS COMPUTATIONAL-4
      DISPLAY
      USAGE IS DISPLAY
      SIGN IS LEADING
      SIGN IS LEADING SEPARATE
      SIGN IS LEADING SEPARATE CHARACTER
      SIGN IS TRAILING
      SIGN IS TRAILING SEPARATE
      SIGN IS TRAILING SEPARATE CHARACTER

    envrnmnt: COBOL environment clause

      CURRENCY SIGN IS x where x is a valid currency sign character
      DECIMAL-POINT IS COMMA

    compname: COBOL compiler name


      IBMVSCOBOLII

    compopts: COBOL compiler options

      (no values are supported at this time)
