You can specify your own transformations and embed them in a model by creating a transformation list and passing it to `DBMS_DATA_MINING.CREATE_MODEL`.

    PROCEDURE create_model(
                      model_name           IN VARCHAR2,
                      mining_function      IN VARCHAR2,
                      data_table_name      IN VARCHAR2,
                      case_id_column_name  IN VARCHAR2,
                      target_column_name   IN VARCHAR2 DEFAULT NULL,
                      settings_table_name  IN VARCHAR2 DEFAULT NULL,
                      data_schema_name     IN VARCHAR2 DEFAULT NULL,
                      settings_schema_name IN VARCHAR2 DEFAULT NULL,
                      xform_list           IN TRANSFORM_LIST DEFAULT NULL);

### 30.4.1 Specifying Transformation Instructions for an Attribute

Learn what is a transformation instruction for an attribute and learn about the fields in a transformation record.

A transformation list is defined as a table of transformation records. Each record (`transform_rec`) specifies the transformation instructions for an attribute.

    TYPE transform_rec IS RECORD (
        attribute_name      VARCHAR2(30),
        attribute_subname   VARCHAR2(4000),
        expression          EXPRESSION_REC,
        reverse_expression  EXPRESSION_REC,
        attribute_spec      VARCHAR2(4000));

The fields in a transformation record are described in this table.

Table 30-2 Fields in a Transformation Record for an Attribute

| Field                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `attribute_name` and `attribute_subname` | These fields identify the attribute, as described in "Scoping of Model Attribute Name"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `expression`                             | A SQL expression for transforming the attribute. For example, this expression transforms the age attribute into two categories: child and adult:\[0,19) for 'child' and \[19,) for adult<br>`CASE WHEN age < 19 THEN 'child' ELSE 'adult'`<br>Expression and reverse expressions are stored in `expression_rec` objects. See "Expression Records" for details.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `reverse_expression`                     | A SQL expression for reversing the transformation. For example, this expression reverses the transformation of the age attribute:<br>`DECODE(age,'child','(-Inf,19)','[19,Inf)')`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `attribute_spec`                         | Specifies special treatment for the attribute. The `attribute_spec` field can be null or it can have one or more of these values:<br>• `FORCE_IN` — For GLM, forces the inclusion of the attribute in the model build when the `ftr_selection_enable` setting is enabled. (`ftr_selection_enable` is disabled by default.) If the model is not using GLM, this value has no effect. `FORCE_IN` cannot be specified for nested attributes or text.<br>• `NOPREP` — When ADP is on, prevents automatic transformation of the attribute. If ADP is not on, this value has no effect. You can specify `NOPREP` for a nested attribute, but not for an individual subname (row) in the nested attribute.<br>• `TEXT` — Indicates that the attribute contains unstructured text. ADP has no effect on this setting. `TEXT` may optionally include subsettings `POLICY_NAME`, `TOKEN_TYPE`, and `MAX_FEATURES`.<br>See Example 30-1 and Example 30-2. |

**Related Topics**

- [Scoping of Model Attribute Name](about-attributes.md)
- Expression Records

#### 30.4.1.1 Expression Records

The transformation expressions in a transformation record are `expression_rec` objects.

    TYPE expression_rec IS RECORD (
         lstmt       DBMS_SQL.VARCHAR2A,
         lb          BINARY_INTEGER DEFAULT 1,
         ub          BINARY_INTEGER DEFAULT 0);

    TYPE varchar2a IS TABLE OF VARCHAR2(32767)
    INDEX BY BINARY_INTEGER;

The `lstmt` field stores a `VARCHAR2A`, which allows transformation expressions to be very long, as they can be broken up across multiple rows of `VARCHAR2`. Use the `DBMS_DATA_MINING_TRANSFORM.SET_EXPRESSION` procedure to create an `expression_rec`.

#### 30.4.1.2 Attribute Specifications

Learn how to define the characteristics specific to an attribute through attribute specification.

The attribute specification in a transformation record defines characteristics that are specific to this attribute. If not null, the attribute specification can include values `FORCE_IN`, `NOPREP`, or `TEXT`, as described in Table 30-2.

Example 30-1 An Attribute Specification with Multiple Keywords

If more than one attribute specification keyword is applicable, you can provide them in a comma-delimited list. The following expression is the specification for an attribute in a GLM model. Assuming that the `ftr_selection_enable` setting is enabled, this expression forces the attribute to be included in the model. If ADP is on, automatic transformation of the attribute is not performed.

    "FORCE_IN,NOPREP"

Example 30-2 A Text Attribute Specification

For text attributes, you can optionally specify subsettings `POLICY_NAME`, `TOKEN_TYPE`, and `MAX_FEATURES`. The subsettings provide configuration information that is specific to text transformation. In this example, the transformation instructions for the text content are defined in a text policy named `my_policy` with token type is `THEME`. The maximum number of extracted features is 3000.

    "TEXT(POLICY_NAME:my_policy)(TOKEN_TYPE:THEME)(MAX_FEATURES:3000)"

**Related Topics**

- [Configuring a Text Attribute](configuring-text-attribute.md)

### 30.4.2 Building a Transformation List

A transformation list is a collection of transformation records. When a new transformation record is added, it is appended to the top of the transformation list. You can use any of the following methods to build a transformation list:

- The `SET_TRANFORM` procedure in `DBMS_DATA_MINING_TRANSFORM`

- The `STACK` interface in `DBMS_DATA_MINING_TRANSFORM`

- The `GET_MODEL_TRANSFORMATIONS` and `GET_TRANSFORM_LIST` functions in `DBMS_DATA_MINING`

#### 30.4.2.1 SET_TRANSFORM

The `SET_TRANSFORM` procedure adds a single transformation record to a transformation list.

    DBMS_DATA_MINING_TRANSFORM.SET_TRANSFORM (
              xform_list               IN OUT NOCOPY TRANSFORM_LIST,
              attribute_name           VARCHAR2,
              attribute_subname        VARCHAR2,
              expression               VARCHAR2,
              reverse_expression       VARCHAR2,
              attribute_spec           VARCHAR2 DEFAULT NULL);

SQL expressions that you specify with `SET_TRANSFORM` must fit within a `VARCHAR2`. To specify a longer expression, you can use the `SET_EXPRESSION` procedure, which builds an expression by appending rows to a `VARCHAR2` array.

#### 30.4.2.2 The STACK Interface

The `STACK` interface creates transformation records from a table of transformation instructions and adds them to a transformation list.

The `STACK` interface specifies that all or some of the attributes of a given type must be transformed in the same way. For example, `STACK_BIN_CAT` appends binning instructions for categorical attributes to a transformation list. The `STACK` interface consists of three steps:

1.  A `CREATE` procedure creates a transformation definition table. For example, `CREATE_BIN_CAT` creates a table to hold categorical binning instructions. The table has columns for storing the name of the attribute, the value of the attribute, and the bin assignment for the value.

2.  An `INSERT` procedure computes the bin boundaries for one or more attributes and populates the definition table. For example, `INSERT_BIN_CAT_FREQ` performs frequency-based binning on some or all of the categorical attributes in the data source and populates a table created by `CREATE_BIN_CAT`.

3.  A `STACK` procedure creates transformation records from the information in the definition table and appends the transformation records to a transformation list. For example, STACK_BIN_CAT creates transformation records for the information stored in a categorical binning definition table and appends the transformation records to a transformation list.

#### 30.4.2.3 GET_MODEL_TRANSFORMATIONS and GET_TRANSFORM_LIST

Use the functions to create a new transformation list.

These two functions can be used to create a new transformation list from the transformations embedded in an existing model.

The `GET_MODEL_TRANSFORMATIONS` function returns a list of embedded transformations.

    DBMS_DATA_MINING.GET_MODEL_TRANSFORMATIONS (
          model_name     IN VARCHAR2)
    RETURN DM_TRANSFORMS PIPELINED;

`GET_MODEL_TRANSFORMATIONS` returns a table of `dm_transform` objects. Each `dm_transform` has these fields

    attribute_name       VARCHAR2(4000)
    attribute_subname    VARCHAR2(4000)
    expression           CLOB
    reverse_expression   CLOB

The components of a transformation list are `transform_rec`, not `dm_transform`. The fields of a `transform_rec` are described in Table 30-2. You can call `GET_MODEL_TRANSFORMATIONS` to convert a list of `dm_transform` objects to `transform_rec` objects and append each `transform_rec` to a transformation list.

    DBMS_DATA_MINING.GET_TRANSFORM_LIST (
          xform_list           OUT NOCOPY TRANSFORM_LIST,
          model_xforms         IN  DM_TRANSFORMS);

**See Also:**

"[DBMS_DATA_MINING_TRANSFORM Operational Notes](../arpls/DBMS_DATA_MINING_TRANSFORM.md)", "[SET_TRANSFORM Procedure](../arpls/DBMS_DATA_MINING_TRANSFORM.md)", "[CREATE_MODEL Procedure](../arpls/DBMS_DATA_MINING.md)", and "[GET_MODEL_TRANSFORMATIONS Function](../arpls/DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference

### 30.4.3 Transformation Lists and Automatic Data Preparation

If you enable ADP and you specify a transformation list, the transformation list is embedded with the automatic, system-generated transformations. The transformation list is executed before the automatic transformations.

If you enable ADP and do not specify a transformation list, only the automatic transformations are embedded in the model.

If ADP is disabled (the default) and you specify a transformation list, your custom transformations are embedded in the model. No automatic transformations are performed.

If ADP is disabled (the default) and you do not specify a transformation list, no transformations is embedded in the model. You have to transform the training, test, and scoring data sets yourself if necessary. You must take care to apply the same transformations to each data set.

### 30.4.4 Oracle Data Mining Transformation Routines

Learn about transformation routines.

Oracle Data Mining provides routines that implement various transformation techniques in the `DBMS_DATA_MINING_TRANSFORM` package.

**Related Topics**

- [Oracle Database SQL Language Reference](../arpls/DBMS_DATA_MINING_TRANSFORM.md)

#### 30.4.4.1 Binning Routines

Explains Binning techniques in Oracle Data Mining.

A number of factors go into deciding a binning strategy. Having fewer values typically leads to a more compact model and one that builds faster, but it can also lead to some loss in accuracy.

Model quality can improve significantly with well-chosen bin boundaries. For example, an appropriate way to bin ages is to separate them into groups of interest, such as children 0-13, teenagers 13-19, youth 19-24, working adults 24-35, and so on.

The following table lists the binning techniques provided by Oracle Data Mining:

Table 30-3 Binning Methods in DBMS_DATA_MINING_TRANSFORM

| Binning Method            | Description                                                                                                                                                                                                                                                                                                                                           |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Top-N Most Frequent Items | You can use this technique to bin categorical attributes. You specify the number of bins. The value that occurs most frequently is labeled as the first bin, the value that appears with the next frequency is labeled as the second bin, and so on. All remaining values are in an additional bin.                                                   |
| Supervised Binning        | Supervised binning is a form of intelligent binning, where bin boundaries are derived from important characteristics of the data. Supervised binning builds a single-predictor decision tree to find the interesting bin boundaries with respect to a target. It can be used for numerical or categorical attributes.                                 |
| Equi-Width Binning        | You can use equi-width binning for numerical attributes. The range of values is computed by subtracting the minimum value from the maximum value, then the range of values is divided into equal intervals. You can specify the number of bins or it can be calculated automatically. Equi-width binning must usually be used with outlier treatment. |
| Quantile Binning          | Quantile binning is a numerical binning technique. Quantiles are computed using the SQL analytic function `NTILE`. The bin boundaries are based on the minimum values for each quantile. Bins with equal left and right boundaries are collapsed, possibly resulting in fewer bins than requested.                                                    |

**Related Topics**

- Routines for Outlier Treatment

#### 30.4.4.2 Normalization Routines

Learn about Normalization routines in Oracle Data Mining.

Most normalization methods map the range of a single attribute to another range, typically 0 to 1 or -1 to +1.

Normalization is very sensitive to outliers. Without outlier treatment, most values are mapped to a tiny range, resulting in a significant loss of information.

Table 30-4 Normalization Methods in DBMS_DATA_MINING_TRANSFORM

| Transformation        | Description                                                                                                                                                                                             |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Min-Max Normalization | This technique computes the normalization of an attribute using the minimum and maximum values. The shift is the minimum value, and the scale is the difference between the maximum and minimum values. |
| Scale Normalization   | This normalization technique also uses the minimum and maximum values. For scale normalization, shift = 0, and scale = max{abs(max), abs(min)}.                                                         |
| Z-Score Normalization | This technique computes the normalization of an attribute using the mean and the standard deviation. Shift is the mean, and scale is the standard deviation.                                            |

**Related Topics**

- Routines for Outlier Treatment

#### 30.4.4.3 Outlier Treatment

A value is considered an outlier if it deviates significantly from most other values in the column. The presence of outliers can have a skewing effect on the data and can interfere with the effectiveness of transformations such as normalization or binning.

Outlier treatment methods such as trimming or clipping can be implemented to minimize the effect of outliers.

Outliers represent problematic data, for example, a bad reading due to the abnormal condition of an instrument. However, in some cases, especially in the business arena, outliers are perfectly valid. For example, in census data, the earnings for some of the richest individuals can vary significantly from the general population. Do not treat this information as an outlier, since it is an important part of the data. You need domain knowledge to determine outlier handling.

#### 30.4.4.4 Routines for Outlier Treatment

**Outliers** are extreme values, typically several standard deviations from the mean. To minimize the effect of outliers, you can Winsorize or trim the data.

**Winsorizing** involves setting the tail values of an attribute to some specified value. For example, for a 90% Winsorization, the bottom 5% of values are set equal to the minimum value in the 5th percentile, while the upper 5% of values are set equal to the maximum value in the 95th percentile.

**Trimming** sets the tail values to NULL. The algorithm treats them as missing values.

Outliers affect the different algorithms in different ways. In general, outliers cause distortion with equi-width binning and min-max normalization.

Table 30-5 Outlier Treatment Methods in DBMS_DATA_MINING_TRANSFORM

| Transformation | Description                                                                                                                                                                                     |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Trimming       | This technique trims the outliers in numeric columns by sorting the non-null values, computing the tail values based on some fraction, and replacing the tail values with nulls.                |
| Windsorizing   | This technique trims the outliers in numeric columns by sorting the non-null values, computing the tail values based on some fraction, and replacing the tail values with some specified value. |
