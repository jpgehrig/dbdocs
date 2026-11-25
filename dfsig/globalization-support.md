This chapter describes the globalization support available with Oracle Database 19c for Fujitsu BS2000, with information about the following:

- Language, Territory, and Character Set

- Supported Language Conventions

- Supported Territories

- Supported Character Sets

- Location of Message Files

- Linguistic Definitions

Character set tables and country and regional information, such as, date format, names of months, and so on, are dynamically loaded at run time. This reduces the actual storage requirements and allows new languages to be added in the future without the need to relink all applications.

The files containing character set information are created in the current BS2000 user ID. The names of these files have the following format:

    O193NLS.LXnnnnn.NLB

These files are for internal use only. You should not make changes to them. If you need a character set, language, or a territory code that is not present, then contact Oracle Support Services to check for any updates.

**Note:**

User-defined character sets as documented in [Oracle Database Globalization Support Guide](../nlspg/customizing-locale-data.md) are not supported in this release.

### 16.1 Language, Territory, and Character Set

To choose a language, a territory, and a character set that you want to work with, you must perform separate procedures for Oracle Database and the supported Oracle Database utilities. This section includes the following topics:

- Oracle Database

- Other Oracle Database Products

#### 16.1.1 Oracle Database

For Oracle Database, the database administrator sets the `NLS_LANGUAGE` and `NLS_TERRITORY` parameters in the initialization files.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information

#### 16.1.2 Other Oracle Database Products

For the supported Oracle Database products, you can choose a language, a territory, and a character set by setting the value of the `NLS_LANG` environment variable. Set this environment variable in the `ORAENV` file or in the POSIX shell as follows:

    NLS_LANG=language_territory.characterset

where:

`language` is any supported language.

`territory` is any supported territory.

`characterset` is the character set required by your terminal.

For example:

    NLS_LANG=German_Germany.D8BS2000

### 16.2 Supported Language Conventions

Oracle Database 19c for Fujitsu BS2000 provides support for language conventions, such as names of days and months, for the following languages:

- American English: `american` (default)

- Czech: `czech`

- Danish: `danish`

- Dutch: `dutch`

- Finnish: `finnish`

- French: `french`

- German: `german`

- Hungarian: `hungarian`

- Italian: `italian`

- Norwegian: `norwegian`

- Polish: `polish`

- Portuguese: `portuguese`

- Slovak: `slovak`

- Spanish: `spanish`

- Swedish: `swedish`

- Russian: `russian`

- Turkish: `turkish`

### 16.3 Supported Territories

Oracle Database Globalization Support provides support for territory conventions, such as start day of the week, for the following territories:

- America: `america` (default)

- Czech Republic: `czech republic`

- Denmark: `denmark`

- Finland: `finland`

- France: `france`

- Germany: `germany`

- Hungary: `hungary`

- Italy: `italy`

- The Netherlands: `the netherlands`

- Norway: `norway`

- Poland: `poland`

- Portugal: `portugal`

- Spain: `spain`

- Sweden: `sweden`

- CIS: `CIS`

- Slovakia: `slovakia`

- Turkey: `turkey`

- United Kingdom: `united kingdom`

### 16.4 Supported Character Sets

Oracle Database 19c supports the following character sets for servers and clients under BS2000:

| Name        | Description                  | Usage                                          |
|:------------|:-----------------------------|:-----------------------------------------------|
| US8BS2000   | Siemens 9750-62 EBCDIC 8-bit | American                                       |
| D8BS2000    | Siemens 9750-62 EBCDIC 8-bit | German                                         |
| F8BS2000    | Siemens 9750-62 EBCDIC 8-bit | French                                         |
| E8BS2000    | Siemens 9750-62 EBCDIC 8-bit | Spanish                                        |
| DK8BS2000   | Siemens 9750-62 EBCDIC 8-bit | Danish                                         |
| S8BS2000    | Siemens 9750-62 EBCDIC 8-bit | Swedish                                        |
| WE8BS2000   | Siemens EBCDIC.DF.04-1 8-bit | West European (= ISO 8859/1)                   |
| CL8BS2000   | Siemens EBCDIC.EHC.LC 8-bit  | Latin/Cyrillic-1 (= ISO 8859/5)                |
| WE8BS2000L5 | Siemens EBCDIC.DF.04-9 8-bit | WE & Turkish (= ISO 8859/9)                    |
| EE8BS2000   | Siemens EBCDIC.EHC.L2 8-bit  | East European (= ISO 8859/2)                   |
| CE8BS2000   | Siemens EBCDIC.DF.04-2 8-bit | Central European (= ISO 8859/2)                |
| WE8BS2000E  | Siemens EBCDIC.DF.04-F 8-bit | West European with Euro symbol (= ISO 8859/15) |

The character sets WE8BS2000, CL8BS2000, WE8BS2000L5, EE8BS2000, CE8BS2000, and WE8BS2000E are the recommended database character sets. The other character sets must only be used as the client character sets.

The character set WE8BS2000E must be used as a database character set to store the euro symbol in the database or to use the euro symbol as the dual currency symbol.

In addition to these supported character sets, if you are connecting to Oracle Database installations with a non-BS2000 character set, then those servers can use any of the character sets as listed in [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md).

**Note:**

A Unicode database character set is not supported on BS2000. To store Unicode characters in the database, you must use Unicode datatypes `NCHAR`, `NVARCHAR2`, and `NCLOB`. During database creation you can specify either AL16UTF16 or UTF8 as the national character set for these data types.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/supporting-multilingual-databases-with-unicode.md) for more information about Unicode support

### 16.5 Location of Message Files

All message files are located in `ORAMESG.LIB` in the installation user ID.

### 16.6 Linguistic Definitions

All the linguistic definitions listed in [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md) except the Unicode Collation Algorithm (UCA) collations are available.
