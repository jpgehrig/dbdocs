Lists and describes cartridge services string formatting functions.

Table 29-6 lists the string formatting functions that are described in this section.

Table 29-6 String Formatting Functions

| Function          | Purpose                                           |
|:------------------|:--------------------------------------------------|
| OCIFormatInit()   | Initialize the OCIFormat package                  |
| OCIFormatString() | Write a text string into the supplied text buffer |
| OCIFormatTerm()   | Terminate the OCIFormat package                   |

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-cartridge-services.md) for more information about using these functions

### 29.7.1 OCIFormatInit()

Initializes the OCIFormat package.

#### Purpose

Initializes the OCIFormat package.

#### Syntax

    sword OCIFormatInit( void      *hndl,
                         OCIError  *err);

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

This routine must be called before calling any other OCIFormat routine, and it must be called only once.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.7.2 OCIFormatString()

Writes a text string into the supplied text buffer using the argument list submitted to it and in accordance with the format string given.

#### Purpose

Writes a text string into the supplied text buffer using the argument list submitted to it and in accordance with the format string given.

#### Syntax

    sword OCIFormatString( void          *hndl,
                           OCIError      *err,
                           OraText       *buffer,
                           sbig_ora       bufferLength,
                           sbig_ora      *returnLength,
                           const OraText *formatString,... );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

buffer (OUT)
The buffer that contains the string.

bufferLength (IN)
The length of the buffer in bytes.

returnLength (OUT)
The number of bytes written to the buffer (excluding the terminating `NULL`).

formatString (IN)
The format string, which can be any combination of literal text and format specifications. A format specification is delimited by the percent character (%) and is followed by any number (including none) of optional format modifiers, and terminated by a mandatory format code. If the format string ends with %, that is, with no format modifiers, or format specifier following it, then no action is taken. The format modifiers and format codes available are described in Table 29-7 and Table 29-8.

... (IN)
Variable number of arguments of the form `OCIFormat type wrapper`(`variable`) where `variable` must be a variable containing the value to be used. No constant values or expressions are allowed as arguments to the `OCIFormat type wrappers`; The `OCIFormat type wrappers` that are available are listed next. The argument list must be terminated with `OCIFormatEnd`.

`OCIFormatUb1(ub1 variable);`

`OCIFormatUb2(ub2 variable);`

`OCIFormatUb4(ub4 variable);`

`OCIFormatUword(uword variable);`

`OCIFormatUbig_ora(ubig_ora variable);`

`OCIFormatSb1(sb1 variable);`

`OCIFormatSb2(sb2 variable);`

`OCIFormatSb4(sb4 variable);`

`OCIFormatSword(sword variable);`

`OCIFormatSbig_ora(sbig_ora variable);`

`OCIFormatEb1(eb1 variable);`

`OCIFormatEb2(eb2 variable);`

`OCIFormatEb4(eb4 variable);`

`OCIFormatEword(eword variable);`

`OCIFormatChar (text variable);`

`OCIFormatText(const text *variable);`

`OCIFormatDouble(double variable);`

`OCIFormatDvoid(const dvoid *variable);`

`OCIFormatEnd `

#### Comments

The first call to this routine must be preceded by a call to the `OCIFormatInit()` routine that initializes the `OCIFormat` package for use. When this routine is no longer needed terminate the `OCIFormat` package by a call to the `OCIFormatTerm()` routine.

#### Format Modifiers

A format modifier alters or extends the format specification, allowing more specialized output. The format modifiers, as described in Table 29-7, can be in any order and are all optional.

Table 29-7 Format Modifier Flags

| Flag  | Operation                                                                   |
|:------|:----------------------------------------------------------------------------|
| `'-'` | Left-justify the output in the field.                                       |
| `'+'` | Always print a sign ('+' or '–') for numeric types.                         |
| `' '` | If a number's sign is not printed, then print a space in the sign position. |
| `'0'` | Pad numeric output with zeros, not spaces.                                  |

- If both the `'+'` and `' '` flags are used in the same format specification, then the `' ' `flag is ignored.

- If both the `'-'` and `'0'` flags are used in the same format specification, then the `'-'` flag is ignored.

Alternate output:

- For the octal format code, add a leading zero.

- For the hexadecimal format code, add a leading '0x'.

- For floating-point format codes, the output always has a radix character.

Field Width

`<w>` where `<w>` is a number specifying a minimum field width. The converted argument is printed in a field at least this wide, and wider if necessary. If the converted argument takes up fewer display positions than the field width, it is padded on the left (or right for left justification) to make up the field width. The padding character is normally a space, but it is a zero if the zero padding flag was specified. The special character `'*'` may be used for `<w>` and indicates the current argument is to be used for the field width value; the actual field or precision follows as the next sequential argument.

Precision

`.<p>` (a period followed by the number `<p>`), specifies the maximum number of display positions to print from a string, or digits after the radix point for a decimal number, or the minimum number of digits to print for an integer type (leading zeros are added to make up the difference). The special character `'*'` may be used for `<p>`, indicating that the current argument contains the precision value.

Argument Index

(`<n>`) where `<n>` is an integer index into the argument list with the first argument being 1. If no argument index is specified in a format specification, the first argument is selected. The next time no argument index is specified in a format specification, the second argument is selected, and so on. Format specifications with and without argument indexes can be in any order and are independent of each other in operation.

For example, the format string `"%u %(4)u %u %(2)u %u"` selects the first, fourth, second, second, and third arguments given to `OCIFormatString()`.

#### Format Codes

A format code specifies how to format an argument that is being written to a string.

Note that these format codes, as described in Table 29-8, can appear in uppercase, which causes all alphabetic characters in the output to appear in uppercase except for text strings, which are not converted.

Table 29-8 Format Codes to Specify How to Format an Argument Written to a String

| Codes | Operation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `'c'` | Single-byte character in the compiler character set                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `'d'` | Signed decimal integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `'e'` | Exponential (scientific) notation of the form \[`-]<d><r>[<d>...]e+[<d>]<d><d> `where `<r>` is the radix character for the current language and `<d>` is any single digit; the default precision is given by the constant `OCIFormatDP`. The precision may be optionally specified as a format modifier. Using a precision of 0 suppresses the radix character; the exponent is always printed in at least 2 digits, and can take up to 3 (for example, 1e+01, 1e+10, and 1e+100).                                                                        |
| `'f'` | Fixed decimal notation of the form `[-]<d>[<d>...]<r>[<d>...]` where `<r>` is the appropriate radix character for the current language and `<d>` is any single digit; the precision may be optionally specified as a format modifier. Using a precision of 0 suppresses the radix character. The default precision is given by the constant `OCIFormatDP`.                                                                                                                                                                                                |
| `'g'` | Variable floating-point notation; chooses `'e'` or `'f'`, selecting `'f'`' if the number fits in the specified precision (default precision if unspecified), and choosing `'e'` only if exponential format allows more significant digits to be printed; does not print a radix character if number has no fractional part                                                                                                                                                                                                                                |
| `'i'` | Identical to `'d'`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `'o'` | Unsigned octal integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `'p'` | Operating system-specific pointer printout                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `'s'` | Prints an argument using the default format code for its type:<br>`ociformatub<n>`, `ociformatuword`, `ociformatubig_ora`, `ociformateb<n>`, and `ociformateword`.<br>The format code used is 'u'.<br>`ociformatsb<n>`, `ociformatsword`, and `ociformatsbig_ora`.<br>The format code used is 'd'.<br>`ociformatchar`<br>The format code used is 'c'.<br>`ociformattext`<br>Prints text until trailing `NULL` is found.<br>`ociformatdouble`<br>The format code used is 'g'.<br>`ociformatdvoid`<br>The format code used is 'p'.<br>`' %' - print a '%'.` |
| `'u'` | Unsigned decimal integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 'x'   | Unsigned hexadecimal integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### Example

Using OCIFormatString() to Format a Date Two Different Ways for Two Countries

    /* This example shows the power of arbitrary argument    */
    /* selection in the context of internationalization.  A  */
    /* date is formatted in two different ways for two different */
    /* countries according to the format string, yet the      */
    /* argument list submitted to OCIFormatString remains    */
    /* invariant.                                            */

    text      buffer[255];
    ub1       day, month, year;
    OCIError *err;
    void     *hndl;
    sbig_ora  returnLen;

    /* Set the date. */

    day   = 10;
    month = 3;
    year  = 97;

    /* Work out the date in United States style: mm/dd/yy */
    OCIFormatString(hndl, err,
                    buffer, (sbig_ora)sizeof(buffer), &returnLen
                    (const text *)"%(2)02u/%(1)02u/%(3)02u",
                    OCIFormatUb1(day),
                    OCIFormatUb1(month),
                    OCIFormatUb1(year),
                    OCIFormatEnd);    /* Buffer is "03/10/97". */

    /* Work out the date in New Zealand style: dd/mm/yy */
    OCIFormatString(hndl, err,
                    buffer, (sbig_ora)sizeof(buffer), &returnLen
                    (const text *)"%(1)02u/%(2)02u/%(3)02u",
                    OCIFormatUb1(day),
                    OCIFormatUb1(month),
                    OCIFormatUb1(year),
                    OCIFormatEnd);    /* Buffer is "10/03/97". */

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIFormatInit()
- OCIFormatTerm()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.7.3 OCIFormatTerm()

Terminates the OCIFormat package.

#### Purpose

Terminates the OCIFormat package.

#### Syntax

    sword OCIFormatTerm( void     *hndl,
                         OCIError *err);

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

This function must be called after the OCIFormat package is no longer being used, and it must be called only once.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
