SQL/JSON conditions `is json` and `is not json` are complementary. They test whether their argument is syntactically correct, that is, well-formed, JSON data. You can use them in a `CASE` expression or the `WHERE` clause of a `SELECT` statement. You can use `is json` in a check constraint.

If the argument is syntactically correct then `is json` returns true and `is not json` returns false.

If an error occurs during parsing then the error is not raised, and the data is considered to not be well-formed: `is json` returns false; `is not json` returns true. If an error occurs other than during parsing then that error is raised.

**Well-formed** data means syntactically correct data. JSON data stored textually can be well-formed in two senses, referred to as strict and lax syntax. In addition, for textual JSON data you can specify whether a JSON object can have duplicate fields (keys).

Whenever textual JSON data is generated inside the database it satisfies condition `is json` with keyword `STRICT`. This includes generation in these ways:

- Using a SQL/JSON generation function (unless you specify keyword `STRICT` with either `FORMAT JSON` or `TREAT AS JSON`, which means that you declare that the data is JSON data; you vouch for it, so its well-formedness is not checked)

- Using SQL function `json_serialize`

- Using SQL function `to_clob`, `to_blob`, or `to_varchar2` on a PL/SQL DOM

- Using SQL/JSON function `json_query`

- Using SQL/JSON function `json_table` with `FORMAT JSON`

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SQL-JSON-Conditions.md) for information about `is json` and `is not json`.

- Unique Versus Duplicate Fields in JSON Objects
  By default, field names need not be unique for a given JSON object. But you can specify that particular JSON data is to be considered well-formed only if none of its objects have duplicate field names.
- About Strict and Lax JSON Syntax
  The Oracle default syntax for JSON is lax. In particular: it reflects the JavaScript syntax for object fields; the Boolean and null values are not case-sensitive; and it is more permissive with respect to numerals, whitespace, and escaping of Unicode characters.
- Specifying Strict or Lax JSON Syntax
  The default JSON syntax for Oracle Database is lax. Strict or lax syntax matters only for SQL/JSON conditions `is json` and `is not json`. All other SQL/JSON functions and conditions use lax syntax for interpreting input and strict syntax when returning output.

**Related Topics**

- [Creating a Table With a JSON Column](creating-a-table-with-a-json-column.md)

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)

### 5.1 Unique Versus Duplicate Fields in JSON Objects

By default, field names need not be unique for a given JSON object. But you can specify that particular JSON data is to be considered well-formed only if none of its objects have duplicate field names.

The JSON standard does not specify whether field names must be unique for a given JSON object. This means that, a priori, a well-formed JSON object can have multiple members that have the same field name. This is the default behavior for handling JSON data in Oracle Database because checking for duplicate names takes additional time.

You can specify that particular JSON data is to be considered well-formed only if all of the objects it contains have unique field names, that is, no object has duplicate field names. You do this by using the keywords `WITH UNIQUE KEYS` with SQL/JSON condition `is json`.<sup>Foot 1</sup>

If you do not specify `UNIQUE KEYS`, or if you use the keywords `WITHOUT UNIQUE KEYS`, then objects can have duplicate field names and still be considered well-formed.

The evaluation that Oracle Database employs always uses only one of the object members that have a given field name; any other members with the same field name are ignored. It is unspecified which of multiple such members is used.

Whether duplicate field names are allowed in well-formed JSON data is orthogonal to whether Oracle uses strict or lax syntax to determine well-formedness.

**Parent topic:** SQL/JSON Conditions IS JSON and IS NOT JSON

### 5.2 About Strict and Lax JSON Syntax

The Oracle default syntax for JSON is lax. In particular: it reflects the JavaScript syntax for object fields; the Boolean and null values are not case-sensitive; and it is more permissive with respect to numerals, whitespace, and escaping of Unicode characters.

Standard ECMA-404, the JSON Data Interchange Format, and ECMA-262, the ECMAScript Language Specification, define JSON syntax.

According to these specifications, each JSON field and each string value must be enclosed in double quotation marks (`"`). Oracle supports this **strict JSON syntax**, but it is not the default syntax.

In JavaScript notation, a field used in an object literal can be, but need not be, enclosed in double quotation marks. It can also be enclosed in single quotation marks (`'`). Oracle also supports this **lax JSON syntax**, and it is the default syntax.

In addition, in practice, some JavaScript implementations (but not the JavaScript standard) allow one or more of the following:

- Case variations for keywords `true`, `false`, and `null` (for example, `TRUE`, `True`, `TrUe`, `fALSe`, `NulL`).

- An extra comma (`,`) after the last element of an array or the last member of an object (for example, `[a, b, c``,``]`, `{a:b, c:d``,``}`).

- Numerals with one or more leading zeros (for example, `0042.3`).

- Fractional numerals that lack `0` before the decimal point (for example, `.14` instead of `0.14`).

- Numerals with no fractional part after the decimal point (for example, `342.` or `1.e27`).

- A plus sign (`+`) preceding a numeral, meaning that the number is non-negative (for example, `+1.3`).

This syntax too is allowed as part of the Oracle default (lax) JSON syntax. (See the JSON standard for the strict numeral syntax.)

In addition to the ASCII space character (U+0020), the JSON standard defines the following characters as insignificant (ignored) whitespace when used outside a quoted field or a string value:

- Tab, horizontal tab (`HT`, ` ^I`, decimal 9, U+0009, `\t`)

- Line feed, newline (`LF`, ` ^J`, decimal 10, U+000A, `\n`)

- Carriage return (`CR`, ` ^M`, decimal 13, U+000D, `\r`)

The lax JSON syntax, however, treats all of the ASCII control characters (Control+0 through Control+31), as well as the ASCII space character (decimal 32, U+0020), as (insignificant) whitespace characters. The following are among the control characters:

- Null (`NUL`, ` ^@`, decimal 0, U+0000, `\0`)

- Bell (`NEL`, ` ^G`, decimal 7, U+0007,` \a`)

- Vertical tab (`VT`, ` ^K`, decimal 11, U+000B)

- Escape (`ESC`, ` ^[`, decimal 27, U+001B, `\e`)

- Delete (`DEL`, ` ^?`, decimal 127, U+007F)

An ASCII space character (U+0020) is the only whitespace character allowed, unescaped, within a quoted field or a string value. This is true for both the lax and strict JSON syntaxes.

For both strict and lax JSON syntax, quoted object field and string values can contain any Unicode character, but some of them must be escaped, as follows:

- ASCII control characters are not allowed, except for those represented by the following escape sequences: `\b` (backspace), `\f` (form feed), `\n` (newline, line feed), `\r` (carriage return), and `\t` (tab, horizontal tab).

- Double quotation mark (`"`), slash (`/`), and backslash (`\`) characters must also be escaped (preceded by a backslash): `\"`, `\/`, and `\\`, respectively.

In the lax JSON syntax, an object field that is not quoted can contain any Unicode character except whitespace and the JSON structural characters — left and right brackets (`[`, `]`) and curly braces (`{`, `}`), colon (`:`), and comma (`,`), but escape sequences are not allowed.

Any Unicode character can also be included in a name or string by using the ASCII escape syntax `\u` followed by the four ASCII hexadecimal digits that represent the Unicode code point.

Note that other Unicode characters that are not printable or that might appear as whitespace, such as a no-break space character (U+00A0), are not considered whitespace for either the strict or the lax JSON syntax.

Table 5-1 shows some examples of JSON syntax.

Table 5-1 JSON Object Field Syntax Examples

| Example                  | Well-Formed?                                                                                                                                                                  |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `"part number": 1234`    | Lax and strict: yes. Space characters are allowed.                                                                                                                            |
| `part number: 1234`      | Lax (and strict): no. Whitespace characters, including space characters, are not allowed in unquoted names.                                                                   |
| `"part\tnumber": 1234`   | Lax and strict: yes. Escape sequence for tab character is allowed.                                                                                                            |
| `"part    number": 1234` | Lax and strict: no. Unescaped tab character is not allowed. Space is the only unescaped whitespace character allowed.                                                         |
| `"\"part\"number": 1234` | Lax and strict: yes. Escaped double quotation marks are allowed, if name is quoted.                                                                                           |
| `\"part\"number: 1234`   | Lax and strict: no. Name must be quoted.                                                                                                                                      |
| `'\"part\"number': 1234` | Lax: yes, strict: no. Single-quoted names (object fields and strings) are allowed for lax syntax only. Escaped double quotation mark is allowed in a quoted name.             |
| `"pärt : number":1234`   | Lax and strict: yes. Any Unicode character is allowed in a quoted name. This includes whitespace characters and characters, such as colon (`:`), that are structural in JSON. |
| `part:number:1234`       | Lax (and strict): no. Structural characters are not allowed in unquoted names.                                                                                                |

**Related Topics**

- [JSON Syntax and the Data It Represents](json-data.md)

**See Also:**

- [IETF RFC4627](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=tools_ietf_rfc4627) and [ECMA 404](https://ecma-international.org/publications-and-standards/standards/ecma-404/) for the syntax of JSON Data Interchange Format

- [ECMA International](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=ecma_international) and [JSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=json_org) for more information about JSON and JavaScript

**Parent topic:** SQL/JSON Conditions IS JSON and IS NOT JSON

### 5.3 Specifying Strict or Lax JSON Syntax

The default JSON syntax for Oracle Database is lax. Strict or lax syntax matters only for SQL/JSON conditions `is json` and `is not json`. All other SQL/JSON functions and conditions use lax syntax for interpreting input and strict syntax when returning output.

If you need to be sure that particular JSON input data has strictly correct syntax, then check it first using `is json` or `is not json`.

You specify that data is to be checked as strictly well-formed according to the JSON standard by appending `(STRICT)` (parentheses included) to an `is json` or an `is not json` expression.

Example 5-1 illustrates this. It is identical to [Example 4-1](creating-a-table-with-a-json-column.md) except that it uses `(STRICT)` to ensure that all data inserted into the column is well-formed according to the JSON standard.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about` CREATE TABLE`

Example 5-1 Using IS JSON in a Check Constraint to Ensure JSON Data is Strictly Well-Formed (Standard)

    CREATE TABLE j_purchaseorder
      (id          VARCHAR2 (32) NOT NULL PRIMARY KEY,
       date_loaded TIMESTAMP (6) WITH TIME ZONE,
       po_document VARCHAR2 (32767)
       CONSTRAINT ensure_json CHECK (po_document IS JSON (STRICT)));

**Related Topics**

- About Strict and Lax JSON Syntax

**Parent topic:** SQL/JSON Conditions IS JSON and IS NOT JSON

------------------------------------------------------------------------



Footnote Legend

Footnote 1: An object field is sometimes called an object “key”.
