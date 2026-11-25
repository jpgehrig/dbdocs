## 7  CTX_CLS Package

This chapter contains the following topics.

- About CTX_CLS Package Procedures

- TRAIN

- CLUSTERING

### 7.1 About CTX_CLS Package Procedures

The `CTX_CLS` PL/SQL package provides procedures for generating rules that define document categories, and enables you to perform document classification.

The following procedures are in the `CTX_CLS` PL/SQL package.

| Name           | Description                                                                                   |
|:---------------|:----------------------------------------------------------------------------------------------|
| TRAIN          | Generates rules that define document categories. Output based on input training document set. |
| CLUSTERING     | Generates clusters for a document collection.                                                 |
| SA_TRAIN_MODEL | Trains a sentiment classifier.                                                                |
| SA_DROP_MODEL  | Drops an existing sentiment classifier.                                                       |

**Note:**

The APIs in the `CTX_CLS` package do not support identifiers that are prefixed with the schema or the owner name.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md) for more information on document classification

### 7.2 TRAIN

Use this procedure to generate query rules that select document categories. You must supply a training set consisting of categorized documents. Documents can be in any format supported by Oracle Text and must belong to one or more categories. This procedure generates the queries that define the categories and then writes the results to a table.

You must also have a document table and a category table. The category table must contain at least two categories.

For example, your document and category tables can be defined as:

    create table trainingdoc(

    docid number primary key,
    text varchar2(4000));

    create table category (

    docid trainingdoc(docid),
    categoryid number);

You can use one of two syntaxes depending on the classification algorithm you need. The query compatible syntax uses the `RULE_CLASSIFIER` preference and generates rules as query strings. The Support Vector Machine syntax uses the `SVM_CLASSIFER` preference and generates rules in binary format. The `SVM_CLASSIFIER` is good for high classification accuracy, but because its rules are generated in binary format, they cannot be examined like the query strings generated with the `RULE_CLASSIFIER`. Note that only those document ids that appear in both the document table and the category table will impact `RULE_CLASSIFIER` and `SVM_CLASSIFIER` learning.

The `CTX_CLS.TRAIN` procedure requires that your document table have an associated context index. For best results, the index should be synchronized before running this procedure. `SVM_CLASSIFIER` syntax enables the use of an unpopulated context index, while query-compatible syntax requires that the context index be populated.

**Note:**

When downgrading the database, you must drop any models that were created in Oracle Database 12c Release 2 (12.2) using `TRAIN`. These models are not compatible with earlier releases. The following error occurs if the models are not dropped before the downgrade: ORA-40350: One or more models exist that cannot be downgraded.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md) for more on document classification

#### Query Compatible Syntax

The following syntax generates query-compatible rules and is used with the [RULE_CLASSIFIER](oracle-text-indexing-elements.md) preference. Use this syntax and preference when different categories are separated from others by several key words. An advantage of generating your rules as query strings is that you can easily examine the generated rules. This is different from generating SVM rules, which are in binary format.

    CTX_CLS.TRAIN(

    index_name    in varchar2,
    docid         in varchar2,
    cattab        in varchar2,
    catdocid      in varchar2,
    catid         in varchar2,
    restab        in varchar2,
    rescatid      in varchar2,
    resquery      in varchar2,
    resconfid     in varchar2,
    preference    in varchar2 DEFAULT NULL

    );

index_name
Specify the name of the context index associated with your document training set.

docid
Specify the name of the document ID column in the document table. The document IDs in this column must be unique, and this column must be of datatype `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0-4294967295.

cattab
Specify the name of the category table. You must have the `READ` or `SELECT` privilege on this table. (See [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md) for information about the `READ` privilege.)

catdocid
Specify the name of the document ID column in the category table. The document IDs in this table must also exist in the document table. This column must be a `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0-4294967295.

catid
Specify the name of the category ID column in the category table. This column must be a `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0-4294967295.

restab
Specify the name of the result table. You must have `INSERT` privilege on this table.

rescatid
Specify the name of the category ID column in the result table. This column must be a `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0-4294967295.

resquery
Specify the name of the query column in the result table. This column must be `VARACHAR2`, `CHAR,` `CLOB`, `NVARCHAR2`, or `NCHAR`.

The queries generated in this column connects terms with `AND` or `NOT` operators, such as:

    'T1 & T2 ~ T3'

Terms can also be theme tokens and be connected with the `ABOUT` operator, such as:

    'about(T1) & about(T2) ~ about(T3)'

Generated rules also support `WITHIN` queries on field sections.

resconfid
Specify the name of the confidence column in result table. This column contains the estimated probability from training data that a document is relevant if that document satisfies the query.

preference
Specify the name of the preference. For classifier types and attributes, see "[Classifier Types](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

#### Syntax for Support Vector Machine (SVM) Rules

The Support Vector Machine, or SVM, rules preference generates rules in binary format. Use this syntax when your application requires high classification accuracy.

The following syntax generates Support Vector Machine (SVM) rules with the [SVM_CLASSIFIER](oracle-text-indexing-elements.md) preference.

    CTX_CLS.TRAIN(
        index_name in varchar2,
        docid      in varchar2,
        cattab     in varchar2,
        catdocid   in varchar2,
        catid      in varchar2,
        restab     in varchar2,
        preference in varchar2 );

index_name
Specify the name of the text index.

docid
Specify the name of `docid` column in document table.

cattab
Specify the name of category table.

catdocid
Specify the name of `docid` column in category table.

catid
Specify the name of category ID column in category table.

restab
Specify the name of result table.

The result table has the following format:

| Column Name | Datatype             | Description                                  |
|:------------|:---------------------|:---------------------------------------------|
| `CAT_ID`    | `NUMBER`             | The ID of the category.                      |
| `TYPE`      | `NUMBER(3) NOT NULL` | 0 for the actual rule or catid; 1 for other. |
| `RULE`      | `BLOB`               | The returned rule.                           |

preference
Specify the name of user preference. For classifier types and attributes, see "[Classifier Types](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

**Note:**

Column names must not be prefixed by the owner, schema or table name.

#### Example

The `CTX_CLS.TRAIN` procedure is used in supervised classification. For an extended example, see [Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md).

### 7.3 CLUSTERING

Use this procedure to cluster a collection of documents. A cluster is a group of documents similar to each other in content.

A clustering result set is composed of document assignments and cluster descriptions:

- A document assignment result set shows how relevant each document is to all generated leaf clusters.

- A cluster description result set contains information about what topic a cluster is about. This result set identifies the cluster and contains cluster description text, a suggested cluster label, and a quality score for the cluster.

Cluster output is hierarchical. Only leaf clusters are scored for relevance to documents. Producing more clusters requires more computing time. Indicate the upper limit for generated clusters with the `CLUSTER_NUM` attribute of the `KMEAN_CLUSTERING` cluster type (see "[Cluster Types](oracle-text-indexing-elements.md)" in this chapter).

There are two versions of this procedure: one with a table result set, and one with an in-memory result set.

Clustering is also known as unsupervised classification.

**See Also:**

For more information about clustering and relevant preferences, see [Cluster Types](oracle-text-indexing-elements.md) in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md), as well as the [Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md)

#### Syntax: Table Result Set

    ctx_cls.clustering (
     index_name  IN VARCHAR2,
     docid       IN VARCHAR2,
     doctab_name IN VARCHAR2,
     clstab_name IN VARCHAR2,
     pref_name   IN VARCHAR2  DEFAULT NULL
    );

index_name
Specify the name of the context index on collection table.

docid
Specify the name of document ID column of the collection table.

doctab_name
Specify the name of document assignment table. This procedure creates the table with the following structure:

    doc_assign(
       docid number,
       clusterid number,
       score number
    );

| Column      | Description                                                                                                                                                                                                  |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DOCID`     | Document ID to identify document.                                                                                                                                                                            |
| `CLUSTERID` | ID of a leaf cluster associated with this document. If `CLUSTERID` is -1, then the cluster contains "miscellaneous" documents; for example, documents that cannot be assigned to any other cluster category. |
| `SCORE`     | The associated score between the document and the cluster.                                                                                                                                                   |

If you require more columns, then create the table before you call this procedure.

clstab_name
Specify the name of the cluster description table. This procedure creates the table with the following structure:

    cluster_desc(
      clusterid NUMBER,
      descript VARCHAR2(4000),
      label VARCHAR2(200),
      sze NUMBER,
      quality_score NUMBER,
      parent NUMBER
    );

| Column          | Description                                                                                                                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLUSTERID`     | Cluster ID to identify cluster. If `CLUSTERID` is -1, then the cluster contains "miscellaneous" documents; for example, documents that cannot be assigned to any other cluster category. |
| `DESCRIPT`      | String to describe the cluster.                                                                                                                                                          |
| `LABEL`         | A suggested label for the cluster.                                                                                                                                                       |
| `SZE`           | This parameter currently has no value.                                                                                                                                                   |
| `QUALITY_SCORE` | The quality score of the cluster. A higher number indicates greater coherence.                                                                                                           |
| `PARENT`        | The parent cluster ID. Zero means no parent cluster.                                                                                                                                     |

If you require more columns, then create the table before you call this procedure.

pref_name
Specify the name of the preference.

#### Syntax: In-Memory Result Set

Put the result set into in-memory structures for better performance. Two in-memory tables are defined in `CTX_CLS` package for document assignment and cluster description respectively.

    CTX_CLS.CLUSTERING(
      index_name     IN VARCHAR2,
      docid          IN VARCHAR2,
      dids           IN DOCID_TAB,
      doctab_name    IN OUT NOCOPY DOC_TAB,
      clstab_name    IN OUT NOCOPY CLUSTER_TAB,
      pref_name      IN VARCHAR2  DEFAULT NULL
              );

index_name
Specify the name of context index on the collection table.

docid
Specify the document ID column of the collection table.

dids
Specify the name of the in-memory `docid_tab`.

    TYPE docid_tab IS TABLE OF number INDEX BY BINARY_INTEGER;

doctab_name
Specify name of the document assignment in-memory table. This table is defined as follows:

    TYPE doc_rec IS RECORD (
       docid NUMBER,
       clusterid NUMBER,
       score NUMBER
    )
    TYPE doc_tab IS TABLE OF doc_rec INDEX BY BINARY_INTEGER;

| Column      | Description                                                                                                                                                                                                  |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DOCID`     | Document ID to identify document.                                                                                                                                                                            |
| `CLUSTERID` | ID of a leaf cluster associated with this document. If `CLUSTERID` is -1, then the cluster contains "miscellaneous" documents; for example, documents that cannot be assigned to any other cluster category. |
| `SCORE`     | The associated score between the document and the cluster.                                                                                                                                                   |

cls_tab
Specify the name of cluster description in-memory table.

    TYPE cluster_rec IS RECORD(
         clusterid NUMBER,
         descript VARCHAR2(4000),
         label VARCHAR2(200),
         sze NUMBER,
         quality_score NUMBER,
         parent NUMBER
    );
    TYPE cluster_tab IS TABLE OF cluster_rec INDEX BY BINARY_INTEGER;

| Column          | Description                                                                                                                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLUSTERID`     | Cluster ID to identify cluster. If `CLUSTERID` is -1, then the cluster contains "miscellaneous" documents; for example, documents that cannot be assigned to any other cluster category. |
| `DESCRIPT`      | String to describe the cluster.                                                                                                                                                          |
| `LABEL`         | A suggested label for the cluster.                                                                                                                                                       |
| `SZE`           | This parameter currently has no value.                                                                                                                                                   |
| `QUALITY_SCORE` | The quality score of the cluster. A higher number indicates greater coherence.                                                                                                           |
| `PARENT`        | The parent cluster ID. Zero means no parent cluster.                                                                                                                                     |

pref_name
Specify the name of the preference. For cluster types and attributes, see [Cluster Types](oracle-text-indexing-elements.md) in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

#### Example

**See Also:**

The [Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md) for an example of using clustering

### 7.4 SA_TRAIN_MODEL

Use this procedure to train a sentiment classifier. You must provide a training set consisting of categorized documents to train the sentiment classifier.

Documents can be in any format supported by Oracle Text and must belong to one or more categories.

Oracle Text first validates the training set table and the categories that are provided. Features extracted from the training set documents are used to train the sentiment classifier. A rule table is created and populated with rules that are generated after the sentiment classifier is trained. The sentiment classifier uses these rules to perform sentiment analysis. The `CTXRULE` index on the rule table is also built.

**Note:**

When downgrading the database, you must drop any models that were created in Oracle Database 12c Release 2 (12.2) using `SA_TRAIN_MODEL`. These models are not compatible with earlier releases. The following error occurs if the models are not dropped before the downgrade: ORA-40350: One or more models exist that cannot be downgraded.

#### Syntax

    SA_TRAIN_MODEL(
        clsfier_name IN VARCHAR2,
        index_name IN VARCHAR2,
        docid IN VARCHAR2,
        cattab IN VARCHAR2,
        catdocid IN VARCHAR2,
        catid IN VARCHAR2,
        pref_name IN VARCHAR2
    );

clsfier_name
Specify the name of the sentiment classifier that must be trained. The maximum length of the sentiment classifier name is 24 bytes.

index_name
Specify the name of text index associated with the document training set. This is a `CONTEXT` index that must be created on the training data before the sentiment classifier is trained.

docid
Specify the name of the document ID column in the document training set. The document IDs in this column must be unique, and this column must be of data type `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0 to 4294967295.

cattab
Specify the name of the category table that contains the true labels for the training set documents. This table should contain the` docid` to `catid` mappings for training the sentiment classifier.

catdocid
Specify the name of document ID column in the category table. The document IDs in this table must also exist in the document table. This column must be a `NUMBER`. The values for this column must be stored in an unsigned 32-bit integer and must be in the range 0 to 4294967295.

catid
Specify the name of the category ID column in the category table. This column must be a `NUMBER`. The values for this column can be either 0, 1, or 2. 0 stands for neutral, 1 stands for positive, and 2 stands for negative.

pref_name
Specify the name of sentiment classifier preference, of type `SENTIMENT_CLASSIFIER`, which is used to train the sentiment classifier. If no name is provided, then the default sentiment classifier, `CTXSYS.DEFAULT_SENT_CLASSIFIER`, is used.

**Related Topics**

- [Oracle Text Application Developer's Guide](../ccapp/performing-sentiment-analysis-using-oracle-text.md)

### 7.5 SA_DROP_MODEL

Use this procedure to drop an existing sentiment classifier.

#### Syntax

    SA_DROP_MODEL(
       clsfier_name IN VARCHAR2
    );

clsfier_name
Specify the name of the sentiment classifier that must be dropped.
