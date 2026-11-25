## B  Unicode Character Code Assignments

This appendix provides an introduction to Unicode character assignments. This appendix contains the following topics:

- Unicode Code Ranges

- UTF-16 Encoding

- UTF-8 Encoding

### B.1 Unicode Code Ranges

Table B-1 contains code ranges that have been allocated in Unicode for UTF-16 character codes.

Table B-1 Unicode Character Code Ranges for UTF-16 Character Codes

| Types of Characters                                                                                                                       | First 16 Bits                                          | Second 16 Bits                            |
|:------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------|:------------------------------------------|
| ASCII                                                                                                                                     | 0000-007F                                              | \-                                        |
| European (except ASCII), Arabic, Hebrew                                                                                                   | 0080-07FF                                              | \-                                        |
| Iindic, Thai, certain symbols (such as the euro symbol), Chinese, Japanese, Korean                                                        | 0800-0FFF<br>1000 - CFFF<br>D000 - D7FF<br>F900 - FFFF | \-                                        |
| Private Use Area \#1                                                                                                                      | E000 - EFFF<br>F000 - F8FF                             | \-                                        |
| Supplementary characters: Additional Chinese, Japanese, and Korean characters; historic characters; musical symbols; mathematical symbols | D800 - D8BF<br>D8CO - DABF<br>DAC0 - DB7F              | DC00 - DFFF<br>DC00 - DFFF<br>DC00 - DFFF |
| Private Use Area \#2                                                                                                                      | DB80 - DBBF<br>DBC0 - DBFF                             | DC00 - DFFF<br>DC00 - DFFF                |

Table B-2 contains code ranges that have been allocated in Unicode for UTF-8 character codes.

Table B-2 Unicode Character Code Ranges for UTF-8 Character Codes

| Types of Characters                                                                                                                       | First Byte                | Second Byte                              | Third Byte                               | Fourth Byte                   |
|:------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------|:-----------------------------------------|:-----------------------------------------|:------------------------------|
| ASCII                                                                                                                                     | 00 - 7F                   | \-                                       | \-                                       | \-                            |
| European (except ASCII), Arabic, Hebrew                                                                                                   | C2 - DF                   | 80 - BF                                  | \-                                       | \-                            |
| Indic, Thai, certain symbols (such as the euro symbol), Chinese, Japanese, Korean                                                         | E0<br>E1 - EC<br>ED<br>EF | A0 - BF<br>80 - BF<br>80 - 9F<br>A4 - BF | 80 - BF<br>80 - BF<br>80 - BF<br>80 - BF | \-                            |
| Private Use Area \#1                                                                                                                      | EE<br>EF                  | 80 - BF<br>80 - A3                       | 80 - BF<br>80 - BF                       | \-                            |
| Supplementary characters: Additional Chinese, Japanese, and Korean characters; historic characters; musical symbols; mathematical symbols | F0<br>F1 - F2<br>F3       | 90 - BF<br>80 - BF<br>80 - AF            | 80 - BF<br>80 - BF<br>80 - BF            | 80 - BF<br>80 - BF<br>80 - BF |
| Private Use Area \#2                                                                                                                      | F3<br>F4                  | B0 - BF<br>80 - 8F                       | 80 - BF<br>80 - BF                       | 80 - BF<br>80 - BF            |

**Note:**

Blank spaces represent nonapplicable code assignments. Character codes are shown in hexadecimal representation.

### B.2 UTF-16 Encoding

As shown in Table B-1, UTF-16 character codes for some characters (Additional Chinese/Japanese/Korean characters and Private Use Area \#2) are represented in two units of 16-bits. These are supplementary characters. A supplementary character consists of two 16-bit values. The first 16-bit value is encoded in the range from 0xD800 to 0xDBFF. The second 16-bit value is encoded in the range from 0xDC00 to 0xDFFF. With supplementary characters, UTF-16 character codes can represent more than one million characters. Without supplementary characters, only 65,536 characters can be represented. The AL16UTF16 character set in Oracle Database supports supplementary characters.

**See Also:**

"[Code Points and Supplementary Characters](supporting-multilingual-databases-with-unicode.md)"

### B.3 UTF-8 Encoding

The UTF-8 character codes in Table B-2 show that the following conditions are true:

- ASCII characters use 1 byte

- European (except ASCII), Arabic, and Hebrew characters require 2 bytes

- Indic, Thai, Chinese, Japanese, and Korean characters as well as certain symbols such as the euro symbol require 3 bytes

- Characters in the Private Use Area \#1 require 3 bytes

- Supplementary characters require 4 bytes

- Characters in the Private Use Area \#2 require 4 bytes

In Oracle Database, the AL32UTF8 character set supports 1-byte, 2-byte, 3-byte, and 4-byte values. In Oracle Database, the UTF8 character set supports 1-byte, 2-byte, and 3-byte values, but not 4-byte values.
