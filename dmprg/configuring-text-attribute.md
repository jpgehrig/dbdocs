Learn how to identify a column as a text attribute and provide transformation instructions for any text attribute.

As shown in [Table 7-2](creating-model-that-includes-text-mining.md), you can identify columns of `CHAR,`shorter `VARCHAR2` (\<=4000), `BFILE`, and `BLOB` as text attributes. If `CHAR` and shorter `VARCHAR2` columns are not explicitly identified as unstructured text, then `CREATE_MODEL` processes them as categorical attributes. If `BFILE` and `BLOB` columns are not explicitly identified as unstructured text, then `CREATE_MODEL` returns an error.

To identify a column as a text attribute, supply the keyword `TEXT` in an **Attribute specification**. The attribute specification is a field (`attribute_spec`) in a transformation record (`transform_rec`). Transformation records are components of transformation lists (`xform_list`) that can be passed to `CREATE_MODEL`.

**Note:**

An attribute specification can also include information that is not related to text. Instructions for constructing an attribute specification are in "Embedding Transformations in a Model".

You can provide transformation instructions for any text attribute by qualifying the `TEXT` keyword in the attribute specification with the subsettings described in the following table.

Table 7-5 Attribute-Specific Text Transformation Instructions

| Subsetting Name | Description                                                                                                                                                                                                                                             | Example                                                     |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------|
| `BIGRAM`        | A sequence of two adjacent elements from a string of tokens, which are typically letters, syllables, or words. <br>Here, `NORMAL` tokens are mixed with their bigrams.                                                                                  | (`TOKEN_TYPE:``BIGRAM`)                                     |
| `POLICY_NAME`   | Name of an Oracle Text policy object created with `CTX_DDL.CREATE_POLICY`                                                                                                                                                                               | (`POLICY_NAME:``my_policy``)`                               |
| `STEM_BIGRAM`   | Here, `STEM` tokens are extracted first and then stem bigrams are formed.                                                                                                                                                                               | (`TOKEN_TYPE:``STEM_BIGRAM`)                                |
| `SYNONYM`       | Oracle Data Mining supports synonyms. The following is an optional parameter:<br>\<`thesaurus`\> where \<`thesaurus`\> is the name of the thesaurus defining synonyms. If `SYNONYM` is used without this parameter, then the default thesaurus is used. | (`TOKEN_TYPE:``SYNONYM`)<br>(`TOKEN_TYPE:``SYNONYM[NAMES]`) |
| `TOKEN_TYPE`    | The following values are supported:<br>• `NORMAL` (the default)<br>• `STEM`<br>• `THEME`<br>See "Token Types in an Attribute Specification"                                                                                                             | `(TOKEN_TYPE:THEME)`                                        |
| `MAX_FEATURES`  | Maximum number of features to use from the attribute.                                                                                                                                                                                                   | `(MAX_FEATURES:3000)`                                       |

**Note:**

The `TEXT` keyword is only required for `CLOB` and longer `VARCHAR2` (\>4000) when you specify transformation instructions. The `TEXT` keyword is always required for `CHAR`, shorter `VARCHAR2`, `BFILE`, and `BLOB` — whether or not you specify transformation instructions.

**Tip:**

You can view attribute specifications in the data dictionary view `ALL_MINING_MODEL_ATTRIBUTES`, as shown in Oracle Database Reference.

### Token Types in an Attribute Specification

When stems or themes are specified as the token type, the lexer preference for the text policy must support these types of tokens.

The following example adds themes and English stems to `BASIC_LEXER`.

    BEGIN
      CTX_DDL.CREATE_PREFERENCE('my_lexer', 'BASIC_LEXER');
      CTX_DDL.SET_ATTRIBUTE('my_lexer', 'index_stems', 'ENGLISH');
      CTX_DDL.SET_ATTRIBUTE('my_lexer', 'index_themes', 'YES');
    END;

Example 7-1 A Sample Attribute Specification for Text

This expression specifies that text transformation for the attribute must use the text policy named `my_policy`. The token type is `THEME`, and the maximum number of features is 3000.

    "TEXT(POLICY_NAME:my_policy)(TOKEN_TYPE:THEME)(MAX_FEATURES:3000)"

**Related Topics**

- [Embedding Transformations in a Model](embedding-transformations-model.md)
- [Specifying Transformation Instructions for an Attribute](embedding-transformations-model.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)
- [`ALL_MINING_MODEL_ATTRIBUTES`](../refrn/ALL_MINING_MODEL_ATTRIBUTES.md)
