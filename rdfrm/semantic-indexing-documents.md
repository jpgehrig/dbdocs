## 5 Semantic Indexing for Documents

Information extractors locate and extract meaningful information from unstructured documents. The ability to search for documents based on this extracted information is a significant improvement over the keyword-based searches supported by the full-text search engines.

Semantic indexing for documents introduces an index type that can make use of information extractors and annotators to semantically index documents stored in relational tables. Documents indexed semantically can be searched using SEM_CONTAINS operator within a standard SQL query. The search criteria for these documents are expressed using SPARQL query patterns that operate on the information extracted from the documents, as in the following example.

    SELECT docId
    FROM   Newsfeed
    WHERE  SEM_CONTAINS (article,
         ' { ?org    rdf:type            typ:Organization  .
             ?org    pred:hasCategory    cat:BusinessFinance } ', ..) = 1

The key components that facilitate Semantic Indexing for documents in an Oracle Database include:

- Extensible information extractor framework, which allows third-party information extractors to be plugged into the database

- SEM_CONTAINS operator to identify documents of interest, based on their extracted information, using standard SQL queries

- SEM_CONTAINS_SELECT ancillary operator to return relevant information about the documents identified using SEM_CONTAINS operator

- SemContext index type to interact with the information extractor and manage the information extracted from a document set in an index structure and to facilitate semantically meaningful searches on the documents

The application program interface (API) for managing extractor policies and semantic indexes created for documents is provided in the SEM_RDFCTX PL/SQL package. [SEM_RDFCTX Package Subprograms](SEM_RDFCTX-reference.md) provides the reference information about the subprograms in SEM_RDFCTX package.

- Information Extractors for Semantically Indexing Documents
  Information extractors process unstructured documents and extract meaningful information from them, often using natural-language processing engines with the aid of ontologies.
- Extractor Policies
  An extractor policy is a named dictionary entity that determines the characteristics of a semantic index that is created using the policy.
- Semantically Indexing Documents
  Textual documents stored in a CLOB or VARCHAR2 column of a relational table can be indexed using the MDSYS.SEMCONTEXT index type, to facilitate semantically meaningful searches.
- SEM_CONTAINS and Ancillary Operators
  You can use the SEM_CONTAINS operator in a standard SQL statement to search for documents or document references that are stored in relational tables.
- Searching for Documents Using SPARQL Query Patterns
  Documents that are semantically indexed (that is, indexed using the mdsys.SemContext index type) can be searched using SEM_CONTAINS operator within a standard SQL query.
- Bindings for SPARQL Variables in Matching Subgraphs in a Document (SEM_CONTAINS_SELECT Ancillary Operator)
  You can use the SEM_CONTAINS_SELECT ancillary operator to return additional information about each document matched using the SEM_CONTAINS operator.
- Improving the Quality of Document Search Operations
  The quality of a document search operation depends on the quality of the information produced by the extractor used to index the documents. If the information extracted is incomplete, you may want to add some annotations to a document.
- Indexing External Documents
  You can use semantic indexing on documents that are stored in a file system or on the network. In such cases, you store the references to external documents in a table column, and you create a semantic index on the column using an appropriate extractor policy.
- Configuring the Calais Extractor type
  The CALAIS_EXTRACTOR type, which is a subtype of the RDFCTX_WS_EXTRACTOR type, enables you to access a Web service end point anywhere on the network, including the one that is publicly accessible (`OpenCalais.com`).
- Working with General Architecture for Text Engineering (GATE)
  General Architecture for Text Engineering (GATE) is an open source natural language processor and information extractor.
- Creating a New Extractor Type
  You can create a new extractor type by extending the RDFCTX_EXTRACTOR or RDFCTX_WS_EXTRACTOR extractor type.
- Creating a Local Semantic Index on a Range-Partitioned Table
  A local index can be created on a VARCHAR2 or CLOB column of a range-partitioned table.
- Altering a Semantic Index
  You can use the ALTER INDEX statement with a semantic index.
- Passing Extractor-Specific Parameters in CREATE INDEX and ALTER INDEX
  The CREATE INDEX and ALTER INDEX statements allow the passing of parameters needed by extractors.
- Performing Document-Centric Inference
  Document-centric inference refers to the ability to infer from each document individually.
- Metadata Views for Semantic Indexing
  This section describes views that contain metadata about semantic indexing
- Default Style Sheet for GATE Extractor Output
  This section lists the default XML style sheet that the `mdsys.gatenlp_extractor` implementation uses to convert the annotation set (encoded in XML) into RDF/XML.

**Parent topic:** [Conceptual and Usage Information](part-concept-usage.md)

### 5.1 Information Extractors for Semantically Indexing Documents

Information extractors process unstructured documents and extract meaningful information from them, often using natural-language processing engines with the aid of ontologies.

The quality and the completeness of information extracted from a document vary from one extractor to another. Some extractors simply identify the entities (such as names of persons, organizations, and geographic locations from a document), while the others attempt to identify the relationships among the identified entities and additional description for those entities. You can search for a specific document from a large set when the information extracted from the documents is maintained as a semantic index.

You can use an information extractor to create a semantic index on the documents stored in a column of a relational table. An extensible framework allows any third-party information extractor that is accessible from the database to be plugged into the database. An object type created for an extractor encapsulates the extraction logic, and has methods to configure the extractor and receive information extracted from a given document in RDF/XML format.

An abstract type MDSYS.RDFCTX_EXTRACTOR defines the common interfaces to all information extractors. An implementation of this abstract type interacts with a specific information extractor to produce RDF/XML for a given document. An implementation for this type can access a third-party information extractor that either is available as a database application or is installed on the network (accessed using Web service callouts). Example 5-1 shows the definition of the RDFCTX_EXTRACTOR abstract type.

Example 5-1 RDFCTX_EXTRACTOR Abstract Type Definition

    create or replace type rdfctx_extractor authid current_user as object (
      extr_type        VARCHAR2(32),
      member function  getDescription return VARCHAR2,
      member function  rdfReturnType return VARCHAR2,
      member function  getContext(attribute VARCHAR2) return VARCHAR2,
      member procedure startDriver,
      member function  extractRDF(document CLOB,
                                  docId    VARCHAR2) return CLOB,
      member function  extractRdf(document CLOB,
                                  docId    VARCHAR2,
                                  params   VARCHAR2,
                                  options  VARCHAR2 default NULL) return CLOB
      member function  batchExtractRdf(docCursor        SYS_REFCURSOR,
                                  extracted_info_table  VARCHAR2,
                                  params                VARCHAR2,
                                  partition_name        VARCHAR2 default NULL,
                                  docId                 VARCHAR2 default NULL,
                                  preferences           SYS.XMLType default NULL,
                                  options               VARCHAR2 default NULL)
                                  return CLOB,
      member procedure closeDriver
    ) not instantiable not final
    /

A specific implementation of the RDFCTX_EXTRACTOR type sets an identifier for the extractor type in the `extr_type` attribute, and it returns a short description for the extractor type using `getDescription` method. All implementations of this abstract type return the extracted information as RDF triples. In the current release, the RDF triples are expected to be serialized using RDF/XML format, and therefore the `rdfReturnType` method should return '`RDF/XML`'.

An extractor type implementation uses the `extractRDF` method to encapsulate the extraction logic, possibly by invoking external information extractor using proprietary interfaces, and returns the extracted information in RDF/XML format. When a third-party extractor uses some proprietary XML Schema to capture the extracted information, an XML style sheet can be used to generate an equivalent RDF/XML. The `startDriver` and `closeDriver` methods can perform any housekeeping operations pertaining to the information extractor. The optional `params` parameter allows the extractor to obtain additional information about the type of extraction needed (for example, the desired quality of extraction).

Optionally, an extractor type implementation may support a batch interface by providing an implementation of the `batchExtractRdf` member function. This function accepts a cursor through the input parameter `docCursor` and typically uses that cursor to retrieve each document, extract information from the document, and then insert the extracted information into (the specified partition identified by the `partition_name` partition of the `extracted_info_table` table. The `preferences` parameter is used to obtain the preferences value associated with the policy (as described in Indexing External Documents and in the [SEM_RDFCTX.CREATE_POLICY](SEM_RDFCTX-reference.md) reference section).

The `getContext` member function accepts an attribute name and returns the value for that attribute. Currently this function is used only for extractors supporting the batch interface. The attribute names and corresponding possible return values are the following:

- For the `BATCH_SUPPORT` attribute, the return values are '`YES`' or '`NO`' depending on whether the extractor supports the batch interface.

- For the `DBUSER` attribute, the return value is the name of a database user that will connect to the database to retrieve rows from the cursor (identified by the `docCursor` parameter) and that will write to the table `extracted_info_table`.

This information is used for granting appropriate privileges to the table being indexed and the table `extracted_info_table`.

The `startDriver` and `closeDriver` methods can perform any housekeeping operations pertaining to the information extractor.

An extractor type for the General Architecture for Text Engineering (GATE) engine is defined as a subtype of the RDFCTX_EXTRACTOR type. The implementation of this extractor type sends the documents to a GATE engine over a TCP connection, receives annotations extracted by the engine in XML format, and converts this proprietary XML document to an RDF/XML document. For more information on configuring a GATE engine to work with Oracle Database, see Working with General Architecture for Text Engineering (GATE). For an example of creating a new information extractor, see Creating a New Extractor Type.

Information extractors that are deployed as Web services can be invoked from the database by extending the RDFCTX_WS_EXTRACTOR type, which is a subtype of the RDFCTX_EXTRACTOR type. The RDFCTX_WS_EXTRACTOR type encapsulates the Web service callouts in the `extractRDF` method; specific implementations for network-based extractors can reuse this implementation by setting relevant attribute values in the type constructor.

Thomson Reuters Calais is an example of a network-based information extractor that can be accessed using web-service callouts. The CALAIS_EXTRACTOR type, which is a subtype of the RDFCTX_WS_EXTRACTOR type, encapsulates the Calais extraction logic, and it can be used to semantically index the documents. The CALAIS_EXTRACTOR type must be configured for the database instance before it can be used to create semantic indexes, as explained in Configuring the Calais Extractor type.

**Parent topic:** Semantic Indexing for Documents

### 5.2 Extractor Policies

An extractor policy is a named dictionary entity that determines the characteristics of a semantic index that is created using the policy.

Each extractor policy refers, directly or indirectly, to an instance of an extractor type. An extractor policy with a direct reference to an extractor type instance can be used to compose other extractor policies that include additional RDF models for ontologies.

The following example creates a basic extractor policy created using the GATE extractor type:

    begin
      sem_rdfctx.create_policy (policy_name => 'SEM_EXTR',
                                extractor   => mdsys.gatenlp_extractor());
    end;
    /

The following example creates a dependent extractor policy that combines the metadata extracted by the policy in the preceding example with a user-defined RDF model named `geo_ontology`:

    begin
      sem_rdfctx.create_policy (policy_name => 'SEM_EXTR_PLUS_GEOONT',
                                base_policy => 'SEM_EXTR',
                                user_models => SEM_MODELS ('geo_ontology'));
    end;
    /

You can use an extractor policy to create one or more semantic indexes on columns that store unstructured documents, as explained in Semantically Indexing Documents.

**Parent topic:** Semantic Indexing for Documents

### 5.3 Semantically Indexing Documents

Textual documents stored in a CLOB or VARCHAR2 column of a relational table can be indexed using the MDSYS.SEMCONTEXT index type, to facilitate semantically meaningful searches.

The extractor policy specified at index creation determines the information extractor used to semantically index the documents. The extracted information, captured as a set of RDF triples for each document, is managed in the semantic data store. Each instance of the semantic index is associated with a system-generated RDF model, which maintains the RDF triples extracted from the corresponding documents.

The following example creates a semantic index named `ArticleIndex` on the textual documents in the ARTICLE column of the NEWSFEED table, using the extractor policy named `SEM_EXTR`:

    CREATE INDEX ArticleIndex on Newsfeed (article)
       INDEXTYPE IS mdsys.SemContext PARAMETERS ('SEM_EXTR');

The RDF model created for an index is managed internally and it is not associated with an application table. The triples stored in such model are automatically maintained for any modifications (such as update, insert, or delete) made to the documents stored in the table column. Although a single RDF model is used to index all documents stored in a table column, the triples stored in the model maintain references to the documents from which they are extracted; therefore, all the triples extracted from a specific document form an individual graph within the RDF model. The documents that are semantically indexed can then be searched using a SPARQL query pattern that operates on the triples extracted from the documents.

When creating a semantic index for documents, you can use a basic extractor policy or a dependent policy, which may include one or more user-defined RDF models. When you create an index with a dependent extractor policy, the document search pattern specified using SPARQL could span the triples extracted from the documents as well as those defined in user-defined models.

You can create an index using multiple extractor policies, in which case the triples extracted by the corresponding extractors are maintained separately in distinct RDF models. A document search query using one such index can select the specific policy to be used for answering the query. For example, an extractor policy named `CITY_EXTR` can be created to extract the names of the cities from a given document, and this extractor policy can be used in combination with the SEM_EXTR policy to create a semantic index, as in the following example:

    CREATE INDEX ArticleIndex on Newsfeed (article)
       INDEXTYPE IS mdsys.SemContext PARAMETERS ('SEM_EXTR CITY_EXTR');

The first extractor policy in the PARAMETERS list is considered to be the default policy if a query does not refer to a specific policy; however, you can change the default extractor policy for a semantic index by using the [SEM_RDFCTX.SET_DEFAULT_POLICY](SEM_RDFCTX-reference.md) procedure, as in the following example:

    begin
      sem_rdfctx.set_default_policy (index_name => 'ArticleIndex',
                                     policy_name => 'CITY_EXTR');
    end;
    /

**Parent topic:** Semantic Indexing for Documents

### 5.4 SEM_CONTAINS and Ancillary Operators

You can use the SEM_CONTAINS operator in a standard SQL statement to search for documents or document references that are stored in relational tables.

This operator has the following syntax:

    SEM_CONTAINS(
      column   VARCHAR2 / CLOB,
      sparql   VARCHAR2,
      policy   VARCHAR2,
      aliases  SEM_ALIASES,
      index_status  NUMBER,
      ancoper  NUMBER
     ) RETURN NUMBER;

The `column` and `sparql` attributes attribute are required. The other attributes are optional (that is, each can be a null value).

The `column` attribute identifies a VARCHAR2 or CLOB column in a relational table that stores the documents or references to documents that are semantically indexed. An index of type MDSYS.SEMCONTEXT must be defined in this column for the SEM_CONTAINS operator to use.

The `sparql` attribute is a string literal that defines the document search criteria, expressed in SPARQL format.

The optional `policy` attribute specifies the name of an extractor policy, usually to override the default policy. A semantic document index can have one or more extractor policies specified at index creation, and one of these policies is the default, which is used if the `policy` attribute is null in the call to SEM_CONTAINS.

The optional `aliases` attribute identifies one or more namespaces, including a default namespace, to be used for expansion of qualified names in the query pattern. Its data type is SEM_ALIASES, which has the following definition: `TABLE OF SEM_ALIAS`, where each SEM_ALIAS element identifies a namespace ID and namespace value. The SEM_ALIAS data type has the following definition: `(namespace_id VARCHAR2(30), namespace_val VARCHAR2(4000))`

The optional `index_status` attribute is relevant only when a dependent policy involving one or more entailments is being used for the SEM_CONTAINS invocation. The `index_status` value identifies the minimum required validity status of the entailments. The possible values are `0` (for VALID, the default), `1` (for INCOMPLETE), and `2` (for INVALID).

The optional `ancoper` attribute specifies a number as the binding to be used when the SEM_CONTAINS_SELECT ancillary operator is used with this operator in a query. The number specified for the `ancoper` attribute should be the same as number specified for the `operbind` attribute in the SEM_CONTAINS_SELECT ancillary operator.

The SEM_CONTAINS operator returns 1 for each document instance matching the specified search criteria, and returns 0 for all other cases.

For more information about using the SEM_CONTAINS operator, including an example, see Searching for Documents Using SPARQL Query Patterns.

- SEM_CONTAINS_SELECT Ancillary Operator
- SEM_CONTAINS_COUNT Ancillary Operator

**Parent topic:** Semantic Indexing for Documents

#### 5.4.1 SEM_CONTAINS_SELECT Ancillary Operator

You can use the SEM_CONTAINS_SELECT ancillary operator to return additional information about each document that matches some search criteria. This ancillary operator has a single numerical attribute (`operbind`) that associates an instance of the SEM_CONTAINS_SELECT ancillary operator with a SEM_CONTAINS operator by using the same value for the binding. This ancillary operator returns an object of type CLOB that contains the additional information from the matching document, formatted in SPARQL Query Results XML format.

The SEM_CONTAINS_SELECT ancillary operator has the following syntax:

    SEM_CONTAINS_SELECT(
      operbind  NUMBER
     ) RETURN CLOB;

For more information about using the SEM_CONTAINS_SELECT ancillary operator, including examples, see Bindings for SPARQL Variables in Matching Subgraphs in a Document (SEM_CONTAINS_SELECT Ancillary Operator).

**Parent topic:** SEM_CONTAINS and Ancillary Operators

#### 5.4.2 SEM_CONTAINS_COUNT Ancillary Operator

You can use the SEM_CONTAINS_COUNT ancillary operator for a SEM_CONTAINS operator invocation. For each matched document, it returns the count of matching subgraphs for the SPARQL graph pattern specified in the SEM_CONTAINS invocation.

The SEM_CONTAINS_COUNT ancillary operator has the following syntax:

    SEM_CONTAINS_COUNT(
      operbind  NUMBER
     ) RETURN NUMBER;

The following example excerpt shows the use of the SEM_CONTAINS_COUNT ancillary operator to return the count of matching subgraphs for each matched document:

    SELECT docId, SEM_CONTAINS_COUNT(1) as matching_subgraph_count
    FROM   Newsfeed
    WHERE  SEM_CONTAINS (article,
      '{ ?org   rdf:type          class:Organization  .
         ?org   pred:hasCategory  cat:BusinessFinance }', ..,
       1)= 1;

**Parent topic:** SEM_CONTAINS and Ancillary Operators

### 5.5 Searching for Documents Using SPARQL Query Patterns

Documents that are semantically indexed (that is, indexed using the mdsys.SemContext index type) can be searched using SEM_CONTAINS operator within a standard SQL query.

In the query, the SEM_CONTAINS operator must have at least two parameters, the first specifying the column in which the documents are stored and the second specifying the document search criteria expressed as a SPARQL query pattern, as in the following example:

    SELECT docId FROM Newsfeed
    WHERE  SEM_CONTAINS (article,
      '{ ?org  rdf:type  <http://www.example.com/classes/Organization>  .
         ?org  <http://example.com/pred/hasCategory>
                 <http://www.example.com/category/BusinessFinance> }'
               )= 1;

The SPARQL query pattern specified with the SEM_CONTAINS operator is matched against the individual graphs corresponding to each document, and a document is considered to match a search criterion if the triples from the corresponding graph satisfy the query pattern. In the preceding example, the SPARQL query pattern identifies the individual graphs (thus, the documents) that refer to an `Organization` that belong to `BusinessFinance` category. The SQL query returns the rows corresponding to the matching documents in its result set. The preceding example assumes that the URIs used in the query are generated by the underlying extractor, and that you (the user searching for documents) are aware of the properties and terms that are generated by the extractor in use.

When you create an index using a dependent extractor policy that includes one or more user-defined RDF models, the triples asserted in the user models are considered to be common to all the documents. Document searches involving such policies test the search criteria against the triples in individual graphs corresponding to the documents, combined with the triples in the user models. For example, the following query identifies all articles referring to organizations in the state of New Hampshire, using the geographical ontology (`geo_ontology` RDF Model from a preceding example) that maps cities to states:

    SELECT docId FROM   Newsfeed
    WHERE  SEM_CONTAINS (article,
            '{ ?org     rdf:type          class:Organization  .
               ?org     pred:hasLocation  ?city .
               ?city    geo:hasState      state:NewHampshire }',
            'SEM_EXTR_PLUS_GEOONT',
                   sem_aliases(
                      sem_alias('class', 'http://www.myorg.com/classes/'),
                      sem_alias('pred', 'http://www.myorg.com/pred/'),
                      sem_alias('geo', 'http://geoont.org/rel/'),
                      sem_alias('state', 'http://geoont.org/state/'))) = 1;

The preceding query, with a reference to the extractor policy SEM_EXTR_PLUS_GEOONT (created in an example in Extractor Policies), combines the triples extracted from the indexed documents and the triples in the user model to find matching documents. In this example, the name of the extractor policy is optional if the corresponding index is created with just this policy or if this is the default extractor policy for the index. When the query pattern uses some qualified names, an optional parameter to the SEM_CONTAINS operator can specify the namespaces to be used for expanding the qualified names.

SPARQL-based document searches can make use of the SPARQL syntax that is supported through SEM_MATCH queries.

**Parent topic:** Semantic Indexing for Documents

### 5.6 Bindings for SPARQL Variables in Matching Subgraphs in a Document (SEM_CONTAINS_SELECT Ancillary Operator)

You can use the SEM_CONTAINS_SELECT ancillary operator to return additional information about each document matched using the SEM_CONTAINS operator.

Specifically, the bindings for the variables used in SPARQL-based document search criteria can be returned using this operator. This operator is ancillary to the SEM_CONTAINS operator, and a literal number is used as an argument to this operator to associate it with a specific instance of SEM_CONTAINS operator, as in the following example:

    SELECT docId, SEM_CONTAINS_SELECT(1) as result
    FROM   Newsfeed
    WHERE  SEM_CONTAINS (article,
      '{ ?org   rdf:type          class:Organization  .
         ?org   pred:hasCategory  cat:BusinessFinance }', ..,
       1)= 1;

The SEM_CONTAINS_SELECT ancillary operator returns the bindings for the variables in SPARQL Query Results XML format, as CLOB data. The variables may be bound to multiple data instances from a single document, in which case all bindings for the variables are returned. The following example is an excerpt from the output of the preceding query: a value returned by the SEM_CONTAINS_SELECT ancillary operator for a document matching the specified search criteria.

    <results>
      <result>
         <binding name="ORG">
            <uri>http://newscorp.com/Org/AcmeCorp</uri>
         </binding>
      </result>
      <result>
         <binding name="ORG">
           <uri>http://newscorp.com/Org/ABCCorp</uri>
         </binding>
      </result>
    </results>

You can rank the search results by creating an instance of XMLType for the CLOB value returned by the SEM_CONTAINS_SELECT ancillary operator and applying an XPath expression to sort the results on some attribute values.

By default, the SEM_CONTAINS_SELECT ancillary operator returns bindings for all variables used in the SPARQL-based document search criteria. However, when the values for only a subset of the variables are relevant for a search, the SPARQL pattern can include a SELECT clause with space-separated list of variables for which the values should be returned, as in the following example:

    SELECT docId, SEM_CONTAINS_SELECT(1) as result
    FROM   Newsfeed
    WHERE  SEM_CONTAINS (article,
            'SELECT ?org  ?city
             WHERE { ?org     rdf:type          class:Organization  .
                     ?org     pred:hasLocation  ?city .
                     ?city    geo:hasState      state:NewHampshire }', ..,
             1) = 1;

**Parent topic:** Semantic Indexing for Documents

### 5.7 Improving the Quality of Document Search Operations

The quality of a document search operation depends on the quality of the information produced by the extractor used to index the documents. If the information extracted is incomplete, you may want to add some annotations to a document.

You can use the [SEM_RDFCTX.MAINTAIN_TRIPLES](SEM_RDFCTX-reference.md) procedure to add annotations, in the form of RDF triples, to specific documents in order to improve the quality of search, as shown in the following example:

    begin
      sem_rdfctx.maintain_triples(
         index_name      => 'ArticleIndex',
         where_clause    => 'docid in (1,15,20)',
         rdfxml_content => sys.xmltype(
          '<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                    xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#"
                    xmlns:pred="http://example.com/pred/">
           <rdf:Description rdf:about=" http://newscorp.com/Org/ExampleCorp">
             <pred:hasShortName
                   rdf:datatype="http://www.w3.org/2001/XMLSchema#string">
                 Example
             </pred:hasShortName>
         </rdf:Description>
        </rdf:RDF>'));
    end;
    /

The index name and the WHERE clause specified in the preceding example identify specific instances of the document to be annotated, and the RDF/XML content passed in is used to add additional triples to the individual graphs corresponding to those documents. This allows domain experts and user communities to improve the quality of search by adding relevant triples to annotate some documents.

**Parent topic:** Semantic Indexing for Documents

### 5.8 Indexing External Documents

You can use semantic indexing on documents that are stored in a file system or on the network. In such cases, you store the references to external documents in a table column, and you create a semantic index on the column using an appropriate extractor policy.

To index external documents, define an extractor policy with appropriate preferences, using an XML document that is assigned to the `preferences` parameter of the [SEM_RDFCTX.CREATE_POLICY](SEM_RDFCTX-reference.md) procedure, as in the following example:

    begin
      sem_rdfctx.create_policy (
           policy_name => 'SEM_EXTR_FROM_FILE',
           extractor   => mdsys.gatenlp_extractor()),
           preferences => sys.xmltype('<RDFCTXPreferences>
                                         <Datastore type="FILE">
                                            <Path>EXTFILES_DIR</Path>
                                         </Datastore>
                                       </RDFCTXPreferences>'));
    end;
    /

The `<Datastore>` element in the preferences document specifies the type of repository used for the documents to be indexed. When the value for the `type` attribute is set to `FILE`, the `<Path>` element identifies a directory object in the database (created using the SQL statement CREATE DIRECTORY). A table column indexed using the specified extractor policy is expected to contain relative paths to individual files within the directory object, as shown in the following example:

    CREATE TABLE newsfeed (docid       number,
                           articleLoc  VARCHAR2(100));
    INSERT INTO into newsfeed (docid, articleLoc) values
                         (1, 'article1.txt');
    INSERT INTO newsfeed (docid, articleLoc) values
                         (2, 'folder/article2.txt');

    CREATE INDEX ArticleIndex on newsfeed (articleLoc)
       INDEXTYPE IS mdsys.SemContext PARAMETERS ('SEM_EXTR_FROM_FILE');

To index documents that are accessed using HTTP protocol, create a extractor policy with preferences that set the `type` attribute of the `<Datastore>` element to `URL` and that list one or more hosts in the `<Path>` elements, as shown in the following excerpt:

    <RDFCTXPreferences>
       <Datastore type="URL">
           <Path>http://cnn.com</Path>
           <Path>http://abc.com</Path>
       </Datastore>
    </RDFCTXPreferences>

The schema in which a semantic index for external documents is created must have the necessary privileges to access the external objects, including access to any proxy server used to access documents outside the firewall, as shown in the following example:

    -- Grant read access to the directory object for FILE data store --
    grant read on directory EXTFILES_DIR to SEMUSR;

    -- Grant connect access to set of hosts for URL data store --
    begin
      dbms_network_acl_admin.create_acl (
                    acl          => 'network_docs.xml',
                    description  => 'Normal Access',
                    principal    => 'SEMUSR',
                    is_grant     => TRUE,
                    privilege    => 'connect');
    end;
    /

    begin
      dbms_network_acl_admin.assign_acl (
                   acl        => 'network_docs.xml',
                   host       =>  'cnn.com',
                   lower_port => 1,
                   upper_port => 10000);
    end;
    /

External documents that are semantically indexed in the database may be in one of the well-known formats such as Microsoft Word, RTF, and PDF. This takes advantage of the Oracle Text capability to extract plain text version from formatted documents using filters (see the CTX_DOC.POLICY_FILTER procedure, described in [Oracle Text Reference](../ccref/CTX_DOC-package.md)). To semantically index formatted documents, you must specify the name of a CTX policy in the extractor preferences, as shown in the following excerpt:

    <RDFCTXPreferences>
       <Datastore type="FILE" filter="CTX_FILTER_POLICY">
           <Path>EXTFILES_DIR</Path>
       </Datastore>
    </RDFCTXPreferences>

In the preceding example, the `CTX_FILTER_POLICY` policy, created using the CTX_DDL.CREATE_POLICY procedure, must exist in your schema. The table columns that are semantically indexed using this preferences document can store paths to formatted documents, from which plain text is extracted using the specified CTX policy. The information extractor associated with the extractor policy then processes the plain text further, to extract the semantics in RDF/XML format.

**Parent topic:** Semantic Indexing for Documents

### 5.9 Configuring the Calais Extractor type

The CALAIS_EXTRACTOR type, which is a subtype of the RDFCTX_WS_EXTRACTOR type, enables you to access a Web service end point anywhere on the network, including the one that is publicly accessible (`OpenCalais.com`).

To do so, you must connect as SYSTEM (not SYS … AS SYSDBA) or another non-SYS user with the DBA role, and configure the Calais extractor type with Web service end point, the SOAP action, and the license key by setting corresponding parameters, as shown in the following example:

    begin
      sem_rdfctx.set_extractor_param (
         param_key   => 'CALAIS_WS_ENDPOINT',
         param_value => 'http://api1.opencalais.com/enlighten/calais.asmx',
         param_desc  => 'Calais web service end-point');

      sem_rdfctx.set_extractor_param (
         param_key   => 'CALAIS_KEY',
         param_value => '<Calais license key goes here>',
         param_desc  => 'Calais extractor license key');

      sem_rdfctx.set_extractor_param (
         param_key   => 'CALAIS_WS_SOAPACTION',
         param_value => 'http://clearforest.com/Enlighten',
         param_desc  => 'Calais web service SOAP Action');
    end;

To enable access to a Web service outside the firewall, you must also set the parameter for the proxy host, as in the following example:

    begin
      sem_rdfctx.set_extractor_param (
          param_key   => 'HTTP_PROXY',
          param_value => 'www-proxy.example.com',
          param_desc  => 'Proxy server');
    end;

**Parent topic:** Semantic Indexing for Documents

### 5.10 Working with General Architecture for Text Engineering (GATE)

General Architecture for Text Engineering (GATE) is an open source natural language processor and information extractor.

For details about GATE, see [`http://gate.ac.uk`](http://gate.ac.uk).

You can use GATE to perform semantic indexing of documents stored in the database. The extractor type `mdsys.gatenlp_extractor` is defined as a subtype of the RDFCTX_EXTRACTOR type. The implementation of this extractor type sends an unstructured document to a GATE engine over a TCP connection, receives corresponding annotations, and converts them into RDF following a user-specified XML style sheet.

The requests for information extraction are handled by a server socket implementation, which instantiates the GATE components and listens to extraction requests at a pre-determined port. The host and the post for the GATE listener are recorded in the database, as shown in the following example, for all instances of the `mdsys.gatenlp_extractor` type to use.

    begin
      sem_rdfctx.set_extractor_param (
         param_key   => 'GATE_NLP_HOST',
         param_value => 'gateserver.example.com',
         param_desc  => 'Host for GATE NLP Listener ');

      sem_rdfctx.set_extractor_param (
         param_key   => 'GATE_NLP_PORT',
         param_value => '7687',
         param_desc  => 'Port for Gate NLP Listener');
    end;

The server socket application receives an unstructured document and constructs an annotation set with the desired types of annotations. Each annotation in the set may be customized to include additional features, such as the relevant phrase from the input document and some domain specific features. The resulting annotation set is serialized into XML (using the `annotationSetToXml` method in the `gate.corpora.DocumentXmlUtils` Java package) and returned back to the socket client.

A sample Java implementation for the GATE listener is available for download from the code samples and examples page on OTN (see [Semantic Data Examples (PL/SQL and Java)](rdf-semantic-graph-overview.md) for information about this page).

The `mdsys.gatenlp_extractor` implementation in the database receives the annotation set encoded in XML, and converts it to RDF/XML using an XML style sheet. You can replace the default style sheet (listed in Default Style Sheet for GATE Extractor Output) used by the `mdsys.gatenlp_extractor` implementation with a custom style sheet when you instantiate the type.

The following example creates an extractor policy that uses a custom style sheet to generate RDF from the annotation set produced by the GATE extractor:

    begin
      sem_rdfctx.create_policy (policy_name => 'GATE_EXTR',
                                extractor   => mdsys.gatenlp_extractor(
          sys.XMLType('<?xml version="1.0"?>
                     <xsl:stylesheet version="2.0"
                        xmlns:xsl="http://www.w3.org/1999/XSL/Transform" >
                       ..
                     </xsl:stylesheet>')));
    end;
    /

**Parent topic:** Semantic Indexing for Documents

### 5.11 Creating a New Extractor Type

You can create a new extractor type by extending the RDFCTX_EXTRACTOR or RDFCTX_WS_EXTRACTOR extractor type.

The extractor type to be extended must be accessible using Web service calls. The schema in which the new extractor type is created must be granted additional privileges to allow creation of the subtype. For example, if a new extractor type is created in the schema RDFCTXU, you must enter the following commands to grant the UNDER and RDFCTX_ADMIN privileges to that schema:

    GRANT under ON mdsys.rdfctx_extractor TO rdfctxu;
    GRANT rdfctx_admin TO rdfctxu;

As an example, assume that an information extractor can process an incoming document and return an XML document that contains extracted information. To enable the information extractor to be invoked using a PL/SQL wrapper, you can create the corresponding extractor type implementation, as in the following example:

    create or replace type rdfctxu.info_extractor under rdfctx_extractor (
      xsl_trans   sys.XMLtype,
      constructor function info_extractor (
                     xsl_trans  sys.XMLType ) return self as result,
      overriding member function getDescription return VARCHAR2,
      overriding member function rdfReturnType return VARCHAR2,
      overriding member function extractRDF(document CLOB,
                                            docId    VARCHAR2) return CLOB
    )
    /

    create or replace type body rdfctxu.info_extractor as
      constructor function info_extractor (
                     xsl_trans  sys.XMLType ) return self as result is
      begin
        self.extr_type := 'Info Extractor Inc.';
        -- XML style sheet to generate RDF/XML from proprietary XML documents
        self.xsl_trans := xsl_trans;
        return;
      end info_extractor;

      overriding member function getDescription return VARCHAR2 is
      begin
        return 'Extactor by Info Extractor Inc.';
      end getDescription;

      overriding member function rdfReturnType return VARCHAR2 is
      begin
        return 'RDF/XML';
      end rdfReturnType;

      overriding member function extractRDF(document CLOB,
                                            docId    VARCHAR2) return CLOB is
        ce_xmlt  sys.xmltype;
      begin
        EXECUTE IMMEDIATE
          'begin :1 = info_extract_xml(doc => :2); end;'
           USING IN OUT ce_xmlt, IN document;

        -- Now pass the ce_xmlt through RDF/XML transformation --
        return ce_xmlt.transform(self.xsl_trans).getClobVal();
      end extractRdf;

    end;

In the preceding example:

- The implementation for the created `info_extractor` extractor type relies on the XML style sheet, set in the constructor, to generate RDF/XML from the proprietary XML schema used by the underlying information extractor.

- The `extractRDF` function assumes that the `info_extract_xml` function contacts the desired information extractor and returns an XML document with the information extracted from the document that was passed in.

- The XML style sheet is applied on the XML document to generate equivalent RDF/XML, which is returned by the `extractRDF` function.

**Parent topic:** Semantic Indexing for Documents

### 5.12 Creating a Local Semantic Index on a Range-Partitioned Table

A local index can be created on a VARCHAR2 or CLOB column of a range-partitioned table.

To do so, use the following syntax:

    CREATE INDEX <index-name> … LOCAL;

The following example creates a range-partitioned table and a local semantic index on that table:

    CREATE TABLE part_newsfeed (
      docid number, article CLOB, cdate DATE)
    partition by range (cdate)
    (partition p1 values less than (to_date('01-Jan-2001')),
     partition p2 values less than (to_date('01-Jan-2004')),
     partition p3 values less than (to_date('01-Jan-2008')),
     partition p4 values less than (to_date('01-Jan-2012'))
    );

    CREATE INDEX ArticleLocalIndex on part_newsfeed (article)
       INDEXTYPE IS mdsys.SemContext PARAMETERS ('SEM_EXTR')
    LOCAL;

Note that every partition of the local semantic index will have content generated for the same set of policies. When you use the ALTER INDEX statement on a local index to add or drop policies associated with a semantic index partition, you should try to keep the same set of policies associated with each partition. You can achieve this result by using ALTER INDEX statements in a loop over the set of partitions. (For more information about altering semantic indexes, see Altering a Semantic Index,)

**Parent topic:** Semantic Indexing for Documents

### 5.13 Altering a Semantic Index

You can use the ALTER INDEX statement with a semantic index.

For a local semantic index, the ALTER INDEX statement applies to a specified partition. The general syntax of the ALTER INDEX command for a semantic index is as follows:

    ALTER INDEX <index-name> REBUILD [PARTITION <index-partition-name>]
      [PARAMETERS ('-<action_for_policy> <policy-name>')];

- Rebuilding Content for All Existing Policies in a Semantic Index
- Rebuilding to Add Content for a New Policy to a Semantic Index
- Rebuilding Content for an Existing Policy from a Semantic Index
- Rebuilding to Drop Content for an Existing Policy from a Semantic Index

**Parent topic:** Semantic Indexing for Documents

#### 5.13.1 Rebuilding Content for All Existing Policies in a Semantic Index

If the PARAMETERS clause is not included in the ALTER INDEX statement, the content of the semantic index (or index partition) is rebuilt for every policy presently associated with the index. The following are two examples:

    ALTER INDEX ArticleIndex REBUILD;
    ALTER INDEX ArticleLocalIndex REBUILD PARTITION p1;

**Parent topic:** Altering a Semantic Index

#### 5.13.2 Rebuilding to Add Content for a New Policy to a Semantic Index

Using `add_policy` for \<action_for_policy\>, you can add content for a new base policy or a dependent policy to a semantic index (or index partition). If a dependent policy is being added and if its base policy is not already a part of the index, then content for the base policy is also added implicitly (by invoking the extractor specified as part of the base policy definition). The following is an example:

    ALTER INDEX ArticleIndex REBUILD PARAMETERS ('-add_policy MY_POLICY');

**Parent topic:** Altering a Semantic Index

#### 5.13.3 Rebuilding Content for an Existing Policy from a Semantic Index

Using `rebuild_policy` for \<action_for_policy\>, you can rebuild the content of the semantic index (or index partition) for an existing policy presently associated with the index. The following is an example:

    ALTER INDEX ArticleIndex REBUILD PARAMETERS ('-rebuild_policy MY_POLICY');

**Parent topic:** Altering a Semantic Index

#### 5.13.4 Rebuilding to Drop Content for an Existing Policy from a Semantic Index

Using `drop_policy` for \<action_for_policy\>, you can drop content corresponding to an existing base policy or a dependent policy from a semantic index (or index partition). Note that dropping the content for a base policy will fail if it is the only policy for the index (or index partition) or if it is used by dependent policies associated with this index (or index partition).

The following example drops the content for a policy from an index:

    ALTER INDEX ArticleIndex REBUILD PARAMETERS ('-drop_policy MY_POLICY');

**Parent topic:** Altering a Semantic Index

### 5.14 Passing Extractor-Specific Parameters in CREATE INDEX and ALTER INDEX

The CREATE INDEX and ALTER INDEX statements allow the passing of parameters needed by extractors.

These parameters are passed on to the extractor using the `params` parameter of the `extractRdf` and `batchExtractRdf` methods. The following two examples show their use:

    CREATE INDEX ArticleIndex on Newsfeed (article)
      INDEXTYPE IS mdsys.SemContext PARAMETERS ('SEM_EXTR=(NE_ONLY)');

    ALTER INDEX ArticleIndex REBUILD
      PARAMETERS ('-add_policy MY_POLICY=(NE_ONLY)');

**Parent topic:** Semantic Indexing for Documents

### 5.15 Performing Document-Centric Inference

Document-centric inference refers to the ability to infer from each document individually.

It does not allow triples extracted from two different documents to be used together for inference. It contrasts with the more common corpus-centric inference, where new triples can be inferred from combinations of triples extracted from multiple documents.

Document-centric inference can be desirable in document search applications because inclusion of a document in the search result is based on the extracted and/or inferred triples for that document only, that is, triples extracted and/or inferred from any other documents in the corpus do not play any role in the selection of this document. (Document-centric inference might be preferred, for example, if there is inconsistency among documents because of differences in the reliability of the data or in the biases of the document creators.)

To perform document-centric inference, use named graph based local inference (explained in [Named Graph Based Local Inference (NGLI)](owl-concepts.md)) by specifying `options => 'LOCAL_NG_INF=T'` in the call to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure.

Entailments created through document-centric inference can be included as content of a semantic index by creating a dependent policy and adding that policy to the semantic index, as shown in Example 5-2.

Example 5-2 Using Document-Centric Inference

    -- Create entailment 'extr_data_inf' using document-centric inference
    -- assuming:
    --   model_name for semantic index based on base policy: 'RDFCTX_MOD_1'
    --    (model name is available from the RDFCTX_INDEX_POLICIES view;
    --     see RDFCTX_INDEX_POLICIES View)
    --   ontology: dataOntology
    --   rulebase: OWL2RL
    -- options: 'LOCAL_NG_INF=T' (for document-centric inference)
    BEGIN
    sem_apis.create_entailment('extr_data_inf',
      models_in    => sem_models('RDFCTX_MOD_1', 'dataOntology'),
      rulebases_in => sem_rulebases('OWL2RL'),
      options      => 'LOCAL_NG_INF=T');
    END;
    /
    -- Create a dependent policy to augment data extracted using base policy
    -- with content of entailment extr_data_inf (computed in previous statement)
    BEGIN
    sem_rdfctx.create_policy (
      policy_name => 'SEM_EXTR_PLUS_DATA_INF',
      base_policy => 'SEM_EXTR',
      user_models => NULL,
      user_entailments => sem_models('extr_data_inf'));
    END;
    /
    -- Add the dependent policy to the ARTICLEINDEX index.
    EXECUTE sem_rdfctx.add_dependent_policy('ARTICLEINDEX','SEM_EXTR_PLUS_DATA_INF');

**Parent topic:** Semantic Indexing for Documents

### 5.16 Metadata Views for Semantic Indexing

This section describes views that contain metadata about semantic indexing

- MDSYS.RDFCTX_POLICIES View
- RDFCTX_INDEX_POLICIES View
- RDFCTX_INDEX_EXCEPTIONS View

**Parent topic:** Semantic Indexing for Documents

#### 5.16.1 MDSYS.RDFCTX_POLICIES View

Information about extractor policies defined in the current schema is maintained in the MDSYS.RDFCTX_POLICIES view, which has the columns shown in Table 5-1 and one row for each extractor policy.

Table 5-1 MDSYS.RDFCTX_POLICIES View Columns

| Column Name  | Data Type              | Description                                                                                                                                    |
|:-------------|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| POLICY_OWNER | VARCHAR2(32)           | Owner of the extractor policy                                                                                                                  |
| POLICY_NAME  | VARCHAR2(32)           | Name of the extractor policy                                                                                                                   |
| EXTRACTOR    | MDSYS.RDFCTX_EXTRACTOR | Instance of extractor type                                                                                                                     |
| IS_DEPENDENT | VARCHAR2(3)            | Contains `YES` if the extractor policy is dependent on a base policy; contains `NO` if the extractor policy is not dependent on a base policy. |
| BASE_POLICY  | VARCHAR2(32)           | For a dependent policy, the name of the base policy                                                                                            |
| USER_MODELS  | MDSYS.RDF_MODELS       | For a dependent policy, a list of the RDF models included in the policy                                                                        |

**Parent topic:** Metadata Views for Semantic Indexing

#### 5.16.2 RDFCTX_INDEX_POLICIES View

Information about semantic indexes defined in the current schema and the extractor policies used to create the index is maintained in the MDSYS.RDFCTX_POLICIES view, which has the columns shown in Table 5-2 and one row for each combination of semantic index and extractor policy.

Table 5-2 MDSYS.RDFCTX_INDEX_POLICIES View Columns

| Column Name     | Data Type     | Description                                                                                                                                                    |
|:----------------|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| INDEX_OWNER     | VARCHAR2(32)  | Owner of the semantic index                                                                                                                                    |
| INDEX_NAME      | VARCHAR2(32)  | Name of the semantic index                                                                                                                                     |
| INDEX_PARTITION | VARCHAR2(32)  | Name of the index partition (for LOCAL index only)                                                                                                             |
| POLICY_NAME     | VARCHAR2(32)  | Name of the extractor policy                                                                                                                                   |
| EXTR_PARAMETERS | VARCHAR2(100) | Parameters specified for the extractor                                                                                                                         |
| IS_DEFAULT      | VARCHAR2(3)   | Contains `YES` if POLICY_NAME is the default extractor policy for the index; contains `NO` if POLICY_NAME is not the default extractor policy for the index.   |
| STATUS          | VARCHAR2(10)  | Contains `VALID` if the index is valid, `INPROGRESS` if the index is being created, or `FAILED` if a system failure occurred during the creation of the index. |
| RDF_MODEL       | VARCHAR2(32)  | Name of the RDF model maintaining the index data                                                                                                               |

**Parent topic:** Metadata Views for Semantic Indexing

#### 5.16.3 RDFCTX_INDEX_EXCEPTIONS View

Information about exceptions encountered while creating or maintaining semantic indexes in the current schema is maintained in the MDSYS.RDFCTX_INDEX_EXCEPTIONS view, which has the columns shown in Table 5-3 and one row for each exception.

Table 5-3 MDSYS.RDFCTX_INDEX_EXCEPTIONS View Columns

| Column Name    | Data Type    | Description                                                          |
|:---------------|:-------------|:---------------------------------------------------------------------|
| INDEX_OWNER    | VARCHAR2(32) | Owner of the semantic index associated with the exception            |
| INDEX_NAME     | VARCHAR2(32) | Name of the semantic index associated with the exception             |
| POLICY_NAME    | VARCHAR2(32) | Name of the extractor policy associated with the exception           |
| DOC_IDENTIFIER | VARCHAR2(38) | Row identifier (rowid) of the document associated with the exception |
| EXCEPTION_TYPE | VARCHAR2(13) | Type of exception                                                    |
| EXCEPTION_CODE | NUMBER       | Error code associated with the exception                             |
| EXCEPTION_TEXT | CLOB         | Text associated with the exception                                   |
| EXTRACTED_AT   | TIMESTAMP    | Time at which the exception occurred                                 |

**Parent topic:** Metadata Views for Semantic Indexing

### 5.17 Default Style Sheet for GATE Extractor Output

This section lists the default XML style sheet that the `mdsys.gatenlp_extractor` implementation uses to convert the annotation set (encoded in XML) into RDF/XML.

(This extractor is explained in Working with General Architecture for Text Engineering (GATE).)

    <?xml version="1.0"?>
      <xsl:stylesheet version="2.0"
                       xmlns:xsl="http://www.w3.org/1999/XSL/Transform" >
         <xsl:output encoding="utf-8" indent="yes"/>
         <xsl:param name="docbase">http://xmlns.oracle.com/rdfctx/</xsl:param>
         <xsl:param name="docident">0</xsl:param>
         <xsl:param name="classpfx">
           <xsl:value-of select="$docbase"/>
           <xsl:text>class/</xsl:text>
         </xsl:param>
         <xsl:template match="/">
            <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                     xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#"
                     xmlns:owl="http://www.w3.org/2002/07/owl#"
                     xmlns:prop="http://xmlns.oracle.com/rdfctx/property/">
            <xsl:for-each select="AnnotationSet/Annotation">
              <rdf:Description>
                <xsl:attribute name="rdf:about">
                  <xsl:value-of select="$docbase"/>
                  <xsl:text>docref/</xsl:text>
                  <xsl:value-of select="$docident"/>
                  <xsl:text>/</xsl:text>
                  <xsl:value-of select="@Id"/>
                </xsl:attribute>
                <xsl:for-each select="./Feature">
                  <xsl:choose>
                    <xsl:when test="./Name[text()='majorType']">
                      <rdf:type>
                        <xsl:attribute name="rdf:resource">
                           <xsl:value-of select="$classpfx"/>
                           <xsl:text>major/</xsl:text>
                           <xsl:value-of select="translate(./Value/text(),
                                                           ' ', '#')"/>
                        </xsl:attribute>
                      </rdf:type>
                    </xsl:when>
                    <xsl:when test="./Name[text()='minorType']">
                      <xsl:element name="prop:hasMinorType">
                        <xsl:attribute name="rdf:resource">
                           <xsl:value-of select="$docbase"/>
                           <xsl:text>minorType/</xsl:text>
                           <xsl:value-of select="translate(./Value/text(),
                                                           ' ', '#')"/>
                        </xsl:attribute>
                      </xsl:element>
                    </xsl:when>
                    <xsl:when test="./Name[text()='kind']">
                      <xsl:element name="prop:hasKind">
                        <xsl:attribute name="rdf:resource">
                           <xsl:value-of select="$docbase"/>
                           <xsl:text>kind/</xsl:text>
                           <xsl:value-of select="translate(./Value/text(),
                                                           ' ', '#')"/>
                        </xsl:attribute>
                      </xsl:element>
                    </xsl:when>
                    <xsl:when test="./Name[text()='locType']">
                      <xsl:element name="prop:hasLocType">
                        <xsl:attribute name="rdf:resource">
                           <xsl:value-of select="$docbase"/>
                           <xsl:text>locType/</xsl:text>
                           <xsl:value-of select="translate(./Value/text(),
                                                           ' ', '#')"/>
                        </xsl:attribute>
                      </xsl:element>
                    </xsl:when>
                    <xsl:when test="./Name[text()='entityValue']">
                      <xsl:element name="prop:hasEntityValue">
                        <xsl:attribute name="rdf:datatype">
                          <xsl:text>
                             http://www.w3.org/2001/XMLSchema#string
                          </xsl:text>
                        </xsl:attribute>
                        <xsl:value-of select="./Value/text()"/>
                      </xsl:element>
                    </xsl:when>
                    <xsl:otherwise>
                      <xsl:element name="prop:has{translate(
                                            substring(./Name/text(),1,1),
                                            'abcdefghijklmnopqrstuvwxyz',
                                            'ABCDEFGHIJKLMNOPQRSTUVWXYZ')}{
                                          substring(./Name/text(),2)}">
                         <xsl:attribute name="rdf:datatype">
                            <xsl:text>
                              http://www.w3.org/2001/XMLSchema#string
                            </xsl:text>
                         </xsl:attribute>
                        <xsl:value-of select="./Value/text()"/>
                      </xsl:element>
                    </xsl:otherwise>
                  </xsl:choose>
                </xsl:for-each>
              </rdf:Description>
            </xsl:for-each>
            </rdf:RDF>
          </xsl:template>
       </xsl:stylesheet>

**Parent topic:** Semantic Indexing for Documents
