A data dictionary is a collection of information about the database objects that were created by various users of the system.

Most database systems have some form of data dictionary. For a relational database, a data dictionary is a set of tables and views that contain information about the data in the database. This information includes information about the users who are using the system and about the objects that they created (such as tables, views, and triggers). Almost all data dictionaries (regardless of the database system) contain the same information, but each database system organizes the information differently.

For example, the `ALL_CATALOG` Oracle data dictionary view gives a list of tables, views, and sequences in the database. It has three columns: the first is called `OWNER`, and it is the name of the owner of the object; the second is called `TABLE_NAME`, and it is the name of the object; and the third is called `TABLE_TYPE`, and it is the data type. This field has value `TABLE`, `VIEW`, `SEQUENCE` and so forth depending on the object type. However, in Sybase, the same information is stored in two tables called `sysusers` and `sysobjects` whose column names are different from those of the Oracle `ALL_CATALOG` table. Additionally, in Oracle Database, the table type is a string with a value such as `TABLE` or `VIEW`. With Sybase, it is a letter, for example, `U` means user table; `S` means system table; `V` means view, and so forth.

If the client program requires information from the table `ALL_CATALOG` on a Sybase system, it sends a query referencing `ALL_CATALOG@``database_link` to a gateway. Heterogeneous Services translates this query to an appropriate query on `systables` and then sends the translated query to the Sybase system, for example:

    SELECT SU."name" OWNER, SO."name" TABLE_NAME,
       DECODE(SO."type", 'U ','TABLE', 'S ', 'TABLE', 'V ', 'VIEW')
    TABLE_TYPE
    FROM "dbo"."sysusers"@remote_db  SU, "dbo"."sysobjects"@remote_db SO
    WHERE SU."uid" = SO."uid" AND
       (SO."type" = 'V' OR SO."type" = 'S' OR SO."type" = 'U');

To relay the translation of a query on an Oracle data dictionary table to the equivalent one on the non-Oracle system data dictionary table, Heterogeneous Services needs data dictionary translations for that non-Oracle system. A data dictionary translation is a view definition (essentially a `SELECT` statement) of one or more non-Oracle system data dictionary tables that look like the Oracle data dictionary table, with the same column names and the same formatting. Most data dictionary translations are not as simple as the preceding example. Often, the information is scattered over many tables, and the data dictionary translation is a complex join of those tables.

In some cases, an Oracle data dictionary table does not have a translation because the information does not exist on the non-Oracle system. In such cases, the gateway must not upload a translation, or the gateway might implement an alternative approach called mimicking. If the gateway mimics a data dictionary table, it informs Heterogeneous Services, and Heterogeneous Services will get the description of the data dictionary table by querying the local database. When asked to retrieve data, it will report that no rows were selected.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)
