## 18  SEM_RDFCTX Package Subprograms

The SEM_RDFCTX package contains subprograms (functions and procedures) to manage extractor policies and semantic indexes created for documents.

To use the subprograms in this chapter, you should understand the conceptual and usage information in [Semantic Indexing for Documents](semantic-indexing-documents.md).

This chapter provides reference information about the subprograms, listed in alphabetical order.

- SEM_RDFCTX.ADD_DEPENDENT_POLICY
- SEM_RDFCTX.CREATE_POLICY
- SEM_RDFCTX.DROP_POLICY
- SEM_RDFCTX.MAINTAIN_TRIPLES
- SEM_RDFCTX.SET_DEFAULT_POLICY
- SEM_RDFCTX.SET_EXTRACTOR_PARAM

**Parent topic:** [Reference Information](part-ref-supp.md)

### 18.1 SEM_RDFCTX.ADD_DEPENDENT_POLICY

#### Format

    SEM_RDFCTX.ADD_DEPENDENT_POLICY(
         index_name     IN VARCHAR2,
         policy_name    IN VARCHAR2,
         partition_name IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Adds a dependent policy to an (already created) index or index partition.

#### Parameters

index_name
Name of the index.

policy_name
Name of the dependent policy.

partition_name
If the specified index is local, the name of the target partition. (Otherwise, must be null.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The base policy corresponding to the new dependent policy must already be a part of the index.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example adds a new dependent policy `SEM_EXTR_PLUS_GEOONT` to the index `ArticleIndex`.

    begin
      sem_rdfctx.add_dependent_policy (index_name  => 'ArticleIndex',
                                       policy_name => 'SEM_EXTR_PLUS_GEOONT');
    end;
    /

**Parent topic:** SEM_RDFCTX Package Subprograms

### 18.2 SEM_RDFCTX.CREATE_POLICY

#### Format

    SEM_RDFCTX.CREATE_POLICY(
         policy_name   IN VARCHAR2,
         extractor     IN mdsys.rdfctx_extractor,
         preferences   IN sys.XMLType DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

or

    SEM_RDFCTX.CREATE_POLICY(
         policy_name       IN VARCHAR2,
         base_policy       IN VARCHAR2,
         user_models       IN SEM_MODELS DEFAULT NULL,
         user_entailments  IN SEM_MODELS DEFAULT NULL,
         network_owner     IN VARCHAR2 DEFAULT NULL,
         network_name      IN VARCHAR2 DEFAULT NULL);

#### Description

Creates an extractor policy. (The first format is for a base policy; the second format is for a policy that is dependent on a base policy.)

#### Parameters

policy_name
Name of the extractor policy.

extractor
An instance of a subtype of the RDFCTX_EXTRACTOR type that encapsulates the extraction logic for the information extractor.

preferences
Any preferences associated with the policy.

base_policy
Base extractor policy for a dependent policy.

user_models
List of user models for a dependent policy.

user_entailments
List of user entailments for a dependent policy.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

An extractor policy created using this procedure determines the characteristics of a semantic index that is created using the policy. Each extractor policy refers to an instance of an extractor type, either directly or indirectly. An extractor policy with a direct reference to an extractor type instance can be used to compose other extractor policies that include additional RDF models for ontologies.

An instance of the extractor type assigned to the extractor parameter must be an instance of a direct or indirect subtype of type `mdsys.rdfctx_extractor`.

The RDF models specified in the `user_models` parameter must be accessible to the user that is creating the policy.

The RDF entailments specified in the `user_entailments` parameter must be accessible to the user that is creating the policy. Note that the RDF models underlying the entailments do not get automatically included in the dependent policy. To include one or more of those underlying RDF models, you need to include the models in the `user_models` parameter.

The preferences specified for extractor policy determine the type of repository used for the documents to be indexed and other relevant information. For more information, see [Indexing External Documents](semantic-indexing-documents.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates an extractor policy using the gatenlp_extractor extractor type, which is included with the Oracle Database support for semantic indexing.

    begin
      sem_rdfctx.create_policy (policy_name => 'SEM_EXTR',
                                extractor   => mdsys.gatenlp_extractor());
    end;
    /

The following example creates a dependent policy for the previously created extractor policy, and it adds the user-defined RDF model `geo_ontology` to the dependent policy.

    begin
      sem_rdfctx.create_policy (policy_name => 'SEM_EXTR_PLUS_GEOONT',
                                base_policy => 'SEM_EXTR',
                                user_models => SEM_MODELS ('geo_ontology'));
    end;
    /

**Parent topic:** SEM_RDFCTX Package Subprograms

### 18.3 SEM_RDFCTX.DROP_POLICY

#### Format

    SEM_RDFCTX.DROP_POLICY(
         policy_name  IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes (drops) an unused extractor policy.

#### Parameters

policy_name
Name of the extractor policy.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

An exception is generated if the specified policy being is used for a semantic index for documents or if a dependent extractor policy exists for the specified policy.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the `SEM_EXTR_PLUS_GEOONT` extractor policy.

    begin
      sem_rdfctx.drop_policy (policy_name => 'SSEM_EXTR_PLUS_GEOONT');
    end;
    /

**Parent topic:** SEM_RDFCTX Package Subprograms

### 18.4 SEM_RDFCTX.MAINTAIN_TRIPLES

#### Format

    SEM_RDFCTX.MAINTAIN_TRIPLES(
         index_name     IN VARCHAR2,
         where_clause   IN VARCHAR2,
         rdfxml_content IN sys.XMLType,
         policy_name    IN VARCHAR2 DEFAULT NULL,
         action         IN VARCHAR2 DEFAULT 'ADD',
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Adds one or more triples to graphs that contain information extracted from specific documents.

#### Parameters

index_name
Name of the semantic index for documents.

where_clause
A SQL predicate (WHERE clause text without the `WHERE` keyword) on the table in which the documents are stored, to identify the rows for which to maintain the index.

rdfxml_content
Triples, in the form of an RDF/XML document, to be added to the individual graphs corresponding to the documents.

policy_name
Name of the extractor policy. If `policy_name` is null (the default), the triples are added to the information extracted by the default (or the only) extractor policy for the index; if you specify a policy name, the triples are added to the information extracted by that policy.

action
Type of maintenance operation to perform on the triples. The only value currently supported in `ADD` (the default), which adds the triples that are specified in the `rdfxml_content` parameter.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The information extracted from the semantically indexed documents may be incomplete and lacking in proper context. This procedure enables a domain expect to add triples to individual graphs pertaining to specific semantically indexed documents, so that all subsequent SEM_CONTAINS queries can consider these triples in their document search criteria.

This procedure accepts the index name and WHERE clause text to identify the specific documents to be annotated with the additional triples. For example, the where_clause might be specified as a simple predicate involving numeric data, such as `'docId IN (1,2,3)'`.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example annotates a specific document with the semantic index `ArticleIndex` by adding triples to the corresponding individual graph.

    begin
      sem_rdfctx.maintain_triples(
         index_name      => 'ArticleIndex',
         where_clause    => 'docid = 15',
         rdfxml_content => sys.xmltype(
          '<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                    xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#"
                    xmlns:pred="http://myorg.com/pred/">
           <rdf:Description rdf:about=" http://newscorp.com/Org/ExampleCorp">
             <pred:hasShortName
                   rdf:datatype="http://www.w3.org/2001/XMLSchema#string">
                 Example
             </pred:hasShortName>
         </rdf:Description>
        </rdf:RDF>'));
    end;
    /

**Parent topic:** SEM_RDFCTX Package Subprograms

### 18.5 SEM_RDFCTX.SET_DEFAULT_POLICY

#### Format

    SEM_RDFCTX.SET_DEFAULT_POLICY(
         index_name    IN VARCHAR2,
         policy_name   IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Sets the default extractor policy for a semantic index that is configured with multiple extractor policies.

#### Parameters

index_name
Name of the semantic index for documents.

policy_name
Name of the extractor policy to be used as the default extractor policy for the specified semantic index. Must be one of the extractor policies listed in the PARAMETERS clause of the CREATE INDEX statement that created `index_name`.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

When you create a semantic index for documents, you can specify multiple extractor policies as a space-separated list of names in the PARAMETERS clause of the CREATE INDEX statement. As explained in [Semantically Indexing Documents](semantic-indexing-documents.md), the first policy from this list is used as the default extractor policy for all SEM_CONTAINS queries that do not identify an extractor policy by name. You can use the SEM_RDFCTX.SET_DEFAULT_POLICY procedure to set a different default policy for the index.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets `CITY_EXTR` as the default extractor policy for the `ArticleIndex` index.

    begin
      sem_rdfctx.set_default_policy (index_name => 'ArticleIndex',
                                     policy_name => 'CITY_EXTR');
    end;
    /

**Parent topic:** SEM_RDFCTX Package Subprograms

### 18.6 SEM_RDFCTX.SET_EXTRACTOR_PARAM

#### Format

    SEM_RDFCTX.SET_EXTRACTOR_PARAM(
         param_key     IN VARCHAR2,
         patam_value   IN VARCHAR2,
         param_desc    IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Configures the Oracle Database semantic indexing support to work with external information extractors, such as Calais and GATE.

#### Parameters

param_key
Key for the parameter to be set.

param_value
Value for the parameter to be set.

param_desc
Short description for the parameter to be set.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must be connected as SYSTEM (not SYS … AS SYSDBA) or another non-SYS user with the DBA role.

To work with the Calais extractor type (see [Configuring the Calais Extractor type](semantic-indexing-documents.md)), you must specify values for the following parameters:

- `CALAIS_WS_ENDPOINT`: Web service end point for Calais.

- `CALAIS_KEY`: License key for Calais.

- `CALAIS_WS_SOAPACTION`: SOAP action for the Calais Web service.

To work with the General Architecture for Text Engineering (GATE) extractor type (see [Working with General Architecture for Text Engineering (GATE)](semantic-indexing-documents.md)), you must specify values for the following parameters:

- `GATE_NLP_HOST`: Host for the GATE NLP Listener.

- `GATE_NLP_PORT`: Port for the GATE NLP Listener.

In addition to these parameters, you may need to specify a value for the `HTTP_PROXY` parameter to work with information extractors or index documents that are outside the firewall.

A database instance only has one set of values for these parameters, and they are used for all instances of semantic indexes using the corresponding information extractor. You can use this procedure if you need to change the existing values of any of the parameters.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

For examples, see the following sections:

- [Configuring the Calais Extractor type](semantic-indexing-documents.md)

- [Working with General Architecture for Text Engineering (GATE)](semantic-indexing-documents.md)

**Parent topic:** SEM_RDFCTX Package Subprograms
