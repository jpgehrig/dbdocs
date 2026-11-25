## 4 Special Characters in Oracle Text Queries

This chapter describes the special characters that can be used in Text queries. In addition, it provides a list of the words and characters that Oracle Text treats as reserved words and characters.

The following topics are covered in this chapter:

- Grouping Characters

- Escape Characters

- Reserved Words and Characters

### 4.1 Grouping Characters

The grouping characters control operator precedence by grouping query terms and operators in a query expression. The grouping characters are described in Table 4-1.

Table 4-1 Characters for Grouping Query Terms

| Grouping Character | Description                                                                                                                                                                    |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ( )                | The parentheses characters serve to group terms and operators found between the characters                                                                                     |
| \[ \]              | The bracket characters serve to group terms and operators found between the characters; however, they prevent penetrations for the expansion operators (fuzzy, soundex, stem). |

The beginning of a group of terms and operators is indicated by an open character from one of the sets of grouping characters. The ending of a group is indicated by the occurrence of the appropriate close character for the open character that started the group. Between the two characters, other groups may occur.

For example, the open parenthesis indicates the beginning of a group. The first close parenthesis encountered is the end of the group. Any open parentheses encountered before the close parenthesis indicate nested groups.

### 4.2 Escape Characters

To query on words or symbols that have special meaning in query expressions such as and & or\| accum, you must escape them. There are two ways to escape characters in a query expression, as described in Table 4-2.

Table 4-2 Characters for Escaping Query Terms

| Escape Character | Description                                                                                                                                                                                                                                            |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| {}               | Use braces to escape a string of characters or symbols. Everything within a set of braces in considered part of the escape sequence.<br>When you use braces to escape a single character, the escaped character becomes a separate token in the query. |
| \\               | Use the backslash character to escape a single character or symbol. Only the character immediately following the backslash is escaped. For example, a query of blue\\green matches blue-green and blue green.                                          |

In the following examples, an escape sequence is necessary because each expression contains a Text operator or reserved symbol:

    'high\-voltage'
    '{high-voltage}'

    'XY\&Z'
    '{XY&Z}'

In the first example, the query matches high-voltage or high voltage.

Note that in the second example, a query on XY&Z will return 'XY Z', 'XY-Z', 'XY\*Z', and so forth, as well as 'XY&Z'. This is because non-alphabetic characters are treated as whitespace (so XY&Z is treated as 'XY Z'). To match only XY&Z, you must declare & as a printjoin. (If you do, however, XY&Z will not match 'XY & Z'.) For more on printjoins, see [BASIC_LEXER](oracle-text-indexing-elements.md).

**Note:**

If you use braces to escape an individual character within a word, the character is escaped, but the word is broken into three tokens. For example, a query written as high{-}voltage searches for high - voltage, with the space on either side of the hyphen.

#### Querying Escape Characters

The open brace { signals the beginning of the escape sequence, and the closed brace } indicates the end of the sequence. Everything between the opening brace and the closing brace is part of the escaped query expression (including any open brace characters). To include the close brace character in an escaped query expression, use `}}`. To escape the backslash escape character, use `\\`.

### 4.3 Reserved Words and Characters

Table 4-3 lists the Oracle Text reserved words and characters that must be escaped when you want to search them in `CONTAINS` queries. Refer to Table 4-2 for the rule for when to use braces {} or the backslash \\ for the escape sequence.

Table 4-3 Reserved Words and Characters

| Reserved Words | Reserved Characters | Operator                      |
|:---------------|:--------------------|:------------------------------|
| ABOUT          | (none)              | ABOUT                         |
| ACCUM          | ,                   | Accumulate                    |
| AND            | &                   | And                           |
| BT             | (none)              | Broader Term                  |
| BTG            | (none)              | Broader Term Generic          |
| BTI            | (none)              | Broader Term Instance         |
| BTP            | (none)              | Broader Term Partitive        |
| EQUIV          | =                   | Equivalence                   |
| FUZZY          | ?                   | fuzzy                         |
| (none)         | { }                 | escape characters (multiple)  |
| (none)         | \\                  | escape character (single)     |
| (none)         | ( )                 | grouping characters           |
| (none)         | \[ \]               | grouping characters           |
| HASPATH        | (none)              | HASPATH                       |
| INPATH         | (none)              | INPATH                        |
| MDATA          | (none)              | MDATA                         |
| MINUS          | \-                  | MINUS                         |
| NEAR           | ;                   | NEAR                          |
| NOT            | ~                   | NOT                           |
| NT             | (none)              | Narrower Term                 |
| NTG            | (none)              | Narrower Term Generic         |
| NTI            | (none)              | Narrower Term Instance        |
| NTP            | (none)              | Narrower Term Partitive       |
| OR             | \|                  | OR                            |
| PATTERN        | (none)              | PATTERN                       |
| PT             | (none)              | Preferred Term                |
| RT             | (none)              | Related Term                  |
| (none)         | \$                  | stem                          |
| (none)         | !                   | soundex                       |
| SQE            | (none)              | Stored Query Expression       |
| SYN            | (none)              | Synonym                       |
| (none)         | \>                  | threshold                     |
| TR             | (none)              | Translation Term              |
| TRSYN          | (none)              | Translation Term Synonym      |
| TT             | (none)              | Top Term                      |
| (none)         | \*                  | weight                        |
| (none)         | %                   | wildcard character (multiple) |
| (none)         | \_                  | wildcard character (single)   |
| WITHIN         | (none)              | WITHIN                        |
