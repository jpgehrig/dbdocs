## 13 Oracle Data Redaction Features and Capabilities

Oracle Data Redaction provides a variety of ways to redact different types of data.

- Full Data Redaction to Redact All Data
  Full data redaction redacts the entire contents of the specified table or view column.
- Partial Data Redaction to Redact Sections of Data
  In partial data redaction, you redact portions of the displayed output.
- Regular Expressions to Redact Patterns of Data
  Regular expressions redact specific data within a column data value, based on a pattern search.
- Redaction Using Null Values
  You can create an Oracle Data Redaction policy that redacts column data by replacing it with null values.
- Random Data Redaction to Generate Random Values
  In random data redaction, the entire value is redacted by replacing it with a random value.
- Comparison of Full, Partial, and Random Redaction Based on Data Types
  The full, partial, and random data redaction styles affect the Oracle built-in, ANSI, user-defined, and Oracle supplied types in different ways.
- No Redaction for Testing Purposes
  You can create a Data Redaction policy that does not perform redaction.
- Central Management of Named Data Redaction Policy Expressions
  You can create a library of named policy expressions that can be used in the columns of multiple tables and views.

**Parent topic:** [Using Oracle Data Redaction](asopart2.md)

### 13.1 Full Data Redaction to Redact All Data

Full data redaction redacts the entire contents of the specified table or view column.

By default the output is displayed as follows:

- Character data types: The output text is a single space.

- Number data types: The output text is a zero (`0`).

- Date-time data types: The output text is set to the first day of January, 2001, which appears as `01-JAN-01`.

Full redaction is the default and is used whenever a Data Redaction policy specifies the column but omits the `function_type` parameter setting. When you run the `DBMS_REDACT.ADD_POLICY` procedure, to set the `function_type` parameter setting for full redaction, you enter the following setting:

    function_type    => DBMS_REDACT.FULL

You can use the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure to change the full redaction output to different values.

**Related Topics**

- [Syntax for Creating a Full Redaction Policy](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.2 Partial Data Redaction to Redact Sections of Data

In partial data redaction, you redact portions of the displayed output.

You can set the position within the [actual data](glossary.md) at which to begin the redaction, the number of characters to redact starting from that position, and the redaction character to use. This type of redaction is useful for situations where you want it to be obvious to the person viewing the data that it was redacted in some way. Typically, you use this type of redaction for credit cards or ID numbers.

Be aware that partial data redaction requires that your data width remain fixed. If you want to redact columns containing string values of variable length, then you must use regular expressions.

To specify partial redaction, you must set the `DBMS_REDACT.ADD_POLICY` procedure `function_type` parameter to `DBMS_REDACT.PARTIAL` and use the `function_parameters` parameter to define the partial redaction behavior.

The displayed output for partial data redaction can be as follows:

- Character data types: When partially redacted, a Social Security number (represented as a hyphenated string within a character data type) with value `987-65-4320` could be redacted so that it is displayed as shown in the following examples. The code on the right specifies how to redact the character data: it specifies the expected input format of the actual data, the format to use for the display of the redacted output, the start position at which to begin the redaction, the character to use for the redaction, and how many characters to redact. The first example uses a predefined format (in previous releases called a shortcut) for character data type Social Security numbers, and the second example replaces the first five numbers with an asterisk (`*`) while preserving the hyphens (`-`) in between the numbers.

      XXX-XX-4320    function_parameters => DBMS_REDACT.REDACT_US_SSN_F5,

      ***-**-4320    function_parameters => 'VVVFVVFVVVV,VVV-VV-VVVV,*,1,5',

- Number data types: The partially redacted `NUMBER` data type Social Security number `987654328` could appear as follows. Both redact the first five digits. The first example uses a predefined format that is designed for Social Security numbers in the `NUMBER` data type, and the second replaces the first five numbers with the number `9`, starting from the first digit.

      XXXXX4328    function_parameters => DBMS_REDACT.REDACT_NUM_US_SSN_F5,

      999994328    function_parameters => '9,1,5',

- Date-time data types: Partially redacted datetime values can appear simply as different dates. For example, the date `29-AUG-11 10.20.50.000000 AM` could appear as follows. In the first example, the day of the month is redacted to `02` (using the setting `d02`) and in the second example, the month is redacted to `DEC` (using `m12`). The uppercase values show the actual month (`M`), year (`Y`), hour (`H`), minute (`M`), and second (`S`).

      02-AUG-11 10.20.50.000000 AM   function_parameters  =>  'Md02YHMS',

      29-DEC-11 10.20.50.000000 AM   function_parameters  =>  'm12DYHMS',

**Related Topics**

- Regular Expressions to Redact Patterns of Data
- [Syntax for Creating a Partial Redaction Policy](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.3 Regular Expressions to Redact Patterns of Data

Regular expressions redact specific data within a column data value, based on a pattern search.

For example, you can redact the user name of email addresses, so that only the domain shows (for example, replacing `hpreston` in the email address `hpreston@example.com` with `[redacted]` so that it appears as `[redacted]@example.com`). To perform the redaction, set the `DBMS_REDACT.ADD_POLICY` procedure `function_type` parameter to either `DBMS_REDACT.REGEXP` or `DBMS_REDACT.REGEXP_WIDTH`, and then use the following parameters to build the regular expression:

- A string search pattern (that is, the values to search for), such as:

      regexp_pattern         => '(.+)@(.+\.[A-Za-z]{2,4})'

  This setting looks for a pattern of the following form:

      one_or_more_characters@one_or_more_characters.2-4_characters_in_range_A-Z_or_a-z

- A replacement string, which replaces the value matched by the `regexp_pattern` setting. The replacement string can include back references to sub-expressions of the main regular expression pattern. The following example replaces the data before the `@` symbol (from the `regexp_pattern` setting) with the text `[redacted]`. The `\2` setting refers to the second match group, which is `(.+\.[A-Za-z]{2,4})` from the `regexp_pattern` setting.

      regexp_replace_string  => '[redacted]@\2'

- The starting position for the string search string, such as the first character of the data, such as:

      regexp_position        => DBMS_REDACT.RE_BEGINNING

- The kind of search and replace operation to perform, such as the first occurrence, every fifth occurrence, or all of the occurrences, such as:

      regexp_occurrence      => DBMS_REDACT.RE_ALL

- The default matching behavior for the search and replace operation, such as whether the search is case-sensitive (`i` sets it to be not case-sensitive):

      regexp_match_parameter => 'i

In addition to the default parameters, you can use a set of predefined formats that enable you to use commonly used regular expressions for telephone numbers, email addresses, and credit card numbers.

**Related Topics**

- [Syntax for Creating a Regular Expression-Based Redaction Policy](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.4 Redaction Using Null Values

You can create an Oracle Data Redaction policy that redacts column data by replacing it with null values.

This feature enables you to use the `DBMS_REDACT.NULLIFY` function hide all of the sensitive data in a table or view column and replace it with null values. You can set this function by using the `function_type` parameter of the `DBMS_REDACT.ADD_POLICY` or `DBMS_REDACT.ALTER_POLICY` procedure.

For example:

    function_type         => DBMS_REDACT.NULLIFY

**Related Topics**

- [Creating a DBMS_REDACT.NULLIFY Redaction Policy](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.5 Random Data Redaction to Generate Random Values

In random data redaction, the entire value is redacted by replacing it with a random value.

The redacted values displayed in the result set of the query change randomly each time application users run the query.

This type of redaction is useful in cases where you do not want it to be obvious that the data was redacted. It works especially well for number and datetime data types, where it is difficult to distinguish between random and real data.

The displayed output for random values changes based on the data type of the redacted column, as follows:

- Character data types: The random output is a mixture of characters (for example, `HTU[G{\pjkEWcK`). It behaves differently for the `CHAR` and `VARCHAR2` data types, as follows:

  - CHAR data type: The redacted output is always in the same character set as the character set of the column. The byte length of the redacted output is always the same as the column definition length (that is, the column length that was provided at the time of table creation). For example, if the column is `CHAR(20)`, then a string of 20 random characters is provided in the redacted output of the user's query.

  - VARCHAR2 data type: For random redaction of a `VARCHAR` data type, the redacted output is always in the same character set as the character set of the column. The length of the redacted output is limited based on the length of the [actual data](glossary.md) in the column. No characters in excess of the length of the actual data are displayed. For example, if the column is `VARCHAR2(20)` and the row being redacted contains actual data with a length of 12, then a string of 12 random characters (not 20) is provided in the redacted output of the user's query for that row.

- Number data types: Each actual number value is redacted by replacing it with a random, non-negative number modulo the absolute value of the actual data. This redaction results in random numbers that do not exceed the precision of the actual data. For example, the number `987654321` can be redacted by replacing it with any of the numbers `12345678`, `13579`, `0`, or `987654320`, but not by replacing it with any of the numbers `987654321`, `99987654321`, or `-1`. The number `-123` could be redacted by replacing it with the numbers `122`, `0`, or `83`, but not by replacing it with any of the numbers `123`, `1123`, or `-2`.

  The only exception to the above is when the actual value is an integer between -1 and 9. In this case, the actual data is redacted by replacing it with a random, non-negative integer modulo ten (10).

- Date-time data types: When values of the date data type are redacted using random Data Redaction, Oracle Database displays them with random dates that are always different from those of the actual data.

The setting for using random redaction is as follows:

    function_type    => DBMS_REDACT.RANDOM

**Related Topics**

- [Syntax for Creating a Random Redaction Policy](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.6 Comparison of Full, Partial, and Random Redaction Based on Data Types

The full, partial, and random data redaction styles affect the Oracle built-in, ANSI, user-defined, and Oracle supplied types in different ways.

- Oracle Built-in Data Types Redaction Capabilities
  Oracle Data Redaction handles the Oracle built-in data types depending on the type of Data Redaction policies that are used.
- ANSI Data Types Redaction Capabilities
  Oracle Data Redaction converts ANSI data types in specific ways, depending on the type of redaction that the Data Redaction policy has.
- Built-in and ANSI Data Types Full Redaction Capabilities
  For full redaction, the default redacted value depends on whether the data type is Oracle built-in or ANSI.
- User-Defined Data Types or Oracle Supplied Types Redaction Capabilities
  Several data types or types are not supported by Oracle Data Redaction.

**Parent topic:** Oracle Data Redaction Features and Capabilities

#### 13.6.1 Oracle Built-in Data Types Redaction Capabilities

Oracle Data Redaction handles the Oracle built-in data types depending on the type of Data Redaction policies that are used.

Table 13-1 describes the Oracle Data Redaction support for Oracle built-in data types.

Table 13-1 Redaction Support for Oracle Built-in Data Types

| Column Data Type           | Full | Partial | Regexp | Random |
|:---------------------------|:-----|:--------|:-------|:-------|
| Character<sup>Foot 1</sup> | Yes  | Yes     | Yes    | Yes    |
| Number<sup>Foot 2</sup>    | Yes  | Yes     | No     | Yes    |
| Raw<sup>Foot 3</sup>       | No   | No      | No     | No     |
| Date-time<sup>Foot 4</sup> | Yes  | Yes     | No     | Yes    |
| Interval<sup>Foot 5</sup>  | No   | No      | No     | No     |
| `BFILE`                    | No   | No      | No     | No     |
| `BLOB`                     | Yes  | No      | No     | No     |
| `CLOB`                     | Yes  | No      | Yes    | No     |
| `NCLOB`                    | Yes  | No      | Yes    | No     |
| `ROWID`                    | No   | No      | No     | No     |
| `UROWID`                   | No   | No      | No     | No     |

<sup>Footnote 1</sup>

Includes `CHAR`, `VARCHAR2` (including long `VARCHAR2`, for example, `VARCHAR2(20000)`), `NCHAR`, `NVARCHAR2`

<sup>Footnote 2</sup>

Includes `NUMBER`, `FLOAT`, `BINARY_FLOAT`, `BINARY_DOUBLE`

<sup>Footnote 3</sup>

Includes `LONG` `RAW`, `RAW`

<sup>Footnote 4</sup>

Includes `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, `TIMESTAMP WITH LOCAL TIME ZONE`

<sup>Footnote 5</sup>

Includes `INTERVAL YEAR TO MONTH`, `INTERVAL DAY TO SECOND`

**Parent topic:** Comparison of Full, Partial, and Random Redaction Based on Data Types

#### 13.6.2 ANSI Data Types Redaction Capabilities

Oracle Data Redaction converts ANSI data types in specific ways, depending on the type of redaction that the Data Redaction policy has.

Table 13-2 compares how the full, partial, and random redaction styles work for ANSI data types, with regard to how they are converted and their support status.

Table 13-2 Redaction Support for the ANSI Data Types

| Data Type                                                                             | How Converted                   | Full Redaction | Partial Redaction | Regexp | NULL Redaction | Random Redaction |
|:--------------------------------------------------------------------------------------|:--------------------------------|:---------------|:------------------|:-------|:---------------|:-----------------|
| `CHARACTER(n)`,<br>`CHAR(n)`                                                          | Converted to `CHAR(``n``)`      | Yes            | Yes               | Yes    | Yes            | Yes              |
| `CHARACTER VARYING(n)`,<br>`CHAR VARYING(n)`                                          | Converted to `VARCHAR2(``n``)`  | Yes            | Yes               | Yes    | Yes            | Yes              |
| `NATIONAL CHARACTER(n)`,<br>`NATIONAL CHAR(n)`,<br>`NCHAR(n)`                         | Converted to `NCHAR(``n``)`     | Yes            | Yes               | Yes    | Yes            | Yes              |
| `NATIONAL CHARACTER VARYING(n)`,<br>`NATIONAL CHAR VARYING(n)`,<br>`NCHAR VARYING(n)` | Converted to `NVARCHAR2(``n``)` | Yes            | Yes               | Yes    | Yes            | Yes              |
| `NUMERIC`\[(`p``,``s`)\]<br>`DECIMAL`\[(`p``,``s`)\]                                  | Converted to `NUMBER(``p,s``)`  | Yes            | Yes               | Yes    | Yes            | Yes              |
| `INTEGER`,<br>`INT`,<br>`SMALLINT`                                                    | Converted to `NUMBER(``38)`     | Yes            | Yes               | Yes    | Yes            | Yes              |
| `FLOAT`,<br>`DOUBLE PRECISION`                                                        | Converted to `FLOAT(``126)`     | Yes            | Yes               | Yes    | Yes            | Yes              |
| `REAL`                                                                                | Converted to `FLOAT(``63)`      | Yes            | Yes               | Yes    | Yes            | Yes              |
| `GRAPHIC`,<br>`LONG VARGRAPHIC`,<br>`VARGRAPHIC`,<br>`TIME`                           | No conversion                   | No             | No                | No     | No             | No               |

**Parent topic:** Comparison of Full, Partial, and Random Redaction Based on Data Types

#### 13.6.3 Built-in and ANSI Data Types Full Redaction Capabilities

For full redaction, the default redacted value depends on whether the data type is Oracle built-in or ANSI.

ANSI Data Types Redaction Capabilities shows the default settings for both Oracle built-in and ANSI data type columns that use full redaction.

Table 13-3 Default Settings and Categories for Columns That Use Full Redaction

| Data Type                                                                             | Default Redacted Value                                           | Data Type Category |
|:--------------------------------------------------------------------------------------|:-----------------------------------------------------------------|:-------------------|
| `CHARACTER`                                                                           | Single space (`“ “`)                                             | Oracle built-in    |
| `CHARACTER(n)`,<br>`CHAR(n)`                                                          | Single space (`“ “`)                                             | ANSI               |
| `CHARACTER VARYING(n)`,<br>`CHAR VARYING(n)`                                          | Single space (`“ “`)                                             | ANSI               |
| `NATIONAL CHARACTER(n)`,<br>`NATIONAL CHAR(n)`,<br>`NCHAR(n)`                         | Single space (`“ “`)                                             | ANSI               |
| `NATIONAL CHARACTER VARYING(n)`,<br>`NATIONAL CHAR VARYING(n)`,<br>`NCHAR VARYING(n)` | Single space (`“ “`)                                             | ANSI               |
| `NUMBER`                                                                              | Zero (`0`)                                                       | Oracle built-in    |
| `NUMERIC`\[(`p``,``s`)\]<br>`DECIMAL`\[(`p``,``s`)\]                                  | Zero (`0`)                                                       | Oracle built-in    |
| `INTEGER`,<br>`INT`,<br>`SMALLINT`                                                    | Zero (`0`)                                                       | ANSI               |
| `FLOAT`,<br>`DOUBLE PRECISION`                                                        | Zero (`0`)                                                       | ANSI               |
| `REAL`                                                                                | Zero (`0`)                                                       | ANSI               |
| `DATE-TIME`                                                                           | `01–01–01` or `01–01–01 01:00:00`                                | Oracle built-in    |
| `BLOB`                                                                                | Oracle’s raw representation of `[redacted]`<br><sup>Foot 6</sup> | Oracle built-in    |
| `CLOB`                                                                                | `[redacted]`                                                     | Oracle built-in    |
| `NCLOB`                                                                               | `[redacted]`                                                     | Oracle built-in    |

<sup>Footnote 6</sup>

If you have changed the character set, then you may need to invoke the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure to set the value to the raw representation in the new character set, as follows:

    DECLARE
     new_red_blob BLOB;
    BEGIN
     DBMS_LOB.CREATETEMPORARY(new_red_blob, TRUE);
     DBMS_LOB.WRITE(new_red_blob, 10, 1, UTL_RAW.CAST_TO_RAW('[redacted]'));
     dbms_redact.update_full_redaction_values(
      blob_val      => new_red_blob);
    DBMS_LOB.FREETEMPORARY(new_red_blob);
    END;
    /

After you run this procedure, restart the database.

See also [Altering the Default Full Data Redaction Value](configuring-oracle-data-redaction-policies.md) for more information about using the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure.

**Parent topic:** Comparison of Full, Partial, and Random Redaction Based on Data Types

#### 13.6.4 User-Defined Data Types or Oracle Supplied Types Redaction Capabilities

Several data types or types are not supported by Oracle Data Redaction.

Table 13-4 compares how the full, partial, regular expression, and random redaction styles work for user-defined and Oracle-supplied types.

Table 13-4 Redaction Support for the User-Defined Data Types or Oracle-Supplied Types

| Data Type or Type                                                 | Full Redaction | Partial Redaction | Regexp | NULL Redaction | Random Redaction |
|:------------------------------------------------------------------|:---------------|:------------------|:-------|:---------------|:-----------------|
| User-defined data types                                           | No             | No                | No     | No             | No               |
| Oracle supplied types: Any types, XML types, Oracle Spatial types | No             | No                | No     | No             | No               |

**Parent topic:** Comparison of Full, Partial, and Random Redaction Based on Data Types

### 13.7 No Redaction for Testing Purposes

You can create a Data Redaction policy that does not perform redaction.

This is useful for cases in which you have a redacted base table, yet you want a specific application user to have a view that always shows the [actual data](glossary.md). You can create a new view of the redacted table and then define a Data Redaction policy for this view. The policy still exists on the base table, but no redaction is performed when the application queries using the view as long as the `DBMS_REDACT.NONE` `function_type` setting was used to create a policy on the view.

**Parent topic:** Oracle Data Redaction Features and Capabilities

### 13.8 Central Management of Named Data Redaction Policy Expressions

You can create a library of named policy expressions that can be used in the columns of multiple tables and views.

By having named policy expressions, you can centrally manage all of the policy expressions within a database.

When you modify the policy expression, the change is reflected in all table columns that use the expression. The policy expression takes precedence over the `expression` setting in the Data Redaction policy. To create the policy expression, you must use the `DBMS_REDACT.CREATE_POLICY_EXPRESSION` procedure, and to apply the policy expression to a column, you use `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL`. This feature provides flexibility to redact different columns in a table or view, based on different runtime conditions.

For example, consider a use case that involves a customer care application. A customer calls the customer care center to request a return on a recent purchase. A level 1 support representative of the call center must first verify the order ID, customer name, and customer address before initiating the return. During the process, there is no need for the level 1 support representative to view the customer’s credit card number. So, the credit card column is redacted when the support representative queries the customer details in the call center application. When the return is initiated, a sales representative from the return department may need to view the credit card number to process the return. However, there is no need for the sales representative to view the expiration date of the credit card. So, when the sales representative queries the customer details in the same application, the credit card number is visible but the expiration date is redacted.

In this use case, different columns in the customer details table must be redacted in different ways, based on who the logged in user is. Oracle Data Redaction simplifies the implementation of this use case by using named Data Redaction policy expressions. This type of policy expression enables you to define and associate different policy expressions on different columns in the same table or view. Moreover, you can centrally manage named policy expressions within a database. Any updates that you make to a named policy expression are immediately propagated to all of the associated table or view columns.

**Related Topics**

- [Creating and Managing Multiple Named Policy Expressions](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction Features and Capabilities
