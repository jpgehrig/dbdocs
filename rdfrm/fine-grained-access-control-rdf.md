## 6 Fine-Grained Access Control for RDF Data

The default control of access to the Oracle Database semantic data store is at the model level: the owner of a model can grant select, delete, and insert privileges on the model to other users by granting appropriate privileges on the view named RDFM\_\<model_name\>. However, for applications with stringent security requirements, you can enforce a fine-grained access control mechanism by using the Oracle Label Security option of Oracle Database.

Oracle Label Security (OLS) for RDF data allows sensitivity labels to be associated with individual triples stored in an RDF model. For each query, access to specific triples is granted by comparing their labels with the user's session labels. This triple-level security option provides a thin layer of RDF-specific capabilities on top of the Oracle Database native support for label security.

For information about using OLS, see [Oracle Label Security Administrator's Guide](../olsag/index.md).

- Triple-Level Security
  The triple-level security option provides a thin layer of RDF-specific capabilities on top of the Oracle Database native support for label security.

**Parent topic:** [Conceptual and Usage Information](part-concept-usage.md)

### 6.1 Triple-Level Security

The triple-level security option provides a thin layer of RDF-specific capabilities on top of the Oracle Database native support for label security.

To use triple-level security, specify `SEM_RDFSA.TRIPLE_LEVEL_ONLY` as the `rdfsa_options` parameter value when you execute the [SEM_RDFSA.APPLY_OLS_POLICY](SEM_RDFSA-reference.md) procedure. For example:

    EXECUTE sem_rdfsa.apply_ols_policy('defense', SEM_RDFSA.TRIPLE_LEVEL_ONLY, network_owner=>'FGAC_ADMIN', network_name=>'OLS_NET');

Do not specify any of the other available parameters for the [SEM_RDFSA.APPLY_OLS_POLICY](SEM_RDFSA-reference.md) procedure.

When you use triple-level security, OLS is applied to each semantic model in the network. That is, label security is applied to the relevant internal tables and to all the application tables; there is no need to manually apply policies to the application tables of existing semantic models. However, if you need to create additional models after applying the OLS policy, you must use the [SEM_OLS.APPLY_POLICY_TO_APP_TAB](SEM_OLS-reference.md) procedure to apply OLS to the application table before creating the model. Similarly, if you have dropped a semantic model and you no longer need to protect the application table, you can use the [SEM_OLS.REMOVE_POLICY_FROM_APP_TAB](SEM_OLS-reference.md) procedure. (These procedures are described in [SEM_OLS Package Subprograms](SEM_OLS-reference.md).)

With triple-level security, duplicate triples with different labels can be inserted in the semantic model. (Such duplicates are not allowed with resource-level security.) For example, assume that you have a triple with a very sensitive label, such as:

    (<urn:X>,<urn:P>,<urn:Y>, "TOPSECRET")

This does not prevent a low-privileged (`UNCLASSIFIED`) user from inserting the triple `(<urn:X>,<urn:P>,<urn:Y>, "UNCLASSIFIED")`. Because SPARQL and SEM_MATCH do not return label information, a query will return both rows (assuming the user has appropriate privileges), and it will not be easy to distinguish between the `TOPSECRET` and `UNCLASSIFIED` triples.

To filter out such low-security triples when querying the semantic models, you can one or more the following options with SEM_MATCH:

- `POLICY_NAME` specifies the OLS policy name.

- `MIN_LABEL` specifies the minimum label for triples that are included in the query

In other words, every triple that contains a label that is strictly dominated by `MIN_LABEL` is not included in the query. For example, to filter out the "UNCLASSIFIED" triple, you could use the following query (assuming the OLS policy name is `DEFENSE` and that the query user has read privileges over `UNCLASSIFIED` and `TOPSECRET` triples):

    SELECT s,p,y FROM table(sem_match('{?s ?p ?y}' ,
      sem_models(TEST'), null, null, null, null,
      'MIN_LABEL=TOPSECRET POLICY_NAME=DEFENSE',
      null, null, ‘FGAC_ADMIN’, 'OLS_NET'));

Note that the filtering in the preceding example occurs in addition to the security checks performed by the native OLS software.

After a triple has been inserted, you can view and update the label information through the `CTXT1` column in the application table for the semantic model (assuming that you have the `WRITEUP` and `WRITEDOWN` privileges to modify the labels).

There are no restrictions on who can perform inference or bulk loading with triple-level security; all of the inferred or bulk loaded triples are inserted with the user's session row label. Note that you can change the session labels by using the SA_UTL package. (For more information about SA_UTL, see [Oracle Label Security Administrator's Guide](../olsag/oracle-label-security-pl-sql-packages.md).)

- Fine-Grained Security for Inferred Data and Ladder-Based Inference (LBI)
- Extended Example: Applying OLS Triple-Level Security on Semantic Data

**Parent topic:** Fine-Grained Access Control for RDF Data

#### 6.1.1 Fine-Grained Security for Inferred Data and Ladder-Based Inference (LBI)

When triple-level security is turned on for RDF data stored in Oracle Database, asserted facts are tagged with data labels to enforce mandatory access control. In addition, when a user invokes the forward-chaining based inference function through the [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) procedure, the newly inferred relationships will be tagged with the current row label (`SA_UTL.NUMERIC_ROW_LABEL`).

These newly inferred relationships are derived solely based on the information that the user is allowed to access. These relationships do, however, share the same data label. This is understandable because a [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md) call can be viewed as a three-step process: read operation, followed by a logical inference computation, followed by a write operation. The read operation gathers information upon which inference computation is based, and it is restricted by access privileges, the user's label, and the data labels; the logical inference computation step is purely mathematical; and the final write of inferred information into the entailed graph is no different from the same user asserting some new facts (which happen to be calculated by the previous step).

Having all inferred assertions tagged with a single label is sufficient if a user only owns a single label. It is, however, not fine-grained enough when there are multiple labels owned by the same user, which is a common situation in a multitenancy setup.

For example, assume a user sets its user label and data label as `TopSecret`, invokes [SEM_APIS.CREATE_ENTAILMENT](SEM_APIS-reference.md), switches to a weaker label named `Secret`, and finally performs a SPARQL query. The query will not be able to see any of those newly inferred relationships because they were all tagged with the `TopSecret` label. However, if the user switches back to the `TopSecret` label, now every single inferred relationship is visible. It is "all or nothing" (that is, all visible or nothing visible) as far as inferred relationships are concerned.

When multiple labels are available for use by a given user, you normally want to assign different labels to different inferred relationships. There are two ways to achieve this goal:

- Invoking SEM_APIS.CREATE_ENTAILMENT Multiple Times

- Using Ladder-Based Inference (LBI)

Ladder-based inference, effective with Oracle Database 12c Release 1 (12.1), is probably the simpler and more convenient of the two approaches.

##### Invoking SEM_APIS.CREATE_ENTAILMENT Multiple Times

Assume a security policy named DEFENSE, a user named SCOTT, and a sequence of user labels Label1, Label2,..., Labeln owned by SCOTT. The following call by SCOTT sets the label as Label1, runs the inference for the first time, and tags the newly inferred triples with Label1:

    EXECUTE sa_utl.set_label('defense',char_to_label('defense','Label1'));
    EXECUTE sa_utl.set_row_label('defense',char_to_label('defense','Label1'));
    EXECUTE sem_apis.create_entailment('inf', sem_models('contracts'), sem_rulebases('owlprime'), SEM_APIS.REACH_CLOSURE, null,'',network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');

Now, SCOTT switches the label to Label2, runs the inference a second time, and tags the newly inferred triples with Label2. Obviously, if Label2 is dominated by Label1, then no new triples will be inferred because Label2 cannot see anything beyond what Label1 is allowed to see. If Label2 is not dominated by Label1, the read step of the inference process will probably see a different set of triples, and consequently the inference call can produce some new triples, which will in turn be tagged with Label2.

For the purpose of this example, assume the following condition holds true: for any 1 \<= i \< j \<= n, Labelj is not dominated by Labeli.

    EXECUTE sa_utl.set_label('defense',char_to_label('defense','Label2'));
    EXECUTE sa_utl.set_row_label('defense',char_to_label('defense','Label2'));
    EXECUTE sem_apis.create_entailment('inf', sem_models('contracts'), sem_rulebases('owlprime'), SEM_APIS.REACH_CLOSURE, null, 'ENTAIL_ANYWAY=T', network_owner=>'FGAC_ADMIN', network_name=>'OLS_NET');

SCOTT continues the preceding actions using the rest of the labels in the label sequence: Label1, Label2, ..., Labeln. The last step will be as follows:

    EXECUTE sa_utl.set_label('defense',char_to_label('defense','Labeln'));
    EXECUTE sa_utl.set_row_label('defense',char_to_label('defense','Labeln'));
    EXECUTE sem_apis.create_entailment('inf', sem_models('contracts'), sem_rulebases('owlprime'), SEM_APIS.REACH_CLOSURE, null, 'ENTAIL_ANYWAY=T', network_owner=>'FGAC_ADMIN', network_name=>'OLS_NET');

After all these actions are performed, the inference graph probably consists of triples tagged with various different labels.

##### Using Ladder-Based Inference (LBI)

Basically, ladder-based inference (LBI) wraps in one API call all the actions described in the Invoking SEM_APIS.CREATE_ENTAILMENT Multiple Times approach. Visually, those actions are like climbing up a ladder. When proceeding from one label to the next, more asserted facts become visible or accessible (assuming the new label is not dominated by any of the previous ones), and therefore new relationships can be inferred.

The syntax to invoke LBI is shown in the following example.

    EXECUTE sem_apis.create_entailment('inf',
      sem_models('contracts'),
      sem_rulebases('owlprime'),
      SEM_APIS.REACH_CLOSURE,
      null,
      null,
      ols_ladder_inf_lbl_seq=>'numericLabel1 numericLabel2 numericLabel3 numericLabel4',
      network_owner=>'FGAC_ADMIN',
      network_name=>'OLS_NET'
    );

The parameter `ols_ladder_inf_lbl_seq` specifies a sequence of labels. This sequence is provided as a list of numeric labels delimited by spaces. When using LBI, it is a good practice to arrange the sequence of labels so that weaker labels are put before stronger labels. This will reduce the size of the inferred graph. (If labels do not dominate each other, they can be specified in any order.)

**Parent topic:** Triple-Level Security

#### 6.1.2 Extended Example: Applying OLS Triple-Level Security on Semantic Data

This section presents an extended example illustrating how to apply OLS triple-level security to semantic data. It assumes that OLS has been configured and enabled. The examples are very simplified, and do not reflect recommended practices regarding user names and passwords.

Unless otherwise indicated, perform the steps while connected AS SYSDBA.

1.  Perform some necessary setup steps.

    1.  As SYSDBA, create database users named A, B, and C.

            create user a identified by <password-for-a>;
            grant connect, unlimited tablespace, resource to a;
            create user b identified by <password-for-b>;
            grant connect, unlimited tablespace, resource to b;
            create user c identified by <password-for-c>;
            grant connect, unlimited tablespace, resource to c;

    2.  As SYSDBA, create a security administrator and grant privileges.

            CREATE USER fgac_admin identified by <password-for-fgac_admin>;
            GRANT connect, unlimited tablespace,resource to fgac_admin;

            -- Needed to administer OLS on a shared schema-private network
            GRANT execute on MDSYS.SEM_RDFSA to fgac_admin;
            GRANT exempt access policy to fgac_admin;

            -- Needed to administer an OLS policy
            GRANT EXECUTE ON sa_components TO fgac_admin;
            GRANT EXECUTE ON sa_user_admin TO fgac_admin;
            GRANT EXECUTE ON sa_label_admin TO fgac_admin;
            GRANT EXECUTE ON sa_policy_admin TO fgac_admin;
            GRANT EXECUTE ON sa_sysdba to fgac_admin;
            GRANT EXECUTE ON TO_LBAC_DATA_LABEL to fgac_admin;
            GRANT lbac_dba to fgac_admin;

    3.  Connect as SYSTEM and create a schema-private semantic network owned by the security administrator with sharing privileges.

            CONNECT system/<password-for-system>;
            EXECUTE sem_apis.create_sem_network('tbs_3',network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');
            EXECUTE sem_apis.grant_network_sharing_privs('FGAC_ADMIN');

    4.  Connect as the security administrator and set up network sharing for users a, b, and c.

            CONNECT fgac_admin/<password-for- fgac_admin>;
            EXECUTE sem_apis.enable_network_sharing(network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');
            EXECUTE sem_apis.grant_network_access_privs(network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET', network_user=>'A');
            EXECUTE sem_apis.grant_network_access_privs(network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET', network_user=>'B');
            EXECUTE sem_apis.grant_network_access_privs(network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET', network_user=>'C');

    5.  Connect as the security administrator and create a policy named defense.

            CONNECT fgac_admin/<password-for-fgac_admin>;
            EXECUTE SA_SYSDBA.CREATE_POLICY('defense','ctxt1');

    6.  Create three security levels (For simplicity, compartments and groups are omitted.)

            EXECUTE SA_COMPONENTS.CREATE_LEVEL('defense',3000,'TS','TOP SECRET');
            EXECUTE SA_COMPONENTS.CREATE_LEVEL('defense',2000,'SE','SECRET');
            EXECUTE SA_COMPONENTS.CREATE_LEVEL('defense',1000,'UN','UNCLASSIFIED');

    7.  Create three labels.

            EXECUTE SA_LABEL_ADMIN.CREATE_LABEL('defense',1000,'UN');
            EXECUTE SA_LABEL_ADMIN.CREATE_LABEL('defense',1500,'SE');
            EXECUTE SA_LABEL_ADMIN.CREATE_LABEL('defense',3100,'TS');

    8.  Assign labels and privileges.

            EXECUTE SA_USER_ADMIN.SET_USER_LABELS('defense','A','UN');
            EXECUTE SA_USER_ADMIN.SET_USER_LABELS('defense','B','SE');
            EXECUTE SA_USER_ADMIN.SET_USER_LABELS('defense','C','TS');
            EXECUTE SA_USER_ADMIN.SET_USER_LABELS('defense','fgac_admin','TS');
            EXECUTE SA_USER_ADMIN.SET_USER_PRIVS('defense','FGAC_ADMIN', 'full');

2.  Create a semantic model.

    1.  Create a model and share it with some other users.

            CONNECT a/<password-for-a>
            CREATE TABLE project_tpl (triple sdo_rdf_triple_s) compress for oltp;
            EXECUTE sem_apis.create_sem_model('project', 'project_tpl', 'triple' ,network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');
            GRANT select on fgac_admin.ols_net#rdfm_project to B;
            GRANT select on fgac_admin.ols_net#rdfm_project to C;
            GRANT select, insert, update, delete on project_tpl to B, C;

    2.  Ensure that the bulk loading API can be executed.

            GRANT insert on project_tpl to fgac_admin;

3.  Apply the OLS policy for RDF.

        CONNECT fgac_admin/<password-for-fgac_admin>
        BEGIN
          sem_rdfsa.apply_ols_policy('defense', sem_rdfsa.TRIPLE_LEVEL_ONLY,network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');
        END;
        /

        /

    Note that the application table now has an extra column named CTXT1:

        CONNECT a/<password-for-a>
        DESCRIBE project_tpl;
        Name                                      Null?    Type
        ----------------------------------------- -------- --------------------------
         TRIPLE                                             PUBLIC.SDO_RDF_TRIPLE_S
         CTXT1                                              NUMBER(10)

4.  Add data to the semantic model.

        -- User A uses incremental APIs to add semantic data
        connect a/<password-for-a>
        INSERT INTO project_tpl(triple) values      (sdo_rdf_triple_s('project','<urn:A>','<urn:hasManager>','<urn:B>','FGAC_ADMIN','OLS_NET'));
        INSERT INTO project_tpl(triple) values      (sdo_rdf_triple_s('project','<urn:B>','<urn:hasManager>','<urn:C>','FGAC_ADMIN','OLS_NET'));
        INSERT INTO project_tpl(triple) values       (sdo_rdf_triple_s('project','<urn:A>','<urn:expenseReportAmount>','"100"','FGAC_ADMIN','OLS_NET'));
        INSERT INTO project_tpl(triple) values       (sdo_rdf_triple_s('project','<urn:expenseReportAmount>','rdfs:subPropertyOf','<urn:projExp>','FGAC_ADMIN','OLS_NET'));
        COMMIT;

        -- User B uses bulk API to add semantic data
        connect b/<password-for-b>
        CREATE TABLE  project_stab(RDF$STC_GRAPH varchar2(4000),
        RDF$STC_sub varchar2(4000),
        RDF$STC_pred varchar2(4000),
        RDF$STC_obj varchar2(4000)) compress;
        GRANT select on project_stab to fgac_admin;

        -- For simplicity, data types are omitted.
        INSERT INTO project_stab values(null, '<urn:B>','<urn:expenseReportAmount>','"200"');
        INSERT INTO project_stab values(null, '<urn:proj1>','<urn:deadline>','"2012-12-25"');
        EXECUTE sem_apis.bulk_load_from_staging_table('project','b','project_stab' ,network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');

        -- As User B, check the contents in the application table
         connect b/<password-for-b>
        SELECT * from a.project_tpl order by ctxt1;

        SDO_RDF_TRIPLE_S(8.5963E+18, 7, 1.4711E+18, 2.0676E+18, 8.5963E+18)    1000
        SDO_RDF_TRIPLE_S(5.1676E+18, 7, 8.5963E+18, 2.0676E+18, 5.1676E+18)    1000
        SDO_RDF_TRIPLE_S(2.3688E+18, 7, 1.4711E+18, 4.6588E+18, 2.3688E+18)    1000
        SDO_RDF_TRIPLE_S(7.6823E+18, 7, 4.6588E+18, 1.1911E+18, 7.6823E+18)    1000
        SDO_RDF_TRIPLE_S(6.6322E+18, 7, 8.5963E+18, 4.6588E+18, 6.6322E+18)    1500
        SDO_RDF_TRIPLE_S(8.4800E+18, 7, 6.2294E+18, 5.4118E+18, 8.4800E+18)    1500

        6 rows selected.
        SELECT count(1) from fgac_admin.ols_net#rdfm_project;
        6

        -- As User A, check the contents in the application table
        -- As expected, A can only see 4 triples
        SQL> conn a/<password>
        SQL> select * from a.project_tpl order by ctxt1;
        SDO_RDF_TRIPLE_S(8.5963E+18, 7, 1.4711E+18, 2.0676E+18, 8.5963E+18)    1000

        SDO_RDF_TRIPLE_S(5.1676E+18, 7, 8.5963E+18, 2.0676E+18, 5.1676E+18)    1000

        SDO_RDF_TRIPLE_S(2.3688E+18, 7, 1.4711E+18, 4.6588E+18, 2.3688E+18)    1000

        SDO_RDF_TRIPLE_S(7.6823E+18, 7, 4.6588E+18, 1.1911E+18, 7.6823E+18)    1000

        SQL> select count(1) fromfgac_admin.ols_net#rdfm_project;
        4

        -- User C uses incremental APIs to add semantic data including 2 quads
        connect c/<password-for-c>
        INSERT INTO a.project_tpl(triple) values      (sdo_rdf_triple_s('project','<urn:C>','<urn:expenseReportAmount>','"400"','FGAC_ADMIN','OLS_NET'));
        INSERT INTO a.project_tpl(triple) values      (sdo_rdf_triple_s('project','<urn:proj1>','<urn:hasBudget>','"10000"','FGAC_ADMIN','OLS_NET'));
        INSERT INTO a.project_tpl(triple) values      (sdo_rdf_triple_s('project:<urn:proj2>','<urn:proj2>','<urn:hasBudget>','"20000"','FGAC_ADMIN','OLS_NET'));
        INSERT INTO a.project_tpl(triple) values      (sdo_rdf_triple_s('project:<urn:proj2>','<urn:proj2>','<urn:dependsOn>','<urn:proj1>','FGAC_ADMIN','OLS_NET'));
        COMMIT;

5.  Query the data as different users using the default label.

        -- Now as user A, B, C, execute the following query
        select lpad(nvl(g, ' '), 20) || ' ' || s || ' ' || p || ' ' || o from table(sem_match('select * where { graph ?g { ?s ?p ?o }}',
        sem_models('project'),
        null,
        null,
        null,
        null,
        'GRAPH_MATCH_UNNAMED=T',
        null,
        null,
        'FGAC_ADMIN',
        'OLS_NET'))
            order by g, s, p, o;

        connect  a/<password-for-a>
        -- Repeat the preceding query
        SQL> /

        urn:A urn:expenseReportAmount 100
        urn:A urn:hasManager urn:B
        urn:B urn:hasManager urn:C
        urn:expenseReportAmount http://www.w3.org/2000/01/rdf-schema#subPropertyOf urn:projExp
        SQL> connect  b/<password-for-b>
        SQL> /

        urn:A urn:expenseReportAmount 100
        urn:A urn:hasManager urn:B
        urn:B urn:expenseReportAmount 200
        urn:B urn:hasManager urn:C
        urn:expenseReportAmount http://www.w3.org/2000/01/rdf-schema#subPropertyOf urn:projExp
        urn:proj1 urn:deadline 2012-12-25
        SQL> connect  c/<password-for-c>
        SQL> /

        urn:proj2 urn:proj2 urn:dependsOn urn:proj1
        urn:proj2 urn:proj2 urn:hasBudget 20000
        urn:A urn:expenseReportAmount 100
        urn:A urn:hasManager urn:B
        urn:B urn:expenseReportAmount 200
        urn:B urn:hasManager urn:C
        urn:C urn:expenseReportAmount 400
        urn:expenseReportAmount http://www.w3.org/2000/01/rdf-schema#subPropertyOf urn:projExp
        urn:proj1 urn:deadline 2012-12-25
        urn:proj1 urn:hasBudget 10000

    As expected, different users (with different labels) can see different sets of triples in the project RDF graph.

6.  Query the same data as user C using different labels.
        exec sa_utl.set_label('defense',char_to_label('defense','SE'));
        exec sa_utl.set_row_label('defense',char_to_label('defense','SE'));

    The same query used in the preceding step produces just 6 matches with label set to SE:

        urn:A urn:expenseReportAmount 100
        urn:A urn:hasManager urn:B
        urn:B urn:expenseReportAmount 200
        urn:B urn:hasManager urn:C
        urn:expenseReportAmount http://www.w3.org/2000/01/rdf-schema#subPropertyOf urn:projExp
        urn:proj1 urn:deadline 2012-12-25

        6 rows selected.

    If user C picks the weakest label ("unclassified"), then user C sees even less

        exec sa_utl.set_label('defense',char_to_label('defense','UN'));
        exec sa_utl.set_row_label('defense',char_to_label('defense','UN'));

    The same query used in the preceding step produces just 4 matches:

        urn:A urn:expenseReportAmount 100
        urn:A urn:hasManager urn:B
        urn:B urn:hasManager urn:C
        urn:expenseReportAmount http://www.w3.org/2000/01/rdf-schema#subPropertyOf urn:projExp

    If user C wants to run the query only against triples/quads with data label that dominates "Secret":

        -- First set the label back
        exec sa_utl.set_label('defense',char_to_label('defense','TS'));
        exec sa_utl.set_row_label('defense',char_to_label('defense','TS'));

        select lpad(nvl(g, ' '), 20) || ' ' || s || ' ' || p || ' ' || o
        from table(sem_match('select * where { graph ?g { ?s ?p ?o }}',
        sem_models('project'),
        null,
        null,
        null,
        null,
        'MIN_LABEL=SE POLICY_NAME=DEFENSE GRAPH_MATCH_UNNAMED=T',
        null,
        null,
        'FGAC_ADMIN',
        'OLS_NET'))
        order by g, s, p, o;

    The query response excludes those assertions made by user A:

        urn:proj2 urn:proj2 urn:dependsOn urn:proj1
        urn:proj2 urn:proj2 urn:hasBudget 20000
        urn:B urn:expenseReportAmount 200
        urn:C urn:expenseReportAmount 400
        urn:proj1 urn:deadline 2012-12-25
        urn:proj1 urn:hasBudget 10000

        6 rows selected.

    The same query can be executed as User A. However, no matches are returned, as expected.

You can delete semantic data when OLS is enabled for RDF. In the following example, assume that [SEM_RDFSA.APPLY_OLS_POLICY](SEM_RDFSA-reference.md) has been executed successfully, and that the same user setup and label designs are used as in the preceding example.

    -- First, create a test model as user A and grant access to users B and C
    connect a/<password-for-a>

    create table test_tpl (triple sdo_rdf_triple_s) compress for oltp;
    grant select, insert, update, delete on test_tpl to B, C;

    -- The following will fail with an error message
    -- "Error while creating triggers: If OLS
    -- is enabled,  you have to apply table policy
    -- before creating an OLS-enabled model"
    --
    EXECUTE sem_apis.create_sem_model('test', 'test_tpl', 'triple',network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');

    -- Grant select on the model view to users B and C
    grant select on fgac_admin.ols_net#rdfm_test to B,C;

    -- You need to run this API first

    connect fgac_admin/<password-for-fgac_admin>

    EXECUTE sem_ols.apply_policy_to_app_tab('defense', 'A', 'TEST_TPL',network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');

    -- Now model creation (after OLS policy has been applied) can go through
    connect a/<password-for-a>
    EXECUTE sem_apis.create_sem_model('test', 'test_tpl', 'triple',network_owner=>'FGAC_ADMIN',network_name=>'OLS_NET');

    -- Add a triple as User A
    INSERT INTO test_tpl(triple) values
    (sdo_rdf_triple_s('test','<urn:A>','<urn:p>','<urn:B>','FGAC_ADMIN','OLS_NET'));
    COMMIT;

    -- Add the same triple as User B
    connect b/<password-for-b>
    INSERT INTO a.test_tpl(triple) values
    (sdo_rdf_triple_s('test','<urn:A>','<urn:p>','<urn:B>','FGAC_ADMIN','OLS_NET'));
    COMMIT;


    -- Now User B can see both triples in the application table as well as the model view
    set numwidth 20
    SELECT * from a.test_tpl;

    SDO_RDF_TRIPLE_S(8596269297967065604, 19, 1471072612573670395, 28121856352072361
    78, 8596269297967065604)
                    1000

    SDO_RDF_TRIPLE_S(8596269297967065604, 19, 1471072612573670395, 28121856352072361
    78, 8596269297967065604)
                    1500

    SELECT count(1) from fgac_admin.ols_net#rdfm_test;
                       2

    -- User A can only see one triple due to A's label assignment, as expected.

    SELECT * from a.test_tpl;

    SDO_RDF_TRIPLE_S(8596269297967065604, 19, 1471072612573670395, 28121856352072361
    78, 8596269297967065604)
                    1000

    SELECT count(1) from fgac_admin.ols_net#rdfm_test;
                       1


    -- User A issues a delete to remove A's assertions
    SQL> delete from a.test_tpl;
    1 row deleted.

    COMMIT;
    Commit complete.


    -- Now user A has no assertions left.

    SELECT * from a.test_tpl;
    no rows selected

    SELECT count(1) from fgac_admin.ols_net#rdfm_test;
                       0

    -- Note that the preceding delete does not affect the same assertion made by B.
    connect b/<password-for-b>
    SELECT * from a.test_tpl;

    SDO_RDF_TRIPLE_S(8596269297967065604, 19, 1471072612573670395, 28121856352072361
    78, 8596269297967065604)
                    1500

    SELECT count(1) from fgac_admin.ols_net#rdfm_test;
                       1

    -- User B can remove this assertion using a DELETE statement.
    -- The following DELETE statement uses the oracle_orardf_res2vid function
    -- to narrow down the scope to triples with a particular subject.
    DELETE FROM a.test_tpl app_tab
           where app_tab.triple.rdf_s_id =
                 sem_apis.res2vid('FGAC_ADMIN.OLS_NET#RDF_VALUE$','<urn:A>');

    1 row deleted.

**Parent topic:** Triple-Level Security
