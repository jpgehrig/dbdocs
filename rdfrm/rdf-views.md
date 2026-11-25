## 10  RDF Views: Relational Data as RDF

You can create and use RDF views over relational data in RDF Semantic Graph.

Relational data is viewed as virtual RDF triples using one of the two forms of RDB2RDF mapping described in W3C documents on Direct Mapping and R2RML mapping:

- R2RML: RDB to RDF Mapping Language, W3C Recommendation ([`http://www.w3.org/TR/r2rml/`](http://www.w3.org/TR/r2rml/))

- A Direct Mapping of Relational Data to RDF, W3C Recommendation ([`http://www.w3.org/TR/rdb-direct-mapping/`](http://www.w3.org/TR/rdb-direct-mapping/))

This chapter explains the following topics:

- Why Use RDF Views on Relational Data?
  Using RDF views on relational data enables you to query relational data using SPARQL and integrate data available from different sources.
- API Support for RDF Views
  Subprograms are included in the SEM_APIS package for creating, dropping, and exporting (that is, materializing the content of) RDF views.
- Example: Using an RDF View Model with Direct Mapping
  This section shows an example of using an RDF view model with direct mapping.
- Combining Native RDF Data with Virtual RDB2RDF Data
  You can combine native triple data with virtual RDB2RDF triple data (from an RDF view model) in a single SEM_MATCH query by means of the SERVICE keyword.

**Parent topic:** [Conceptual and Usage Information](part-concept-usage.md)

### 10.1 Why Use RDF Views on Relational Data?

Using RDF views on relational data enables you to query relational data using SPARQL and integrate data available from different sources.

You can exploit the advantages of relational data without the need for physical storage of the RDF triples that correspond to the relational data.

The simplest way to create a mapping of relational data to RDF data is by calling the [SEM_APIS.CREATE_RDFVIEW_MODEL](SEM_APIS-reference.md) procedure to create an RDF view model, supplying the list of tables or views whose content you would like to be viewed as RDF. This provides a direct mapping of those relational tables or views.

To get a more customized mapping, you can call the [SEM_APIS.CREATE_RDFVIEW_MODEL](SEM_APIS-reference.md) procedure to create an RDF view model, supplying the R2RML mapping (using Turtle or N-Triple syntax) with the `r2rml_string` parameter.

**Parent topic:** RDF Views: Relational Data as RDF

### 10.2 API Support for RDF Views

Subprograms are included in the SEM_APIS package for creating, dropping, and exporting (that is, materializing the content of) RDF views.

An RDF view model is created as an RDF model, but the RDF model physically contains only the mapping metadata. The actual data remains in the relational tables for which the RDF view model has been created. (The SEM_APIS subprograms are documented in [SEM_APIS Package Subprograms](SEM_APIS-reference.md).)

Once an RDF view model is created, you can also materialize the RDF triples into a staging table by using the [SEM_APIS.EXPORT_RDFVIEW_MODEL](SEM_APIS-reference.md) subprogram.

For the examples throughout this chapter, assume that the relational tables, `EMP` and `DEPT`, are present in the `TESTUSER` schema (see Section 10.3 for the definitions of these two tables). Also, assume that a schema-private network, named NET1 and owned by the RDFUSER schema, already exists and RDFUSER has READ privilege on these two tables.

For the example illustrating the use of exporting of RDF triples, assume that the staging table to which the materialized RDF triples will be stored are owned by `TESTUSER` and the network owner has `INSERT` privilege on that table.

- Creating an RDF View Model with Direct Mapping
- Creating an RDF View Model with R2RML Mapping
- Dropping an RDF View Model
- Exporting Virtual Content of an RDF View Model into a Staging Table

**Parent topic:** RDF Views: Relational Data as RDF

#### 10.2.1 Creating an RDF View Model with Direct Mapping

Example 10-1 creates an RDF view model using direct mapping of two tables, EMP and DEPT (see Section 10.3 for the definitions of these two tables), with a base prefix of `http://empdb/` in a schema-private network. The (virtual) RDF terms are generated according to [A Direct Mapping of Relational Data to RDF](https://www.w3.org/TR/rdb-direct-mapping/), W3C Recommendation.

Example 10-1 Creating an RDF View Model with Direct Mapping in a Schema-Private Network

    BEGIN
      sem_apis.create_rdfview_model(
        model_name => 'empdb_model',
        tables => SYS.ODCIVarchar2List('"TESTUSER"."EMP"', '"TESTUSER"."DEPT"'),
        prefix => 'http://empdb/',
        options => 'KEY_BASED_REF_PROPERTY=T',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );
    END;
    /

To see the properties that are generated, enter the following query:

    SELECT p
      FROM TABLE(SEM_MATCH(
        'SELECT DISTINCT ?p {?s ?p ?o} ORDER BY ?p',
        SEM_Models('empdb_model'),
        NULL, NULL, NULL, NULL,
        NULL, NULL, NULL,
       'RDFUSER', 'NET1'));
    P
    --------------------------------------------------------------------------------
    http://empdb/TESTUSER.EMP#EMPNO
    http://empdb/TESTUSER.EMP#JOB
    http://empdb/TESTUSER.EMP#ENAME
    http://empdb/TESTUSER.EMP#DEPTNO
    http://www.w3.org/1999/02/22-rdf-syntax-ns#type
    http://empdb/TESTUSER.EMP#ref-DEPTNO
    http://empdb/TESTUSER.DEPT#DEPTNO
    http://empdb/TESTUSER.DEPT#DNAME
    http://empdb/TESTUSER.DEPT#LOC

    9 rows selected.

**Parent topic:** API Support for RDF Views

#### 10.2.2 Creating an RDF View Model with R2RML Mapping

You can create an RDF view model using the two tables EMP and DEPT, but with your own customizations, by creating an R2RML mapping document specified using Turtle, as shown:

    @prefix rr: <http://www.w3.org/ns/r2rml#>.
    @prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
    @prefix ex: <http://example.com/ns#>.

    ex:TriplesMap_Dept
        rr:logicalTable [ rr:tableName "TESTUSER.DEPT" ];
        rr:subjectMap [
            rr:template "http://data.example.com/department/{DEPTNO}";
            rr:class ex:Department;
        ];
        rr:predicateObjectMap [
            rr:predicate ex:deptNum;
            rr:objectMap [ rr:column "DEPTNO" ; rr:datatype xsd:integer ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:deptName;
            rr:objectMap [ rr:column "DNAME" ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:deptLocation;
            rr:objectMap [ rr:column "LOC" ];
        ].

    ex:TriplesMap_Emp
        rr:logicalTable [ rr:tableName "TESTUSER.EMP" ];
        rr:subjectMap [
            rr:template "http://data.example.com/employee/{EMPNO}";
            rr:class ex:Employee;
        ];
        rr:predicateObjectMap [
            rr:predicate ex:empNum;
            rr:objectMap [ rr:column "EMPNO" ; rr:datatype xsd:integer ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:empName;
            rr:objectMap [ rr:column "ENAME" ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:jobType;
            rr:objectMap [ rr:column "JOB" ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:worksForDeptNum;
            rr:objectMap [ rr:column "DEPTNO" ; rr:dataType xsd:integer ];
        ];
        rr:predicateObjectMap [
            rr:predicate ex:worksForDept;
            rr:objectMap [
              rr:parentTriplesMap ex:TriplesMap_Dept ;
              rr:joinCondition [ rr:child "DEPTNO"; rr:parent "DEPTNO" ]]].

Example 10-2 Creating an RDF View Model with an R2RML Mapping String

The following example creates an RDF view model directly from an R2RML string, using the preceding R2RML mapping:

    DECLARE
      r2rmlStr CLOB;

    BEGIN

      r2rmlStr :=
       '@prefix rr: <http://www.w3.org/ns/r2rml#>. '||
       '@prefix xsd: <http://www.w3.org/2001/XMLSchema#>. '||
       '@prefix ex: <http://example.com/ns#>. '||'

        ex:TriplesMap_Dept
            rr:logicalTable [ rr:tableName "TESTUSER.DEPT" ];
            rr:subjectMap [
                rr:template "http://data.example.com/department/{DEPTNO}";
                rr:class ex:Department;
            ];
            rr:predicateObjectMap [
                rr:predicate ex:deptNum;
                rr:objectMap [ rr:column "DEPTNO" ; rr:datatype xsd:integer ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:deptName;
                rr:objectMap [ rr:column "DNAME" ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:deptLocation;
                rr:objectMap [ rr:column "LOC" ];
            ].'||'

        ex:TriplesMap_Emp
            rr:logicalTable [ rr:tableName "TESTUSER.EMP" ];
            rr:subjectMap [
                rr:template "http://data.example.com/employee/{EMPNO}";
                rr:class ex:Employee;
            ];
            rr:predicateObjectMap [
                rr:predicate ex:empNum;
                rr:objectMap [ rr:column "EMPNO" ; rr:datatype xsd:integer ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:empName;
                rr:objectMap [ rr:column "ENAME" ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:jobType;
                rr:objectMap [ rr:column "JOB" ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:worksForDeptNum;
                rr:objectMap [ rr:column "DEPTNO" ; rr:dataType xsd:integer ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:worksForDept;
                rr:objectMap [
                  rr:parentTriplesMap ex:TriplesMap_Dept ;
                  rr:joinCondition [ rr:child "DEPTNO"; rr:parent "DEPTNO" ]]].';

      sem_apis.create_rdfview_model(
        model_name => 'empdb_model',
        tables => NULL,
        r2rml_string => r2rmlStr,
        r2rml_string_fmt => 'TURTLE',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );

    END;
    /

**Parent topic:** API Support for RDF Views

#### 10.2.3 Dropping an RDF View Model

An RDF view model can be dropped using the [SEM_APIS.DROP_RDFVIEW_MODEL](SEM_APIS-reference.md) procedure, as shown in Example 10-3.

Example 10-3 Dropping an RDF View Model

    BEGIN
      sem_apis.drop_rdfview_model(
        model_name => 'empdb_model',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );
    END;
    /

**Parent topic:** API Support for RDF Views

#### 10.2.4 Exporting Virtual Content of an RDF View Model into a Staging Table

The content of an RDF view model is virtual; that is, the RDF triples corresponding to the underlying relational data, as mapped by direct mapping or R2RML mapping, are not materialized and stored anywhere. The [SEM_APIS.EXPORT_RDFVIEW_MODEL](SEM_APIS-reference.md) subprogram lets you materialize the virtual RDF triples of an RDF view model into a staging table. The staging table can then be used for loading into an RDF model.

Example 10-4 Exporting an RDF View Model in a Schema-Private Network

Example 10-4 materializes (in N-Triples format) the content of RDF view `empdb_model` into the staging table `TESTUSER.R2RTAB`.

    BEGIN
      sem_apis.export_rdfview_model(
        model_name => 'empdb_model',
        rdf_table_owner => 'TESTUSER',
        rdf_table_name => 'R2RTAB',
        network_owner => 'RDFUSER',
        network_name => 'NET1'
      );
    END;
    PL/SQL procedure successfully completed.

**Parent topic:** API Support for RDF Views

### 10.3 Example: Using an RDF View Model with Direct Mapping

This section shows an example of using an RDF view model with direct mapping.

Perform the following steps for creating and using an RDF view model with direct mapping.

1.  Create two relational tables, `EMP` and `DEPT`, in the `TESTUSER` schema and grant `READ` privilege on these two tables to `RDFUSER`.

        -- Use the following relational tables.
        CREATE TABLE TESTUSER.dept (
          deptno NUMBER CONSTRAINT pk_DeptTab_deptno PRIMARY KEY,
          dname VARCHAR2(30),
          loc VARCHAR2(30)
        );

        CREATE TABLE TESTUSER.emp (
          empno NUMBER PRIMARY KEY,
          ename VARCHAR2(30),
          job VARCHAR2(20),
          deptno NUMBER REFERENCES dept (deptno)
        );

        GRANT READ ON TESTUSER.dept TO RDFUSER;

        GRANT READ ON TESTUSER.emp TO RDFUSER;

2.  Insert data into the tables.

        -- Insert some data.

        INSERT INTO TESTUSER.dept (deptno, dname, loc)
          VALUES (1, 'Sales', 'Boston');
        INSERT INTO TESTUSER.dept (deptno, dname, loc)
          VALUES (2, 'Manufacturing', 'Chicago');
        INSERT INTO TESTUSER.dept (deptno, dname, loc)
          VALUES (3, 'Marketing', 'Boston');

        INSERT INTO TESTUSER.emp (empno, ename, job, deptno)
          VALUES (1, 'Alvarez', 'SalesRep', 1);
        INSERT INTO TESTUSER.emp (empno, ename, job, deptno)
          VALUES (2, 'Baxter', 'Supervisor', 2);
        INSERT INTO TESTUSER.emp (empno, ename, job, deptno)
          VALUES (3, 'Chen', 'Writer', 3);
        INSERT INTO TESTUSER.emp (empno, ename, job, deptno)
          VALUES (4, 'Davis', 'Technician', 2);

3.  Connect as `RDFUSER` and create an RDF view model, `empdb_model`, using direct mapping of the two tables created and populated in the preceding steps.

        -- Create an RDF view model using direct mapping of two tables, EMP and DEPT,
        -- with a base prefix of http://empdb/.
        -- Specify KEY_BASED_REF_PROPERTY=T for the options parameter.

        BEGIN
          sem_apis.create_rdfview_model(
            model_name => 'empdb_model',
            tables => SYS.ODCIVarchar2List('"TESTUSER"."EMP"', '"TESTUSER"."DEPT"'),
            prefix => 'http://empdb/',
            options => 'KEY_BASED_REF_PROPERTY=T'
            network_owner=>'RDFUSER',
            network_name=>'NET1'
          );
        END;
        /

4.  Query the newly created RDF view model using a SEM_MATCH-based SQL query.

        SELECT emp
          FROM TABLE(SEM_MATCH(
            'PREFIX dept: <http://empdb/TESTUSER.DEPT#>
             PREFIX emp: <http://empdb/TESTUSER.EMP#>
             SELECT ?emp {?emp emp:ref-DEPTNO ?dept . ?dept dept:LOC "Boston"}',
            SEM_Models('empdb_model'),
            NULL,
            NULL,
            NULL, NULL,NULL, NULL,NULL, 'RDFUSER', 'NET1'));

        EMP
        --------------------------------------------------------------------------------
        http://empdb/TESTUSER.EMP/EMPNO=1
        http://empdb/TESTUSER.EMP/EMPNO=3

    The query shown in this step is functionally comparable to:

        SQL> SELECT e.empno FROM emp e, dept d WHERE e.deptno = d.deptno AND d.loc = 'Boston';

             EMPNO
        ----------
                 1
                 3

**Parent topic:** RDF Views: Relational Data as RDF

### 10.4 Combining Native RDF Data with Virtual RDB2RDF Data

You can combine native triple data with virtual RDB2RDF triple data (from an RDF view model) in a single SEM_MATCH query by means of the SERVICE keyword.

The SERVICE keyword (explained in [Graph Patterns: Support for SPARQL 1.1 Federated Query](rdf-semantic-graph-overview.md)) is overloaded through the use of special SERVICE URLs that signify local (virtual) RDF data. The following prefixes are used to denote special SERVICE URLs:

- Native models - `oram`: \<http://xmlns.oracle.com/models/\>

- Native virtual models - `oravm`: \<http://xmlns.oracle.com/virtual_models/\>

- RDB2RDF models - `orardbm`: \<http://xmlns.oracle.com/rdb_models/\>

Example 10-5 Querying Multiple Data Sets

Example 10-5 queries multiple data sets. In this query, the first triple pattern `{ ?x rdf:type :Person }` will go against native model `m1` as usual, but `{ ?x :name ?name }` will go against the local native model `m2`, and {` ?x emp:JOB ?job }` will go against the local RDB2RDF model `empdb_model`.

    SELECT * FROM TABLE (SEM_MATCH(
    'PREFIX    : <http://people.org/>
     PREFIX emp: <http://empdb/TESTUSER.EMP#>
     SELECT ?x ?name ?job
     WHERE {
       ?x rdf:type :Person .
       OPTIONAL { SERVICE oram:m2 { ?x :name ?name } }
       OPTIONAL { SERVICE orardbm:empdb_model { ?x emp:JOB ?job } }
     }',
     SEM_MODELS('m1'), NULL, NULL, NULL, NULL, ' ', NULL, NULL, 'RDFUSER', 'NET1'));

Overloaded SERVICE use is only allowed with a single model specified in the `models` argument of SEM_MATCH. Overloaded SERVICE queries do not allow multiple models or a rulebase as input. A virtual model that contains multiple models and/or entailments should be used instead for such combinations. In addition, the `index_status` argument for SEM_MATCH will only check the entailment contained in the virtual model passed as input in the models parameter. This means the status of entailments that are referenced in overloaded SERVICE calls will not be checked.

Example 10-6 queries two data sets: the `empdb_model` from Example: Using an RDF View Model with Direct Mapping and a native model named `people`.

Example 10-6 Querying Virtual RDB2RDF Data and Native RDF Data in a Schema-Private Network

    -- Create native model people --
     EXECUTE SEM_APIS.CREATE_SEM_MODEL('people', NULL, NULL, network_owner=>'rdfuser', network_name=>'net1');

    BEGIN
      sem_apis.update_model('people',
       'PREFIX peop: <http://people.org/>
        INSERT DATA {
           <http://empdb/TESTUSER.EMP/EMPNO=1> peop:age 35 .
           <http://empdb/TESTUSER.EMP/EMPNO=2> peop:age 39 .
           <http://empdb/TESTUSER.EMP/EMPNO=3> peop:age 30 .
           <http://empdb/TESTUSER.EMP/EMPNO=4> peop:age 42 .
        } ');
    END;
    /
    COMMIT;

    -- Querying multiple datasets --
    SELECT emp, age
      FROM TABLE(SEM_MATCH(
        'PREFIX dept: <http://empdb/TESTUSER.DEPT#>
         PREFIX emp: <http://empdb/TESTUSER.EMP#>
         PREFIX peop: <http://people.org/>
         SELECT ?emp ?age WHERE {
           ?emp peop:age ?age
           SERVICE orardbm:empdb_model { ?emp emp:ref-DEPTNO ?dept . ?dept dept:LOC "Boston" }
        }',
        SEM_Models('people'),
        NULL,
        NULL,
        NULL, NULL, NULL, NULL, NULL, 'RDFUSER', 'NET1'));

The query produces the following output:

    EMP                                                AGE
    -------------------------------------------------- --------------------------------------------------
    http://empdb/TESTUSER.EMP/EMPNO=1                   35
    http://empdb/TESTUSER.EMP/EMPNO=3                   30

- Nested Loop Pushdown with Overloaded Service

**Parent topic:** RDF Views: Relational Data as RDF

#### 10.4.1 Nested Loop Pushdown with Overloaded Service

Using a nested loop service can improve performance is some scenarios. Consider the following example queries against multiple data sets for a schema-private network. The query finds the properties of all the departments with people who are 35 years old.

    –- Query example for a schema-private network.

    SELECT emp, dept, p, o
      FROM TABLE(SEM_MATCH(
        'PREFIX dept: <http://empdb/TESTUSER.DEPT#>
         PREFIX emp: <http://empdb/TESTUSER.EMP#>
         PREFIX peop: <http://people.org/>
         SELECT * WHERE{
           ?emp peop:age 35
           SERVICE orardbm:empdb_model{ ?emp emp:ref-DEPTNO ?dept . ?dept ?p ?o }
         }',
         SEM_Models('people'),
         NULL,
         NULL,
         NULL, NULL, NULL, NULL, NULL, 'RDFUSER', 'NET1'));

The preceding query produces the following output:

    EMP                                DEPT                                P                                                 O
    ---------------------------------- ----------------------------------- ------------------------------------------------  --------------------------
    http://empdb/TESTUSER.EMP/EMPNO=1   http://empdb/TESTUSER.DEPT/DEPTNO=1  http://empdb/TESTUSER.DEPT#DEPTNO                1
    http://empdb/TESTUSER.EMP/EMPNO=1   http://empdb/TESTUSER.DEPT/DEPTNO=1  http://empdb/TESTUSER.DEPT#DNAME                 Sales
    http://empdb/TESTUSER.EMP/EMPNO=1   http://empdb/TESTUSER.DEPT/DEPTNO=1  http://empdb/TESTUSER.DEPT#LOC                   Boston
    http://empdb/TESTUSER.EMP/EMPNO=1   http://empdb/TESTUSER.DEPT/DEPTNO=1  http://www.w3.org/1999/02/22-rdf-syntax-ns#type  http://empdb/TESTUSER.DEPT

To get all the results that match for given graph pattern, first the triple pattern `{ ?emp peop:age 35 }` is matched against model `people`, then the triple patterns `{ ?emp emp:ref-DEPTNO ?d . ?d dept:DNAME ?dept }` are matched against model `empdb_model`, and finally the results are joined. Assume that there is only one 35-year-old person in the model `people`, but there are 100,000 triples with information about departments. Obviously, a strategy that retrieves all the results is not the most efficient, and query may have poor performance because a large number of results that need to be processed before being joined with the rest of the query.

An nested-loop service can improve performance in this case. If the hint `OVERLOADED_NL=T` is used, the results of the first part of the query are computed and the SERVICE pattern is executed procedurally in a nested loop once for each `?emp` value from the root triple pattern. The `?emp` subject variable in the SERVICE pattern is replaced with a constant from the root triple pattern in each execution. This effectively pushes the join condition down into the SERVICE clause.

The following example shows the use of the `OVERLOADED_NL=T` hint for the preceding query.

    SELECT emp, dept, p, o
      FROM TABLE(SEM_MATCH(
        'PREFIX dept: <http://empdb/TESTUSER.DEPT#>
         PREFIX emp: <http://empdb/TESTUSER.EMP#>
         PREFIX peop: <http://people.org/>
         SELECT * WHERE{
           ?emp peop:age 35
           SERVICE orardbm:empdb_model { ?emp emp:ref-DEPTNO ?dept . ?dept ?p ?o }
         }',
         SEM_Models('people'),
         NULL,
         NULL,
         NULL, NULL,' OVERLOADED_NL=T ', NULL, NULL, 'RDFUSER', 'NET1'));

The hint `OVERLOADED_NL=T` can be specified among SEM_MATCH options or among inline comments for a given SERVICE graph.

**Parent topic:** Combining Native RDF Data with Virtual RDB2RDF Data
