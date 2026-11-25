Lists Oracle Data Mining data dictionary views.

The data dictionary views for Oracle Data Mining are listed in the following table. A database administrator (DBA) and USER versions of the views are also available.

Table 2-1 Data Dictionary Views for Oracle Data Mining

| View Name                                                                | Description                                                                            |
|:-------------------------------------------------------------------------|:---------------------------------------------------------------------------------------|
| [`ALL_MINING_MODELS`](../refrn/ALL_MINING_MODELS.md)                     | Provides information about all accessible mining models                                |
| [`ALL_MINING_MODEL_ATTRIBUTES`](../refrn/ALL_MINING_MODEL_ATTRIBUTES.md) | Provides information about the attributes of all accessible mining models              |
| [`ALL_MINING_MODEL_PARTITIONS`](../refrn/ALL_MINING_MODEL_PARTITIONS.md) | Provides information about the partitions of all accessible partitioned mining models  |
| [`ALL_MINING_MODEL_SETTINGS`](../refrn/ALL_MINING_MODEL_SETTINGS.md)     | Provides information about the configuration settings for all accessible mining models |
| [`ALL_MINING_MODEL_VIEWS`](../refrn/ALL_MINING_MODEL_VIEWS.md)           | Provides information about the model views for all accessible mining models            |
| [`ALL_MINING_MODEL_XFORMS`](../refrn/ALL_MINING_MODEL_XFORMS.md)         | Provides the user-specified transformations embedded in all accessible mining models.  |

### 2.2.1 ALL_MINING_MODELS

Describes an example of `ALL_MINING_MODELS` and shows a sample query.

The following example describes `ALL_MINING_MODELS` and shows a sample query.

Example 2-1 ALL_MINING_MODELS

     describe ALL_MINING_MODELS
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     MINING_FUNCTION                                    VARCHAR2(30)
     ALGORITHM                                          VARCHAR2(30)
     CREATION_DATE                             NOT NULL DATE
     BUILD_DURATION                                     NUMBER
     MODEL_SIZE                                         NUMBER
     PARTITIONED                                        VARCHAR2(3)
     COMMENTS                                           VARCHAR2(4000)

The following query returns the models accessible to you that use the Support Vector Machine algorithm.

    SELECT mining_function, model_name
        FROM all_mining_models
        WHERE algorithm = 'SUPPORT_VECTOR_MACHINES'
        ORDER BY mining_function, model_name;

    MINING_FUNCTION           MODEL_NAME
    ------------------------- --------------------
    CLASSIFICATION            PART2_CLAS_SAMPLE
    CLASSIFICATION            PART_CLAS_SAMPLE
    CLASSIFICATION            SVMC_SH_CLAS_SAMPLE
    CLASSIFICATION            SVMO_SH_CLAS_SAMPLE
    CLASSIFICATION            T_SVM_CLAS_SAMPLE
    REGRESSION                SVMR_SH_REGR_SAMPLE

**Related Topics**

- [Creating a Model](model-creation.md)
- [Oracle Database Reference](../refrn/ALL_MINING_MODELS.md)

### 2.2.2 ALL_MINING_MODEL_ATTRIBUTES

Describes an example of `ALL_MINING_MODEL_ATTRIBUTES` and shows a sample query.

The following example describes `ALL_MINING_MODEL_ATTRIBUTES` and shows a sample query. Attributes are the predictors or conditions that are used to create models and score data.

Example 2-2 ALL_MINING_MODEL_ATTRIBUTES

    describe ALL_MINING_MODEL_ATTRIBUTES
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     ATTRIBUTE_NAME                            NOT NULL VARCHAR2(128)
     ATTRIBUTE_TYPE                                     VARCHAR2(11)
     DATA_TYPE                                          VARCHAR2(106)
     DATA_LENGTH                                        NUMBER
     DATA_PRECISION                                     NUMBER
     DATA_SCALE                                         NUMBER
     USAGE_TYPE                                         VARCHAR2(8)
     TARGET                                             VARCHAR2(3)
     ATTRIBUTE_SPEC                                     VARCHAR2(4000)

The following query returns the attributes of an SVM classification model named `T_SVM_CLAS_SAMPLE`. The model has both categorical and numerical attributes and includes one attribute that is unstructured text.

    SELECT attribute_name, attribute_type, target
        FROM all_mining_model_attributes
        WHERE model_name = 'T_SVM_CLAS_SAMPLE'
        ORDER BY attribute_name;

    ATTRIBUTE_NAME            ATTRIBUTE_TYPE       TAR
    ------------------------- -------------------- ---
    AFFINITY_CARD             CATEGORICAL          YES
    AGE                       NUMERICAL            NO
    BOOKKEEPING_APPLICATION   NUMERICAL            NO
    BULK_PACK_DISKETTES       NUMERICAL            NO
    COMMENTS                  TEXT                 NO
    COUNTRY_NAME              CATEGORICAL          NO
    CUST_GENDER               CATEGORICAL          NO
    CUST_INCOME_LEVEL         CATEGORICAL          NO
    CUST_MARITAL_STATUS       CATEGORICAL          NO
    EDUCATION                 CATEGORICAL          NO
    FLAT_PANEL_MONITOR        NUMERICAL            NO
    HOME_THEATER_PACKAGE      NUMERICAL            NO
    HOUSEHOLD_SIZE            CATEGORICAL          NO
    OCCUPATION                CATEGORICAL          NO
    OS_DOC_SET_KANJI          NUMERICAL            NO
    PRINTER_SUPPLIES          NUMERICAL            NO
    YRS_RESIDENCE             NUMERICAL            NO
    Y_BOX_GAMES               NUMERICAL            NO

**Related Topics**

- [About the Data Mining API](data-mining-API.md)
- [Oracle Database Reference](../refrn/ALL_MINING_MODEL_ATTRIBUTES.md)

### 2.2.3 ALL_MINING_MODEL_PARTITIONS

Describes an example of `ALL_MINING_MODEL_PARTITIONS` and shows a sample query.

The following example describes `ALL_MINING_MODEL_PARTITIONS` and shows a sample query.

Example 2-3 ALL_MINING_MODEL_PARTITIONS

    describe ALL_MINING_MODEL_PARTITIONS
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     PARTITION_NAME                                     VARCHAR2(128)
     POSITION                                           NUMBER
     COLUMN_NAME                               NOT NULL VARCHAR2(128)
     COLUMN_VALUE                                       VARCHAR2(4000)

The following query returns the partition names and partition key values for two partitioned models. Model `PART2_CLAS_SAMPLE` has a two column partition key with system-generated partition names.

    SELECT model_name, partition_name, position, column_name, column_value
        FROM all_mining_model_partitions
        ORDER BY model_name, partition_name, position;

    MODEL_NAME           PARTITION_ POSITION COLUMN_NAME          COLUMN_VALUE
    -------------------- ---------- -------- -------------------- ---------------
    PART2_CLAS_SAMPLE    DM$$_P0           1 CUST_GENDER          F
    PART2_CLAS_SAMPLE    DM$$_P0           2 CUST_INCOME_LEVEL    HIGH
    PART2_CLAS_SAMPLE    DM$$_P1           1 CUST_GENDER          F
    PART2_CLAS_SAMPLE    DM$$_P1           2 CUST_INCOME_LEVEL    LOW
    PART2_CLAS_SAMPLE    DM$$_P2           1 CUST_GENDER          F
    PART2_CLAS_SAMPLE    DM$$_P2           2 CUST_INCOME_LEVEL    MEDIUM
    PART2_CLAS_SAMPLE    DM$$_P3           1 CUST_GENDER          M
    PART2_CLAS_SAMPLE    DM$$_P3           2 CUST_INCOME_LEVEL    HIGH
    PART2_CLAS_SAMPLE    DM$$_P4           1 CUST_GENDER          M
    PART2_CLAS_SAMPLE    DM$$_P4           2 CUST_INCOME_LEVEL    LOW
    PART2_CLAS_SAMPLE    DM$$_P5           1 CUST_GENDER          M
    PART2_CLAS_SAMPLE    DM$$_P5           2 CUST_INCOME_LEVEL    MEDIUM
    PART_CLAS_SAMPLE     F                 1 CUST_GENDER          F
    PART_CLAS_SAMPLE     M                 1 CUST_GENDER          M
    PART_CLAS_SAMPLE     U                 1 CUST_GENDER          U

**Related Topics**

- [Oracle Database Reference](../refrn/ALL_MINING_MODEL_PARTITIONS.md)

### 2.2.4 ALL_MINING_MODEL_SETTINGS

Describes an example of `ALL_MINING_MODEL_SETTINGS` and shows a sample query.

The following example describes `ALL_MINING_MODEL_SETTINGS` and shows a sample query. Settings influence model behavior. Settings may be specific to an algorithm or to a mining function, or they may be general.

Example 2-4 ALL_MINING_MODEL_SETTINGS

     describe ALL_MINING_MODEL_SETTINGS
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     SETTING_NAME                              NOT NULL VARCHAR2(30)
     SETTING_VALUE                                      VARCHAR2(4000)
     SETTING_TYPE                                       VARCHAR2(7)

The following query returns the settings for a model named `SVD_SH_SAMPLE`. The model uses the Singular Value Decomposition algorithm for feature extraction.

    SELECT setting_name, setting_value, setting_type
        FROM all_mining_model_settings
        WHERE model_name = 'SVD_SH_SAMPLE'
        ORDER BY setting_name;

    SETTING_NAME                   SETTING_VALUE                  SETTING
    ------------------------------ ------------------------------ -------
    ALGO_NAME                      ALGO_SINGULAR_VALUE_DECOMP     INPUT
    ODMS_MISSING_VALUE_TREATMENT   ODMS_MISSING_VALUE_AUTO        DEFAULT
    ODMS_SAMPLING                  ODMS_SAMPLING_DISABLE          DEFAULT
    PREP_AUTO                      OFF                            INPUT
    SVDS_SCORING_MODE              SVDS_SCORING_SVD               DEFAULT
    SVDS_U_MATRIX_OUTPUT           SVDS_U_MATRIX_ENABLE           INPUT

**Related Topics**

- [Specifying Model Settings](specifying-model-settings.md)
- [Oracle Database Reference](../refrn/ALL_MINING_MODEL_SETTINGS.md)

### 2.2.5 ALL_MINING_MODEL_VIEWS

Describes an example of `ALL_MINING_MODEL_VIEWS` and shows a sample query.

The following example describes `ALL_MINING_MODEL_VIEWS` and shows a sample query. Model views provide details on the models.

Example 2-5 ALL_MINING_MODEL_VIEWS

    describe ALL_MINING_MODEL_VIEWS
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     VIEW_NAME                                 NOT NULL VARCHAR2(128)
     VIEW_TYPE                                          VARCHAR2(128)

The following query returns the model views for a model `SVD_SH_SAMPLE`. The model uses the Singular Value Decomposition algorithm for feature extraction.

    SELECT view_name, view_type
        FROM all_mining_model_views
        WHERE model_name = 'SVD_SH_SAMPLE'
        ORDER BY view_name;

    VIEW_NAME                 VIEW_TYPE
    ------------------------- --------------------------------------------------
    DM$VESVD_SH_SAMPLE        Singular Value Decomposition S Matrix
    DM$VGSVD_SH_SAMPLE        Global Name-Value Pairs
    DM$VNSVD_SH_SAMPLE        Normalization and Missing Value Handling
    DM$VSSVD_SH_SAMPLE        Computed Settings
    DM$VUSVD_SH_SAMPLE        Singular Value Decomposition U Matrix
    DM$VVSVD_SH_SAMPLE        Singular Value Decomposition V Matrix
    DM$VWSVD_SH_SAMPLE        Model Build Alerts

**Related Topics**

- [Oracle Database Reference](../refrn/DBA_MINING_MODEL_VIEWS.md)

### 2.2.6 ALL_MINING_MODEL_XFORMS

Describes an example of `ALL_MINING_MODEL_XFORMS` and provides a sample query.

The following example describes `ALL_MINING_MODEL_XFORMS` and provides a sample query.

Example 2-6 ALL_MINING_MODEL_XFORMS

    describe ALL_MINING_MODEL_XFORMS
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(128)
     MODEL_NAME                                NOT NULL VARCHAR2(128)
     ATTRIBUTE_NAME                                     VARCHAR2(128)
     ATTRIBUTE_SUBNAME                                  VARCHAR2(4000)
     ATTRIBUTE_SPEC                                     VARCHAR2(4000)
     EXPRESSION                                         CLOB
     REVERSE                                            VARCHAR2(3)

The following query returns the embedded transformations for a model `PART2_CLAS_SAMPLE`.

    SELECT attribute_name, expression
        FROM all_mining_model_xforms
        WHERE model_name = 'PART2_CLAS_SAMPLE'
        ORDER BY attribute_name;

    ATTRIBUTE_NAME
    -------------------------
    EXPRESSION
    --------------------------------------------------------------------------------
    CUST_INCOME_LEVEL
    CASE CUST_INCOME_LEVEL WHEN 'A: Below 30,000' THEN 'LOW'
        WHEN 'L: 300,000 and above' THEN 'HIGH'
        ELSE 'MEDIUM' END

**Related Topics**

- [Oracle Database Reference](../refrn/ALL_MINING_MODEL_XFORMS.md)
