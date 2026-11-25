Learn how to create a model that includes text mining.

Oracle Data Mining supports unstructured text within columns of `VARCHAR2`, `CHAR`, `CLOB`, `BLOB`, and `BFILE`, as described in the following table:

Table 33-2 Column Data Types That May Contain Unstructured Text

| Data Type          | Description                                                                                                                                                                                                                                   |
|:-------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BFILE` and `BLOB` | Oracle Data Mining interprets `BLOB` and `BFILE` as text only if you identify the columns as text when you create the model. If you do not identify the columns as text, then `CREATE_MODEL` returns an error.                                |
| `CLOB`             | Oracle Data Mining interprets `CLOB` as text.                                                                                                                                                                                                 |
| `CHAR`             | Oracle Data Mining interprets `CHAR` as categorical by default. You can identify columns of `CHAR` as text when you create the model.                                                                                                         |
| `VARCHAR2`         | Oracle Data Mining interprets `VARCHAR2` with data length \> 4000 as text.<br>Oracle Data Mining interprets `VARCHAR2` with data length \<= 4000 as categorical by default. You can identify these columns as text when you create the model. |

**Note:**

Text is not supported in nested columns or as a target in supervised data mining.

The settings described in the following table control the term extraction process for text attributes in a model. Instructions for specifying model settings are in "Specifying Model Settings".

Table 33-3 Model Settings for Text

| Setting Name             | Data Type        | Setting Value                                                             | Description                                                                                                                                      |
|:-------------------------|:-----------------|:--------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `ODMS_TEXT_POLICY_NAME`  | `VARCHAR2(4000)` | Name of an Oracle Text policy object created with `CTX_DDL.CREATE_POLICY` | Affects how individual tokens are extracted from unstructured text. See "[Creating a Text Policy](creating-text-policy.md)".                     |
| `ODMS_TEXT_MAX_FEATURES` | `INTEGER`        | 1 \<= value \<= 100000                                                    | Maximum number of features to use from the document set (across all documents of each text column) passed to `CREATE_MODEL`.<br>Default is 3000. |

A model can include one or more text attributes. A model with text attributes can also include categorical and numerical attributes.

### To create a model that includes text attributes:

1.  Create an Oracle Text policy object..

2.  Specify the model configuration settings that are described in "Table 33-3".

3.  Specify which columns must be treated as text and, optionally, provide text transformation instructions for individual attributes.

4.  Pass the model settings and text transformation instructions to `DBMS_DATA_MINING.CREATE_MODEL`.

    **Note:**

    All algorithms except O-Cluster can support columns of unstructured text.

    The use of unstructured text is not recommended for association rules (Apriori).

**Related Topics**

- [Specifying Model Settings](specifying-model-settings.md)
- [Creating a Text Policy](creating-text-policy.md)
- [Configuring a Text Attribute](configuring-text-attribute.md)
- [Embedding Transformations in a Model](embedding-transformations-model.md)
