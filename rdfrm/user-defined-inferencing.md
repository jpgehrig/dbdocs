## 9  User-Defined Inferencing and Querying

RDF Semantic Graph extension architectures enable the addition of user-defined capabilities.

**Note:**

If you are using an Autonomous Database instance in a shared deployment, then user-defined inferencing and querying capabilities requires Oracle JVM to be enabled. See [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless to enable Oracle JVM on your Autonomous Database instance.

Effective with Oracle Database 12c Release 1 (12.1):

- The inference extension architecture enables you to add user-defined inferencing to the presupplied inferencing support.

- The query extension architecture enables you to add user-defined functions and aggregates to be used in SPARQL queries, both through the SEM_MATCH table function and through the support for Apache Jena.

**Note:**

The capabilities described in this chapter are intended for advanced users. You are assumed to be familiar with the main concepts and techniques described in [RDF Semantic Graph Overview](rdf-semantic-graph-overview.md) and [OWL Concepts](owl-concepts.md) .

- User-Defined Inferencing
  The RDF Semantic Graph inference extension architecture enables you to add user-defined inferencing to the presupplied inferencing support.
- User-Defined Functions and Aggregates
  The RDF Semantic Graph query extension architecture enables you to add user-defined functions and aggregates to be used in SPARQL queries, both through the SEM_MATCH table function and through the support for Apache Jena.

**Parent topic:** [Conceptual and Usage Information](part-concept-usage.md)

### 9.1 User-Defined Inferencing

The RDF Semantic Graph inference extension architecture enables you to add user-defined inferencing to the presupplied inferencing support.

- Problem Solved and Benefit Provided by User-Defined Inferencing
- API Support for User-Defined Inferencing
- User-Defined Inference Extension Function Examples

**Parent topic:** User-Defined Inferencing and Querying

#### 9.1.1 Problem Solved and Benefit Provided by User-Defined Inferencing

Before Oracle Database 12c Release 1 (12.1), the Oracle Database inference engine provided native support for OWL 2 RL,RDFS, SKOS, SNOMED (core EL), and user-defined rules, which covered a wide range of applications and requirements. However, there was the limitation that no new RDF resources could be created as part of the rules deduction process.

As an example of the capabilities and the limitation before Oracle Database 12c Release 1 (12.1), consider the following straightforward inference rule:

    ?C   rdfs:subClassOf  ?D .
    ?x    rdf:type  ?C  .  ==>  ?x   rdf:type  ?D

The preceding rule says that any instance `x` of a subclass `C` will be an instance of `C`'s superclass, `D`. The consequent part of the rule mentions two variables` ?x` and `?D`. However, these variables must already exist in the antecedents of the rule, which further implies that these RDF resources must already exist in the knowledge base. In other words, for example, you can derive that `John` is a `Student` only if you know that `John` exists as a `GraduateStudent` and if an axiom specifies that the `GraduateStudent` class is a subclass of the `Student` class.

Another example of a limitation is that before Oracle Database 12c Release 1 (12.1), the inference functions did not support combining a person's first name and last name to produce a full name as a new RDF resource in the inference process. Specifically, this requirement can be captured as a rule like the following:

    ?x   :firstName  ?fn
    ?x   :lastName   ?ln  ==>  ?x  :fullName  concatenate(?fn ?ln)

Effective with Oracle Database 12c Release 1 (12.1), the RDF Semantic Graph inference extension architecture opens the inference process so that users can implement their own inference extension functions and integrate them into the native inference process. This architecture:

- Supports rules that require the generation of new RDF resources.

  Examples might include concatenation of strings or other string operations, mathematical calculations, and web service callouts.

- Allows implementation of certain existing rules using customized optimizations.

  Although the native OWL inference engine has optimizations for many rules and these rules work efficiently for a variety of large-scale ontologies, for some new untested ontologies a customized optimization of a particular inference component may work even better. In such a case, you can disable a particular inference component in the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) call and specify a customized inference extension function (using the `inf_ext_user_func_name` parameter) that implements the new optimization.

- Allows the inference engine to be extended with sophisticated inference capabilities.

  Examples might include integrating geospatial reasoning, time interval reasoning, and text analytical functions into the native database inference process.

**Parent topic:** User-Defined Inferencing

#### 9.1.2 API Support for User-Defined Inferencing

The primary application programming interface (API) for user-defined inferencing is the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, specifically the last parameter:

    inf_ext_user_func_name  IN VARCHAR2 DEFAULT NULL

The `inf_ext_user_func_name` parameter, if specified, identifies one or more user-defined inference functions that implement the specialized logic that you want to use.

- User-Defined Inference Function Requirements

**Parent topic:** User-Defined Inferencing

##### 9.1.2.1 User-Defined Inference Function Requirements

Each user-defined inference function that is specified in the `inf_ext_user_func_name` parameter in the call to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure must:

- Have a name that starts with the following string: `SEM_INF_`

- Be created with definer's rights, not invoker's rights. (For an explanation of definer's rights and invoker's rights, see [Oracle Database Security Guide](../dbseg/managing-security-for-definers-rights-and-invokers-rights.md).)

The format of the user-defined inference function must be that shown in the following example for a hypothetical function named `SEM_INF_EXAMPLE`:

    create or replace function sem_inf_example(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      pragma autonomous_transaction;
    begin
      if (action = SDO_SEM_INFERENCE.INF_EXT_ACTION_START) then
        <... preparation work ...>
      end if;
      if (action = SDO_SEM_INFERENCE.INF_EXT_ACTION_RUN) then
        <... actual inference logic ...>
        commit;
      end if;
      if (action = SDO_SEM_INFERENCE.INF_EXT_ACTION_END) then
        <... clean up ...>
      end if;
    return true;  -- succeed
    end;
    /
    grant execute on sem_inf_example to MDSYS;

In the user-defined function format, the `optimization_flag` output parameter can specify one or more Oracle-defined names that are associated with numeric values. You can specify one or more of the following:

- `SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NONE` indicates that the inference engine should not enable any optimizations for the extension function. (This is the default behavior of the inference engine when the `optimization_flag` parameter is not set.)

- `SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_ALL_IDS` indicates that all triples/quads inferred by the extension function use only resource IDs. In other words, the `output_tab` table only contains resource IDs (columns `gid`, `sid`, `pid`, and `oid`) and does not contain any lexical values (columns `g`, `s`, `p`, and `o` are all null). Enabling this optimization flag allows the inference engine to skip resource ID lookups.

- `SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY` indicates that all the triples/quads inferred by the extension function are new and do not already exist in `src_tab_view`. Enabling this optimization flag allows the inference engine to skip checking for duplicates between the `output_tab` table and `src_tab_view`. Note that the `src_tab_view` contains triples/quads from previous rounds of reasoning, including triples/quads inferred from extension functions.

- `SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY` indicates that all the triples/quads inferred by the extension function are unique and do not already exist in the `output_tab` table. Enabling this optimization flag allows the inference engine to skip checking for duplicates within the `output_tab` table (for example, no need to check for the same triple inferred twice by an extension function). Note that the `output_tab` table is empty at the beginning of each round of reasoning for an extension function, so uniqueness of the data must only hold for the current round of reasoning.

- `SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_IGNORE_NULL` indicates that the inference engine should ignore an inferred triple or quad if the subject, predicate, or object resource is null. The inference engine considers a resource null if both of its columns in the `output_tab` table are null (for example, subject is null if the `s` and `sid` columns are both null). Enabling this optimization flag allows the inference engine to skip invalid triples/quads in the `output_tab` table. Note that the inference engine interprets null graph columns (`g` and `gid`) as the default graph.

To specify more than one value for the `optimization_flag` output parameter, use the plus sign (`+`) to concatenate the values. For example:

    optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_ALL_IDS +
                         SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY +
                         SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY;

For more information about using the `optimization_flag` output parameter, see Example 3: Optimizing Performance.

**Parent topic:** API Support for User-Defined Inferencing

#### 9.1.3 User-Defined Inference Extension Function Examples

The following examples demonstrate how to use user-defined inference extension functions to create entailments.

- Example 1: Adding Static Triples, Example 2: Adding Dynamic Triples, and Example 3: Optimizing Performance cover the basics of user-defined inference extensions.

  Example 1: Adding Static Triples and Example 2: Adding Dynamic Triples focus on adding new, inferred triples.

  Example 3: Optimizing Performance focuses on optimizing performance.

- Example 4: Temporal Reasoning (Several Related Examples) and Example 5: Spatial Reasoning demonstrate how to handle special data types efficiently by leveraging native Oracle types and operators.

  Example 4: Temporal Reasoning (Several Related Examples) focuses on the `xsd:dateTime` data type.

  Example 5: Spatial Reasoning focuses on geospatial data types.

- Example 6: Calling a Web Service makes a web service call to the Oracle Geocoder service.

The first three examples assume that the model `EMPLOYEES` exists and contains the following semantic data, displayed in Turtle format:

    :John   :firstName  "John"  ;
            :lastName   "Smith" .

    :Mary   :firstName  "Mary"  ;
            :lastName   "Smith" ;
            :name       "Mary Smith" .

    :Alice  :firstName  "Alice" .

    :Bob    :firstName  "Bob" ;
            :lastName   "Billow" .

For requirements and guidelines for creating user-defined inference extension functions, see API Support for User-Defined Inferencing.

- Example 1: Adding Static Triples
- Example 2: Adding Dynamic Triples
- Example 3: Optimizing Performance
- Example 4: Temporal Reasoning (Several Related Examples)
- Example 5: Spatial Reasoning
- Example 6: Calling a Web Service

**Parent topic:** User-Defined Inferencing

##### 9.1.3.1 Example 1: Adding Static Triples

The most basic method to infer new data in a user-defined inference extension function is adding static data. Static data does not depend on any existing data in a model. This is not a common case for a user-defined inference extension function, but it demonstrates the basics of adding triples to an entailment. Inserting static data is more commonly done during the preparation phase (that is, `action='START'`) to expand on the existing ontology.

The following user-defined inference extension function (`sem_inf_static`) adds three static triples to an entailment:

    -- this user-defined rule adds static triples
    create or replace function sem_inf_static(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      query varchar2(4000);
      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- generic query we use to insert triples
        query :=
          'insert /*+ parallel append */ into ' || output_tab ||
          ' ( s,  p,  o) VALUES ' ||
          ' (:1, :2, :3) ';

        -- execute the query with different values
        execute immediate query using
          '<http://example.org/S1>', '<http://example.org/P2>', '"O1"';

        execute immediate query using
          '<http://example.org/S2>', '<http://example.org/P2>', '"2"^^xsd:int';

        -- duplicate quad
        execute immediate query using
          '<http://example.org/S2>', '<http://example.org/P2>', '"2"^^xsd:int';

        execute immediate query using
          '<http://example.org/S3>', '<http://example.org/P3>', '"3.0"^^xsd:double';

        -- commit our changes
        commit;
      end if;

      -- return true to indicate success
      return true;
    end sem_inf_static;
    /
    show errors;

The `sem_inf_static` function inserts new data by executing a SQL insert query, with `output_tab` as the target table for insertion. The `output_tab` table will only contain triples added by the `sem_inf_static` function during the current call (see the `num_calls` parameter). The inference engine will always call a user-defined inference extension function at least three times, once for each possible value of the action parameter (`'START'`, `'RUN``'`, and `'END'`). Because `sem_inf_static` does not need to perform any preparation or cleanup, the function only adds data during the `RUN` phase. The extension function can be called more than once during the `RUN` phase, depending on the data inferred during the current round of reasoning.

Although the `sem_inf_static` function makes no checks for existing triples (to prevent duplicate triples), the inference engine will not generate duplicate triples in the resulting entailment. The inference engine will filter out duplicates from the `output_tab` table (the data inserted by the extension function) and from the final entailment (the model or models and other inferred data). Setting the appropriate optimization flags (using the `optimization_flag` parameter) will disable this convenience feature and improve performance. (See Example 3: Optimizing Performance for more information about optimization flags.)

Although the table definition for `output_tab` shows a column for graph names, the inference engine will ignore and override all graph names on triples added by extension functions when performing Global Inference (default behavior of [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md)) and Named Graph Global Inference (NGGI). To add triples to specific named graphs in a user-defined extension function, use NGLI (Named Graph Local Inference). During NGLI, all triples must belong to a named graph (that is, the `gid` and `g` columns of `output_tab` cannot both be null).

The MDSYS user must have execute privileges on the `sem_inf_static` function to use the function for reasoning. The following example shows how to grant the appropriate privileges on the `sem_inf_static` function and create an entailment using the function (along with OWLPRIME inference logic):

    -- grant appropriate privileges
    grant execute on sem_inf_static to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'EMPLOYEES_INF'
      , sem_models('EMPLOYEES')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_static'
    );
    end;
    /

The following example displays the newly entailed data:

    -- formatting
    column s format a23;
    column p format a23;
    column o format a23;
    set linesize 100;

    -- show results
    select s, p, o from table(SEM_MATCH(
        'select ?s ?p ?o where { ?s ?p ?o } order by ?s ?p ?o'
      , sem_models('EMPLOYEES')
      , sem_rulebases('OWLPRIME')
      , null, null, null
      , 'INF_ONLY=T'));

The preceding query returns the three unique static triples added by `sem_inf_static`, with no duplicates:

    S                      P                      O
    ---------------------- ---------------------- -----------------------
    http://example.org/S1  http://example.org/P2  O1
    http://example.org/S2  http://example.org/P2  2
    http://example.org/S3  http://example.org/P3  3E0

**Parent topic:** User-Defined Inference Extension Function Examples

##### 9.1.3.2 Example 2: Adding Dynamic Triples

Adding static data is useful, but it is usually done during the preparation (that is, `action='START'`) phase. Adding dynamic data involves looking at existing data in the model and generating new data based on the existing data. This is the most common case for a user-defined inference extension function.

The following user-defined inference extension function (`sem_inf_dynamic`) concatenates the first and last names of employees to create a new triple that represents the full name.

    -- this user-defined rule adds static triples
    create or replace function sem_inf_dynamic(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      firstNamePropertyId number;
      lastNamePropertyId  number;
      fullNamePropertyId  number;

      sqlStmt    varchar2(4000);
      insertStmt varchar2(4000);
      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- retrieve ID of resource that already exists in the data (will
        -- throw exception if resource does not exist). These will improve
        -- performance of our SQL queries.
        firstNamePropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/firstName');
        lastNamePropertyId  := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/lastName');
        fullNamePropertyId  := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/name');

        -- SQL query to find all employees and their first and last names
        sqlStmt :=
          'select ids1.sid employeeId,
                  values1.value_name firstName,
                  values2.value_name lastName
           from   ' || resource_id_map_view || ' values1,
                  ' || resource_id_map_view || ' values2,
                  ' || src_tab_view || '         ids1,
                  ' || src_tab_view || '         ids2
           where  ids1.sid = ids2.sid
             AND  ids1.pid = ' || to_char(firstNamePropertyId,'TM9') || '
             AND  ids2.pid = ' || to_char(lastNamePropertyId,'TM9')  || '
             AND  ids1.oid = values1.value_id
             AND  ids2.oid = values2.value_id
           /* below ensures we have NEWDATA (a no duplicate optimization flag) */
             AND  not exists
                   (select 1
                    from   ' || src_tab_view || '
                    where  sid = ids1.sid AND
                           pid = ' || to_char(fullNamePropertyId,'TM9') || ')';

        -- create the insert statement that concatenates the first and
        -- last names from our sqlStmt into a new triple.
        insertStmt :=
          'insert /*+ parallel append */
           into ' || output_tab || ' (sid, pid, o)
           select employeeId, ' || to_char(fullNamePropertyId,'TM9') || ', ''"'' || firstName || '' '' || lastName ||  ''"''
           from   (' || sqlStmt || ')';

        -- execute the insert statement
        execute immediate insertStmt;

        -- commit our changes
        commit;

        -- set our optimization flags indicating we already checked for
        -- duplicates in the model (src_tab_view)
        optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY;
      end if;

      -- return true to indicate success
      return true;
    end sem_inf_dynamic;
    /
    show errors;

The `sem_inf_dynamic` function inserts new data using two main steps. First, the function builds a SQL query that collects all first and last names from the existing data. The `sqlStmt` variable stores this SQL query. Next, the function inserts new triples based on the first and last names it collects, to form a full name for each employee. The `insertStmt` variable stores this SQL query. Note that the `insertStmt` query includes the `sqlStmt` query because it is performing an INSERT with a subquery.

The `sqlStmt` query performs a join across two main views: the resource view (`resource_id_map_view`) and the existing data view (`src_tab_view`). The existing data view contains all existing triples but stores the values of those triples using numeric IDs instead of lexical values. Because the `sqlStmt` query must extract the lexical values of the first and last names of an employee, it joins with the resource view twice (once for the first name and once for the last name).

The `sqlStmt` query contains the `PARALLEL` SQL hint to help improve performance. Parallel execution on a balanced hardware configuration can significantly improve performance. (See Example 3: Optimizing Performance for more information.)

The `insertStmt` query also performs a duplicate check to avoid adding a triple if it already exists in the existing data view (`src_tab_view`). The function indicates it has performed this check by enabling the `INF_EXT_OPT_FLAG_NEWDATA_ONLY` optimization flag. Doing the check inside the extension function improves overall performance of the reasoning. Note that the existing data view does not contain the new triples currently being added by the `sem_inf_dynamic` function, so duplicates may still exist within the `output_tab` table. If the `sem_inf_dynamic` function additionally checked for duplicates within the output_tab table, then it could also enable the `INF_EXT_OPT_FLAG_UNIQUEDATA_ONLY` optimization flag.

Both SQL queries use numeric IDs of RDF resources to perform their joins and inserts. Using IDs instead of lexical values improves the performance of the queries. The `sem_inf_dynamic` function takes advantage of this performance benefit by looking up the IDs of the lexical values it plans to use. In this case, the function looks up three URIs representing the first name, last name, and full name properties. If the `sem_inf_dynamic` function inserted all new triples purely as IDs, then it could enable the `INF_EXT_OPT_FLAG_ALL_IDS` optimization flag. For this example, however, the new triples each contain a single, new, lexical value: the full name of the employee.

To create an entailment with the `sem_inf_dynamic` function, grant execution privileges to the MDSYS user, then pass the function name to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, as follows:

    -- grant appropriate privileges
    grant execute on sem_inf_dynamic to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'EMPLOYEES_INF'
      , sem_models('EMPLOYEES')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_dynamic'
    );
    end;
    /

The entailment should contain the following two new triples added by `sem_inf_dynamic`:

    S                        P                        O
    ------------------------ ------------------------ -----------------------
    http://example.org/Bob   http://example.org/name  Bob Billow
    http://example.org/John  http://example.org/name  John Smith

Note that the `sem_inf_dynamic` function in the preceding example did not infer a full name for Mary Smith, because Mary Smith already had their full name specified in the existing data.

**Parent topic:** User-Defined Inference Extension Function Examples

##### 9.1.3.3 Example 3: Optimizing Performance

Several techniques can improve the performance of an inference extension function. One such technique is to use the numeric IDs of resources rather than their lexical values in queries. By only using resource IDs, the extension function avoids having to join with the resource view (`resource_id_map_view`), and this can greatly improve query performance. Inference extension functions can obtain additional performance benefits by also using resource IDs when adding new triples to the `output_tab` table (that is, using only using the `gid`, `sid`, `pid`, and `oid` columns of the `output_tab` table).

The following user-defined inference extension function (`sem_inf_related`) infers a new property, `:possibleRelative`, for employees who share the same last name. The SQL queries for finding such employees use only resource IDs (no lexical values, no joins with the resource view). Additionally, the inference extension function in this example inserts the new triples using only resource IDs, allowing the function to enable the `INF_EXT_OPT_FLAG_ALL_IDS` optimization flag.

    -- this user-defined rule adds static triples
    create or replace function sem_inf_related(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      lastNamePropertyId  number;
      relatedPropertyId   number;

      sqlStmt    varchar2(4000);
      insertStmt varchar2(4000);
      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- retrieve ID of resource that already exists in the data (will
        -- throw exception if resource does not exist).
        lastNamePropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/lastName');

        -- retreive ID of resource or generate a new ID if resource does
        -- not already exist
        relatedPropertyId := sdo_sem_inference.oracle_orardf_add_res('http://example.org/possibleRelative');

        -- SQL query to find all employees that share a last name
        sqlStmt :=
          'select ids1.sid employeeId,
                  ids2.sid relativeId
           from   ' || src_tab_view || '         ids1,
                  ' || src_tab_view || '         ids2
           where  ids1.pid = ' || to_char(lastNamePropertyId,'TM9') || '
             AND  ids2.pid = ' || to_char(lastNamePropertyId,'TM9') || '
             AND  ids1.oid  = ids2.oid
           /* avoid employees related to themselves */
             AND  ids1.sid != ids2.sid
           /* below ensures we have NEWDATA (a no duplicate optimization flag) */
             AND  not exists
                   (select 1
                    from   ' || src_tab_view || '
                    where  sid = ids1.sid
                      AND  pid = ' || to_char(relatedPropertyId,'TM9') || '
                      AND  oid = ids2.sid)
           /* below ensures we have UNIQDATA (a no duplicate optimization flag) */
             AND  not exists
                   (select 1
                    from   ' || output_tab || '
                    where  sid = ids1.sid
                      AND  pid = ' || to_char(relatedPropertyId,'TM9') || '
                      AND  oid = ids2.sid)';

        -- create the insert statement that only uses resource IDs
        insertStmt :=
          'insert /*+ parallel append */
           into ' || output_tab || ' (sid, pid, oid)
           select employeeId, ' || to_char(relatedPropertyId,'TM9') || ', relativeId
           from   (' || sqlStmt || ')';

        -- execute the insert statement
        execute immediate insertStmt;

        -- commit our changes
        commit;

        -- set flag indicating our new triples
        --   1) are specified using only IDs
        --   2) produce no duplicates with the model (src_tab_view)
        --   3) produce no duplicates in the output (output_tab)
        optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_ALL_IDS +
                             SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY +
                             SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY;
      end if;

      -- return true to indicate success
      return true;
    end sem_inf_related;
    /
    show errors;

The `sem_inf_related` function has a few key differences from previous examples. First, the `sem_inf_related` function queries purely with resource IDs and inserts new triples using only resource IDs. Because all the added triples in the `output_tab` table only use resource IDs, the function can enable the `INF_EXT_OPT_FLAG_ALL_IDS` optimization flag. For optimal performance, functions should try to use resource IDs over lexical values. However, sometimes this is not possible, as in Example 2: Adding Dynamic Triples, which concatenates lexical values to form a new lexical value. Note that in cases like Example 2: Adding Dynamic Triples, it is usually better to join with the resource view (`resource_id_map_view`) than to embed calls to `oracle_orardf_res2vid` within the SQL query. This is due to the overhead of calling the function for each possible match as opposed to joining with another table.

Another key difference in the `sem_inf_related` function is the use of the `oracle_orardf_add_res` function (compared to `oracle_orardf_res2vid`). Unlike the `res2vid` function, the `add_res` function will add a resource to the resource view (`resource_id_map_view`) if the resource does not already exist. Inference extensions functions should use the `add_res` function if adding the resource to the resource view is not a concern. Calling the function multiple times will not generate duplicate entries in the resource view.

The last main difference is the additional `NOT EXISTS `clause in the SQL query. The first `NOT EXISTS` clause avoids adding any triples that may be duplicates of triples already in the model or triples inferred by other rules (`src_tab_view`). Checking for these duplicates allows `sem_inf_related` to enable the `INF_EXT_OPT_FLAG_NEWDATA_ONLY` optimization flag. The second `NOT EXISTS` clause avoids adding triples that may be duplicates of triples already added by the `sem_inf_related` function to the output_tab table during the current round of reasoning (see the `num_calls` parameter). Checking for these duplicates allows `sem_inf_related` to enable the `INF_EXT_OPT_FLAG_UNIQDATA_ONLY` optimization flag.

Like the `sem_inf_dynamic` example, `sem_inf_related` example uses a `PARALLEL` SQL query hint in its insert statement. Parallel execution on a balanced hardware configuration can significantly improve performance. For a data-intensive application, a good I/O subsystem is usually a critical component to the performance of the whole system.

To create an entailment with the `sem_inf_dynamic` function, grant execution privileges to the MDSYS user, then pass the function name to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, as follows:

    -- grant appropriate privileges
    grant execute on sem_inf_related to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'EMPLOYEES_INF'
      , sem_models('EMPLOYEES')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_related'
    );
    end;
    /

The entailment should contain the following two new triples added by `sem_inf_related`:

    S                        P                                    O
    ------------------------ ------------------------------------ ------------------------
    http://example.org/John  http://example.org/possibleRelative  http://example.org/Mary
    http://example.org/Mary  http://example.org/possibleRelative  http://example.org/John

**Parent topic:** User-Defined Inference Extension Function Examples

##### 9.1.3.4 Example 4: Temporal Reasoning (Several Related Examples)

User-defined extension functions enable you to better leverage certain data types (like `xsd:dateTime`) in the triples. For example, with user-defined extension functions, it is possible to infer relationships between triples based on the difference between two `xsd:dateTime` values. The three examples in this section explore two different temporal reasoning rules and how to combine them into one entailment. The examples assume the models `EVENT` and `EVENT_ONT` exist and contain the following semantic data:

##### EVENT_ONT

    @prefix owl:  <http://www.w3.org/2002/07/owl#> .
    @prefix rdf:  <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
    @prefix xsd:  <http://www.w3.org/2001/XMLSchema#> .
    @prefix :     <http://example.org/event/> .

    # we model two types of events
    :Meeting      rdfs:subClassOf :Event .
    :Presentation rdfs:subClassOf :Event .

    # events have topics
    :topic        rdfs:domain     :Event .

    # events have start and end times
    :startTime    rdfs:domain     :Event ;
                  rdfs:range      xsd:dateTime .
    :endTime      rdfs:domain     :Event ;
                  rdfs:range      xsd:dateTime .

    # duration (in minutes) of an event
    :lengthInMins rdfs:domain      :Event ;
                  rdfs:range       xsd:integer .

    # overlaps property identifies conflicting events
    :overlaps     rdfs:domain      :Event ;
                  rdf:type         owl:SymmetricProperty .
    :noOverlap    rdfs:domain      :Event ;
                  rdf:type         owl:SymmetricProperty .

##### EVENT_TBOX

    @prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
    @prefix :    <http://example.org/event/> .

    :m1 rdf:type   :Meeting ;
        :topic     "Beta1 launch" ;
        :startTime "2012-04-01T09:30:00-05:00"^^xsd:dateTime ;
        :endTime   "2012-04-01T11:00:00-05:00"^^xsd:dateTime .

    :m2 rdf:type   :Meeting ;
        :topic     "Standards compliance" ;
        :startTime "2012-04-01T12:30:00-05:00"^^xsd:dateTime ;
        :endTime   "2012-04-01T13:30:00-05:00"^^xsd:dateTime .

    :p1 rdf:type   :Presentation ;
        :topic     "OWL Reasoners" ;
        :startTime "2012-04-01T11:00:00-05:00"^^xsd:dateTime ;
        :endTime   "2012-04-01T13:00:00-05:00"^^xsd:dateTime .

The examples are as follow.

- Example 4a: Duration Rule
- Example 4b: Overlap Rule
- Example 4c: Duration and Overlap Rules

**Parent topic:** User-Defined Inference Extension Function Examples

###### 9.1.3.4.1 Example 4a: Duration Rule

The following user-defined inference extension function (`sem_inf_durations`) infers the duration in minutes of events, given the start and end times of an event. For example, an event starting at 9:30 AM and ending at 11:00 AM has duration of 90 minutes. The following extension function extracts the start and end times for each event, converts the `xsd:dateTime` values into Oracle timestamps, then computes the difference between the timestamps. Notice that this extension function can handle time zones.

    create or replace function sem_inf_durations(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      eventClassId        number;
      rdfTypePropertyId   number;
      startTimePropertyId number;
      endTimePropertyId   number;
      durationPropertyId  number;

      xsdTimeFormat       varchar2(100);
      sqlStmt             varchar2(4000);
      insertStmt          varchar2(4000);

      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- retrieve ID of resource that already exists in the data (will
        -- throw exception if resource does not exist).
        eventClassId        := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/Event');
        startTimePropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/startTime');
        endTimePropertyId   := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/endTime');
        durationPropertyId  := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/lengthInMins');
        rdfTypePropertyId   := sdo_sem_inference.oracle_orardf_res2vid('http://www.w3.org/1999/02/22-rdf-syntax-ns#type');

        -- set the TIMESTAMP format we will use to parse XSD times
        xsdTimeFormat := 'YYYY-MM-DD"T"HH24:MI:SSTZH:TZM';

        -- query we use to extract the event ID and start/end times.
        sqlStmt :=
          'select ids1.sid eventId,
                  TO_TIMESTAMP_TZ(values1.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') startTime,
                  TO_TIMESTAMP_TZ(values2.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') endTime
           from   ' || resource_id_map_view || ' values1,
                  ' || resource_id_map_view || ' values2,
                  ' || src_tab_view || '         ids1,
                  ' || src_tab_view || '         ids2,
                  ' || src_tab_view || '         ids3
           where  ids1.sid = ids3.sid
             AND  ids3.pid = ' || to_char(rdfTypePropertyId,'TM9') || '
             AND  ids3.oid = ' || to_char(eventClassId,'TM9')      || '
             AND  ids1.sid = ids2.sid
             AND  ids1.pid = ' || to_char(startTimePropertyId,'TM9') || '
             AND  ids2.pid = ' || to_char(endTimePropertyId,'TM9')   || '
             AND  ids1.oid = values1.value_id
             AND  ids2.oid = values2.value_id
           /* ensures we have NEWDATA */
             AND  not exists
                   (select 1
                    from   ' || src_tab_view || '
                    where  sid = ids3.sid
                      AND  pid = ' || to_char(durationPropertyId,'TM9') || ')
           /* ensures we have UNIQDATA */
             AND  not exists
                   (select 1
                    from   ' || output_tab || '
                    where  sid = ids3.sid
                      AND  pid = ' || to_char(durationPropertyId,'TM9') || ')';

        -- compute the difference (in minutes) between the two Oracle
        -- timestamps from our sqlStmt query.  Store the minutes as
        -- xsd:integer.
        insertStmt :=
          'insert /*+ parallel append */ into ' || output_tab || ' (sid, pid, o)
           select eventId,
                  ' || to_char(durationPropertyId,'TM9') || ',
                  ''"'' || minutes || ''"^^xsd:integer''
           from   (
             select eventId,
                    (extract(day    from (endTime - startTime))*24*60 +
                     extract(hour   from (endTime - startTime))*60 +
                     extract(minute from (endTime - startTime))) minutes
             from   (' || sqlStmt || '))';

        -- execute the query
        execute immediate insertStmt;

        -- commit our changes
        commit;
      end if;

      -- we already checked for duplicates in src_tab_view (NEWDATA) and
      -- in output_tab (UNIQDATA)
      optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY +
                           SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY;

      -- return true to indicate success
      return true;

      -- handle any exceptions
      exception
        when others then
          diag_message := 'error occurred: ' || SQLERRM;
          return false;
    end sem_inf_durations;
    /
    show errors;

The `sem_inf_durations` function leverages built-in Oracle temporal functions to compute the event durations. First, the function converts the `xsd:dateTime` literal value to an Oracle `TIMESTAMP` object using the `TO_TIMESTAMP_TZ` function. Taking the difference between two Oracle `TIMESTAMP` objects produces an `INTERVAL` object that represents a time interval. Using the `EXTRACT` operator, the `sem_inf_durations` function computes the duration of each event in minutes by extracting the days, hours, and minutes out of the duration intervals.

Because the `sem_inf_durations` function checks for duplicates against both data in the existing model (`src_tab_view`) and data in the `output_tab` table, it can enable the `INF_EXT_OPT_FLAG_NEWDATA_ONLY` and `INF_EXT_OPT_FLAG_UNIQDATA_ONLY` optimization flags. (See Example 3: Optimizing Performance for more information about optimization flags.)

Notice that unlike previous examples, `sem_inf_durations` contains an exception handler. Exception handlers are useful for debugging issues in user-defined inference extension functions. To produce useful debugging messages, catch exceptions in the extension function, set the `diag_message` parameter to reflect the error, and return `FALSE` to indicate that an error occurred during execution of the extension function. The `sem_inf_durations` function catches all exceptions and sets the `diag_message` value to the exception message.

To create an entailment with the `sem_inf_durations` function, grant execution privileges to the MDSYS user, then pass the function name to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, as follows:

    -- grant appropriate privileges
    grant execute on sem_inf_durations to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'EVENT_INF'
      , sem_models('EVENT', 'EVENT_ONT')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_durations'
    );
    end;
    /

In addition to the triples inferred by OWLPRIME, the entailment should contain the following three new triples added by `sem_inf_durations`:

    S                            P                                      O
    ---------------------------- -------------------------------------- ---------
    http://example.org/event/m1  http://example.org/event/lengthInMins  90
    http://example.org/event/m2  http://example.org/event/lengthInMins  60
    http://example.org/event/p1  http://example.org/event/lengthInMins  120

**Parent topic:** Example 4: Temporal Reasoning (Several Related Examples)

###### 9.1.3.4.2 Example 4b: Overlap Rule

The following user-defined inference extension function (`sem_inf_overlap`) infers whether two events overlap. Two events overlap if one event starts while the other event is in progress. The function extracts the start and end times for every pair of events, converts the `xsd:dateTime` values into Oracle timestamps, then computes whether one event starts within the other.

    create or replace function sem_inf_overlap(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      eventClassId        number;
      rdfTypePropertyId   number;
      startTimePropertyId number;
      endTimePropertyId   number;
      overlapsPropertyId  number;
      noOverlapPropertyId number;

      xsdTimeFormat       varchar2(100);
      sqlStmt             varchar2(4000);
      insertStmt          varchar2(4000);

      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- retrieve ID of resource that already exists in the data (will
        -- throw exception if resource does not exist).
        eventClassId        := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/Event');
        startTimePropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/startTime');
        endTimePropertyId   := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/endTime');
        overlapsPropertyId  := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/overlaps');
        noOverlapPropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/event/noOverlap');
        rdfTypePropertyId   := sdo_sem_inference.oracle_orardf_res2vid('http://www.w3.org/1999/02/22-rdf-syntax-ns#type');

        -- set the TIMESTAMP format we will use to parse XSD times
        xsdTimeFormat := 'YYYY-MM-DD"T"HH24:MI:SSTZH:TZM';

        -- query we use to extract the event ID and start/end times.
        sqlStmt :=
          'select idsA1.sid eventAId,
                  idsB1.sid eventBId,
                  TO_TIMESTAMP_TZ(valuesA1.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') startTimeA,
                  TO_TIMESTAMP_TZ(valuesA2.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') endTimeA,
                  TO_TIMESTAMP_TZ(valuesB1.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') startTimeB,
                  TO_TIMESTAMP_TZ(valuesB2.value_name,''YYYY-MM-DD"T"HH24:MI:SSTZH:TZM'') endTimeB
           from   ' || resource_id_map_view || ' valuesA1,
                  ' || resource_id_map_view || ' valuesA2,
                  ' || resource_id_map_view || ' valuesB1,
                  ' || resource_id_map_view || ' valuesB2,
                  ' || src_tab_view || '         idsA1,
                  ' || src_tab_view || '         idsA2,
                  ' || src_tab_view || '         idsA3,
                  ' || src_tab_view || '         idsB1,
                  ' || src_tab_view || '         idsB2,
                  ' || src_tab_view || '         idsB3
           where  idsA1.sid = idsA3.sid
             AND  idsA3.pid = ' || to_char(rdfTypePropertyId,'TM9') || '
             AND  idsA3.oid = ' || to_char(eventClassId,'TM9')      || '
             AND  idsB1.sid = idsB3.sid
             AND  idsB3.pid = ' || to_char(rdfTypePropertyId,'TM9') || '
             AND  idsB3.oid = ' || to_char(eventClassId,'TM9')      || '
           /* only do half the checks, our TBOX ontology will handle symmetries */
             AND  idsA1.sid < idsB1.sid
           /* grab values of startTime and endTime for event A */
             AND  idsA1.sid = idsA2.sid
             AND  idsA1.pid = ' || to_char(startTimePropertyId,'TM9') || '
             AND  idsA2.pid = ' || to_char(endTimePropertyId,'TM9')   || '
             AND  idsA1.oid = valuesA1.value_id
             AND  idsA2.oid = valuesA2.value_id
           /* grab values of startTime and endTime for event B */
             AND  idsB1.sid = idsB2.sid
             AND  idsB1.pid = ' || to_char(startTimePropertyId,'TM9') || '
             AND  idsB2.pid = ' || to_char(endTimePropertyId,'TM9')   || '
             AND  idsB1.oid = valuesB1.value_id
             AND  idsB2.oid = valuesB2.value_id
           /* ensures we have NEWDATA */
             AND  not exists
                   (select 1
                    from   ' || src_tab_view || '
                    where  sid = idsA1.sid
                      AND  oid = idsB1.sid
                      AND  pid in (' || to_char(overlapsPropertyId,'TM9')  || ',' ||
                                        to_char(noOverlapPropertyId,'TM9') || '))
           /* ensures we have UNIQDATA */
             AND  not exists
                   (select 1
                    from   ' || output_tab   || '
                    where  sid = idsA1.sid
                      AND  oid = idsB1.sid
                      AND  pid in (' || to_char(overlapsPropertyId,'TM9')  || ',' ||
                                        to_char(noOverlapPropertyId,'TM9') || '))';

        -- compare the two event times
        insertStmt :=
          'insert /*+ parallel append */ into ' || output_tab || ' (sid, pid, oid)
           select eventAId, overlapStatusId, eventBId
           from   (
             select eventAId,
                    (case
                     when (startTimeA < endTimeB and
                           startTimeA > startTimeB) then
                       ' || to_char(overlapsPropertyId,'TM9') || '
                     when (startTimeB < endTimeA and
                           startTimeB > startTimeA) then
                       ' || to_char(overlapsPropertyId,'TM9') || '
                     else
                       ' || to_char(noOverlapPropertyId,'TM9') || '
                     end) overlapStatusId,
                     eventBId
             from   (' || sqlStmt || '))';

        -- execute the query
        execute immediate insertStmt;

        -- commit our changes
        commit;
      end if;

      -- we only use ID values in the output_tab and we check for
      -- duplicates with our NOT EXISTS clause.
      optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_ALL_IDS +
                           SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY +
                           SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY;

      -- return true to indicate success
      return true;

      -- handle any exceptions
      exception
        when others then
          diag_message := 'error occurred: ' || SQLERRM;
          return false;
    end sem_inf_overlap;
    /
    show errors;

The `sem_inf_overlap` function is similar to the `sem_inf_durations` function in Example 4b: Overlap Rule. The main difference between the two is that the query in `sem_inf_overlap` contains more joins and enables the INF_EXT_OPT_FLAG_ALL_IDS optimization flag because it does not need to generate new lexical values. (See Example 3: Optimizing Performance for more information about optimization flags.)

To create an entailment with the `sem_inf_overlap` function, grant execution privileges to the MDSYS user, then pass the function name to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, as follows:

    -- grant appropriate privileges
    grant execute on sem_inf_overlap to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'EVENT_INF'
      , sem_models('EVENT', 'EVENT_ONT')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_overlap'
    );
    end;
    /

In addition to the triples inferred by OWLPRIME, the entailment should contain the following six new triples added by `sem_inf_overlap`:

    S                            P                                   O
    ---------------------------- ----------------------------------- ----------------------------
    http://example.org/event/m1  http://example.org/event/noOverlap  http://example.org/event/m2
    http://example.org/event/m1  http://example.org/event/noOverlap  http://example.org/event/p1
    http://example.org/event/m2  http://example.org/event/noOverlap  http://example.org/event/m1
    http://example.org/event/m2  http://example.org/event/overlaps   http://example.org/event/p1
    http://example.org/event/p1  http://example.org/event/noOverlap  http://example.org/event/m1
    http://example.org/event/p1  http://example.org/event/overlaps   http://example.org/event/m2

**Parent topic:** Example 4: Temporal Reasoning (Several Related Examples)

###### 9.1.3.4.3 Example 4c: Duration and Overlap Rules

The example in this section uses the extension functions from Example 4a: Duration Rule (`sem_inf_durations`) and Example 4b: Overlap Rule (`sem_inf_overlap`) together to produce a single entailment. The extension functions are left unmodified for this example.

To create an entailment using multiple extension functions, use a comma to separate each extension function passed to the `inf_ext_user_func_name` parameter of [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md). The following example assumes that the MDSYS user has already been granted the appropriate privileges on the extension functions.

    -- use multiple user-defined inference functions
    begin
      sem_apis.create_entailment(
        'EVENT_INF'
      , sem_models('EVENT', 'EVENT_ONT')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_durations,sem_inf_overlap'
    );
    end;
    /

In addition to the triples inferred by OWLPRIME, the entailment should contain the following nine new triples added by `sem_inf_durations` and `sem_inf_overlap`:

    S                            P                                      O
    ---------------------------- -------------------------------------- ----------------------------
    http://example.org/event/m1  http://example.org/event/lengthInMins  90
    http://example.org/event/m1  http://example.org/event/noOverlap     http://example.org/event/m2
    http://example.org/event/m1  http://example.org/event/noOverlap     http://example.org/event/p1
    http://example.org/event/m2  http://example.org/event/lengthInMins  60
    http://example.org/event/m2  http://example.org/event/noOverlap     http://example.org/event/m1
    http://example.org/event/m2  http://example.org/event/overlaps      http://example.org/event/p1
    http://example.org/event/p1  http://example.org/event/lengthInMins  120
    http://example.org/event/p1  http://example.org/event/noOverlap     http://example.org/event/m1
    http://example.org/event/p1  http://example.org/event/overlaps      http://example.org/event/m2

Notice that the extension functions, `sem_inf_durations` and `sem_inf_overlap`, did not need to use the same optimization flags. It is possible to use extension functions with contradictory optimization flags (for example, one function using `INF_EXT_OPT_FLAG_ALL_IDS` and another function inserting all new triples as lexical values).

**Parent topic:** Example 4: Temporal Reasoning (Several Related Examples)

##### 9.1.3.5 Example 5: Spatial Reasoning

User-defined inference extension functions can also leverage geospatial data types, like WKT (well-known text), to perform spatial reasoning. For example, with user-defined extension functions, it is possible to infer a "contains" relationship between geometric entities, such as states and cities.

The example in this section demonstrates how to infer whether a geometry (a US state) contains a point (a US city). This example assumes the RDF network already has a spatial index (described in section 1.6.6.2). This example also assumes the model `STATES` exists and contains the following semantic data:

    @prefix orageo: <http://xmlns.oracle.com/rdf/geo/> .
    @prefix rdf:    <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix rdfs:   <http://www.w3.org/2000/01/rdf-schema#> .
    @prefix :       <http://example.org/geo/> .

    :Colorado rdf:type  :State ;
              :boundary "Polygon((-109.0448 37.0004, -102.0424 36.9949, -102.0534 41.0006, -109.0489 40.9996, -109.0448 37.0004))"^^orageo:WKTLiteral .
    :Utah     rdf:type  :State ;
              :boundary "Polygon((-114.0491 36.9982, -109.0462 37.0026, -109.0503 40.9986, -111.0471 41.0006, -111.0498 41.9993, -114.0395 41.9901, -114.0491 36.9982))"^^orageo:WKTLiteral .
    :Wyoming  rdf:type  :State ;
              :boundary "Polygon((-104.0556 41.0037, -104.0584 44.9949, -111.0539 44.9998, -111.0457 40.9986, -104.0556 41.0037))"^^orageo:WKTLiteral

    :StateCapital rdfs:subClassOf :City ;

    :Denver   rdf:type  :StateCapital ;
              :location "Point(-104.984722 39.739167)"^^orageo:WKTLiteral .
    :SaltLake rdf:type  :StateCaptial ;
              :location "Point(-111.883333 40.75)"^^orageo:WKTLiteral .
    :Cheyenne rdf:type  :StateCapital ;
              :location "Point(-104.801944 41.145556)"^^orageo:WKTLiteral .

The following user-defined inference extension function (`sem_inf_capitals`) searches for capital cities within each state using the WKT geometries. If the function finds a capital city, it infers the city is the capital of the state containing it.

    create or replace function sem_inf_capitals(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      stateClassId        number;
      capitalClassId      number;

      boundaryPropertyId  number;
      locationPropertyId  number;
      rdfTypePropertyId   number;
      capitalPropertyId   number;

      defaultSRID         number := 8307;

      xsdTimeFormat       varchar2(100);
      sqlStmt             varchar2(4000);
      insertStmt          varchar2(4000);

      pragma autonomous_transaction;
    begin
      if (action = 'RUN') then
        -- retrieve ID of resource that already exists in the data (will
        -- throw exception if resource does not exist).
        stateClassId       := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/geo/State');
        capitalClassId     := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/geo/StateCapital');
        boundaryPropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/geo/boundary');
        locationPropertyId := sdo_sem_inference.oracle_orardf_res2vid('http://example.org/geo/location');
        rdfTypePropertyId  := sdo_sem_inference.oracle_orardf_res2vid('http://www.w3.org/1999/02/22-rdf-syntax-ns#type');

        -- retreive ID of resource or generate a new ID if resource does
        -- not already exist
        capitalPropertyId := sdo_sem_inference.oracle_orardf_add_res('http://example.org/geo/capital');

        -- query we use to extract the capital cities contained within state boundaries
        sqlStmt :=
          'select idsA1.sid stateId,
                  idsB1.sid cityId
           from   ' || resource_id_map_view || ' valuesA,
                  ' || resource_id_map_view || ' valuesB,
                  ' || src_tab_view || '         idsA1,
                  ' || src_tab_view || '         idsA2,
                  ' || src_tab_view || '         idsB1,
                  ' || src_tab_view || '         idsB2
           where  idsA1.pid = ' || to_char(rdfTypePropertyId,'TM9') || '
             AND  idsA1.oid = ' || to_char(stateClassId,'TM9')      || '
             AND  idsB1.pid = ' || to_char(rdfTypePropertyId,'TM9') || '
             AND  idsB1.oid = ' || to_char(capitalClassId,'TM9')    || '
           /* grab geometric lexical values */
             AND  idsA2.sid = idsA1.sid
             AND  idsA2.pid = ' || to_char(boundaryPropertyId,'TM9')|| '
             AND  idsA2.oid = valuesA.value_id
             AND  idsB2.sid = idsB1.sid
             AND  idsB2.pid = ' || to_char(locationPropertyId,'TM9')|| '
             AND  idsB2.oid = valuesB.value_id
           /* compare geometries to see if city is contained by state */
             AND  SDO_RELATE(
                    SDO_RDF.getV$GeometryVal(
                      valuesA.value_type,
                      valuesA.vname_prefix,
                      valuesA.vname_suffix,
                      valuesA.literal_type,
                      valuesA.language_type,
                      valuesA.long_value,
                      ' || to_char(defaultSRID,'TM9') || '),
                    SDO_RDF.getV$GeometryVal(
                      valuesB.value_type,
                      valuesB.vname_prefix,
                      valuesB.vname_suffix,
                      valuesB.literal_type,
                      valuesB.language_type,
                      valuesB.long_value,
                      ' || to_char(defaultSRID,'TM9') || '),
                    ''mask=CONTAINS'') = ''TRUE''
           /* ensures we have NEWDATA and only check capitals not assigned to a state */
             AND  not exists
                   (select 1
                    from   ' || src_tab_view || '
                    where  pid = ' || to_char(capitalPropertyId,'TM9') || '
                      AND  (sid = idsA1.sid OR oid = idsB1.sid))
           /* ensures we have UNIQDATA and only check capitals not assigned to a state */
             AND  not exists
                   (select 1
                    from   ' || output_tab   || '
                    where  pid = ' || to_char(capitalPropertyId,'TM9') || '
                      AND  (sid = idsA1.sid OR oid = idsB1.sid))';

        -- insert new triples using only IDs
        insertStmt :=
          'insert /*+ parallel append */ into ' || output_tab || ' (sid, pid, oid)
           select stateId, ' || to_char(capitalPropertyId,'TM9') || ', cityId
           from   (' || sqlStmt || ')';

        -- execute the query
        execute immediate insertStmt;

        -- commit our changes
        commit;
      end if;

      -- we only use ID values in the output_tab and we check for
      -- duplicates with our NOT EXISTS clauses.
      optimization_flag := SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_ALL_IDS +
                           SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_NEWDATA_ONLY +
                           SDO_SEM_INFERENCE.INF_EXT_OPT_FLAG_UNIQDATA_ONLY;

      -- return true to indicate success
      return true;

      -- handle any exceptions
      exception
        when others then
          diag_message := 'error occurred: ' || SQLERRM;
          return false;
    end sem_inf_capitals;
    /
    show errors;

The `sem_inf_capitals` function is similar to the `sem_inf_durations` function in Example 4a: Duration Rule, in that both functions must convert the lexical values of some triples into Oracle types to leverage native Oracle operators. In the case of `sem_inf_capitals`, the function converts the WKT lexical values encoding polygons and points into the Oracle Spatial and Graph SDO_GEOMETRY type, using the `SDO_RDF.getV$GeometryVal` function. The `getV$GeometryVal` function requires arguments mostly provided by the resource view (`resource_id_map_view`) and an additional argument, an ID to a spatial reference system (SRID). The `getV$GeometryVal` function will convert the geometry into the spatial reference system specified by SRID. The `sem_inf_capitals` function uses the default Oracle Spatial and Graph reference system, WGS84 Longitude-Latitude, specified by SRID value 8307. (For more information about support in RDF Semantic Graph for spatial references systems, see [Spatial Support](rdf-semantic-graph-overview.md).)

After converting the WKT values into SDO_GEOMETRY types using the `getV$GeometryVal` function, the `sem_inf_capitals` function compares the state geometry with the city geometry to see if the state contains the city. The `SDO_RELATE` operator performs this comparison and returns the literal value `'TRUE'` when the state contains the city. The `SDO_RELATE` operator can perform various different types of comparisons. (See [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md) for more information about `SDO_RELATE` and other spatial operators.)

To create an entailment with the `sem_inf_capitals` function, grant execution privileges to the MDSYS user, then pass the function name to the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md)procedure, as follows:

    -- grant appropriate privileges
    grant execute on sem_inf_capitals to mdsys;

    -- create the entailment
    begin
      sem_apis.create_entailment(
        'STATES_INF'
      , sem_models('STATES')
      , sem_rulebases('OWLPRIME')
      , passes => SEM_APIS.REACH_CLOSURE
      , inf_ext_user_func_name => 'sem_inf_capitals'
    );
    end;
    /

In addition to the triples inferred by OWLPRIME, the entailment should contain the following three new triples added by `sem_inf_capitals`:

    S                                P                               O
    -------------------------------- ------------------------------- --------------------------------
    http://example.org/geo/Colorado  http://example.org/geo/capital  http://example.org/geo/Denver
    http://example.org/geo/Utah      http://example.org/geo/capital  http://example.org/geo/SaltLake
    http://example.org/geo/Wyoming   http://example.org/geo/capital  http://example.org/geo/Cheyenne

**Parent topic:** User-Defined Inference Extension Function Examples

##### 9.1.3.6 Example 6: Calling a Web Service

This section contains a user-defined inference extension function (`sem_inf_geocoding`) and a related helper procedure (`geocoding`), which enable you to make a web service call to the Oracle Geocoder service. The user-defined inference extension function looks for the object values of triples using predicate `<urn:streetAddress>`, makes callouts to the Oracle public Geocoder service endpoint at `http://maps.oracle.com/geocoder/gcserver`, and inserts the longitude and latitude information as two separate triples.

For example, assume that the semantic model contains the following assertion:

    <urn:NEDC>  <urn:streetAddress>  "1 Oracle Dr., Nashua, NH"

In this case, an inference call using `sem_inf_geocoding` will produce the following new assertions:

    <urn:NEDC> <http://www.w3.org/2003/01/geo/wgs84_pos#long>  "-71.46421"
    <urn:NEDC> <http://www.w3.org/2003/01/geo/wgs84_pos#lat>   "42.75836"
    <urn:NEDC> <http://www.opengis.net/geosparql#asWKT>  "POINT(-71.46421 42.75836)"^^<http://www.opengis.net/geosparql#wktLiteral>
    <urn:NEDC> <http://xmlns.oracle.com/rdf/geo/asWKT>   "POINT(-71.46421 42.75836)"^^<http://xmlns.oracle.com/rdf/geo/WKTLiteral>

The `sem_inf_geocoding` function is defined as follows:

    create or replace function sem_inf_geocoding(
        src_tab_view         in  varchar2,
        resource_id_map_view in  varchar2,
        output_tab           in  varchar2,
        action               in  varchar2,
        num_calls            in  number,
        tplInferredLastRound in  number,
        options              in  varchar2 default null,
        optimization_flag    out number,
        diag_message         out varchar2
        )
    return boolean
    as
      pragma autonomous_transaction;
      iCount integer;

      nLong number;
      nLat  number;
      nWKT  number;
      nOWKT number;
      nStreetAddr number;

      sidTab    dbms_sql.number_table;
      oidTab    dbms_sql.number_table;

      vcRequestBody varchar2(32767);
      vcStmt        varchar2(32767);
      vcStreeAddr   varchar2(3000);

      type cur_type is ref cursor;
      cursorFind    cur_type;
      vcLong varchar2(100);
      vcLat  varchar2(100);
    begin
      if (action = 'START') then
        nLat := sdo_sem_inference.oracle_orardf_add_res('http://www.w3.org/2003/01/geo/wgs84_pos#lat');
        nLong := sdo_sem_inference.oracle_orardf_add_res('http://www.w3.org/2003/01/geo/wgs84_pos#long');
        nWKT  := sdo_sem_inference.oracle_orardf_add_res('http://www.opengis.net/geosparql#asWKT');
        nOWKT := sdo_sem_inference.oracle_orardf_add_res('http://xmlns.oracle.com/rdf/geo/asWKT');
      end if;

      if (action = 'RUN') then
        nStreetAddr := sdo_sem_inference.oracle_orardf_res2vid('<urn:streetAddress>');
        nLat := sdo_sem_inference.oracle_orardf_res2vid('http://www.w3.org/2003/01/geo/wgs84_pos#lat');
        nLong := sdo_sem_inference.oracle_orardf_res2vid('http://www.w3.org/2003/01/geo/wgs84_pos#long');
        nWKT  := sdo_sem_inference.oracle_orardf_res2vid('http://www.opengis.net/geosparql#asWKT');
        nOWKT := sdo_sem_inference.oracle_orardf_res2vid('http://xmlns.oracle.com/rdf/geo/asWKT');

        vcStmt := '
          select /*+ parallel */ distinct s1.sid as s_id, s1.oid as o_id
            from ' || src_tab_view || ' s1
           where s1.pid = :1
             and not exists ( select 1
                                from   ' || src_tab_view || ' x
                               where  x.sid = s1.sid
                                 and  x.pid = :2
                            ) ';
        open cursorFind for vcStmt using nStreetAddr, nLong;

        loop
          fetch cursorFind bulk collect into sidTab, oidTab limit 10000;
          for i in 1..sidTab.count loop
            vcStreeAddr := sdo_sem_inference.oracle_orardf_vid2lit(oidTab(i));
            -- dbms_output.put_line('Now processing street addr ' || vcStreeAddr);
            geocoding(vcStreeAddr, vcLong, vcLat);
            execute immediate 'insert into ' || output_tab || '(sid,pid,oid,gid,s,p,o,g)
                values(:1, :2, null, null, null, null, :3, null) '
                using sidTab(i), nLong, '"'||vcLong||'"';
            execute immediate 'insert into ' || output_tab || '(sid,pid,oid,gid,s,p,o,g)
                values(:1, :2, null, null, null, null, :3, null) '
                using sidTab(i), nLat, '"'||vcLat||'"';
            execute immediate 'insert into ' || output_tab || '(sid,pid,oid,gid,s,p,o,g)
                values(:1, :2, null, null, null, null, :3, null) '
                using sidTab(i), nWKT, '"POINT('|| vcLong || ' ' ||vcLat ||')"^^<http://www.opengis.net/geosparql#wktLiteral>';
            execute immediate 'insert into ' || output_tab || '(sid,pid,oid,gid,s,p,o,g)
                values(:1, :2, null, null, null, null, :3, null) '
                using sidTab(i), nOWKT, '"POINT('|| vcLong || ' ' ||vcLat ||')"^^<http://xmlns.oracle.com/rdf/geo/WKTLiteral>';
          end loop;
          exit when cursorFind%notfound;
        end loop;
        commit;
      end if;
      return true;
    end;
    /
    grant execute on sem_inf_geocoding to mdsys;

The `sem_inf_geocoding` function makes use of the following helper procedure named `geocoding`, which does the actual HTTP communication with the Geocoder web service endpoint. Note that proper privileges are required to connect to the web server.

    create or replace procedure geocoding(addr varchar2,
                                         vcLong out varchar2,
                                         vcLat  out varchar2
                                        )
    as
      httpReq  utl_http.req;
      httpResp utl_http.resp;

      vcRequestBody varchar2(32767);

      vcBuffer  varchar2(32767);
      idxLat integer;
      idxLatEnd integer;
    begin
      vcRequestBody := utl_url.escape('xml_request=<?xml version="1.0" standalone="yes"?>
        <geocode_request vendor="elocation">
          <address_list>
          <input_location id="27010">
          <input_address match_mode="relax_street_type">
            <unformatted country="US">
               <address_line value="'|| addr ||'"/>
            </unformatted>
           </input_address>
          </input_location>
        </address_list>
        </geocode_request>
      ');
      dbms_output.put_line('request ' || vcRequestBody);

      -- utl_http.set_proxy('<your_proxy_here_if_necessary>', null);
      httpReq := utl_http.begin_request (
        'http://maps.oracle.com/geocoder/gcserver', 'POST');

      utl_http.set_header(httpReq, 'Content-Type', 'application/x-www-form-urlencoded');
      utl_http.set_header(httpReq, 'Content-Length', lengthb(vcRequestBody));

      utl_http.write_text(httpReq, vcRequestBody);

      httpResp := utl_http.get_response(httpReq);

      utl_http.read_text(httpResp, vcBuffer, 32767);
      utl_http.end_response(httpResp);

      -- dbms_output.put_line('response ' || vcBuffer);
      -- Here we are doing some simple string parsing out of an XML.
      -- It is more robust to use XML functions instead.
      idxLat := instr(vcBuffer, 'longitude="');
      idxLatEnd := instr(vcBuffer, '"', idxLat + 12);
      vcLong := substr(vcBuffer, idxLat + 11, idxLatEnd - idxLat - 11);
      dbms_output.put_line('long = ' || vcLong);

      idxLat := instr(vcBuffer, 'latitude="');
      idxLatEnd := instr(vcBuffer, '"', idxLat + 11);
      vcLat := substr(vcBuffer, idxLat + 10, idxLatEnd - idxLat - 10);
      dbms_output.put_line('lat = ' || vcLat);
    exception
      when others then
        dbms_output.put_line('geocoding: error ' || dbms_utility.format_error_backtrace || ' '
                                                 || dbms_utility.format_error_stack);
    end;
    /

**Parent topic:** User-Defined Inference Extension Function Examples

### 9.2 User-Defined Functions and Aggregates

The RDF Semantic Graph query extension architecture enables you to add user-defined functions and aggregates to be used in SPARQL queries, both through the SEM_MATCH table function and through the support for Apache Jena.

The SPARQL 1.1 Standard provides several functions used mainly for filtering and categorizing data obtained by a query. However, you may need specialized functions not supported by the standard.

Some simple examples include finding values that belong to a specific type, or obtaining values with a square sum value that is greater than a certain threshold. Although this can be done by means of combining functions, it may be useful to have a single function that handles the calculations, which also allows for a simpler and shorter query.

The RDF Semantic Graph query extension allows you to include your own query functions and aggregates. This architecture allows:

- Custom query functions that can be used just like built-in SPARQL query functions, as explained in API Support for User-Defined Functions

- Custom aggregates that can be used just like built-in SPARQL aggregates, as explained in API Support for User-Defined Aggregates

<!-- -->

- Data Types for User-Defined Functions and Aggregates
- API Support for User-Defined Functions
- API Support for User-Defined Aggregates

**Parent topic:** User-Defined Inferencing and Querying

#### 9.2.1 Data Types for User-Defined Functions and Aggregates

The SDO_RDF_TERM object type is used to represent an RDF term when creating user-defined functions and aggregates.

SDO_RDF_TERM has the following attributes, which correspond to columns in the MDSYS.RDF_VALUE\$ table (see [Table 1-4](rdf-semantic-graph-overview.md) in [Statements](rdf-semantic-graph-overview.md) for a description of these attributes). The CTX1 attribute is reserved for future use and does not have a corresponding column in MDSYS.RDF_VALUE\$.

    SDO_RDF_TERM(
      VALUE_TYPE   VARCHAR2(10),
      VALUE_NAME    VARCHAR2(4000),
      VNAME_PREFIX   VARCHAR2(4000),
      VNAME_SUFFIX   VARCHAR2(512),
      LITERAL_TYPE   VARCHAR2(1000),
      LANGUAGE_TYPE   VARCHAR2(80),
      LONG_VALUE   CLOB,
      CTX1   VARCHAR2(4000) )

The following constructors are available for creating SDO_RDF_TERM objects. The first constructor populates each attribute from a single, lexical RDF term string. The second and third constructors receive individual attribute values as input. Only the first RDF term string constructor sets values for VNAME_PREFIX and VNAME_SUFFIX. These values are initialized to null by the other constructors.

    SDO_RDF_TERM (
      rdf_term_str  VARCHAR2)
      RETURN SELF;

    SDO_RDF_TERM (
      value_type  VARCHAR2,
      value_name  VARCHAR2,
      literal_type  VARCHAR2,
      language_type  VARCHAR2,
      long_value  CLOB)
      RETURN SELF;

    SDO_RDF_TERM (
      value_type  VARCHAR2,
      value_name  VARCHAR2,
      literal_type  VARCHAR2,
      language_type  VARCHAR2,
      long_value  CLOB,
      ctx1 VARCHAR2)
      RETURN SELF;

The SDO_RDF_TERM_LIST type is used to hold a list of SDO_RDF_TERM objects and is defined as `VARRAY(32767) of SDO_RDF_TERM`.

**Parent topic:** User-Defined Functions and Aggregates

#### 9.2.2 API Support for User-Defined Functions

A user-defined function is created by implementing a PL/SQL function with a specific signature, and a specific URI is used to invoke the function in a SPARQL query pattern.

After each successful inference extension function call, a commit is executed to persist changes made in the inference extension function call. If an inference extension function is defined as autonomous by specifying `pragma autonomous_transaction`, then it should either commit or roll back at the end of its implementation logic. Note that the inference engine may call an extension function multiple times when creating an entailment (once per round). Commits and rollbacks from one call will not affect other calls.

- PL/SQL Function Implementation
- Invoking User-Defined Functions from a SPARQL Query Pattern
- User-Defined Function Examples

**Parent topic:** User-Defined Functions and Aggregates

##### 9.2.2.1 PL/SQL Function Implementation

Each user-defined function must be implemented by a PL/SQL function with a signature in the following format:

    FUNCTION user_function_name (params IN SDO_RDF_TERM_LIST)
      RETURN SDO_RDF_TERM

This signature supports an arbitrary number of RDF term arguments, which are passed in using a single SDO_RDF_TERM_LIST object, and returns a single RDF term as output, which is represented as a single SDO_RDF_TERM object. Type checking or other verifications for these parameters are not performed. You should take steps to validate the data according to the function goals.

Note that PL/SQL supports callouts to functions written in other programming languages, such as C and Java, so the PL/SQL function that implements a user-defined query function can serve only as a wrapper for functions written in other programming languages.

**Parent topic:** API Support for User-Defined Functions

##### 9.2.2.2 Invoking User-Defined Functions from a SPARQL Query Pattern

After a user-defined function is implemented in PL/SQL, it can be invoked from a SPARQL query pattern using a function URI constructed from the prefix `<http://xmlns.oracle.com/rdf/extensions/>` followed by `schema.package_name.function_name` if the corresponding PL/SQL function is part of a PL/SQL package, or `schema.function_name` if the function is not part of a PL/SQL package. The following are two example function URIs:

    <http://xmlns.oracle.com/rdf/extensions/my_schema.my_package.my_function>(arg_1, …, arg_n)

    <http://xmlns.oracle.com/rdf/extensions/my_schema.my_function>(arg_1, …, arg_n)

**Parent topic:** API Support for User-Defined Functions

##### 9.2.2.3 User-Defined Function Examples

This section presents examples of the implementation of a user-defined function and the use of that function in a FILTER clause, in a SELECT expression, and in a BIND operation.

For the examples, assume that the following data, presented here in N-triple format, exists inside a model called `MYMODEL`:

      <p>  "1.0"^^xsd:double .
    <b>  <p>  "1.5"^^xsd:float .
    <c>  <p>  "3"^^xsd:decimal .
    <d>  <p>  "4"^^xsd:string .

Example 9-1 User-Defined Function to Calculate Sum of Two Squares

Example 9-1 shows the implementation of a simple function that receives two values and calculates the sum of the squares of each value.

    CREATE OR REPLACE FUNCTION sum_squares (params IN MDSYS.SDO_RDF_TERM_LIST)
       RETURN MDSYS.SDO_RDF_TERM
       AS
         retTerm    SDO_RDF_TERM;
         sqr1       NUMBER;
         sqr2       NUMBER;
         addVal     NUMBER;
         val1       SDO_RDF_TERM;
         val2       SDO_RDF_TERM;
       BEGIN
         –- Set the return value to null.
         retTerm := SDO_RDF_TERM(NULL,NULL,NULL,NULL,NULL);
         –- Obtain the data from the first two parameters.
         val1 := params(1);
         val2 := params(2);
         –- Convert the value stored in the sdo_rdf_term to number.
         –- If any exception occurs, return the null value.
         BEGIN
           sqr1 := TO_NUMBER(val1.value_name);
           sqr2 := TO_NUMBER(val2.value_name);
           EXCEPTION WHEN OTHERS THEN RETURN retTerm;
         END;
         –- Compute the square sum of both values.
           addVal := (sqr1 * sqr1) + (sqr2 * sqr2);
         –- Set the return value to the desired rdf term type.
         retTerm := SDO_RDF_TERM('LIT',to_char(addVal),
                    'http://www.w3.org/2001/XMLSchema#integer','',NULL);
         – Return the new value.
         RETURN retTerm;
    END;
    /
    SHOW ERRORS;

Note that the `sum_squares` function in Example 9-1 does not verify the data type of the value received. It is intended as a demonstration only, and relies on TO_NUMBER to obtain the numeric value stored in the VALUE_NAME field of SDO_RDF_TERM.

Example 9-2 User-Defined Function Used in a FILTER Clause

Example 9-2 shows the `sum_squares` function (from Example 9-1) used in a FILTER clause.

    SELECT s, o
    FROM table(sem_match(
    'SELECT  ?s ?o
     WHERE { ?s ?p ?o
     FILTER (<http://xmlns.oracle.com/rdf/extensions/schema.sum_squares>(?o,?o) > 2)}',
    sem_models('MYMODEL'),null,null,null,null,''));

The query in Example 9-2 returns the following result:

    s                    o
    -------------------- --------------------
    b                    1.5
    c                    3
    d                    4

Example 9-3 User-Defined Function Used in a SELECT Expression

Example 9-3 shows the `sum_squares` function (from Example 9-1) used in an expression in the SELECT clause.

    SELECT s, o, sqr_sum
    FROM table(sem_match(
    'SELECT  ?s ?o
           (<http://xmlns.oracle.com/rdf/extensions/schema.sum_squares>(?o,?o) AS
            ?sqr_sum)
     WHERE { ?s ?p ?o }',
    sem_models('MYMODEL'),null,null,null,null,''));

The query in Example 9-3 returns the following result:

    s                    o                    sqr_sum
    -------------------- -------------------- --------------------
    a                    1                    2
    b                    1.5                  4.5
    c                    3                    18
    d                    4                    32

Example 9-4 User-Defined Function Used in a BIND Operation

Example 9-4 shows the `sum_squares` function (from Example 9-1) used in a BIND operation.

    SELECT s, o, sqr_sum
    FROM table(sem_match(
    'SELECT  ?s ?o ?sqr_sum
     WHERE { ?s ?p ?o .
     BIND (<http://xmlns.oracle.com/rdf/extensions/schema.sum_squares>(?o,?o) AS
           ?sqr_sum)}',
    sem_models('MYMODEL'),null,null,null,null,''));

The query in Example 9-4 returns the following result:

    s                    o                    sqr_sum
    -------------------- -------------------- --------------------
    a                    1                    2
    b                    1.5                  4.5
    c                    3                    18
    d                    4                    32

**Parent topic:** API Support for User-Defined Functions

#### 9.2.3 API Support for User-Defined Aggregates

User-defined aggregates are implemented by defining a PL/SQL object type that implements a set of interface methods. After the user-defined aggregate is created, a specific URI is used to invoke it.

- ODCIAggregate Interface
- Invoking User-Defined Aggregates
- User-Defined Aggregate Examples

**Parent topic:** User-Defined Functions and Aggregates

##### 9.2.3.1 ODCIAggregate Interface

User-defined aggregates use the `ODCIAggregate` PL/SQL interface. For more detailed information about this interface, see the chapter about user-defined aggregate functions in [Oracle Database Data Cartridge Developer's Guide](../addci/using-user-defined-aggregate-functions.md).

The `ODCIAggregate` interface is implemented by a PL/SQL object type that implements four main functions:

- `ODCIAggregateInitialize`

- `ODCIAggregateIterate`

- `ODCIAggregateMerge`

- `ODCIAggregateTerminate`

As with user-defined functions (described in API Support for User-Defined Functions), user-defined aggregates receive an arbitrary number of RDF term arguments, which are passed in as an SDO_RDF_TERM_LIST object, and return a single RDF term value, which is represented as an SDO_RDF_TERM object.

This scheme results in the following signatures for the PL/SQL `ODCIAggregate` interface functions (with my_aggregate_obj_type representing the actual object type name):

    STATIC FUNCTION ODCIAggregateInitialize(
            sctx IN OUT my_aggregate_obj_type)
    RETURN NUMBER

    MEMBER FUNCTION ODCIAggregateIterate(
            self       IN OUT my_aggregate_obj_type
           ,value      IN MDSYS.SDO_RDF_TERM_LIST)
    RETURN NUMBER

    MEMBER FUNCTION ODCIAggregateMerge(
            self IN OUT my_aggregate_obj_type
           ,ctx2 IN     my_aggregate_obj_type)
    RETURN NUMBER

    MEMBER FUNCTION ODCIAggregateTerminate (
            self IN my_aggregate_obj_type
           ,return_value OUT MDSYS.SDO_RDF_TERM
           ,flags IN NUMBER)
    RETURN NUMBER

**Parent topic:** API Support for User-Defined Aggregates

##### 9.2.3.2 Invoking User-Defined Aggregates

After a user-defined aggregate is implemented in PL/SQL, it can be invoked from a SPARQL query by referring to an aggregate URI constructed from the prefix `<http://xmlns.oracle.com/rdf/aggExtensions/>` followed by `schema_name.aggregate_name`. The following is an example aggregate URI:

    <http://xmlns.oracle.com/rdf/aggExtensions/schema.my_aggregate>(arg_1, …, arg_n)

The DISTINCT modifier can be used with user-defined aggregates, as in the following example:

    <http://xmlns.oracle.com/rdf/aggExtensions/schema.my_aggregate>(DISTINCT arg_1)

In this case, only distinct argument values are passed to the aggregate. Note, however, that the DISTINCT modifier can only be used with aggregates that have exactly one argument.

**Parent topic:** API Support for User-Defined Aggregates

##### 9.2.3.3 User-Defined Aggregate Examples

This section presents examples of implementing and using a user-defined aggregate. For the examples, assume that the following data, presented here in N-triple format, exists inside a model called `MYMODEL`:

      <p>  "1.0"^^xsd:double .
    <b>  <p>  "1.5"^^xsd:float .
    <c>  <p>  "3"^^xsd:decimal .
    <c>  <p>  "4"^^xsd:decimal .
    <d>  <p>  "4"^^xsd:string .

Example 9-5 User-Defined Aggregate Implementation

Example 9-5 shows the implementation of a simple user-defined aggregate (`countSameType`). This aggregate has two arguments: the first is any RDF term, and the second is a constant data type URI. The aggregate counts how many RDF terms from the first argument position have a data type equal to the second argument.

    -- Aggregate type creation
    CREATE OR REPLACE TYPE countSameType authid current_user AS OBJECT(

    count NUMBER, –- Variable to store the number of same-type terms.

    –- Mandatory Functions for aggregates
    STATIC FUNCTION ODCIAggregateInitialize(
            sctx IN OUT countSameType)
    RETURN NUMBER,

    MEMBER FUNCTION ODCIAggregateIterate(
             self       IN OUT countSameType
           , value      IN MDSYS.SDO_RDF_TERM_LIST)
    RETURN NUMBER,

    MEMBER FUNCTION ODCIAggregateMerge(
            self IN OUT countSameType
           ,ctx2 IN     countSameType)
    RETURN NUMBER,

    MEMBER FUNCTION ODCIAggregateTerminate (
            self IN countSameType
           ,return_value OUT MDSYS.SDO_RDF_TERM
           ,flags IN NUMBER)
    RETURN NUMBER
    );
    /
    SHOW ERRORS;

    –- Interface function for the user-defined aggregate
    CREATE OR REPLACE FUNCTION countSameAs (input MDSYS.SDO_RDF_TERM_LIST) RETURN MDSYS.SDO_RDF_TERM
    PARALLEL_ENABLE AGGREGATE USING countSameType;
    /
    show errors;

    –- User-defined aggregate body
    CREATE OR REPLACE TYPE BODY countSameType IS

    STATIC FUNCTION ODCIAggregateInitialize(
             sctx            IN OUT countSameType)
    RETURN NUMBER IS
    BEGIN
      sctx := countSameType (0); –- Aggregate initialization
      RETURN ODCIConst.Success;
    END;

    MEMBER FUNCTION ODCIAggregateIterate(
             self           IN OUT countSameType
           , value          IN MDSYS.SDO_RDF_TERM_LIST )
    RETURN NUMBER IS
    BEGIN
      -- Increment count if the first argument has a literal type
      -- URI equal to the value of the second argument
      IF (value(1).literal_type = value(2).value_name) THEN
        self.count := self.count + 1;
      END IF;
      RETURN ODCIConst.Success;
    END;

    MEMBER FUNCTION ODCIAggregateMerge(
             self            IN OUT countSameType
            ,ctx2            IN countSameType)
    RETURN NUMBER IS
    BEGIN
      –- Sum count to merge parallel threads.
      self.count := self.count + ctx2.count;
      RETURN ODCIConst.Success;
    END;

    MEMBER FUNCTION ODCIAggregateTerminate(
             self            IN countSameType
            ,return_value    OUT MDSYS.SDO_RDF_TERM
            ,flags           IN NUMBER)
    RETURN NUMBER IS
    BEGIN
       -- Set the return value
       return_value := MDSYS.SDO_RDF_TERM('LIT',to_char(self.count),
         'http://www.w3.org/2001/XMLSchema#decimal',NULL,NULL); RETURN  ODCIConst.Success;
    END;

    END;
    /
    SHOW ERRORS;

Example 9-6 User-Defined Aggregate Used Without a GROUP BY Clause

Example 9-6 shows the `countSameType` aggregate (from Example 9-5) used over an entire query result group.

    FROM o
    from table(sem_match(
    'SELECT
     (<http://xmlns.oracle.com/rdf/aggExtensions/schema.countSameType>(?o,xsd:decimal)
      AS ?o)
     WHERE { ?s ?p ?o }',
    sem_models('MYMODEL'),null,null,null,null,''));

The query in Example 9-6 returns the following result:

    o
    --------------------
    2

Example 9-7 User-Defined Aggregate Used With a GROUP BY Clause

Example 9-7 shows the `countSameType` aggregate (from Example 9-5) used over a set of groups formed from a GROUP BY clause.

    select s, o
    from table(sem_match(
    'SELECT ?s
     (<http://xmlns.oracle.com/rdf/aggExtensions/schema.countSameType>(?o,xsd:decimal)
      AS ?o)
     WHERE { ?s ?p ?o } GROUP BY ?s',
    sem_models('MYMODEL'),null,null,null,null,''));

The query in Example 9-7 returns the following result:

    s                    o
    -------------------- --------------------
    a                    0
    b                    0
    c                    2
    d                    0

**Parent topic:** API Support for User-Defined Aggregates
