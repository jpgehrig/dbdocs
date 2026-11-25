Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterSet.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterBuffer.md)
- [Next Class](CharacterSetWithConverter.md)

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

## Class CharacterSet

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.CharacterSet

<!-- -->

- Direct Known Subclasses:
  [CharacterSetWithConverter](CharacterSetWithConverter.md)

  ------------------------------------------------------------------------



      public abstract class CharacterSet
      extends Object

  This class encapsulates methods and attributes of the character sets defined by Oracle. It also defines a set of character set IDs that their character conversions are supported by Oracle JDBC.
  Most methods are of conversions between character representations.

  There are no public constructors. To create a CharacterSet use oracle.sql.CharacterSetFactory. There is no notion of "unsupported" character set. CharacterSet's can be created with any oracleId. However, there is a notion of unsupported conversions and the current implementation is limited to the small number of character sets for which constants are defined in the class

  There are two variants of an operation (e.g. convert vs. convertUnshared) the plain version is the fast (but possibly unsafe) one.

  The descriptions of methods in this class use the phrase "bytes in oracleId representation". What this means is that the bytes can be interpreted as a sequence of characters in the character set defined by oracleId. Both what characters are available and how they are represented as sequences of bytes is determined by oracleId.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                 |
    |-------------------|-------------------------------------------------------|
    | `static short`    | `AL16UTF16_CHARSET`                                   |
    | `static short`    | `AL16UTF16LE_CHARSET`                                 |
    | `static short`    | `AL24UTFFSS_CHARSET`                                  |
    | `static short`    | `AL32UTF8_CHARSET`                                    |
    | `static short`    | `AR8ADOS710_CHARSET`                                  |
    | `static short`    | `AR8ADOS710T_CHARSET`                                 |
    | `static short`    | `AR8ADOS720_CHARSET`                                  |
    | `static short`    | `AR8ADOS720T_CHARSET`                                 |
    | `static short`    | `AR8APTEC715_CHARSET`                                 |
    | `static short`    | `AR8APTEC715T_CHARSET`                                |
    | `static short`    | `AR8ARABICMAC_CHARSET`                                |
    | `static short`    | `AR8ARABICMACS_CHARSET`                               |
    | `static short`    | `AR8ARABICMACT_CHARSET`                               |
    | `static short`    | `AR8ASMO708PLUS_CHARSET`                              |
    | `static short`    | `AR8ASMO8X_CHARSET`                                   |
    | `static short`    | `AR8EBCDIC420S_CHARSET`                               |
    | `static short`    | `AR8EBCDICX_CHARSET`                                  |
    | `static short`    | `AR8HPARABIC8T_CHARSET`                               |
    | `static short`    | `AR8ISO8859P6_CHARSET`                                |
    | `static short`    | `AR8MSAWIN_CHARSET`                                   |
    | `static short`    | `AR8MSWIN1256_CHARSET`                                |
    | `static short`    | `AR8MUSSAD768_CHARSET`                                |
    | `static short`    | `AR8MUSSAD768T_CHARSET`                               |
    | `static short`    | `AR8NAFITHA711_CHARSET`                               |
    | `static short`    | `AR8NAFITHA711T_CHARSET`                              |
    | `static short`    | `AR8NAFITHA721_CHARSET`                               |
    | `static short`    | `AR8NAFITHA721T_CHARSET`                              |
    | `static short`    | `AR8SAKHR706_CHARSET`                                 |
    | `static short`    | `AR8SAKHR707_CHARSET`                                 |
    | `static short`    | `AR8SAKHR707T_CHARSET`                                |
    | `static short`    | `AR8XBASIC_CHARSET`                                   |
    | `static short`    | `ASCII_CHARSET`                                       |
    | `static short`    | `AZ8ISO8859P9E_CHARSET`                               |
    | `static short`    | `BG8MSWIN_CHARSET`                                    |
    | `static short`    | `BG8PC437S_CHARSET`                                   |
    | `static short`    | `BLT8CP921_CHARSET`                                   |
    | `static short`    | `BLT8EBCDIC1112_CHARSET`                              |
    | `static short`    | `BLT8EBCDIC1112S_CHARSET`                             |
    | `static short`    | `BLT8ISO8859P13_CHARSET`                              |
    | `static short`    | `BLT8MSWIN1257_CHARSET`                               |
    | `static short`    | `BLT8PC775_CHARSET`                                   |
    | `static short`    | `BN8BSCII_CHARSET`                                    |
    | `static short`    | `CDN8PC863_CHARSET`                                   |
    | `static short`    | `CE8BS2000_CHARSET`                                   |
    | `static short`    | `CEL8ISO8859P14_CHARSET`                              |
    | `static short`    | `CH7DEC_CHARSET`                                      |
    | `static short`    | `CL8BS2000_CHARSET`                                   |
    | `static short`    | `CL8EBCDIC1025_CHARSET`                               |
    | `static short`    | `CL8EBCDIC1025C_CHARSET`                              |
    | `static short`    | `CL8EBCDIC1025R_CHARSET`                              |
    | `static short`    | `CL8EBCDIC1025S_CHARSET`                              |
    | `static short`    | `CL8EBCDIC1025X_CHARSET`                              |
    | `static short`    | `CL8EBCDIC1158_CHARSET`                               |
    | `static short`    | `CL8EBCDIC1158R_CHARSET`                              |
    | `static short`    | `CL8ISO8859P5_CHARSET`                                |
    | `static short`    | `CL8ISOIR111_CHARSET`                                 |
    | `static short`    | `CL8KOI8R_CHARSET`                                    |
    | `static short`    | `CL8KOI8U_CHARSET`                                    |
    | `static short`    | `CL8MACCYRILLIC_CHARSET`                              |
    | `static short`    | `CL8MACCYRILLICS_CHARSET`                             |
    | `static short`    | `CL8MSWIN1251_CHARSET`                                |
    | `static short`    | `D7DEC_CHARSET`                                       |
    | `static short`    | `D7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `D8BS2000_CHARSET`                                    |
    | `static short`    | `D8EBCDIC1141_CHARSET`                                |
    | `static short`    | `D8EBCDIC273_CHARSET`                                 |
    | `static short`    | `DEFAULT_CHARSET`<br>Special value.                   |
    | `static short`    | `DK7SIEMENS9780X_CHARSET`                             |
    | `static short`    | `DK8BS2000_CHARSET`                                   |
    | `static short`    | `DK8EBCDIC1142_CHARSET`                               |
    | `static short`    | `DK8EBCDIC277_CHARSET`                                |
    | `static short`    | `E7DEC_CHARSET`                                       |
    | `static short`    | `E7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `E8BS2000_CHARSET`                                    |
    | `static short`    | `EE8BS2000_CHARSET`                                   |
    | `static short`    | `EE8EBCDIC870_CHARSET`                                |
    | `static short`    | `EE8EBCDIC870C_CHARSET`                               |
    | `static short`    | `EE8EBCDIC870S_CHARSET`                               |
    | `static short`    | `EE8ISO8859P2_CHARSET`                                |
    | `static short`    | `EE8MACCE_CHARSET`                                    |
    | `static short`    | `EE8MACCES_CHARSET`                                   |
    | `static short`    | `EE8MACCROATIAN_CHARSET`                              |
    | `static short`    | `EE8MACCROATIANS_CHARSET`                             |
    | `static short`    | `EE8MSWIN1250_CHARSET`                                |
    | `static short`    | `EE8PC852_CHARSET`                                    |
    | `static short`    | `EEC8EUROASCI_CHARSET`                                |
    | `static short`    | `EEC8EUROPA3_CHARSET`                                 |
    | `static short`    | `EL8DEC_CHARSET`                                      |
    | `static short`    | `EL8EBCDIC423R_CHARSET`                               |
    | `static short`    | `EL8EBCDIC875_CHARSET`                                |
    | `static short`    | `EL8EBCDIC875R_CHARSET`                               |
    | `static short`    | `EL8EBCDIC875S_CHARSET`                               |
    | `static short`    | `EL8GCOS7_CHARSET`                                    |
    | `static short`    | `EL8ISO8859P7_CHARSET`                                |
    | `static short`    | `EL8MACGREEK_CHARSET`                                 |
    | `static short`    | `EL8MACGREEKS_CHARSET`                                |
    | `static short`    | `EL8MSWIN1253_CHARSET`                                |
    | `static short`    | `EL8PC437S_CHARSET`                                   |
    | `static short`    | `EL8PC737_CHARSET`                                    |
    | `static short`    | `EL8PC851_CHARSET`                                    |
    | `static short`    | `EL8PC869_CHARSET`                                    |
    | `static short`    | `ET8MSWIN923_CHARSET`                                 |
    | `static short`    | `F7DEC_CHARSET`                                       |
    | `static short`    | `F7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `F8BS2000_CHARSET`                                    |
    | `static short`    | `F8EBCDIC1147_CHARSET`                                |
    | `static short`    | `F8EBCDIC297_CHARSET`                                 |
    | `static short`    | `HU8ABMOD_CHARSET`                                    |
    | `static short`    | `HU8CWI2_CHARSET`                                     |
    | `static short`    | `I7DEC_CHARSET`                                       |
    | `static short`    | `I7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `I8EBCDIC1144_CHARSET`                                |
    | `static short`    | `I8EBCDIC280_CHARSET`                                 |
    | `static short`    | `IN8ISCII_CHARSET`                                    |
    | `static short`    | `IS8MACICELANDIC_CHARSET`                             |
    | `static short`    | `IS8MACICELANDICS_CHARSET`                            |
    | `static short`    | `IS8PC861_CHARSET`                                    |
    | `static short`    | `ISO_LATIN_1_CHARSET`                                 |
    | `static short`    | `IW7IS960_CHARSET`                                    |
    | `static short`    | `IW8EBCDIC1086_CHARSET`                               |
    | `static short`    | `IW8EBCDIC424_CHARSET`                                |
    | `static short`    | `IW8EBCDIC424S_CHARSET`                               |
    | `static short`    | `IW8ISO8859P8_CHARSET`                                |
    | `static short`    | `IW8MACHEBREW_CHARSET`                                |
    | `static short`    | `IW8MACHEBREWS_CHARSET`                               |
    | `static short`    | `IW8MSWIN1255_CHARSET`                                |
    | `static short`    | `IW8PC1507_CHARSET`                                   |
    | `static short`    | `JA16DBCS_CHARSET`                                    |
    | `static short`    | `JA16EBCDIC930_CHARSET`                               |
    | `static short`    | `JA16EUC_CHARSET`                                     |
    | `static short`    | `JA16EUCTILDE_CHARSET`                                |
    | `static short`    | `JA16EUCYEN_CHARSET`                                  |
    | `static short`    | `JA16MACSJIS_CHARSET`                                 |
    | `static short`    | `JA16SJIS_CHARSET`                                    |
    | `static short`    | `JA16SJISTILDE_CHARSET`                               |
    | `static short`    | `JA16SJISYEN_CHARSET`                                 |
    | `static short`    | `JA16TSTSET_CHARSET`                                  |
    | `static short`    | `JA16TSTSET2_CHARSET`                                 |
    | `static short`    | `JA16VMS_CHARSET`                                     |
    | `static short`    | `KO16DBCS_CHARSET`                                    |
    | `static short`    | `KO16KSC5601_CHARSET`                                 |
    | `static short`    | `KO16KSCCS_CHARSET`                                   |
    | `static short`    | `KO16MSWIN949_CHARSET`                                |
    | `static short`    | `KO16TSTSET_CHARSET`                                  |
    | `static short`    | `LA8ISO6937_CHARSET`                                  |
    | `static short`    | `LA8PASSPORT_CHARSET`                                 |
    | `static short`    | `LT8MSWIN921_CHARSET`                                 |
    | `static short`    | `LT8PC772_CHARSET`                                    |
    | `static short`    | `LT8PC774_CHARSET`                                    |
    | `static short`    | `LV8PC1117_CHARSET`                                   |
    | `static short`    | `LV8PC8LR_CHARSET`                                    |
    | `static short`    | `LV8RST104090_CHARSET`                                |
    | `static short`    | `N7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `N8PC865_CHARSET`                                     |
    | `static short`    | `NDK7DEC_CHARSET`                                     |
    | `static short`    | `NE8ISO8859P10_CHARSET`                               |
    | `static short`    | `NEE8ISO8859P4_CHARSET`                               |
    | `static short`    | `NL7DEC_CHARSET`                                      |
    | `static short`    | `RU8BESTA_CHARSET`                                    |
    | `static short`    | `RU8PC855_CHARSET`                                    |
    | `static short`    | `RU8PC866_CHARSET`                                    |
    | `static short`    | `S7DEC_CHARSET`                                       |
    | `static short`    | `S7SIEMENS9780X_CHARSET`                              |
    | `static short`    | `S8BS2000_CHARSET`                                    |
    | `static short`    | `S8EBCDIC1143_CHARSET`                                |
    | `static short`    | `S8EBCDIC278_CHARSET`                                 |
    | `static short`    | `SE8ISO8859P3_CHARSET`                                |
    | `static short`    | `SF7ASCII_CHARSET`                                    |
    | `static short`    | `SF7DEC_CHARSET`                                      |
    | `static short`    | `TH8MACTHAI_CHARSET`                                  |
    | `static short`    | `TH8MACTHAIS_CHARSET`                                 |
    | `static short`    | `TH8TISASCII_CHARSET`                                 |
    | `static short`    | `TH8TISEBCDIC_CHARSET`                                |
    | `static short`    | `TH8TISEBCDICS_CHARSET`                               |
    | `static short`    | `TR7DEC_CHARSET`                                      |
    | `static short`    | `TR8DEC_CHARSET`                                      |
    | `static short`    | `TR8EBCDIC1026_CHARSET`                               |
    | `static short`    | `TR8EBCDIC1026S_CHARSET`                              |
    | `static short`    | `TR8MACTURKISH_CHARSET`                               |
    | `static short`    | `TR8MACTURKISHS_CHARSET`                              |
    | `static short`    | `TR8MSWIN1254_CHARSET`                                |
    | `static short`    | `TR8PC857_CHARSET`                                    |
    | `static short`    | `UNICODE_1_CHARSET`                                   |
    | `static short`    | `UNICODE_2_CHARSET`<br>This unicode is a "true UTF8". |
    | `static short`    | `US16TSTFIXED_CHARSET`                                |
    | `static short`    | `US7ASCII_CHARSET`                                    |
    | `static short`    | `US8BS2000_CHARSET`                                   |
    | `static short`    | `US8ICL_CHARSET`                                      |
    | `static short`    | `US8NOOP_CHARSET`                                     |
    | `static short`    | `US8PC437_CHARSET`                                    |
    | `static short`    | `UTF8_CHARSET`                                        |
    | `static short`    | `UTFE_CHARSET`                                        |
    | `static short`    | `VN8MSWIN1258_CHARSET`                                |
    | `static short`    | `VN8VN3_CHARSET`                                      |
    | `static short`    | `WE8BS2000_CHARSET`                                   |
    | `static short`    | `WE8BS2000E_CHARSET`                                  |
    | `static short`    | `WE8BS2000L5_CHARSET`                                 |
    | `static short`    | `WE8DEC_CHARSET`                                      |
    | `static short`    | `WE8DECTST_CHARSET`                                   |
    | `static short`    | `WE8DG_CHARSET`                                       |
    | `static short`    | `WE8EBCDIC1047_CHARSET`                               |
    | `static short`    | `WE8EBCDIC1047E_CHARSET`                              |
    | `static short`    | `WE8EBCDIC1140_CHARSET`                               |
    | `static short`    | `WE8EBCDIC1140C_CHARSET`                              |
    | `static short`    | `WE8EBCDIC1145_CHARSET`                               |
    | `static short`    | `WE8EBCDIC1146_CHARSET`                               |
    | `static short`    | `WE8EBCDIC1148_CHARSET`                               |
    | `static short`    | `WE8EBCDIC1148C_CHARSET`                              |
    | `static short`    | `WE8EBCDIC284_CHARSET`                                |
    | `static short`    | `WE8EBCDIC285_CHARSET`                                |
    | `static short`    | `WE8EBCDIC37_CHARSET`                                 |
    | `static short`    | `WE8EBCDIC37C_CHARSET`                                |
    | `static short`    | `WE8EBCDIC500_CHARSET`                                |
    | `static short`    | `WE8EBCDIC500C_CHARSET`                               |
    | `static short`    | `WE8EBCDIC871_CHARSET`                                |
    | `static short`    | `WE8EBCDIC924_CHARSET`                                |
    | `static short`    | `WE8GCOS7_CHARSET`                                    |
    | `static short`    | `WE8HP_CHARSET`                                       |
    | `static short`    | `WE8ICL_CHARSET`                                      |
    | `static short`    | `WE8ISO8859P1_CHARSET`                                |
    | `static short`    | `WE8ISO8859P15_CHARSET`                               |
    | `static short`    | `WE8ISO8859P9_CHARSET`                                |
    | `static short`    | `WE8ISOICLUK_CHARSET`                                 |
    | `static short`    | `WE8MACROMAN8_CHARSET`                                |
    | `static short`    | `WE8MACROMAN8S_CHARSET`                               |
    | `static short`    | `WE8MSWIN1252_CHARSET`                                |
    | `static short`    | `WE8NCR4970_CHARSET`                                  |
    | `static short`    | `WE8NEXTSTEP_CHARSET`                                 |
    | `static short`    | `WE8PC850_CHARSET`                                    |
    | `static short`    | `WE8PC858_CHARSET`                                    |
    | `static short`    | `WE8PC860_CHARSET`                                    |
    | `static short`    | `WE8ROMAN8_CHARSET`                                   |
    | `static short`    | `YUG7ASCII_CHARSET`                                   |
    | `static short`    | `ZHS16CGB231280_CHARSET`                              |
    | `static short`    | `ZHS16DBCS_CHARSET`                                   |
    | `static short`    | `ZHS16GBK_CHARSET`                                    |
    | `static short`    | `ZHS16MACCGB231280_CHARSET`                           |
    | `static short`    | `ZHS32GB18030_CHARSET`                                |
    | `static short`    | `ZHT16BIG5_CHARSET`                                   |
    | `static short`    | `ZHT16CCDC_CHARSET`                                   |
    | `static short`    | `ZHT16DBCS_CHARSET`                                   |
    | `static short`    | `ZHT16DBT_CHARSET`                                    |
    | `static short`    | `ZHT16HKSCS_CHARSET`                                  |
    | `static short`    | `ZHT16HKSCS31_CHARSET`                                |
    | `static short`    | `ZHT16MSWIN950_CHARSET`                               |
    | `static short`    | `ZHT32EUC_CHARSET`                                    |
    | `static short`    | `ZHT32SOPS_CHARSET`                                   |
    | `static short`    | `ZHT32TRIS_CHARSET`                                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                          | Method and Description                                                                                                                                                                                                                                                                                                                                 |
    |------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`                                                                                               | `AL16UTF16BytesToJavaChars``(byte[] bytes, int nbytes, char[] chars)`<br>Convert a sequence of bytes in AL16UTF16 to an array of chars caller needs to allocate the chars array                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `AL16UTF16BytesToString``(byte[] bytes, int nbytes)`<br>Convert a sequence of bytes in AL16UTF16 to a String this function will allocate a chars array                                                                                                                                                                                                 |
    | `static char[]`                                                                                            | `AL32UTF8ToJavaChar``(byte[] bytes, int offset, int count, boolean useReplacementCharacter)`<br>Converts an AL32UTF8 byte array to an array of char.                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `AL32UTF8ToString``(byte[] bytes, int offset, int nbytes)`<br>Convert a sequence of bytes in AL32UTF8 format to a String.                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `AL32UTF8ToString``(byte[] bytes, int offset, int nbytes, boolean useReplacementCharacter)`                                                                                                                                                                                                                                                            |
    | `abstract byte[]`                                                                                          | `convert``(CharacterSet from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation.                                                                                                                                                                                                              |
    | `abstract byte[]`                                                                                          | `convert``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Convert a String to bytes in oracleId representation.                                                                                                                                                                              |
    | `static int`                                                                                               | `convertAL16UTF16BytesToJavaChars``(byte[] bytes, int offset, char[] chars, int chars_offset, int count, boolean convertWithReplacement)`<br>Converts a sequence of bytes in AL16UTF16 to an array of char's.                                                                                                                                          |
    | `static int`                                                                                               | `convertAL16UTF16LEBytesToJavaChars``(byte[] bytes, int offset, char[] chars, int chars_offset, int count, boolean convertWithReplacement)`<br>Converts a sequence of bytes in AL16UTF16LE to an array of char's.                                                                                                                                      |
    | `static int`                                                                                               | `convertAL32UTF8BytesToJavaChars``(byte[] bytes, int offsetBytes, char[] chars, int offsetChars, int[] countArr, boolean convertWithReplacement)`<br>Convert a sequence of bytes in AL32UTF8 to an array of char's.                                                                                                                                    |
    | `static int`                                                                                               | `convertAL32UTF8BytesToJavaChars``(byte[] bytes, int offsetBytes, char[] chars, int offsetChars, int[] countArr, boolean convertWithReplacement, int charSize)`<br>Same as convertAL32UTF8BytesToJavaChars(byte\[\],int,char\[\],int,int\[\],boolean) with an additional argument 'charSize' which is the number of chars available in the char array. |
    | `static int`                                                                                               | `convertASCIIBytesToJavaChars``(byte[] bytes, int bytes_offset, char[] chars, int chars_offset, int count)`<br>convert a byte array in ascii to a Java char array.                                                                                                                                                                                     |
    | `static int`                                                                                               | `convertJavaCharsToAL16UTF16Bytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_offset, int nchars)`                                                                                                                                                                                                                                       |
    | `static int`                                                                                               | `convertJavaCharsToAL16UTF16LEBytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_offset, int nchars)`                                                                                                                                                                                                                                     |
    | `static int`                                                                                               | `convertJavaCharsToAL32UTF8Bytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_begin, int chars_count)`<br>Convert char's to the UTF-8 representation.                                                                                                                                                                                     |
    | `static int`                                                                                               | `convertJavaCharsToASCIIBytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_offset, int nchars)`<br>convert a Java char array to a byte array in ascii.                                                                                                                                                                                    |
    | `static int`                                                                                               | `convertJavaCharsToASCIIBytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_offset, int nchars, boolean strictConversion)`                                                                                                                                                                                                                 |
    | `static int`                                                                                               | `convertJavaCharsToISOLATIN1Bytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_offset, int nchars)`                                                                                                                                                                                                                                       |
    | `static int`                                                                                               | `convertJavaCharsToUTFBytes``(char[] chars, int chars_offset, byte[] bytes, int bytes_begin, int chars_count)`<br>Convert char's to the UTF8 representation.                                                                                                                                                                                           |
    | `byte[]`                                                                                                   | `convertUnshared``(CharacterSet from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation.                                                                                                                                                                                                      |
    | `static long`                                                                                              | `convertUTF32toUTF16``(long ucs4ch)`                                                                                                                                                                                                                                                                                                                   |
    | `static int`                                                                                               | `convertUTFBytesToJavaChars``(byte[] bytes, int offset, char[] chars, int chars_offset, int[] countArr, boolean convertWithReplacement)`<br>Convert a sequence of bytes in UTF8 to an array of char's.                                                                                                                                                 |
    | `static int`                                                                                               | `convertUTFBytesToJavaChars``(byte[] bytes, int offset, char[] chars, int chars_offset, int[] countArr, boolean convertWithReplacement, int charSize)`<br>Convert a sequence of bytes in UTF8 to an array of char's.                                                                                                                                   |
    | `byte[]`                                                                                                   | `convertWithReplacement``(char[] chars, int charOffset, byte[] bytes, int byteOffset, int[] nchars)`<br>Similar to convertWithReplacement(String s); Instead of a string, a char\[\] + offset with a length stored in nchars\[0\] will be converted.                                                                                                   |
    | `abstract byte[]`                                                                                          | `convertWithReplacement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Convert a String to bytes in oracleId representation.                                                                                                                                                               |
    | `int`                                                                                                      | `encodedByteLength``(char[] carray)`<br>Return the length of the byte array which would result if the char array were encoded in this character set                                                                                                                                                                                                    |
    | `int`                                                                                                      | `encodedByteLength``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Return the length of the byte array which would result if the String were encoded in this character set                                                                                                                  |
    | `boolean`                                                                                                  | `equals``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` rhs)`<br>Two CharacterSet's are equal when their oracleId's are equal                                                                                                                                                                      |
    | `protected oracle.jdbc.internal.OracleConnection`                                                          | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                             |
    | `int`                                                                                                      | `getOracleId``()`<br>The integer that identifies the character set.                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                      | `hashCode``()`<br>Implements a hash based on oracleId                                                                                                                                                                                                                                                                                                  |
    | `abstract boolean`                                                                                         | `isConvertibleFrom``(CharacterSet source)`<br>Are conversions supported.                                                                                                                                                                                                                                                                               |
    | `abstract boolean`                                                                                         | `isLossyFrom``(CharacterSet from)`<br>A conversion looses information if the mapping is not invertible.                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                  | `isUnicode``()`<br>Is this a Unicode Character Set.                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                  | `isUnknown``()`                                                                                                                                                                                                                                                                                                                                        |
    | `static int`                                                                                               | `javaCharsToAL16UTF16Bytes``(char[] chars, int nchars, byte[] bytes)`<br>Convert a sequence of chars in UCS2 to an array of bytes caller needs to allocate the bytes array                                                                                                                                                                             |
    | `static int`                                                                                               | `javaCharsToAL16UTF16LEBytes``(char[] chars, int nchars, byte[] bytes)`<br>Convert a sequence of chars in UCS2 to an array of bytes caller needs to allocate the bytes array                                                                                                                                                                           |
    | `static CharacterSet`                                                                                      | `make``(int oracleId)`<br>Factory.                                                                                                                                                                                                                                                                                                                     |
    | `static int`                                                                                               | `string32UTF8Length``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Returns the number of bytes in the UTF-8 representation of a String                                                                                                                                                     |
    | `static byte[]`                                                                                            | `stringToAL16UTF16Bytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert a String to an array of bytes this function will allocate the bytes array                                                                                                                                 |
    | `static byte[]`                                                                                            | `stringToAL16UTF16LEBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert a String to an array of bytes this function will allocate the bytes array                                                                                                                               |
    | `static byte[]`                                                                                            | `stringToAL32UTF8``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`                                                                                                                                                                                                                            |
    | `static byte[]`                                                                                            | `stringToASCII``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>convert a String to a byte array in ascii.                                                                                                                                                                                 |
    | `static byte[]`                                                                                            | `stringToUTF``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert the str to a byte array that in UTF8 representation.                                                                                                                                                                 |
    | `static int`                                                                                               | `stringUTFLength``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Returns the number of bytes in the UTF8 representation of a String                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)            | `toString``()`<br>The official name of the character set.                                                                                                                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)            | `toString``(byte[] bytes, int offset, int count)`<br>Convert bytes in oracleId representation to a String.                                                                                                                                                                                                                                             |
    | `abstract `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toStringWithReplacement``(byte[] bytes, int offset, int count)`<br>Convert bytes in oracleId representation to a String.                                                                                                                                                                                                                              |
    | `static char[]`                                                                                            | `UTFToJavaChar``(byte[] bytes, int offset, int count)`<br>Convert a sequence of bytes in UTF8 to an array of char's.                                                                                                                                                                                                                                   |
    | `static char[]`                                                                                            | `UTFToJavaChar``(byte[] bytes, int offset, int count, boolean useReplacementChar)`<br>Convert a sequence of bytes in UTF8 to an array of char's.                                                                                                                                                                                                       |
    | `static char[]`                                                                                            | `UTFToJavaCharWithReplacement``(byte[] bytes, int offset, int count)`<br>Convert a sequence of bytes in UTF8 to an array of char's.                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `UTFToString``(byte[] bytes, int offset, int nbytes)`<br>Convert a sequence of bytes in UTF8 to a String this function will to allocate the chars array                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `UTFToString``(byte[] bytes, int offset, int nbytes, boolean useReplacementChar)`<br>Convert a sequence of bytes in UTF8 to a String this function will to allocate the chars array                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### DEFAULT_CHARSET

          public static final short DEFAULT_CHARSET

      Special value. What character set it returned depends on where this class running. When run in the server this is the database character set. When run in a client ...
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ASCII_CHARSET

          public static final short ASCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ISO_LATIN_1_CHARSET

          public static final short ISO_LATIN_1_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UNICODE_1_CHARSET

          public static final short UNICODE_1_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US7ASCII_CHARSET

          public static final short US7ASCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8DEC_CHARSET

          public static final short WE8DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8HP_CHARSET

          public static final short WE8HP_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US8PC437_CHARSET

          public static final short US8PC437_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC37_CHARSET

          public static final short WE8EBCDIC37_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC500_CHARSET

          public static final short WE8EBCDIC500_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC285_CHARSET

          public static final short WE8EBCDIC285_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8PC850_CHARSET

          public static final short WE8PC850_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### D7DEC_CHARSET

          public static final short D7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### F7DEC_CHARSET

          public static final short F7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### S7DEC_CHARSET

          public static final short S7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### E7DEC_CHARSET

          public static final short E7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SF7ASCII_CHARSET

          public static final short SF7ASCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NDK7DEC_CHARSET

          public static final short NDK7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### I7DEC_CHARSET

          public static final short I7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NL7DEC_CHARSET

          public static final short NL7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CH7DEC_CHARSET

          public static final short CH7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### YUG7ASCII_CHARSET

          public static final short YUG7ASCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SF7DEC_CHARSET

          public static final short SF7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR7DEC_CHARSET

          public static final short TR7DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW7IS960_CHARSET

          public static final short IW7IS960_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IN8ISCII_CHARSET

          public static final short IN8ISCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ISO8859P1_CHARSET

          public static final short WE8ISO8859P1_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8ISO8859P2_CHARSET

          public static final short EE8ISO8859P2_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SE8ISO8859P3_CHARSET

          public static final short SE8ISO8859P3_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NEE8ISO8859P4_CHARSET

          public static final short NEE8ISO8859P4_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8ISO8859P5_CHARSET

          public static final short CL8ISO8859P5_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ISO8859P6_CHARSET

          public static final short AR8ISO8859P6_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8ISO8859P7_CHARSET

          public static final short EL8ISO8859P7_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8ISO8859P8_CHARSET

          public static final short IW8ISO8859P8_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ISO8859P9_CHARSET

          public static final short WE8ISO8859P9_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NE8ISO8859P10_CHARSET

          public static final short NE8ISO8859P10_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TH8TISASCII_CHARSET

          public static final short TH8TISASCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TH8TISEBCDIC_CHARSET

          public static final short TH8TISEBCDIC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BN8BSCII_CHARSET

          public static final short BN8BSCII_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### VN8VN3_CHARSET

          public static final short VN8VN3_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### VN8MSWIN1258_CHARSET

          public static final short VN8MSWIN1258_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ISO8859P15_CHARSET

          public static final short WE8ISO8859P15_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8NEXTSTEP_CHARSET

          public static final short WE8NEXTSTEP_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ASMO708PLUS_CHARSET

          public static final short AR8ASMO708PLUS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8EBCDICX_CHARSET

          public static final short AR8EBCDICX_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8XBASIC_CHARSET

          public static final short AR8XBASIC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8DEC_CHARSET

          public static final short EL8DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8DEC_CHARSET

          public static final short TR8DEC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC37C_CHARSET

          public static final short WE8EBCDIC37C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC500C_CHARSET

          public static final short WE8EBCDIC500C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8EBCDIC424_CHARSET

          public static final short IW8EBCDIC424_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8EBCDIC1026_CHARSET

          public static final short TR8EBCDIC1026_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC871_CHARSET

          public static final short WE8EBCDIC871_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC284_CHARSET

          public static final short WE8EBCDIC284_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1047_CHARSET

          public static final short WE8EBCDIC1047_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EEC8EUROASCI_CHARSET

          public static final short EEC8EUROASCI_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EEC8EUROPA3_CHARSET

          public static final short EEC8EUROPA3_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LA8PASSPORT_CHARSET

          public static final short LA8PASSPORT_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BG8PC437S_CHARSET

          public static final short BG8PC437S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8PC852_CHARSET

          public static final short EE8PC852_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RU8PC866_CHARSET

          public static final short RU8PC866_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RU8BESTA_CHARSET

          public static final short RU8BESTA_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8PC1507_CHARSET

          public static final short IW8PC1507_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RU8PC855_CHARSET

          public static final short RU8PC855_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8PC857_CHARSET

          public static final short TR8PC857_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8MACCYRILLIC_CHARSET

          public static final short CL8MACCYRILLIC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8MACCYRILLICS_CHARSET

          public static final short CL8MACCYRILLICS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8PC860_CHARSET

          public static final short WE8PC860_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IS8PC861_CHARSET

          public static final short IS8PC861_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8MACCES_CHARSET

          public static final short EE8MACCES_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8MACCROATIANS_CHARSET

          public static final short EE8MACCROATIANS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8MACTURKISHS_CHARSET

          public static final short TR8MACTURKISHS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IS8MACICELANDICS_CHARSET

          public static final short IS8MACICELANDICS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8MACGREEKS_CHARSET

          public static final short EL8MACGREEKS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8MACHEBREWS_CHARSET

          public static final short IW8MACHEBREWS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8MSWIN1250_CHARSET

          public static final short EE8MSWIN1250_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8MSWIN1251_CHARSET

          public static final short CL8MSWIN1251_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ET8MSWIN923_CHARSET

          public static final short ET8MSWIN923_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BG8MSWIN_CHARSET

          public static final short BG8MSWIN_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8MSWIN1253_CHARSET

          public static final short EL8MSWIN1253_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8MSWIN1255_CHARSET

          public static final short IW8MSWIN1255_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LT8MSWIN921_CHARSET

          public static final short LT8MSWIN921_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8MSWIN1254_CHARSET

          public static final short TR8MSWIN1254_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8MSWIN1252_CHARSET

          public static final short WE8MSWIN1252_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8MSWIN1257_CHARSET

          public static final short BLT8MSWIN1257_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### D8EBCDIC273_CHARSET

          public static final short D8EBCDIC273_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### I8EBCDIC280_CHARSET

          public static final short I8EBCDIC280_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DK8EBCDIC277_CHARSET

          public static final short DK8EBCDIC277_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### S8EBCDIC278_CHARSET

          public static final short S8EBCDIC278_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8EBCDIC870_CHARSET

          public static final short EE8EBCDIC870_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1025_CHARSET

          public static final short CL8EBCDIC1025_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### F8EBCDIC297_CHARSET

          public static final short F8EBCDIC297_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8EBCDIC1086_CHARSET

          public static final short IW8EBCDIC1086_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1025X_CHARSET

          public static final short CL8EBCDIC1025X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### N8PC865_CHARSET

          public static final short N8PC865_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8CP921_CHARSET

          public static final short BLT8CP921_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LV8PC1117_CHARSET

          public static final short LV8PC1117_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LV8PC8LR_CHARSET

          public static final short LV8PC8LR_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8EBCDIC1112_CHARSET

          public static final short BLT8EBCDIC1112_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LV8RST104090_CHARSET

          public static final short LV8RST104090_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8KOI8R_CHARSET

          public static final short CL8KOI8R_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8PC775_CHARSET

          public static final short BLT8PC775_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### F7SIEMENS9780X_CHARSET

          public static final short F7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### E7SIEMENS9780X_CHARSET

          public static final short E7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### S7SIEMENS9780X_CHARSET

          public static final short S7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DK7SIEMENS9780X_CHARSET

          public static final short DK7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### N7SIEMENS9780X_CHARSET

          public static final short N7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### I7SIEMENS9780X_CHARSET

          public static final short I7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### D7SIEMENS9780X_CHARSET

          public static final short D7SIEMENS9780X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8GCOS7_CHARSET

          public static final short WE8GCOS7_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8GCOS7_CHARSET

          public static final short EL8GCOS7_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US8BS2000_CHARSET

          public static final short US8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### D8BS2000_CHARSET

          public static final short D8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### F8BS2000_CHARSET

          public static final short F8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### E8BS2000_CHARSET

          public static final short E8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DK8BS2000_CHARSET

          public static final short DK8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### S8BS2000_CHARSET

          public static final short S8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8BS2000_CHARSET

          public static final short WE8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8BS2000_CHARSET

          public static final short CL8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8BS2000L5_CHARSET

          public static final short WE8BS2000L5_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8DG_CHARSET

          public static final short WE8DG_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8NCR4970_CHARSET

          public static final short WE8NCR4970_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ROMAN8_CHARSET

          public static final short WE8ROMAN8_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8MACCE_CHARSET

          public static final short EE8MACCE_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8MACCROATIAN_CHARSET

          public static final short EE8MACCROATIAN_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8MACTURKISH_CHARSET

          public static final short TR8MACTURKISH_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IS8MACICELANDIC_CHARSET

          public static final short IS8MACICELANDIC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8MACGREEK_CHARSET

          public static final short EL8MACGREEK_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8MACHEBREW_CHARSET

          public static final short IW8MACHEBREW_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US8ICL_CHARSET

          public static final short US8ICL_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ICL_CHARSET

          public static final short WE8ICL_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8ISOICLUK_CHARSET

          public static final short WE8ISOICLUK_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8MACROMAN8_CHARSET

          public static final short WE8MACROMAN8_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8MACROMAN8S_CHARSET

          public static final short WE8MACROMAN8S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TH8MACTHAI_CHARSET

          public static final short TH8MACTHAI_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TH8MACTHAIS_CHARSET

          public static final short TH8MACTHAIS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### HU8CWI2_CHARSET

          public static final short HU8CWI2_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8PC437S_CHARSET

          public static final short EL8PC437S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8EBCDIC875_CHARSET

          public static final short EL8EBCDIC875_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8PC737_CHARSET

          public static final short EL8PC737_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LT8PC772_CHARSET

          public static final short LT8PC772_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LT8PC774_CHARSET

          public static final short LT8PC774_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8PC869_CHARSET

          public static final short EL8PC869_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8PC851_CHARSET

          public static final short EL8PC851_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CDN8PC863_CHARSET

          public static final short CDN8PC863_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### HU8ABMOD_CHARSET

          public static final short HU8ABMOD_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ASMO8X_CHARSET

          public static final short AR8ASMO8X_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8NAFITHA711T_CHARSET

          public static final short AR8NAFITHA711T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8SAKHR707T_CHARSET

          public static final short AR8SAKHR707T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8MUSSAD768T_CHARSET

          public static final short AR8MUSSAD768T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ADOS710T_CHARSET

          public static final short AR8ADOS710T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ADOS720T_CHARSET

          public static final short AR8ADOS720T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8APTEC715T_CHARSET

          public static final short AR8APTEC715T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8NAFITHA721T_CHARSET

          public static final short AR8NAFITHA721T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8HPARABIC8T_CHARSET

          public static final short AR8HPARABIC8T_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8NAFITHA711_CHARSET

          public static final short AR8NAFITHA711_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8SAKHR707_CHARSET

          public static final short AR8SAKHR707_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8MUSSAD768_CHARSET

          public static final short AR8MUSSAD768_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ADOS710_CHARSET

          public static final short AR8ADOS710_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ADOS720_CHARSET

          public static final short AR8ADOS720_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8APTEC715_CHARSET

          public static final short AR8APTEC715_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8MSAWIN_CHARSET

          public static final short AR8MSAWIN_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8NAFITHA721_CHARSET

          public static final short AR8NAFITHA721_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8SAKHR706_CHARSET

          public static final short AR8SAKHR706_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ARABICMAC_CHARSET

          public static final short AR8ARABICMAC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ARABICMACS_CHARSET

          public static final short AR8ARABICMACS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8ARABICMACT_CHARSET

          public static final short AR8ARABICMACT_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LA8ISO6937_CHARSET

          public static final short LA8ISO6937_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US8NOOP_CHARSET

          public static final short US8NOOP_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8DECTST_CHARSET

          public static final short WE8DECTST_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16VMS_CHARSET

          public static final short JA16VMS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16EUC_CHARSET

          public static final short JA16EUC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16EUCYEN_CHARSET

          public static final short JA16EUCYEN_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16SJIS_CHARSET

          public static final short JA16SJIS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16DBCS_CHARSET

          public static final short JA16DBCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16SJISYEN_CHARSET

          public static final short JA16SJISYEN_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16EBCDIC930_CHARSET

          public static final short JA16EBCDIC930_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16MACSJIS_CHARSET

          public static final short JA16MACSJIS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16EUCTILDE_CHARSET

          public static final short JA16EUCTILDE_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16SJISTILDE_CHARSET

          public static final short JA16SJISTILDE_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KO16KSC5601_CHARSET

          public static final short KO16KSC5601_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KO16DBCS_CHARSET

          public static final short KO16DBCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KO16KSCCS_CHARSET

          public static final short KO16KSCCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KO16MSWIN949_CHARSET

          public static final short KO16MSWIN949_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHS16CGB231280_CHARSET

          public static final short ZHS16CGB231280_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHS16MACCGB231280_CHARSET

          public static final short ZHS16MACCGB231280_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHS16GBK_CHARSET

          public static final short ZHS16GBK_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHS16DBCS_CHARSET

          public static final short ZHS16DBCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHS32GB18030_CHARSET

          public static final short ZHS32GB18030_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT32EUC_CHARSET

          public static final short ZHT32EUC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT32SOPS_CHARSET

          public static final short ZHT32SOPS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16DBT_CHARSET

          public static final short ZHT16DBT_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT32TRIS_CHARSET

          public static final short ZHT32TRIS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16DBCS_CHARSET

          public static final short ZHT16DBCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16BIG5_CHARSET

          public static final short ZHT16BIG5_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16CCDC_CHARSET

          public static final short ZHT16CCDC_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16MSWIN950_CHARSET

          public static final short ZHT16MSWIN950_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AL24UTFFSS_CHARSET

          public static final short AL24UTFFSS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UTF8_CHARSET

          public static final short UTF8_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UTFE_CHARSET

          public static final short UTFE_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AL32UTF8_CHARSET

          public static final short AL32UTF8_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KO16TSTSET_CHARSET

          public static final short KO16TSTSET_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16TSTSET2_CHARSET

          public static final short JA16TSTSET2_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JA16TSTSET_CHARSET

          public static final short JA16TSTSET_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### US16TSTFIXED_CHARSET

          public static final short US16TSTFIXED_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AL16UTF16_CHARSET

          public static final short AL16UTF16_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AL16UTF16LE_CHARSET

          public static final short AL16UTF16LE_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TH8TISEBCDICS_CHARSET

          public static final short TH8TISEBCDICS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8EBCDIC1112S_CHARSET

          public static final short BLT8EBCDIC1112S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CE8BS2000_CHARSET

          public static final short CE8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1025R_CHARSET

          public static final short CL8EBCDIC1025R_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1158R_CHARSET

          public static final short CL8EBCDIC1158R_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### D8EBCDIC1141_CHARSET

          public static final short D8EBCDIC1141_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DK8EBCDIC1142_CHARSET

          public static final short DK8EBCDIC1142_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8BS2000_CHARSET

          public static final short EE8BS2000_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8EBCDIC870S_CHARSET

          public static final short EE8EBCDIC870S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8EBCDIC423R_CHARSET

          public static final short EL8EBCDIC423R_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8EBCDIC875S_CHARSET

          public static final short EL8EBCDIC875S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EL8EBCDIC875R_CHARSET

          public static final short EL8EBCDIC875R_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### F8EBCDIC1147_CHARSET

          public static final short F8EBCDIC1147_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### I8EBCDIC1144_CHARSET

          public static final short I8EBCDIC1144_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8BS2000E_CHARSET

          public static final short WE8BS2000E_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1047E_CHARSET

          public static final short WE8EBCDIC1047E_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1140_CHARSET

          public static final short WE8EBCDIC1140_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1145_CHARSET

          public static final short WE8EBCDIC1145_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1146_CHARSET

          public static final short WE8EBCDIC1146_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1148_CHARSET

          public static final short WE8EBCDIC1148_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8EBCDIC420S_CHARSET

          public static final short AR8EBCDIC420S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IW8EBCDIC424S_CHARSET

          public static final short IW8EBCDIC424S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TR8EBCDIC1026S_CHARSET

          public static final short TR8EBCDIC1026S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16HKSCS_CHARSET

          public static final short ZHT16HKSCS_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLT8ISO8859P13_CHARSET

          public static final short BLT8ISO8859P13_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AR8MSWIN1256_CHARSET

          public static final short AR8MSWIN1256_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### S8EBCDIC1143_CHARSET

          public static final short S8EBCDIC1143_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ZHT16HKSCS31_CHARSET

          public static final short ZHT16HKSCS31_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### AZ8ISO8859P9E_CHARSET

          public static final short AZ8ISO8859P9E_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CEL8ISO8859P14_CHARSET

          public static final short CEL8ISO8859P14_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8ISOIR111_CHARSET

          public static final short CL8ISOIR111_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8KOI8U_CHARSET

          public static final short CL8KOI8U_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8PC858_CHARSET

          public static final short WE8PC858_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1025C_CHARSET

          public static final short CL8EBCDIC1025C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1025S_CHARSET

          public static final short CL8EBCDIC1025S_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CL8EBCDIC1158_CHARSET

          public static final short CL8EBCDIC1158_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EE8EBCDIC870C_CHARSET

          public static final short EE8EBCDIC870C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC924_CHARSET

          public static final short WE8EBCDIC924_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1140C_CHARSET

          public static final short WE8EBCDIC1140C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### WE8EBCDIC1148C_CHARSET

          public static final short WE8EBCDIC1148C_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UNICODE_2_CHARSET

          public static final short UNICODE_2_CHARSET

      This unicode is a "true UTF8". That means null bytes can appear (unlike Java UTF8 where null bytes are always represented by two non-null bytes
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### make

          public static CharacterSet make(int oracleId)

      Factory. A factory is used rather than a constructor because CharacterSet is abstract.
      Parameters:
      `oracleId` - the number of the Oracle character set. A list of official Oracle character sets is maintained by ...

      Returns:
      CharacterSet for oracleId.

    <!-- -->

    - #### toString

          public String toString()

      The official name of the character set.
      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      the name of the character set

    <!-- -->

    - #### isLossyFrom

          public abstract boolean isLossyFrom(CharacterSet from)

      A conversion looses information if the mapping is not invertible. (A mathematicial would say that the map of characters in from to this is not injective.)
      Parameters:
      `from` - a CharacterSet being tested for compatibility with this CharacterSet.

      Returns:
      true if characters in the from character set can be mapped uniquely to characters in oracleId representation.

    <!-- -->

    - #### isConvertibleFrom

          public abstract boolean isConvertibleFrom(CharacterSet source)

      Are conversions supported.
      Parameters:
      `source` - a CharacterSet to inquire about

      Returns:
      true if conversion from source to oracleId is supported. If it isn't supported attempts to convert will always throw exceptions.

    <!-- -->

    - #### isUnicode

          public boolean isUnicode()

      Is this a Unicode Character Set.
      Returns:
      true if this CharacterSet is an encoding of Unicode

    <!-- -->

    - #### getOracleId

          public int getOracleId()

      The integer that identifies the character set.
      Returns:
      Oracle character set ID

    <!-- -->

    - #### equals

          public boolean equals(Object rhs)

      Two CharacterSet's are equal when their oracleId's are equal
      Overrides:
      [`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `rhs` - the target character set

      Returns:
      `true` if the given CharacterSet object equals to this object

    <!-- -->

    - #### hashCode

          public int hashCode()

      Implements a hash based on oracleId
      Overrides:
      [`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a hash code

    <!-- -->

    - #### toStringWithReplacement

          public abstract String toStringWithReplacement(byte[] bytes,
                                                         int offset,
                                                         int count)

      Convert bytes in oracleId representation to a String. If a character has no Unicode representation the effect is unspecified. The conversion might omit it, or replace it with a special character. The preferred result is replacement by a single character, but it is not guaranteed. If the conversion isn't supported at all, the result may be a fixed string.
      Parameters:
      `bytes` - a array containing characters represented in this character set.

      `offset` - the index of the first byte or the charcters

      `count` - the number of bytes to be converted.

      Returns:
      the String resulting from converting to UCS-2.

    <!-- -->

    - #### toString

          public String toString(byte[] bytes,
                                 int offset,
                                 int count)
                          throws SQLException

      Convert bytes in oracleId representation to a String. The difference between toStringInvertible and plain toString is that toStringInvertible will throw an exception when toString would make some replacement.
      Parameters:
      `bytes` - a array containing characters represented in this character set.

      `offset` - the index of the first byte or the charcters

      `count` - the number of bytes to be converted.

      Returns:
      the String resulting from converting to UCS-2.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - when conversion is not supported.

    <!-- -->

    - #### convert

          public abstract byte[] convert(String s)
                                  throws SQLException

      Convert a String to bytes in oracleId representation.
      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in String.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - when the oracleId does not support conversion from Unicode.

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - when s contains a character that cannot be converted.

    <!-- -->

    - #### convertWithReplacement

          public abstract byte[] convertWithReplacement(String s)

      Convert a String to bytes in oracleId representation. A String is always produced even when the conversion isn't supported or it contains characters that do not have a representation in oracleId. The usual conversion is to replace characters that don't have a representation with some fixed character, but that is not guranteed.
      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in String.

    <!-- -->

    - #### convertWithReplacement

          public byte[] convertWithReplacement(char[] chars,
                                               int charOffset,
                                               byte[] bytes,
                                               int byteOffset,
                                               int[] nchars)

      Similar to convertWithReplacement(String s); Instead of a string, a char\[\] + offset with a length stored in nchars\[0\] will be converted.
      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in the char\[\]. nchars\[0\] has the bytes length.

    <!-- -->

    - #### convert

          public abstract byte[] convert(CharacterSet from,
                                         byte[] source,
                                         int offset,
                                         int count)
                                  throws SQLException

      Converts bytes in some representation to oracleId representation. Note that the input is not guaranteed to be different from the output. If a copy is always wanted then use convertUnshared.
      Parameters:
      `from` - the character set of the input bytes

      `source` - an array of bytes containing the bytes to be converted

      `offset` - the index of the first byte to be converted

      `count` - the number of bytes to be converted

      Returns:
      a byte array in the Oracle character set

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the conversion is not supported

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if some character cannot be converted. This exception is not guaranteed to be thrown. For some conversions a replacement character may be used instead.

    <!-- -->

    - #### convertUnshared

          public byte[] convertUnshared(CharacterSet from,
                                        byte[] source,
                                        int offset,
                                        int count)
                                 throws SQLException

      Converts bytes in some representation to oracleId representation. This is identical to convert except that it always returns a copy of it's input.
      Parameters:
      `from` - the character set of the input bytes

      `source` - an array of bytes containing the bytes to be converted

      `offset` - the index of the first byte to be converted

      `count` - the number of bytes to be converted

      Returns:
      an array containing a representation as an oracleId of characters in the source.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the conversion is not supported.

    <!-- -->

    - #### UTFToString

          public static final String UTFToString(byte[] bytes,
                                                 int offset,
                                                 int nbytes,
                                                 boolean useReplacementChar)
                                          throws SQLException

      Convert a sequence of bytes in UTF8 to a String this function will to allocate the chars array
      Parameters:
      `bytes` - containing the UTF8 string

      `nbytes` - of bytes

      `useReplacementChar` - if true invalid characters are replaced by replacement characters.

      Returns:
      the number of char wrote to the chars array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### UTFToString

          public static final String UTFToString(byte[] bytes,
                                                 int offset,
                                                 int nbytes)
                                          throws SQLException

      Convert a sequence of bytes in UTF8 to a String this function will to allocate the chars array
      Parameters:
      `bytes` - containing the UTF8 string

      `nbytes` - of bytes

      Returns:
      the number of char wrote to the chars array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### UTFToJavaChar

          public static final char[] UTFToJavaChar(byte[] bytes,
                                                   int offset,
                                                   int count)
                                            throws SQLException

      Convert a sequence of bytes in UTF8 to an array of char's. This is different from the offical UTF-8 in that this does not support surrogate characters. To support surrogate, use AL32UTF8 The primary use of this code is to create a string. Note that this method is "true" UTF8. That is in the input, null's may appear encoding themselves.
      Parameters:
      `bytes` - the array holding the UTF8 bytes

      `offset` - the index of the first byte

      `count` - the number of bytes in the UFT8 sequence.

      Returns:
      an array of char's equivalent to the UTF8 sequence.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any error occurs

    <!-- -->

    - #### UTFToJavaChar

          public static final char[] UTFToJavaChar(byte[] bytes,
                                                   int offset,
                                                   int count,
                                                   boolean useReplacementChar)
                                            throws SQLException

      Convert a sequence of bytes in UTF8 to an array of char's. This is different from the offical UTF-8 in that this does not support surrogate characters. To support surrogate, use AL32UTF8 The primary use of this code is to create a string. Note that this method is "true" UTF8. That is in the input, null's may appear encoding themselves.
      Parameters:
      `bytes` - the array holding the UTF8 bytes

      `offset` - the index of the first byte

      `count` - the number of bytes in the UFT8 sequence.

      `useReplacementChar` - if true invalid characters are replaced by replacement characters.

      Returns:
      an array of char's equivalent to the UTF8 sequence.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any error occurs

    <!-- -->

    - #### UTFToJavaCharWithReplacement

          public static final char[] UTFToJavaCharWithReplacement(byte[] bytes,
                                                                  int offset,
                                                                  int count)

      Convert a sequence of bytes in UTF8 to an array of char's. This is different from the offical UTF-8 in that this does not support surrogate characters. To support surrogate, use AL32UTF8 The primary use of this code is to create a string. Note that this method is "true" UTF8. That is in the input, null's may appear encoding themselves.
      Parameters:
      `bytes` - the array holding the UTF8 bytes

      `offset` - the index of the first byte

      `count` - the number of bytes in the UFT8 sequence.

      Returns:
      an array of char's equivalent to the UTF8 sequence.

      Throws:
      [`IllegalStateException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalStateException.html?is-external=true) - if any error occurs

    <!-- -->

    - #### convertUTFBytesToJavaChars

          public static final int convertUTFBytesToJavaChars(byte[] bytes,
                                                             int offset,
                                                             char[] chars,
                                                             int chars_offset,
                                                             int[] countArr,
                                                             boolean convertWithReplacement)
                                                      throws SQLException

      Convert a sequence of bytes in UTF8 to an array of char's. This is different from the offical UTF-8 in that the maximum length of a character is 3 bytes. So a surrogate pair will be represented as 6 bytes (2 times 3 bytes). To support surrogate pairs as 4 bytes, use AL32UTF8. Note that this method is "true" UTF8. That is in the input, null's may appear encoding themselves.
      Parameters:
      `bytes` - the array holding the UTF8 bytes

      `offset` - the index of the first byte

      `chars` - the array of holding the UTF-16 char array

      `chars_offset` - the idnex of the first char that will be written

      `countArr` - IN/OUT parameter. countArr\[0\](IN) contains the number of bytes in the UTF8 sequence that need to be converted.

      `convertWithReplacement` - set to true to use replacement character for illegal sequences

      Returns:
      the number of chars written. countArr\[0\](OUT) contains the number of bytes in the bytes\[\] array that have been ignored because the rest of the sequence is missing (can be up to 3) or because the char\[\] was too short (can be more that 3).

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if invalid, illegal UTF data is given

    <!-- -->

    - #### convertUTFBytesToJavaChars

          public static final int convertUTFBytesToJavaChars(byte[] bytes,
                                                             int offset,
                                                             char[] chars,
                                                             int chars_offset,
                                                             int[] countArr,
                                                             boolean convertWithReplacement,
                                                             int charSize)
                                                      throws SQLException

      Convert a sequence of bytes in UTF8 to an array of char's. This is different from the offical UTF-8 in that the maximum length of a character is 3 bytes. So a surrogate pair will be represented as 6 bytes (2 times 3 bytes). To support surrogate pairs as 4 bytes, use AL32UTF8. Note that this method is "true" UTF8. That is in the input, null's may appear encoding themselves. Same as convertUTFBytesToJavaChars(byte\[\],int,char\[\],int,int\[\],boolean) with an additional argument 'charSize' which is the number of chars available in the char array. Note that if chars_offset+charSize\>char.length, then an IndexArrayOutOfBound exception will be thrown. This method has been optimized for speed: 1) 'switch -case' has been replaced with a series of logical shifts and zero comparisons; 2) the internal loop with attempt to optimize array bounds checks away has been added.
      Parameters:
      `bytes` - the array holding the UTF8 bytes

      `offset` - the index of the first byte

      `chars` - the array of holding the UTF-16 char array

      `chars_offset` - the idnex of the first char that will be written

      `countArr` - IN/OUT parameter. countArr\[0\](IN) contains the number of bytes in the UTF8 sequence that need to be converted.

      `convertWithReplacement` - set to true to use replacement character for illegal sequences

      Returns:
      the number of chars written. countArr\[0\](OUT) contains the number of bytes in the bytes\[\] array that have been ignored because the rest of the sequence is missing (can be up to 3) or because the char\[\] was too short (can be more that 3).

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if invalid, illegal UTF data is given

    <!-- -->

    - #### stringToUTF

          public static final byte[] stringToUTF(String str)

      Convert the str to a byte array that in UTF8 representation.

    <!-- -->

    - #### convertJavaCharsToUTFBytes

          public static final int convertJavaCharsToUTFBytes(char[] chars,
                                                             int chars_offset,
                                                             byte[] bytes,
                                                             int bytes_begin,
                                                             int chars_count)

      Convert char's to the UTF8 representation. `No validation is performed.`
      Parameters:
      `chars` - a source string in an array of chars

      `chars_offset` - an offset to start copying in the source string

      `chars_count` - a length to copy from the source string

      `bytes` - a destination byte array

      `bytes_begin` - an offset to start copying in the destination byte array

      Returns:
      the length copy operation was performed

    <!-- -->

    - #### stringUTFLength

          public static final int stringUTFLength(String s)

      Returns the number of bytes in the UTF8 representation of a String
      Parameters:
      `s` - a Java string

      Returns:
      The number of bytes in the UTF8 encoding

    <!-- -->

    - #### AL32UTF8ToString

          public static final String AL32UTF8ToString(byte[] bytes,
                                                      int offset,
                                                      int nbytes)

      Convert a sequence of bytes in AL32UTF8 format to a String. this function will allocate the memory for holding the returning String.
      Parameters:
      `bytes` - containing the AL32UTF8 string

      `offset` - an offset to start conversion

      `nbytes` - of bytes

      Returns:
      the converted String

    <!-- -->

    - #### AL32UTF8ToString

          public static final String AL32UTF8ToString(byte[] bytes,
                                                      int offset,
                                                      int nbytes,
                                                      boolean useReplacementCharacter)

    <!-- -->

    - #### AL32UTF8ToJavaChar

          public static final char[] AL32UTF8ToJavaChar(byte[] bytes,
                                                        int offset,
                                                        int count,
                                                        boolean useReplacementCharacter)
                                                 throws SQLException

      Converts an AL32UTF8 byte array to an array of char. This function will allocate a char array for holding the returning result.
      Parameters:
      `bytes` - an AL32UTF8 byte array

      `offset` - an offset to start conversion

      `count` - number of bytes to be converted.

      Returns:
      an array of char data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### convertAL32UTF8BytesToJavaChars

          public static final int convertAL32UTF8BytesToJavaChars(byte[] bytes,
                                                                  int offsetBytes,
                                                                  char[] chars,
                                                                  int offsetChars,
                                                                  int[] countArr,
                                                                  boolean convertWithReplacement)
                                                           throws SQLException

      Convert a sequence of bytes in AL32UTF8 to an array of char's. A char in AL32UTF8 can be represented with up to 4 bytes. The only difference between UTF8 (Oracle's) and AL32UTF8 is the representation of a surrogate pair. In AL32UTF8 a surrogate pair is represented with 4 bytes instead of 6 bytes in UTF8.
      Parameters:
      `bytes` - the array holding the AL32UTF8 bytes

      `offsetBytes` - the index of the first byte

      `chars` - the array of holding the UTF-16 char array

      `offsetChars` - the index of the first char that will be written

      `countArr` - IN/OUT parameter. countArr\[0\](IN) contains the number of bytes in the UTF8 sequence that need to be converted.

      `convertWithReplacement` - set to true to use replacement character for illegal sequences

      Returns:
      the number of chars written. countArr\[0\](OUT) contains the number of bytes in the bytes\[\] array that have been ignored because the rest of the sequence is missing (can be up to 4) or because the char\[\] was too short (can be more than 4).

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if invalid, illegal UTF data is given

    <!-- -->

    - #### convertAL32UTF8BytesToJavaChars

          public static final int convertAL32UTF8BytesToJavaChars(byte[] bytes,
                                                                  int offsetBytes,
                                                                  char[] chars,
                                                                  int offsetChars,
                                                                  int[] countArr,
                                                                  boolean convertWithReplacement,
                                                                  int charSize)
                                                           throws SQLException

      Same as convertAL32UTF8BytesToJavaChars(byte\[\],int,char\[\],int,int\[\],boolean) with an additional argument 'charSize' which is the number of chars available in the char array. Note that if chars_offset+charSize\>char.length, then an IndexArrayOutOfBound exception will be thrown. This method has been optimized for speed: 1) 'switch -case' has been replaced with a series of logical shifts and zero comparisons; 2) the internal loop with attempt to optimize array bounds checks away has been added.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringToAL32UTF8

          public static final byte[] stringToAL32UTF8(String str)

    <!-- -->

    - #### convertJavaCharsToAL32UTF8Bytes

          public static final int convertJavaCharsToAL32UTF8Bytes(char[] chars,
                                                                  int chars_offset,
                                                                  byte[] bytes,
                                                                  int bytes_begin,
                                                                  int chars_count)

      Convert char's to the UTF-8 representation. `No validation is performed except surrogate pairs`
      Parameters:
      `chars` - a source string in an array of chars

      `chars_offset` - an offset to start copying in the source string

      `bytes` - a destination byte array

      `bytes_begin` - an offset to start copying in the destination byte array

      `chars_count` - a length to copy from the source string

      Returns:
      the length copy operation was performed

    <!-- -->

    - #### string32UTF8Length

          public static final int string32UTF8Length(String s)

      Returns the number of bytes in the UTF-8 representation of a String
      This method doesn't check neither invalid- nor illegal-UTF sequence.

      Parameters:
      `s` - a UTF-16 string to count the number of bytes in UTF8 format

      Returns:
      The number of bytes in the UTF-8 representaion of a string

    <!-- -->

    - #### AL16UTF16BytesToString

          public static final String AL16UTF16BytesToString(byte[] bytes,
                                                            int nbytes)

      Convert a sequence of bytes in AL16UTF16 to a String this function will allocate a chars array
      Parameters:
      `bytes` - containing the AL16UTF16 string

      `nbytes` - of bytes

      Returns:
      a newly generated String

    <!-- -->

    - #### AL16UTF16BytesToJavaChars

          public static final int AL16UTF16BytesToJavaChars(byte[] bytes,
                                                            int nbytes,
                                                            char[] chars)

      Convert a sequence of bytes in AL16UTF16 to an array of chars caller needs to allocate the chars array
      Parameters:
      `bytes` - containing the AL16UTF16 string

      `nbytes` - of bytes

      `chars` - char array which the UCS2 string will be returned in

      Returns:
      the number of char wrote to the chars array

    <!-- -->

    - #### convertAL16UTF16BytesToJavaChars

          public static final int convertAL16UTF16BytesToJavaChars(byte[] bytes,
                                                                   int offset,
                                                                   char[] chars,
                                                                   int chars_offset,
                                                                   int count,
                                                                   boolean convertWithReplacement)
                                                            throws SQLException

      Converts a sequence of bytes in AL16UTF16 to an array of char's.
      Parameters:
      `bytes` - the array holding the AL16UTF16 bytes

      `offset` - the index of the first byte

      `chars` - the array of holding the UTF-16 char array

      `chars_offset` - the index of the first char

      `count` - the number of bytes in the AL16UTF16 sequence.

      `convertWithReplacement` - set to true to use replacement character for illegal

      Returns:
      the number of chars written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if invalid, illegal UTF data is given

    <!-- -->

    - #### convertAL16UTF16LEBytesToJavaChars

          public static final int convertAL16UTF16LEBytesToJavaChars(byte[] bytes,
                                                                     int offset,
                                                                     char[] chars,
                                                                     int chars_offset,
                                                                     int count,
                                                                     boolean convertWithReplacement)
                                                              throws SQLException

      Converts a sequence of bytes in AL16UTF16LE to an array of char's.
      Parameters:
      `bytes` - the array holding the AL16UTF16LE bytes

      `offset` - the index of the first byte

      `chars` - the array of holding the UTF16UTF16LE char array

      `chars_offset` - the index of the first char

      `count` - the number of bytes in the AL16UTF16LE sequence.

      `convertWithReplacement` - set to true to use replacement character for illegal

      Returns:
      an array of char's equivalent to the AL16UTF16LE sequence.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if invalid, illegal UTF data is given

    <!-- -->

    - #### stringToAL16UTF16Bytes

          public static final byte[] stringToAL16UTF16Bytes(String str)

      Convert a String to an array of bytes this function will allocate the bytes array
      Parameters:
      `str` - containing the UCS2 string

      Returns:
      the AL16UTF16 byte array

    <!-- -->

    - #### javaCharsToAL16UTF16Bytes

          public static final int javaCharsToAL16UTF16Bytes(char[] chars,
                                                            int nchars,
                                                            byte[] bytes)

      Convert a sequence of chars in UCS2 to an array of bytes caller needs to allocate the bytes array
      Parameters:
      `chars` - containing the UCS2 string

      `nchars` - of chars

      `bytes` - byte array which the AL16UTF16 string will be returned in

      Returns:
      the number of bytes wrote to the bytes array

    <!-- -->

    - #### convertJavaCharsToAL16UTF16Bytes

          public static final int convertJavaCharsToAL16UTF16Bytes(char[] chars,
                                                                   int chars_offset,
                                                                   byte[] bytes,
                                                                   int bytes_offset,
                                                                   int nchars)

    <!-- -->

    - #### stringToAL16UTF16LEBytes

          public static final byte[] stringToAL16UTF16LEBytes(String str)

      Convert a String to an array of bytes this function will allocate the bytes array
      Parameters:
      `str` - containing the UCS2 string

      Returns:
      the AL16UTF16LE byte array

    <!-- -->

    - #### javaCharsToAL16UTF16LEBytes

          public static final int javaCharsToAL16UTF16LEBytes(char[] chars,
                                                              int nchars,
                                                              byte[] bytes)

      Convert a sequence of chars in UCS2 to an array of bytes caller needs to allocate the bytes array
      Parameters:
      `chars` - containing the UCS2 string

      `nchars` - of chars

      `bytes` - byte array which the AL16UTF16LE string will be returned in

      Returns:
      the number of bytes wrote to the bytes array

    <!-- -->

    - #### convertJavaCharsToAL16UTF16LEBytes

          public static final int convertJavaCharsToAL16UTF16LEBytes(char[] chars,
                                                                     int chars_offset,
                                                                     byte[] bytes,
                                                                     int bytes_offset,
                                                                     int nchars)

    <!-- -->

    - #### convertASCIIBytesToJavaChars

          public static final int convertASCIIBytesToJavaChars(byte[] bytes,
                                                               int bytes_offset,
                                                               char[] chars,
                                                               int chars_offset,
                                                               int count)
                                                        throws SQLException

      convert a byte array in ascii to a Java char array. The caller needs to allocate the buffer of chars.
      Parameters:
      `bytes` - input bytes

      `bytes_offset` - the starting position to convert

      `chars` - output Java char array (buffer is allocated by the caller)

      `chars_offset` - starting position to store the Java char array

      `count` - number of characters in chars

      Returns:
      the number of Java character written into chars\[\]

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if errors occurred

    <!-- -->

    - #### convertJavaCharsToASCIIBytes

          public static final int convertJavaCharsToASCIIBytes(char[] chars,
                                                               int chars_offset,
                                                               byte[] bytes,
                                                               int bytes_offset,
                                                               int nchars)
                                                        throws SQLException

      convert a Java char array to a byte array in ascii. The caller needs to allocate the buffer of bytes.
      Parameters:
      `chars` - input Java char array

      `chars_offset` - input the starting position to convert

      `bytes` - output the converted byte array in ascii

      `bytes_offset` - input the starting position to hold the returning bytes

      Returns:
      the number of chars converted

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if errors occurred

    <!-- -->

    - #### convertJavaCharsToASCIIBytes

          public static final int convertJavaCharsToASCIIBytes(char[] chars,
                                                               int chars_offset,
                                                               byte[] bytes,
                                                               int bytes_offset,
                                                               int nchars,
                                                               boolean strictConversion)
                                                        throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### convertJavaCharsToISOLATIN1Bytes

          public static final int convertJavaCharsToISOLATIN1Bytes(char[] chars,
                                                                   int chars_offset,
                                                                   byte[] bytes,
                                                                   int bytes_offset,
                                                                   int nchars)
                                                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringToASCII

          public static final byte[] stringToASCII(String str)

      convert a String to a byte array in ascii. This method will allocate the byte array.
      Parameters:
      `str` - input the String to be converted

      Returns:
      the byte array in ascii

    <!-- -->

    - #### convertUTF32toUTF16

          public static final long convertUTF32toUTF16(long ucs4ch)

    <!-- -->

    - #### encodedByteLength

          public int encodedByteLength(String s)
                                throws SQLException

      Return the length of the byte array which would result if the String were encoded in this character set
      Parameters:
      `s` - is a Java String

      Returns:
      the length of the encoded bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### encodedByteLength

          public int encodedByteLength(char[] carray)

      Return the length of the byte array which would result if the char array were encoded in this character set
      Parameters:
      `carray` - is a char array

      Returns:
      the length of the encoded bytes

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### isUnknown

          public boolean isUnknown()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterSet.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterBuffer.md)
- [Next Class](CharacterSetWithConverter.md)

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
