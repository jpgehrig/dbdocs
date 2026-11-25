## 2.1 Getting Started with Semantic Data in a Schema-Private Network

1.  Create a tablespace for the system tables. You must be connected as a user with appropriate privileges to create the tablespace. The following example creates a tablespace named `rdf_tblspace`:
        CREATE TABLESPACE rdf_tblspace
         DATAFILE 'rdf_tblspace.dat' SIZE 1024M REUSE
         AUTOEXTEND ON NEXT 256M MAXSIZE UNLIMITED
         SEGMENT SPACE MANAGEMENT AUTO;
2.  Create a database user to work with semantic data in the database and grant the necessary privileges to the database user. You must be connected as a user with appropriate privileges to create the database user.
    The following example creates a network owner user `rdfuser` and grants the necessary privileges to `rdfuser`:
        CREATE USER rdfuser
        IDENTIFIED BY <password-for-rdfuser>
        QUOTA 5G ON rdf_tblspace;

        GRANT CONNECT, RESOURCE, CREATE VIEW TO rdfuser;
3.  Connect as the network owner user.
        CONNECT rdfuser/<password-for-rdfuser>
4.  Create a schema-private semantic network.
    Creating a semantic network adds semantic data support to an Oracle database. You must create a semantic network as the intended owner of the schema-private network, specifying a valid tablespace with adequate space.

    The following example creates a schema-private semantic network named `net1` owned by a database user named `rdfuser` using a tablespace named `rdf_tblspace`:

        EXECUTE SEM_APIS.CREATE_SEM_NETWORK('rdf_tblspace', network_owner=>'rdfuser', network_name=>'net1');
5.  Create a model.
    When you create a model, you specify the model name, the table to hold references to semantic data for the model, and the column of type SDO_RDF_TRIPLE_S in that table.

    The following command creates a model named `articles` in the `net1` schema-private network.

        EXECUTE SEM_APIS.CREATE_SEM_MODEL('articles', NULL, NULL, network_owner=>'rdfuser', network_name=>'net1');

After you create the model, you can insert triples into the model, as shown in the examples in [Semantic Data Examples (PL/SQL and Java)](rdf-semantic-graph-overview.md).

**Parent topic:** [Quick Start for Using Semantic Data](quick-start-using-rdf-data.md)
