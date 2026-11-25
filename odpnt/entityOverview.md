ODP.NET 11.2.0.3.0 and higher includes support for the ADO.NET Entity Framework and LINQ to Entities. ODP.NET also supports Entity SQL.

Entity Framework is a framework for providing object-relational mapping service on data models. Entity Framework addresses the impedance mismatch between the relational database format and the client's preferred object format.

Entity Framework and LINQ provides productivity benefits for the .NET developer. It abstracts the database's data model from the application's data model. Working with object-relational data becomes easier with Entity Framework's tools. Oracle's integration with Entity Framework and LINQ enables Oracle .NET developers to take advantage of all these productivity benefits.

**Note:**

- Entity Framework and LINQ to Entities support is included in ODP.NET for .NET Framework 4. ODP.NET for .NET Framework 2.0 does not support the ADO.NET Entity Framework and LINQ to Entities.

- Code First is supported starting with Entity Framework 6 and higher.

- Binding scalar parameters is supported with ODP.NET and Entity Framework. In Entity Framework, parameter binding by name is supported. Binding by position is not supported.

Entity data models can be generated from Oracle database schemas. Schemas can be generated from entity data models. These Oracle entity data models can be queried and manipulated using Visual Studio and ODP.NET. Oracle supports Code First, Database First, and Model First modeling approaches. Specifying filters on the Visual Studio Server Explorer data connection enables the Entity Data Model Wizard to also filter Oracle database objects that are fetched and displayed.

LINQ to Entities can perform queries on the Oracle Database using ODP.NET, including using LINQ to Entities built-in functions. `INSERT`s, `UPDATE`s, and `DELETE`s can be executed using Oracle stored procedures, or by using the `ObjectContext` `SaveChanges` method.

ODP.NET supports function import of Oracle stored procedures that Entity Framework can then execute. These Oracle function imports can return a collection of scalar, complex, and entity types, including returning an Oracle implicit result set as an entity type. Implicit result set binding is supported using Oracle `REF CURSOR.`

**See Also:**

- [Implicit REF CURSOR Binding](featImplRefCursor.md).

- For a tutorial on how to use Entity Framework, Language Integrated Query (LINQ), and generate Data Definition Language (DDL) scripts using Model First, refer to:

  [`http://www.oracle.com/webfolder/technetwork/tutorials/obe/db/dotnet/EntityFrameworkOBE/EntityFrameworkOBE.htm`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=otn_entityframework_obe)
