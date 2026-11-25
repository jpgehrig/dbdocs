These topics describe the components of Oracle OLAP Provider for OLE DB (the provider) and how they are used to develop OLE DB for OLAP applications.

- Using Oracle OLAP Provider for OLE DB

- Sessions

- Schema Information

- Provider-Specific Properties

- MDX Execution

- Result Set

- Unicode Support

- Error Message Information

### Using Oracle OLAP Provider for OLE DB

To use any provider, the application must be able to uniquely identify it. The identification process differs depending on whether OLE DB or ADO MD is used to invoke the provider.

#### OLE DB

A class ID (CLSID) uniquely identifies an OLE DB provider. The macro `CLSID_OraOLEDBOLAP`, which is defined in `OraOLEDBOLAP.h`, defines the CLSID for OraOLEDB OLAP. The `CoCreateInstance()` API uses this macro as a parameter to create an instance of the provider's data source object and to obtain an interface pointer to it, as shown in the following code snippet:

    #include <OraOLEDBOLAP.h>

    ...
    HRESULT hr;
    IDBInitialize *pIDBInitialize;
    hr = CoCreateInstance(CLSID_OraOLEDBOLAP, NULL, CLSCTX_INPROC_SERVER,
         IID_IDBInitialize, (void**)&pIDBInitialize);

To use the OLE DB services (client cursor, connection pooling, and so on) in conjunction with OraOLEDB OLAP, invoke the following APIs instead:

    #include <OraOLEDBOLAP.h>

    ...
    HRESULT hr;
    IDataInitialize *pIDataInitialize;
    IDBInitialize *pIDBInitialize;

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, NULL, CLSCTX_INPROC_SERVER,
         IID_IDataInitialize,(void**)&pIDataInitialize);
    hr = pIDataInitialize->CreateDBInstance(CLSID_OraOLEDBOLAP, NULL,
         CLSCTX_INPROC_SERVER,NULL, IID_IDBInitialize,(IUnknown**)
         &pIDBInitialize);

#### ADO MD

To use a particular OLE DB for OLAP provider through ADO MD, a Program ID (ProgID) must be supplied as a value for the "`Provider`" connection string attribute. Set the provider value to "`OraOLEDB.OLAP`" as shown in the following code snippet:

    Dim cat As New ADOMD.Catalog
    ...
    cat.ActiveConnection = "Provider=OraOLEDB.OLAP;" & _
      "User Id=sh;Password=sh;Data Source=oracle;"

When ADO MD is used, OLE DB Services are automatically enabled.

#### Connecting to Oracle Database

OraOLEDB OLAP supports connections to Oracle databases. In most cases, the `User` `Id`, `Password`, and the `Data` `Source` are required to establish a connection. The data source is not required when connecting to a local database. However, when connecting to a remote database, the data source must be supplied and set to the appropriate Oracle Net Service Name, which should be included as an alias in the `tnsnames.ora` file.

##### OLE DB

For an OLE DB application to connect to an Oracle database, a consumer typically sets the following properties of the `DBPROPSET_DBINIT` property set:

- `DBPROP_AUTH_USERNAME`

- `DBPROP_AUTH_PASSWORD`

- `DBPROP_INIT_DATABASE`

##### ADO MD

For ADO MD applications, the username, password, and the data source are set within the connection string, as in the following example:

    Dim cat As New ADOMD.Catalog
    ...
    cat.ActiveConnection = "Provider=OraOLEDB.OLAP;" & _
      "User Id=<userid>;Password=<password>;Data Source=oracle;"

**See Also:**

[Oracle Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md) for more information

#### Provider-Specific Connection String Attributes

The following is a list of Oracle OLAP Provider for OLE DB provider-specific connection string attributes:

- `OSAuthent` - Operating System Authentication

  This feature enables operating system users to connect to an Oracle database.

  To enable operating system users to connect to the database, either:

  - Set the `OSAuthent` connection string attribute to `"1"`

    or

  - Set the `User` `Id` connection string attribute to `"/"`.

  To disable operating system users from connecting to the database:

  - Set the `OSAuthent` connection string attribute to `"0"`.

- `PwdChgDlg` - Password Change Dialog

  This feature enables the provider to display a password change dialog box for non-console applications during logon if the password has expired.

  To enable the dialog box to be displayed in the event of a password expiration:

  - Set the `PwdChgDlg` connection string attribute to `"1"`.

  To disable the dialog box from displaying in the event of a password expiration:

  - Set the `PwdChgDlg` connection string attribute to `"0"`

- `PreserveMaxPrecision` - Preserve Maximum Precision

  This feature allows the application to specify whether the maximum precision of `NUMBER` and `FLOAT` column values are preserved. If this feature is enabled, the provider preserves the maximum precision of the column values by fetching them as an Oracle native type. If this feature is disabled, the provider fetches the column values as C native types, which can cause some precision loss based on the limitations of the C native type. However, this approach provides better performance than fetching numeric data as an Oracle native type.

  To preserve maximum precision of `NUMBER` and `FLOAT` column values:

  - Set the `PreserverMaxPrecision` connection string attribute to `"1"`.

  To disable preservation of maximum precision for `NUMBER` and `FLOAT` column values:

  - Set the `PreserverMaxPrecision` connection string attribute to `"0"`

##### Default Connection String Attribute Values

The provider obtains the default attribute values for provider-specific connection string attributes from the `\\HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE \OLEDBOLAP` registry key. If the provider-specific connection string attributes are not set in the connection string, the values specified in the registry are used. If these attributes are set in the connection string, the specified values override the default values set in the registry.

Changing the registry default values can affect all OraOLEDB OLAP applications if they do not override the default attribute values within the connection string.

**Note:**

The provider only reads the registry values once at load time, so changes to the registry values do not affect applications that are already running.

##### OLE DB

To set any provider-specific connection string attributes from an OLE DB application, the `DBPROP_INIT_PROVIDERSTRING` property is used. To set more than one provider-specific connection string attribute, separate the attribute value pair with a semi-colon. To enable both `OSAuthent` and `PwdChgDlg`, for example, the OLE DB application can set the `DBPROP_INIT_PROVIDERSTRING` property to `"OSAuthent=1;PwdChgDlg=1;PreserveMaxPrecision=1"`.

##### ADO MD

ADO MD applications can set these provider-specific attribute values in the connection string along with the username, password, and data source, as in the following code snippet:

    Dim cat As New ADOMD.Catalog
    ...
    cat.ActiveConnection = "Provider=OraOLEDB.OLAP;" & _
        "User Id=<userid>;Password=<password>;Data Source=oracle;" & _
        "OSAuthent=1;PwdChgDlg=1;PreserveMaxPrecision=1"

**See Also:**

[Oracle Database Security Guide](../dbseg/introduction-to-oracle-database-security.md) for more information on password expiration and authenticating database users in Windows

### Sessions

OraOLEDB OLAP establishes connections and sessions to the Oracle database.

#### OLE DB

When the OLE DB data source object is instantiated, the provider establishes both a connection and a session for it. The first OLE DB session object that is instantiated from that data source object inherits the already established connection and session. Any subsequent OLE DB session objects created from the same OLE DB data source object establishes its own connection and session.

#### ADO MD

Whenever a new connection is established by an ADO MD object, a session is implicitly created for the connection.

### Schema Information

OraOLEDB OLAP supports both core OLE DB and OLE DB for OLAP schema rowsets as listed in this section. `DBSCHEMA` and `MDSCHEMA` macros can be used by OLE DB applications. `SchemaEnum` values, in parentheses, can be used by ADO MD applications.

#### Core OLE DB Schema Rowsets

- `DBSCHEMA_COLUMNS` (`adSchemaColumns`)

- `DBSCHEMA_SCHEMATA` (`adSchemaSchemata`)

- `DBSCHEMA_TABLES` (`adSchemaTables`)

- `DBSCHEMA_PROVIDER_TYPES` (`adSchemaProviderTypes`)

**See Also:**

"[Core OLE DB Schema Rowsets](core-provider.md)" for supported Schema Rowset columns

#### OLE DB for OLAP Schema Rowsets

- `MDSCHEMA_CUBES` (`adSchemaCubes`)

- `MDSCHEMA_DIMENSIONS` (`adSchemaDimensions`)

- `MDSCHEMA_FUNCTIONS` (`adSchemaFunctions`)

- `MDSCHEMA_HIERARCHIES` (`adSchemaHierarchies`)

- `MDSCHEMA_LEVELS` (`adSchemaLevels`)

- `MDSCHEMA_MEASURES` (`adSchemaMeasures`)

- `MDSCHEMA_MEMBERS` (`adSchemaMembers`)

- `MDSCHEMA_PROPERTIES` (`adSchemaProperties`)

- `MDSCHEMA_SETS` (`adSchemaSets`)

**See Also:**

"[OLE DB for OLAP Schema Rowsets](core-provider.md)" for supported Schema Rowset Columns

The unique names generated by OraOLEDB OLAP are consistent from one session to the next, if the underlying metadata does not change. Since dimensions can be shared between cubes, the same unique name can appear in multiple cubes. However, the provider guarantees that within the context of a cube, the unique name is genuinely unique.

### Provider-Specific Properties

OraOLEDB OLAP exposes the following provider-specific property sets and properties which can only be used by OLE DB applications.

- `DBPROPSET_ORAOLEDBOLAP_ROWSET` property set

  - `DBPROP_ORAOLEDBOLAP_ROWSETFETCHSIZE` property

- `DBPROPSET_ORAOLEDBOLAP_COMMAND` property set

  - `MDPROP_ORAOLEDBOLAP_CELLDATACACHE` property

  - `MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE` property

  - `MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION` property

For ADO MD applications, the default property values are used.

#### Provider-Specific Rowset Property

Table 2-1 lists the `DBPROP_ORAOLEDBOLAP_ROWSETFETCHSIZE` property which is part of the `DBPROPSET_ORAOLEDBOLAP_ROWSET` property set. `DBPROPSET_ORAOLEDBOLAP_ROWSET` belongs to the Rowset property group.

Table 2-1 Provider-Specific Rowset Property

| Property Name                         | Type     | R/W | Default Value |
|:--------------------------------------|:---------|:----|:--------------|
| `DBPROP_ORAOLEDBOLAP_ROWSETFETCHSIZE` | `VT_I4 ` | R/W | `262144`      |

The property can only be set when requesting a Schema Rowset using the `IDBSchemaRowset::GetRowset()` method. The property value specifies the maximum amount of data in bytes that OraOLEDB OLAP should fetch for each server round-trip made for a particular schema rowset.

#### Provider-Specific Command Properties

Provider-specific properties are part of the `DBPROPSET_ORAOLEDBOLAP_COMMAND` property set, which is part of the Rowset property set group.

Table 2-2 lists the provider-specific OLE DB command properties. All these properties take effect only if they are set before the execution of the MDX statement:

Table 2-2 Provider-Specific Command Properties

| Property Name                              | Type                     | R/W | Default Value    |
|:-------------------------------------------|:-------------------------|:----|:-----------------|
| `MDPROP_ORAOLEDBOLAP_CELLDATACACHE`        | `VT_BOOL`                | R/W | `VARIANT_TRUE`   |
| `MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE`       | `VT_ARRAY |`<br>`VT_I4 ` | R/W | `NULL`           |
| `MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION` | `VT_BOOL`                | R/W | `VARIANT_FALSE ` |

##### MDPROP_ORAOLEDBOLAP_CELLDATACACHE (Cell Data Cache)

OLE DB consumers can enable or disable caching of the result set data cell by setting the `MDPROP_ORAOLEDBOLAP_CELLDATACACHE` property to either `VARIANT_TRUE` or `VARIANT_FALSE`, respectively.

If cell data cache is enabled, the OraOLEDB OLAP provider tries to fetch, at least, the number of cells specified by the `MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE` for every server round-trip.

##### MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE (Cache Block Size)

OLE DB consumers can explicitly set the Cache Block Size by setting the `MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE` property with an array of `VT_I4` values.

If Cell Data Cache is enabled, the Cache Block Size determines the following:

- The shape of the cache block.

- The minimum amount of cell data the provider attempts to fetch for each server round-trip.

If Cache Block Size is set to its default value of `NULL`, the provider determines a reasonable Cache Block Size for the result set.

To override the default behavior, the OLE DB consumer must provide an array of four-byte integers. OraOLEDB OLAP uses the supplied array values to determine the shape of the Cache Block Size. The value at the `0`th index of the array determines the number of cells that are to be fetched from the X-axis (that is, `Axis(0)`). The value at the 1st index of the array determines the number of cells that are to be fetched from the Y-axis (that is, `Axis(1)`). In general, the value at the `n`th index of the array determines the number of cells that are to be fetched from `Axis(``n``)`.

If the length of the array is greater than the actual number of axes that exist on the result set, then the extra values are ignored. However, if the length of the array is less than the actual number of axes that exist on the result set, the provider populates the missing values with reasonable values.

##### MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION (Preserve Maximum Precision)

OLE DB consumers can choose to either preserve maximum precision or maximize performance when fetching numeric cell data by setting the `MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION` property to either `VARIANT_TRUE` or `VARIANT_FALSE`, respectively.

This property can also be set by using the `PreserveMaxPrecision` connection string attribute which overrides the registry value.

All the commands created from that connection inherit the value specified in the connection string (or the registry, if it is set there). The `MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION` property exposed on the command object allows OLE DB consumers to override this inherited value on a particular command object.

##### OLE DB Example

    ...

      HRESULT             hr              = S_OK;
      ICommandText       *pICmdText       = NULL;
      ICommandProperties *pICmdProperties = NULL;
      IMDDataset         *pIMDDataset     = NULL:
      long               *px              = NULL;
      SAFEARRAY          *psa             = NULL;
      SAFEARRAYBOUND      rgsabound[1];
      DBPROPSET           dbPropSets[1];
      DBPROP              dbProp[3];

      ...

      hr = pIDBCreateCmd->CreateCommand(NULL, IID_ICommandText,
              (IUnknown **)&pICmdText);

      hr = pICmdText->SetCommandText(DBGUID_DEFAULT, pCmdText);

      hr = pICmdText->QueryInterface(IID_ICommandProperties,
               (void**)&pICmdProperties);

      // Create the SAFEARRAY
      rgsabound[0].lLbound = 0;
      rgsabound[0].cElements = 3;
      psa = SafeArrayCreate(VT_I4, 1, rgsabound);

      // Get a pointer to the elements of the array.
      hr = SafeArrayAccessData(psa, (void HUGEP* FAR*)&px);

      // Create an array for a cache block size of {20, 40, 1}
      //   that will fetch 800 cells for each server round-trip
      px[0] = 20; // 20 coordinates from Axis(0)
      px[1] = 40; // 40 coordinates from Axis(1)
      px[2] = 1;  // 1 coordinate from Axis(2)

      dbPropSets[0].rgProperties    = &dbProp[0];
      dbPropSets[0].guidPropertySet = DBPROPSET_ORAOLEDBOLAP_COMMAND;
      dbPropSets[0].cProperties     = 3;

      dbProp[0].dwPropertyID        = MDPROP_ORAOLEDBOLAP_CELLDATACACHE;
      dbProp[0].dwOptions           = DBPROPOPTIONS_OPTIONAL;
      dbProp[0].colid               = DB_NULLID;
      V_VT(&(dbProp[0].vValue))     = VT_BOOL;
      dbProp[0].vValue.boolVal      = VARIANT_TRUE;

      dbProp[1].dwPropertyID        = MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE;
      dbProp[1].dwOptions           = DBPROPOPTIONS_OPTIONAL;
      dbProp[1].colid               = DB_NULLID;
      V_VT(&(dbProp[1].vValue))     = VT_ARRAY | VT_I4;
      dbProp[1].vValue.parray       = psa;

      dbProp[2].dwPropertyId    = MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION;
      dbProp[2].dwOptions       = DBPROPOPTIONS_OPTIONAL;
      dbProp[2].colid           = DB_NULLID;
      V_VT(&(dbProp[2].vValue)) = VT_BOOL;
      dbProp[2].vValue.boolVal  = VARIANT_FALSE;
      hr = pICmdProperties->SetProperties(1, dbPropSets);

      SafeArrayUnaccessData(psa);
      SafeArrayDestroy(psa);

      // Execute the MDX statement
      hr = pICmdText->Execute(NULL, IID_IMDDataset, NULL, NULL,
               (IUnknown **)&pIMDDataset);

      ...

##### Caching Behavior

For every `IMDDataset::GetCellData()` invocation, the provider checks to see whether all requested cells are in the cache or not. If all the requested cells are in the cache, the cell data is returned without incurring a server round-trip. If there are any cells that must be fetched from the database to satisfy the request, the provider incurs a server round-trip and fetches at least the number of cells specified by the Cache Block Size.

If a cell retrieval request by the application spans multiple cache blocks, the provider only incurs a single server round-trip to fetch all the blocks.

##### Performance

A typical spreadsheet-like OLAP application displays a finite set of data on a grid of C columns and R rows. For such applications, the Cache Block Size should be set to at least `{C,` `R`, `1,` `1,...}` so that the initial grid display does not incur more than one server round-trip. With this approach, additional server-round-trips are only required when the application user requests data beyond the initial C columns and R rows.

If users typically request data beyond these initial C columns and R rows, a Cache Block Size that is slightly larger than `{C,` `R,` `1,` `1,...}` (for example, `{C * 2,` `R` `*` `2,` `1,` `1,...}`) can enhance performance. However, unnecessarily using a large Cache Block Size may complicate the fetch request and require more processing time on the server-side.

### MDX Execution

OraOLEDB OLAP supports MDX statements only.

#### MDX Keywords

OraOLEDB OLAP supports a collection of MDX keywords which are provided in the appendix.

**See Also:**

"[MDX Keywords](core-provider.md)" for a detailed keyword list

#### MDX Operators

OraOLEDB OLAP supports the following MDX operators:

| Operator | Description              |
|:---------|:-------------------------|
| `*`      | cross join operator      |
| `<`      | less than                |
| `<=`     | less than or equal to    |
| `>`      | greater than             |
| `>=`     | greater than or equal to |
| `<>`     | not equal to             |
| `=`      | equal to                 |

### Result Set

The dataset represents the result set from the execution of a MDX statement. Consumers can obtain axis information as well as cell data from the dataset.

#### Cell Properties

OraOLEDB OLAP supports the following cell properties:

- `VALUE`

- `FORMATTED_VALUE`

  OraOLEDB OLAP uses the `FORMAT_STRING`, `VALUE`, and user default-locale identifier to generate the `FORMATTED_VALUE`. The `FORMATTED_VALUE` is not affected by any Oracle NLS parameters.

- `CELL_ORDINAL`

- `FORMAT_STRING`

### Unicode Support

Oracle OLAP Provider for OLE DB supports the Unicode character set, enabling consumers to retrieve data in various languages on the same client computer. It can be especially useful in creating global Internet applications supporting as many languages as the Unicode standard entails. For example, you can write a single Active Server Page (ASP) that accesses an Oracle database to dynamically generate contents in Japanese, Arabic, English, and Thai.

#### Types of Unicode Encoding

The Oracle databases store the Unicode data in the UTF8 encoding scheme, which is an ASCII compatible multibyte encoding of Unicode. Supported Microsoft operating system use the UCS2 encoding, which is a 2-byte fixed width encoding scheme. OraOLEDB OLAP transparently converts the data between the two encoding schemes allowing the consumers to deal with only UCS2.

**Note:**

The Unicode support is transparent to ADO MD consumers. OLE DB consumers using C/C++ need to explicitly specify `DBTYPE_WSTR` in their datatype bindings when Unicode data in involved.

#### Unicode Support Setup

In order to prevent any data loss, the database character set should be UTF8. Other than this, there is no other setup required for the Unicode support.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md)

- [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

- "[Datatype Mappings](oledb-info.md)"

### Error Message Information

OraOLEDB OLAP supports extended error information. The mechanism to obtain this information differs based on whether OLE DB or ADO MD is used to invoke OraOLEDB OLAP.

#### OLE DB

OLE DB and COM objects report errors through the `HRESULT` return code of the object member functions. An OLE/COM `HRESULT` is a bit-packed structure. OLE DB provides macros that dereference structure members. Oracle OLAP Provider for OLE DB exposes `IErrorLookup` to retrieve information about an error.

All objects support extended error information. For this, the consumer must instantiate the OLE DB Extended Error object followed by calling the method `GetErrorDescription()` to get the error text.

    // Instantiate OraOLEDBOLAPErrorLookup and obtain a pointer to its
    //  IErrorLookup interface
    IErrorLookup *pErrorLookup = NULL;
    CoCreateInstance(CLSID_OraOLEDBOLAPErrorLookup, NULL, CLSCTX_INPROC_SERVER,
                     IID_IErrorLookup, (void **)&pIErrorLookup)
    //Call the method GetErrorDescription() to get the full error text
    pIErrorLookup->GetErrorDescription()

#### ADO MD

For ADO MD users, the generic `Error` object can be used to fetch error information:

    Dim cat As New ADOMD.Catalog

    Sub Connect()

      On Error GoTo ErrorHandler

      cat.ActiveConnection = "Provider=OraOLEDB.OLAP;" & _
        "User Id=sh;Password=sh;Data Source=oracle;"
      Exit Sub

      ErrorHandler:
        Debug.Print Err.Description
    End Sub
