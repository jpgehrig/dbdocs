Oracle Data Provider for Microsoft .NET (ODP.NET) is an implementation of a data provider for Oracle Database. It uses Oracle native APIs to offer fast and reliable access to Oracle data and features from any .NET application.

It also uses and inherits classes and interfaces available in the Microsoft .NET Framework Class Library. ODP.NET supports the following LOB data types natively with .NET: `BLOB`, `CLOB`, `NCLOB`, and `BFILE`.

- Oracle XML DB and ODP.NET XML
  ODP.NET supports XML data natively in the database, through Oracle XML DB.
- Using XMLType Data with ODP.NET
  An example illustrates passing `XMLType` data from the database to .NET

**Parent topic:** [XMLType APIs](XMLType-APIs.md)

### 15.1 Oracle XML DB and ODP.NET XML

ODP.NET supports XML data natively in the database, through Oracle XML DB.

ODP.NET:

- Stores XML data natively in Oracle Database as `XMLType`.

- Accesses relational and object-relational data as XML data from Oracle Database to a Microsoft .NET environment, and processes the XML using Microsoft .NET framework.

- Saves changes to the database server using XML data.

- Provides the following XML-specific classes:

  - `OracleXmlType`

  - `OracleXmlStream`

  - `OracleXmlQueryProperties`

  - `OracleXmlSaveProperties`

- Enhances classes `OracleCommand`, `OracleConnection`, and `OracleDataReader`.

**Parent topic:** Oracle XML DB and Oracle Data Provider for .NET

### 15.2 Using XMLType Data with ODP.NET

An example illustrates passing `XMLType` data from the database to .NET

Example 15-1 retrieves `XMLType` data from the database to .NET and outputs the results:

**See Also:**

[Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featXML.md) for complete information about Oracle .NET support for Oracle XML DB.

Example 15-1 Retrieve XMLType Data to .NET

    //Create OracleCommand and query XMLType
    OracleCommand xmlCmd = new OracleCommand();
    poCmd.CommandText = "SELECT po FROM po_tab";
    poCmd.Connection = conn;
    // Execute OracleCommand and output XML results to an OracleDataReader
    OracleDataReader poReader = poCmd.ExecuteReader();
    // ODP.NET native XML data type object from Oracle XML DB
    OracleXmlType poXml;
    string str = ""; //read XML results
    while (poReader.Read())
    {
      // Return OracleXmlType object of the specified XmlType column
      poXml = poReader.GetOracleXmlType(0);
      // Concatenate output for all the records
      str = str + poXml.Value;
    } //Output XML results to the screen
    Console.WriteLine(str);

**Parent topic:** Oracle XML DB and Oracle Data Provider for .NET
