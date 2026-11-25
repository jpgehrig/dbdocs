In addition to the requirements described in the preceding section, if you plan to use Instant Client Light, then the applications must use the following languages and character sets:

- Language: Any language that is supported by Oracle

- Territory: Any territory that is supported by Oracle

- Character sets:

  - Single byte

    - US7ASCII

    - WE8DEC

    - WE8MSWIN1252

    - WE8ISO8859P1

  - Unicode

    - UTF8

    - AL16UTF16

    - AL32UTF8

    Instant Client Light can connect to databases having one of the following database character sets:

    - US7ASCII

    - WE8DEC

    - WE8MSWIN1252

    - WE8ISO8859P1

    - WE8EBCDIC37C

    - WE8EBCDIC1047

    - UTF8

    - AL32UTF8

Instant Client Light can also operate with the OCI Environment handles created in the OCI_UTF16 mode.

The language, territory, and character sets are determined by the `NLS_LANG` environment variable.

**Note:**

Ensure that you set the `NLS_LANG` environment variable to the required character set before you run Oracle Database Instant Client.

**Parent topic:** [Checking the Software Requirements](checking-the-software-requirements.md)
