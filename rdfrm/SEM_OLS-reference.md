## 16  SEM_OLS Package Subprograms

The SEM_OLS package contains subprograms (functions and procedures) related to triple-level security to RDF data, using Oracle Label Security (OLS).

To use the subprograms in this chapter, you should understand the conceptual and usage information in [RDF Semantic Graph Overview](rdf-semantic-graph-overview.md) and [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

This chapter provides reference information about the subprograms, listed in alphabetical order.

- SEM_OLS.APPLY_POLICY_TO_APP_TAB
- SEM_OLS.REMOVE_POLICY_FROM_APP_TAB

**Parent topic:** [Reference Information](part-ref-supp.md)

### 16.1 SEM_OLS.APPLY_POLICY_TO_APP_TAB

#### Format

    SEM_OLS.APPLY_POLICY_TO_APP_TAB(
         policy_name   IN VARCHAR2,
         schema_name   IN VARCHAR2,
         table_name    IN VARCHAR2,
         predicate     IN VARCHAR2 DEFAULT NULL);

#### Description

Applies an OLS policy to an application table in the MDSYS-owned network.

#### Parameters

policy_name
Name of an existing OLS policy.

schema_name
Name of the schema containing the application table.

table_name
Name of the application table.

predicate
An additional predicate to combine with the label-based predicate.

#### Usage Notes

When you use triple-level security, OLS is applied to each semantic model in the network. That is, label security is applied to the relevant internal tables and to all the application tables; there is no need to manually apply policies to the application tables of existing semantic models. However, if you need to create additional models after applying the OLS policy, you must use the SEM_OLS.APPLY_POLICY_TO_APP_TAB procedure to apply OLS to the application table before creating the model.

You must have the following to execute this procedure: `EXECUTE` privilege for the SA_POLICY_ADMIN package, and the `policy_DBA` role.

Before executing this procedure, you must have executed the [SEM_RDFSA.APPLY_OLS_POLICY](SEM_RDFSA-reference.md) procedure specifying `SEM_RDFSA.TRIPLE_LEVEL_ONLY` for the `rdfsa_options` parameter.

To remove the OLS policy from the application table, use the SEM_OLS.REMOVE_POLICY_FROM_APP_TAB procedure.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

This procedure applies only to the MDSYS-owned network, not to schema-private networks. For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example applies an OLS policy named `defense` to the MY_SCHEMA.MY_APP_TABLE application table.

    begin
      sem_ols.apply_policy_to_app_table(
            policy_name => 'defense',
            schema_name => 'my_schema',
            table_name  => 'my_app_table');
    end;
    /

**Parent topic:** SEM_OLS Package Subprograms

### 16.2 SEM_OLS.REMOVE_POLICY_FROM_APP_TAB

#### Format

    SEM_OLS.REMOVE_POLICY_FROM_APP_TAB(
         policy_name   IN VARCHAR2,
         schema_name   IN VARCHAR2,
         table_name    IN VARCHAR2,
         check_model   IN BOOLEAN DEFAULT TRUE);

#### Description

Permanently removes or detaches the OLS policy from an application table associated with a model in the MDSYS-owned network.

#### Parameters

policy_name
Name of the existing OLS policy.

schema_name
Name of the schema containing the application table.

table_name
Name of the application table.

check_model
`TRUE` (the default) checks if the model associated with the application table exists (and generates an exception if the model exists); `FALSE` does not check if the model exists before performing the operation.

#### Usage Notes

If you have dropped a semantic model and you no longer need to protect the application table, you can use this procedure.

You must have the following to execute this procedure: `EXECUTE` privilege for the SA_POLICY_ADMIN package, and the `policy_DBA` role.

Before executing this procedure, you must have executed the [SEM_RDFSA.APPLY_OLS_POLICY](SEM_RDFSA-reference.md) procedure specifying `SEM_RDFSA.TRIPLE_LEVEL_ONLY` for the `rdfsa_options` parameter.

If `check_model` is `TRUE` (the default), an exception is generated if the associated model exists. In this case, if you want to execute this procedure, you must first drop the model.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

This procedure applies only to the MDSYS-owned network, not to schema-private networks. For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example removes the OLS policy named `defense` from the MY_SCHEMA.MY_APP_TABLE application table.

    begin
      sem_ols.remove_policy_from_app_table(
            policy_name => 'defense',
            schema_name => 'my_schema',
            table_name  => 'my_app_table');
    end;
    /

**Parent topic:** SEM_OLS Package Subprograms
