Lists and describes OCI character classification functions.

Table 31-5 lists the OCI character classification functions that are described in this section.

Table 31-5 OCI Character Classification Functions

| Function                  | Purpose                                                                                |
|:--------------------------|:---------------------------------------------------------------------------------------|
| OCIWideCharIsAlnum()      | Test whether the wide character is a letter or a decimal digit                         |
| OCIWideCharIsAlpha()      | Test whether the wide character is a letter                                            |
| OCIWideCharIsCntrl()      | Test whether the wide character is a control character                                 |
| OCIWideCharIsDigit()      | Test whether the wide character is a decimal digital character                         |
| OCIWideCharIsGraph()      | Test whether the wide character is a graph character                                   |
| OCIWideCharIsLower()      | Test whether the wide character is a lowercase character                               |
| OCIWideCharIsPrint()      | Test whether the wide character is a printable character                               |
| OCIWideCharIsPunct()      | Test whether the wide character is a punctuation character                             |
| OCIWideCharIsSingleByte() | Test whether the wide character is a single-byte character when converted to multibyte |
| OCIWideCharIsSpace()      | Test whether the wide character is a space character                                   |
| OCIWideCharIsUpper()      | Test whether the wide character is an uppercase character                              |
| OCIWideCharIsXdigit()     | Test whether the wide character is a hexadecimal digit                                 |

### 31.5.1 OCIWideCharIsAlnum()

Tests whether the wide character is a letter or a decimal digit.

#### Purpose

Tests whether a wide character is a letter or a decimal digit.

#### Syntax

    boolean OCIWideCharIsAlnum ( void       *hndl,
                                 OCIWchar    wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.2 OCIWideCharIsAlpha()

Tests whether the wide character is a letter.

#### Purpose

Tests whether a wide character is a letter.

#### Syntax

    boolean OCIWideCharIsAlpha ( void      *hndl,
                                 OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.3 OCIWideCharIsCntrl()

Tests whether the wide character is a control character.

#### Purpose

Tests whether a wide character is a control character.

#### Syntax

    boolean OCIWideCharIsCntrl ( void        *hndl,
                                 OCIWchar     wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.4 OCIWideCharIsDigit()

Test whether the wide character is a decimal digital character.

#### Purpose

Tests whether a wide character is a decimal digit character.

#### Syntax

    boolean OCIWideCharIsDigit ( void       *hndl,
                                 OCIWchar    wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.5 OCIWideCharIsGraph()

Tests whether a wide character is a graph character.

#### Purpose

A graph character is a character with a visible representation and normally includes alphabetic letters, decimal digits, and punctuation.

#### Syntax

    boolean OCIWideCharIsGraph ( void      *hndl,
                                 OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.6 OCIWideCharIsLower()

Tests whether a wide character is a lowercase letter.

#### Purpose

Tests whether a wide character is a lowercase letter.

#### Syntax

    boolean OCIWideCharIsLower ( void       *hndl,
                                 OCIWchar    wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.7 OCIWideCharIsPrint()

Tests whether a wide character is a printable character.

#### Purpose

Tests whether a wide character is a printable character.

#### Syntax

    boolean OCIWideCharIsPrint ( void      *hndl,
                                 OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.8 OCIWideCharIsPunct()

Tests whether a wide character is a punctuation character.

#### Purpose

Tests whether a wide character is a punctuation character.

#### Syntax

    boolean OCIWideCharIsPunct ( void       *hndl,
                                 OCIWchar    wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.9 OCIWideCharIsSingleByte()

Tests whether a wide character is a single-byte character when converted to multibyte.

#### Purpose

Tests whether a wide character is a single-byte character when converted to multibyte.

#### Syntax

    boolean OCIWideCharIsSingleByte ( void      *hndl,
                                      OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.10 OCIWideCharIsSpace()

Tests whether a wide character is a space character.

#### Purpose

A space character causes white space only in displayed text (for example, space, tab, carriage return, new line, vertical tab, or form feed).

#### Syntax

    boolean OCIWideCharIsSpace ( void     *hndl,
                                 OCIWchar  wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.11 OCIWideCharIsUpper()

Tests whether a wide character is an uppercase letter.

#### Purpose

Tests whether a wide character is an uppercase letter.

#### Syntax

    boolean OCIWideCharIsUpper ( void      *hndl,
                                 OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`

### 31.5.12 OCIWideCharIsXdigit()

Tests whether the wide character is a hexadecimal digit.

#### Purpose

Tests whether a wide character is a hexadecimal digit (0 through 9, A through F, a through f).

#### Syntax

    boolean OCIWideCharIsXdigit ( void      *hndl,
                                  OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for testing.

#### Returns

`TRUE` or `FALSE.`
