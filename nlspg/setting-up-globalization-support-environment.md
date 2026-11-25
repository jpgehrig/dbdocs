## 3  Setting Up a Globalization Support Environment

This chapter tells how to set up a globalization support environment. It includes the following topics:

- Setting NLS Parameters

- Choosing a Locale with the NLS_LANG Environment Variable

- Character Set Parameter

- NLS Database Parameters

- Language and Territory Parameters

- Date and Time Parameters

- Calendar Definitions

- Numeric and List Parameters

- Monetary Parameters

- Linguistic Sort Parameters

- Character Set Conversion Parameter

- Length Semantics

### 3.1 Setting NLS Parameters

NLS (National Language Support) parameters determine the locale-specific behavior on both the client and the server. NLS parameters can be specified in the following ways:

- As initialization parameters on the server

  You can include parameters in the initialization parameter file to specify a default session NLS environment. These settings have no effect on the client side; they control only the server's behavior. For example:

      NLS_TERRITORY = "CZECH REPUBLIC"

- As environment variables on the client

  You can use NLS environment variables, which may be platform-dependent, to specify locale-dependent behavior for the client and also to override the default values set for the session in the initialization parameter file. For example, on a UNIX system:

      % setenv NLS_SORT FRENCH

- With the `ALTER SESSION` statement

  You can use NLS parameters that are set in an `ALTER SESSION` statement to override the default values that are set for the session in the initialization parameter file or set by the client with environment variables.

      SQL> ALTER SESSION SET NLS_SORT = FRENCH;

  **See Also:**

  [Oracle Database SQL Language Reference](../sqlrf/ALTER-SESSION.md) for more information about the `ALTER SESSION` statement

- In SQL functions

  You can use NLS parameters explicitly to hardcode NLS behavior within a SQL function. This practice overrides the default values that are set for the session in the initialization parameter file, set for the client with environment variables, or set for the session by the `ALTER SESSION` statement. For example:

      TO_CHAR(hiredate, 'DD/MON/YYYY', 'nls_date_language = FRENCH')

  **See Also:**

  [Oracle Database SQL Language Reference](../sqlrf/About-SQL-Functions.md) for more information about SQL functions, including the `TO_CHAR` function

Table 3-1 shows the precedence order of the different methods of setting NLS parameters. Higher priority settings override lower priority settings. For example, a value specified in the initialization parameter file can be overridden by a value explicitly set in a SQL function.

Default values have the lowest priority. They are set at the time of database creation and cannot be changed. They can be overridden by any other method, with the following exception: Default values are always used when evaluating expressions in virtual columns, `CHECK` constraints, and fine-grained auditing (FGA) rules. These expressions must have deterministic results for the duration of their existence and cannot depend on NLS parameter settings that may change.

Table 3-1 Methods of Setting NLS Parameters and Their Priorities

| Priority    | Method                                                |
|:------------|:------------------------------------------------------|
| 1 (highest) | Explicitly set in SQL functions                       |
| 2           | Set by an `ALTER` `SESSION` statement                 |
| 3           | Set as an environment variable                        |
| 4           | Specified in the initialization parameter file        |
| 5 (lowest)  | Default value specified when the database was created |

Table 3-2 lists the available NLS parameters. Because the SQL function NLS parameters can be specified only with specific functions, the table does not show the SQL function scope. This table shows the following values for Scope:

   I = Initialization Parameter File
   E = Environment Variable
   A = ALTER SESSION

Table 3-2 NLS Parameters

| Parameter               | Description                                                 | Default                           | Scope   |
|:------------------------|:------------------------------------------------------------|:----------------------------------|:--------|
| NLS_CALENDAR            | Calendar system                                             | Gregorian                         | I, E, A |
| NLS_COMP                | SQL, PL/SQL operator comparison                             | `BINARY`                          | I, E, A |
| NLS_CREDIT              | Credit accounting symbol                                    | Derived from` NLS_TERRITORY`      | E       |
| NLS_CURRENCY            | Local currency symbol                                       | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_DATE_FORMAT         | Date format                                                 | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_DATE_LANGUAGE       | Language for day and month names                            | Derived from` NLS_LANGUAGE`       | I, E, A |
| NLS_DEBIT               | Debit accounting symbol                                     | Derived from` NLS_TERRITORY`      | E       |
| NLS_DUAL_CURRENCY       | Dual currency symbol                                        | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_ISO_CURRENCY        | ISO international currency symbol                           | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_LANG                | Language, territory, character set                          | `AMERICAN_AMERICA.`<br>`US7ASCII` | E       |
| NLS_LANGUAGE            | Language                                                    | Derived from` NLS_LANG`           | I, A    |
| NLS_LENGTH_SEMANTICS    | How strings are treated                                     | `BYTE`                            | I, E, A |
| NLS_LIST_SEPARATOR      | Character that separates items in a list                    | Derived from` NLS_TERRITORY`      | E       |
| NLS_MONETARY_CHARACTERS | Monetary symbol for dollar and cents (or their equivalents) | Derived from` NLS_TERRITORY`      | E       |
| NLS_NCHAR_CONV_EXCP     | Reports data loss during a character type conversion        | `FALSE`                           | I, A    |
| NLS_NUMERIC_CHARACTERS  | Decimal character and group separator                       | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_SORT                | Collation                                                   | Derived from` NLS_LANGUAGE`       | I, E, A |
| NLS_TERRITORY           | Territory                                                   | Derived from` NLS_LANG`           | I, A    |
| NLS_TIMESTAMP_FORMAT    | Timestamp                                                   | Derived from` NLS_TERRITORY`      | I, E, A |
| NLS_TIMESTAMP_TZ_FORMAT | Timestamp with time zone                                    | Derived from` NLS_TERRITORY`      | I, E, A |

### 3.2 Choosing a Locale with the NLS_LANG Environment Variable

A locale is a linguistic and cultural environment in which a system or program is running. Setting the `NLS_LANG` environment parameter is the simplest way to specify locale behavior for Oracle Database software. It sets the language and territory used by the client application and the database server. It also sets the client's character set, which is the character set for data entered or displayed by a client program.

`NLS_LANG` is set as an environment variable on UNIX platforms. `NLS_LANG` is set in the registry on Windows platforms.

The `NLS_LANG` parameter has three components: language, territory, and character set. Specify it in the following format, including the punctuation:

    NLS_LANG = language_territory.charset

For example, if the Oracle Universal Installer does not populate `NLS_LANG`, then its value by default is `AMERICAN_AMERICA.US7ASCII`. The language is `AMERICAN`, the territory is `AMERICA`, and the character set is `US7ASCII`. The values in `NLS_LANG` and other NLS parameters are case-insensitive.

Each component of the `NLS_LANG` parameter controls the operation of a subset of globalization support features:

- language

  Specifies conventions such as the language used for Oracle Database messages, sorting, day names, and month names. Each supported language has a unique name; for example, `AMERICAN`, `FRENCH`, or `GERMAN`. The language argument specifies default values for the territory and character set arguments. If the language is not specified, then the value defaults to `AMERICAN`.

- territory

  Specifies conventions such as the default date, monetary, and numeric formats. Each supported territory has a unique name; for example, `AMERICA`, `FRANCE`, or `CANADA`. If the territory is not specified, then the value is derived from the language value.

- charset

  Specifies the character set used by the client application (normally the Oracle Database character set that corresponds to the user's terminal character set or the OS character set). Each supported character set has a unique acronym, for example, `US7ASCII`, `WE8ISO8859P1`, `WE8DEC`, `WE8MSWIN1252`, or `JA16EUC`. Each language has a default character set associated with it.

  **Note:**

  All components of the `NLS_LANG` definition are optional; any item that is not specified uses its default value. If you specify territory or character set, then you must include the preceding delimiter (underscore (\_) for territory, period (.) for character set). Otherwise, the value is parsed as a language name.

  For example, to set only the territory portion of `NLS_LANG`, use the following format: `NLS_LANG=_JAPAN`

The three components of `NLS_LANG` can be specified in many combinations, as in the following examples:

    NLS_LANG = AMERICAN_AMERICA.WE8MSWIN1252

    NLS_LANG = FRENCH_CANADA.WE8ISO8859P1

    NLS_LANG = JAPANESE_JAPAN.JA16EUC

Note that illogical combinations can be set but do not work properly. For example, the following specification tries to support Japanese by using a Western European character set:

    NLS_LANG = JAPANESE_JAPAN.WE8ISO8859P1

Because the WE8ISO8859P1 character set does not support any Japanese characters, you cannot store or display Japanese data if you use this definition for `NLS_LANG`.

The rest of this section includes the following topics:

- Specifying the Value of NLS_LANG

- Overriding Language and Territory Specifications

- Locale Variants

**See Also:**

- "[Locale Data](appendix-A-locale-data.md)" for a complete list of supported languages, territories, and character sets

- Your operating system documentation for information about additional globalization settings that may be necessary for your platform

#### 3.2.1 Specifying the Value of NLS_LANG

In a UNIX operating system C-shell session, you can specify the value of `NLS_LANG` by entering a statement similar to the following example:

    % setenv NLS_LANG FRENCH_FRANCE.WE8ISO8859P1

Because `NLS_LANG` is an environment variable, it is read by the client application at startup time. The client communicates the information defined by `NLS_LANG` to the server when it connects to the database server.

The following examples show how date and number formats are affected by the `NLS_LANG` parameter.

Example 3-1 Setting NLS_LANG to American_America.WE8ISO8859P1

Set `NLS_LANG` so that the language is `AMERICAN`, the territory is `AMERICA`, and the Oracle Database character set is `WE8ISO8859P1`:

    % setenv NLS_LANG American_America.WE8ISO8859P1

Enter a `SELECT` statement:

    SQL> SELECT last_name, hire_date, ROUND(salary/8,2) salary FROM employees;

You should see results similar to the following output:

    LAST_NAME                 HIRE_DATE     SALARY
    ------------------------- --------- ----------
    ...
    Sciarra                   30-SEP-05      962.5
    Urman                     07-MAR-06        975
    Popp                      07-DEC-07      862.5
    ...

Example 3-2 Setting NLS_LANG to French_France.WE8ISO8859P1

Set `NLS_LANG` so that the language is `FRENCH`, the territory is `FRANCE`, and the Oracle Database character set is `WE8ISO8859P1`:

    % setenv NLS_LANG French_France.WE8ISO8859P1

Then the query shown in Example 3-1 returns the following output:

    LAST_NAME      HIRE_DATE     SALARY
    -------------- ---------  ---------
    ...
    Sciarra        30/09/05       962,5
    Urman          07/03/06         975
    Popp           07/12/07       862,5
    ...

Note that the date format and the number format have changed. The numbers have not changed, because the underlying data is the same.

#### 3.2.2 Overriding Language and Territory Specifications

The `NLS_LANG` parameter sets the language and territory environment used by both the server session (for example, SQL command execution) and the client application (for example, display formatting in Oracle Database tools). Using this parameter ensures that the language environments of both the database and the client application are automatically the same.

The language and territory components of the `NLS_LANG` parameter determine the default values for other detailed NLS parameters, such as date format, numeric characters, and linguistic sorting. Each of these detailed parameters can be set in the client environment to override the default values if the `NLS_LANG` parameter has already been set.

If the `NLS_LANG` parameter is not set, then the server session environment remains initialized with values of `NLS_LANGUAGE`, `NLS_TERRITORY`, and other NLS instance parameters from the initialization parameter file. You can modify these parameters and restart the instance to change the defaults.

You might want to modify the NLS environment dynamically during the session. To do so, you can use the `ALTER` `SESSION` statement to change `NLS_LANGUAGE`, `NLS_TERRITORY`, and other NLS parameters.

**Note:**

You cannot modify the setting for the client character set with the `ALTER SESSION` statement.

The `ALTER` `SESSION` statement modifies only the session environment. The local client NLS environment is not modified, unless the client explicitly retrieves the new settings and modifies its local environment.

**See Also:**

- "Overriding Default Values for NLS_LANGUAGE and NLS_TERRITORY During a Session"

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-SESSION.md)

#### 3.2.3 Locale Variants

Before Oracle Database 10g, Oracle defined language and territory definitions separately. This resulted in the definition of a territory being independent of the language setting of the user. Since Oracle Database 10g, some territories can have different date, time, number, and monetary formats based on the language setting of a user. This type of language-dependent territory definition is called a locale variant.

For the variant to work properly, both `NLS_TERRITORY` and `NLS_LANGUAGE` must be specified.

The following table shows the territories that have been enhanced to support variations.

Table 3-3 Oracle Database Locale Variants

| Oracle Database Territory | Oracle Database Language |
|:--------------------------|:-------------------------|
| BELGIUM                   | DUTCH                    |
| BELGIUM                   | FRENCH                   |
| BELGIUM                   | GERMAN                   |
| CANADA                    | FRENCH                   |
| CANADA                    | ENGLISH                  |
| DJIBOUTI                  | FRENCH                   |
| DJIBOUTI                  | ARABIC                   |
| FINLAND                   | FINLAND                  |
| FINLAND                   | SWEDISH                  |
| HONG KONG                 | TRADITIONAL CHINESE      |
| HONG KONG                 | ENGLISH                  |
| INDIA                     | ENGLISH                  |
| INDIA                     | ASSAMESE                 |
| INDIA                     | BANGLA                   |
| INDIA                     | GUJARATI                 |
| INDIA                     | HINDI                    |
| INDIA                     | KANNADA                  |
| INDIA                     | MALAYALAM                |
| INDIA                     | MARATHI                  |
| INDIA                     | ORIYA                    |
| INDIA                     | PUNJABI                  |
| INDIA                     | TAMIL                    |
| INDIA                     | TELUGU                   |
| LUXEMBOURG                | GERMAN                   |
| LUXEMBOURG                | FRENCH                   |
| SINGAPORE                 | ENGLISH                  |
| SINGAPORE                 | MALAY                    |
| SINGAPORE                 | SIMPLIFIED CHINESE       |
| SINGAPORE                 | TAMIL                    |
| SWITZERLAND               | GERMAN                   |
| SWITZERLAND               | FRENCH                   |
| SWITZERLAND               | ITALIAN                  |

#### 3.2.4 Should the NLS_LANG Setting Match the Database Character Set?

The `NLS_LANG` character set should reflect the setting of the operating system character set of the client. For example, if the database character set is AL32UTF8 and the client is running on a Windows operating system, then you should not set AL32UTF8 as the client character set in the `NLS_LANG` parameter because there are no UTF-8 WIN32 clients. Instead, the `NLS_LANG` setting should reflect the code page of the client. For example, on an English Windows client, the code page is 1252. An appropriate setting for `NLS_LANG` is `AMERICAN_AMERICA.WE8MSWIN1252`.

Setting `NLS_LANG` correctly enables proper conversion from the client operating system character set to the database character set. When these settings are the same, Oracle Database assumes that the data being sent or received is encoded in the same character set as the database character set, so character set validation or conversion may not be performed. This can lead to corrupt data if the client code page and the database character set are different and conversions are necessary.

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/configuring-locale-and-character-sets-using-environment-variable.md) for more information about commonly used values of the `NLS_LANG` parameter in Windows

### 3.3 Character Set Parameter

Oracle provides an environment variable, `NLS_OS_CHARSET`, for handling the situation where the client OS character set is different from the Oracle NLS client character set.

#### 3.3.1 NLS_OS_CHARSET Environment Variable

The `NLS_OS_CHARSET` environment variable should be set on Oracle client installations if the client OS character set is different from the Oracle NLS client character set specified by the `NLS_LANG` environment variable. The client OS character set is the character set used to represent characters in the OS fields like machine name, program executable name and logged on user name. On UNIX platforms, this is usually the character set specified in the `LANG` environment variable or the `LC_ALL` environment variable. An example of setting `NLS_OS_CHARSET` would be if the locale charset specified in `LANG` or `LC_ALL` in a Linux client could be `zh_CN` (simplified Chinese) and the Oracle client application charset specified in `NLS_LANG` could be `UTF8`. In this case, the `NLS_OS_CHARSET` variable must be set to the equivalent Oracle charset `ZHT16GBK`.

The `NLS_OS_CHARSET` environment variable must be set to the Oracle character set name corresponding to the client OS character set.

If `NLS_LANG` corresponds to the OS character set, `NLS_OS_CHARSET` does not need to be set. `NLS_OS_CHARSET` does not need to be set and is ignored on Windows platforms.

### 3.4 NLS Database Parameters

When a new database is created during the execution of the `CREATE` `DATABASE` statement, the NLS-related database configuration is established. The current NLS instance parameters are stored in the data dictionary along with the database and national character sets. The NLS instance parameters are read from the initialization parameter file at instance startup.

You can find the values for NLS parameters by using:

- NLS Data Dictionary Views

- NLS Dynamic Performance Views

- OCINlsGetInfo() Function

#### 3.4.1 NLS Data Dictionary Views

Applications can check the session, instance, and database NLS parameters by querying the following data dictionary views:

- `NLS_SESSION_PARAMETERS` shows the NLS parameters and their values for the session that is querying the view. It does not show information about the character set.

- `NLS_INSTANCE_PARAMETERS` shows the current NLS instance parameters that have been explicitly set and the values of the NLS instance parameters.

- `NLS_DATABASE_PARAMETERS` shows the values of the NLS parameters for the database. The values are stored in the database.

#### 3.4.2 NLS Dynamic Performance Views

Applications can check the following NLS dynamic performance views:

- `V$NLS_VALID_VALUES` lists values for the following NLS parameters:

      NLS_LANGUAGE
      NLS_SORT
      NLS_TERRITORY
      NLS_CHARACTERSET

- `V$NLS_PARAMETERS` shows current values of the following NLS parameters:

      NLS_CHARACTERSET
      NLS_NCHAR_CHARACTERSET
      NLS_NUMERIC_CHARACTERS
      NLS_DATE_FORMAT
      NLS_DATE_LANGUAGE
      NLS_TIME_TZ_FORMAT
      NLS_TIMESTAMP_FORMAT
      NLS_TIMESTAMP_TZ_FORMAT
      NLS_CALENDAR
      NLS_LANGUAGE
      NLS_CURRENCY
      NLS_ISO_CURRENCY
      NLS_TERRITORY
      NLS_SORT
      NLS_COMP
      NLS_LENGTH_SEMANTICS
      NLS_NCHAR_CONV_EXP

**See Also:**

[Oracle Database Reference](../refrn/V-NLS_PARAMETERS.md)

#### 3.4.3 OCINlsGetInfo() Function

User applications can query client NLS settings with the `OCINlsGetInfo()` function.

**See Also:**

"[Getting Locale Information in OCI](OCI-programming-in-global-environment.md)" for the description of `OCINlsGetInfo()`

### 3.5 Language and Territory Parameters

This section contains information about the following parameters:

- NLS_LANGUAGE

- NLS_TERRITORY

#### 3.5.1 NLS_LANGUAGE

| Property        | Description                                  |
|:----------------|:---------------------------------------------|
| Parameter type  | String                                       |
| Parameter scope | Initialization parameter and `ALTER SESSION` |
| Default value   | Derived from `NLS_LANG`                      |
| Range of values | Any valid language name                      |

`NLS_LANGUAGE` specifies the default conventions for the following session characteristics:

- Language for server messages

- Language for day and month names and their abbreviations (specified in the SQL functions `TO_CHAR` and `TO_DATE`)

- Symbols for equivalents of AM, PM, AD, and BC. (A.M., P.M., A.D., and B.C. are valid only if `NLS_LANGUAGE` is set to `AMERICAN`.)

- Default sorting sequence for character data when `ORDER` `BY` is specified. (`GROUP BY` uses a binary sort unless `ORDER` `BY` is specified.)

- Writing direction

- Affirmative and negative response strings (for example, `YES` and `NO`)

The value specified for `NLS_LANGUAGE` in the initialization parameter file is the default for all sessions in that instance. For example, to specify the default session language as French, the parameter should be set as follows:

    NLS_LANGUAGE = FRENCH

Consider the following server message:

    ORA-00942: table or view does not exist

When the language is French, the server message appears as follows:

    ORA-00942: table ou vue inexistante

Messages used by the server are stored in binary-format files that are placed in the `$ORACLE_HOME/``product_name``/mesg` directory, or the equivalent for your operating system. Multiple versions of these files can exist, one for each supported language, using the following file name convention:

    <product_id><language_abbrev>.MSB

For example, the file containing the server messages in French is called `oraf.msb`, because `ORA` is the product ID (`<product_id>`) and `F` is the language abbreviation (`<language_abbrev>`) for French. The `product_name` is `rdbms`, so it is in the `$ORACLE_HOME/rdbms/mesg` directory.

If `NLS_LANG` is specified in the client environment, then the value of `NLS_LANGUAGE` in the initialization parameter file is overridden at connection time.

Messages are stored in these files in one specific character set, depending on the language and the operating system. If this character set is different from the database character set, then message text is automatically converted to the database character set. If necessary, it is then converted to the client character set if the client character set is different from the database character set. Hence, messages are displayed correctly at the user's terminal, subject to the limitations of character set conversion.

The language-specific binary message files that are actually installed depend on the languages that the user specifies during product installation. Only the English binary message file and the language-specific binary message files specified by the user are installed.

The default value of `NLS_LANGUAGE` may be specific to the operating system. You can alter the `NLS_LANGUAGE` parameter by changing its value in the initialization parameter file and then restarting the instance.

**See Also:**

Your operating system-specific Oracle Database documentation for more information about the default value of `NLS_LANGUAGE`

All messages and text should be in the same language. For example, when you run an Oracle Developer application, the messages and boilerplate text that you see originate from three sources:

- Messages from the server

- Messages and boilerplate text generated by Oracle Forms

- Messages and boilerplate text generated by the application

`NLS_LANGUAGE` determines the language used for the first two kinds of text. The application is responsible for the language used in its messages and boilerplate text.

**See Also:**

"Overriding Default Values for NLS_LANGUAGE and NLS_TERRITORY During a Session" for more information about using the `ALTER SESSION` statement

The following examples show behavior that results from setting `NLS_LANGUAGE` to different values.

Example 3-3 NLS_LANGUAGE=ITALIAN

Use the `ALTER SESSION` statement to set `NLS_LANGUAGE` to Italian:

    SQL> ALTER SESSION SET NLS_LANGUAGE=Italian;

Enter a `SELECT` statement:

    SQL> SELECT last_name, hire_date, ROUND(salary/8,2) salary FROM employees;

You should see results similar to the following output:

    LAST_NAME      HIRE_DATE     SALARY
    -------------- --------- ----------
    ...
    Sciarra        30-SET-05      962.5
    Urman          07-MAR-06        975
    Popp           07-DIC-07      862.5
    ...

Note that the month name abbreviations are in Italian.

Example 3-4 NLS_LANGUAGE=GERMAN

Use the `ALTER SESSION` statement to change the language to German:

    SQL> ALTER SESSION SET NLS_LANGUAGE=German;

Enter the same `SELECT` statement:

    SQL> SELECT last_name, hire_date, ROUND(salary/8,2) salary FROM employees;

You should see results similar to the following output:

    LAST_NAME      HIRE_DATE     SALARY
    -------------- --------- ----------
    ...
    Sciarra        30-SEP-05      962.5
    Urman          07-MRZ-06        975
    Popp           07-DEZ-07      862.5
    ...

Note that the language of the month abbreviations has changed.

#### 3.5.2 NLS_TERRITORY

| Property        | Description                                  |
|:----------------|:---------------------------------------------|
| Parameter type  | String                                       |
| Parameter scope | Initialization parameter and `ALTER SESSION` |
| Default value   | Derived from `NLS_LANG`                      |
| Range of values | Any valid territory name                     |

`NLS_TERRITORY` specifies the conventions for the following default date and numeric formatting characteristics:

- Date format

- Decimal character and group separator

- Local currency symbol

- ISO currency symbol

- Dual currency symbol

- First day of the week

- Credit and debit symbols

- ISO week flag

- List separator

The value specified for `NLS_TERRITORY` in the initialization parameter file is the default for the instance. For example, to specify the default as France, the parameter should be set as follows:

    NLS_TERRITORY = FRANCE

When the territory is `FRANCE`, numbers are formatted using a comma as the decimal character.

You can alter the `NLS_TERRITORY` parameter by changing the value in the initialization parameter file and then restarting the instance. The default value of `NLS_TERRITORY` can be specific to the operating system.

If `NLS_LANG` is specified in the client environment, then the value of `NLS_TERRITORY` in the initialization parameter file is overridden at connection time.

The territory can be modified dynamically during the session by specifying the new `NLS_TERRITORY` value in an `ALTER` `SESSION` statement. Modifying `NLS_TERRITORY` resets all derived NLS session parameters to default values for the new territory.

To change the territory to France during a session, issue the following `ALTER SESSION` statement:

    SQL> ALTER SESSION SET NLS_TERRITORY = France;

**See Also:**

"Overriding Default Values for NLS_LANGUAGE and NLS_TERRITORY During a Session" for more information about using the `ALTER SESSION` statement

The following examples show behavior that results from different settings of `NLS_TERRITORY` and `NLS_LANGUAGE`.

Example 3-5 NLS_LANGUAGE=AMERICAN, NLS_TERRITORY=AMERICA

Enter the following `SELECT` statement:

    SQL> SELECT TO_CHAR(salary,'L99G999D99') salary FROM employees;

When `NLS_TERRITORY` is set to `AMERICA` and `NLS_LANGUAGE` is set to `AMERICAN`, results similar to the following should appear:

    SALARY
    --------------------
    $24,000.00
    $17,000.00
    $17,000.00

Example 3-6 NLS_LANGUAGE=AMERICAN, NLS_TERRITORY=GERMANY

Use an `ALTER SESSION` statement to change the territory to Germany:

    SQL> ALTER SESSION SET NLS_TERRITORY = Germany;
    Session altered.

Enter the same `SELECT` statement as before:

    SQL> SELECT TO_CHAR(salary,'L99G999D99') salary FROM employees;

You should see results similar to the following output:

    SALARY
    --------------------
    €24.000,00
    €17.000,00
    €17.000,00

Note that the currency symbol has changed from `$` to €. The numbers have not changed because the underlying data is the same.

Example 3-7 NLS_LANGUAGE=GERMAN, NLS_TERRITORY=GERMANY

Use an `ALTER SESSION` statement to change the language to German:

    SQL> ALTER SESSION SET NLS_LANGUAGE = German;
    Session wurde geändert.

Note that the server message now appears in German.

Enter the same `SELECT` statement as before:

    SQL> SELECT TO_CHAR(salary,'L99G999D99') salary FROM employees;

You should see the same results as in Example 3-6:

    SALARY
    --------------------
    €24.000,00
    €17.000,00
    €17.000,00

Example 3-8 NLS_LANGUAGE=GERMAN, NLS_TERRITORY=AMERICA

Use an `ALTER SESSION` statement to change the territory to America:

    SQL> ALTER SESSION SET NLS_TERRITORY = America;
    Session wurde geändert.

Enter the same `SELECT` statement as in the other examples:

    SQL> SELECT TO_CHAR(salary,'L99G999D99') salary FROM employees;

You should see results similar to the following output:

    SALARY
    --------------------
    $24,000.00
    $17,000.00
    $17,000.00

Note that the currency symbol changed from € to `$` because the territory changed from Germany to America.

##### 3.5.2.1 Overriding Default Values for NLS_LANGUAGE and NLS_TERRITORY During a Session

Default values for `NLS_LANGUAGE` and `NLS_TERRITORY` and default values for specific formatting parameters can be overridden during a session by using the `ALTER` `SESSION` statement.

Example 3-9 NLS_LANG=ITALIAN_ITALY.WE8DEC

Set the `NLS_LANG` environment variable so that the language is Italian, the territory is Italy, and the character set is WE8DEC:

    % setenv NLS_LANG Italian_Italy.WE8DEC

Enter a `SELECT` statement:

    SQL> SELECT last_name, hire_date, ROUND(salary/8,2) salary FROM employees;

You should see results similar to the following output:

    LAST_NAME      HIRE_DATE     SALARY
    -------------- --------- ----------
    ...
    Sciarra        30-SET-05      962,5
    Urman          07-MAR-06        975
    Popp           07-DIC-07      862,5
    ...

Note the language of the month abbreviations and the decimal character.

Example 3-10 Change Language, Date Format, and Decimal Character

Use `ALTER SESSION` statements to change the language, the date format, and the decimal character:

    SQL> ALTER SESSION SET NLS_LANGUAGE=german;

    Session wurde geändert.

    SQL> ALTER SESSION SET NLS_DATE_FORMAT='DD.MON.YY';

    Session wurde geändert.

    SQL> ALTER SESSION SET NLS_NUMERIC_CHARACTERS='.,';

    Session wurde geändert.

Enter the `SELECT` statement shown in Example 3-9:

    SQL> SELECT last_name, hire_date, ROUND(salary/8,2) salary FROM employees;

You should see results similar to the following output:

    LAST_NAME      HIRE_DATE     SALARY
    -------------- --------- ----------
    ...
    Sciarra        30.SEP.05      962.5
    Urman          07.MRZ.06        975
    Popp           07.DEZ.07      862.5
    ...

Note that the language of the month abbreviations is German and the decimal character is a period.

The behavior of the `NLS_LANG` environment variable implicitly determines the language environment of the database for each session. When a session connects to a database, an `ALTER` `SESSION` statement is automatically executed to set the values of the database parameters `NLS_LANGUAGE` and `NLS_TERRITORY` to those specified by the `language` and `territory` arguments of `NLS_LANG`. If `NLS_LANG` is not defined, then no implicit `ALTER` `SESSION` statement is executed.

When `NLS_LANG` is defined, the implicit `ALTER` `SESSION` is executed for all instances to which the session connects, for both direct and indirect connections. If the values of NLS parameters are changed explicitly with `ALTER` `SESSION` during a session, then the changes are propagated to all instances to which that user session is connected.

### 3.6 Date and Time Parameters

Oracle Database enables you to control the display of date and time. This section contains the following topics:

- Date Formats

- Time Formats

#### 3.6.1 Date Formats

Different Oracle Database date formats are shown in the following table.

Table 3-4 Date Formats

| Country | Description | Example    |
|:--------|:------------|:-----------|
| Estonia | dd.mm.yyyy  | 28.02.2003 |
| Germany | dd-mm-rr    | 28-02-03   |
| Japan   | rr-mm-dd    | 03-02-28   |
| UK      | dd-mon-rr   | 28-Feb-03  |
| US      | dd-mon-rr   | 28-Feb-03  |

This section includes the following parameters:

- NLS_DATE_FORMAT

- NLS_DATE_LANGUAGE

##### 3.6.1.1 NLS_DATE_FORMAT

| Property        | Description                                                         |
|:----------------|:--------------------------------------------------------------------|
| Parameter type  | String                                                              |
| Parameter scope | Initialization parameter, environment variable, and `ALTER SESSION` |
| Default value   | Derived from `NLS_TERRITORY`                                        |
| Range of values | Any valid date format mask                                          |

The `NLS_DATE_FORMAT` parameter defines the default date format to use with the `TO_CHAR` and `TO_DATE` functions. The `NLS_TERRITORY` parameter determines the default value of `NLS_DATE_FORMAT`. The value of `NLS_DATE_FORMAT` can be any valid date format mask. For example:

    NLS_DATE_FORMAT = "MM/DD/YYYY"

To add string literals to the date format, enclose the string literal with double quotes. Note that when double quotes are included in the date format, the entire value must be enclosed by single quotes. For example:

    NLS_DATE_FORMAT = '"Date: "MM/DD/YYYY'

The value of `NLS_DATE_FORMAT` is stored in the internal date format. Each format element occupies two bytes, and each string occupies the number of bytes in the string plus a terminator byte. Also, the entire format mask has a two-byte terminator. For example, "MM/DD/YY" occupies 14 bytes internally because there are three format elements (month, day, and year), two 3-byte strings (the two slashes), and the two-byte terminator for the format mask. The format for the value of `NLS_DATE_FORMAT` cannot exceed 24 bytes.

You can alter the default value of `NLS_DATE_FORMAT` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using an `ALTER` `SESSION` `SET` `NLS_DATE_FORMAT` statement

  **See Also:**

  [Oracle Database SQL Language Reference](../sqlrf/ALTER-SESSION.md) for more information about date format elements and the `ALTER` `SESSION` statement

If a table or index is partitioned on a date column, and if the date format specified by `NLS_DATE_FORMAT` does not specify the first two digits of the year, then you must use the `TO_DATE` function with a 4-character format mask for the year. For example:

    TO_DATE('11-jan-1997', 'dd-mon-yyyy')

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md) for more information about partitioning tables and indexes and using `TO_DATE`

Example 3-11 Setting the Date Format to Display Roman Numerals

To set the default date format to display Roman numerals for the month, include the following line in the initialization parameter file:

    NLS_DATE_FORMAT = "DD RM YYYY"

Enter the following `SELECT` statement:

    SQL> SELECT TO_CHAR(SYSDATE) currdate FROM DUAL;

You should see the following output if today's date is February 12, 1997:

    CURRDATE
    ---------
    12 II 1997

##### 3.6.1.2 NLS_DATE_LANGUAGE

| Property        | Description                                                                        |
|:----------------|:-----------------------------------------------------------------------------------|
| Parameter type  | String                                                                             |
| Parameter scope | Initialization parameter, environment variable, `ALTER SESSION`, and SQL functions |
| Default value   | Derived from `NLS_LANGUAGE`                                                        |
| Range of values | Any valid language name                                                            |

The `NLS_DATE_LANGUAGE` parameter specifies the language for the day and month names produced by the `TO_CHAR` and `TO_DATE` functions. `NLS_DATE_LANGUAGE` overrides the language that is specified implicitly by `NLS_LANGUAGE`. `NLS_DATE_LANGUAGE` has the same syntax as the `NLS_LANGUAGE` parameter, and all supported languages are valid values.

`NLS_DATE_LANGUAGE` also determines the language used for:

- Month and day abbreviations returned by the `TO_CHAR` and `TO_DATE` functions

- Month and day abbreviations used by the default date format (`NLS_DATE_FORMAT`)

- Abbreviations for AM, PM, AD, and BC

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Format-Models.md)

Example 3-12 NLS_DATE_LANGUAGE=FRENCH, Month and Day Names

As an example of how to use `NLS_DATE_LANGUAGE`, set the date language to French:

    SQL> ALTER SESSION SET NLS_DATE_LANGUAGE = FRENCH;

Enter a `SELECT` statement:

    SQL> SELECT TO_CHAR(SYSDATE, 'Day:Dd Month yyyy') FROM DUAL;

You should see results similar to the following output:

    TO_CHAR(SYSDATE,'DAY:DDMONTHYYYY')
    ------------------------------------------------------------
    Vendredi:07 Décembre  2001

When numbers are spelled in words using the `TO_CHAR` function, the English spelling is always used. For example, enter the following `SELECT` statement:

    SQL> SELECT TO_CHAR(TO_DATE('12-Oct.-2001'),'Day: ddspth Month') FROM DUAL;

You should see results similar to the following output:

    TO_CHAR(TO_DATE('12-OCT.-2001'),'DAY:DDSPTHMONTH')
    --------------------------------------------------------------------
    Vendredi: twelfth Octobre

Example 3-13 NLS_DATE_LANGUAGE=FRENCH, Month and Day Abbreviations

Month and day abbreviations are determined by `NLS_DATE_LANGUAGE`. Enter the following `SELECT` statement:

    SQL> SELECT TO_CHAR(SYSDATE, 'Dy:dd Mon yyyy') FROM DUAL;

You should see results similar to the following output:

    TO_CHAR(SYSDATE,'DY:DDMO
    ------------------------
    Ve:07 Déc. 2001

Example 3-14 NLS_DATE_LANGUAGE=FRENCH, Default Date Format

The default date format uses the month abbreviations determined by `NLS_DATE_LANGUAGE`. For example, if the default date format is `DD-MON-YYYY`, then insert a date as follows:

    SQL> INSERT INTO tablename VALUES ('12-Févr.-1997');

#### 3.6.2 Time Formats

Different Oracle Database time formats are shown in the following table.

Table 3-5 Time Formats

| Country | Description    | Example        |
|:--------|:---------------|:---------------|
| Estonia | hh24:mi:ss     | 13:50:23       |
| Germany | hh24:mi:ss     | 13:50:23       |
| Japan   | hh24:mi:ss     | 13:50:23       |
| UK      | hh24:mi:ss     | 13:50:23       |
| US      | hh:mi:ssxff am | 1:50:23.555 PM |

This section contains information about the following parameters:

- NLS_TIMESTAMP_FORMAT

- NLS_TIMESTAMP_TZ_FORMAT

**See Also:**

"[Datetime Data Types and Time Zone Support](datetime-data-types-and-time-zone-support.md)"

##### 3.6.2.1 NLS_TIMESTAMP_FORMAT

| Property        | Description                                                         |
|:----------------|:--------------------------------------------------------------------|
| Parameter type  | String                                                              |
| Parameter scope | Initialization parameter, environment variable, and `ALTER SESSION` |
| Default value   | Derived from `NLS_TERRITORY`                                        |
| Range of values | Any valid datetime format mask                                      |

`NLS_TIMESTAMP_FORMAT` defines the default date format for the `TIMESTAMP` and `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` data types. The following example shows a value for `NLS_TIMESTAMP_FORMAT`:

    NLS_TIMESTAMP_FORMAT  = 'YYYY-MM-DD HH:MI:SS.FF'

You can specify the value of `NLS_TIMESTAMP_FORMAT` by setting it in the initialization parameter file. You can specify its value for a client as a client environment variable.

You can also alter the value of `NLS_TIMESTAMP_FORMAT` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using the `ALTER` `SESSION` `SET` `NLS_TIMESTAMP_FORMAT` statement

**See Also:**

[Oracle Database SQL Language Reference ](../sqlrf/TO_TIMESTAMP.md)for more information about the `TO_TIMESTAMP` function and the `ALTER SESSION` statement

Example 3-15 Timestamp Format

    SQL> SELECT TO_TIMESTAMP('11-nov-2000 01:00:00.336', 'dd-mon-yyyy hh:mi:ss.ff') FROM DUAL;

You should see results similar to the following output:

    TO_TIMESTAMP('11-NOV-200001:00:00.336','DD-MON-YYYYHH:MI:SS.FF')
    ---------------------------------------------------------------------------
    2000-11-11 01:00:00.336000000

##### 3.6.2.2 NLS_TIMESTAMP_TZ_FORMAT

| Property        | Description                                                         |
|:----------------|:--------------------------------------------------------------------|
| Parameter type  | String                                                              |
| Parameter scope | Initialization parameter, environment variable, and `ALTER SESSION` |
| Default value   | Derived from `NLS_TERRITORY`                                        |
| Range of values | Any valid datetime format mask                                      |

`NLS_TIMESTAMP_TZ_FORMAT` defines the default date format for the `TIMESTAMP` and `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` data types. It is used with the `TO_CHAR` and `TO_TIMESTAMP_TZ` functions.

You can specify the value of `NLS_TIMESTAMP_TZ_FORMAT` by setting it in the initialization parameter file. You can specify its value for a client as a client environment variable.

You can change the value of `NLS_TIMESTAMP_TZ_FORMAT` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using the `ALTER` `SESSION` statement.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/TO_TIMESTAMP_TZ.md) for more information about the `TO_TIMESTAMP_TZ` function and the `ALTER SESSION` statement

- "[Choosing a Time Zone File](datetime-data-types-and-time-zone-support.md)" for more information about time zones

Example 3-16 Setting NLS_TIMESTAMP_TZ_FORMAT

The format value must be surrounded by quotation marks. For example:

    NLS_TIMESTAMP_TZ_FORMAT  = 'YYYY-MM-DD HH:MI:SS.FF TZH:TZM'

The following example of the `TO_TIMESTAMP_TZ` function uses the format value that was specified for `NLS_TIMESTAMP_TZ_FORMAT`:

    SQL> SELECT TO_TIMESTAMP_TZ('2000-08-20, 05:00:00.55 America/Los_Angeles', 'yyyy-mm-dd hh:mi:ss.ff TZR') FROM DUAL;

You should see results similar to the following output:

    TO_TIMESTAMP_TZ('2000-08-20,05:00:00.55AMERICA/LOS_ANGELES','YYYY-MM-DDHH:M
    ---------------------------------------------------------------------------
    2000-08-20 05:00:00.550000000 -07:00

### 3.7 Calendar Definitions

This section includes the following topics:

- Calendar Formats

- NLS_CALENDAR

#### 3.7.1 Calendar Formats

The following calendar information is stored for each territory:

- First Day of the Week

- First Calendar Week of the Year

- Number of Days and Months in a Year

- First Year of Era

##### 3.7.1.1 First Day of the Week

Some cultures consider Sunday to be the first day of the week. Others consider Monday to be the first day of the week. A German calendar starts with Monday, as shown in the following table.

Table 3-6 German Calendar Example: March 1998

| Mo  | Di  | Mi  | Do  | Fr  | Sa  | So  |
|:----|:----|:----|:----|:----|:----|:----|
| \-  | \-  | \-  | \-  | \-  | \-  | 1   |
| 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| 9   | 10  | 11  | 12  | 13  | 14  | 15  |
| 16  | 17  | 18  | 19  | 20  | 21  | 22  |
| 23  | 24  | 25  | 26  | 27  | 28  | 29  |
| 30  | 31  | \-  | \-  | \-  | \-  | \-  |

The first day of the week is determined by the `NLS_TERRITORY` parameter.

**See Also:**

"NLS_TERRITORY"

##### 3.7.1.2 First Calendar Week of the Year

Some countries use week numbers for scheduling, planning, and bookkeeping. Oracle Database supports this convention. In the ISO standard, the week number can be different from the week number of the calendar year. For example, 1st Jan 1988 is in ISO week number 53 of 1987. An ISO week always starts on a Monday and ends on a Sunday.

- If January 1 falls on a Friday, Saturday, or Sunday, then the ISO week that includes January 1 is the last week of the previous year, because most of the days in the week belong to the previous year.

- If January 1 falls on a Monday, Tuesday, Wednesday, or Thursday, then the ISO week is the first week of the new year, because most of the days in the week belong to the new year.

To support the ISO standard, Oracle Database provides the IW date format element. It returns the ISO week number.

The following table shows an example in which January 1 occurs in a week that has four or more days in the first calendar week of the year. The week containing January 1 is the first ISO week of 1998.

Table 3-7 First ISO Week of the Year: Example 1, January 1998

| Mo  | Tu  | We  | Th  | Fr  | Sa  | Su  | ISO Week                |
|:----|:----|:----|:----|:----|:----|:----|:------------------------|
| \-  | \-  | \-  | 1   | 2   | 3   | 4   | First ISO week of 1998  |
| 5   | 6   | 7   | 8   | 9   | 10  | 11  | Second ISO week of 1998 |
| 12  | 13  | 14  | 15  | 16  | 17  | 18  | Third ISO week of 1998  |
| 19  | 20  | 21  | 22  | 23  | 24  | 25  | Fourth ISO week of 1998 |
| 26  | 27  | 28  | 29  | 30  | 31  | \-  | Fifth ISO week of 1998  |

The following table shows an example in which January 1 occurs in a week that has three or fewer days in the first calendar week of the year. The week containing January 1 is the 53rd ISO week of 1998, and the following week is the first ISO week of 1999.

Table 3-8 First ISO Week of the Year: Example 2, January 1999

| Mo  | Tu  | We  | Th  | Fr  | Sa  | Su  | ISO Week                     |
|:----|:----|:----|:----|:----|:----|:----|:-----------------------------|
| \-  | \-  | \-  | \-  | 1   | 2   | 3   | Fifty-third ISO week of 1998 |
| 4   | 5   | 6   | 7   | 8   | 9   | 10  | First ISO week of 1999       |
| 11  | 12  | 13  | 14  | 15  | 16  | 17  | Second ISO week of 1999      |
| 18  | 19  | 20  | 21  | 22  | 23  | 24  | Third ISO week of 1999       |
| 25  | 26  | 27  | 28  | 29  | 30  | 31  | Fourth ISO week of 1999      |

The first calendar week of the year is determined by the `NLS_TERRITORY` parameter.

**See Also:**

"NLS_TERRITORY"

##### 3.7.1.3 Number of Days and Months in a Year

Oracle Database supports six calendar systems in addition to Gregorian, the default:

- Japanese Imperial—uses the same number of months and days as Gregorian, but the year starts with the beginning of each Imperial Era.

- ROC Official—uses the same number of months and days as Gregorian, but the year starts with the founding of the Republic of China.

- Persian—has 31 days for each of the first six months. The next five months have 30 days each. The last month has either 29 days or 30 days (leap year).

- Thai Buddha—uses a Buddhist calendar

- Arabic Hijrah—has 12 months with 354 or 355 days

- English Hijrah—has 12 months with 354 or 355 days

- Ethiopian—has 12 months of 30 days each, then a 13th month that is either five or six days (leap year). The sixth day of the 13th month is added every four years.

The calendar system is specified by the `NLS_CALENDAR` parameter.

**See Also:**

"NLS_CALENDAR"

##### 3.7.1.4 First Year of Era

The Islamic calendar starts from the year of the Hegira.

The Japanese Imperial calendar starts from the beginning of an Emperor's reign. For example, 1998 is the tenth year of the Heisei era. It should be noted, however, that the Gregorian system is also widely understood in Japan, so both 98 and Heisei 10 can be used to represent 1998.

#### 3.7.2 NLS_CALENDAR

| Property        | Description                                                                          |
|:----------------|:-------------------------------------------------------------------------------------|
| Parameter type  | String                                                                               |
| Parameter scope | Initialization parameter, environment variable, `ALTER` `SESSION`, and SQL functions |
| Default value   | None, implies `GREGORIAN`                                                            |
| Range of values | Any valid calendar format name                                                       |

Many different calendar systems are in use throughout the world. `NLS_CALENDAR` specifies which calendar system Oracle Database uses.

`NLS_CALENDAR` can have one of the following values:

- `Arabic` `Hijrah`

- `English` `Hijrah`

- `Ethiopian`

- `GREGORIAN`

- `Japanese` `Imperial`

- `Persian`

- `ROC` `Official` (Republic of China)

- `Thai` `Buddha`

**See Also:**

"[Calendar Systems](appendix-A-locale-data.md)" for a list of calendar systems, their default date formats, and the character sets in which dates are displayed

Example 3-17 NLS_CALENDAR='English Hijrah'

Set `NLS_CALENDAR` to English Hijrah.

    SQL> ALTER SESSION SET NLS_CALENDAR='English Hijrah';

Enter a `SELECT` statement to display `SYSDATE`:

    SQL> SELECT SYSDATE FROM DUAL;

You should see results similar to the following output:

    SYSDATE
    --------------------
    24 Ramadan     1422

### 3.8 Numeric and List Parameters

This section includes the following topics:

- Numeric Formats

- NLS_NUMERIC_CHARACTERS

- NLS_LIST_SEPARATOR

#### 3.8.1 Numeric Formats

The database must know the number-formatting convention used in each session to interpret numeric strings correctly. For example, the database needs to know whether numbers are entered with a period or a comma as the decimal character (234.00 or 234,00). Similarly, applications must be able to display numeric information in the format expected at the client site.

Examples of numeric formats are shown in the following table.

Table 3-9 Examples of Numeric Formats

| Country | Numeric Formats |
|:--------|:----------------|
| Estonia | 1 234 567,89    |
| Germany | 1.234.567,89    |
| Japan   | 1,234,567.89    |
| UK      | 1,234,567.89    |
| US      | 1,234,567.89    |

Numeric formats are derived from the setting of the `NLS_TERRITORY` parameter, but they can be overridden by the `NLS_NUMERIC_CHARACTERS` parameter.

**See Also:**

"NLS_TERRITORY"

#### 3.8.2 NLS_NUMERIC_CHARACTERS

| Property        | Description                                                                        |
|:----------------|:-----------------------------------------------------------------------------------|
| Parameter type  | String                                                                             |
| Parameter scope | Initialization parameter, environment variable, `ALTER SESSION`, and SQL functions |
| Default value   | Default decimal character and group separator for a particular territory           |
| Range of values | Any two valid numeric characters                                                   |

This parameter specifies the decimal character and group separator. The group separator is the character that separates integer groups to show thousands and millions, for example. The group separator is the character returned by the G number format mask. The decimal character separates the integer and decimal parts of a number. Setting `NLS_NUMERIC_CHARACTERS` overrides the values derived from the setting of `NLS_TERRITORY`.

Any character can be the decimal character or group separator. The two characters specified must be single-byte, and the characters must be different from each other. The characters cannot be any numeric character or any of the following characters: plus (+), hyphen (-), less than sign (\<), greater than sign (\>). Either character can be a space.

You can change the default value of `NLS_NUMERIC_CHARACTERS` by:

- Changing the value of `NLS_NUMERIC_CHARACTERS` in the initialization parameter file and then restarting the instance

- Using the `ALTER` `SESSION` statement to change the parameter's value during a session

  **See Also:**

  [Oracle Database SQL Language Reference ](../sqlrf/ALTER-SESSION.md)for more information about the `ALTER SESSION` statement

Example 3-18 Setting NLS_NUMERIC_CHARACTERS

To set the decimal character to a comma and the grouping separator to a period, define `NLS_NUMERIC_CHARACTERS` as follows:

    SQL> ALTER SESSION SET NLS_NUMERIC_CHARACTERS = ",.";

SQL statements can include numbers represented as numeric or text literals. Numeric literals are not enclosed in quotes. They are part of the SQL language syntax and always use a dot as the decimal character and never contain a group separator. Text literals are enclosed in single quotes. They are implicitly or explicitly converted to numbers, if required, according to the current NLS settings.

The following `SELECT` statement formats the number 4000 with the decimal character and group separator specified in the `ALTER` `SESSION` statement:

    SQL> SELECT TO_CHAR(4000, '9G999D99') FROM DUAL;

You should see results similar to the following output:

    TO_CHAR(4
    ---------
     4.000,00

#### 3.8.3 NLS_LIST_SEPARATOR

| Property        | Description                  |
|:----------------|:-----------------------------|
| Parameter type  | String                       |
| Parameter scope | Environment variable         |
| Default value   | Derived from `NLS_TERRITORY` |
| Range of values | Any valid character          |

`NLS_LIST_SEPARATOR` specifies the character to use to separate values in a list of values (usually `,` or `.` or `;` or `:`). Its default value is derived from the value of `NLS_TERRITORY`. For example, a list of numbers from 1 to 5 can be expressed as 1,2,3,4,5 or 1.2.3.4.5 or 1;2;3;4;5 or 1:2:3:4:5.

The character specified must be single-byte and cannot be the same as either the numeric or monetary decimal character, any numeric character, or any of the following characters: plus (+), hyphen (-), less than sign (\<), greater than sign (\>), period (.).

### 3.9 Monetary Parameters

This section includes the following topics:

- Currency Formats

- NLS_CURRENCY

- NLS_ISO_CURRENCY

- NLS_DUAL_CURRENCY

- NLS_MONETARY_CHARACTERS

- NLS_CREDIT

- NLS_DEBIT

#### 3.9.1 Currency Formats

Different currency formats are used throughout the world. Some typical ones are shown in the following table.

Table 3-10 Currency Format Examples

| Country | Example     |
|:--------|:------------|
| Estonia | 1 234,56 kr |
| Germany | 1.234,56€   |
| Japan   | ©1,234.56   |
| UK      | £1,234.56   |
| US      | \$1,234.56  |

#### 3.9.2 NLS_CURRENCY

| Property        | Description                                                                        |
|:----------------|:-----------------------------------------------------------------------------------|
| Parameter type  | String                                                                             |
| Parameter scope | Initialization parameter, environment variable, `ALTER SESSION`, and SQL functions |
| Default value   | Derived from `NLS_TERRITORY`                                                       |
| Range of values | Any valid currency symbol string                                                   |

`NLS_CURRENCY` specifies the character string returned by the L number format mask, the local currency symbol. Setting `NLS_CURRENCY` overrides the setting defined implicitly by `NLS_TERRITORY`.

You can change the default value of `NLS_CURRENCY` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using an `ALTER` `SESSION` statement

  **See Also:**

  [Oracle Database SQL Language Reference ](../sqlrf/ALTER-SESSION.md)for more information about the `ALTER` `SESSION` statement

Example 3-19 Displaying the Local Currency Symbol

Connect to the sample order entry schema:

    SQL> connect oe/oe
    Connected.

Enter a `SELECT` statement similar to the following example:

    SQL> SELECT TO_CHAR(order_total, 'L099G999D99') "total" FROM orders
         WHERE order_id > 2450;

You should see results similar to the following output:

    total
    ---------------------
              $078,279.60
              $006,653.40
              $014,087.50
              $010,474.60
              $012,589.00
              $000,129.00
              $003,878.40
              $021,586.20

#### 3.9.3 NLS_ISO_CURRENCY

| Property        | Description                                                                          |
|:----------------|:-------------------------------------------------------------------------------------|
| Parameter type  | String                                                                               |
| Parameter scope | Initialization parameter, environment variable, `ALTER` `SESSION`, and SQL functions |
| Default value   | Derived from `NLS_TERRITORY`                                                         |
| Range of values | Any valid string                                                                     |

`NLS_ISO_CURRENCY` specifies the character string returned by the `C` number format mask, the ISO currency symbol. Setting `NLS_ISO_CURRENCY` overrides the value defined implicitly by `NLS_TERRITORY`.

Local currency symbols can be ambiguous. For example, a dollar sign (\$) can refer to US dollars or Australian dollars. ISO specifications define unique currency symbols for specific territories or countries. For example, the ISO currency symbol for the US dollar is USD. The ISO currency symbol for the Australian dollar is AUD.

More ISO currency symbols are shown in the following table.

Table 3-11 ISO Currency Examples

| Country | Example          |
|:--------|:-----------------|
| Estonia | 1 234 567,89 EEK |
| Germany | 1.234.567,89 EUR |
| Japan   | 1,234,567.89 JPY |
| UK      | 1,234,567.89 GBP |
| US      | 1,234,567.89 USD |

`NLS_ISO_CURRENCY` has the same syntax as the `NLS_TERRITORY` parameter, and all supported territories are valid values.

You can change the default value of `NLS_ISO_CURRENCY` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using an `ALTER SESSION` statement

  **See Also:**

  [Oracle Database SQL Language Reference ](../sqlrf/ALTER-SESSION.md)for more information about the `ALTER` `SESSION` statement

Example 3-20 Setting NLS_ISO_CURRENCY

This example assumes that you are connected as `oe/oe` in the sample schema.

To specify the ISO currency symbol for France, set `NLS_ISO_CURRENCY` as follows:

    SQL> ALTER SESSION SET NLS_ISO_CURRENCY = FRANCE;

Enter a `SELECT` statement:

    SQL> SELECT TO_CHAR(order_total, 'C099G999D99') "TOTAL" FROM orders
         WHERE customer_id = 146;

You should see results similar to the following output:

    TOTAL
    ------------------
    EUR017,848.20
    EUR027,455.30
    EUR029,249.10
    EUR013,824.00
    EUR000,086.00

#### 3.9.4 NLS_DUAL_CURRENCY

| Property        | Description                                                                          |
|:----------------|:-------------------------------------------------------------------------------------|
| Parameter type  | String                                                                               |
| Parameter scope | Initialization parameter, environmental variable, `ALTER SESSION`, and SQL functions |
| Default value   | Derived from `NLS_TERRITORY`                                                         |
| Range of values | Any valid symbol                                                                     |

Use `NLS_DUAL_CURRENCY` to override the default dual currency symbol defined implicitly by `NLS_TERRITORY`.

`NLS_DUAL_CURRENCY` was introduced to support the euro currency symbol during the euro transition period. See [Table A-8](appendix-A-locale-data.md) for the character sets that support the euro symbol.

#### 3.9.5 Oracle Database Support for the Euro

Twelve members of the European Monetary Union (EMU) have adopted the euro as their currency. Setting `NLS_TERRITORY` to correspond to a country in the EMU (Austria, Belgium, Finland, France, Germany, Greece, Ireland, Italy, Luxembourg, the Netherlands, Portugal, and Spain) results in the default values for `NLS_CURRENCY` and `NLS_DUAL_CURRENCY` being set to `EUR`.

During the transition period (1999 through 2001), Oracle Database support for the euro was provided in Oracle Database 8i and later as follows:

- `NLS_CURRENCY` was defined as the primary currency of the country

- `NLS_ISO_CURRENCY` was defined as the ISO currency code of a given territory

- `NLS_DUAL_CURRENCY` was defined as the secondary currency symbol (usually the euro) for a given territory

Beginning with Oracle Database 9i Release 2, the value of `NLS_ISO_CURRENCY` results in the ISO currency symbol being set to `EUR` for EMU member countries who use the euro. For example, suppose `NLS_ISO_CURRENCY` is set to `FRANCE`. Enter the following `SELECT` statement:

    SQL> SELECT TO_CHAR(order_total, 'C099G999D99') "TOTAL" FROM orders
         WHERE customer_id=116;

You should see results similar to the following output:

    TOTAL
    -------
    EUR006,394.80
    EUR011,097.40
    EUR014,685.80
    EUR000,129.00

Customers who must retain their obsolete local currency symbol can override the default for `NLS_DUAL_CURRENCY` or `NLS_CURRENCY` by defining them as parameters in the initialization file on the server and as environment variables on the client.

**Note:**

`NLS_LANG` must also be set on the client for `NLS_CURRENCY` or `NLS_DUAL_CURRENCY` to take effect.

It is not possible to override the ISO currency symbol that results from the value of `NLS_ISO_CURRENCY`.

#### 3.9.6 NLS_MONETARY_CHARACTERS

| Property        | Description                  |
|:----------------|:-----------------------------|
| Parameter type  | String                       |
| Parameter scope | Environment variable         |
| Default value   | Derived from `NLS_TERRITORY` |
| Range of values | Any valid character          |

`NLS_MONETARY_CHARACTERS` specifies the character that separates groups of numbers in monetary expressions. For example, when the territory is America, the thousands separator is a comma, and the decimal separator is a period.

#### 3.9.7 NLS_CREDIT

| Property        | Description                                         |
|:----------------|:----------------------------------------------------|
| Parameter type  | String                                              |
| Parameter scope | Environment variable                                |
| Default value   | Derived from `NLS_TERRITORY`                        |
| Range of values | Any string, maximum of 9 bytes (not including null) |

`NLS_CREDIT` sets the symbol that displays a credit in financial reports. The default value of this parameter is determined by `NLS_TERRITORY`. For example, a space is a valid value of `NLS_CREDIT`.

This parameter can be specified only in the client environment.

It can be retrieved through the `OCINlsGetInfo()` function.

#### 3.9.8 NLS_DEBIT

| Property        | Description                                         |
|:----------------|:----------------------------------------------------|
| Parameter type  | String                                              |
| Parameter scope | Environment variable                                |
| Default value   | Derived from `NLS_TERRITORY`                        |
| Range of values | Any string, maximum or 9 bytes (not including null) |

`NLS_DEBIT` sets the symbol that displays a debit in financial reports. The default value of this parameter is determined by `NLS_TERRITORY`. For example, a minus sign (-) is a valid value of `NLS_DEBIT`.

This parameter can be specified only in the client environment.

It can be retrieved through the `OCINlsGetInfo()` function.

### 3.10 Linguistic Sort Parameters

You can choose how to sort data by using linguistic sort parameters.

This section includes the following topics:

- NLS_SORT

- NLS_COMP

**See Also:**

"[Linguistic Sorting and Matching](linguistic-sorting-and-matching.md)"

#### 3.10.1 NLS_SORT

| Property        | Description                                                                        |
|:----------------|:-----------------------------------------------------------------------------------|
| Parameter type  | String                                                                             |
| Parameter scope | Initialization parameter, environment variable, `ALTER SESSION`, and SQL functions |
| Default value   | Derived from `NLS_LANGUAGE`                                                        |
| Range of values | `BINARY` or any valid linguistic collation name                                    |

`NLS_SORT` specifies a set of matching and comparison rules for character data. It overrides the default value that is derived from `NLS_LANGUAGE`.

`NLS_SORT` contains either of the following values:

    NLS_SORT = BINARY | collation_name

`BINARY` specifies the binary collation. `collation_``name` specifies a linguistic named collation.

Example 3-21 Setting NLS_SORT

To specify the German linguistic collation, set `NLS_SORT` as follows:

    NLS_SORT = German

**Note:**

When the `NLS_SORT` parameter is set to `BINARY`, the optimizer can, in some cases, satisfy the `ORDER` `BY` clause without doing a sort operation by choosing an index scan.

When `NLS_SORT` is set to a linguistic collation, a sort operation is needed to satisfy the `ORDER` `BY` clause, if there is no linguistic index for the linguistic collation specified by `NLS_SORT`.

If a linguistic index exists for the linguistic collation specified by `NLS_SORT`, then the optimizer can, in some cases, satisfy the `ORDER` `BY` clause without doing a sort operation by choosing an index scan.

You can alter the default value of `NLS_SORT` by:

- Changing its value in the initialization parameter file and then restarting the instance

- Using an `ALTER` `SESSION` statement

**See Also:**

- "[Linguistic Sorting and Matching](linguistic-sorting-and-matching.md)"

- [Oracle Database SQL Language Reference ](../sqlrf/ALTER-SESSION.md)for more information about the `ALTER SESSION` statement

- "[Linguistic Sorts](appendix-A-locale-data.md)" for a list of linguistic collation names

#### 3.10.2 NLS_COMP

| Property        | Description                                                         |
|:----------------|:--------------------------------------------------------------------|
| Parameter type  | String                                                              |
| Parameter scope | Initialization parameter, environment variable, and `ALTER SESSION` |
| Default value   | `BINARY`                                                            |
| Range of values | `BINARY` , `LINGUISTIC`, or `ANSI`                                  |

The value of `NLS_COMP` affects the comparison behavior of SQL operations whose determined collation is `USING_NLS_COMP`.

**See Also:**

- "[Using Linguistic Collation](linguistic-sorting-and-matching.md)"

- "[Using Linguistic Indexes](linguistic-sorting-and-matching.md)"

- "[Performing Linguistic Comparisons](linguistic-sorting-and-matching.md)"

- "[About Data-Bound Collation](linguistic-sorting-and-matching.md)" for more information about the pseudo-collation `USING_NLS_COMP`

### 3.11 Character Set Conversion Parameter

This section includes the following topic:

- NLS_NCHAR_CONV_EXCP

#### 3.11.1 NLS_NCHAR_CONV_EXCP

| Property        | Description                                  |
|:----------------|:---------------------------------------------|
| Parameter type  | String                                       |
| Parameter scope | Initialization parameter and `ALTER SESSION` |
| Default value   | `FALSE`                                      |
| Range of values | `TRUE` or `FALSE`                            |

`NLS_NCHAR_CONV_EXCP` determines whether an error is reported when there is data loss during an implicit or explicit character type conversion between `NCHAR`/`NVARCHAR` data and `CHAR`/`VARCHAR2` data. The default value results in no error being reported.

**See Also:**

"[Character Set Migration](character-set-migration.md)" for more information about data loss during character set conversion

### 3.12 Length Semantics

This section includes the following topic:

- NLS_LENGTH_SEMANTICS

#### 3.12.1 NLS_LENGTH_SEMANTICS

| Property        | Description                                                         |
|:----------------|:--------------------------------------------------------------------|
| Parameter type  | String                                                              |
| Parameter scope | Environment variable, initialization parameter, and `ALTER SESSION` |
| Default value   | `BYTE`                                                              |
| Range of values | `BYTE` or `CHAR`                                                    |

By default, the character data types `CHAR` and `VARCHAR2` are specified in bytes, not characters. Hence, the specification `CHAR(20)` in a table definition allows 20 bytes for storing character data.

This works well if the database character set uses a single-byte character encoding scheme because the number of characters is the same as the number of bytes. If the database character set uses a multibyte character encoding scheme, then the number of bytes no longer equals the number of characters because a character can consist of one or more bytes. Thus, column widths must be chosen with care to allow for the maximum possible number of bytes for a given number of characters. You can overcome this problem by switching to character semantics when defining the column size.

`NLS_LENGTH_SEMANTICS` enables you to create `CHAR`, `VARCHAR2`, and `LONG` columns using either byte or character length semantics. `NCHAR`, `NVARCHAR2`, `CLOB`, and `NCLOB` columns are always character-based. Existing columns are not affected.

You may be required to use byte semantics in order to maintain compatibility with existing applications.

`NLS_LENGTH_SEMANTICS` does not apply to tables created in the `SYS` schema. The data dictionary always uses byte semantics. Tables owned by `SYS` always use byte semantics if the length qualifier `BYTE` or `CHAR` is not specified in the table creation DDL.

Note that if the `NLS_LENGTH_SEMANTICS` environment variable is not set on the client, then the client session defaults to the value for `NLS_LENGTH_SEMANTICS` on the database server. This enables all client sessions on the network to have the same `NLS_LENGTH_SEMANTICS` behavior. Setting the environment variable on an individual client enables the server initialization parameter to be overridden for that client.

Note that if the `NLS_LENGTH_SEMANTICS` environment variable is not set on the client or the client connects through the Oracle JDBC Thin driver, then the client session defaults to the value for the `NLS_LENGTH_SEMANTICS` initialization parameter of the instance to which the client connects. For compatibility reasons, Oracle recommends that this parameter be left undefined or set to `BYTE`.

**Note:**

Oracle strongly recommends that you do NOT set the `NLS_LENGTH_SEMANTICS` parameter to `CHAR` in the instance or server parameter file. This may cause many existing installation scripts to unexpectedly create columns with character length semantics, resulting in run-time errors, including buffer overflows.

**See Also:**

"[Length Semantics](choosing-character-set.md)"
