## 19  SEM_RDFSA Package Subprograms

The SEM_RDFSA package contains subprograms (functions and procedures) for providing fine-grained access control to RDF data using Oracle Label Security (OLS).

To use the subprograms in this chapter, you should understand the conceptual and usage information in [RDF Semantic Graph Overview](rdf-semantic-graph-overview.md) and [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

This chapter provides reference information about the subprograms, listed in alphabetical order.

- SEM_RDFSA.APPLY_OLS_POLICY
- SEM_RDFSA.DISABLE_OLS_POLICY
- SEM_RDFSA.ENABLE_OLS_POLICY
- SEM_RDFSA.REMOVE_OLS_POLICY
- SEM_RDFSA.RESET_MODEL_LABELS
- SEM_RDFSA.SET_PREDICATE_LABEL
- SEM_RDFSA.SET_RDFS_LABEL
- SEM_RDFSA.SET_RESOURCE_LABEL
- SEM_RDFSA.SET_RULE_LABEL

**Parent topic:** [Reference Information](part-ref-supp.md)

### 19.1 SEM_RDFSA.APPLY_OLS_POLICY

#### Format

    SEM_RDFSA.APPLY_OLS_POLICY(
         policy_name    IN VARCHAR2,
         rdfsa_options  IN NUMBER  DEFAULT SEM_RDFSA.SECURE_SUBJECT,
         table_options  IN VARCHAR2 DEFAULT 'ALL_CONTROL',
         label_function IN VARCHAR2 DEFAULT NULL,
         predicate      IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Applies an OLS policy to the semantic data store.

#### Parameters

policy_name
Name of an existing OLS policy.

rdfsa_options
Options specifying the mode of fine-grained access control to be enabled for RDF data. The default option for securing RDF data involves assigning sensitivity labels for the resources appearing the triples' subject position. You can override the defaults by using the `rdfsa_options` parameter and specifying one of the constants defined in Table 19-1 in the Usage Notes.

table_options
Policy enforcement options. The default value (`ALL_CONTROL`) is the only supported value for this procedure.

label_function
A string invoking a function to return a label value to use as the default.

predicate
An additional predicate to combine with the label-based predicate.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The OLS policy specified with this procedure must be created with CTXT1 as the column name, and it should use default policy options. For information about policy options, see [Oracle Label Security Administrator's Guide](../olsag/implementing-policy-enforcement-options-and-labeling-functions.md).

This procedure invokes the `sa_policy_admin.apply_table_policy` procedure on multiple tables defined in the MDSYS schema. The parameters `table_options`, `label_function`, and `predicate` for the SEM_RDFSA.APPLY_OLS_POLICY procedure have same semantics as the parameters with same names in the sa_policy_admin.apply_table_policy procedure.

For the `rdfsa_options` parameter, you can specify the package constant for the desired option. Table 19-1 lists these constants and their descriptions.

Table 19-1 SEM_RDFSA Package Constants for rdfsa_options Parameter

| Constant                         | Description                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SEM_RDFSA.SECURE_SUBJECT         | Assigns sensitivity labels for the resources appearing the triples' subject position.                                                                                                                                                                                                                                                                                                                      |
| SEM_RDFSA.SECURE_PREDICATE       | Assigns sensitivity labels for the resources appearing the triples' predicate position.                                                                                                                                                                                                                                                                                                                    |
| SEM_RDFSA.SECURE_OBJECT          | Assigns sensitivity labels for the resources appearing the triples' object position.                                                                                                                                                                                                                                                                                                                       |
| SEM_RDFSA.TRIPLE_LEVEL_ONLY      | Applies triple-level security. Provides good performance, and eliminates the need to assign labels to individual resources. (Requires that Patch 9819833, available from My Oracle Support, be installed.)                                                                                                                                                                                                 |
| SEM_RDFSA.OPT_DEFINE_BEFORE_USE  | Restricts the use of an RDF resource in a triple before the sensitivity label is defined for the resource. If this option is not specified, the user's initial row label is used as the default label for the resource upon first use.                                                                                                                                                                     |
| SEM_RDFSA.OPT_RELAX_TRIPLE_LABEL | Relaxes the dominating relationship that exists between the triple label and the labels associated with all its components. With this option, a triple can be defined if the user has READ access to all the triple components and the triple label may not bear any relationship with the component labels. Without this option, the triple label should at least cover the label for all its components. |

You can specify a function in the `label_function` parameter to generate custom labels for newly inserted triples. The label function is associated with the MDSYS.RDF_LINK\$ table, and the columns in this table may be configured as parameters to the label function as shown in the following example:

    fgac_admin.new_triple_label(:new.model_id,
                                :new.start_node_id,
                                :new.p_value_id,
                                :new.canon_end_node_id)'

Because the OLS policy is applied to more than one table with different structures, the only valid column reference in any predicates assigned to the `predicate` parameter is that of the label column: CTXT1. If OLS is enabled for a semantic data store with existing data, you can specify a predicate of the form `'OR CTXT1 is null'` to be able to continue using this data with no access restrictions.

An OLS-enabled semantic data store uses sensitivity labels for all the RDF triples organized in multiple models. User access to such triples, through model views and SEM_MATCH queries, is restricted by the OLS policy. Additionally, independent of a user owning the application table, access to the triple column (of type SDO_RDF_TRIPLE_S) in the table is restricted to users with FULL access privileges with the OLS policy.

The triples are inserted into a specific RDF model using the INSERT privileges on the corresponding application table. A sensitivity label for the new triple is generated using the user's session context (initial row label) or the label function. The triple is validated for any RDF policy violations using labels associated with the triple components. Although the triple information may not be accessed trough the application table, the model view may be queried to access the triples, while enforcing the OLS policy restrictions. If you have the necessary policy privileges (such as writeup, writeacross), you can update the CTXT1 column in the model view to reset the label assigned to the triple. The new label is automatically validated for any RDF policy violations involving the triple components. Update privilege on the CTXT1 column of the model view is granted to the owner of the model, and this user may selectively grant this privilege to other users.

If the RDF models are created in schemas other than the user with FULL access, necessary privileges on the model objects -- specifically, read/write access on the application table, read access to the model view, and write access to the CTXT1 column in the model view -- can be granted to such users for maintenance operations. These operations include bulk loading into the model, resetting any sensitivity labels assigned to the triples, and creating entailments using the model.

To disable the OLS policy, use the SEM_RDFSA.DISABLE_OLS_POLICY procedure.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enable secure access to RDF data with secure subject and secure predicate options.

    begin
      sem_rdfsa.apply_ols_policy(
            policy_name   => 'defense',
            rdfsa_options => sem_rdfsa.SECURE_SUBJECT+
                             sem_rdfsa.SECURE_PREDICATE);
    end;
    /

The following example extends the preceding example by specifying a Define Before Use option, which allows a user to define a triple only if the triple components secured (Subject, Predicate or Object) are predefined with an associated sensitivity label. This configuration is effective if the user inserting the triple does not have execute privileges on the SEM_RDFSA package.

    begin
      sem_rdfsa.apply_ols_policy(
            policy_name   => 'defense',
            rdfsa_options => sem_rdfsa.SECURE_SUBJECT+
                             sem_rdfsa.SECURE_PREDICATE+
                             sem_rdfsa.OPT_DEFINE_BEFORE_USE);
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.2 SEM_RDFSA.DISABLE_OLS_POLICY

#### Format

    SEM_RDFSA.DISABLE_OLS_POLICY(
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Disables the OLS policy that has been previously applied to or enabled on the semantic data store.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You can use this procedure to disable temporarily the OLS policy that had been applied to or enabled for the semantic data store. The user disabling the policy should have the necessary privileges to administer OLS policies and should also have access to the OLS policy applied to RDF data.

The sensitivity labels assigned to various RDF resources and triples are preserved and the OLS policy may be re-enabled to enforce them. New resources with specific labels can be added, or labels for existing triples and resources can be updated when the OLS policy is disabled.

To apply an OLS policy, use the SEM_RDFSA.APPLY_OLS_POLICY procedure; to enable an OLS policy that had been disabled, use the SEM_RDFSA.ENABLE_OLS_POLICY procedure.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example disables the OLS policy for the semantic data store.

    begin
      sem_rdfsa.disable_ols_policy;
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.3 SEM_RDFSA.ENABLE_OLS_POLICY

#### Format

    SEM_RDFSA.ENABLE_OLS_POLICY(
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Enables the OLS policy that has been previously disabled.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You can use this procedure to enable the OLS policy that had been disabled for the semantic data store. The user enabling the policy should have the necessary privileges to administer OLS policies and should also have access to the OLS policy applied to RDF data.

To disable an OLS policy, use the SEM_RDFSA.DISABLE_OLS_POLICY procedure.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

#### Examples

The following example enables the OLS policy for the semantic data store.

    begin
      sem_rdfsa.enable_ols_policy;
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.4 SEM_RDFSA.REMOVE_OLS_POLICY

#### Format

    SEM_RDFSA.REMOVE_OLS_POLICY(
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Permanently removes or detaches the OLS policy from the semantic data store.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You should have the necessary privileges to administer OLS policies, and you should also have access to the OLS policy applied to RDF data. Once the OLS policy is detached from the semantic data store, all the sensitivity labels previously assigned to the triples and resources are lost.

This operation drops objects that are specifically created to maintain the RDF security policies.

To apply an OLS policy, use the SEM_RDFSA.APPLY_OLS_POLICY procedure.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example removes the OLS policy that had been previously applied to the semantic data store.

    begin
      sem_rdfsa.remove_ols_policy;
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.5 SEM_RDFSA.RESET_MODEL_LABELS

#### Format

    SEM_RDFSA.RESET_MODEL_LABELS(
         model_name    IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Resets the labels associated with a model or with global resources; requires that the associated model or models be empty.

#### Parameters

model_name
Name of the model for which the labels should be reset, or the string `RDF$GLOBAL` to reset the labels associated with all global resources.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)



#### Usage Notes

If you specify a model name, the model must be empty. If you specify `RDF$GLOBAL`, all the models must be empty (that is, no triples in the RDF repository).

You must have FULL access privilege with the OLS policy applied to the semantic data store.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example removes all resources and their labels associated with the `Contracts` model.

    begin
       sem_rdfsa.reset_model_labels(model_name => 'Contracts');
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.6 SEM_RDFSA.SET_PREDICATE_LABEL

#### Format

    SEM_RDFSA.SET_PREDICATE_LABEL(
         model_name    IN VARCHAR2,
         predicate     IN VARCHAR2,
         label_string  IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Sets a sensitivity label for a predicate at the model level or for the whole repository.

#### Parameters

model_name
Name of the model to which the predicate belongs, or the string `RDF$GLOBAL` if the same label should applied for the use of the predicate in all models.

predicate
Predicate for which the label should be assigned.

label_string
OLS row label in string representation.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

If you specify a model name, you must have read access to the model and execute privileges on the SEM_RDFSA package to perform this operation. If you specify `RDF$GLOBAL`, you must have FULL access privilege with the OLS policy applied to RDF data.

You must have access to the specified label and OLS policy privilege to overwrite an existing label if a label already exists for the predicate. The SECURE_PREDICATE option must be enabled for RDF data.

If an existing predicate label is updated with this operation, the labels for the triples using this predicate must all dominate the new predicate label. The only exception is when the OPT_RELAX_TRIPLE_LABEL option is chosen for the OLS-enabled RDF data.

If you specify `RDF$GLOBAL`, a global predicate with a unique sensitivity label across models is created. If the same predicate is previously defined in one or more models, the global label dominates all such labels and the model-specific labels are replaced for the given predicate.

After a label for a predicate is set, new triples with the predicate can be added only if the triple label (which may be initialized from user's initial row label or using a label function) dominates the predicate's sensitivity label. This dominance relationship can be relaxed with the OPT_RELAX_TRIPLE_LABEL option, in which case the user should at least have read access to the predicate to be able to define a new triple using the predicate.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets a predicate label for `Contracts` model and another predicate label for all models in the database instance.

    begin
      sem_rdfsa.set_predicate_label(
             model_name   => 'contracts',
             predicate    => '<http://www.myorg.com/pred/hasContractValue>',
             label_string => 'TS:US_SPCL');
    end;
    /

    begin
      sem_rdfsa.set_predicate_label(
             model_name   => 'rdf$global',
             predicate    => '<http://www.myorg.com/pred/hasStatus>',
             label_string => 'SE:US_SPCL:US');
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.7 SEM_RDFSA.SET_RDFS_LABEL

#### Format

    SEM_RDFSA.SET_RDFS_LABEL(
         label_string  IN VARCHAR2,
         inf_override  IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Sets a sensitivity label for RDFS schema elements.

#### Parameters

label_string
OLS row label in string representation, to be used as the sensitivity label for all RDF schema constructs.

inf_override
OLS row label to be used as the override for generating labels for inferred triples.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure sets or resets the sensitivity label associated with the RDF schema resources, often recognized by `http://www.w3.org/1999/02/22-rdf-syntax-ns#` and `http://www.w3.org/2000/01/rdf-schema#` prefixes for their URIs. You can assign a sensitivity label with restricted access to these resources, so that operations such as creating new RDF classes and adding new properties can be restricted to users with higher privileges.

You must have FULL access privilege with policy applied to RDF data.

RDF schema elements implicitly use the relaxed triple label option, so that the triples using RDFS and OWL constructs for subject, predicate, or object are not forced to have a sensitivity label that dominates the labels associated with the schema constructs. Therefore, a user capable of defining new RDF classes and properties must least have read access to the schema elements.

When RDF schema elements are referred to in the inferred triples, the system-defined and custom label generators consider the inference override label in determining the appropriate label for the inferred triples. If a custom label generator is used, this override label is passed instead of the actual label when an RDF schema element is involved.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets a label with a unique compartment for all RDF schema elements. A user capable of defining new RDF classes and properties is expected to have an exclusive membership to the compartment.

    begin
      sem_rdfsa.set_rdfs_label(
             label_string  => 'SE:RDFS:',
             inf_override  => 'SE:US_SPCL:US');
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.8 SEM_RDFSA.SET_RESOURCE_LABEL

#### Format

    SEM_RDFSA.SET_RESOURCE_LABEL(
         model_name   IN VARCHAR2,
         resource_uri IN VARCHAR2,
         label_string IN VARCHAR2,
         resource_pos IN VARCHAR2 DEFAULT 'S',
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Sets a sensitivity label for a resource that may be used in the subject and/or object position of a triple.

#### Parameters

model_name
Name of the model to which the resource belongs, or the string `RDF$GLOBAL` if the same label should applied for using the resource in all models.

resource_uri
URI for the resource that may be used as subject or object in one or more triples.

label_string
OLS row label in string representation.

resource_pos
Position of the resource within a triple: `S`, `O`, or `S,O`. You can specify up to two separate labels for the same resource, one to be considered when the resource is used in the subject position of a triple and the other to be considered when it appears in the object position. The values '`S`', '`O`' or '`S,O`' set a label for the resource in subject, object or both subject and object positions, respectively.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

If you specify a model name, you must have read access to the model and execute privileges on the SEM_RDFSA package to perform this operation. If you specify `RDF$GLOBAL`, you must have FULL access privilege with the OLS policy applied to RDF data.

You must have access to the specified label and OLS policy privilege to overwrite an existing label if a label already exists for the predicate. The SECURE_PREDICATE option must be enabled for RDF data.

If an existing resource label is updated with this operation, the labels for the triples using this resource in the specified position must all dominate the new resource label. The only exception is when the OPT_RELAX_TRIPLE_LABEL option is chosen for the OLS-enabled RDF data.

If you specify `RDF$GLOBAL`, a global resource with a unique sensitivity label across models is created. If the same resource is previously defined in one or more models with the same triple position, the global label dominates all such labels and the model-specific labels are replaced for the given resource in that position.

After a label for a predicate is set, new triples using the resource in the specified position can be added only if the triple label dominates the resource's sensitivity label. This dominance relationship can be relaxed with OPT_RELAX_TRIPLE_LABEL option, in which case, the user should at least have read access to the resource.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets sensitivity labels for multiple resources based on their position.

    begin
      sem_rdfsa.set_resource_label(
             model_name   => 'contracts',
             resource_uri => '<http://www.myorg.com/contract/projectHLS>',
             label_string => 'SE:US_SPCL:US',
             resource_pos => 'S,O');
    end;
    /

    begin
      sem_rdfsa.set_resource_label(
           model_name   => 'rdf$global',
           resource_uri => '<http://www.myorg.com/contract/status/Complete>',
           label_string => 'SE:US_SPCL:US',
           resource_pos => 'O');
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms

### 19.9 SEM_RDFSA.SET_RULE_LABEL

#### Format

    SEM_RDFSA.SET_RULE_LABEL(
         rule_base     IN VARCHAR2,
         rule_name     IN VARCHAR2,
         label_string  IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Sets sensitivity label for a rule belonging to a rulebase.

#### Parameters

rule_base
Name of an existing RDF rulebase.

rule_name
Name of the rule belonging to the rulebase.

label_string
OLS row label in string representation.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The sensitivity label assigned to the rule is used to generate the label for the inferred triples when an appropriate label generator option is chosen.

You must have access have access to the rulebase, and you must have FULL access privilege with the OLS policy can assign labels for system-defined rules in the RDFS rulebase.

There is no support for labels assigned to user-defined rules.

For information about support for OLS, see [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example assigns a sensitivity label for an RDFS rule.

    begin
    sem_rdfsa.set_rule_label (rule_base    => 'RDFS',
                              rule_name    => 'RDF-AXIOMS',
                              label_string => 'SE:US_SPCL:');
    end;
    /

**Parent topic:** SEM_RDFSA Package Subprograms
