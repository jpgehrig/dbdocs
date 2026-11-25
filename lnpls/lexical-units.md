## 2.2 Lexical Units

The lexical units of PL/SQL are its smallest individual components—delimiters, identifiers, literals, pragmas, and comments.

### Topics

- Delimiters

- Identifiers

- Literals

- Pragmas

- Comments

- Whitespace Characters Between Lexical Units

### 2.2.1 Delimiters

A delimiter is a character, or character combination, that has a special meaning in PL/SQL.

Do not embed any others characters (including whitespace characters) inside a delimiter.

Table 2-2 summarizes the PL/SQL delimiters.

Table 2-2 PL/SQL Delimiters

| Delimiter | Meaning                                     |
|:----------|:--------------------------------------------|
| `+`       | Addition operator                           |
| `:=`      | Assignment operator                         |
| `=>`      | Association operator                        |
| `%`       | Attribute indicator                         |
| `'`       | Character string delimiter                  |
| `.`       | Component indicator                         |
| `||`      | Concatenation operator                      |
| `/`       | Division operator                           |
| `**`      | Exponentiation operator                     |
| `(`       | Expression or list delimiter (begin)        |
| `)`       | Expression or list delimiter (end)          |
| `:`       | Host variable indicator                     |
| `,`       | Item separator                              |
| `<<`      | Label delimiter (begin)                     |
| `>>`      | Label delimiter (end)                       |
| `/*`      | Multiline comment delimiter (begin)         |
| `*/`      | Multiline comment delimiter (end)           |
| `*`       | Multiplication operator                     |
| `"`       | Quoted identifier delimiter                 |
| `..`      | Range operator                              |
| `=`       | Relational operator (equal)                 |
| `<>`      | Relational operator (not equal)             |
| `!=`      | Relational operator (not equal)             |
| `~=`      | Relational operator (not equal)             |
| ` ^=`     | Relational operator (not equal)             |
| `<`       | Relational operator (less than)             |
| `>`       | Relational operator (greater than)          |
| `<=`      | Relational operator (less than or equal)    |
| `>=`      | Relational operator (greater than or equal) |
| `@`       | Remote access indicator                     |
| `--`      | Single-line comment indicator               |
| `;`       | Statement terminator                        |
| `-`       | Subtraction or negation operator            |

### 2.2.2 Identifiers

Identifiers name PL/SQL elements, which include:

- Constants

- Cursors

- Exceptions

- Keywords

- Labels

- Packages

- Reserved words

- Subprograms

- Types

- Variables

Every character in an identifier, alphabetic or not, is significant. For example, the identifiers `lastname` and `last_name` are different.

You must separate adjacent identifiers by one or more whitespace characters or a punctuation character.

Except as explained in "Quoted User-Defined Identifiers", PL/SQL is case-insensitive for identifiers. For example, the identifiers `lastname`, `LastName`, and `LASTNAME` are the same.

#### Topics

- Reserved Words and Keywords

- Predefined Identifiers

- User-Defined Identifiers

#### 2.2.2.1 Reserved Words and Keywords

Reserved words and keywords are identifiers that have special meaning in PL/SQL.

You cannot use reserved words as ordinary user-defined identifiers. You can use them as quoted user-defined identifiers, but it is not recommended. For more information, see "Quoted User-Defined Identifiers".

You can use keywords as ordinary user-defined identifiers, but it is not recommended.

For lists of PL/SQL reserved words and keywords, see [Table D-1](plsql-reserved-words-keywords.md) and [Table D-2](plsql-reserved-words-keywords.md), respectively.

#### 2.2.2.2 Predefined Identifiers

Predefined identifiers are declared in the predefined package `STANDARD`.

An example of a predefined identifier is the exception `INVALID_NUMBER`.

For a list of predefined identifiers, connect to Oracle Database as a user who has the DBA role and use this query:

    SELECT TYPE_NAME FROM ALL_TYPES WHERE PREDEFINED='YES';

You can use predefined identifiers as user-defined identifiers, but it is not recommended. Your local declaration overrides the global declaration (see "[Scope and Visibility of Identifiers](scope-and-visibility-identifiers.md)").

#### 2.2.2.3 User-Defined Identifiers

A user-defined identifier is:

- Composed of characters from the database character set

- Either ordinary or quoted

**Tip:**

Make user-defined identifiers meaningful. For example, the meaning of `cost_per_thousand` is obvious, but the meaning of `cpt` is not.

**Tip:**

Avoid using the same user-defined identifier for both a schema and a schema object. This decreases code readability and maintainability and can lead to coding mistakes. Note that local objects have name resolution precedence over schema qualification.

For more information about database object naming rules, see [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md).

For more information about PL/SQL-specific name resolution rules, see "[Differences Between PL/SQL and SQL Name Resolution Rules](differences-pl-sql-and-sql-name-resolution-rules.md)".

##### 2.2.2.3.1 Ordinary User-Defined Identifiers

An ordinary user-defined identifier:

- Begins with a letter

- Can include letters, digits, and these symbols:

  - Dollar sign (\$)

  - Number sign (#)

  - Underscore (\_)

- Is not a reserved word (listed in [Table D-1](plsql-reserved-words-keywords.md)).

The database character set defines which characters are classified as letters and digits. If COMPATIBLE is set to a value of 12.2 or higher, the representation of the identifier in the database character set cannot exceed 128 bytes. If COMPATIBLE is set to a value of 12.1 or lower, the limit is 30 bytes.

Examples of acceptable ordinary user-defined identifiers:

    X
    t2
    phone#
    credit_limit
    LastName
    oracle$number
    money$$$tree
    SN##
    try_again_

Examples of unacceptable ordinary user-defined identifiers:

    mine&yours
    debit-amount
    on/off
    user id

##### 2.2.2.3.2 Quoted User-Defined Identifiers

A quoted user-defined identifier is enclosed in double quotation marks.

Between the double quotation marks, any characters from the database character set are allowed except double quotation marks, new line characters, and null characters. For example, these identifiers are acceptable:

    "X+Y"
    "last name"
    "on/off switch"
    "employee(s)"
    "*** header info ***"

If COMPATIBLE is set to a value of 12.2 or higher, the representation of the quoted identifier in the database character set cannot exceed 128 bytes (excluding the double quotation marks). If COMPATIBLE is set to a value of 12.1 or lower, the limit is 30 bytes.

A quoted user-defined identifier is case-sensitive, with one exception: If a quoted user-defined identifier, without its enclosing double quotation marks, is a valid ordinary user-defined identifier, then the double quotation marks are optional in references to the identifier, and if you omit them, then the identifier is case-insensitive.

It is not recommended, but you can use a reserved word as a quoted user-defined identifier. Because a reserved word is not a valid ordinary user-defined identifier, you must always enclose the identifier in double quotation marks, and it is always case-sensitive.

Example 2-1 Valid Case-Insensitive Reference to Quoted User-Defined Identifier

In this example, the quoted user-defined identifier `"HELLO"`, without its enclosing double quotation marks, is a valid ordinary user-defined identifier. Therefore, the reference `Hello` is valid.

    DECLARE
      "HELLO" varchar2(10) := 'hello';
    BEGIN
      DBMS_Output.Put_Line(Hello);
    END;
    /

Result:

    hello

Example 2-2 Invalid Case-Insensitive Reference to Quoted User-Defined Identifier

In this example, the reference `"Hello"` is invalid, because the double quotation marks make the identifier case-sensitive.

    DECLARE
      "HELLO" varchar2(10) := 'hello';
    BEGIN
      DBMS_Output.Put_Line("Hello");
    END;
    /

Result:

      DBMS_Output.Put_Line("Hello");
                            *
    ERROR at line 4:
    ORA-06550: line 4, column 25:
    PLS-00201: identifier 'Hello' must be declared
    ORA-06550: line 4, column 3:
    PL/SQL: Statement ignored

Example 2-3 Reserved Word as Quoted User-Defined Identifier

This example declares quoted user-defined identifiers `"BEGIN"`, `"Begin"`, and `"begin"`. Although `BEGIN`, `Begin`, and `begin` represent the same reserved word, `"BEGIN"`, `"Begin"`, and `"begin"` represent different identifiers.

    DECLARE
      "BEGIN" varchar2(15) := 'UPPERCASE';
      "Begin" varchar2(15) := 'Initial Capital';
      "begin" varchar2(15) := 'lowercase';
    BEGIN
      DBMS_Output.Put_Line("BEGIN");
      DBMS_Output.Put_Line("Begin");
      DBMS_Output.Put_Line("begin");
    END;
    /

Result:

    UPPERCASE
    Initial Capital
    lowercase

    PL/SQL procedure successfully completed.

Example 2-4 Neglecting Double Quotation Marks

This example references a quoted user-defined identifier that is a reserved word, neglecting to enclose it in double quotation marks.

    DECLARE
      "HELLO" varchar2(10) := 'hello';  -- HELLO is not a reserved word
      "BEGIN" varchar2(10) := 'begin';  -- BEGIN is a reserved word
    BEGIN
      DBMS_Output.Put_Line(Hello);      -- Double quotation marks are optional
      DBMS_Output.Put_Line(BEGIN);      -- Double quotation marks are required
    end;
    /

Result:

      DBMS_Output.Put_Line(BEGIN);      -- Double quotation marks are required
                           *
    ERROR at line 6:
    ORA-06550: line 6, column 24:
    PLS-00103: Encountered the symbol "BEGIN" when expecting one of the following:
    ( ) - + case mod new not null <an identifier>

    table continue avg count current exists max min prior sql
    stddev sum variance execute multiset the both leading
    trailing forall merge year month day hour minute second
    timezone_hour timezone_minute timezone_region timezone_abbr
    time timestamp interval date
    y THEN max:=x;ELSE max:=y;END IF;  -- correct but hard to read

      -- Easier to read:

      IF x > y THEN
        max:=x;
      ELSE
        max:=y;
      END IF;
    END;
    /
