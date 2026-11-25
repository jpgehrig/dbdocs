## Configuring Locale and Character Sets Using the NLS_LANG Environment Variable

The `NLS_LANG` environment variable determines the language of the user interface and the globalization behavior for components such as SQL\*Plus, exp, and imp.

It sets the language and territory used by the client application and the database user session. It also declares the character set for entering and displaying data by the client application.

The `NLS_LANG` environment variable uses the following format:

    NLS_LANG=language_territory.characterset

In this format:

- `language` specifies the language used for displaying Oracle messages, sorting, day names, and month names

- `territory` specifies the conventions for default date, monetary and numeric formats

- `characterset` specifies the encoding used by the client application

  In most cases, this is the Oracle character set that corresponds to the Windows ANSI Code Page as determined by the System Locale.

The `NLS_LANG` parameter on Windows can be set

- in Registry under the subkey corresponding to a given Oracle home,

- as an environment variable.

When you install Oracle Database components and the `NLS_LANG` parameter is not yet set in the Registry subkey of the target Oracle home, Oracle Universal Installer sets the `NLS_LANG` parameter to a default value derived from the operating system locale for the current user.

**See Also:**

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for information about the `NLS_LANG` parameter and Globalization Support initialization parameters

For example:

- Arabic (U.A.E.) - `ARABIC_UNITED ARAB EMIRATES.AR8MSWIN1256`

- Chinese (PRC) - `SIMPLIFIED CHINESE_CHINA.ZHS16GBK`

- Chinese (Taiwan) - `TRADITIONAL CHINESE_TAIWAN.ZHT16MSWIN950`

- English (United Kingdom) - `ENGLISH_UNITED KINGDOM.WE8MSWIN1252`

- English (United States) - `AMERICAN_AMERICA.WE8MSWIN1252`

- French (Canada) - `CANADIAN FRENCH_CANADA.WE8MSWIN1252`

- French (France) - `FRENCH_FRANCE.WE8MSWIN1252`

- German (Germany) - `GERMAN_GERMANY.WE8MSWIN1252`

- Hebrew - `HEBREW_ISRAEL.IW8MSWIN1255`

- Japanese - `JAPANESE_JAPAN.JA16SJISTILDE`

- Russian - `RUSSIAN_RUSSIA.CL8MSWIN1251`

- Spanish (Spain) - `SPANISH_SPAIN.WE8MSWIN1252`

- Spanish (Mexico) - `MEXICAN SPANISH_MEXICO.WE8MSWIN1252`

- Spanish (Venezuela) - `LATIN AMERICAN SPANISH_VENEZUELA.WE8MSWIN1252`

**Parent topic:** [Installing and Using Oracle Components in Different Languages](installing-and-using-oracle-components-in-different-languages.md)
