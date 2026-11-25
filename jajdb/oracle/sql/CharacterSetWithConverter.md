Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterSetWithConverter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterSet.md)
- [Next Class](CharacterWalker.md)

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

## Class CharacterSetWithConverter

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.CharacterSet](CharacterSet.md)

  - - oracle.sql.CharacterSetWithConverter

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class CharacterSetWithConverter
      extends CharacterSet

  This is an abstract base class that all character sets that use CharacterConverter are based on.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                       | Field and Description |
    |---------------------------------------------------------|-----------------------|
    | `static oracle.sql.converter.CharacterConverterFactory` | `ccFactory`           |

    - ### Fields inherited from class oracle.sql.[CharacterSet](CharacterSet.md)

      [`AL16UTF16_CHARSET`](CharacterSet.md)`, `[`AL16UTF16LE_CHARSET`](CharacterSet.md)`, `[`AL24UTFFSS_CHARSET`](CharacterSet.md)`, `[`AL32UTF8_CHARSET`](CharacterSet.md)`, `[`AR8ADOS710_CHARSET`](CharacterSet.md)`, `[`AR8ADOS710T_CHARSET`](CharacterSet.md)`, `[`AR8ADOS720_CHARSET`](CharacterSet.md)`, `[`AR8ADOS720T_CHARSET`](CharacterSet.md)`, `[`AR8APTEC715_CHARSET`](CharacterSet.md)`, `[`AR8APTEC715T_CHARSET`](CharacterSet.md)`, `[`AR8ARABICMAC_CHARSET`](CharacterSet.md)`, `[`AR8ARABICMACS_CHARSET`](CharacterSet.md)`, `[`AR8ARABICMACT_CHARSET`](CharacterSet.md)`, `[`AR8ASMO708PLUS_CHARSET`](CharacterSet.md)`, `[`AR8ASMO8X_CHARSET`](CharacterSet.md)`, `[`AR8EBCDIC420S_CHARSET`](CharacterSet.md)`, `[`AR8EBCDICX_CHARSET`](CharacterSet.md)`, `[`AR8HPARABIC8T_CHARSET`](CharacterSet.md)`, `[`AR8ISO8859P6_CHARSET`](CharacterSet.md)`, `[`AR8MSAWIN_CHARSET`](CharacterSet.md)`, `[`AR8MSWIN1256_CHARSET`](CharacterSet.md)`, `[`AR8MUSSAD768_CHARSET`](CharacterSet.md)`, `[`AR8MUSSAD768T_CHARSET`](CharacterSet.md)`, `[`AR8NAFITHA711_CHARSET`](CharacterSet.md)`, `[`AR8NAFITHA711T_CHARSET`](CharacterSet.md)`, `[`AR8NAFITHA721_CHARSET`](CharacterSet.md)`, `[`AR8NAFITHA721T_CHARSET`](CharacterSet.md)`, `[`AR8SAKHR706_CHARSET`](CharacterSet.md)`, `[`AR8SAKHR707_CHARSET`](CharacterSet.md)`, `[`AR8SAKHR707T_CHARSET`](CharacterSet.md)`, `[`AR8XBASIC_CHARSET`](CharacterSet.md)`, `[`ASCII_CHARSET`](CharacterSet.md)`, `[`AZ8ISO8859P9E_CHARSET`](CharacterSet.md)`, `[`BG8MSWIN_CHARSET`](CharacterSet.md)`, `[`BG8PC437S_CHARSET`](CharacterSet.md)`, `[`BLT8CP921_CHARSET`](CharacterSet.md)`, `[`BLT8EBCDIC1112_CHARSET`](CharacterSet.md)`, `[`BLT8EBCDIC1112S_CHARSET`](CharacterSet.md)`, `[`BLT8ISO8859P13_CHARSET`](CharacterSet.md)`, `[`BLT8MSWIN1257_CHARSET`](CharacterSet.md)`, `[`BLT8PC775_CHARSET`](CharacterSet.md)`, `[`BN8BSCII_CHARSET`](CharacterSet.md)`, `[`CDN8PC863_CHARSET`](CharacterSet.md)`, `[`CE8BS2000_CHARSET`](CharacterSet.md)`, `[`CEL8ISO8859P14_CHARSET`](CharacterSet.md)`, `[`CH7DEC_CHARSET`](CharacterSet.md)`, `[`CL8BS2000_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1025_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1025C_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1025R_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1025S_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1025X_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1158_CHARSET`](CharacterSet.md)`, `[`CL8EBCDIC1158R_CHARSET`](CharacterSet.md)`, `[`CL8ISO8859P5_CHARSET`](CharacterSet.md)`, `[`CL8ISOIR111_CHARSET`](CharacterSet.md)`, `[`CL8KOI8R_CHARSET`](CharacterSet.md)`, `[`CL8KOI8U_CHARSET`](CharacterSet.md)`, `[`CL8MACCYRILLIC_CHARSET`](CharacterSet.md)`, `[`CL8MACCYRILLICS_CHARSET`](CharacterSet.md)`, `[`CL8MSWIN1251_CHARSET`](CharacterSet.md)`, `[`D7DEC_CHARSET`](CharacterSet.md)`, `[`D7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`D8BS2000_CHARSET`](CharacterSet.md)`, `[`D8EBCDIC1141_CHARSET`](CharacterSet.md)`, `[`D8EBCDIC273_CHARSET`](CharacterSet.md)`, `[`DEFAULT_CHARSET`](CharacterSet.md)`, `[`DK7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`DK8BS2000_CHARSET`](CharacterSet.md)`, `[`DK8EBCDIC1142_CHARSET`](CharacterSet.md)`, `[`DK8EBCDIC277_CHARSET`](CharacterSet.md)`, `[`E7DEC_CHARSET`](CharacterSet.md)`, `[`E7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`E8BS2000_CHARSET`](CharacterSet.md)`, `[`EE8BS2000_CHARSET`](CharacterSet.md)`, `[`EE8EBCDIC870_CHARSET`](CharacterSet.md)`, `[`EE8EBCDIC870C_CHARSET`](CharacterSet.md)`, `[`EE8EBCDIC870S_CHARSET`](CharacterSet.md)`, `[`EE8ISO8859P2_CHARSET`](CharacterSet.md)`, `[`EE8MACCE_CHARSET`](CharacterSet.md)`, `[`EE8MACCES_CHARSET`](CharacterSet.md)`, `[`EE8MACCROATIAN_CHARSET`](CharacterSet.md)`, `[`EE8MACCROATIANS_CHARSET`](CharacterSet.md)`, `[`EE8MSWIN1250_CHARSET`](CharacterSet.md)`, `[`EE8PC852_CHARSET`](CharacterSet.md)`, `[`EEC8EUROASCI_CHARSET`](CharacterSet.md)`, `[`EEC8EUROPA3_CHARSET`](CharacterSet.md)`, `[`EL8DEC_CHARSET`](CharacterSet.md)`, `[`EL8EBCDIC423R_CHARSET`](CharacterSet.md)`, `[`EL8EBCDIC875_CHARSET`](CharacterSet.md)`, `[`EL8EBCDIC875R_CHARSET`](CharacterSet.md)`, `[`EL8EBCDIC875S_CHARSET`](CharacterSet.md)`, `[`EL8GCOS7_CHARSET`](CharacterSet.md)`, `[`EL8ISO8859P7_CHARSET`](CharacterSet.md)`, `[`EL8MACGREEK_CHARSET`](CharacterSet.md)`, `[`EL8MACGREEKS_CHARSET`](CharacterSet.md)`, `[`EL8MSWIN1253_CHARSET`](CharacterSet.md)`, `[`EL8PC437S_CHARSET`](CharacterSet.md)`, `[`EL8PC737_CHARSET`](CharacterSet.md)`, `[`EL8PC851_CHARSET`](CharacterSet.md)`, `[`EL8PC869_CHARSET`](CharacterSet.md)`, `[`ET8MSWIN923_CHARSET`](CharacterSet.md)`, `[`F7DEC_CHARSET`](CharacterSet.md)`, `[`F7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`F8BS2000_CHARSET`](CharacterSet.md)`, `[`F8EBCDIC1147_CHARSET`](CharacterSet.md)`, `[`F8EBCDIC297_CHARSET`](CharacterSet.md)`, `[`HU8ABMOD_CHARSET`](CharacterSet.md)`, `[`HU8CWI2_CHARSET`](CharacterSet.md)`, `[`I7DEC_CHARSET`](CharacterSet.md)`, `[`I7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`I8EBCDIC1144_CHARSET`](CharacterSet.md)`, `[`I8EBCDIC280_CHARSET`](CharacterSet.md)`, `[`IN8ISCII_CHARSET`](CharacterSet.md)`, `[`IS8MACICELANDIC_CHARSET`](CharacterSet.md)`, `[`IS8MACICELANDICS_CHARSET`](CharacterSet.md)`, `[`IS8PC861_CHARSET`](CharacterSet.md)`, `[`ISO_LATIN_1_CHARSET`](CharacterSet.md)`, `[`IW7IS960_CHARSET`](CharacterSet.md)`, `[`IW8EBCDIC1086_CHARSET`](CharacterSet.md)`, `[`IW8EBCDIC424_CHARSET`](CharacterSet.md)`, `[`IW8EBCDIC424S_CHARSET`](CharacterSet.md)`, `[`IW8ISO8859P8_CHARSET`](CharacterSet.md)`, `[`IW8MACHEBREW_CHARSET`](CharacterSet.md)`, `[`IW8MACHEBREWS_CHARSET`](CharacterSet.md)`, `[`IW8MSWIN1255_CHARSET`](CharacterSet.md)`, `[`IW8PC1507_CHARSET`](CharacterSet.md)`, `[`JA16DBCS_CHARSET`](CharacterSet.md)`, `[`JA16EBCDIC930_CHARSET`](CharacterSet.md)`, `[`JA16EUC_CHARSET`](CharacterSet.md)`, `[`JA16EUCTILDE_CHARSET`](CharacterSet.md)`, `[`JA16EUCYEN_CHARSET`](CharacterSet.md)`, `[`JA16MACSJIS_CHARSET`](CharacterSet.md)`, `[`JA16SJIS_CHARSET`](CharacterSet.md)`, `[`JA16SJISTILDE_CHARSET`](CharacterSet.md)`, `[`JA16SJISYEN_CHARSET`](CharacterSet.md)`, `[`JA16TSTSET_CHARSET`](CharacterSet.md)`, `[`JA16TSTSET2_CHARSET`](CharacterSet.md)`, `[`JA16VMS_CHARSET`](CharacterSet.md)`, `[`KO16DBCS_CHARSET`](CharacterSet.md)`, `[`KO16KSC5601_CHARSET`](CharacterSet.md)`, `[`KO16KSCCS_CHARSET`](CharacterSet.md)`, `[`KO16MSWIN949_CHARSET`](CharacterSet.md)`, `[`KO16TSTSET_CHARSET`](CharacterSet.md)`, `[`LA8ISO6937_CHARSET`](CharacterSet.md)`, `[`LA8PASSPORT_CHARSET`](CharacterSet.md)`, `[`LT8MSWIN921_CHARSET`](CharacterSet.md)`, `[`LT8PC772_CHARSET`](CharacterSet.md)`, `[`LT8PC774_CHARSET`](CharacterSet.md)`, `[`LV8PC1117_CHARSET`](CharacterSet.md)`, `[`LV8PC8LR_CHARSET`](CharacterSet.md)`, `[`LV8RST104090_CHARSET`](CharacterSet.md)`, `[`N7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`N8PC865_CHARSET`](CharacterSet.md)`, `[`NDK7DEC_CHARSET`](CharacterSet.md)`, `[`NE8ISO8859P10_CHARSET`](CharacterSet.md)`, `[`NEE8ISO8859P4_CHARSET`](CharacterSet.md)`, `[`NL7DEC_CHARSET`](CharacterSet.md)`, `[`RU8BESTA_CHARSET`](CharacterSet.md)`, `[`RU8PC855_CHARSET`](CharacterSet.md)`, `[`RU8PC866_CHARSET`](CharacterSet.md)`, `[`S7DEC_CHARSET`](CharacterSet.md)`, `[`S7SIEMENS9780X_CHARSET`](CharacterSet.md)`, `[`S8BS2000_CHARSET`](CharacterSet.md)`, `[`S8EBCDIC1143_CHARSET`](CharacterSet.md)`, `[`S8EBCDIC278_CHARSET`](CharacterSet.md)`, `[`SE8ISO8859P3_CHARSET`](CharacterSet.md)`, `[`SF7ASCII_CHARSET`](CharacterSet.md)`, `[`SF7DEC_CHARSET`](CharacterSet.md)`, `[`TH8MACTHAI_CHARSET`](CharacterSet.md)`, `[`TH8MACTHAIS_CHARSET`](CharacterSet.md)`, `[`TH8TISASCII_CHARSET`](CharacterSet.md)`, `[`TH8TISEBCDIC_CHARSET`](CharacterSet.md)`, `[`TH8TISEBCDICS_CHARSET`](CharacterSet.md)`, `[`TR7DEC_CHARSET`](CharacterSet.md)`, `[`TR8DEC_CHARSET`](CharacterSet.md)`, `[`TR8EBCDIC1026_CHARSET`](CharacterSet.md)`, `[`TR8EBCDIC1026S_CHARSET`](CharacterSet.md)`, `[`TR8MACTURKISH_CHARSET`](CharacterSet.md)`, `[`TR8MACTURKISHS_CHARSET`](CharacterSet.md)`, `[`TR8MSWIN1254_CHARSET`](CharacterSet.md)`, `[`TR8PC857_CHARSET`](CharacterSet.md)`, `[`UNICODE_1_CHARSET`](CharacterSet.md)`, `[`UNICODE_2_CHARSET`](CharacterSet.md)`, `[`US16TSTFIXED_CHARSET`](CharacterSet.md)`, `[`US7ASCII_CHARSET`](CharacterSet.md)`, `[`US8BS2000_CHARSET`](CharacterSet.md)`, `[`US8ICL_CHARSET`](CharacterSet.md)`, `[`US8NOOP_CHARSET`](CharacterSet.md)`, `[`US8PC437_CHARSET`](CharacterSet.md)`, `[`UTF8_CHARSET`](CharacterSet.md)`, `[`UTFE_CHARSET`](CharacterSet.md)`, `[`VN8MSWIN1258_CHARSET`](CharacterSet.md)`, `[`VN8VN3_CHARSET`](CharacterSet.md)`, `[`WE8BS2000_CHARSET`](CharacterSet.md)`, `[`WE8BS2000E_CHARSET`](CharacterSet.md)`, `[`WE8BS2000L5_CHARSET`](CharacterSet.md)`, `[`WE8DEC_CHARSET`](CharacterSet.md)`, `[`WE8DECTST_CHARSET`](CharacterSet.md)`, `[`WE8DG_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1047_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1047E_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1140_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1140C_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1145_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1146_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1148_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC1148C_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC284_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC285_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC37_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC37C_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC500_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC500C_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC871_CHARSET`](CharacterSet.md)`, `[`WE8EBCDIC924_CHARSET`](CharacterSet.md)`, `[`WE8GCOS7_CHARSET`](CharacterSet.md)`, `[`WE8HP_CHARSET`](CharacterSet.md)`, `[`WE8ICL_CHARSET`](CharacterSet.md)`, `[`WE8ISO8859P1_CHARSET`](CharacterSet.md)`, `[`WE8ISO8859P15_CHARSET`](CharacterSet.md)`, `[`WE8ISO8859P9_CHARSET`](CharacterSet.md)`, `[`WE8ISOICLUK_CHARSET`](CharacterSet.md)`, `[`WE8MACROMAN8_CHARSET`](CharacterSet.md)`, `[`WE8MACROMAN8S_CHARSET`](CharacterSet.md)`, `[`WE8MSWIN1252_CHARSET`](CharacterSet.md)`, `[`WE8NCR4970_CHARSET`](CharacterSet.md)`, `[`WE8NEXTSTEP_CHARSET`](CharacterSet.md)`, `[`WE8PC850_CHARSET`](CharacterSet.md)`, `[`WE8PC858_CHARSET`](CharacterSet.md)`, `[`WE8PC860_CHARSET`](CharacterSet.md)`, `[`WE8ROMAN8_CHARSET`](CharacterSet.md)`, `[`YUG7ASCII_CHARSET`](CharacterSet.md)`, `[`ZHS16CGB231280_CHARSET`](CharacterSet.md)`, `[`ZHS16DBCS_CHARSET`](CharacterSet.md)`, `[`ZHS16GBK_CHARSET`](CharacterSet.md)`, `[`ZHS16MACCGB231280_CHARSET`](CharacterSet.md)`, `[`ZHS32GB18030_CHARSET`](CharacterSet.md)`, `[`ZHT16BIG5_CHARSET`](CharacterSet.md)`, `[`ZHT16CCDC_CHARSET`](CharacterSet.md)`, `[`ZHT16DBCS_CHARSET`](CharacterSet.md)`, `[`ZHT16DBT_CHARSET`](CharacterSet.md)`, `[`ZHT16HKSCS_CHARSET`](CharacterSet.md)`, `[`ZHT16HKSCS31_CHARSET`](CharacterSet.md)`, `[`ZHT16MSWIN950_CHARSET`](CharacterSet.md)`, `[`ZHT32EUC_CHARSET`](CharacterSet.md)`, `[`ZHT32SOPS_CHARSET`](CharacterSet.md)`, `[`ZHT32TRIS_CHARSET`](CharacterSet.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                               |
    |-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `byte[]`                                                                                        | `convert``(`[`CharacterSet`](CharacterSet.md)` from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation.                                                                                     |
    | `byte[]`                                                                                        | `convert``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Convert a String to bytes in oracleId representation.                                                                            |
    | `byte[]`                                                                                        | `convertWithReplacement``(char[] chars, int charOffset, byte[] bytes, int byteOffset, int[] nchars)`<br>Similar to convertWithReplacement(String s); Instead of a string, a char\[\] + offset with a length stored in nchars\[0\] will be converted. |
    | `byte[]`                                                                                        | `convertWithReplacement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Convert a String to bytes in oracleId representation.                                                             |
    | `boolean`                                                                                       | `isConvertibleFrom``(`[`CharacterSet`](CharacterSet.md)` source)`<br>Are conversions supported.                                                                                                                                                      |
    | `boolean`                                                                                       | `isLossyFrom``(`[`CharacterSet`](CharacterSet.md)` from)`<br>A conversion looses information if the mapping is not invertible.                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``(byte[] bytes, int offset, int count)`<br>Convert bytes in oracleId representation to a String.                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toStringWithReplacement``(byte[] bytes, int offset, int count)`<br>Convert bytes in oracleId representation to a String.                                                                                                                            |

    - ### Methods inherited from class oracle.sql.[CharacterSet](CharacterSet.md)

      [`AL16UTF16BytesToJavaChars`](CharacterSet.md)`, `[`AL16UTF16BytesToString`](CharacterSet.md)`, `[`AL32UTF8ToJavaChar`](CharacterSet.md)`, `[`AL32UTF8ToString`](CharacterSet.md)`, `[`AL32UTF8ToString`](CharacterSet.md)`, `[`convertAL16UTF16BytesToJavaChars`](CharacterSet.md)`, `[`convertAL16UTF16LEBytesToJavaChars`](CharacterSet.md)`, `[`convertAL32UTF8BytesToJavaChars`](CharacterSet.md)`, `[`convertAL32UTF8BytesToJavaChars`](CharacterSet.md)`, `[`convertASCIIBytesToJavaChars`](CharacterSet.md)`, `[`convertJavaCharsToAL16UTF16Bytes`](CharacterSet.md)`, `[`convertJavaCharsToAL16UTF16LEBytes`](CharacterSet.md)`, `[`convertJavaCharsToAL32UTF8Bytes`](CharacterSet.md)`, `[`convertJavaCharsToASCIIBytes`](CharacterSet.md)`, `[`convertJavaCharsToASCIIBytes`](CharacterSet.md)`, `[`convertJavaCharsToISOLATIN1Bytes`](CharacterSet.md)`, `[`convertJavaCharsToUTFBytes`](CharacterSet.md)`, `[`convertUnshared`](CharacterSet.md)`, `[`convertUTF32toUTF16`](CharacterSet.md)`, `[`convertUTFBytesToJavaChars`](CharacterSet.md)`, `[`convertUTFBytesToJavaChars`](CharacterSet.md)`, `[`encodedByteLength`](CharacterSet.md)`, `[`encodedByteLength`](CharacterSet.md)`, `[`equals`](CharacterSet.md)`, `[`getConnectionDuringExceptionHandling`](CharacterSet.md)`, `[`getOracleId`](CharacterSet.md)`, `[`hashCode`](CharacterSet.md)`, `[`isUnicode`](CharacterSet.md)`, `[`isUnknown`](CharacterSet.md)`, `[`javaCharsToAL16UTF16Bytes`](CharacterSet.md)`, `[`javaCharsToAL16UTF16LEBytes`](CharacterSet.md)`, `[`make`](CharacterSet.md)`, `[`string32UTF8Length`](CharacterSet.md)`, `[`stringToAL16UTF16Bytes`](CharacterSet.md)`, `[`stringToAL16UTF16LEBytes`](CharacterSet.md)`, `[`stringToAL32UTF8`](CharacterSet.md)`, `[`stringToASCII`](CharacterSet.md)`, `[`stringToUTF`](CharacterSet.md)`, `[`stringUTFLength`](CharacterSet.md)`, `[`toString`](CharacterSet.md)`, `[`UTFToJavaChar`](CharacterSet.md)`, `[`UTFToJavaChar`](CharacterSet.md)`, `[`UTFToJavaCharWithReplacement`](CharacterSet.md)`, `[`UTFToString`](CharacterSet.md)`, `[`UTFToString`](CharacterSet.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### ccFactory

          public static oracle.sql.converter.CharacterConverterFactory ccFactory

  <!-- -->

  - ### Method Detail

    - #### isLossyFrom

          public boolean isLossyFrom(CharacterSet from)

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      A conversion looses information if the mapping is not invertible. (A mathematicial would say that the map of characters in from to this is not injective.)
      Specified by:
      [`isLossyFrom`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Parameters:
      `from` - a CharacterSet being tested for compatibility with this CharacterSet.

      Returns:
      true if characters in the from character set can be mapped uniquely to characters in oracleId representation.

    <!-- -->

    - #### isConvertibleFrom

          public boolean isConvertibleFrom(CharacterSet source)

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Are conversions supported.
      Specified by:
      [`isConvertibleFrom`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Parameters:
      `source` - a CharacterSet to inquire about

      Returns:
      true if conversion from source to oracleId is supported. If it isn't supported attempts to convert will always throw exceptions.

    <!-- -->

    - #### toStringWithReplacement

          public String toStringWithReplacement(byte[] bytes,
                                                int offset,
                                                int count)

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Convert bytes in oracleId representation to a String. If a character has no Unicode representation the effect is unspecified. The conversion might omit it, or replace it with a special character. The preferred result is replacement by a single character, but it is not guaranteed. If the conversion isn't supported at all, the result may be a fixed string.
      Specified by:
      [`toStringWithReplacement`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

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

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Convert bytes in oracleId representation to a String. The difference between toStringInvertible and plain toString is that toStringInvertible will throw an exception when toString would make some replacement.
      Overrides:
      [`toString`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

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

          public byte[] convert(String s)
                         throws SQLException

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Convert a String to bytes in oracleId representation.
      Specified by:
      [`convert`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in String.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - when the oracleId does not support conversion from Unicode.

    <!-- -->

    - #### convertWithReplacement

          public byte[] convertWithReplacement(String s)

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Convert a String to bytes in oracleId representation. A String is always produced even when the conversion isn't supported or it contains characters that do not have a representation in oracleId. The usual conversion is to replace characters that don't have a representation with some fixed character, but that is not guranteed.
      Specified by:
      [`convertWithReplacement`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in String.

    <!-- -->

    - #### convertWithReplacement

          public byte[] convertWithReplacement(char[] chars,
                                               int charOffset,
                                               byte[] bytes,
                                               int byteOffset,
                                               int[] nchars)

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Similar to convertWithReplacement(String s); Instead of a string, a char\[\] + offset with a length stored in nchars\[0\] will be converted.
      Overrides:
      [`convertWithReplacement`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Returns:
      an array containing the sequence of bytes in oracleId representation that represent the sequence of Unicode characters in the char\[\]. nchars\[0\] has the bytes length.

    <!-- -->

    - #### convert

          public byte[] convert(CharacterSet from,
                                byte[] source,
                                int offset,
                                int count)
                         throws SQLException

      Description copied from class: [`CharacterSet`](CharacterSet.md)
      Converts bytes in some representation to oracleId representation. Note that the input is not guaranteed to be different from the output. If a copy is always wanted then use convertUnshared.
      Specified by:
      [`convert`](CharacterSet.md) in class [`CharacterSet`](CharacterSet.md)

      Parameters:
      `from` - the character set of the input bytes

      `source` - an array of bytes containing the bytes to be converted

      `offset` - the index of the first byte to be converted

      `count` - the number of bytes to be converted

      Returns:
      a byte array in the Oracle character set

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the conversion is not supported

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterSetWithConverter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterSet.md)
- [Next Class](CharacterWalker.md)

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
