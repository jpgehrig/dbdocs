## 2.2 Getting Started with Semantic Data in an MDSYS-Owned Network

1.  Create a tablespace for the system tables. You must be connected as a user with appropriate privileges to create the tablespace. The following example creates a tablespace named `rdf_tblspace`:
        CREATE TABLESPACE rdf_tblspace
         DATAFILE 'rdf_tblspace.dat' SIZE 1024M REUSE
         AUTOEXTEND ON NEXT 256M MAXSIZE UNLIMITED
         SEGMENT SPACE MANAGEMENT AUTO;
2.  Create an MDSYS-owned semantic network.
    Creating a semantic network adds semantic data support to an Oracle database. You must create a semantic network as a user with DBA privileges.

    The following example creates a MDSYS-owned semantic network:

        EXECUTE SEM_APIS.CREATE_SEM_NETWORK('rdf_tblspace');
3.  Create a database user under whose schema you will manage your semantic data and grant the necessary privileges to the database user. You must be connected as a user with appropriate privileges to create the database user.
    The following example creates a database user `rdfuser` and grants the necessary privileges to `rdfuser`:
        CREATE USER rdfuser
        IDENTIFIED BY <password-for-rdfuser>
        QUOTA 5G ON rdf_tblspace;

        GRANT CONNECT, RESOURCE, CREATE VIEW TO rdfuser;
4.  Connect as the database user.
        CONNECT rdfuser/<password-for-rdfuser>

    **Note:**

    You must not perform the following steps while connected as SYS, SYSTEM, or MDSYS.
5.  Create an application table to store references to the semantic data and manage privileges for insert, update and delete operations. (You do not need to be connected as a user with DBA privileges for this step and the remaining steps.)
    This table must contain a column of type `SDO_RDF_TRIPLE_S`, which will contain references to all data associated with a single model.

    The following example creates a table named `articles_rdf_data` with one column to hold the data for triples:

        CREATE TABLE articles_rdf_data (triple SDO_RDF_TRIPLE_S) COMPRESS;
6.  Create a model.
    When you create a model, you must specify the model name, the table to hold references to semantic data for the model, and the column of type SDO_RDF_TRIPLE_S in that table.

    The following command creates a model named `articles` in the MDSYS-owned network, which will use the table created in the preceding step.

        EXECUTE SEM_APIS.CREATE_SEM_MODEL('articles', 'articles_rdf_data', 'triple');

After you create the model, you can insert triples into the model, as shown in the examples in [Semantic Data Examples (PL/SQL and Java)](rdf-semantic-graph-overview.md).

**Note:**

You must omit the `network_owner` and `network_name` arguments in the [Semantic Data Examples (PL/SQL and Java)](rdf-semantic-graph-overview.md) when using an MDSYS-owned semantic network.

**Parent topic:** [Quick Start for Using Semantic Data](quick-start-using-rdf-data.md)
