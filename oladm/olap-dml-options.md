This chapter contains the following topics:

- About Options

- Options: Alphabetical Listing

- Options by Category

- One topic for each of the OLAP DML options, arranged alphabetically beginning with ALLOCERRLOGFORMAT.

For other OLAP DML reference topics, see [OLAP DML Properties](olap-dml-properties.md), [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md), [OLAP DML Commands: A-G](olap-dml-commands-a-g.md), and [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

### 5.1 About Options

An OLAP DML option is a special type of analytic workspace object that specifies the characteristic of some aspect of how Oracle OLAP calculates or formats data or what Oracle OLAP operations are activated. Some options are read-only, while others are read/write options for which you can specify values. Read/write options have default values.

You can use the [SET](olap-dml-commands-h-z.md) (=) command to retrieve the value of an option into a predefined variable and to specify a new value for a read/write option. Use the [SHOW](olap-dml-commands-h-z.md) command to display the value of an option.

### 5.2 Options: Alphabetical Listing

#### A

- ALLOCERRLOGFORMAT
- ALLOCERRLOGHEADER
- AWWAITTIME

#### B

- BADLINE
- BMARGIN

#### C

- CALENDARWEEK
- COLWIDTH
- COMMAS
- COMPILEMESSAGE
- COMPILEWARN

#### D

- DATEFORMAT
- DATEORDER
- DAYABBRLEN
- DAYNAMES
- DECIMALCHAR
- DECIMALOVERFLOW
- DECIMALS
- DEFAULTAWSEGSIZE
- DIVIDEBYZERO
- DSECONDS

#### E

- ECHOPROMPT
- EIFBYTES
- EIFEXTENSIONPATH
- EIFNAMES
- EIFSHORTNAMES
- EIFTYPES
- EIFUPDBYTES
- EIFVERSION
- ERRNAMES
- ERRORNAME
- ERRORTEXT
- ESCAPEBASE
- EXPTRACE

#### I

- INF_STOP_ON_ERROR

#### L

- LCOLWIDTH
- LIKECASE
- LIKEESCAPE
- LIKENL
- LIMIT.SORTREL
- LIMITSTRICT
- LINENUM
- LINESLEFT
- LOCK_LANGUAGE_DIMS
- LSIZE

#### M

- MAXFETCH
- MODDAMP
- MODERROR
- MODGAMMA
- MODINPUTORDER
- MODMAXITERS
- MODOVERFLOW
- MODSIMULTYPE
- MODTOLERANCE
- MODTRACE
- MONTHABBRLEN
- MONTHNAMES
- MULTIPATHHIER

#### N

- NASKIP
- NASKIP2
- NASPELL
- NLS_CALENDAR
- NLS_CURRENCY
- NLS_DATE_FORMAT
- NLS_DATE_LANGUAGE
- NLS_DUAL_CURRENCY
- NLS_ISO_CURRENCY
- NLS_LANG
- NLS_LANGUAGE
- NLS_NUMERIC_CHARACTERS
- NLS_SORT
- NLS_TERRITORY
- NOSPELL

#### O

- OKFORLIMIT
- OKNULLSTATUS
- OUTFILEUNIT

#### P

- PAGENUM
- PAGEPRG
- PAGESIZE
- PAGING
- PARENS
- PERMITERROR
- PERMITREADERROR
- PRGTRACE

#### R

- RANDOM.SEED.1 and RANDOM.SEED.2
- RECURSIVE
- ROLE
- ROOTOFNEGATIVE

#### S

- SECONDS
- SESSCACHE
- SESSION_NLS_LANGUAGE
- SPARSEINDEX
- SQLBLOCKMAX
- SQLCODE
- SQLERRM
- SQLMESSAGES
- STATIC_SESSION_LANGUAGE

#### T

- THIS_AW
- THOUSANDSCHAR
- TMARGIN
- TRACEFILEUNIT
- TRIGGERMAXDEPTH
- TRIGGERSTOREOK

#### U

- USERID
- USETRIGGERS

#### V

- VARCACHE

#### W

- WEEKDAYSNEWYEAR
- WRAPERRORS

#### Y

- YESSPELL
- YRABSTART

#### Z

- ZEROROW
- ZSPELL

### 5.3 Options by Category

- Analytic Workspace Options
- Globalization Support
- Multi-Language Support Options
- Aggregation Options
- Allocation Options
- Model Options
- Compilation Options
- Error Options
- Debugging Options
- SQL Embed Options
- File Reading and Writing Options
- EIF Options
- Report Options
- NA Values Options
- Date-only Data Type Options
- Datetime Options
- Numeric Options
- RANK Function Monitoring Options

#### Analytic Workspace Options

- AWWAITTIME
- DEFAULTAWSEGSIZE

#### Globalization Support

- NLS_CALENDAR
- NLS_CURRENCY
- NLS_DATE_FORMAT
- NLS_DATE_LANGUAGE
- NLS_DUAL_CURRENCY
- NLS_ISO_CURRENCY
- NLS_LANG
- NLS_LANGUAGE
- NLS_NUMERIC_CHARACTERS
- NLS_SORT
- NLS_TERRITORY

#### Multi-Language Support Options

- LOCK_LANGUAGE_DIMS
- NLS_DATE_LANGUAGE
- NLS_LANG
- NLS_LANGUAGE
- SESSION_NLS_LANGUAGE
- STATIC_SESSION_LANGUAGE

#### Aggregation Options

- MULTIPATHHIER
- SESSCACHE
- VARCACHE

#### Allocation Options

- ALLOCERRLOGFORMAT
- ALLOCERRLOGHEADER

#### Model Options

- MODDAMP
- MODERROR
- MODGAMMA
- MODINPUTORDER
- MODMAXITERS
- MODOVERFLOW
- MODSIMULTYPE
- MODTOLERANCE
- MODTRACE

#### Compilation Options

- COMPILEMESSAGE
- COMPILEWARN
- THIS_AW

#### Error Options

- BADLINE
- ERRNAMES
- ERRORNAME
- ERRORTEXT
- INF_STOP_ON_ERROR
- MODERROR
- PERMITERROR
- PERMITREADERROR
- SQLERRM
- SQLMESSAGES
- WRAPERRORS

#### Debugging Options

- EXPTRACE
- MODTRACE
- PRGTRACE

#### SQL Embed Options

- SQLBLOCKMAX
- SQLCODE
- SQLERRM
- SQLMESSAGES

#### File Reading and Writing Options

- ECHOPROMPT
- ESCAPEBASE
- INF_STOP_ON_ERROR
- OUTFILEUNIT

#### EIF Options

- EIFBYTES
- EIFEXTENSIONPATH
- EIFNAMES
- EIFSHORTNAMES
- EIFTYPES
- EIFUPDBYTES
- EIFVERSION

#### Report Options

- BMARGIN
- COLWIDTH
- COMMAS
- DECIMALCHAR
- DECIMALS
- LCOLWIDTH
- LINENUM
- LINESLEFT
- LSIZE
- NASPELL
- NOSPELL
- PAGENUM
- PAGEPRG
- PAGESIZE
- PAGING
- PARENS
- THOUSANDSCHAR
- TMARGIN
- YESSPELL
- ZEROROW
- ZSPELL

#### NA Values Options

- LIMITSTRICT
- NASKIP
- NASKIP2
- NASPELL
- RECURSIVE
- TRIGGERMAXDEPTH
- TRIGGERSTOREOK

#### Date-only Data Type Options

- CALENDARWEEK
- DATEFORMAT
- DATEORDER
- DAYABBRLEN
- DAYNAMES
- DSECONDS
- MONTHABBRLEN
- MONTHNAMES
- WEEKDAYSNEWYEAR
- YRABSTART

#### Datetime Options

- CALENDARWEEK
- DSECONDS
- SECONDS

#### Numeric Options

- DECIMALOVERFLOW
- DIVIDEBYZERO
- RANDOM.SEED.1 and RANDOM.SEED.2
- ROOTOFNEGATIVE

#### RANK Function Monitoring Options

- [RANK_CALLS](olap-dml-functions-l-z.md)
- [RANK_CELLS](olap-dml-functions-l-z.md)
- [RANK_SORTS](olap-dml-functions-l-z.md)

### 5.4 ALLOCERRLOGFORMAT

The ALLOCERRLOGFORMAT option determines the contents and the formatting of the error log that you specify with the ERRORLOG argument to the ALLOCATE command.

#### Syntax

ALLOCERRLOGFORMAT = text

#### Parameters

text
Characters that determine the contents and formatting of the error log that you specify with an [ERRORLOG](olap-dml-commands-a-g.md) statement in an [ALLOCMAP](olap-dml-commands-a-g.md) command. By placing an `INTEGER` value before the formatting character, you can specify the number of characters that the object occupies in the error log. You can specify escape sequences as formatting characters. For valid escape sequences, see "[Escape Sequences](data-types-operators-and-expressions.md)". The following table lists the characters that specify the contents of the error log. The default value of ALLOCERRLOGFORMAT is the following.

    '%8p %8y %8z %e (%n)'

Table 5-1 Characters for Specify the Contents of the Error Log for ALLOCATE

| Character | Output Specified                                            |
|:----------|:------------------------------------------------------------|
| b         | The basis object being processed.                           |
| c         | The child node of the dimension being processed.            |
| d         | The name of the dimension being processed.                  |
| e         | A description of the error encountered.                     |
| n         | The error code of the error encountered.                    |
| p         | The parent node of the dimension being processed.           |
| r         | The name of the relation being allocated down.              |
| s         | The source object being processed.                          |
| t         | The target object being processed.                          |
| n         | The basis value of the child cell receiving the allocation. |
| y         | The source value of the parent cell being allocated.        |
| z         | The basis value of the parent cell being allocated.         |

#### Examples

Example 5-1 Setting the ALLOCERRLOGFORMAT Option

This example sets the ALLOCERRLOGFORMAT option and produces the results shown in the last line.

    ALLOCERRLOGFORMAT = '%8p %8y %8z %e (%n)'
    SHOW ALLOCERRLOGFORMAT
    %8p %8y %8z %e (%n)

### 5.5 ALLOCERRLOGHEADER

The ALLOCERRLOGHEADER option determines the column headings for the error log that you specify with the ERRORLOG argument to the ALLOCATE command. To specify additional formatting for the error log, use the ALLOCERRLOGFORMAT option.

#### Syntax

ALLOCERRLOGHEADER = text

#### Parameters

text
Characters that determine the content and formatting of the column headers that are the first line of the error log that you specify with the ALLOCATE command. (See ALLOCERRLOGFORMAT for a list of the characters you can use.)

When you specify `NA` as the value for this option, then ALLOCATE does not write any header to the error log. The following is the default value of ALLOCERRLOGHEADER.

    'Dim      Source   Basis\n%-8d %-8v %-8b Description\n
    -------- -------- -------- -----------'

#### Examples

Example 5-2 Setting the ALLOCERRLOGHEADER Option

The following statements define the heading for the error log specified by an ALLOCATE statement and show the value of the ALLOCERRLOGHEADER option.

    ALLOCERRLOGHEADER = 'Dim      Source   Basis\n %-8d %-8v %-8b Description \n
    -------- -------- -------- -----------'
    SHOW ALLOCERRLOGHEADER

The preceding statement produces the following results.

    Dim      Source   Basis
    %-8d %-8s %-8b Description 
    -------- -------- -------- -----------

An allocation operation that has a variable named `budget` as both the source and basis objects and which encounters a deadlock when allocating down the `division` dimension produces the following entry in the error log.

     
    Dim      Source   Basis
    Division Budget   Budget  Description 
    -------- -------- -------- -----------
    Accdiv   650000    NA      A deadlock occurred allocating data (5)

### 5.6 AWWAITTIME

The AWWAITTIME option holds the number of seconds that an AW ATTACH command with the WAIT keyword waits for an analytic workspace to become available for access. The default value of AWWAITTIME is 20 seconds.

#### Data Type

`INTEGER`

#### Syntax

AWWAITTIME = seconds

#### Parameters

seconds
The number of seconds to wait for an analytic workspace to be available. The default value is 20 seconds.

#### Usage Notes

Workspace Sharing

When your user ID has the appropriate access rights and no user has read/write exclusive access to the workspace, you can get read-only access to an analytic workspace, no matter how many other users are using it. When another user has read/write access and commits the workspace, your view of the workspace does not change; you must detach and reattach the workspace to see the changes.

#### Examples

Example 5-3 Specifying a Wait Time of One Minutes

Assume that you want to wait for 60 seconds when attaching an analytic workspace. To do so, reset the value of the AWWAITTIME option by issuing the following statement.

    AWWAITTIME = 60

### 5.7 BADLINE

When a program, model, or input file is executing, the BADLINE option controls whether Oracle OLAP records, in the current outfile, the line that caused an error.

**See Also:**

[PROGRAM](olap-dml-commands-h-z.md), [MODEL](olap-dml-commands-h-z.md), and [INFILE](olap-dml-commands-h-z.md).

#### Data Type

BOOLEAN

#### Syntax

BADLINE = {YES\|NO}

#### Parameters

YES
When an error occurs during the execution of a program, model, or input file, Oracle OLAP records in the current outfile the name of the program, model, or file in which the error occurred and the line that caused the error. When an error message is included in the output, the BADLINE information appears immediately after the error message.

NO
(Default) When an error occurs in a program, model, or input file, Oracle OLAP does not record the error in the current outfile.

#### Examples

Example 5-4 Using the BADLINE Option

In a simple program called `test`, the variable `myint1` is divided by zero.

    DEFINE test PROGRAM
    PROGRAM
    VARIABLE myint1 INTEGER
    VARIABLE myint2 INTEGER
    myint1 = 0
    myint2 = 250/myint1
    END

When you run the program when the `DIVIDEBYZERO` option is set to `NO`, then an error occurs because division by zero is not allowed. When `BADLINE` is set to `YES`, the following messages are recorded in the current outfile.

    ERROR: (MXXEQ01) A division by zero was attempted. Set DIVIDEBYZERO to
    YES if you want NA to be returned as the result of division by zero.
    In DEMO!TEST PROGRAM:
    myint2 = 250/myint1

Example 5-5 Finding Errors in Program Lines

In a simple program called `test`, the variable `myint1` is divided by `0` (zero).

    DEFINE test PROGRAM
    PROGRAM
    VARIABLE myint1 INTEGER
    VARIABLE myint2 INTEGER
    myint1 = 0
    myint2 = 250/myint1
    END

When you run the program, an error occurs because division by zero is not allowed (that is, when DIVIDEBYZERO is set to `NO`).

When BADLINE is set to `NO` only the error is recorded in the current outfile.

    ERROR: (MXXEQ01) A division by zero was attempted.  (If you want NA to
    be returned as the result of a division by zero, set the DIVIDEBYZERO
    option to YES.)
     

When BADLINE is set to `YES`, the line that causes the error and the name of the program in which the error occurred are recorded in the current outfile.

    ERROR: (MXXEQ01) A division by zero was attempted.  (If you want NA to
    be returned as the result of a division by zero, set the DIVIDEBYZERO
    option to YES.)
    In TESTBAD PROGRAM:
    myint2 = 250/myint1
    In EDDE.RUNCMD PROGRAM:

### 5.8 BMARGIN

The BMARGIN option defines the number of blank lines for the bottom margin of output pages. BMARGIN is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and DESCRIBE. The BMARGIN option is usually set in the initialization section of report programs.

#### Data Type

`INTEGER`

#### Syntax

BMARGIN = n

#### Parameters

n
An `INTEGER` expression that specifies the number of lines to set aside for the bottom margin in a report. The default is `1`.

#### Usage Notes

Setting BMARGIN for a File

To set BMARGIN for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set BMARGIN to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, BMARGIN returns to its default value of `1` for the file.

When you set BMARGIN for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE statements that send output to a file. That is, the value of BMARGIN is automatically saved for the default outfile

#### Examples

Example 5-6 Setting the Bottom Margin of a Report Page

Suppose you want to be able to make notes on the bottom of a report page. You can set a large bottom margin of 5 lines. Here is the statement that you would include in the initialization section of your report program.

    BMARGIN = 5

### 5.9 CALENDARWEEK

The CALENDARWEEK option determines whether weeks should be aligned with the actual calendar year.

**Note:**

You can only use this function with dimensions of type WEEK.

#### Data Type

BOOLEAN

#### Syntax

CALENDARWEEK = {YES\|NO}

#### Parameters

YES
(Default) Specifies that weeks are aligned with the calendar year. For example, if you have defined a dimension of type WEEK, Oracle OLAP numbers its values so that the first week in the calendar year is week 1, the second week in the calendar year is week 2, and so on. Weeks are aligned with the calendar year regardless of any beginning or ending date specified in the WEEK dimension definition.

NO
Specifies that weeks are not aligned with the calendar year. Instead, weeks are numbered so that they are aligned with the date specified in the dimension definition. For example, if you have defined a dimension of type WEEK with a beginning or ending date, its values are numbered so that the week corresponding to the date in the dimension definition is week `1`, the following week is week `2`, and so on.

#### Usage Notes

Fiscal Years

Setting CALENDARWEEK to `NO` causes weeks to be numbered so that the number 1 is assigned to the week beginning or ending on the date specified in the DEFINE DIMENSION statement. This week is then assigned to a fiscal year, which is the calendar year of the first January 1 on or after the week's starting date. For example, if you define a dimension of type WEEK with a starting date of `02Jan1996` (or, equivalently, an ending date of `08Jan1996`), the week starting `02Jan1996` is considered week `1` of fiscal year `1997`. If, by contrast, you had given the dimension a starting date between `02Jan1995` and` 01Jan1996`, then the week starting on that date is week `1` of fiscal year `1996`.

#### Examples

Example 5-7 Aligning Weeks with the Calendar Year

The following statements define a dimension of type WEEK, define its ending date, add values to the dimension, and produce a report.

    DEFINE week dimension WEEK ENDING '18Jan97'
    MAINTAIN week ADD '21Dec96' '25Jan97'
    REPORT W 22 CONVERT(week DATE)

These statements produce the following output.

    WEEK             CONVERT(WEEK DATE)
    -------------- --------------------
    w51.96         21Dec96
    w52.96         28Dec96
    w1.97          04Jan97
    w2.97          11Jan97
    w3.97          18Jan97
    w4.97          25Jan97

Example 5-8 Aligning Weeks with a Specified Ending Date

The following statements set the CALENDARWEEK option to `NO`, which aligns the weeks with the ending date that is specified in the definition of the `week` dimension in "Example 5-7" .

    CALENDARWEEK = NO
    REPORT W 22 CONVERT(week date)

These statements produce the following output.

    WEEK             CONVERT(WEEK DATE)
    -------------- --------------------
    w50.97         21Dec96
    w51.97         28Dec96
    w52.97         04Jan97
    w53.97         11Jan97
    w1.98          18Jan97
    w2.98          25Jan97

### 5.10 COLWIDTH

The COLWIDTH option controls the default width of data columns in report output. For output from the ROW command and HEADING command, COLWIDTH affects all columns except the first column. For output from REPORT, COLWIDTH affects all data columns and the label columns for a composite or a conjoint dimension.

**Note:**

For an individual column, the COLWIDTH value is always overridden by a WIDTH attribute in a HEADING, REPORT, or ROW command

#### Data Type

`INTEGER`

#### Syntax

COLWIDTH = n

#### Parameters

n
An `INTEGER` expression that specifies the desired column width in number of characters. You can set COLWIDTH to any value from `1` to `4,000`. The default is `10`.

**Note:**

The maximum width of a line in a report is 4,000 characters. Therefore, the combined width of all the columns of a report cannot be greater than 4,000 characters.

#### Examples

Example 5-9 Setting the Default Column Width in a Report

Suppose you want to look at unit sales for six months. Because the data values are not large, you do not need a width of 10 characters for your data columns. You can set COLWIDTH to provide a narrower default column.

    LIMIT district TO 'Atlanta'
    LIMIT month TO 'Oct95' TO 'Mar96'
    COLWIDTH = 6
    REPORT ACROSS month: units

These statements produce the following output.

    DISTRICT: ATLANTA
                   ------------------UNITS------------------
                   ------------------MONTH------------------
    PRODUCT        Oct95  Nov95  Dec95  Jan96  Feb96  Mar96
    -------------- ------ ------ ------ ------ ------ ------
    Tents             503    345    259    279    305    356
    Canoes            317    282    267    281    309    386
    Racquets        1,365  1,270  1,357  1,125  1,304  1,263
    Sportswear      3,065  2,327  1,955  2,591  2,829  3,137
    Footwear        3,445  3,247  2,831  3,089  3,282  3,475

### 5.11 COMMAS

The COMMAS option controls the use of the character that separates thousands and millions in numeric output. This character is typically a comma; however, it might be different depending on your NLS_TERRITORY setting. The THOUSANDSCHAR option records the character that is currently being used for separating thousands. The COMMAS option controls whether the character appears in numeric output.

COMMAS affects all commands that produce output, including the ROW command, HEADING, REPORT, and SHOW.

**Note:**

You can use the COMMA and NOCOMMA attributes of a HEADING, REPORT, or ROW command to override the COMMAS setting.

#### Data Type

BOOLEAN

#### Syntax

COMMAS = {NO\|YES}

#### Parameters

NO
Numeric output does not contain a character that separates thousands, millions, and so on.

YES
(Default) Numeric output contains a character that separates thousands, millions, and so on.

#### Examples

Example 5-10 Showing Numerical Data Without Commas

Suppose you want to look at the cost of goods sold, without commas in the data values. You can set COMMAS to `NO` before producing your report.

    COMMAS = NO
    LIMIT line TO 'Cogs'
    LIMIT month TO 'Jan96' 'Feb96'
    REPORT DOWN division ACROSS month: DECIMAL 0 actual

These statements produce the following output.

    LINE: COGS
                   -----ACTUAL------
                   ------MONTH------
    DIVISION       Jan96      Feb96
    -------------- -------- ----------
    Camping          368044     385120
    Sporting         287558     315299
    Clothing         567767     610727

### 5.12 COMPILEMESSAGE

You use the COMPILEMESSAGE option to specify whether you want Oracle OLAP to send to the current outfile non-irrecoverable error messages during execution of the COMPILE command. Non-irrecoverable error messages are those indicating errors that do not prevent a program from compiling.

**See Also:**

For more information about compiling objects, see [COMPILE](olap-dml-commands-a-g.md).

#### Data Type

BOOLEAN

#### Syntax

COMPILEMESSAGE = {YES\|NO}

#### Parameters

YES
(Default) Indicates that Oracle OLAP should record non-irrecoverable error messages during execution of the COMPILE command.

NO
Indicates that Oracle OLAP should suppress non-irrecoverable error messages during execution of the COMPILE command.

#### Examples

Example 5-11 Suppressing Error Messages During Compilation

The following statement specifies that Oracle OLAP should suppress non-irrecoverable error messages during execution of the COMPILE command.

    COMPILEMESSAGE = NO

### 5.13 COMPILEWARN

The COMPILEWARN option controls whether Oracle OLAP records a warning message in the current outfile when a compilable object, such as a program or a model, is being compiled automatically. (When you use the COMPILE command to explicitly compile an object, Oracle OLAP does not display the COMPILEWARN message.)

A compilable object is automatically compiled in the following cases:

- The first time it is executed after being edited.

- The first time it is executed in a session when it was compiled in a previous session after the last time the analytic workspace was updated and committed.

- After an analytic workspace object referred to in the code has been renamed or deleted. When the object name in the code has not been redefined, you receive an error message.

- When the code refers to objects in another analytic workspace and the objects in the currently attached analytic workspace do not have the same object type (variable, relation, and so on), data type (`INTEGER`, `TEXT`, and so on), or dimensions as the objects available when the code was previously compiled.

#### Data Type

BOOLEAN

#### Syntax

COMPILEWARN = {YES\|NO}

#### Parameters

YES
Oracle OLAP records a message warning you that a compilable object is being compiled automatically. The message explains why the compilation was necessary.

NO
(Default) Oracle OLAP does not record a message warning you that an object is being compiled automatically.

#### Examples

Example 5-12 Specifying That You Want Compiler Warnings

When COMPILEWARN is set to `YES`, when you run the` do_report` program just after editing it, Oracle OLAP places the following message in your current outfile before the `do_report` output.

    DO_REPORT is being automatically compiled.

### 5.14 DATEFORMAT

The DATEFORMAT option holds the template used for displaying DATE-only data type values and converting DATE-only values to text values. The template can include format specifications for any of the four components of a date (day, month, year, and day of the week). It can also include additional text.

**See Also:**

"Date-only Data Type Options"

#### Data Type

TEXT

#### Syntax

DATEFORMAT = template

#### Parameters

template
A TEXT expression that specifies the template for displaying dates. Each component in the template must be preceded by a left angle bracket and followed by a right angle bracket. You can include additional text before, after, or between the components. The default template is `'<DD><MTXT><YY>'`.

The following tables present the valid formats for each component. The tables provide two display examples, one for March 1, 1990 and another for November 12, 2051.

The following table presents the valid formats for days.

Table 5-2 DATEFORMAT Templates for Day

| Format  | Meaning                  | March 1, 1990 | November 12, 2051 |
|:--------|:-------------------------|:--------------|:------------------|
| `<D>`   | One digit or two digits  | `1`           | `12`              |
| `<DD>`  | Two digits               | `01`          | `12`              |
| `<DS>`  | Space-padded, two digits | `1`           | `12`              |
| `<DT>`  | Ordinal, uppercase       | `1ST`         | `12TH`            |
| `<DTL>` | Ordinal, lowercase       | `1st`         | `12th`            |

The following table presents the valid formats for weeks. The table provides two display examples, one for March 1, 1990 and another for November 12, 2051.

Table 5-3 DATEFORMAT Templates for Week

| Format     | Meaning                         | March 1, 1990 | November 12, 2051 |
|:-----------|:--------------------------------|:--------------|:------------------|
| `<W>`      | Numeric                         | `4`           | `1`               |
| `<WT>`     | First letter, uppercase         | `W`           | `S`               |
| `<WTXT>`   | First three letters, uppercase. | `WED`         | `SUN`             |
| `<WTXTL>`  | First three letters, lowercase  | `Wed`         | `Sun`             |
| `<WTEXT>`  | Full name, uppercase            | `WEDNESDAY`   | `SUNDAY`          |
| `<WTEXTL>` | Full name, lowercase            | `Wednesday`   | `Sunday`          |

Note that when you specify a format of` <WTXT>`, `<WTXTL>`, `<WTEXT>`, or `<WTEXTL>`, the case in which the value is specified in DAYNAMES affects the displayed value:

- When the name in DAYNAMES is entered as all lowercase, the entire name is converted to uppercase. Otherwise, the first letter is converted to uppercase and the second and subsequent letters remain in their original case.

- When the name in DAYNAMES is entered as all uppercase, the second and subsequent letters are converted to lowercase. Otherwise, the entire name remains in the case specified in DAYNAMES.

The following table presents the valid formats for months. The table provides two display examples, one for March 1, 1990 and another for November 12, 2051.

Table 5-4 DATEFORMAT Templates for Month

| Format    | Meaning                        | March 1, 1990 | November 12, 2051 |
|:----------|:-------------------------------|:--------------|:------------------|
| `<M>`     | One digit or two digits        | 1             | `11`              |
| `<MM>`    | Two digits                     | `03`          | `11`              |
| `<MS>`    | Space-padded, two digits       | `3`           | `11`              |
| `<MT>`    | First letter, uppercase        | `M`           | `N`               |
| `<MTXT>`  | First three letters, uppercase | `MAR`         | `NOV`             |
| `<MTXTL>` | First three letters, lowercase | `Mar`         | `Nov`             |

Note that when you specify a format of` <MTXT>` or `<MTXTL>`, the case in which the value is specified in MONTHNAMES affects the displayed value:

- When the name in MONTHNAMES is entered as all lowercase, the entire name is converted to uppercase. Otherwise, the first letter is converted to uppercase and the second and subsequent letters remain in their original case.

- When the name in MONTHNAMES is entered as all uppercase, the second and subsequent letters are converted to lowercase. Otherwise, the entire name remains in the case specified in MONTHNAMES.

The following table presents the valid formats for years. The table provides two display examples, one for March 1, 1990 and another for November 12, 2051.

Table 5-5 DATEFORMAT Templates for Year

| Format   | Meaning                   | March 1, 1990 | November 12, 2051 |
|:---------|:--------------------------|:--------------|:------------------|
| `<YY>`   | Two digits or four digits | `90`          | `2051`            |
| `<YYYY>` | Four digits               | `1990`        | `2051`            |

#### Usage Notes

Specifying Angle Brackets as Text in a DATEFORMAT Template

To include an angle bracket as additional text in a template, specify two angle brackets for each angle bracket to be included as text (for example, to display the entire date in angle brackets, specify` '<<<D><M><YY>>>'`).

Month and Day Names

The names used in the month component for the MT, MTXT, MTXTL, MTEXT, and MTEXTL formats are drawn from the current setting of the MONTHNAMES option. The names used in the day-of-the-week component for the WT, WTXT, WTXTL, WTEXT, and WTEXTL formats are drawn from the current setting of the DAYNAMES option.

Specifying Abbreviations for Day and Month

You can set the DAYABBRLEN and MONTHABBRLEN options to use abbreviations of different lengths for day and month names.

Out-of-Range Years for DATEFORMAT

When you specify the YY format, and a year outside the range of 1950 to 2049 is to be displayed, the year is displayed in four digits.

Automatic Conversion of DATE-only Values to Text Values

When you use a value with DATE-only data type where a text data type is expected. Oracle OLAP also uses the date template in the DATEFORMAT option to automatically convert the date to a text value. When you want to override the current DATEFORMAT template, you can convert the date result to text by using the CONVERT function with a date-format argument.

Once a DATE-only value is stored in a text variable, the DATEFORMAT template is no longer used to format the display of the value, and subsequent changes to DATEFORMAT have no impact.

DATE-only Dimension Values

The DATEFORMAT option does not how Oracle OLAP displays DATE-only values of DAY, WEEK, MONTH, QUARTER, and YEAR dimensions. How these values are displayed is controlled by a [VNF](olap-dml-commands-h-z.md) (value name format) attached to the dimension definition, or by default conventions for DAY, WEEK, MONTH, QUARTER, and YEAR dimensions as described in the Default VNFs for DWMQY Dimensions table in [Date-only Dimension Values](data-types-operators-and-expressions.md).

#### Examples

Example 5-13 Changing the Format of Dates

The following statements define a DATE-only variable and set its value to March 24, 1997, then set the date format to two digits each in the order of day, month, and year, and send the result to the current outfile.

    DEFINE datevar VARIABLE DATE
    datevar = '24Mar97'
    DATEFORMAT = '<DD>/<MM>/<YY>'
    SHOW datevar

These statements produce the following output.

    24/03/97

The following statements change the date format to month (text), day (two digits), and year (four digits), and send the result to the current outfile.

    DATEFORMAT = '<MTEXTL> <D>, <YYYY>'
    SHOW DATEVAR

These statements produce the following output.

    March 24, 1997

The following statements change the date format to day of the week (text), month (text), day (one or two digits), and year (four digits), and send the result to the current outfile.

    DATEFORMAT = '<WTEXTL> <MTEXTL> <D>, <YYYY>'
    SHOW DATEVAR

These statements produce the following output.

    Monday March 24, 1997

Example 5-14 Including Text in the Format of a Date

The following statements save and then change the DATEFORMAT option to include extra text for an analytic workspace startup greeting.

    PUSH DATEFORMAT
    DATEFORMAT = 'Hello.  Today is <wtextl>, the <dtl> -
    OF <MTEXTL>.'
    SHOW TODAY
    POP DATEFORMAT

When today's date is May 30, 1997, the following output is sent to the current outfile when the program is run.

    Hello.  Today is Friday, the 30th of May.

### 5.15 DATEORDER

The DATEORDER option holds three characters that indicate the intended order of the month, day, and year components of the DATE-only values in an analytic workspace for those cases in which their interpretation is ambiguous. Oracle OLAP automatically refers to DATEORDER whenever you enter an ambiguous DATE-only value or convert one from a text value. For information about date values, see "[Date-only Data Type](data-types-operators-and-expressions.md)".

#### Data Type

ID

#### Syntax

DATEORDER = order

#### Parameters

order
One of the following text expressions: `'MDY'`, `'DMY'`, `'YMD'`, `'YDM'`, `'MYD'`, `'DYM'`. Each letter represents a component of the date. `M` stands for the month, `D` for the day, and Y for the year. The default date order is `'MDY'`.

#### Usage Notes

Ambiguous Dates

When you enter an unambiguous DATE-only value or convert a text value that has only one interpretation as a date, it is handled without consulting the DATEORDER option. For example, in `03-24-97` the `97` can only refer to the year. Considering what is left, the `24` cannot refer to the month, so it must be the day. Only `03` is left, so it must be the month. When, however, the interpretation is ambiguous, as in the value `3-5-97`, the current value of DATEORDER is used to interpret the meaning of each component.

DATEORDER and TEXT-to-DATE-only Conversion

When you use a text value where a DATE-only value is expected, or when you store a text value in a DATE-only variable, the text value must conform to a style listed "[Date-only Input Values](data-types-operators-and-expressions.md)". Oracle OLAP automatically converts the text value to a DATE-only value. When the meaning of the text value is ambiguous, the current setting of DATEORDER is used to interpret the value.

To override the current DATEORDER setting in converting a text value to a DATE-only value, use the CONVERT function with the date-order argument.

Essential Date Components

Suppose you want to assign a date value to a DAY, WEEK, MONTH, QUARTER, or YEAR dimension using a MAINTAIN statement or to a valueset using the LIMIT command. When you specify the value in the form of a DATE-only expression or a text literal, Oracle OLAP uses the DATEORDER option to interpret the value. When supplying a text literal, you can use any valid input style for dates. However, you must supply only the date components that are necessary for identifying a time period in the particular type of dimension or valueset you are using. For example, for a MONTH dimension or its valueset, you can specify a complete date, such as `30jun97`, or you can provide only the essential components, such as `jun97` or `0697`.

DWMQY Dimension Phases

The DATEORDER option is used to interpret a phase argument to a DEFINE DIMENSION statement for DAY, WEEK, MONTH, QUARTER, and YEAR dimensions.

#### Examples

Example 5-15 Changing the Date Order

The following statements define and assign a value to a DATE-only variable, specify the date format and the date order, and send the output to the current outfile.

    DEFINE datevar VARIABLE DATE
    dATEFORMAT = '<MTXT> <D>, <YYYY>'
    DATEORDER = 'MDY'
    DATEVAR = '3 5 1997'
    SHOW DATEVAR

These statements produce the following output.

    MAR 5, 1997

The following statements change the date order, and, therefore, the way the same value of the DATE-only variable is interpreted.

    DATEORDER = 'DMY'
    SHOW DATEVAR

These statements produce the following output.

    MAY 3, 1997

### 5.16 DAYABBRLEN

The DAYABBRLEN option specifies the number of characters to use for abbreviations of day names that are stored in the DAYNAMES option. You can specify how many characters to use for abbreviating particular day names when you specify the `<WT>`, `<WTXT>`, and `<WTXTL>` formats with the DATEFORMAT text option.

#### Data Type

TEXT

#### Syntax

DAYABBRLEN = specification \[;\|, specification\]...

where `specification` is a text expression that has the following form:

     startpos \[- endpos\] : length

You can define many different groups of days, each with different abbreviation lengths. When you do so, separate the groups with a comma or a semicolon as shown in the syntax.

#### Parameters

startpos \[- endpos\]
Numbers that represent the first and last days whose abbreviation length is defined by length. These numeric positions apply to the corresponding lines of text in the DAYNAMES option. You can specify these ranges of values in reverse order, endpos \[-startpos\], when you prefer.

The DAYNAMES option can have more than seven lines, so you can specify startpos and endpos greater than seven in the setting of DAYABBRLEN. When you specify a range where neither startpos nor endpos has a corresponding text value in the DAYNAMES option, then Oracle OLAP has no text values to abbreviate for that range. When you later change your day names list so that startpos is valid, the specified abbreviation is applied.

length
A number that specifies the length in characters (not bytes) of abbreviated day names. When you do not specify an abbreviation length for a given position in the DAYNAMES option, or when you explicitly set a given position to zero, Oracle OLAP uses the default abbreviations of one character for `<WT>` and three characters for `<WTXT>` and `<WTXTL>`. Oracle OLAP never uses abbreviations when you have designated the full name specifications `<WTEXT>` and `<WTEXTL>`.

#### Usage Notes

Ambiguous Day Names

You can use DAYABBRLEN to interpret ambiguous names, for example, whether `'T'` stands for Tuesday or Thursday. When the DAYABBRLEN for Tuesday was `1` and for Thursday was 2, then `'T'` would always match Tuesday, and it would require at least `'Th'` to match Thursday. This interpretation does not depend on the order of Tuesday and Thursday in the week; it would work the same way when the two days were reversed. If, on the other hand, the DAYABBRLEN for each of these was `2`, then `'T'` would not match either one, and you would have to enter at least `'Tu'` or `'Th'` to get a match.

#### Examples

Example 5-16 Specifying Day Abbreviations

The following DAYABBRLEN setting specifies that the first five days of the week are abbreviated with one character and the last two days are abbreviated with two characters.

    DAYABBRLEN = '1-5:1, 6-7:2'
    DATEFORMAT = '<WTXT> <MTXT> <D>, <YYYY>'
    SHOW CONVERT ('2 august 2005' DATE)

These statements product the following result, with Tuesday abbreviated to one character.

    T AUGUST 2, 2005

### 5.17 DAYNAMES

The DAYNAMES option holds the list of valid names for the days of the week. The names are used to display values of type DATE-only or to convert DATE-only values to text.

Oracle OLAP consults the DAYNAMES list when it displays or converts a date using the `<WT>`, `<WTXT>`, `<WTXTL>`, `<WTEXT>`, or `<WTEXTL>` formats. These formats are specified in the DATEFORMAT option. When you have multiple sets of day names, Oracle OLAP chooses the synonym whose number of characters and capitalization pattern best match the DATEFORMAT specification.

#### Data Type

TEXT

#### Syntax

DAYNAMES = name-list

#### Parameters

name-list
A multiline text expression that lists the names of the seven days of the week. Each name occupies a separate line. Regardless of which day you are treating as the first day of the week, the list must begin with the name for Sunday. The default value is the list of English names for the days of the week, in uppercase. You can include multiple sets of seven names in your list. The eighth name is a synonym for the first name, the ninth name is a synonym for the second name, and so on.

#### Examples

Example 5-17 Specifying Day Names

The following statements set DAYNAMES to the French names for the days of the week and send the output to the current outfile.

    DAYNAMES = 'dimanche\nlundi\n-
    mardi\nmercredi\njeudi\nvendredi\nsamedi'
    SHOW DAYNAMES

These statements produce the following output.

    dimanche
    lundi
    mardi
    mercredi
    jeudi
    vendredi
    samedi

### 5.18 DECIMALCHAR

(Read-only) The DECIMALCHAR option is the value specified for the NLS_NUMERIC_CHARACTERS option.

DECIMALCHAR only affects the way Oracle OLAP formats numbers in output. When you format numbers for input, use a period (`.`) for the decimal marker. To use a different decimal marker, enclose the value in single quotes and use the TO_NUMBER function to convert the value from text to a valid number.

#### Data Type

ID

#### Syntax

DECIMALCHAR

#### Examples

Example 5-18 Identifying the Decimal and Thousands Markers

The statements in this example show the DECIMALCHAR and THOUSANDSCHAR values.

- The following statement might produce a comma as output.

      SHOW THOUSANDSCHAR

- The following statement might produce a period as output.

      SHOW DECIMALCHAR

- With these values, the following statement might produce the output that follows it.

      SHOW TOTAL(sales)
      63,181,743.50

### 5.19 DECIMALOVERFLOW

The DECIMALOVERFLOW option controls the result of arithmetic operations that produce out-of-range numbers. Decimal numbers are stored as a mantissa and an exponent. Decimal overflow occurs when the result of a calculation is very large and can no longer be represented by the exponent portion of the decimal representation.

#### Data Type

BOOLEAN

#### Syntax

DECIMALOVERFLOW = YES\|NO

#### Parameters

YES
Allows overflow. A calculation that generates overflow executes without error, and the results of the calculation are `NA`.

NO
(Default) Disallows overflow. A calculation involving overflow stops executing, and an error message is produced.

#### Examples

produce the following result.

    NA

Example 5-19 The Effect of DECIMALOVERFLOW

This example shows the effect of changing the value of the DECIMALOVERFLOW option.

When you execute a SHOW statement such as the following without changing DECIMALOVERFLOW from its default value of `NO`, an error occurs.

    SHOW 1000000.0 ** 133

When you change DECIMALOVERFLOW to `YES`, the same statement executes without an error and produces `NA` as the result of the operation. The statements

    DECIMALOVERFLOW = YES
    SHOW 1000000.0 ** 133

### 5.20 DECIMALS

The DECIMALS option controls the number of decimal places that are shown in numeric output. Values are rounded to fit the specified number of decimal places. (Note, however, that the setting of DECIMALS does not affect the format of INTEGER values in output. INTEGER values are shown with no decimal places, unless you explicitly apply a DECIMAL attribute to them in a HEADING, REPORT, or ROW command.)

#### Data Type

INTEGER

#### Syntax

DECIMALS = n

#### Parameters

n
An `INTEGER` expression that specifies the number of decimal places to include in all output of DECIMAL and SHORTDECIMAL values; n can be any number in the range 0 to 40 or the number 255. (When you set DECIMALS to `255`, you are specifying the formats for values of both SHORTDECIMAL and DECIMAL data types. See "Example 5-21".) The default is 2.

#### Examples

Example 5-20 Showing Data with No Decimal Places

To show no decimal places in numeric output, set the DECIMALS option to `0` (zero) before you produce your report.

    DECIMALS = 0
    LIMIT line TO 'COGS'
    LIMIT month TO 'Jan96' 'Feb96'
    REPORT DOWN division ACROSS month: budget

These statements produce the following output.

    LINE: COGS
                   -------BUDGET--------
                   --------MONTH--------
    DIVISION         Jan96      Feb96
    -------------- ---------- ----------
    Camping           355,933    385,308
    Sporting          279,773    323,982
    Clothing          528,370    546,468

Example 5-21 Comparing 2 Decimal Places with Best Presentation Format

This example contrasts the effects of setting DECIMALS to `2` and setting it to `255` ("best presentation" format).

The OLAP DML statements

    DECIMALS = 2
    SHOW JOINCHARS(1.1 'A')

produce the following output.

    1.10A

The OLAP DML statements

    DECIMALS = 255
    SHOW JOINCHARS(1.1 'A')

produce the following output.

    1.1A

### 5.21 DEFAULTAWSEGSIZE

The DEFAULTAWSEGSIZE option holds the default maximum segment size for an analytic workspace created in your database session. The setting is in effect for the duration of your session. For each new session, DEFAULTAWSEGSIZE reverts to the default value.

**Tip:**

To change the maximum size for new segments in an existing workspace, use the AW command with the SEGMENTSIZE keyword. To discover the current maximum size for new segments, use the AW function with the SEGMENTSIZE keyword.

#### Syntax

DEFAULTAWSEGSIZE = n

#### Parameters

n
The number of bytes.

#### Examples

Example 5-22 Displaying the Maximum Segment Size for a Session

The following statement lists the current maximum segment size for workspaces.

    SHOW DEFAULTAWSIZE

Example 5-23 Setting the Maximum Segment Size for a Session

The following statement sets the maximum segment size to approximately 1/2 gigabyte.

    DEFAULTAWSIZE = 536870910

### 5.22 DIVIDEBYZERO

The DIVIDEBYZERO option controls the result of division by zero. (Note that division by zero includes raising zero to a negative power; for example, `0` `**` `-2`.)

#### Data Type

BOOLEAN

#### Syntax

DIVIDEBYZERO = YES\|NO

#### Parameters

YES
Allows division by zero. A statement involving division by zero executes without error; however, the result of the division by zero is `NA`. When you are dividing by a dimensioned variable or expression, setting DIVIDEBYZERO to `YES` enables you to get results for most of the expression's values when a few calculations might involve dividing by zero.

NO
(Default) Disallows division by zero. A statement involving division by zero stops executing and produces an error message.

#### Examples

Example 5-24 The Effect of DIVIDEBYZERO

This example shows the effect of changing the value of the DIVIDEBYZERO option.

When you execute a SHOW statement, such as the following, without changing the DIVIDEBYZERO option from its default value of `NO`, Oracle OLAP attempts to divide 100 by 0 and then produces an error message.

    SHOW 100 / 0

When you change DIVIDEBYZERO to `YES`, the same statement executes without error and produces `NA` as the result of the division. The statements

    DIVIDEBYZERO = YES
    SHOW 100 / 0

produce the following result.

    NA

### 5.23 DSECONDS

(Read-only) The DSECONDS option returns the elapsed time as a `DECIMAL` value. When Oracle is installed on UNIX, the DSECONDS option is the elapsed number of seconds since Oracle was started. When Oracle is installed on Windows, the DSECONDS option is the elapsed number of seconds since the computer on which Oracle is installed was rebooted. As an aid to enhancing a program's speed, DSECONDS can be used to determine how much time elapses while the program is running.

**Note:**

The SECONDS option for information about retrieving elapsed time as an `INTEGER` value.

#### Data Type

DECIMAL

#### Syntax

DSECONDS

#### Examples

Example 5-25 Timing a Program Using DSECONDS

The following program puts the value of DSECONDS at the start of the program in a variable called `t1` and then displays the difference between `t1` and the value of DSECONDS after the program executes.

    DEFINE prodsummary PROGRAM
    PROGRAM
    VARIABLE t1 DECIMAL
    t1 = dseconds
    LIMIT product TO ALL
    BLANK
    FOR product
    DO
      ROW WIDTH 16 name.product ACROSS month Jun96: DECIMAL 0 LSET -
       '$'WIDTH 18 <RSET ' (Actual)' sales rset ' (Plan)' sales.plan>
    DOEND
    BLANK
    ROW WIDTH 35 LSET 'The program took ' rset ' seconds.' -
     (dseconds - t1)
    END

Running this program produces the following results.

    3-Person Tents     $95,121 (actual)     $80,138 (plan)
    Aluminum Canoes   $157,762 (actual)    $132,931 (plan)
    Tennis Racquets    $97,174 (actual)     $84,758 (plan)
    Warm-up Suits      $79,630 (actual)     $73,569 (plan)
    Running Shoes     $153,688 (actual)    $109,219 (plan)
     
          The program took .20 seconds.

### 5.24 ECHOPROMPT

The ECHOPROMPT option determines if input lines and error messages should be echoed to the current outfile. When ECHOPROMPT is set to `YES` and you have specified a debugging file with DBGOUTFILE, the input lines and error messages are echoed to the debugging file instead of the current outfile.

#### Data Type

BOOLEAN

#### Syntax

ECHOPROMPT = {YES\|NO}

#### Parameters

YES
Input lines and error messages are echoed to the current outfile or the debugging file specified by DBGOUTFILE.

NO
(Default) Input lines and error messages do not appear in the current outfile or in the debugging file.

#### Examples

Example 5-26 Using ECHOPROMPT

Suppose you want to have all input lines and error messages included in the disk file that contains your output. Set ECHOPROMPT to `YES` before issuing an OUTFILE statement that sends the output to the disk file. In the following statements, the disk file is in the current directory object.

    ECHOPROMPT = YES
    OUTFILE 'newcalc.dat'

### 5.25 EIFBYTES

(Read-only) The EIFBYTES option holds the number of bytes read by the most recent [IMPORT (EIF)](olap-dml-commands-h-z.md) command or written by the most recent [EXPORT (EIF)](olap-dml-commands-a-g.md) command.

#### Data Type

INTEGER

#### Syntax

EIFBYTES

#### Examples

Example 5-27 Finding Out the Number of Bytes

To find out how many bytes of information were exported to an EIF file when you exported the dimensions of the `demo` workspace, you use the following statements.

    LIMIT name TO OBJ(TYPE) EQ 'DIMENSION'
    EXPORT ALL TO EIF FILE 'myfile.eif'
    SHOW EIFBYTES

The SHOW statement produces the following output.

    2,038

### 5.26 EIFEXTENSIONPATH

The EIFEXTENSIONPATH option contains a list of directory objects that identify the locations where EIF extension files should be created.

#### Data Type

TEXT

#### Syntax

EIFEXTENSIONPATH = path-expression

#### Parameters

path-expression
A text expression that contains one or more directory object names. When you specify multiple aliases, you must enter each one on a separate line. Specify multiple aliases in the order in which they should be used for storing EIF extension files.

#### Usage Notes

When Extension Files Are Created

When the size of an EIF file grows beyond the size specified for EIF files by the FILESIZE argument to the EXPORT (EIF) command, or the current disk or location becomes full, an EIF extension file is created.

Before creating a new extension file, the location specified by EIFEXTENSIONPATH is checked for sufficient disk space. The required amount of disk space is the amount specified for FILESIZE in the EXPORT (EIF). When no value has been specified for FILESIZE, then a check is made for at least 80K of disk space (the minimum size allowed by FILESIZE). When there is insufficient disk space, checking continues through the list until a location with enough available disk space is found.

Multiple Paths in EIFEXTENSIONPATH

When EIFEXTENSIONPATH contains multiple directory objects, the first extension file is created in the first alias in the list. The second extension file is created in the second alias on the list, and so on. When the end of the list is reached, the process starts over again at the beginning. When EIFEXTENSIONPATH contains a single directory object, all extension files are created in that location.

#### Examples

Example 5-28 Establishing a Location for Extension Files

The following statement establishes the `eifext` directory object as the location in which EIF extension files should be created.

    EIFEXTENSIONPATH = 'eifext'

### 5.27 EIFNAMES

The EIFNAMES option holds a list of the names of all the objects imported by the most recent [IMPORT (EIF)](olap-dml-commands-h-z.md) command.

#### Data Type

TEXT

#### Syntax

EIFNAMES

#### Examples

Checking What You Have Imported

Suppose you have exported the `units` variable and the `productset` valueset from the `demo` analytic workspace to a file called `myfile.eif`. After importing the contents of the file into a new workspace, you can use the EIFNAMES option to see the names of the objects you have just imported.

The following statements

    AW CREATE mytest
    IMPORT ALL FROM EIF FILE 'myfile.eif'
    SHOW EIFNAMES

produce this output.

    DISTRICT
    PRODUCT
    MONTH
    UNITS
    PRODUCTSET

### 5.28 EIFSHORTNAMES

The EIFSHORTNAMES option controls the structure of the extension of EIF overflow (extension) file names.

#### Data Type

BOOLEAN

#### Syntax

EIFSHORTNAMES = YES\|NO

#### Parameters

YES
Sets the extension of EIF overflow (extension) file names to `xx`, where each `x` is an automatically assigned lowercase letter between `a` and `z`.

NO
(Default) Sets the extension of EIF overflow (extension) file names have the structure filename.ennn, where nnn is a three-digit number beginning with 001, to distinguish them from workspace extension file names. For example, when an EIF file is named `export.eif`, the extension files are named `export.e001`, `export.e002`, and so on,

#### Examples

Example 5-29 Limiting the Extension of a File Name to Three Characters

The following statement specifies that the file extension for EIF extension file names must be in the form `xx`.

    EIFSHORTNAMES = YES

### 5.29 EIFTYPES

The EIFTYPES option holds a list of the types of objects that are contained in the list produced by the EIFNAMES option. The types are listed in the same order as the corresponding object names in the EIFNAMES list.

#### Data Type

TEXT

#### Syntax

EIFTYPES

#### Examples

Example 5-30 Checking What You Have Imported

Suppose you have exported the `units` variable and the `productset` valueset from an analytic workspace named `demo` to a file called `myfile.eif`. After importing the contents of the file into a new workspace, you can use the EIFNAMES and EIFTYPES options to see the names and object types of the objects you have just imported.

Create the workspace and import the objects with these statements.

    AW CREATE mytest
    IMPORT ALL FROM EIF FILE 'myfile.eif'

Send the names of the imported objects to the current outfile with this statement

    SHOW EIFNAMES

to produce this output.

    DISTRICT
    PRODUCT
    MONTH
    UNITS
    PRODUCTSET

Send the types of the imported objects to the current outfile with this statement

    SHOW EIFTYPES

to produce this output.

    DIMENSION
    DIMENSION
    DIMENSION
    VARIABLE
    VALUESET

### 5.30 EIFUPDBYTES

The EIFUPDBYTES option controls the frequency of updates when you are using the [IMPORT (EIF)](olap-dml-commands-h-z.md) command with its UPDATE keyword. The value of EIFUPDBYTES has an effect only when the UPDATE keyword is specified in this command.

#### Data Type

INTEGER

#### Syntax

EIFUPDBYTES = n

#### Parameters

n
An `INTEGER` expression that specifies the minimum number of bytes to be read between updates, during an import. When EIFUPDBYTES has a value of 0, an update is triggered after each analytic workspace object is imported. When EIFUPDBYTES has a value greater than 0, an update is triggered each time the specified number of bytes is imported. The default is `0` (zero).

#### Examples

Example 5-31 Reducing Update Frequency

In the following example, the UPDATE keyword in the IMPORT (EIF) command ensures that updates occur periodically. The setting of EIFUPDBYTES ensures that the updates do not occur too often.

    EIFUPDBYTES = 500000
    IMPORT ALL FROM EIF FILE 'finance.eif' UPDATE

### 5.31 EIFVERSION

The EIFVERSION option is used with the [EXPORT (EIF)](olap-dml-commands-a-g.md) and [IMPORT (EIF)](olap-dml-commands-h-z.md) commands to copy data between different versions of Express® Server or Oracle OLAP. The version from which the data is exported is referred to as the source. The version to which the data is imported is referred to as the target.

Before you use the EXPORT command to export data to an EIF file, you use the EIFVERSION option to specify the internal version or build number of the target. Then, when you use EXPORT to copy data from the source to an EIF file, the data is in a format that can be imported by the target. Generally, you can import data from an EIF file into any target that has a later version number than the one you specify for the EIF file with EIFVERSION. However, when you set EIFVERSION to a value that is lower than the default version (that is, the version number of the current process), and you try to export data that the earlier version cannot manage, an error is generated. For example, when you try to export an aggmap to a 6.2 version of Express Server, an error is generated because Express Server 6.2 cannot manage aggmap.

You can use the EVERSION function to determine the internal version or build number of the target.

#### Syntax

EIFVERSION = n

#### Parameters

n
The internal version or build number of an Express Server or Oracle OLAP process which is the target into which you want the data imported.

By default, EIFVERSION is set to the internal version or build number of the current process.

#### Examples

Example 5-32 Exporting and Importing Between Different Versions

This example shows how to use EIFVERSION when you want to export data from Oracle OLAP to an EIF file and then import it into Express Server version 6.2.0.

This statement (issued from the target 6.2.0 Express Server)

    SHOW EVERSION

returns the following version and build information

    Module Mgr, Version: 6.2.0.0.0, Build: 60232
    OES Kernel, Version: 6.2.0.0.0, Build: 60232

The following statements export the data from Oracle OLAP (which has a higher build number than 60232) to an EIF file that can be read in Express 6.2.0

    EIFVERSION = 60232
    EXPORT ALL TO EIF FILE 'myeif.eif'

### 5.32 ERRNAMES

The ERRNAMES option controls whether the value of the ERRORTEXT option contains the name of the error (that is, the value of the ERRORNAME option) and the text of the error message.

#### Data Type

BOOLEAN

#### Syntax

ERRNAMES = {NO\|YES}

#### Parameters

NO
ERRORTEXT contains only the text of the error message.

YES
(Default) ERRORTEXT contains the name and the text of the error message.

#### Examples

Example 5-33 ERRORTEXT Value Depending on ERRNAMES Setting

Suppose that you run the following program.

    VARIABLE myint INTEGER
    myint = 35/0
    SHOW ERRORTEXT

When the value of ERRNAMES is set to `YES`, the program returns the following value for ERRORTEXT.

    ERROR: (MXXEQ01) A division by zero was attempted.  (If you want NA to
      be returned as the result of a division by zero, set the DIVIDEBYZERO
      option to YES.)

When the value of ERRNAMES is set to `NO`, the program returns the following value for ERRORTEXT.

    ERROR: A division by zero was attempted.  (If you want NA to be
      returned as the result of a division by zero, set the DIVIDEBYZERO
      option to YES.)

### 5.33 ERRORNAME

The ERRORNAME option holds the name of the first error that occurs when you execute a program or when you execute an OLAP DML statement.

#### Data Type

TEXT

#### Syntax

ERRORNAME

#### Usage Notes

ERRORNAME and SIGNAL

You can create your own error conditions in a program with the SIGNAL command. SIGNAL sets ERRORNAME and ERRORTEXT to the values you specify.

You can use the special name `PRGERR` with the SIGNAL command to communicate to a calling program that an error has occurred. The command `SIGNAL PRGERR` sets ERRORNAME to a blank value and passes an error condition to the calling program without causing another error message to be displayed. For information on using SIGNAL to pass an Oracle OLAP error up a chain of nested programs, see the [TRAP](olap-dml-commands-h-z.md) command.

#### Examples

Example 5-34 Using ERRORNAME with TRAP

In a report program that uses a TRAP command to handle errors, you can use the SIGNAL command to send the appropriate error name to the current outfile.

    DEFINE myreport PROGRAM
    LD Monthly Report
    PROGRAM
    TRAP ON CLEANUP NOPRINT
    PUSH month DECIMALS LSIZE PAGESIZE
    LIMIT month TO LAST 1
       ...
    POP month DECIMALS LSIZE PAGESIZE
    RETURN
    CLEANUP:
    POP month DECIMALS LSIZE PAGESIZE
    SIGNAL ERRORNAME ERRORTEXT
    END

### 5.34 ERRORTEXT

The ERRORTEXT option holds the text of the first error message that occurs when you execute a program or a statement. The name of the error whose message is found in ERRORTEXT is contained in the ERRORNAME option.

**See Also:**

ERRORNAME option, ERRNAMES option, [TRAP](olap-dml-commands-h-z.md) command

#### Data Type

TEXT

#### Syntax

ERRORTEXT

#### Examples

Example 5-35 ERRORTEXT with the SIGNAL Command

In a report program that uses a TRAP command to handle errors, you can use the SIGNAL command to send the appropriate error message to the current outfile.

    DEFINE myreport PROGRAM
    LD Monthly Report
    PROGRAM
    TRAP ON CLEANUP NOPRINT
    PUSH month DECIMALS LSIZE PAGESIZE
    LIMIT month TO LAST 1
       ...
    POP month DECIMALS LSIZE PAGESIZE
    RETURN
    CLEANUP:
    POP month DECIMALS LSIZE PAGESIZE
    SIGNAL ERRORNAME ERRORTEXT
    END

### 5.35 ESCAPEBASE

The ESCAPEBASE option specifies the type of escape that is produced by the INFILE keyword of the CONVERT function.

#### Syntax

ESCAPEBASE = 'escape-type' 

#### Parameters

escape-type
Specify `'d'` for decimal escape, `'x'` for hexadecimal escape.

The default escape type is decimal, which produces the `INTEGER` value for a character in the following form.

     '\dnnn'

A hexadecimal escape is the `INTEGER` value for a character in the following form.

     '\xnn'

#### Examples

For an example of using ESCAPEBASE with CONVERT to convert a text value to an escape sequence, see [Example 7-50](olap-dml-functions-a-k.md).

### 5.36 EXPTRACE

The EXPTRACE option controls whether OLAP DML programs in the analytic workspace named `EXPRESS` are traced when the PRGTRACE option is set to `YES`. The `EXPRESS` analytic workspace is always attached and contains, among other things, OLAP DML programs documented as OLAP DML statements and other "helper" OLAP DML programs.

#### Data Type

BOOLEAN

#### Syntax

EXPTRACE = {YES\|NO}

#### Parameters

YES
All programs are traced, including OLAP DML programs provided as OLAP DML statements.

NO
(Default) OLAP DML programs provided as OLAP DML statements are not traced. Only other types of programs are traced.

#### Usage Notes

How to Identify OLAP DML Programs Provided as OLAP DML Statements

Some OLAP DML statements are implemented as OLAP DML programs. These programs are affected by EXPTRACE. To send to the current outfile a list of these programs, issue the following statement.

    SHOW AW(PROGRAM 'express')

#### Examples

Example 5-36 Tracing System DML Programs

After the following statements are issued, system DML programs such as LISTNAMES and ALLSTAT are traced in addition to user-defined programs.

    PRGTRACE = YES
    EXPTRACE = YES

### 5.37 INF_STOP_ON_ERROR

The INF_STOP_ON_ERROR option specifies the behavior of Oracle OLAP when an error occurs during the execution of an INFILE statement.

#### Syntax

INF_STOP_ON_ERROR = {YES\|NO}

#### Parameters

YES
When an error occurs, report the error and stop reading from the file.

NO
When an error occurs, report the error and continue reading from the file.

#### Examples

Example 5-37 Using INF_STOP_ON_ERROR with DBMS_EXECUTE

Assume that you have an file named `attachmyaw.inf` that includes the following OLAP DML statement that detaches an analytic workspace named `myaw`

    AW DETACH myaw

Assume that the `myaw` workspace is not attached when a SQL application issues the `DBMS_AW.EXECUTE` statement with an OLAP DML INFILE statement to read the `attachmyaw.infinfile` file.

When the INF_STOP_ON_ERR option is set to `NO` then the error `Analytic workspace MYAW is not attached` is reported, Oracle OLAP continues to read the file, and the `DBMS_AW.EXECUTE` procedure completes successfully.

    DBMS_AW.EXECUTE('INF_STOP_ON_ERR = NO ');
    DBMS_AW.EXECUTE('INFILE attachmyaw.inf');

    The current directory is MYDIR.
    ERROR: (ORA-34344) Analytic workspace MYAW is not attached.
    ERROR: (ORA-34344) Analytic workspace MYAW is not attached.

    PL/SQL procedure successfully completed.

When the INF_STOP_ON_ERR option is set to `YES` then the error `Analytic workspace MYAW is not attached` is reported, Oracle OLAP stops reading the file, and the `DBMS_AW.EXECUTE` procedure aborts.

    DBMS_AW.EXECUTE('INF_STOP_ON_ERR = YES ');
    DBMS_AW.EXECUTE('INFILE attachmyaw.inf');

    The current directory is MYSPL.
    DECLARE
      *
    ERROR at line 1:
    ORA-35166: (ORA-34344) Analytic workspace MYAW is not attached.
    ORA-06512: at "SYS.DBMS_AW", line 27
    ORA-06512: at "SYS.DBMS_AW", line 115
    ORA-06512: at line 8

### 5.38 LCOLWIDTH

The LCOLWIDTH option controls the default width of the label column in reports. For output from ROW command and HEADING, LCOLWIDTH affects the first column. For output from REPORT, LCOLWIDTH affects the first column unless the first column is a data column or part of a set of columns that represent the base dimensions of a composite or a conjoint dimension.

**Note:**

For an individual column, the LCOLWIDTH value is always overridden by a WIDTH attribute in a HEADING, REPORT, or ROW command

**See Also:**

COLWIDTH

#### Data Type

INTEGER

#### Syntax

LCOLWIDTH = n

#### Parameters

n
An `INTEGER` expression that specifies the desired column width in number of characters. You can set LCOLWIDTH to any value from 1 to 4000. The default is `14`.

**Note:**

The maximum width of a line in a report is 4,000 characters. Therefore, the combined width of all the columns of a report cannot be greater than 4,000 characters

#### Examples

Example 5-38 Setting Default Column Widths

Suppose you want to look at unit sales for six months. Because the longest product name is 10 characters, you do not need the default width of 14 for your label column. Also, because the sales figures are not large, you do not need a width of 10 characters for your data columns. You can set LCOLWIDTH and COLWIDTH to give smaller default column widths.

    LIMIT district TO 'Atlanta'
    LIMIT month TO 'Oct95' TO 'Mar96'
    LCOLWIDTH = 10
    COLWIDTH = 6
    REPORT ACROSS month: units

These statements produce the following output.

    DISTRICT: ATLANTA
                ------------------UNITS------------------
                ------------------MONTH------------------
    PRODUCT     Oct95  Nov95  Dec95  Jan96  Feb96  Mar96
    ---------- ------ ------ ------ ------ ------ ------
    Tents         503    345    259    279    305    356
    Canoes        317    282    267    281    309    386
    Racquets    1,365  1,270  1,357  1,125  1,304  1,263
    Sportswear  3,065  2,327  1,955  2,591  2,829  3,137
    Footwear    3,445  3,247  2,831  3,089  3,282  3,475

### 5.39 LIKECASE

The LIKECASE option controls whether the LIKE operator is case sensitive.

**Tip:**

The LIKENL option controls whether the LIKE operator recognizes newline characters.

#### Data Type

BOOLEAN

#### Syntax

LIKECASE = {YES\|NO}

#### Parameters

YES
(Default) Specifies that the LIKE operator is case sensitive.

NO
Specifies that the LIKE operator is not case sensitive.

#### Examples

Example 5-39 The Effect of LIKECASE

The following statements show the use of the LIKECASE option.

    LIKECASE = YES
    SHOW 'oracle' LIKE 'Oracle%'

The output of this SHOW statement is

    NO

The SHOW statement

    SHOW 'ORACLE' LIKE '%orc%'

produces the following output.

    NO

The statements

    LIKECASE = NO
    SHOW 'ORACLE' like 'orc%'

produce the following output.

    YES

### 5.40 LIKEESCAPE

The LIKEESCAPE option lets you specify an escape character for the LIKE operator.

#### Data Type

ID

#### Syntax

LIKEESCAPE = char

#### Parameters

char
A text expression that specifies the character to use as an escape character in a LIKE text comparison. The default is no escape character.

The LIKE escape character affects the LISTNAMES program, which accepts a LIKE argument that it uses in a LIKE text comparison.

#### Usage Notes

Using the Escape Character

The LIKE escape character lets you find text expressions that contain the LIKE operator wildcard characters, which are an underscore (`_`), which matches any single character, and a percent character (`%`), which matches any string of zero or more characters.

To include an underscore or percent character in a text comparison, first specify an escape character with the LIKEESCAPE option. Then, in your LIKE expression, precede the underscore or percent character with the LIKEESCAPE character you specified.

You might want to avoid using a backslash (`\`) as the LIKE escape character, because the backslash is the standard OLAP DML escape character. You would therefore need two backslashes to indicate that LIKEESCAPE should treat the second backslash as a literal character.

#### Examples

Example 5-40 Using an Escape Character with the LIKE Operator

This example demonstrates how to specify an escape character and how to use it with the LIKE operator.

Suppose you have a variable named `prodstat` that contains the following text values.

    DEFINE prodstat TEXT <product>
    prodstat(product 'Tents') = - 
    'What are the results of the fabric testing?'
    prodstat(product 'Canoes') = -
    'How has the flooding affected distribution?'
    prodstat(product 'Racquets') = -
    'The best-selling model is Whack_it!'
    prodstat(product 'Sportswear') = -
    '90% of the stock is ready to ship.'
    prodstat(product 'Footwear') = -
    'When are the new styles going to be ready?'

Suppose you have the following program, named `findeschar`, to find certain characters in the text contained in the cells of the `prodstat` variable. The program uses the LIKE operator.

    ARGUMENT findstring TEXT
    FOR product
       IF prodstat LIKE findstring
       THEN SHOW JOINCHARS(product ' - ' prodstat)

Before the program can find a text value that contains a percent character (`%`) or an underscore (`_`), you must specify an escape character by using the LIKEESCAPE option. Suppose you want to use a question mark (`?`) as the escape character. Before you set the escape character to a question mark, the following statement finds text that contains a question mark.

    CALL findeschar('%?%') "Find any text that contains a question mark.

The preceding statement produces the following output.

    Tents - What are the results of the fabric testing?
    Canoes - How has the flooding affected distribution?
    Footwear - When are the new styles going to be ready?

The following statements specify the question mark (`?`) as the escape character and then call the FINDESCHAR program.

    LIKEESCAPE = '?'
    CALL findeschar('%?%') "Find any text that ends with a percent character.

The preceding statement does not find any text because none of the text values in `prodstat` ends in a percent character. To find any text that contains a percent character, the following statement adds another wildcard character. LIKEESCAPE interprets the first percent character as the wildcard that matches zero or more characters, the second percent character as the literal percent character (%) because it is preceded by the question mark escape character, and the third percent character as another wildcard character. The result is that LIKEESCAPE looks for a percent character preceded by and followed by zero or more characters.

    CALL findeschar('%?%%') "Find any text that contains a percent character.

The preceding statement produces the following output.

    Sportswear - 90% of the stock is ready to ship.

The following statement finds text that contains an underscore.

    CALL findeschar('%?%') "Find any text that contains an underscore.

The preceding statement produces the following output.

    Racquets - The best-selling model is Whack_it!

The following statement doubles the escape character to find text that contains the escape character.

    CALL findeschar('%??%') "Find any text that contains a question mark.

The preceding statement produces the following output.

    Tents - What are the results of the fabric testing?
    Canoes - How has the flooding affected distribution?
    Footwear - When are the new styles going to be ready?

Example 5-41 Using an Escape Character with the LISTNAMES Program

This example demonstrates how to find the name of an object that contains a LIKE argument wildcard character. These following statements use the LIKEESCAPE option to specify an escape character, define a couple of object names that contain an underscore, and then list the dimensions whose names include an underscore.

    LIKEESCAPE = '?'
    DEFINE my_textdim DIMENSION TEXT
    DEFINE my_intdim DIMENSION INTEGER
    LISTNAMES DIMENSION LIKE '%?%'

The preceding statement produces the following output.

    3 DIMENSIONs
    ----------------
    MY_INTDIM
    MY_TEXTDIM
    _DE_LANGDIM

### 5.41 LIKENL

The LIKENL option controls whether the LIKE operator recognizes newline characters between lines of a text expression, when deciding whether a text value is like a text pattern. (In the OLAP DML, the representation of a newline character is "`\n`".)

The LIKENL option applies to the text expressions on either side of the LIKE operator.

#### Data Type

BOOLEAN

#### Syntax

LIKENL = {YES\|NO}

#### Parameters

YES
(Default) Specifies that the LIKE operator recognizes newline characters between lines of a text expression.

NO
Specifies that the LIKE operator ignores newline characters between lines of a text expression. Newline characters are ignored in both of the expressions being compared.

#### Examples

Example 5-42 The Effect of LIKENL

The following statements show the use of the LIKENL option:

- The statement

      SHOW textvar

  produces the following output.

      Hello
      world

- The statements

      LIKENL = YES
      SHOW textvar LIKE '%low%'

  produce the following output.

      NO

- The statement

      SHOW '   Hello\nworld' LIKE '%\n%'

  produces the following output.

      YES

- The statement

      SHOW 'Hello\nworld' LIKE '%low%'

  produces the following output.

      NO

- The statements

      LIKENL = NO
      SHOW textvar LIKE '%low%'

  produce the following output.

      YES

- The statement

      SHOW 'Hello\nworld' LIKE '%\n%' 

  produces the following output.

      YES

- The statement

      SHOW 'Hello\nworld' LIKE '%low%'

  produces the following output.

      YES

### 5.42 LIMIT.SORTREL

The LIMIT.SORTREL option controls if a sort is done when you limit a dimension to a related dimension.

#### Data Type

BOOLEAN

#### Syntax

LIMIT.SORTREL = {YES\|NO}

#### Parameters

YES
(Default) Oracle OLAP performs a sort when you limit a dimension to a related dimension.

NO
Oracle OLAP does not perform a sort when limiting to a related dimension.

#### Usage Notes

The Sorting Explained

Normally, when you limit a dimension to a related dimension, the values of the dimension being limited are arranged in the order of the related dimension. When there are multiple values of the first dimension related to a value of the related dimension, the values are sorted in the order of the default status of the first dimension. It is this sort that LIMIT.SORTREL suppresses.

Output Lists when LIMIT.SORTREL Is NO

When LIMIT.SORTREL is `NO`, the output for any given dimension may not list values in logical order.

#### Examples

Example 5-43 Efficient Processing

You are performing calculations on a variable dimensioned by a large dimension named `product`. Your `product` dimension has all levels of the product hierarchy embedded in it: category, vendor, brand, and so on. You are performing the calculations one level at a time, using the relationship between `product` and `productlevel`. Because the order of the dimension values is not important for the calculations and because you are limiting `product` using a related dimension, you use LIMIT.SORTREL to suppress unnecessary sorting which makes the process more efficient.

    LIMIT.SORTREL = NO

### 5.43 LIMITSTRICT

The LIMITSTRICT option is a BOOLEAN option that determines how Oracle OLAP behaves when a list of values in a LIMIT command, a LIMIT function, or a QDR contains a nonexistent value.

#### Syntax

LIMITSTRICT = YES \| NO

#### Parameters

YES
(Default) When a list of values in a LIMIT command, a LIMIT function, or a QDR contains a nonexistent value, Oracle OLAP stops executing the limit and issues an error.

NO
When a list of values in a LIMIT command, a LIMIT function, or a QDR contains a nonexistent value, Oracle OLAP processes the limit while treating the specified value as an NA.

#### Examples

Example 5-44 Limiting with LIMITSTRICT Set to YES

Assume that you have two dimensions (`prod` and `year`) and one variable (`sales`) with the following definitions and values.

    DEFINE prod DIMENSION TEXT
    DEFINE year DIMENSION TEXT
    DEFINE sales VARIABLE INTEGER <prod year>

    PROD
    --------------
    Radios
    TVs

    YEAR
    --------------
    2003
    2004

                   --------SALES--------
                   --------PROD---------
    YEAR             Radios      TVs
    -------------- ---------- ----------
    2003                2,459      3,534
    2004                3,366      3,018


When LIMITSTRICT is set to `YES`, then Oracle OLAP treats requests to limit by the nonexistent `prod` value of `'IDontExist'`, as a request to limit by an invalid value:

- Limiting `prod` to just nonexistent value, results in the error message ORA-34706 and does not change the values in status for `prod`.


      ->LIMIT prod to 'Idontexist'
      ORA-34706: Idontexist is not a valid TESTLIMITSTRICT!PROD.

      ->REPORT prod

      PROD
      --------------
      Radios
      TVs


- Limiting `prod` to a list of values that includes the nonexistent value results in the error message ORA-34706 and does not change the values in status for `prod`

      ->LIMIT prod to 'Idontexist' 'Radios'
      ORA-34706: Idontexist is not a valid TESTLIMITSTRICT!PROD.

      ->REPORT prod

      PROD
      --------------
      Radios
      TVs

- Specifying a nonexistent `prod` value in a QDR for `sales` also results in the error message ORA-34706.

      ->REPORT sales (year '2004'prod 'IDontExist')
      ORA-34706: IDontExist is not a valid TESTLIMITSTRICT!PROD.

Example 5-45 Limiting with LIMITSTRICT Set to NO

Assume that you have the same two dimensions (`prod` and `year`) and variable (`sales`) described in Example 5-44.

When LIMITSTRICT is set to `NO`, then Oracle OLAP treats requests to limit by the nonexistent `prod` value of `'IDontExist'`, as a request to limit by an `NA` value:

- Limiting `prod` to just nonexistent value, results in the error message ORA-35654 and does not change the values in status for `prod`.

      ->LIMIT prod to 'Idontexist'
      ORA-35654: The status of the TESTLIMITSTRICT!PROD dimension cannot be set to null.

      ->REPORT prod
      PROD
      --------------
      Radios
      TVs

- Limiting `prod` to a list of values that includes a nonexistent value does not result in an error message. Instead, `prod` is limited to the existing values.

      ->LIMIT prod to 'Idontexist' 'Radios'

      ->REPORT prod

      PROD
      --------------
      Radios

- Specifying a nonexistent `prod` value in a QDR for `sales` does not result in an error message. Instead, a report of `sales` displays an `NA` value.

      ->REPORT sales (year '2004'prod 'IDontExist')
      ----------        NA

<!-- -->

### 5.44 LINENUM

The LINENUM option contains the current line number of the output. Its value is incremented automatically as output lines are produced. The LINENUM option is meaningful only when PAGING is set to `YES` and only for output from commands such as REPORT and LISTNAMES.

**See Also:**

[RECNO](olap-dml-functions-l-z.md)

#### Data Type

INTEGER

#### Syntax

LINENUM = n

#### Parameters

n
An `INTEGER` expression. Normally you do not want to set LINENUM explicitly, but just want to check its current value.

#### Usage Notes

Starting a New Page

When PAGING is set to `YES`, LINENUM increases by `1` after each line of output. When LINENUM equals PAGESIZE minus BMARGIN, a new page automatically begins.

At the beginning of each new page, LINENUM is automatically reset to `1`.

LINENUM Compared to PAGESIZE

Because the lines in the bottom margin are included in PAGESIZE, LINENUM can never reach PAGESIZE when BMARGIN is set to a number greater than `0` (zero).

The Effect of PAGING on LINENUM

When PAGING is set to `NO` (its default), the value of the LINENUM option continues to increment as more output lines are produced. When you set PAGING to `YES`, LINENUM is set to `1` and it begins counting lines on the current page.

The Effect of OUTFILE on LINENUM

When you use an OUTFILE statement to direct output to a file, LINENUM is set to `1` for the file. When you use OUTFILE with the EOF keyword to redirect output to the default outfile, LINENUM contains the value that it last held for the default outfile.

Sending LINENUM in Output

When you produce output that contains the value of LINENUM, and a new page is created by this output, the value of LINENUM is recorded as `1` when your output consists of a single line. However, when the output is a multiline value, the value of LINENUM may be recorded as a value that is larger than PAGESIZE.

#### Examples

Example 5-46 Keeping the Heading Size Constant

Suppose you have a heading that varies between one and two lines from page to page. Regardless of this variation, you want to draw a line across the page at a constant position below the heading. Include the following statement in the page heading program that you use with your report program.

    WHILE LINENUM LT 5
    BLANK
    ROW W LSIZE ROW CENTER '--------------------------------'

### 5.45 LINESLEFT

(Read-only) The LINESLEFT option contains the number of lines left on the current page. The LINESLEFT option is meaningful only when PAGING is set to `YES` and only for output from commands such as REPORT and LISTNAMES.

#### Data Type

INTEGER

#### Syntax

LINESLEFT

#### Usage Notes

Controlling Page Breaks

LINESLEFT is used primarily in report programs to check the number of lines left on a particular page. When the number of lines left is less than that required for a part of the report that you do not want interrupted by a page break, you can then use a PAGE statement to skip to a new page.

The Effect of PAGESIZE on LINESLEFT

When you change the value of PAGESIZE, the value of LINESLEFT is adjusted accordingly. First, LINESLEFT is subtracted from the old value of PAGESIZE, which gives the lines already used. This result is then subtracted from the new value of PAGESIZE which gives the new value of LINESLEFT. When LINESLEFT becomes less than 1, a new page is started at the next output line.

The Effect of PAGING on LINESLEFT

When you set PAGING to `NO`, LINESLEFT is set to the value of PAGESIZE, and it keeps this value until PAGING is set to `YES`. When you set PAGING to `YES`, LINESLEFT begins counting the lines on the current page.

The Effect of OUTFILE on LINESLEFT

When you use an OUTFILE statement to direct output to a file, LINESLEFT is set to `66` for the file, to match the default value of PAGESIZE. When you set PAGESIZE to a new value for the current outfile, LINESLEFT is adjusted accordingly. For example, assume that you direct output to a file and then set PAGESIZE to `40`. In this case, Oracle OLAP sets LINESLEFT to `40` for the file which ensures that the first line of output to the file triggers a new page when PAGING is set to `YES`.

When you use an OUTFILE statement with the EOF keyword to redirect output to the default outfile, LINESLEFT contains the value that it last held for the default outfile.

Sending LINESLEFT in Output

When you produce output that contains the value of LINESLEFT, the lines that contain this value are never included in the value recorded for LINESLEFT.

#### Examples

Example 5-47 Including a Footnote

In a report, you want a one-line footnote preceded by two blank lines at the bottom of a page. Use the following statements to generate the footnote when three lines remain on the page.

    IF LINESLEFT EQ 3
       THEN DO
       BLANK 2
       ROW W 50 'Subject To Change Without Notice.'
       DOEND

### 5.46 LOCK_LANGUAGE_DIMS

The LOCK_LANGUAGE_DIMS option specifies if the status of language dimension can be changed.

**See Also:**

"Working with Language Dimension Status" in [\$DEFAULT_LANGUAGE](olap-dml-properties.md), [\$DEFAULT_LANGUAGE](olap-dml-properties.md) property, SESSION_NLS_LANGUAGE option, and STATIC_SESSION_LANGUAGE option.

#### Data Type

BOOLEAN

#### Syntax

LOCK_LANGUAGE_DIMS= TRUE \| FALSE

#### Parameters

TRUE
Specifies that Oracle OLAP returns an error if a LIMIT statement tries to limit the status of a language dimension.

When a program changes the value the LOCK_LANGUAGE_DIMS option from FALSE to TRUE, Oracle OLAP resets the status of the language dimension in any attached analytic workspace according to the value of the SESSION_NLS_LANGUAGE option.

FALSE
Sets the status of the language dimension to ALL, and specifies that programs can modify the status of the language dimension using LIMIT.

When a program changes the value the LOCK_LANGUAGE_DIMS option from TRUE to FALSE, Oracle OLAP resets the status of the language dimension in any attached analytic workspace to ALL.

#### Examples

Example 5-48 Explicitly Limiting a Language Dimension

Assume that your analytic workspace contains a language dimension named `mylangs` that has the following definition and values.

    DEFINE MYLANGS DIMENSION TEXT
    PROPERTY '$DEFAULT_LANGUAGE' -
    'AMERICAN'

    MYLANGS
    --------------
    FRENCH
    AMERICAN


Assume also, as shown by the following report, that when you attach the analytic workspace that the status of `mylangs` is American.

    REPORT mylangs

    MYLANGS
    --------------
    AMERICAN


As the following code illustrates, you can explicitly change the status of `mylangs` to French using LIMIT if you first set the value of LOCK_LANGUAGE_DIMS to FALSE. You cannot use LIMIT against a language dimension when the value of LOCK_LANGUAGE_DIMS has its default value of TRUE.

    " Try to LIMIT mylangs

    LIMIT  mylangs to 'FRENCH'
    ORA-33558: The status or contents of the MYAW3!MYLANGS dimension cannot be changed while the LOCK_LANGUAGE_DIMS option is set to yes.

    " Got an error
    SHOW LOCK_LANGUAGE_DIMS
    TRUE

    " Got the error because LOCK_LANGUAGE_DIMS was TRUE
    "Change LOCK_LANGUAGE_DIMS to FALSE
    LOCK_LANGUAGE_DIMS = FALSE

    " Try to LIMIT mylangs again

    LIMIT mylangs TO 'FRENCH'

    " Verify if the LIMIT worked. It did
    REPORT mylangs
    MYLANGS
    --------------
    FRENCH

    " Then relock the language
    LOCK_LANGUAGE_DIMS = TRUE

### 5.47 LSIZE

The LSIZE option defines the line size within which the STDHDR program centers the standard header. LSIZE can be set in the initialization section of a report program.

#### Data Type

INTEGER

#### Syntax

LSIZE = n

#### Parameters

n
An `INTEGER` expression that specifies the line size within which the STDHDR program centers the standard header, or the maximum line size for output from a HEADING statement. The default is 80 characters for a line.

The maximum width of any line in a report, including a heading line, is 4,000 characters. Therefore, it generally makes sense to set LSIZE to a value of 4000 or less.

#### Usage Notes

Centering Report Segments

Because STDHDR centers the running page heading within the width of LSIZE, you can use it with LSIZE to center parts of your report. (Start by setting LSIZE to the width of the longest line in your report.)

Creating Centered Headings

You can use LSIZE in centering your own headings for each page or at the beginning of a section. Start by setting LSIZE to the width of your line. Then use a HEADING statement with a WIDTH of LSIZE and the keyword CENTER before the text of your heading. See Example 5-49.

Setting LSIZE for a File

To set LSIZE for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set LSIZE to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, LSIZE returns to its default value of 80 for the file.

When you set LSIZE for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE commands that send output to a file. That is, the value of LSIZE is automatically saved for the default outfile.

#### Examples

Example 5-49 Centering a Heading

Suppose you design a quarterly sales report to have a short line width of 50 characters so that readers have plenty of room to make notes in the margins. To center your headings, include the following lines near the beginning of your report program.

    PAGEPRG = 'stdhdr'
    LSIZE = 50
    PAGING = YES
    PAGE
    HEADING WIDTH LSIZE CENTER 'Quarterly Sales'

The following output is produced at the beginning of the report.

    96/05/13 15:05:16                            PAGE 1
     
                      Quarterly Sales

### 5.48 MAXFETCH

The MAXFETCH option sets an upper limit on the size of a data block generated by a FETCH statement specified in the `OLAP_command` parameter of the `OLAP_TABLE` function.

**See Also:**

For more information on using FETCH statements, see [FETCH](olap-dml-commands-a-g.md) command. For more information on The `OLAP_TABLE` function, see Oracle OLAP DML Reference.

#### Return Value

INTEGER

#### Syntax

MAXFETCH = integer-expression

#### Parameters

integer-expression
An `INTEGER` expression representing the maximum size in bytes of a data block generated by FETCH. The minimum value for MAXFETCH is 1K (approximately 1,000 bytes), and the maximum value is 2GB (approximately 2,000,000,000 bytes). The default value of MAXFETCH is `256K`.

#### Usage Notes

Improving Performance of Queries Using OLAP_TABLE

The setting of MAXFETCH can effect the performance of queries using the `OLAP_TABLE` function. Large queries with joins of `OLAP_TABLE` function may run faster with higher settings. However, larger settings use more memory which can cause slower performance when there are multiple users. The setting of MAXFETCH does not affect a `SELECT` using only one `OLAP_TABLE` function.

MAXFETCH can cause a FETCH error

When FETCH cannot package a data block within the size limit set by MAXFETCH, it produces an error, and no data is returned to the client. By setting MAXFETCH, you can produce an error, rather than run out of memory, when you attempt to fetch too much data.

#### Examples

Limiting Data Blocks to 4K

The following statement limits the size of data blocks to 4K.

      MAXFETCH = 4096

### 5.49 MODDAMP

The MODDAMP option specifies a weighting factor that damps out oscillations between iterations when you use the Gauss-Seidel method for solving simultaneous equations in a model. MODDAMP can allow the solution of models that would otherwise never converge because the oscillation between equations is stable. In these cases, the oscillations never decay without damping.

With the Gauss-Seidel method, Oracle OLAP tests each model equation for convergence or divergence in each iteration over a block of simultaneous equations. The tests are made by comparing the results of the current iteration to the results from the previous iteration. When MODDAMP specifies a weighting factor that is greater than zero, the value that Oracle OLAP tests and stores after each iteration is a weighted average of the current and previous results. For equations that oscillate between iterations, you can therefore use MODDAMP to damp out the oscillations and either prevent divergence or speed up the convergence of the equations.

#### Data Type

DECIMAL

#### Syntax

MODDAMP = {n\|0.00}

#### Parameters

n
A decimal value, greater than or equal to zero and less than one, that specifies the weighting factor. The closer MODDAMP is to 0.00, the more weight is given to the value from the current iteration. The default value is 0.00, which gives full weight to the current iteration.

When MODDAMP is greater than zero, Oracle OLAP calculates the weighted average for the current iteration as follows.

calcvalue \* (1 - MODDAMP) + weightavg

where:

- `calcvalue` is the value calculated from the model equation in the current iteration.

- `weightavg` is the weighted average calculated in the previous iteration.

See "Stored Weighted Average".

#### Usage Notes

Specifying the Solution Method

The MODDAMP option is used only with the Gauss-Seidel method for solving simultaneous equations. The MODSIMULTYPE option determines the solution method that is being used. The possible settings for MODSIMULTYPE are `GAUSS`, for the Gauss-Seidel method, and `AITKENS`, for the Aitkens delta-squared method.

Effect of MODDAMP on Convergence Speed

MODDAMP is used in calculating the results of all model equations in every simultaneous block, whether they oscillate between iterations or not. For equations that do not oscillate, convergence is slowed down when the value of MODDAMP is greater than zero. Therefore, when your model contains some equations that oscillate and some that do not, you might be able to speed up overall convergence by setting MODDAMP to a small nonzero value, such as `0.20`. A small nonzero value slows down the convergence of non-oscillating equations only slightly, while speeding up the convergence of oscillating equations.

Stored Weighted Average

When the model equation does not converge or diverge on the current iteration, the weighted average calculated in the current iteration is stored. In the next iteration, Oracle OLAP uses this stored average as weightavg (that is, the weighted average calculated in the previous iteration) in the formula for the weighted average.

In the first iteration over a block, Oracle OLAP uses the starting value of the target variable (or dimension value) as the weightavg (that is, the weighted average calculated in the previous iteration).

Iteration Results Compared

In tests for convergence and divergence in each iteration, Oracle OLAP compares the results of the current iteration to the results from the previous iteration. When MODDAMP is greater than zero, Oracle OLAP tests a `comparison value` that is calculated as follows.

(weightavg - weightavg) / (weightavg PLUS MODGAMMA)

where `weightavg` is the weighted average calculated in the previous iteration

For an explanation of the test for convergence, see the MODTOLERANCE option. For an explanation of the test for divergence, see the MODOVERFLOW option.

Options to Control the Solution of Simultaneous Blocks

Altering the value of MODDAMP is just one step you can take in attempting to speed up or attain convergence of a simultaneous block. MODEL lists additional options that you can use to control the solution of simultaneous blocks and provides information on running and debugging models.

#### Examples

Example 5-50 Using the Default MODDAMP Value

The following statements trace a model called `income.bud`, specify that the Gauss-Seidel method should be used for solving simultaneous blocks, limit a dimension, and run the `income.bud` model.

    MODTRACE = YES
    MODSIMULTYPE = 'GAUSS'
    LIMIT division TO 'Camping'
    income.bud budget

These statements produce the following output.

    (MOD= INCOME.BUD) BLOCK 1: SIMULTANEOUS 
    (MOD= INCOME.BUD) ITERATION 1: EVALUATION
    (MOD= INCOME.BUD) revenue = marketing * 300 - cogs
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 35) =  368.650399101
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 36) =  369.209604252
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 37) =  368.718556135
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 38) =  369.149674626
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 39) =  368.771110244
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 40) =  369.103479583
    (MOD= INCOME.BUD) END BLOCK 1

The MODDAMP option is set to its default value of 0.00. The equation for the Revenue line item converged in 40 iterations over a block of simultaneous equations. In the trace lines, you can see the results that were calculated for the Revenue line item in the final 6 iterations.

Example 5-51 Setting MODDAMP to Speed Up the Convergence of a Model

The following statements change the value of MODDAMP and run the `income.bud` model.

    MODDAMP = 0.2
    income.bud budget

These statements produce the following output.

    (MOD= INCOME.BUD) BLOCK 1: SIMULTANEOUS 
    (MOD= INCOME.BUD) ITERATION 1: EVALUATION
    (MOD= INCOME.BUD) revenue = marketing * 300 - cogs
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 1) =  276.200000000
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 2) =  416.187139753
        ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 3) =  368.021098186
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 4) =  367.209906847
       ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 5) =  369.271224267
      ...
    (MOD= INCOME.BUD) BUDGET (LINE REVENUE MONTH 'JAN97' ITER 6) =  368.965397407
    (MOD= INCOME.BUD) END BLOCK 1

In "Example 5-50", the equation for the `Revenue` line item converged in 40 iterations. With MODDAMP set to `0.2` in the current example, the same equation converged in just 6 iterations.

### 5.50 MODERROR

The MODERROR option determines the action that Oracle OLAP takes when a block of simultaneous equations in a model cannot be solved within a specified number of iterations.

**Note:**

"Model Options" for descriptions of all of the options that control the solution of simultaneous blocks

#### Data Type

ID

#### Syntax

MODERROR = {'STOP'\|'CONTINUE'}

#### Parameters

'STOP'
(Default) Oracle OLAP sends an error message to the current outfile and stops executing the model.

'CONTINUE'
Oracle OLAP sends a warning message to the current outfile, stops executing the current block, and resumes execution at the next block in the model.

#### Usage Notes

Block-Solution Failure

When every equation in a simultaneous block passes a convergence test, the block is considered solved. When any equation diverges or fails to converge within a specified number of iterations, the solution of the block fails and an error occurs. MODERROR controls the action that Oracle OLAP takes when an error occurs.

Attaining Convergence for a Simultaneous Block in a Model

When an error occurs, you might be able to attain convergence for the block by changing the value of one or more options that control the solution of simultaneous blocks. For example, you can increase the number of iterations that is attempted or you can change the criteria used in testing for convergence and divergence.

Using 'STOP'

When MODERROR is set to `STOP` and execution of the model halts because of an error, you can run the MODEL.XEQRPT program to produce a report about the execution of the model. The report specifies the block where the solution failed and shows the values of the model options that were used in solving simultaneous blocks.

Using 'CONTINUE'

When MODERROR is set to `CONTINUE` and one block in the model is a simultaneous block that either diverges or fails to converge, Oracle OLAP executes any remaining blocks in the model.

Moreover, Oracle OLAP executes the model for the remaining values in the status of any additional dimensions of the solution variable that are not dimensions of the model. In this case, when you run the MODEL.XEQRPT program when Oracle OLAP finishes executing the model, you see a report on the solution for the final values of the additional dimensions.

When the simultaneous blocks in the model converged when the model was executed for the final values of the additional dimensions, then `MODEL.XEQRPT` reports that the blocks were solved, even though an earlier execution of the model for another dimension value might have failed. When you want to see the `MODEL.XEQRPT` for the dimension values where the failure occurred, you can set MODERROR to `STOP` and rerun the model.

#### Examples

Example 5-52 Debugging a Model

This example assumes that you are connected through OLAP Worksheet and enter the following statements in the Command Input window. The statements set MODERROR to `DEBUG` so that you can debug the `myModel` model (which contains a block of simultaneous equations) when the simultaneous block fails to converge.

    MODERROR = 'DEBUG'
    myModel actual

When the simultaneous block fails to converge, you can type an Oracle OLAP or debugger command in the Command Input window in OLAP Worksheet. Because the solution variable, `actual`, is dimensioned by `division`, you might want to display the current value of `division`.

    SHOW division
    Camping

### 5.51 MODGAMMA

The MODGAMMA option specifies a value to use in testing how much an equation in a simultaneous block of a model is changing between iterations. MODGAMMA controls the degree to which the test compares the absolute amount of the change between iterations versus the proportional change. MODGAMMA is especially important in testing equations that result in very small values.

**Note:**

"Model Options" for descriptions of all of the options that control the solution of simultaneous blocks.

#### Data Type

INTEGER

#### Syntax

MODGAMMA = {n\|1}

#### Parameters

n
An `INTEGER` value to use in testing for convergence and divergence. As Oracle OLAP calculates each equation in a simultaneous block, it constructs a comparison value that is based on the results of the equation for the current iteration and the previous iteration. When the comparison value passes a tolerance test, the equation is considered to have converged. When the comparison value meets an overflow test, the equation is considered to have diverged.

The comparison value that is tested is as follows.

    (thisResult - prevResult) DIVIDED BY (prevResult PLUS MODGAMMA)

where thisResult is the result of this iteration and prevResult is the result of the previous iteration.

Oracle OLAP calculates the absolute value of the enclosed expression. The default value of MODGAMMA is `1`.

#### Usage Notes

Testing Convergence

In the test for convergence, the MODTOLERANCE option determines how closely the results of an equation must match between successive iterations. With the default value of `3` for MODTOLERANCE, the equation is considered to have converged when the comparison value is less than `0.001`.

Testing Divergence

In the test for divergence, the MODOVERFLOW option determines how dissimilar the results of an equation must be in successive iterations. With the default value of `3` for MODOVERFLOW, the equation is considered to have diverged when the comparison value is greater than `1000`.

Comparison Value

The comparison value that Oracle OLAP evaluates in tests of convergence and divergence is fundamentally a proportional value. It expresses the change between iterations as a proportion of the previous results. In the test for convergence, the change between iterations must be small in proportion to the previous results. In the test for divergence, the change between iterations must be large in proportion to the previous results. By testing a proportional value, rather than testing the absolute amount of change, Oracle OLAP can apply the same test criteria to all equations, regardless of the magnitude of the equation results.

However, the comparison value that Oracle OLAP tests is not strictly proportional. When the results of an equation are very close to zero, the denominator of a strictly proportional comparison value would also be very close to zero, and thus the comparison value itself would generally be large. Therefore, the test for convergence would be difficult to satisfy, while the test for divergence would be easy to meet. To solve this problem, Oracle OLAP adds the value of MODGAMMA to the denominator of the comparison value. When the default value of 1 is used for MODGAMMA, the effect of MODGAMMA is as follows:

- When the equation results are close to zero, the denominator is close to one and the test is essentially a test of the absolute change between iterations.

- When the equation results are very large, the effect of adding MODGAMMA to the denominator is negligible, and the test is close to being a strictly proportional test.

Controlling Test Sensitivity

For equation values close to zero, you can control the sensitivity to the tests for convergence and divergence by changing the value of MODGAMMA. When equation values are very small, you essentially scale the changes in model values between iterations when you change the value of MODGAMMA. For example, when you change MODGAMMA from 1 to 2, the comparison value is essentially cut in half. As a consequence, you reduce the likelihood that divergence occurs.

Ways to Increase Speed of Convergence of Model Equations

The default value of MODGAMMA is appropriate in most situations. When you increase the value of MODGAMMA, the model equations converge more quickly, but the results are less precise. The smaller the equation value, the more pronounced is the effect of increasing MODGAMMA; convergence is attained relatively more quickly for small model values, while more precision is lost.

You can also force the simultaneous blocks of a model to converge more quickly by decreasing the value of MODTOLERANCE and thereby relaxing the test for convergence. However, when you do this, you sacrifice the precision of all the results, not just the results of equations with small values.

Therefore, when a model contains some equations with large values and some equations with very small values, it might be preferable to increase MODGAMMA rather than decreasing MODTOLERANCE. By increasing MODGAMMA, you might be able to force equations with small values to converge more quickly while retaining the precision of equations with large values.

#### Examples

Example 5-53 Using the Default MODGAMMA Value

The following statements specify a trace for a model called` income.bud`, specify that the Gauss-Seidel method should be used for solving simultaneous blocks, limit a dimension, and run the model.

    MODTRACE = YES
    MODSIMULTYPE = 'GAUSS'
    LIMIT division TO 'Camping'
    income.bud budget

These statements produce the following output.

    (MOD= INCOME.BUD) BLOCK 1: SIMULTANEOUS 
       ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 16) = 0.026243533
         ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 17) = 0.024054312
       ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 18) = 0.025788293
       ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 19) = 0.024390642
        ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 20) = 0.025501664
        ...
    (MOD= INCOME.BUD) BUDGET (LINE NET.INCOME MONTH 'JAN97' ITER 21) = 0.024608562

In the trace, you can see the results that were calculated for the NET.INCOME line item in the final six iterations over a block of simultaneous equations.

The value of MODTOLERANCE is its default value of `3`. Consequently, for an equation to pass the convergence test, its comparison value must be less than `.001`.

MODGAMMA is set to its default value of `1`. The equation for the NET.INCOME line item passed the convergence test in the twenty-first iteration. The comparison value for `Net.Income` in the twenty-first iteration was calculated as follows.

    (0.024608562967 - 0.025501664970 = 0.00087) / (0.025501664970 + 1)

Example 5-54 Setting MODGAMMA to Speed up the Convergence of a Model

The following statements change the MODGAMMA setting and run the `income.bud` model.

    MODGAMMA = 2
    income.bud budget

With MODGAMMA set to `2`, the equation for `Net.Income` converges in the eighteenth iteration. The comparison value for `Net.Income` in the eighteenth iteration is calculated as follows.

    (0.025788293304 - 0.024054312748 = 0.00086) / (0.024054312748 + 2)

### 5.52 MODINPUTORDER

The MODINPUTORDER option controls whether the equations in a simultaneous block of a model are executed in the order in which you place them or in an order determined by the model compiler. MODINPUTORDER has no effect on the order of equations in simple blocks and step blocks.

**Note:**

"Model Options" for descriptions of all of the options that control the solution of simultaneous blocks.

#### Data Type

BOOLEAN

#### Syntax

MODINPUTORDER = {YES\|NO}

#### Parameters

YES
The equations in a simultaneous block of a model are executed in the order in which they appear in the model.

NO
(Default) The equations in a simultaneous block are executed in an order determined by the model compiler.

#### Examples

Example 5-55 Using the Default Order

The following statements define the `income.calc` model.

    DEFINE income.calc MODEL
    MODEL
    DIMENSION line month
    Net.Income = Opr.Income - Taxes
    Opr.Income = Gross.Margin - TOTAL(Marketing + Selling + R.D)
    Marketing = LAG(Opr.Income, 1, month)
    Gross.Margin = Revenue - Cogs
    END

The following statements compile the model and produce a compilation report using the MODEL.COMPRPT program.

    COMPILE income.calc
    MODEL.COMPRPT income.calc

These statements produce the following output.

    MODEL INCOME.CALC <LINE MONTH>
                 BLOCK 1 (SIMPLE)
    INCOME.CALC 5: gross.margin = revenue - cogs
                  BLOCK 2 (SIMULTANEOUS <MONTH>)
    INCOME.CALC 4: marketing = lag(opr.income, 1, month)
    INCOME.CALC 3: opr.income = gross.margin - total(marketing + selling + r.d)
                  END BLOCK 2
    INCOME.CALC 2: net.income = opr.income - taxes
                 END BLOCK 1

When you compile `income.calc` with MODINPUTORDER set to its default value of `NO`, you can see that the compiler reverses the order of the equations in the simultaneous block.

Example 5-56 Changing the MODINPUT Value

The following statements set the value of MODINPUTORDER to `YES`, compile the model, and produce a compilation report.

    MODINPUTORDER = YES
    COMPILE income.calc
    MODEL.COMPRPT income.calc

These statements produce the following output.

    MODEL INCOME.CALC <LINE MONTH>
                    BLOCK 1 (SIMPLE)
    INCOME.CALC 5: gross.margin = revenue - cogs
                     BLOCK 2 (SIMULTANEOUS <MONTH>)
    INCOME.CALC 3:  opr.income = gross.margin - total(marketing + selling + r.d)
    INCOME.CALC 4:  marketing = lag(opr.income, 1, month)
                     END BLOCK 2
    INCOME.CALC 2: net.income = opr.income - taxes
                    END BLOCK 1

You can see that the compiler leaves the simultaneous equations in the order in which you placed them.

### 5.53 MODMAXITERS

The MODMAXITERS option determines the maximum number of iterations Oracle OLAP performs in attempting to solve a block of simultaneous equations in a model.

**Note:**

"Model Options" for descriptions of all of the options that control the solution of simultaneous blocks, and

#### Data Type

INTEGER

#### Syntax

MODMAXITERS = {n\|50}

#### Parameters

n
A positive `INTEGER` value that indicates the maximum number of iterations Oracle OLAP should perform in attempting to solve a simultaneous block. The default is `50`.

#### Usage Notes

Reporting Model Execution Results

When any equation in a simultaneous block diverges or fails to converge within the number of iterations specified by MODMAXITERS, the solution of the block fails and an error occurs. You can use the MODEL.XEQRPT program to produce a report on the results of the model's execution. The report indicates whether a simultaneous block diverged or failed to converge. When a block failed to converge, you can experiment with increasing the value of MODMAXITERS to see if convergence can be attained.

#### Examples

Example 5-57 Model with MODMAXITERS

Suppose a model named MYMODEL contains a block of simultaneous equations that failed to converge within 50 iterations. The following statements increase the value of MODMAXITERS and run the model again.

    MODMAXITERS = 100
    myModel actual

### 5.54 MODOVERFLOW

The MODOVERFLOW option is used in testing whether any equation in a simultaneous block of a model has diverged. MODOVERFLOW determines how dissimilar the results of an equation must be in successive iterations for the equation to be considered to have diverged.

**Note:**

"Model Options" for a list of all of the options that control the solution of simultaneous blocks.

#### Data Type

INTEGER

#### Syntax

MODOVERFLOW = {n\|3}

#### Parameters

n
An `INTEGER` value to use in testing for divergence. As Oracle OLAP calculates each equation in a simultaneous block, it constructs a comparison value that is based on the results of the equation for the current iteration and the previous iteration. When the comparison value meets a divergence test, the equation is considered to have diverged.

The comparison value that is tested is as follows.

(thisResult - prevResult) / (prevResult + MODGAMMA)

where` thisResult` is the result of this iteration and `prevResult` is the result of the previous iteration

In the preceding calculation, MODGAMMA is an INTEGER option that controls the degree to which the comparison value represents the absolute amount of change between iterations versus the proportional change. The default value of MODGAMMA is `1`.

In the divergence test, Oracle OLAP tests whether the comparison value is greater than `10` to the power of MODOVERFLOW. The calculation for this test is as follows.

    Comparison value  >  10**MODOVERFLOW

For the equation to be considered to have diverged, the comparison value must meet the test described earlier. The default value of MODOVERFLOW is `3`. With this default, the comparison value meets the test when it is greater than `1000`.

#### Usage Notes

Equation Divergence

When an equation diverges, an error occurs. The MODERROR option controls the action that Oracle OLAP takes when an error occurs.

Faster Divergence During Development

While you are developing a model, you can sometimes save time by using a small value for MODOVERFLOW. When Oracle OLAP is performing many iterations over a particular simultaneous block, a smaller value of MODOVERFLOW can cause rapid divergence of that block. When you set the MODOVERFLOW option to `CONTINUE`, execution of the model continues when the divergence occurs, and you can concentrate on debugging the other blocks in the model. After you have debugged the model, you can use a larger value for MODOVERFLOW.

#### Examples

Example 5-58 Using the Default MODOVERFLOW Value

The following statements specify a trace for a model called `income.est`, limit a dimension, and run the model.

    MODTRACE = YES
    LIMIT division TO 'Camping'
    income.est budget

These statements produce the following output.

    (MOD= INCOME.EST) BLOCK 1: SIMULTANEOUS 
    (MOD= INCOME.EST) ITERATION 1: EVALUATION
    (MOD= INCOME.EST) selling = marketing * 3
    (MOD= INCOME.EST) BUDGET (LINE SELLING MONTH 'JAN97' ITER 1) = 3
      ...
    (MOD= INCOME.EST) BUDGET (LINE SELLING MONTH 'JAN97' ITER 2) = -997
       ...
    (MOD= INCOME.EST) BUDGET (LINE SELLING MONTH 'JAN97' ITER 3) = 6.00902708124
       ...
    (MOD= INCOME.EST) BUDGET (LINE SELLING MONTH 'JAN97' ITER 49) = 34.2715693388
       ...
    (MOD= INCOME.EST) BUDGET (LINE SELLING MONTH 'JAN97' ITER 50) = -7.22300601861

In the trace, you can see the results that were calculated for the `Selling` line item in the first three iterations and the forty-ninth and fiftieth iterations over a block of simultaneous equations. The block failed to converge after 50 iterations.

The value of MODOVERFLOW is its default value of `3`. Consequently, for an equation to meet the divergence test, its comparison value must be greater than `1000`.

Example 5-59 Speeding Up the Divergence

The following statements change the MODOVERFLOW setting and run the `income.est` model.

    MODOVERFLOW = 2
    income.est budget

With MODOVERFLOW set to `2`, any comparison value of more than 100 meets the test for divergence. In this example, the equation for `Selling` meets the test in the second iteration. In the second iteration, Oracle OLAP calculates the comparison value for `Selling` as follows.

    (-997 - 3) / (3 + 1) = 250

Because this comparison value is greater than 100, the equation for `Selling` diverges in the second iteration.

### 5.55 MODSIMULTYPE

The MODSIMULTYPE option specifies the method to use for solving simultaneous blocks in a model.

**Note:**

"Model Options" for a list of all of the options that control the solution of simultaneous blocks.

#### Data Type

ID

#### Syntax

MODSIMULTYPE = {'AITKENS'\|'GAUSS'}

#### Parameters

'AITKENS'
(Default) Oracle OLAP uses the Aitkens delta-squared solution method. In the first two of every three iterations over a block of simultaneous equations, the equations are solved using the values from the previous iteration, and the results are tested for convergence and divergence. In every third iteration, the results are obtained not by solving the equations, but by making a next-guess calculation. This calculation uses the results of the previous three iterations. The results of the guesses are not tested for convergence and divergence, and the solution always continues to the next iteration.

'GAUSS'
Oracle OLAP uses the Gauss-Seidel solution method. Equations in a simultaneous block are solved in each iteration over the block. The results are tested for convergence and divergence in each iteration.

#### Usage Notes

Solving Simultaneous Blocks

Oracle OLAP uses an iterative method to solve the equations in a simultaneous block. In each iteration, except the next-guess iterations in an Aitkens solution, a comparison value is calculated from the result of the current iteration and the result of the previous iteration. When the comparison value falls within a specified tolerance (see the MODTOLERANCE option), the equation is considered to have converged. When the comparison value is too great (see the MODOVERFLOW option), the equation is considered to have diverged and solution of the block ends.

When all equations in a block converge, the block is considered solved. When any equation diverges or when any equation fails to converge after a specified number of iterations (see the MODMAXITERS option), solution of the block (and of the model) fails and Oracle OLAP generates an error.

Next-Guess Calculation

The Aitkens method requires three values to perform a next-guess calculation. Therefore, in the first three iterations over a simultaneous block, Oracle OLAP solves the equations. The fourth iteration is a next-guess iteration that uses the results from the first three iterations in its calculation.

Thereafter, every third iteration is a next-guess iteration that calculates results by using the previous guess and the equation results from the intervening two iterations. For example, the seventh iteration makes a next-guess calculation that is based on the guess from the fourth iteration and the equation results from the fifth and sixth iterations.

Memory Required

The Aitkens method usually speeds convergence, and it generally produces more accurate results than the Gauss-Seidel method. However, the Aitkens method requires more memory because the results of three previous iterations are stored.

In general, use the Aitkens method. Use the Gauss-Seidel method only when limited memory is a problem on your system.

Handling NA Values When Solving Simultaneous Blocks in a Model

In calculating equation results and making next-guess calculations, Oracle OLAP observes the setting of the NASKIP2 option. NASKIP2 controls how `NA` values are handled when `+` (plus) and `-` (minus) operations are performed. The setting of NASKIP2 is important when you specify a solution variable that contains `NA` values. Because the values in the solution variable are used as the initial values in the first iteration over a simultaneous block, the results of the equations might be `NA` when there are `NA` values in the solution variable. An `NA` result in the first iteration might also produce `NA` results in later iterations. Therefore, to avoid obtaining `NA` for the results, you can ensure that the solution variable does not contain `NA` values or you can set NASKIP2 to `YES` before running the model.

Data Type Problems

A simultaneous equation might fail to converge when it assigns data to a variable with an INTEGER data type or when you specify a solution variable with an INTEGER data type for a dimension-based model. Oracle OLAP converts the data to decimal values when it calculates the equation in each iteration, but the results are stored in the INTEGER variable between iterations which has the effect of rounding the values and thereby interfering with a progression toward convergence.

Function Problems

A simultaneous equation might fail to converge when it contains a function that produces rounded values (such as INSTRB or ROUND) or when it contains a function that introduces discontinuities in the data (such as MAX or MIN).

Starting-Value Problems

The solution of a simultaneous block is sensitive to starting values. For example, when a model has a proportional relationship between two model values, then starting values close to zero inhibits convergence. Consequently, attempt to use starting values that are reasonable for the equations being solved.

Order of Equations

The solution of a simultaneous block is also sensitive to the order of the equations. When you compile a model, the model compiler determines an optimal equation order that is based on the dependencies among the equations.

To force the equations in a simultaneous block to be solved in a particular order, you can write the equations in the desired order and set the MODINPUTORDER option to `YES` before compiling the model. When MODINPUTORDER is `YES`, the model compiler leaves the equations in a simultaneous block in the order in which they appear in the model.

By placing simultaneous equations in a particular order and setting MODINPUTORDER to `YES` before compiling the model, you might be able to encourage convergence in some models. In general, however, it is preferable to rely on the model compiler to order the equations.

Producing an Execution Report

After running a model, you can use the MODEL.XEQRPT program to produce a report about the execution of the model.

#### Examples

Example 5-60 Economizing on Memory Requirements

When a model named `budget98` is a complex model that iterates over a large number of dimension values in a simultaneous block, you can economize on the memory requirements of the model solution by using the Gauss-Seidel method.

The following statements specify the Gauss-Seidel method and run the model.

    MODSIMULTYPE = 'GAUSS'
    budget98 budget

### 5.56 MODTOLERANCE

The MODTOLERANCE option is used in testing whether each equation in a simultaneous block of a model has converged. MODTOLERANCE determines how closely the results of an equation must match between successive iterations for the equation to be considered to have converged.

#### Data Type

INTEGER

#### Syntax

MODTOLERANCE = {n\|3}

#### Parameters

n
An `INTEGER` value to use in testing for convergence. As Oracle OLAP calculates each equation in a simultaneous block, it constructs a comparison value that is based on the results of the equation for the current iteration and the previous iteration. When the comparison value passes a tolerance test, the equation is considered to have converged.

The comparison value that is tested is as follows.

    (thisResult - prevResult) / (prevResult+ MODGAMMA)

where thisResult is the result of this iteration and prevResult is the result of the previous iteration

In the preceding calculation, MODGAMMA is an INTEGER option that controls the degree to which the comparison value represents the absolute amount of change between iterations versus the proportional change. The default value of MODGAMMA is 1.

In the tolerance test, Oracle OLAP tests whether the comparison value is less than `10` to the negative power of MODTOLERANCE. The calculation for this test is as follows.

    Comparison value  <  10**-MODTOLERANCE

An equivalent way of writing this calculation is as follows.

    Comparison value  < (1 / (10**MODTOLERANCE))

For the equation to be considered to have converged, the comparison value must meet the test described earlier. The default value of MODTOLERANCE is `3`. With this default, the comparison value meets the test when it is less than `0.001`.

#### Usage Notes

Failure to Converge

When an equation fails to converge after a specified number of iterations, an error occurs. The MODMAXITERS option controls the maximum number of iterations that are attempted. The MODERROR option controls the action that Oracle OLAP takes when an error occurs.

Precision of Results

Because MODTOLERANCE controls how closely results of an equation must match between iterations, it therefore controls the precision of the results of the solution. A small value of MODTOLERANCE results in less precision, while a large value provides more precision.

Large and Small Values

When a model contains some equations with large values and some equations with very small values, it might be preferable to increase the value of the MODGAMMA option rather than decreasing MODTOLERANCE. By increasing MODGAMMA, you might be able to force equations with small values to converge more quickly while retaining the precision of equations with large values.

Faster Convergence During Development

While you are developing a model, you might want to use a small value for MODTOLERANCE. While this gives less precise results, the model equations converges more quickly. After you have debugged the model, you can increase the value of MODTOLERANCE and thereby increase the precision of the final results.

Options for Controlling the Solution of Simultaneous Blocks

For a list of all the options that you can use to control the solution of simultaneous blocks, see "Model Options".

#### Examples

Example 5-61 Using the Default MODTOLERANCE Value

The following statements specify a trace for a model called` income.plan`, specify that the Gauss-Seidel method should be used for solving simultaneous blocks, limit a dimension, and run the model.

    MODTRACE = YES
    MODSIMULTYPE = 'GAUSS'
    LIMIT division TO 'Camping'
    income.plan budget

These statements produce the following output.

    (MOD= INCOME.PLAN) BLOCK 1: SIMULTANEOUS 
    (MOD= INCOME.PLAN) ITERATION 1: EVALUATION
    (MOD= INCOME.PLAN) marketing = .15 * net.income
    (MOD= INCOME.PLAN) BUDGET(LINE MARKETING MONTH 'JAN97' ITER 1) = 11887.403671736
      ...
    (MOD= INCOME.PLAN) BUDGET(LINE MARKETING MONTH 'JAN97' ITER 6) = 73379.713232251
        ...
    (MOD= INCOME.PLAN) BUDGET(LINE MARKETING MONTH 'JAN97' ITER 7) = 73474.784648631
        ...
    (MOD= INCOME.PLAN) BUDGET(LINE MARKETING MONTH 'JAN97' ITER 8) = 73446.025848156
    (MOD= INCOME.PLAN) END BLOCK 1

In the trace, you can see the results that were calculated for the `Marketing` line item in the final three iterations over a block of simultaneous equations.

MODTOLERANCE is set to its default value of `3`. Consequently, for an equation to pass the convergence test, its comparison value must be less than `0.001`. In the seventh iteration, Oracle OLAP calculates the comparison value for `Marketing` as follows.

    (73474.784648631100 - 73379.713232251300) / (73379.713232251300 + 1) = 0.0013

This comparison value is greater than `0.001`, so it did not pass the test for convergence.

In the eighth iteration, Oracle OLAP calculated the comparison value as follows.

    (73446.025848156700 - 73474.784648631100) /(73474.784648631100 + 1) = 0.0004

Because this comparison value is less than `0.001`, it passed the convergence test.

Example 5-62 Setting MODTOLERANCE to Speed Up the Convergence of a Model

The following statements change the MODTOLERANCE value and run the `income.bud` model.

    MODTOLERANCE = 2
    income.plan budget

With MODTOLERANCE set to `2`, any comparison value of less than `0.01` passes the test for convergence. In this example, the equation for `Marketing` passes the test in the seventh iteration.

### 5.57 MODTRACE

The MODTRACE option controls whether each equation in a model is recorded in a file during execution of the model. MODTRACE is used primarily as a debugging tool to uncover problems by tracing the execution of a model.

**Tip:**

The INFO function lets you obtain specific items of information about the structure of the compiled model and the solution status of a model you have run. See [INFO (MODEL)](olap-dml-functions-a-k.md).

#### Data Type

BOOLEAN

#### Syntax

MODTRACE = {YES\|NO}

#### Parameters

YES
Oracle OLAP sends the text of each model equation to the current outfile before calculating the model equation, and then sends the results of the calculation to the current outfile.

When you have used a DBGOUTFILE statement to specify a debugging file, Oracle OLAP sends MODTRACE output to the debugging file instead of the current outfile.

NO
(Default) Oracle OLAP does not send the text of model equations and results to a file while a model executes.

#### Usage Notes

Previewing the Solution Order

MODTRACE sends the equations of a model to the current outfile in the order in which they are being solved. Before you run the model, you might want to use the MODEL.COMPRPT program to get a preview of the solution order. A preview can be especially helpful when the model is large and complex. The `MODEL.COMPRPT` program, which you can run after compiling a model, produces a report that shows how the compiler has organized the model equations into blocks and the order in which the blocks and equations are solved.

Understanding Trace Information

MODTRACE shows the name of the current model on each line of the trace. The trace includes the following types of lines.

- Block. A block line gives the block number and block type of the block that is about to be executed. The type of block can be simple, step-forward, step-backward, or simultaneous. For a step-forward or step-backward block, the block line specifies the dimension being stepped over. For a simultaneous block with a cross-dimensional dependency, the block line specifies the dimensions involved in the dependency. See [MODEL](olap-dml-commands-h-z.md) command for information on blocks in a model.

- Iteration. These lines occur in simultaneous blocks and specify the number of the iteration that is about to be performed for the current block. When you are using the Aitkens solution method, the next-guess iterations are identified. (The MODSIMULTYPE option determines the solution method being used.)

- Equation. The equation that is about to be calculated.

- Results. A results line follows each equation line and shows the results assigned by the equation. It shows the variable to which the results were assigned and the current value of each model dimension. In a simultaneous block, it also shows the current iteration number. For example, when `actual` is the solution variable and the model dimensions are `line` and `month`, a results line in a simultaneous block might look like the following one.

      (MOD= INCOME.CALC) ACTUAL (LINE OPR.INCOME MONTH 'JAN96'
         ITER 1) = 108.9600000

<!-- -->

Using MODTRACE with Dimension-Based Equations

When you run a model that contains dimension-based equations, Oracle OLAP automatically loops over all the dimensions of the solution variable. In the trace, the results lines show the current value of each dimension listed in a DIMENSION statement, but they do not show the current values of extra dimensions that are not listed in DIMENSION statement. See [DIMENSION (in models)](olap-dml-commands-h-z.md) for more information about using DIMENSION statements.

Thus, when the model dimensions are `line` and `month`, and when the solution variable is dimensioned by `line`, `month`, and `division`, the current value of `division` is not shown in the results lines. Oracle OLAP executes the entire model for the first value in the status of `division`, then for the second value in the status, and so on.

When you run a model that assigns values to variables, Oracle OLAP automatically loops over all the dimensions (or bases of a composite) of those variables. In this case, the current value of each of the variable's dimensions is shown in the trace.

#### Examples

Example 5-63 Debugging a Model with MODTRACE

The following statements define a model named `income.budget`.

    DEFINE income.budget MODEL
    LD Model for estimating budget items
    MODEL
    DIMENSION line month
    Opr.Income = Gross.Margin - Marketing
    Gross.Margin = Revenue - Cogs
    Revenue = LAG(Revenue, 1, month) * 1.02
    Cogs = LAG(Cogs, 1, month) * 1.01
    Marketing = LAG(Opr.Income, 1, month) * 0.20
    END

This model estimates budget line items on an income statement. The model equations are based on a `line` dimension. The following statements compile the model and run the MODEL.COMPRPT program.

    COMPILE income.budget
    MODEL.COMPRPT income.budget

The `MODEL.COMPRPT` statement produces the following compilation report.

    MODEL INCOME.BUDGET <LINE MONTH>
                       BLOCK 1 (SIMPLE)
    INCOME.BUDGET  4:  revenue = lag(revenue, 1, month) * 1.02
    INCOME.BUDGET  5:  cogs = lag(cogs, 1, month) * 1.01
    INCOME.BUDGET  3:  gross.margin = revenue - cogs
                        BLOCK 2 (STEP-FORWARD <MONTH>)
    INCOME.BUDGET  6:   marketing = lag(opr.income, 1, month) * 0.20
    INCOME.BUDGET  2:   opr.income = gross.margin - marketing
                        END BLOCK 2
                       END BLOCK 1

When you want to debug this model, you can trace its execution, line by line, by turning on MODTRACE before running the model.

The following statements limit dimensions, specify tracing, and run the model.

    LIMIT month TO 'Jan97' TO 'Mar97'
    LIMIT division TO 'Camping'
    MODTRACE = YES
    income.budget budget

These statements produce the following line-by-line results.

    (MOD= INCOME.BUDGET) BLOCK 1: SIMPLE 
    (MOD= INCOME.BUDGET) revenue = lag(revenue, 1, month) * 1.02
    (MOD= INCOME.BUDGET) BUDGET (LINE REVENUE MONTH 'JAN97') = 744491.1966
    (MOD= INCOME.BUDGET) BUDGET (LINE REVENUE MONTH 'FEB97') = 759381.020532
    (MOD= INCOME.BUDGET) BUDGET (LINE REVENUE MONTH 'MAR97') = 774568.64094264
    (MOD= INCOME.BUDGET) cogs = lag(cogs, 1, month) * 1.01
    (MOD= INCOME.BUDGET) BUDGET (LINE COGS MONTH 'JAN97') = 382386.2323
    (MOD= INCOME.BUDGET) BUDGET (LINE COGS MONTH 'FEB97') = 386210.094623
    (MOD= INCOME.BUDGET) BUDGET (LINE COGS MONTH 'MAR97') = 390072.19556923
    (MOD= INCOME.BUDGET) gross.margin = revenue - cogs
    (MOD= INCOME.BUDGET) BUDGET (LINE GROSS.MARGIN MONTH 'JAN97') = 362104.9643
    (MOD= INCOME.BUDGET) BUDGET (LINE GROSS.MARGIN MONTH 'FEB97') = 373170.925909
    (MOD= INCOME.BUDGET) BUDGET (LINE GROSS.MARGIN MONTH 'MAR97') = 384496.44537341
    (MOD= INCOME.BUDGET) BLOCK 2 STEP-FORWARD <MONTH>
    (MOD= INCOME.BUDGET) marketing = lag(opr.income, 1, month) * 0.20
    (MOD= INCOME.BUDGET) BUDGET (LINE MARKETING MONTH 'JAN97') = 39938.192
    (MOD= INCOME.BUDGET) opr.income = gross.margin - marketing
    (MOD= INCOME.BUDGET) BUDGET (LINE OPR.INCOME MONTH 'JAN97') = 322166.7723
    (MOD= INCOME.BUDGET) marketing = lag(opr.income, 1, month) * 0.20
    (MOD= INCOME.BUDGET) BUDGET (LINE MARKETING MONTH 'FEB97') = 64433.35446
    (MOD= INCOME.BUDGET) opr.income = gross.margin - marketing
    (MOD= INCOME.BUDGET) BUDGET (LINE OPR.INCOME MONTH 'FEB97') = 308737.571449 
    (MOD= INCOME.BUDGET) marketing = lag(opr.income, 1, month) * 0.20
    (MOD= INCOME.BUDGET) BUDGET (LINE MARKETING MONTH 'MAR97') = 61747.5142898
    (MOD= INCOME.BUDGET) opr.income = gross.margin - marketing
    (MOD= INCOME.BUDGET) BUDGET (LINE OPR.INCOME MONTH 'MAR97') = 322748.93108361
    (MOD= INCOME.BUDGET) END BLOCK 2
    (MOD= INCOME.BUDGET) END BLOCK 1

In Block 1, which is a simple block, Oracle OLAP solved the equations one at a time, looping over the three values in the status of `month` as it solved each equation. In Block 2, which is a step-forward block over the `month` dimension, Oracle OLAP stepped over the values in the status of `month`, solving all the equations in the block for each month in turn.

### 5.58 MONTHABBRLEN

The MONTHABBRLEN option specifies the number of characters to use for abbreviations of month names that are stored in the MONTHNAMES option. You can specify how many characters to use for abbreviating particular month names when you specify the `<MT>`,` <MTXT>`, and `<MTXTL>` formats with the DATEFORMAToption or a [VNF](olap-dml-commands-h-z.md) (value name format) specified for a dimension of type dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR.

#### Data Type

TEXT

#### Syntax

MONTHABBRLEN = specification \[;\|, specification\]... 

where `specification` is a text expression that has the following form:

     startpos \[ - endpos\] : length

#### Parameters

startpos \[-endpos\]
Numbers that represent the first and last months whose abbreviation length is defined by length. These numeric positions apply to the corresponding lines of text in the MONTHNAMES option. You can specify these ranges of values in reverse order, endpos \[-startpos\], if you prefer.

The MONTHNAMES option can have more than 12 lines, so you can specify startpos and endpos greater than 12 in the setting of MONTHABBRLEN. When you specify a range where neither startpos nor endpos has a corresponding text value in the MONTHNAMES option, MONTHABBRLEN has no text values to abbreviate for that range. When you later change your month names list so that startpos is valid, the specified abbreviation is applied.

length
A number that specifies the length in characters (not bytes) of abbreviated month names. When you do not specify an abbreviation length for a given position in the MONTHNAMES option, or when you explicitly set a given position to zero, the default abbreviation is used. The default abbreviations are one character for `<MT>` and three characters for `<MTXT>` and `<MTXTL>`. Abbreviations are never used when you have designated the full name specifications `<MTEXT>` and `<MTEXTL>`.

#### Usage Notes

Ambiguous Month Names

You can use MONTHABBRLEN to interpret ambiguous names, for example, whether `A` stands for `April` or `August`. When the MONTHABBRLEN for April was `1` and for August was `2`, then `A` would always match `April`, and it would require at least `Au` to match `August`. This interpretation does not depend on the order of `April` and `August` in the year; it would work the same way when the two months were reversed. If, on the other hand, the MONTHABBRLEN for each of these was `2`, then `A` would not match either one, and you would have to enter at least `Ap` or `Au` to get a match.

#### Examples

Example 5-64 Specifying Month Abbreviations

The following MONTHABBRLEN setting specifies that the first 10 months of the year are abbreviated to one character and the last 2 months are abbreviated to two characters.

    MONTHABBRLEN = '1-10:1, 11-12:2'
    SHOW CONVERT ('2 August 2005' DATE)

These statements product the following result, with August abbreviated to the letter A.

    02A05

### 5.59 MONTHNAMES

The MONTHNAMES option holds the list of valid names for months that is used in handling values with a DATE-only data type and values of dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR. The list of names is used to interpret dates that are entered and to format dates that are displayed or converted to text values.

The MONTHNAMES list is used when you enter a date that includes a month name or abbreviation. See the DATEFORMAT option for a discussion of methods for entering DATE-only values. The MONTHNAMES list is also used when you display or convert a date using the `<MT>`, `<MTXT>`, `<MTXTL>`, `<MTEXT>`, or `<MTEXTL>` formats. These formats are specified in the DATEFORMAT option. When you have multiple sets of month names, Oracle OLAP chooses the synonym whose number of characters and capitalization pattern best match the DATEFORMAT specification.

**See Also:**

MONTHABBRLEN option

#### Data Type

TEXT

#### Syntax

MONTHNAMES = name-list

#### Parameters

name-list
A multiline text expression that lists the names of the 12 months of the year. Each month name occupies a separate line. Regardless of which month you are treating as the first month of the year, the list must begin with the name for January. The default value is the list of English month names, all in capital letters.

You can include more than 1 set of 12 names in your list. Any name in the list is considered a valid name for input. The thirteenth name is a synonym for the first name, the fourteenth name is a synonym for the second name, and so on.

#### Examples

Example 5-65 Specifying Two Sets of Month Names

The following statement creates two sets of month names, one in uppercase English and the second in lowercase French.

    MONTHNAMES = -
    'JANUARY -
    ...
    DECEMBER -
    janvier -
    ...
    decembre'

Example 5-66 Specifying English Month Names

The following statements define a DATE-only variable, assign a value to that variable, assign a setting to DATEFORMAT, and send the output to the current outfile. The DATEFORMAT value includes `<MTEXT>`, which specifies uppercase, so the English month names are used.

    DEFINE datevar DATE
    datevar = '27feb98'
    DATEFORMAT = '<MTEXT> <D>, <YYYY>'
    SHOW datevar

These statements produce the following output.

    FEBRUARY 27, 1998

Example 5-67 Specifying French Month Names

The following statements assign a new setting to DATEFORMAT and send the output to the current outfile. The DATEFORMAT value includes `<MTEXTL>`, which specifies lowercase, so the French month names are used.

    DATEFORMAT = 'le <D> <MTEXTL> <YYYY>'
    SHOW datevar

These statements produce the following output.

    le 27 fevrier 1998

### 5.60 MULTIPATHHIER

The MULTIPATHHIER option specifies that a given cell that contains detail data can have multiple paths into a cell that contains aggregated data. Certain calculations require this kind of multiple-path aggregation.

#### Data Type

BOOLEAN

#### Syntax

MULTIPATHHIER = {YES\|NO}

#### Parameters

YES
Allows a detail data cell to aggregate in multiple paths to the same ancestor cell.

NO
(Default) Disallows a detail data cell to aggregate in multiple paths to the same ancestor cell.

#### Usage Notes

When to Use MULTIPATHHIER

The only time you set the MULTIPATHHIER option to `YES` is when a calculation requires the use of multiple paths.

Interpreting an XSHIERCK01 Error Message

When you use the AGGREGATE command, dimension hierarchies are automatically checked for circularity. When MULTIPATHHIER is set to `NO`, or when the default of `NO` has not been changed, then the following error message is displayed when a detail data cell uses multiple paths to the same aggregate data cell.

    ERROR: (XSHIERCK01) One or more loops have been detected 
    in your hierarchy n over N. The loops include 2 items 
    (UNDIRECTED: X and Y).

In the preceding error message, `X` is the name of the detail data cell, and `Y` is the name of the ancestor cell into which the detail data cell takes multiple paths to aggregate. For more information, see Example 5-68.

This error message is displayed because the multiple paths taken by the detail data cell have been interpreted as a circular hierarchy. When this is a mistake and you did not intend to create multiple paths, then change the hierarchy. Otherwise, set the MULTIPATHHIER option to `YES`.

#### Examples

Example 5-68 Defining Multiple Paths in a Hierarchy

This example shows how you can define multiple paths in a hierarchy, the error message that results when you attempt to aggregate data, how to interpret that message, and how to resolve the problem.

The following statements create two paths from a detail data cell to an ancestor cell that contains aggregated data.

    DEFINE geog TEXT DIMENSION
    DEFINE path INTEGER DIMENSION
    DEFINE geog.geog RELATION geog <geog path>
    MAINTAIN geog ADD 'A1' 'b1' 'b2' 'Top'
    MAINTAIN path ADD 2
    geog.geog(geog 'A1' path 1) = 'B1'
    geog.geog(geog 'A1' path 2) = 'B2'
    geog.geog(geog 'B1' path 1) = 'Top'
    geog.geog(geog 'B2' path 1) = 'Top'

First, a geography dimension named `geog` and a second dimension named `path` are defined.

A relation named `geog.geog` is defined, in which the geography dimension is dimensioned by itself and the `path` dimension.

Dimension values named `A1`, `B1`, `B2`, and `Top` are added to the `geog` dimension.

Two dimension values are added to the `path` dimension. Because `path` was defined with an `INTEGER` data type, the dimension values that are automatically assigned to it are the `INTEGER` values `1` and `2`.

Finally, the hierarchy for the `geog` dimension is created. The `A1` dimension value is the detail data. The `B1` and `B2` dimension values are the second level of the hierarchy. The `Top` dimension value is the top of the hierarchy.

`A1` has two aggregation paths: `A1` aggregates into `B1`, which aggregates into `Top`; `A1` aggregates into `B2`, which aggregates into `Top`.

The following statements define a variable named `myvar`, assign a data value of `1` to its detail data level (`A1`), and define an aggmap for that variable.

    DEFINE myvar INTEGER VARIABLE <geog>
    myvar(geog 'A1') = 1
    DEFINE myvar.aggmap <geog>
    AGGMAP 'RELATION geog.geog'

An attempt to aggregate `myvar` generates the following error message.

    AGGREGATE myvar USING myvar.aggmap
    ERROR: (XSHIERCK01) One or more loops have been detected 
    in your hierarchy GEOG.GEOG over GEOG. The loops include 2 
    items (UNDIRECTED: A1 and TOP).

The multiple paths of aggregation that have been created for `A1` have been interpreted as a circular hierarchy, because the MULTIPATHHIER option is currently set to `NO`.

When you had made a mistake and created these multiple paths by mistake, you would fix the problem in the hierarchy.

However, in this case, the multiple paths have been created because a calculation requires them. Therefore, the solution is to set MULTIPATHHIER to `YES`. Now you can execute the AGGREGATE command without error.

### 5.61 NASKIP

The NASKIP option controls whether `NA` values are considered as input to aggregation functions.

**See Also:**

[\$NATRIGGER](olap-dml-properties.md) property, NASKIP2 option which controls how `NA` values are treated with the `+` (plus) and `-` (minus) operators, and NASPELL option.

#### Data Type

BOOLEAN

#### Syntax

NASKIP = NO\|YES

#### Parameters

NO
(Default) `NA` values are considered by aggregation functions. When any of the values being considered are `NA`, the function returns `NA` for that value.

YES
`NA` values are ignored by aggregation functions. Only expressions with actual values are used in calculations.

#### Usage Notes

Statements Affected by NASKIP

The following OLAP DML statements are affected by NASKIP.

- AGGREGATE command
- AGGREGATE function
- ANY
- AVERAGE
- COUNT
- CUMSUM
- DEPRDECL
- DEPRDECLSW
- DEPRSL
- DEPRSOYD
- EVERY
- FINTSCHED
- FPMTSCHED
- IRR
- LARGEST
- MEDIAN
- MOVINGAVERAGE
- MOVINGMAX
- MOVINGMIN
- MOVINGTOTAL
- NONE
- NPV
- SMALLEST
- STDDEV
- TCONVERT
- TOTAL
- VINTSCHED
- VPMTSCHED
-

Other statements are not affected by the setting of NASKIP, they always ignore `NA` values.

#### Examples

Example 5-69 The Effect of NASKIP on the TOTAL Function

In the `demo` workspace, the 1997 values for sales are `NA`. The TOTAL function returns different results depending on the setting of NASKIP.

The statements

    ALLSTAT
    NASKIP = YES
    SHOW TOTAL(sales)

produce the following result.

    63,181,743.50

In contrast, the OLAP DML statements

    NASKIP = NO
    SHOW TOTAL(sales)

produce the following result.

    NA

Example 5-70 The Effect of NASKIP on the MOVINGMIN Function

This example aggregates values for three months: the current month and the two months before it. The first report of SALES shows the `NA` values for months in 1997. When NASKIP is `YES`, the MOVINGMIN function returns `NA` only for March 1997 because all the values considered for that month were `NA`. When NASKIP is `NO`, the third statement (`REPORT` `DOWN` `month` `sales`) shows `NA` values for January through March 1997, because at least one value considered by MOVINGMIN for those months was `NA`.

    LIMIT district TO 'Seattle'
    LIMIT month TO 'Jul96' TO 'Mar97'
    REPORT DOWN month sales

The preceding statements produce the following report of SALES data.

    DISTRICT: SEATTLE
          ------------------------SALES-------------------------
          -----------------------PRODUCT------------------------
    MONTH   Tents      Canoes    Racquets  Sportswear  Footwear
    ----- ---------- ---------- ---------- ----------  ---------
    Jul96 123,700.17 157,274.03  60,198.52  78,305.97  78,019.87
    Aug96 120,650.72 128,660.89  45,046.71  66,853.26  83,347.55
    Sep96  97,188.43 122,702.13  42,257.14  63,777.36  99,464.05
    Oct96  91,578.77  79,925.93  39,729.25  55,021.85  83,537.58
    Nov96  56,044.34  77,357.10  39,024.93  44,004.12  65,216.94
    Dec96  41,576.26  67,609.36  36,156.10  40,575.34  62,113.72
    Jan97         NA         NA         NA         NA         NA
    Feb97         NA         NA         NA         NA         NA
    Mar97         NA         NA         NA         NA         NA

The statements

    NASKIP = YES
    REPORT DOWN month MOVINGMIN(sales -2, 0, 1, month)

produce the following report, which shows `NA` values for March 1997.

    DISTRICT: SEATTLE
          -----------MOVINGMIN(SALES -2, 0, 1, MONTH)-----------
          ---------------------PRODUCT--------------------------
    MONTH   Tents      Canoes    Racquets  Sportswear  Footwear
    ----- ---------- ---------- ---------- ----------  ---------
    Jul96 108,663.59 125,823.37 57,666.37  57,713.27   73,085.88
    Aug96 119,066.18 128,660.89 45,046.71  60,322.88   78,019.87
    Sep96  97,188.43 122,702.13 42,257.14  63,777.36   78,019.87
    Oct96  91,578.77  79,925.93 39,729.25  55,021.85   83,347.55
    Nov96  56,044.34  77,357.10 39,024.93  44,004.12   65,216.94
    Dec96  41,576.26  67,609.36 36,156.10  40,575.34   62,113.72
    Jan97  41,576.26  67,609.36 36,156.10  40,575.34   62,113.72
    Feb97  41,576.26  67,609.36 36,156.10  40,575.34   62,113.72
    Mar97         NA         NA         NA         NA         NA

The statements

    NASKIP = NO
    REPORT DOWN month MOVINGMIN(sales -2, 0, 1, month)

produce the following report, which shows `NA` values for January through March 1997.

    DISTRICT: SEATTLE
          ----------MOVINGMIN(SALES -2, 0, 1, MONTH)-------------
          ------------------------PRODUCT------------------------
    MONTH   Tents      Canoes    Racquets  Sportswear  Footwear
    ----- ---------- ---------- ---------- ----------  ----------
    Jul96 108,663.59 125,823.37  57,666.37  57,713.27   73,085.88
    Aug96 119,066.18 128,660.89  45,046.71  60,322.88   78,019.87
    Sep96  97,188.43 122,702.13  42,257.14  63,777.36   78,019.87
    Oct96  91,578.77  79,925.93  39,729.25  55,021.85   83,347.55
    Nov96  56,044.34  77,357.10  39,024.93  44,004.12   65,216.94
    Dec96  41,576.26  67,609.36  36,156.10  40,575.34   62,113.72
    Jan97         NA         NA         NA         NA          NA
    Feb97         NA         NA         NA         NA          NA
    Mar97         NA         NA         NA         NA          NA

### 5.62 NASKIP2

The NASKIP2 option controls how `NA` values are treated in arithmetic operations with the `+` (plus) and `-` (minus) operators. The result is `NA` when any operand is `NA` unless NASKIP2 is set to `YES`.

**See Also:**

[\$NATRIGGER](olap-dml-properties.md) property, NASKIP option, and NASPELL option.

#### Data Type

BOOLEAN

#### Syntax

NASKIP2 = YES\|NO

#### Parameters

YES
Zeroes are substituted for `NA` values in arithmetic operations using the `+` (plus) and `-` (minus) operators. The two special cases of `NA` `+` `NA` and `NA` `-` `NA` both result in `NA`.

NO
(Default) `NA` values are treated as NAs in arithmetic operations using the `+` (plus) and `-` (minus) operators. When any of the operands being considered is `NA`, the arithmetic operation evaluates to `NA`.

#### Usage Notes

Operators in Function Arguments

NASKIP2 is independent of NASKIP. NASKIP2 applies only to arithmetic operations with the `+` (plus) and `-` (minus) operators. NASKIP applies only to aggregation functions. However, when an expression argument to an aggregation function contains a`+` (plus) and `-` (minus) operator, the results of the calculation depend on both NASKIP and NASKIP2. See Example 5-71.

How NASKIP2 Works

The following four lines show four steps in the evaluation of a complex expression that contains NAs when NASKIP2 is set to `YES`.

    3 * (NA + NA) - 5 * (NA + 3)
       3 * NA     -    5 *  3
         NA       -      15
                 -15

#### Examples

Example 5-71 Effects of NASKIP and NASKIP2 When an Expression in an Aggregation Function Contains a Negative Values

In the following examples, INTEGER variables `X` and `Z`, dimensioned by the INTEGER dimension INTDIM, have the values shown in the second and third columns of the report. The sum of X + Z is given for each combination of NASKIP and NASKIP2 settings, starting with their defaults. The example also shows that when the `+` (plus) operator is used in the expression argument to the TOTAL function, the results that are returned by TOTAL depend on the settings of both NASKIP and NASKIP2.

- NASKIP Set to YES, NASKIP2 Set to NO

  In this example, NASKIP is set to `YES`, which means `NA` values are ignored by the TOTAL function. NASKIP2 is set to `NO`, which means that the result of a `+` (plus) operation is `NA` when any of the operands are `NA`.

      NASKIP = YES
      NASKIP2 = NO
      COLWIDTH = 5
      REPORT LEFT W 6 DOWN intdim x, z, x + z

  These statements produce the following output. With NASKIP2 set to `NO`, the expression X + Z evaluates to `NA` when either X or Z is `NA`.

      INTDIM   X     Z   x + z
      ------ ----- ----- -----
      1         NA     2    NA
      2          3    NA    NA
      3          7     6    13

  The following statement uses a `+` (plus) operator within the expression argument to the TOTAL function.

      SHOW TOTAL(x + z)

  This statement produces the following result.

      13

  The next statement uses the `+` (plus) operator to add the results that are returned by two TOTAL functions.

      SHOW TOTAL(x) + TOTAL(z)

  This statement produces the following result.

      18

- NASKIP Set to YES, NASKIP2 Set to YES

  In this example, NASKIP is set to `YES`, which means `NA` values are ignored by the TOTAL function. NASKIP2 is set to `YES`, which means that `NA` values are ignored by the `+` (plus) operator

      NASKIP = YES
      NASKIP2 = YES
      REPORT LEFT W 6 DOWN intdim x, z, x + z

  These statements produce the following output. With NASKIP2 set to `YES`, `NA` values are ignored when the expression `X` `+` `Z` is evaluated.

      INTDIM   X     Z   X + Z
      ------ ----- ----- -----
      1         NA     2     2
      2          3    NA     3
      3          7     6    13

  The following statement uses a `+` (plus) operator within the expression argument to the TOTAL function.

      SHOW TOTAL(x + z)

  This statement produces the following result.

      18

  The next statement uses the `+` (plus) operator to add the results that are returned by two TOTAL functions.

      SHOW TOTAL(x) + TOTAL(z)

  This statement produces the following result.

      18

- NASKIP Set to NO, NASKIP2 Set to YES

  In this example, NASKIP is set to `NO`, which means that when any values considered by the TOTAL function are `NA`, TOTAL returns `NA`. NASKIP2 is set to `YES`, which means that `NA` values are ignored by the `+` (plus) operator.

      NASKIP = NO
      NASKIP2 = YES
      REPORT LEFT W 6 DOWN intdim x, z, x + z

  These statements produce the following result.

      INTDIM   X     Z   X + Z
      ------ ----- ----- -----
      1         NA     2     2
      2          3    NA     3
      3          7     6    13

  The following statement uses a `+` (plus) operator within the expression argument to the TOTAL function.

      SHOW TOTAL(x + z)

  This statement produces the following result.

      18

  The next statement uses the `+` (plus) operator to add the results that are returned by two TOTAL functions.

      SHOW TOTAL(x) + TOTAL(z)

  This statement produces the following result.

      NA

- NASKIP Set to NO, NASKIP Set to NO

  In this example, NASKIP is again set to `NO`, which means that when any values considered by the TOTAL function are `NA`, TOTAL returns `NA`. NASKIP2 is also set to `NO`, which means that the result of a `+` (plus) operation is `NA` when any of the operands are `NA`.

      NASKIP = NO
      NASKIP2 = NO
      REPORT LEFT W 6 DOWN intdim x, z, x + z

  These statements produce the following result.

      INTDIM   X     Z   X + Z
      ------ ----- ----- -----
      1         NA     2    NA
      2          3    NA    NA
      3          7     6    13

  The following statement uses a `+` (plus) operator within the expression argument to the TOTAL function.

      SHOW TOTAL(x + z)

  This statement produces the following result.

      NA

  The next statement uses the `+` (plus) operator to add the results that are returned by two TOTAL functions.

      SHOW TOTAL(x) + TOTAL(z)

  This statement produces the following result.

      NA

### 5.63 NASPELL

The NASPELL option controls the spelling that is used for `NA` values in output.

#### Data Type

TEXT

#### Syntax

NASPELL = {'text'\|'NA'}

#### Parameters

text
The spelling to use for any `NA` value in output. When you specify an expression rather than a text literal, you can omit the single quotes. The default is `NA`.

#### Usage Notes

Setting NASPELL to "0"

Setting NASPELL to the text character `0` (zero) causes `NA` values to appear as `0`. However, they are still treated as NAs in calculations.

Assigning NA Values

NASPELL affects only Oracle OLAP output; it does not affect the way you assign an `NA` value. For example, even when you have set NASPELL to NONE, you assign an `NA` value as follows.

    var1 = NA

\$NATRIGGER Takes Precedence over NASPELL

Oracle OLAP evaluates an \$NATRIGGER property expression before applying the NASPELL option. When the \$NATRIGGER expression is `NA`, then the NASPELL option has an effect.

#### Examples

Example 5-72 Showing NA Values as "NONE"

Suppose you have a variable called `current.month`, which has a value of `NA` whenever no current month has been specified. In this case, you would like the value to appear as `None` rather than `NA`.

When NASPELL is set to its default value of `NA`, the OLAP DML statement

    SHOW current.month

produces the following output.

    NA

In contrast, the OLAP DML statements

    NASPELL = 'None'
    SHOW current.month

produce the following output.

    None

### 5.64 NLS_CALENDAR

The NLS_CALENDAR option specifies the calendar for the session.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_CALENDAR = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

Example 5-73 Changing Calendar Systems

The following statement sets NLS_CALENDAR to the Thai Buddha calendar.

    NLS_CALENDAR = 'THAI BUDDHA'

### 5.65 NLS_CURRENCY

The NLS_CURRENCY option specifies the local currency symbol for the `L` number format element for the session. (See the [TO_NUMBER](olap-dml-functions-l-z.md) function for a description of number format elements.)

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_CURRENCY = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

### 5.66 NLS_DATE_FORMAT

The NLS_DATE_FORMAT option specifies the default format for datetime values.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_DATE_FORMAT = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

See Example 5-74.

### 5.67 NLS_DATE_LANGUAGE

The NLS_DATE_LANGUAGE option specifies the language for days, months, and similar language-dependent datetime format elements.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_DATE_LANGUAGE = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

Example 5-74 Setting the Language for Dates

The following statements set the language for dates to Spanish and change the default date format.

    NLS_DATE_LANGUAGE = 'SPANISH'
    NLS_DATE_FORMAT = 'Month DD, YYYY'

A `SHOW SYSDATE` statement now generates the date in Spanish.

    Septiembre 08, 2000

### 5.68 NLS_DUAL_CURRENCY

The NLS_DUAL_CURRENCY option specifies a second currency symbol that takes the place of the letter `U` in a number format mode and is used primarily to identify the Euro symbol. (Note that when you want to identify the Euro symbol as the value of NLS_DUAL_CURRENCY, the instance character set must support that symbol.)

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_DUAL_CURRENCY= option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

### 5.69 NLS_ISO_CURRENCY

The NLS_ISO_CURRENCY option specifies the international currency symbol for the `C` number format element.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_ISO_CURRENCY = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

### 5.70 NLS_LANG

(Read-only) The NLS_LANG option specifies the current language, territory, and database character set, which are determined by session-wide globalization parameters.

#### Data Type

TEXT

#### Syntax

NLS_LANG 

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

Example 5-75 Checking the Current Value of NLS_LANG

A `SHOW NLS_LANG` statement might produce the following.

    AMERICAN_AMERICA.WE8ISO8859P1

### 5.71 NLS_LANGUAGE

The NLS_LANGUAGE option specifies the current language for the session. the setting of this option determines the value of the SESSION_NLS_LANGUAGE option.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_LANGUAGE = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

Example 5-76 Effects of Changing NLS_LANGUAGE

In this example, the NLS_LANG option is initially set to:

    AMERICAN_AMERICA.WE8ISO8859P1 

The value of YESSPELL is `yes`.

A change to the language setting:

    NLS_LANGUAGE = 'FRENCH'

changes the value of NLS_LANG to

    FRENCH_AMERICAN.WE8ISO8859P1

The value of YESSPELL is now `oui`.

### 5.72 NLS_NUMERIC_CHARACTERS

The NLS_NUMERIC_CHARACTERS option specifies the decimal marker and thousands group marker for the session. NLS_NUMERIC_CHARACTERS affects the display of numeric data and the setting of the OLAP DML THOUSANDSCHAR option, the DECIMALCHAR option, or both.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_NUMERIC_CHARACTERS = option-value

#### Parameters

See [Setting NLS Parameters](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about NLS parameters, including valid values.

#### Examples

Example 5-77 Changing the Decimal Marker to a Comma

The following statement changes the decimal marker to a comma, and the thousands marker to a space.

    NLS_NUMERIC_CHARACTERS = ', '

The result of the following statement

    show 1234.56

is now

    1 234,56

### 5.73 NLS_SORT

The NLS_SORT option specifies the sequence of character values used when sorting or comparing text. The value of NLS_SORT affects the `GT`, `GE`, `LT`, and `LE` operators, [SORT command](olap-dml-commands-h-z.md), and the [SORTLINES](olap-dml-functions-l-z.md) function.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_SORT = option-value

#### Parameters

See [NLS_SORT](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for more information about the NLS_SORT parameter.

#### Examples

Example 5-78 Binary and Linguistic Sorts

A dimension named `words` has the following values.

    cerveza, Colorado, cheremoya, llama, luna, lago

This example shows the results of a binary sort.

    NLS_SORT = 'BINARY'
    SORT words A words
    STATUS words
    The current status of WORDS is:
    Colorado, cerveza, cheremoya, lago, llama, luna

A Spanish language sort results in this order.

    NLS_SORT = 'SPANISH'
    SORT words A words
    STATUS words
    The current status of WORDS is:
    cerveza, cheremoya, Colorado, lago, llama, luna

An extended Spanish language sort results in this order.

    NLS_SORT = 'XSPANISH'
    SORT words A words
    STATUS words
    The current status of WORDS is:
    cerveza TO cheremoya, lago TO llama

### 5.74 NLS_TERRITORY

The NLS_TERRITORY option specifies current territory for the session.

Within a session, you can dynamically modify the value of this option using the OLAP DML syntax show below or by using the SQL statement `ALTER SESSION` `SET` `option` `=` `value`.  

#### Data Type

TEXT

#### Syntax

NLS_TERITORRY = option-value

#### Parameters

See [NLS_TERRITORY](../nlspg/setting-up-globalization-support-environment.md) in Oracle Database Globalization Support Guide for information about NLS_TERRITORY parameters.

#### Examples

Example 5-79 Effects of Changing NLS_TERRITORY

In this example, the NLS_LANG option is initially set to:

    AMERICAN_AMERICA.WE8ISO8859P1 

The thousands marker is a comma (`,`), and the decimal marker is a period (`.`).

    SHOW TO_NUMBER('12345')
    12,345.00

A change to the territory setting:

    NLS_TERRITORY = 'FRANCE'

changes the value of NLS_LANG to

    AMERICAN_FRANCE.WE8ISO8859P1

The thousands marker is now a period (`.`), and the decimal marker is a comma (`,`).

    SHOW TO_NUMBER('12345')
    12.345,00

### 5.75 NOSPELL

(Read-only) The NOSPELL option holds the text that is used for `FALSE` Boolean values in the output of OLAP DML statements.

The value of the NOSPELL option is the word for "no" in the current language, as specified by the NLS_LANGUAGE option. For example, when NLS_LANGUAGE is set to "American," then the default value of NOSPELL is `NO`.

#### Data Type

TEXT

#### Syntax

NOSPELL

#### Examples

Example 5-80 Seeing the Effect of the NOSPELL Option

Suppose you have a variable called BOOLVAR that currently has a value of `NO`. When "non" is the word for "no" in the language specified by the NLS_LANGUAGE option,

    SHOW boolvar

produces the following output.

    non

### 5.76 OKFORLIMIT

The OKFORLIMIT option controls whether you can limit the dimension you are looping over within an explicit FOR loop.

**Tip:**

To set the status of the dimension you are looping over in a loop that is generated by a REPORT statement, use a TEMPSTAT statement.

#### Data Type

BOOLEAN

#### Syntax

OKFORLIMIT = {NO\|YES}

#### Parameters

NO
(Default) You cannot limit the dimension you are looping over within an explicit FOR loop.

YES
You can limit the dimension you are looping over within an explicit FOR loop.

#### Examples

Example 5-81 Allowing Limits Within a Loop

The following program excerpt sets OKFORLIMIT to `YES`, thereby allowing the user to limit `market` within a FOR loop.

     ...
    OKFORLIMIT = YES
    FOR market
        DO
          LIMIT market TO CHILDREN USING market.market 
          REPORT market
        DOEND
     ...

### 5.77 OKNULLSTATUS

The OKNULLSTATUS option determines whether Oracle OLAP allows a dimension status list to be set to null. The default is to not allow an empty status list. When null status lists are not allowed, Oracle OLAP produces an error message when you execute a [LIMIT command](olap-dml-commands-h-z.md) that would result in a null status list.

#### Data Type

BOOLEAN

#### Syntax

OKNULLSTATUS = {YES\|NO}

#### Parameters

YES
Indicates that null status lists are allowed. With this setting, when you execute a LIMIT command (without the IFNONE argument) that results in a dimension status list being null, the status list is set to null, and no error message is produced.

NO
(Default) Indicates that null status lists are not allowed. With this setting, when you execute a LIMIT command (without the IFNONE argument and without the NULL keyword) that would result in a dimension status list being null, the status list is not changed and an error message is produced.

#### Usage Notes

Conditions When OKNULLSTATUS Has No Effect

The value of OKNULLSTATUS has no effect in the following situations.

- When a LIMIT command includes an IFNONE argument.

- When a LIMIT command uses the NULL keyword to set a dimension status list to null.

- When a LIMIT command sets a valueset to null (unless the IFNONE argument is used). The valueset is set to null, and no error message is produced, even when OKNULLSTATUS is `NO`.

- When a LIMIT function is specified to return a null dimension status list. The value returned is `NA`, and no error message is produced, even when OKNULLSTATUS is `NO`.

See the [LIMIT command](olap-dml-commands-h-z.md) for more information about using null status in dimensions and valuesets.

#### Examples

Example 5-82 Using OKNULLSTATUS

The following statement turns off error messages about the null status of dimensions and allows dimension status lists to be set to null.

    OKNULLSTATUS = YES

### 5.78 OUTFILEUNIT

(Read-only) The OUTFILEUNIT option holds the file unit number of the current OUTFILE destination, set by the last OUTFILE statement. The first time you redirect output to a given file, OUTFILE assigns that file an arbitrary `INTEGER` as a file unit number.

#### Data Type

INTEGER

#### Syntax

OUTFILEUNIT

#### Usage Notes

OUTFILE and OUTFILEUNIT

You automatically change the setting of OUTFILEUNIT whenever you specify a different file with an OUTFILE statement. For example, after the statement `OUTFILE ``myfilename`, the value of OUTFILEUNIT is the file unit number assigned to myfilename.

#### Examples

Example 5-83 Using OUTFILEUNIT with FILEQUERY

Suppose you have saved the file unit number for a file in a variable called `filenum`. Your current outfile is another disk file. You want to set the value of PAGEPRG for the first file to the value that it has for the current outfile. Because the file unit number for the current outfile is contained in the OUTFILEUNIT option, you can use FILEQUERY with the OUTFILEUNIT number to get the PAGEPRG setting for the current outfile.

    FILESET filenum PAGEPRG FILEQUERY(OUTFILEUNIT PAGEPRG)

### 5.79 PAGENUM

The PAGENUM option holds the current page number of output. You can use PAGENUM with PAGEPRG to produce the page number on each page of a report. The PAGENUM option is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and LISTNAMES.

#### Data Type

INTEGER

#### Syntax

PAGENUM = n

#### Parameters

n
An `INTEGER` expression that specifies the page number to use for the next page of output. The default is `1`.

#### Usage Notes

Starting with Page 1

When you are sending output to the default outfile, set both PAGENUM and LINENUM to 1 whenever you want to produce a report starting on page 1. You can set these options in the initialization section of your report program. When you use an OUTFILE statement to send output to a file, PAGENUM is automatically set to `1`.

Setting PAGENUM in Mid-Page

The value of PAGENUM is incremented automatically when the last line of output has been generated on a page. When you set PAGENUM when an output page is only partially full, the value of PAGENUM is incremented by 1 before the next page is produced. Consequently, you usually have to set PAGENUM to a value of one less than the number you want to show on the following page.

The Effect of PAGING on PAGENUM

When you set PAGING to `NO`, PAGENUM stops counting and keeps its last value. When you reset PAGING to `YES`, PAGENUM resumes counting at the page number where it left off.

The Effect of OUTFILE on PAGENUM

When you use an OUTFILE statement to direct output to a file, PAGENUM is set to `1` for the file. When you use an OUTFILE statement with the EOF keyword to redirect output to the default outfile, PAGENUM contains the number that it last held for the default outfile.

#### Examples

Example 5-84 Changing the Heading for Page 2

Suppose you want each page of a report to have a standard running page heading and a custom title, and pages after the first page to also have the heading "(Continued)". You can define a page heading program called `report.head` that uses the PAGENUM value to determine when to add the "(Continued)" heading.

    DEFINE report.head PROGRAM
    PROGRAM
    STDHDR
    BLANK
    PAGING = YES
    HEADING WIDTH LSIZE CENTER 'Annual Sales Report'
    BLANK
    IF PAGENUM GT 1
       THEN HEADING WIDTH LSIZE CENTER '(Continued)'
    BLANK
    END

In your report program, set the PAGEPRG option to use the `report.head` program.

    PAGEPRG = 'report.head'

When you run the report program, each page after the first page starts with a heading such as the following.

    15JAN95 15:05:16                                      Page  2
                           Annual Sales Report
     
                               (Continued)

### 5.80 PAGEPRG

The PAGEPRG option holds the name of a program or the text of a statement to be executed at the beginning of each page of output. You can use this program or statement to create titles and column headings on multiple pages of a report. A program can also contain other statements appropriate for execution at the start of every page. Normally, you set the value of PAGEPRG in the initialization section of a report program.

The PAGEPRG option is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and LISTNAMES.

#### Data Type

TEXT

#### Syntax

PAGEPRG = {'program'\|'statement'\|'NONE'\|'STDHDR'}

#### Parameters

program
The name of a program to be executed after every page break. When you specify the program name as a text expression, you can omit the single quotes.

statement
The text of a statement to be executed after every page break. When you specify the statement as a text expression, you can omit the single quotes.

NONE
Indicates that no statement or program is executed automatically after a page break.

STDHDR
(Default) Makes STDHDR the program name that PAGEPRG stores. You can also set PAGEPRG to `'DEFAULT'` to make STDHDR the program name that PAGEPRG stores. STDHDR produces a heading with the date and time on the left and the page number on the right.

#### Usage Notes

Using a STDHDR Program in a PAGPRG Program

When you create a PAGEPRG program, you can include the STDHDR program as a line in the program. Generally, you place STDHDR before the other statements that produces the custom heading. See Example 5-85.

Keeping Header Information Current

You can use Oracle OLAP functions such as TODAY, TOD, and PAGENUM in a program that is specified by the PAGEPRG option. You can also have a header program that accepts arguments, such as the title for a particular report. In this case you would set the PAGEPRG option to a text expression that invokes the report header program with arguments. See Example 5-86.

Setting PAGEPRG for a File

To set PAGEPRG for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set PAGEPRG to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, PAGEPRG returns to its default value of `'STDHDR'` for the file.

When you set PAGEPRG for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE commands that send output to a file. That is, the value of PAGEPRG is automatically saved for the default outfile.

#### Examples

Example 5-85 Creating a Custom Heading

Suppose you want each page of a report to include both the standard running page heading and the title "Annual Sales Report." To accomplish this, create a program called `report.head`.

    DEFINE report.head PROGRAM
    PROGRAM
    STDHDR
    BLANK
    HEADING WIDTH LSIZE CENTER 'Annual Sales Report'
    BLANK
    IF PAGENUM GT 1
       THEN HEADING WIDTH LSIZE CENTER '(Continued)'
    BLANK
    END

Specify this program to execute after every page break by setting the PAGEPRG option in the report program. You can include PUSH and POP commands to save the PAGEPRG setting that is active.

    PUSH PAGEPRG PAGING
    PAGEPRG = 'report.head'
    PAGING = YES
          ... (body of report program)
      POP PAGEPRG PAGING

When you run the report, each page contains the following heading.

    15JAN98  15:05:16                                      Page 1
     
                           Annual Sales Report

Each page after the first page also contains the subheading "(Continued)" because of the PAGENUM test in the IF statement.

Example 5-86 Using Program Arguments

As an alternative to specifying the report name in the `report.head` program, you can pass the report name to the `report.head` program from your report program. You can do this by setting the PAGEPRG option to a text expression that invokes the report.head program with the report name as an argument. Suppose your report program contains the following statement.

    PAGEPRG = 'CALL report.head(\'Annual Sales Report\')'

Then you can change the first few lines of the report.head program to the following.

    ARGUMENT titlevar TEXT
    STDHDR
    BLANK
    HEADING WIDTH LSIZE CENTER titlevar

### 5.81 PAGESIZE

The PAGESIZE option specifies the size of a page of output. The value of PAGESIZE is the number of output lines to be produced on each page. PAGESIZE is usually used in the initialization section of report programs. The PAGESIZE option is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and LISTNAMES. PAGESIZE also controls the LINELEFT option. When PAGESIZE is changed, Oracle OLAP adjusts LINELEFT accordingly.

**See Also:**

[PAGE](olap-dml-commands-h-z.md) command, PAGING option, LINESLEFT option

#### Data Type

INTEGER

#### Syntax

PAGESIZE = n

#### Parameters

n
An `INTEGER` expression that specifies the number of output lines on a page; n includes the top and bottom margins (controlled by the TMARGIN and BMARGIN options). The default is 66 lines, which is suitable for printing report output on 8 1/2" by 11" paper.

#### Usage Notes

Usable Output Lines with Standard Heading and Default Settings

When you use the standard heading and the default settings for the PAGESIZE, TMARGIN, and BMARGIN options, the total number of usable output lines is 61.

                                  Output Lines
    Lines from PAGESIZE                     66
    Lines for TMARGIN                      - 2
    Lines for the standard heading         - 2
    Lines for BMARGIN                      - 1
    Lines available for output              61

Eliminating Headings and Page Breaks

You can produce pages with no headings by using the statement `PAGEPRG='NONE'` or suppress page breaks entirely by using the statement `PAGING = NO`.

Setting PAGESIZE for a File

To set PAGESIZE for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set PAGESIZE to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, PAGESIZE returns to its default value of `66` for the file.

When you set PAGESIZE for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE commands that send output to a file. That is, the value of PAGESIZE is automatically saved for the default outfile.

#### Examples

Example 5-87 Printing on Legal Paper

In this example, you want to produce a report on legal-size paper (8 1/2" by 14"). Include the following statement in the initialization section of your report program.

    PAGESIZE = 84

### 5.82 PAGING

The PAGING option controls the production of paged output in Oracle OLAP. When you set PAGING to `YES`, output from statements such as DESCRIBE, REPORT, ROW command, HEADING, SHOW, and LISTNAMES is produced in a page-oriented format. Output is produced in page-size segments with standard top and bottom margins and headings. You can use a variety of paging-related options to change the size of the page, the size of the margins, and the headings on each page.

Paging is useful primarily for making output more attractive when you plan to print output that you send to a file. However, you can also send paged output to the default outfile. Normally you would set the PAGING option in the initialization section of a report program to turn paging on for your report.

#### Data Type

BOOLEAN

#### Syntax

PAGING = {YES\|NO}

#### Parameters

YES
Produces output with page breaks, top and bottom margins, and page headings.

NO
(Default) Produces output that contains no page breaks, top and bottom margins, or page headings. Output is continuous, one line after another.

#### Usage Notes

Setting PAGING for a File

To set PAGING for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set PAGING to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, PAGING returns to its default value of `NO` for the file.

When you set PAGING for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE commands that send output to a file. That is, the value of PAGING is automatically saved for the default outfile.

Paging-Related Options

Oracle OLAP uses default values for page length, page headings, and top and bottom margins. You can change these values by setting the PAGESIZE, PAGEPRG, TMARGIN, and BMARGIN options. Other paging options that become meaningful when PAGING is set to YES are LINENUM, LINELEFT, and PAGENUM.

The value of PAGING for the current outfile determines whether the paging-related options are used. You must set PAGING to `YES` for the current outfile to make the paging options take effect.

Toggling PAGING On and Off

Toggling PAGING on and off, has the following effect on paging options:

- When you toggle PAGING from on (YES) to off (NO):

  - The value of the LINENUM option continues to increment as more output lines are produced.

  - The LINELEFT option is set to PAGESIZE.

  - The PAGENUM option stops counting and retains its current value

- When you toggle PAGING from off (NO) to on (YES):

  - LINENUM is set to `1` and it begins counting lines on the current page.

  - LINELEFT begins counting the lines left on the current page.

  - PAGENUM resumes counting at the page number where it left off.

Changing Outfiles

When you use an OUTFILE statement to direct output to a file, all the paging-related options are set to their default values for the file. When you use an OUTFILE statement with the EOF keyword to redirect output to the default outfile, the paging-related options contain the values that they last held for the default outfile.

#### Examples

Example 5-88 Setting Paging Options

Suppose you are writing a report program and you want to control page breaks and the top margin. You can include the following lines in the initialization section of your program. These lines send output to a file named `repfile.txt`, turn the PAGING option on, and change the page size and top margin.

    OUTFILE 'repfile.txt'
    PAGING = YES
    PAGESIZE = 84
    TMARGIN = 6

### 5.83 PARENS

The PARENS option controls whether negative numbers are represented in output with parentheses or a minus sign.

#### Data Type

BOOLEAN

#### Syntax

PARENS = {YES\|NO}

#### Parameters

YES
Encloses negative values in parentheses, instead of using a minus sign.

NO
(Default) Uses a minus sign to represent negative values.

#### Usage Notes

Overriding PARENS

The setting of the PARENS option is overridden by a PAREN or NOPAREN attribute in a HEADING, REPORT, or ROW command. The PAREN attribute specifies the use of parentheses; the NOPAREN attribute specifies the use of a minus sign.

Allowing Space for Parentheses

When you use parentheses to represent negative values in a report, Oracle OLAP lines up the positive and negative values in the column. To do this, it reserves the right-most character in each numeric column for the closing parenthesis. The column is always reserved, even when there are no negative values in the output. Consequently, each value requires more space than when you use the minus sign, and you might have to increase your column width to accommodate your data.

#### Examples

Example 5-89 Showing Negative Values in Parentheses

In a report, you would like to show negative values in parentheses, so you first set PARENS to `YES`.

    LIMIT line TO 'Cogs'
    LIMIT division TO 'Sporting'
    LIMIT month TO 'Jan96' TO 'Jun96'
    PARENS = YES
    DECIMALS = 0
    REPORT DOWN month budget actual budget-actual

These statements produce the following output.

    DIVISION: SPORTING
                   --------------LINE--------------
                   --------------COGS--------------
                                         BUDGET-ACT
    MONTH            BUDGET     ACTUAL      UAL
    -------------- ---------- ---------- ----------
    Jan96            279,773    287,558     (7,785)
    Feb96            323,982    315,299      8,683
    Mar96            302,178    326,185    (24,007)
    Apr96            386,101    394,544     (8,443)
    May96            433,998    449,862    (15,864)
    Jun96            448,042    457,348     (9,305)

### 5.84 PERMITERROR

The PERMITERROR option controls if an error is signaled on attempted access of a variable for which read or write permission is denied by a PERMIT statement.

**See Also:**

"[Startup Programs](olap-dml-programs.md)", PERMITREADERROR option, [PERMIT](olap-dml-commands-h-z.md) command, and [PERMITRESET](olap-dml-commands-h-z.md) command.

#### Data Type

BOOLEAN

#### Syntax

PERMITERROR = NO \| YES

#### Parameters

NO
When you set PERMITERROR to `NO`, an error condition is not created on attempted access of a variable for which read or write permission is denied with a PERMIT statement. Values for which you do not have read permission are displayed as `NA`s. When you try to change a value for which you do not have write permission, the request is ignored.

YES
(Default) When PERMITERROR is `YES`, an error is signaled upon attempted access of a variable for which read or write permission is denied with a PERMIT statement. The error, which can be trapped, terminates the Oracle OLAP operation that initiated the illegal access.

#### Usage Notes

PERMITERROR With Non-Data Objects

The setting of PERMITERROR is ignored for violations of permission for non-data objects such as programs, models, and valuesets. Attempted access of variables and relations with permission, whether or not they have dimensionality, is always affected by the setting of PERMITERROR.

Maintaining Dimensions

The setting of PERMITERROR is ignored for violations of maintain and permit permission. Attempted violations of permission to maintain dimensions and to change permission are always treated as errors. Attempted violations of read or write permission for dimensions are, similarly, always treated as errors.

Obtaining Data Without Full Permission

When PERMITERROR is `YES` and you attempt to fetch a dimensioned variable that contains values that do not have read permission, an error condition is created when the first of those values is encountered. You can avoid creating an error condition by limiting the dimensions in advance so that only permissible values are in status, or by setting PERMITERROR to `NO`, before doing the report.

#### Examples

Example 5-90 Report Without Full Permission

In the following example, the read permission on the `price` variable prevents you from seeing price data for any values of `product` other than `Tents`. However, when you set PERMITERROR to `NO`, you can still do a report of the `price` variable for Dec. 1996 without creating an error condition.

    PERMITERROR = no
    DESCRIBE price

The output of this statement is

    DEFINE PRICE VARIABLE DECIMAL <MONTH PRODUCT>
    LD Wholesale Unit Selling Price
    PERMIT READ WHEN product eq 'Tents'

The statements

    LIMIT month TO 'Dec96'
    REPORT price

produce the following output.

                      ----PRICE----
                      ----MONTH----
    PRODUCT               DEC96      
    ----------------  -------------
    Tents                  165.64
    Canoes                     NA
    Racquets                   NA
    Sportswear                 NA
    Footwear                   NA

The statements

    PERMITERROR = yes
    REPORT price

produce the following error,

    ERROR: You do not have permission to read this value of PRICE

and the following output.

                     ---PRICE---
                     ---MONTH---
    PRODUCT             DEC96
    ---------------  -----------
    Tents                165.64

### 5.85 PERMITREADERROR

The PERMITREADERROR option controls if an error is signaled on attempted read of a variable, valueset, formula, or relation for which read or write permission is denied by a PERMIT statement.

**See Also:**

"[Startup Programs](olap-dml-programs.md)", PERMITERROR option, [PERMIT](olap-dml-commands-h-z.md) command, and [PERMITRESET](olap-dml-commands-h-z.md) command.

#### Data Type

BOOLEAN

#### Syntax

PERMITREADERROR = NO \| YES

#### Parameters

NO
(Default) When the value ofPERMITREADERROR is `YES`, an error condition is not created on attempted access of a variable, valueset, formula, or relation for which read or write permission is denied with a PERMIT statement. Values for which you do not have read permission are displayed as `NA`s. When you try to change a value for which you do not have write permission, the request is ignored.

YES
When PERMITERROR is `YES` , an error is signaled upon attempted to read a variable, valueset, formula, or relation for which read or write permission is denied with a PERMIT statement. The error, which can be trapped, terminates the Oracle OLAP operation that initiated the illegal access.

### 5.86 PRGTRACE

The PRGTRACE option controls whether each line of a program is recorded in the current outfile or in a debugging file during execution of the program. PRGTRACE is primarily used as a debugging tool to uncover problems by tracing the execution of a program.

OLAP DML programs provided as OLAP DML statements are not traced unless EXPTRACE is set to `YES`.

When you have used a DBGOUTFILE statement to specify a debugging file, Oracle OLAP sends PRGTRACE output to the debugging file instead of the current outfile.

#### Data Type

BOOLEAN

#### Syntax

PRGTRACE = {YES\|NO}

#### Parameters

YES
Oracle OLAP records each line in a program before it is executed.

NO
(Default) Oracle OLAP does not record each line in a program.

#### Usage Notes

PRGTRACE Output

PRGTRACE records the name of the current program at the beginning of each program line. It includes an equals sign to indicate a compiled line.

    (PRG= SALESREP) . . .

It includes a colon to indicate an uncompiled line.

    (PRG: SALESREP) . . .

A compiled line is a line that has been translated into an efficient internal form, whereas an uncompiled line has not. Oracle OLAP ordinarily stores lines in compiled form to make programs work more efficiently, especially programs that contain loops.

Uncompiled Program Lines

Oracle OLAP compiles a program before running it. Therefore, the only lines that are marked as uncompiled in the PRGTRACE output are lines that cannot be compiled, such as lines that include ampersand substitution.

#### Examples

Example 5-91 Tracing Program Execution

Suppose you have a program called `salesrep` that produces a simple budget report.

    DEFINE salesrep PROGRAM
    PROGRAM
    PUSH month division line
    TRAP ON cleanup
    LIMIT month TO &ARGS
    LIMIT division TO ALL
    LIMIT line TO FIRST 1
    REPORT DOWN division across month: dec 0 budget
     
    cleanup:
    POP month division line
    END

When you want to debug this program, you can trace the execution of each of its lines by turning on PRGTRACE and executing the program.

    PRGTRACE = yes
    salesrep FIRST 3

PRGTRACE produces the following output in the current outfile or debugging file.

    (PRG= SALESREP) push month division line
    (PRG= SALESREP) trap on cleanup
    (PRG: SALESREP) limit month to &args
    (PRG= SALESREP) limit division to all
    (PRG= SALESREP) limit line to first 1
    (PRG= SALESREP) report down division across month: dec0 budget
    LINE: REVENUE
                   -------------BUDGET-------------
                   -------------MONTH--------------
    DIVISION         JAN95      FEB95      MAR95
    -------------- ---------- ---------- ----------
    CAMPING          679,149    707,945    780,994
    SPORTING         482,771    517,387    525,368
    CLOTHING         983,888  1,016,528    992,331
    (PRG= SALESREP) cleanup:
    (PRG= SALESREP) pop month division line

### 5.87 RANDOM.SEED.1 and RANDOM.SEED.2

The RANDOM.SEED.1 and RANDOM.SEED.2 options specify values used by RANDOM when computing random numbers. To compute the number, RANDOM uses the values of the options RANDOM.SEED.1 and RANDOM.SEED.2, and then changes the values for the next time.

When you want to reproduce the same sequence of random numbers when you are developing and debugging your application programs set RANDOM.SEED.1 and RANDOM.SEED.2 to some specific values just before using RANDOM.

#### Data Type

INTEGER

#### Syntax

RANDOM.SEED.1\|RANDOM.SEED.2 = n

#### Parameters

n
An `INTEGER` expression that specifies the value to use when generating random numbers. The default is for RANDOM.SEED.1 is 12345 and RANDOM.SEED.2 is 1073.

#### Usage Notes

Reproducing a Random Sequence

As illustrated in [Example 8-64](olap-dml-functions-l-z.md), when you want to reproduce the same sequence of random numbers when you are developing and debugging your application programs, set RANDOM.SEED.1 and RANDOM.SEED.2 to some specific values just before using RANDOM. To duplicate the sequence, set these options to the same values just before using RANDOM again. Then changes in the behavior of your programs are caused by your changes to the programs and not by differing sequences of random numbers.

#### Examples

Example 5-92 Explicitly Seeding RANDOM for a Test

Assume that you have the following dimension and variable in your analytic workspace

    DEFINE id DIMENSION TEXT
    DEFINE myvar VARIABLE INTEGER <id>


As shown in the following code, when you use RANDOM to populate `myvar` without seeding it first. Oracle OLAP populates `myvar` with different values each time the RANDOM executes.

    myvar = 0
    myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     11
    a2                     19
    a3                     14

    myvar = 0
    myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     16
    a2                     13
    a3                     12


Now, assume that you want to write a test that uses RANDOM to create predictable values for `myvar`. As the following code illustrates, to ensure that the results of RANDOM are the same from time to time, you must set the values of RANDOM.SEED.1 and RANDOM.SEED.2 right before the execution of RANDOM.

    myvar = 0
    RANDOM.SEED.1 = 5
    RANDOM.SEED.2 = 3
        myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     10
    a2                     16
    a3                     13

    myvar = 0
    RANDOM.SEED.1 = 5
    RANDOM.SEED.2 = 3
    myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     10
    a2                     16
    a3                     13

The values that you set for RANDOM.SEED.1 and RANDOM.SEED.2 do not stay the same throughout a session. As the following code illustrates, when you do not reseed with the same values before each execution, the values produced by RANDOM are not the same.

    myvar = 0RANDOM.SEED.1 = 5
    RANDOM.SEED.2 = 3
    myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     10
    a2                     16
    a3                     13

    myvar = 0
        myvar = RANDOM (10, 20)
    REPORT myvar

    ID               MYVAR
    -------------- ----------
    a1                     11
    a2                     16
    a3                     20

### 5.88 RECURSIVE

The RECURSIVE option controls the ability of a formula or \$NATRIGGER` `expression to call itself.

#### Syntax

RECURSIVE = {YES\|NO}

#### Parameters

YES
Specifying `YES` allows a formula or \$NATRIGGER` `expression to call itself. Set this option to `YES` when you define a formula or an expression for the \$NATRIGGER property that uses a recursive method of computation.

NO
(Default) Specifying `NO` prevents a formula or \$NATRIGGER expression from calling itself. When you attempt to evaluate a recursive formula or \$NATRIGGER expression, then Oracle OLAP displays an error message, which states that the RECURSIVE option is currently set to `NO`. Until the workspace contains a recursive formula or \$NATRIGGER` `expression, keep this option set to `NO` to detect errors that could result in infinite looping behavior.

#### Usage Notes

For Formulas and \$NATRIGGER Expressions Only

When you set RECURSIVE to `YES`, only formulas and \$NATRIGGER property expressions are affected. This option does not affect programs; that is, a program can be recursive regardless of the setting of the RECURSIVE option unless the program is a \$NATRIGGER expression. A \$NATRIGGER expression cannot call itself unless the RECURSIVE option is `YES`.

Limiting \$NATRIGGER Recursion

You can limit the depth of recursion for \$NATRIGGER property expressions with the TRIGGERMAXDEPTH option, which sets the maximum number of \$NATRIGGER` e`xpressions that Oracle OLAP executes simultaneously.

### 5.89 ROLE

(Read-only) The ROLE option holds a list of Oracle Database roles associated with the user ID under which an Oracle OLAP session is running.

#### Data Type

TEXT

#### Syntax

ROLE

#### Examples

Example 5-93 Displaying a List of Groups or Roles

This statement displays a list of the roles associated with the current session user ID.

    SHOW ROLE

### 5.90 ROOTOFNEGATIVE

The ROOTOFNEGATIVE option determines the result of any attempt to obtain a root of a negative number.

#### Data Type

BOOLEAN

#### Syntax

ROOTOFNEGATIVE = YES\|NO

#### Parameters

YES
Allows any attempt to obtain a root of a negative number. Consequently, a statement that attempts to obtain a root of a negative number executes without an error; however, the result of the attempt to obtain the root is `NA`. When you are working with a dimensioned variable or expression, setting ROOTOFNEGATIVE to `YES` enables you to obtain the root of most of the expression's values when a few of the values might be negative.

NO
(Default) Disallows any attempt to obtain a root of a negative number. Any statement that attempts to obtain a root of a negative number stops executing and an error message is produced.

#### Usage Notes

Raising to a Noninteger Power

Raising a number to a noninteger power (for example,` 5 ** 0.3` or `14 ** 2.7`) is an attempt to obtain a root.

#### Examples

Example 5-94 The Effect of ROOTOFNEGATIVE

The following example shows the effect of changing the value of the ROOTOFNEGATIVE option. The variable TESTNUMBER has a value of `-56`. When you execute a SHOW statement such as the following one, without changing the ROOTOFNEGATIVE option from its default value of `NO`, an attempt is made to obtain the square root and then an error message is produced.

    SHOW SQRT(testnumber)

When you change ROOTOFNEGATIVE to `YES`, the same statement executes without error

    ROOTOFNEGATIVE = YES
    SHOW SQRT(testnumber)

and produces the following result.

    NA

### 5.91 SECONDS

(Read-only) The SECONDS option holds the number of seconds since January 1, 1970. As an aid to enhancing a program's speed, SECONDS can be used to determine how many real seconds elapse while the program is running.

#### Data Type

INTEGER

#### Syntax

SECONDS

#### Examples

Example 5-95 Timing a Program Using SECONDS

The following program puts the value of SECONDS at the start of the program in a variable called `t1`, then displays the difference between `t1` and the value of SECONDS after the program executes.

    DEFINE prodsummary PROGRAM
    PROGRAM
    VARIABLE t1 INTEGER
    t1 = seconds
    LIMIT product TO ALL
    BLANK
    FOR product
    DO
      ROW WIDTH 16 name.product ACROSS month Jun96: DECIMAL 0 LSET -
       '$'WIDTH 18 <RSET ' (actual)' sales RSET ' (plan)' sales.plan>
    DOEND
    BLANK
    ROW WIDTH 35 LSET 'the program took ' RSET ' SECOND(s).' -
     (SECONDS-t1)
    END

Running this program produces the following results.

    3-Person Tents     $95,121 (actual)     $80,138 (plan)
    Aluminum Canoes   $157,762 (actual)    $132,931 (plan)
    Tennis Racquets    $97,174 (actual)     $84,758 (plan)
    Warm-up Suits      $79,630 (actual)     $73,569 (plan)
    Running Shoes     $153,688 (actual)    $109,219 (plan)
     
          The program took 2 second(s).

### 5.92 SESSCACHE

Typically used only when debugging, the SESSCACHE option controls whether Oracle OLAP creates an Oracle OLAP session cache described in "What is an Oracle OLAP Session Cache".

#### Data Type

BOOLEAN

#### Syntax

SESSCACHE = {YES\|NO}

#### Parameters

YES
The session cache is created to hold the data described in "What is an Oracle OLAP Session Cache".

NO
Oracle OLAP does not read or write to the session cache. When you specify `NO`, caching does not occur even when you have specified caching by coding a CACHE SESSION statement in the specification for one or more aggmap objects, by setting one or more \$VARCACHE properties to `SESSION`, or by setting the VARCACHE option to `SESSION`.

#### Usage Notes

What is an Oracle OLAP Session Cache?

An Oracle OLAP session cache is a special place in memory used to hold:

- All data that was calculated on the fly when an AGGREGATE function executed in the following situations:

  - The specification for the aggregation included a CACHE SESSION.

  - The specification for the aggregation did not include a CACHE SESSION statement, but the variable being aggregated had a \$VARCACHE property with the value of `SESSION`.

  - The specification for the aggregation did not include a CACHE SESSION statement and the variable being aggregated did not have a \$VARCACHE property, but the VARCACHE option was set to `SESSION`.

- The `NA` values (only) that were calculated when an AGGREGATE function executed and the specification for the aggregation included a CACHE NA statement.

- All data that was calculated when a \$NATRIGGER expression executed in the following situations:

  - The variable with the \$NATRIGGER property also had a \$VARCACHE property with the value of `SESSION`.

  - The variable with the \$NATRIGGER property did not have a \$VARCACHE property, but the VARCACHE option was set to `SESSION`.

There is one internal cache for a session. Cached data is ignored by UPDATE and COMMIT statements. However, once data is cached, Oracle OLAP uses the values in the cache for all calculations unless an AGGREGATE function with the FORCECALC keyword executes. In this case, the FORCECALC keyword specifies that Oracle OLAP recalculate the values.

When a session is terminated, its cache is cleared. To clear the session cache without terminating the session, issue a CLEAR statement.

The effectiveness of a session cache is tracked in the `V$AW_CALC` dynamic performance view.

### 5.93 SESSION_NLS_LANGUAGE

(Read-only) The SESSION_NLS_LANGUAGE option is an OLAP session-wide, option that holds the value of NLS_LANGUAGE when the value of STATIC_SESSION_LANGUAGE is NO; or, when the value of STATIC_SESSION_LANGUAGE is YES, the value of NLS_LANGUAGE the last time that the value of STATIC_SESSION_LANGUAGE was NO.

**See Also:**

"SESSION_NLS_LANGUAGE" in [\$DEFAULT_LANGUAGE](olap-dml-properties.md)

#### Data Type

TEXT

#### Syntax

SESSION_NLS_LANGUAGE

#### Examples

For examples of retrieving how the value of SESSION_NLS_LANGUAGE is impacted by changes in the value of NLS_LANGUAGE and STATIC_SESSION_LANGUAGE, see [Example 4-9](olap-dml-properties.md) and Example 5-102.

Example 5-96 SESSION_NLS_LANGUAGE is a Session-Wide Option

Assume that you have two analytic workspace, one named `myaw3` and another named `myaw4`. Assume also, as shown in the following code, that they both have language dimensions named `mylangs` and that the languages for `mylangs` in `myaw3`are American and French and that the languages for `mylangs` in `myaw4` are American and German.

    REPORT myaw3!mylangs
    MYLANGS
    --------------
    AMERICAN
    FRENCH

    REPORT myaw4!mylangs
    MYLANGS
    --------------
    AMERICAN
    GERMAN


Now assume that you attach both of these analytic workspaces while NLS_LANGUAGE and SESSION_NLS_LANGUAGE are set to American. As shown in the following code, Oracle OLAP limits `mylangs` in both analytic workspace to American.

    REPORT myaw3!mylangs
    MYLANGS
    --------------
    AMERICAN

    REPORT myaw4!mylangs
    MYLANGS
    --------------
    AMERICAN

### 5.94 SPARSEINDEX

The SPARSEINDEX option controls the type of index algorithm that composites use to load and access their values. The value of SPARSEINDEX at the time a named composite is defined, or an unnamed composite is created, determines the type of algorithm the composite uses by default. When you specify an index algorithm in a DEFINE COMPOSITE statement, this overrides the default specified by the SPARSEINDEX option.

Choosing an index algorithm is important only in regard to performance issues. Any recommendations are for the version of Oracle OLAP that is associated with this documentation. You can test how using different algorithms affect performance by using a CHGDFN statement to change the algorithm for a composite (for example, before loading data).

#### Data Type

TEXT

#### Syntax

SPARSEINDEX = {'BTREE'\|'HASH'}

#### Parameters

BTREE
A standard indexing method that is recommended for composites. Use BTREE unless you are an advanced user. BTREE tends to group similar values together, which results in better locality of access. BTREE is the default algorithm.

HASH
A standard indexing method that should only be used when a composite has only two or three base dimensions. HASH is generally not recommended for composites because using HASH results in a very large index table, which can be too large to fit into memory.

#### Examples

Example 5-97 Using the HASH Algorithm

The following example sets SPARSEINDEX to `HASH` so that composites that are subsequently defined or created are created using the HASH index algorithm by default.

    SPARSEINDEX = 'HASH'

### 5.95 SQLBLOCKMAX

The SQLBLOCKMAX option controls the maximum number of records retrieved from an Oracle Database instance at one time. This option provides a means of fine-tuning the performance of data fetches.

#### Data Type

INTEGER

#### Syntax

SQLBLOCKMAX = records

#### Parameters

records
An `INTEGER` that identifies the number of records you want fetched at one time. While you can set SQLBLOCKMAX to any `INTEGER`, no appreciable change in performance results in setting it over 100. The default is `10` records.

#### Usage Notes

Opening Cursors

Only cursors opened after SQLBLOCKMAX is reset use the new block size.

Number of Records

When a program typically opens a cursor, reads one record, and closes the cursor, set SQLBLOCKMAX to `1`. Otherwise, the SQL FETCH statement retrieves 10 records and discards 9 of them. The same is true for other routine fetches of less than 10 records.

Block Size

When your program is fetching small records, you can increase SQLBLOCKMAX to reduce the number of blocks required for the fetch. Oracle OLAP fetches the data into a 64K buffer. The block size in bytes is the number of records multiplied by the size of the records. When the block size exceeds the 64K limit imposed by the buffer, Oracle OLAP automatically reduces the number of records fetched. See Example 5-98.

#### Examples

Example 5-98 Defining a Cursor with SQLBLOCKMAX

The following program fragment defines a cursor for fetching 50-byte records from a database. The new block size easily fits into Oracle OLAP's 64K buffer (`50` bytes `*` `100` `=` `50k` block size).

    SQLBLOCKMAX = 100
    SQL DECLARE CURSOR c1 FOR SELECT * FROM mydata
    SQL OPEN c1

### 5.96 SQLCODE

(Read-only) The SQLCODE option holds the value returned by the Oracle RDBMS after the most recently attempted SQL operation.

#### Return Value

INTEGER. `0` after a successful operation, `-1` after an error, or `100` after all requested rows have been fetched.

#### Syntax

SQLCODE

#### Usage Notes

Handling SQL Errors

Oracle OLAP does not signal an error when SQLCODE becomes nonzero. Therefore, your program must test the value of SQLCODE and take the appropriate action. Because each SQL operation sets SQLCODE, you must test for errors after each operation to avoid missing an error condition.

**Tip:**

After an error, the SQLERRM option typically contains an error message.

You can write programs that look for a specific error code. For example, the most common warning code is `100`, which indicates that the cursor reached the end of its table selection and the FETCH statement is complete.

#### Examples

Example 5-99 Using SQLCODE When Fetching Data

The following program fragment includes a WHILE loop that tests for the value of SQLCODE and stops trying to fetch data when the end of the cursor's active set is reached.

    WHILE SQLCODE EQ 0
       SQL FETCH cursor1 INTO :employee, :title

### 5.97 SQLERRM

(Read-only) After the database reports an error and SQLCODE has a nonzero value, the SQLERRM option usually contains text that explains the problem.

#### Data Type

TEXT

#### Syntax

SQLERRM

#### Usage Notes

Oracle Relational Manager

You can set the SQLMESSAGES option to `YES` to send the value of SQLERRM to the current output file automatically.

#### Examples

Example 5-100 Displaying Error Messages

The following statements attempt to create a table and check for error messages afterward.

    SQL CREATE TABLE Products -
       (Prod_ID CHAR(8) -
       Prod_Name VARCHAR(30) -
       Suggested_Price DECIMAL(10,2))
    IF SQLCODE NE 0
       SHOW SQLERRM

Example 5-101 Sample Error Message

The following statement is incomplete and does not provide sufficient information to create a table.

    SQL CREATE TABLE Products

The Oracle RDBMS returns an error message such as the following.

    ORA-00906: Missing left parenthesis.

### 5.98 SQLMESSAGES

The SQLMESSAGES option controls whether error messages are sent to the current output file.

#### Data Type

BOOLEAN

#### Syntax

SQLMESSAGES = {YES\|NO}

#### Parameters

YES
Error messages are sent to the current output file.

NO
(Default) Error messages are only stored as values of SQLERRM.

#### Usage Notes

Typical Usage

You want to set SQLMESSAGES to `YES` while you are developing an application so that you can diagnose errors quickly. When your application is in use, you probably want it to capture and handle errors in a different manner with SQLMESSAGES set to `NO`.

### 5.99 STATIC_SESSION_LANGUAGE

The STATIC_SESSION_LANGUAGE option is a read/write option that controls if Oracle OLAP keeps the value of the SESSION_NLS_LANGUAGE option synchronized with the value of the NLS_LANGUAGE option.

**See Also:**

"Working with Language Dimension Status" in [\$DEFAULT_LANGUAGE](olap-dml-properties.md)

#### Data Type

BOOLEAN

#### Syntax

STATIC_SESSION_LANGUAGE = NO \| YES

#### Parameters

NO
Specifies that whenever the value of the NLS_LANGUAGE option changes, Oracle OLAP changes the value of SESSION_NLS_LANGUAGE to the value of the NLS_LANGUAGE option. (Default)

YES
Specifies that the value of SESSION_NLS_LANGUAGE does not change when the value of NLS_LANGUAGE changes.

#### Examples

Example 5-102 Changing NLS_LANGUAGE Without Changing the Language of the OLAP Session

[Example 4-9](olap-dml-properties.md) illustrates how changing the NLS_LANGUAGE value can change the language of the OLAP session. This example illustrates how you can keep the language of the OLAP session the same even as the value of the NLS_LANGUAGE option changes.

Assume that you attach your analytic workspace while the NLS_LANGUAGE is American. As the following code illustrates by changing the value of the STATIC_SESSION_LANGUAGE to Yes, you can insure that even as the value of the NLS_LANGUAGE option is changed to French, the value of the SESSION_NLS_LANGUAGE stays American which means that Oracle OLAP limits the language dimension (`mylangs`) to American.

    SHOW NLS_LANGUAGEFRENCH
    AMERICAN

    " Make the session language static
    STATIC_SESSION_LANGUAGE = yes

    "Change the value of NLS_LANGUAGE to FRENCH
    SET NLS_LANGUAGE= 'FRENCH'

    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN
    SHOW NLS_LANGUAGE
    FRENCH
    SHOW SESSION_NLS_LANGUAGE
    AMERICAN
    SHOW LOCK_LANGUAGE_DIMS
    oui
    SHOW STATIC_SESSION_LANGUAGE
    oui

    REPORT mylangs
    MYLANGS
    --------------
    AMERICAN

    REPORT prod_desc
                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    AMERICAN       Trousers   Skirts

### 5.100 THIS_AW

(Read-only) The THIS_AW option is the value of the workspace name that Oracle OLAP uses when it replaces occurrences of the THIS_AW keyword to create a qualified object name.

#### Data Type

TEXT

#### Syntax

THIS_AW

### 5.101 THOUSANDSCHAR

(Read-only) The THOUSANDSCHAR option is the value specified for the NLS_NUMERIC_CHARACTERS option discussed in NLS Options.

**Note:**

The value of THOUSANDSCHAR only affects the way Oracle OLAP formats numbers in output. It does not affect the way numbers should be formatted for input.

#### Data Type

ID

#### Syntax

THOUSANDSCHAR

#### Examples

Example 5-103 Displaying the Decimal and Thousands Markers

The following statements show the DECIMALCHAR and THOUSANDSCHAR values. Assume that you issue the following statements.

    SHOW THOUSANDSCHAR
    SHOW DECIMALCHAR

Assume that a comma is displayed as the marker for THOUSANDSCHAR and that a period is displayed as the marker for DECIMALCHAR. With these values, a `SHOW TOTAL(sales)` statement would produce the following output.

    63,181,743.50

### 5.102 TMARGIN

The TMARGIN option defines the number of blank lines for the top margin of output pages, above the running page heading. In other words, the top margin lines are produced before the program that is defined by PAGEPRG, if any, is run.

TMARGIN is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and DESCRIBE. The TMARGIN option is usually set in the initialization section of report programs.

#### Data Type

INTEGER

#### Syntax

TMARGIN = n

#### Parameters

n
An `INTEGER` expression that specifies the number of lines to set aside for the top margin in a report. The default is` 2`.

#### Usage Notes

Setting TMARGIN for a File

To set TMARGIN for a file, first make the file your current outfile by specifying its name in an OUTFILE statement, then set TMARGIN to the desired value. The new value remains in effect until you reset it or until you use an OUTFILE statement to direct output to a different outfile. When you direct output to a different outfile, TMARGIN returns to its default value of 2 for the file.

When you set TMARGIN for the default outfile, the new value remains in effect until you reset it, regardless of intervening OUTFILE commands that send output to a file. That is, the value of TMARGIN is automatically saved for the default outfile.

#### Examples

Example 5-104 Setting the Top Margin of a Report

In this example, you want to save space when you produce a long report, so you set a small top margin of 1 line. Here is the statement that you would include in the initialization section of your report program.

    TMARGIN = 1

### 5.103 TRACEFILEUNIT

(Read-only) The TRACEFILEUNIT option records the unit number of the Oracle trace file which is a writable output file that collects information about the activity in the Oracle session.

#### Syntax

TRACEFILEUNIT

#### Usage Notes

Use of the TRACEFILEUNIT Value

With the OUTFILE or DBGOUTFILE commands, you can specify the unit number stored in the TRACEFILEUNIT option to send the output to the Oracle trace file.

#### Examples

Example 5-105 Specifying the Oracle Trace File with DBGOUTFILE

In the following code, the DBGOUTFILE command specifies the value of TRACEFILEUNIT option.

    DBGOUTFILE TRACEFILEUNIT

### 5.104 TRIGGERMAXDEPTH

The TRIGGERMAXDEPTH option determines the maximum number of \$NATRIGGER property expressions that Oracle OLAP can execute simultaneously.

#### Data Type

`INTEGER`

#### Syntax

TRIGGERMAXDEPTH = n

#### Parameters

n
An `INTEGER` expression that specifies the maximum number of \$NATRIGGER property expressions that can execute simultaneously. The default value is `50`.

#### Usage Notes

About the \$NATRIGGER Property

The TRIGGERMAXDEPTH option works with the \$NATRIGGER property of a variable.

Recursive Triggers

While a \$NATRIGGER expression is executing, it cannot be invoked again by a formula, program, or other \$NATRIGGER expression that it invokes unless the RECURSIVE option is set to YES. The TRIGGERMAXDEPTH option governs the depth of recursion of \$NATRIGGER expressions and prevents infinite recursions or excessively deep recursions, which can cause Oracle OLAP to malfunction.

#### Examples

Example 5-106 Setting the Maximum Trigger Depth

This example sets the maximum trigger depth, exceeds it, then sets the depth to a higher value. Usually the TRIGGERMAXDEPTH value would be much higher than `2`, which is used in this example. The default value is `50`.

    DEFINE d1 INTEGER DIMENSION
    MAINTAIN d1 ADD 2
    DEFINE v1 DECIMAL <d1>
    PROPERTY '$NATRIGGER' 'v2 + 1'
    DEFINE v2 DECIMAL <d1>
    PROPERTY '$NATRIGGER' 'v3 + 1'
    DEFINE v3 DECIMAL <d1>
    PROPERTY '$NATRIGGER' 'v4 + 1'
    DEFINE v4 DECIMAL <d1>
    v4(d1 1) = 333.3
    RECURSIVE = YES
    TRIGGERMAXDEPTH = 2
    SHOW v1
     

The preceding statements produce the following output.

    ERROR: Depth of NA trigger calls exceeds allowable (maximum depth 2)

The following statements set the maximum trigger depth to a higher value and show the value of the variable.

    TRIGGERMAXDEPTH = 3
    SHOW v1

The preceding statements produce the following output.

    336.3

### 5.105 TRIGGERSTOREOK

The TRIGGERSTOREOK option controls whether you can use \$STORETRIGGERVAL properties to specify that `NA` values in an object be permanently replaced by the values specified by a \$NATRIGGER property.

**Note:**

The value of the TRIGGERSTOREOK option is only one factor that Oracle OLAP uses to determine what to do with variable data that is the result of \$NATRIGGER expression execution. For a discussion of the other factors and their interrelationship, see "[How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER](olap-dml-properties.md)".

#### Data Type

BOOLEAN

#### Syntax

TRIGGERSTOREOK = {NO\|YES}

#### Parameters

NO
(Default) `NA` values are not permanently replaced with the \$NATRIGGER property expression that is set for a variable.

YES
`NA` values are permanently replaced with the \$NATRIGGER property expression that is set for a variable. The default value is `NO`.

For Oracle OLAP to permanently replace `NA` values for a variable with the valid \$NATRIGGER property expression that is set for the variable, you must set both the TRIGGERSTOREOK option and the \$STORETRIGGERVAL property for the variable to YES.

#### Usage Notes

About the \$NATRIGGER and STORETRIGGERVAL Properties

The TRIGGERSTOREOK option works with the \$NATRIGGER and \$STORETRIGGERVAL properties of a variable.

#### Examples

Example 5-107 Replacing NA Values Temporarily

This example replaces the `NA` values in the cells of a variable temporarily. The following statements define a dimension with three values and define a variable dimensioned by the dimension. They add the \$NATRIGGER property to the variable, then put a value in one cell of the variable and leave the other cells empty, so that their values are `NA`. Finally, they report the values in the cells of the variable.

    DEFINE d1 INTEGER DIMENSION
    MAINTAIN d1 ADD 3
    DEFINE v1 DECIMAL <d1>
    PROPERTY '$NATRIGGER' '500.0'
    v1(d1 1) = 333.3
     
    REPORT v1

The preceding statements produce the following output.

    D1            V1
    --------- ----------
            1     333.30
            2     500.00
            3     500.00

This statement deletes the \$NATRIGGER property from the `v1` variable.

    CONSIDER v1
    PROPERTY DELETE '$NATRIGGER'
    REPORT v1

The preceding statements produce the following output.

    D1            V1
    --------- ----------
            1     333.30
            2         NA
            3         NA

Example 5-108 Replacing NA Values Permanently

The following statements add the \$NATRIGGER property to the `v1` variable that was defined in the previous example and set the TRIGGERSTOREOK option and the \$STORETRIGGERVAL properties to YES. They then report the values in the cells of the variable.

    CONSIDER v1
    PROPERTY '$NATRIGGER' '800.0'
    TRIGGERSTOREOK = YES
    PROPERTY 'STORETRIGGERVAL' YES
    REPORT v1

The preceding statements produce the following output.

    D1                 V1
    -------------- ----------
                 1     333.30
                 2     800.00
                 3     800.00

The following statements delete the \$NATRIGGER property from the `v1` variable and report the values in the cells of the variable.

    CONSIDER v1
    PROPERTY DELETE '$NATRIGGER'
    REPORT v1

The preceding statements produce the following output.

    D1                 V1
    -------------- ----------
                 1     333.30
                 2     800.00
                 3     800.00

### 5.106 USERID

(Read-only) The USERID option holds the user ID for the current Oracle Database session which is the same value as that returned by SYSINFO(USER).

#### Data Type

TEXT

#### Syntax

USERID

#### Examples

Example 5-109 Displaying the Session User ID

This statement displays the Oracle user ID associated with the current session.

    SHOW USERID

### 5.107 USETRIGGERS

The USETRIGGERS option determines if a trigger program as triggers execute.

**Tip:**

Oracle OLAP does not support recursive triggers. Set the USETRIGGERS option to `NO` before you issue the same DML statement within a trigger program that triggered the program itself. For example, assume that you have written a TRIGGER_DEFINE program. Within the TRIGGER_DEFINE program, you must set the USETRIGGERS option to `NO` before you issue a DEFINE statement

**See Also:**

"[Trigger Programs](olap-dml-programs.md)"

#### Data Type

BOOLEAN

#### Syntax

USETRIGGERS = {NO\|YES}

#### Parameters

YES
(Default) Trigger programs execute.

NO
Trigger programs do not execute.

#### Examples

Example 5-110 Changing USETRIGGERS to NO

Assume you have just created a new analytic workspace. As illustrated in the following statement, the default value of the USETRIGGERS option is `YES`, but you can set the option to `NO` at any time.

    SHOW USETRIGGERS
    yes


    USETRIGGERS = NO
    SHOW USETRIGGERS
    no

### 5.108 VARCACHE

The VARCACHE option specifies whether Oracle OLAP stores or caches all variable data that is the result of the execution of an AGGREGATE function or \$NATRIGGER property expression.

**Note:**

The value of the VARCACHE option is only one factor that Oracle OLAP uses to determine whether variable data computed when the AGGREGATE function or \$NATRIGGER property executes is stored or cached. For a discussion of the other factors and their interrelationship, see "[How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER](olap-dml-properties.md)" and "[How Oracle OLAP Determines Whether to Store or Cache Aggregated Data](olap-dml-properties.md)".

#### Syntax

VARCACHE = {VARIABLE \| SESSION \| NONE}

#### Parameters

VARIABLE
Specifies that Oracle OLAP stores the data in the variable in the database. When you specify this option, the results of the calculation are permanently stored in the variable when the analytic workspace is updated and committed.

SESSION
Specifies that Oracle OLAP caches the calculated data in the session cache (See "What is an Oracle OLAP Session Cache?"). When you specify this option, the results of the calculation are ignored during updates and commits and are discarded after the session.

**Note:**

When SESSCACHE is set to `NO`, Oracle OLAP does not cache the data even when you specify `SESSION`. In this case, specifying `SESSION` is the same as specifying `NONE`.

NONE
For data that is calculated on the fly using the AGGREGATE function, specifies that Oracle OLAP calculates the data each time the AGGREGATE function executes; Oracle OLAP does not store or cache the data calculated by the AGGREGATE function

#### Usage Notes

The VARCACHE Option Can Affect All Variables

When you set the VARCACHE option, its setting can affect all variables. When you have not set the `$VARCACHE` property on a variable and there is no CACHE statement in the aggmaps that you use with the AGGREGATE function to calculate data on the fly, then it is the VARCACHE option that determines how or if that data is stored.

### 5.109 WEEKDAYSNEWYEAR

For a dimension of type WEEK, the WEEKDAYSNEWYEAR option determines how many days of the new year there must be for a week to be identified as week 1 of the new year.

By default, week 1 in a given year is the first week that contains at least one day in the new year. For example, January 1, 2000, is a Saturday. Using the default, the first week in that year (`W1.00`) is the period from Sunday, December 26, 1999, through Saturday, January 1, 2000.

Using WEEKDAYSNEWYEAR, you can specify how many days of the year must be present in week 1 in that year. When you use WEEKDAYSNEWYEAR to specify that the first week in a year must contain two or more days, then the week of December 26, 1999, through January 1, 2000, is the last week in 1999 (`W53.99`), and the week of January 2 through January 8 is the first week in the year 2000 (`W1.00`).

#### Data Type

`INTEGER`

#### Syntax

WEEKDAYSNEWYEAR = days

#### Parameters

days
An `INTEGER` expression in the range 1 through 7 that indicates how many days in the year must be present in week 1 of that year. The default value for days is `1`.

#### Examples

The Effect of WEEKDAYSNEWYEAR

The following statements send a list of weeks with the associated ending dates for each of those weeks to the current outfile.

    DEFINE week DIMENSION WEEK
    MAINTAIN week ADD '12 18 99' '1 15 00'
    weekdaysnewyear = 2
    REPORT W 22 CONVERT(week date)

These statements produce the following output.

    WEEK             CONVERT(WEEK DATE)
    -------------- --------------------
    W51.99         18DEC99
    W52.99         25DEC99
    W53.99         01JAN00
    W1.00          08JAN00
    W2.00          15JAN00

January 1, 2000, is a Saturday, so setting WEEKDAYSNEWYEAR to `2` causes the week from January 2 through January 8 to appear as `W1.00`.

### 5.110 WRAPERRORS

The WRAPERRORS option determines if Oracle OLAP displays long error messages as multiple lines with each line being 72 characters in length.

#### Data Type

`BOOLEAN`

#### Syntax

WRAPERRORS = NO \| YES

#### Parameters

NO
Error messages are not wrapped. (Default)

YES
Error message are wrapped. Oracle OLAP inserts a line break after each group of 72 characters.

#### Usage Notes

Change in Default Behavior as of Oracle OLAP 10.2

In pre 10.2 releases of Oracle OLAP, long error messages are always wrapped.

### 5.111 YESSPELL

(Read-only) The YESSPELL option holds the text that is used for `TRUE` Boolean values in the output of OLAP DML statements.

The value of the YESSPELL option is the word for "yes" in the current language, as specified by the NLS_LANGUAGE option. For example, when NLS_LANGUAGE is set to `American`, then the value of YESSPELL is `YES`. When NLS_LANGUAGE is set to `Spanish`, then the value of YESSPELL is `SI`.

#### Data Type

TEXT

#### Syntax

YESSPELL

#### Examples

Example 5-111 Seeing the Effect of the YESSPELL Value

Suppose you have a variable called BOOLVAR that currently has a value of `YES`. When "si" is the word for "yes" in the language specified by the NLS_LANGUAGE option,

    SHOW boolvar

produces the following output.

    si

### 5.112 YRABSTART

The YRABSTART option sets the specific 100-year period associated with years that are read or displayed using a two-digit abbreviation.

#### Data Type

`INTEGER`

#### Syntax

YRABSTART = year

#### Parameters

year
A four-digit `INTEGER` expression that indicates the year at which the 100-year period begins. You can specify any value in the range 1000 to 9999. However, when you specify a value greater than 9900 for year, requests to read or display two-digit year values that correspond to a year later than 9999 result in a return value of `NA`. The default is 1950; two-digit year abbreviations are interpreted as being in the range 1950 to 2049 unless a different range is set through YRABSTART.

#### Examples

Example 5-112 Using the Default Value

The following statements specify a date format and send output to the current outfile.

    DATEFORMAT = '<Mtextl> <d>, <yyyy>'
    SHOW MAKEDATE(96 9 13)

These statements produce the following output.

    September 13, 1996

Example 5-113 Setting the 100-Year Period for a Date

The following statements set a 100-year period of 2000 to 2099 and send the output to the current outfile.

    YRABSTART = 2000
    SHOW MAKEDATE(96 9 13)

These statements produce the following output.

    September 13, 2096

### 5.113 ZEROROW

For output produced by the REPORT and ROW commands, the ZEROROW option suppresses report rows with numeric values that are all NAs or all zeros or would be represented as zeros. When your report includes a small number, such as `0.004`, the number of decimal places being shown affects whether ZEROROW treats that number as zero. When you are producing a report with totals, the actual number is used to calculate the total, even when the number is suppressed.

#### Data Type

BOOLEAN

#### Syntax

ZEROROW = {YES\|NO}

#### Parameters

YES
Suppresses report rows that contain any numeric values when all the numeric values would be shown either as zeros or NAs.

NO
(Default) Produces all rows of the report, regardless of the values they contain.

#### Usage Notes

Non-Numeric Data

Even when a row contains non-numeric data, such as TEXT, ID, or BOOLEAN values, along with numeric values, the row is suppressed when ZEROROW is YES and all the numeric values would be shown either as zeros or NAs.

The Effect of NASPELL and ZSPELL

The value of NASPELL does not affect the way ZEROROW handles `NA` values. The value of ZSPELL does not affect the functioning of ZEROROW; numeric zero values are treated as zeros regardless of their spelling in output.

#### Examples

Example 5-114 Suppressing Report Rows of All-Zero Data

Suppose you have a variable called `worstcase`, that is dimensioned by `division`, `month`, and `line`, in which you store the results of calculations to project sales. When you produce a report of the results, you want to suppress any rows for which the value of the worst-case projections is zero for all months in the status. Set ZEROROW to YES, as shown in the following statements.

    ZEROROW = YES
    LIMIT line TO 'Revenue'
    LIMIT month TO 'Nov95' TO 'Feb96'
    REPORT WIDTH 8 DOWN division ACROSS month: worstcase

These statements produce the following report.

    LINE: REVENUE
             -----------------WORSTCASE-----------------
             -------------------MONTH-------------------
    DIVISION   Nov95      Dec95      Jan96      Feb96
    -------- ---------- ---------- ---------- ----------
    Camping        0.00       0.00  45,500.00  47,400.00
    Sporting       0.00       0.00  29,200.00  28,400.00
    Clothing       0.00       0.00  15,200.00  14,900.00

In the preceding report, no rows are suppressed, because some months for each division have projected sales. However, when you lay out this report with `month` down and `division` across, the rows for `Nov95` and `Dec95` are suppressed, because these months have no projected sales.

    REPORT DOWN month ACROSS division: worstcase

This statement produces the following report.

    LINE: REVENUE
                   -----------WORSTCASE------------
                   ------------DIVISION------------
    MONTH           Camping    Sporting   Clothing
    -------------- ---------- ---------- ----------
    Jan96           45,500.00  29,200.00  15,200.00
    Feb96           47,400.00  28,400.00  14,900.00

### 5.114 ZSPELL

The ZSPELL option holds the default text that is used for representing numeric zero values in output produced by the HEADING, REPORT, and ROW commands.

#### Data Type

TEXT

#### Syntax

ZSPELL = {'text'\|'OFF'}

#### Parameters

text
The spelling to use as the default spelling for numeric zero values. When you specify an expression rather than a text literal, you can omit the single quotes.

OFF
(Default) Shows a zero (0) with the appropriate number of decimal places (determined by a DECIMAL attribute) for each numeric zero value.

#### Usage Notes

Assigning Zero Values

ZSPELL affects output only; it does not affect the way you assign a zero value. For example, even when you have set ZSPELL to `NONE`, you still assign a zero value as follows.

    var1 = 0

Showing Decimal Places

The default of OFF means that a zero value is shown as 0 (zero), with the number of decimal places indicated by a DECIMAL attribute (for example, `0.00`). When you set ZSPELL to the text character `0`, zero values are shown as a `0` with no decimal places, regardless of any DECIMAL specification.

Effect of ZSPELL on Values Close to Zero

When your output includes a small number, such as `0.004`, the number of decimal places shown affects whether ZSPELL treats the number as zero. See Example 5-116.

#### Examples

Example 5-115 Showing Zero Values as NONE

This example changes the value of ZSPELL, so that a zero value in the DECIMAL variable `testvar` is shown as NONE in report output. When ZSPELL is set to its default value of `OFF`, the Oracle OLAP statements

    testvar = 0.00
    ROW testvar

produce the following output.

              0.00

In contrast, these OLAP DML statements

    ZSPELL = 'NONE'
    ROW testvar

produce the following output.

              NONE

Example 5-116 Showing Very Small Numbers

This example illustrates how the number of decimal places shown in output affects whether ZSPELL treats very small numbers as zeros. When ZSPELL is set to its default value of `OFF`, these OLAP DML statements

    ZSPELL = 'OFF'
    testvar = 0.004
    ROW DECIMAL 3 testvar

produce the following output.

              0.004

The following statements set ZSPELL to `NONE` and specify two decimal places for the output.

    ZSPELL = 'NONE'
    ROW DECIMAL 2 testvar

These statements produce the following output.

              NONE

With ZSPELL still set to `NONE`, the following statement specifies three decimal places for the output.

    ROW DECIMAL 3 testvar

This statement produces the following output.

              0.004
