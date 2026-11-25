Mining model objects support SQL `COMMENT` and `AUDIT` statements.

### 34.5.1 Adding a Comment to a Mining Model

Comments can be used to associate descriptive information with a database object. You can associate a comment with a mining model using a SQL `COMMENT` statement.

    COMMENT ON MINING MODEL schema_name.model_name IS string;

**Note:**

To add a comment to a model in another schema, you must have the `COMMENT ANY MINING MODEL` system privilege.

To drop a comment, set it to the empty `''` string.

The following statement adds a comment to the model `DT_SH_CLAS_SAMPLE` in your own schema.

    COMMENT ON MINING MODEL dt_sh_clas_sample IS
               'Decision Tree model predicts promotion response';

You can view the comment by querying the catalog view `USER_MINING_MODELS`.

    SELECT model_name, mining_function, algorithm, comments FROM user_mining_models;

    MODEL_NAME        MINING_FUNCTION  ALGORITHM      COMMENTS
    ----------------- ---------------- -------------- -----------------------------------------------
    DT_SH_CLAS_SAMPLE CLASSIFICATION   DECISION_TREE  Decision Tree model predicts promotion response

To drop this comment from the database, issue the following statement:

    COMMENT ON MINING MODEL dt_sh_clas_sample '';

**See Also:**

- [Table 34-2](controlling-access-mining-models-data.md)

- [Oracle Database SQL Language Reference](../sqlrf/COMMENT.md) for details about SQL `COMMENT` statements

### 34.5.2 Auditing Mining Models

The Oracle Database auditing system is a powerful, highly configurable tool for tracking operations on schema objects in a production environment. The auditing system can be used to track operations on data mining models.

**Note:**

To audit mining models, you must have the `AUDIT_ADMIN` role.

Unified auditing is documented in Oracle Database Security Guide. However, the full unified auditing system is not enabled by default. Instructions for migrating to unified auditing are provided in Oracle Database Upgrade Guide.

**See Also:**

- "Auditing Oracle Data Mining Events" in [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) for details about auditing mining models

- "Monitoring Database Activity with Auditing" in [Oracle Database Security Guide](../dbseg/part_6.md) for a comprehensive discussion of unified auditing in Oracle Database

- "About the Unified Auditing Migration Process for Oracle Database" in [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for information about migrating to unified auditing

- [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md)
