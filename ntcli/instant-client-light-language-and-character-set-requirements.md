## Instant Client Light Language and Character Set Requirements

Describes the requirements to use Instant Client Light.

In addition to the requirements, if you plan to use Instant Client Light, then the applications must use the following languages and character sets:

- Language: Any language that Oracle supports, but only US English error messages returns errors on the client side.

- Territory: Any territory that Oracle supports.

- Character sets:

  - Single byte

    - US7ASCII

    - WE8DEC

    - WE8ISO8859P1

    - WE8MSWIN1252

  <!-- -->

  - Unicode

    - UTF8

    - AL16UTF16

    - AL32UTF8

    Instant Client Light can connect to databases having one of the following database character sets. If a character set other than those in the list is used as the client or database character set, then an error is returned.

    - US7ASCII

    - WE8DEC

    - WE8MSWIN1252

    - WE8ISO8859P1

    - WE8EBCDIC37C

    - WE8EBCDIC1047

    - UTF8

    - AL32UTF8

    Instant Client Light can also operate with the OCI Environment handles created in the OCI_UTF16 mode.

    The language, territory, and character sets are determined by the `NLS_LANG` parameter, which is stored in the registry under the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\``KEY_HomeName``\NLS_LANG` subkey, where `HomeName` is the unique name identifying the Oracle home. The Registry setting is overridden by the `NLS_LANG` environment variable.

    **Note:**

    AL32UTF8 is the Oracle Database character set that is appropriate for XMLType data. It is equivalent to the IANA registered standard UTF-8 encoding, which supports all valid XML characters.

    Do not confuse Oracle Database database character set UTF8 (no hyphen) with database character set AL32UTF8 or with character encoding UTF-8. Database character set UTF8 has been superseded by AL32UTF8. Do not use UTF8 for XML data. UTF8 supports only Unicode version 3.1 and earlier; it does not support all valid XML characters. AL32UTF8 has no such limitation.

    Using database character set UTF8 for XML data potentially causes an irrecoverable error or affects security negatively. If a character that is not supported by the database character set appears in an input-document element name, then a replacement character (usually "?") is substituted for it. This terminates parsing and raises an exception.

**Parent topic:** [Oracle Database Client Software Requirements](oracle-database-client-software-requirements.md)
