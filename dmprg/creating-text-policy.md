An Oracle Text policy specifies how text content must be interpreted. You can provide a text policy to govern a model, an attribute, or both the model and individual attributes.

If a model-specific policy is present and one or more attributes have their own policies, Oracle Data Mining uses the attribute policies for the specified attributes and the model-specific policy for the other attributes.

The `CTX_DDL.CREATE_POLICY` procedure creates a text policy.

    CTX_DDL.CREATE_POLICY(
              policy_name    IN VARCHAR2,
                            filter         IN VARCHAR2 DEFAULT NULL,
                            section_group  IN VARCHAR2 DEFAULT NULL,
                            lexer          IN VARCHAR2 DEFAULT NULL,
                            stoplist       IN VARCHAR2 DEFAULT NULL,
                            wordlist       IN VARCHAR2 DEFAULT NULL);

The parameters of `CTX_DDL.CREATE_POLICY` are described in the following table.

Table 7-4 CTX_DDL.CREATE_POLICY Procedure Parameters

| Parameter Name  | Description                                                                                                                                                                                                                                                                                                                                 |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`   | Name of the new policy object. Oracle Text policies and text indexes share the same namespace.                                                                                                                                                                                                                                              |
| `filter`        | Specifies how the documents must be converted to plain text for indexing. Examples are: `CHARSET_FILTER` for character sets and `NULL_FILTER` for plain text, HTML and XML.<br>For `filter` values, see "[Filter Types](../ccref/oracle-text-indexing-elements.md)" in Oracle Text Reference.                                               |
| `section_group` | Identifies sections within the documents. For example, `HTML_SECTION_GROUP` defines sections in HTML documents.<br>For `section_group` values, see "[Section Group Types](../ccref/oracle-text-indexing-elements.md)" in Oracle Text Reference.<br>Note: You can specify any section group that is supported by `CONTEXT` indexes.          |
| `lexer`         | Identifies the language that is being indexed. For example, `BASIC_LEXER` is the lexer for extracting terms from text in languages that use white space delimited words (such as English and most western European languages).<br>For `lexer` values, see "[Lexer Types](../ccref/index.md)" in Oracle Text Reference.                      |
| `stoplist`      | Specifies words and themes to exclude from term extraction. For example, the word "the" is typically in the stoplist for English language documents.<br>The system-supplied stoplist is used by default.<br>See "[Stoplists](../ccref/oracle-text-indexing-elements.md)" in Oracle Text Reference.                                          |
| `wordlist`      | Specifies how stems and fuzzy queries must be expanded. A stem defines a root form of a word so that different grammatical forms have a single representation. A fuzzy query includes common misspellings in the representation of a word.<br>See "[`BASIC_WORDLIST`](../ccref/oracle-text-indexing-elements.md)" in Oracle Text Reference. |

**Related Topics**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md)
