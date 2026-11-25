This chapter describes how to retrieve metadata about result sets or the database as a whole.

This chapter contains these topics:

- Overview of Metadata

- Using Identity Column Metadata

- About Describing Database Metadata

- Attribute Reference Information

### 6.1 Overview of Metadata

Database objects have various attributes that describe them; you can obtain information about a particular schema object by performing a `DESCRIBE` operation. The result can be accessed as an object of the `Metadata` class by passing object attributes as arguments to the various methods of the `Metadata` class.

You can perform an explicit `DESCRIBE` operation on the database as a whole, on the types and properties of the columns contained in a `ResultSet` class, or on any of the following schema and subschema objects, such as tables, types, sequences, views, type attributes, columns, procedures, type methods, arguments, functions, collections, results, packages, synonyms, and lists

You must specify the type of the attribute you are looking for. By using the `getAttributeCount()`, `getAttributeId()`, and `getAttributeType()` methods of the `MetaData` class, you can scan through each available attribute.

All `DESCRIBE` information is cached until the last reference to it is deleted. Users are in this way prevented from accidentally trying to access `DESCRIBE` information that is freed.

You obtain metadata by calling the `getMetaData()` method on the `Connection` class in case of an explicit describe, or by calling the `getColumnListMetaData()` method on the `ResultSet` class to get the metadata of the result set columns. Both methods return a `MetaData` object with the describing information. The `MetaData` class provides the `get``xxx``()` methods to access this information.

**See Also:**

[Table 13-27](metadata-class.md)

When performing `DESCRIBE` operations, be aware of the following issues:

- The `ATTR_TYPECODE` returns type codes that represent the type supplied when you created a new type by using the `CREATE` `TYPE` statement. These type codes are of the enumerated type `TypeCode`, which are represented by `OCCI_TYPECODE` constants. Internal PL/SQL types (boolean, indexed table) are not supported

- The `ATTR_DATA_TYPE` returns types that represent the data types of the database columns. These values are of enumerated type `Type`. For example, `LONG` types return `OCCI_SQLT_LNG` types.

### 6.2 Using Identity Column Metadata

Starting with Oracle Database Release 12c, columns may be created as identity columns. When new rows are inserted into tables, the values for these columns are generated automatically.

This feature adds a new `ColumnAttrId enum` to the [MetaData Class](metadata-class.md) (see [Table 13-27](metadata-class.md)), and an overloaded form of [getBoolean()](metadata-class.md) method in the [MetaData Class](metadata-class.md). Example 6-1 shows how to use this feature.

For more information, see [Oracle Database SQL Translation and Migration Guide](../drdaa/intro-to-tools-and-products-supporting-migraiton.md), and [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md). Additionally, see the changes to [Oracle Database Reference](../refrn/release-changes.md):

- A new `IDENTITY_COLUMN` column for views [`ALL_TAB_COLUMNS`](../refrn/ALL_TAB_COLUMNS.md), [`DBA_TAB_COLUMNS`](../refrn/DBA_TAB_COLUMNS.md), [`USER_TAB_COLUMNS`](../refrn/USER_TAB_COLUMNS.md), [`ALL_TAB_COLS`](../refrn/ALL_TAB_COLS.md), [`DBA_TAB_COLS`](../refrn/DBA_TAB_COLS.md), and [`USER_TAB_COLS`](../refrn/USER_TAB_COLS.md)

- A new `HAS_IDENTITY` column for views [`ALL_TABLES`](../refrn/ALL_TABLES.md), [`DBA_TABLES`](../refrn/DBA_TABLES.md), and [`USER_TABLES`](../refrn/USER_TABLES.md)

- The new views [`ALL_TAB_IDENTITY_COLS`](../refrn/ALL_TAB_IDENTITY_COLS.md), [`DBA_TAB_IDENTITY_COLS`](../refrn/DBA_TAB_IDENTITY_COLS.md), and [`USER_TAB_IDENTITY_COLS`](../refrn/USER_TAB_IDENTITY_COLS.md), which display a table's identity column properties

Example 6-1 How to use Identity Column Metadata

    vector<MetaData> v1;
    MetaData metaData = conn->getMetaData(tableName);
    columnCount = metaData.getInt(MetaData::ATTR_NUM_COLS);
    cout << "Number of Columns : " << columnCount << endl;

    v1 =  metaData.getVector(MetaData::ATTR_LIST_COLUMNS);

    for(int i=0; i < v1.size(); i++) {
       MetaData md = v1[i];
       colNames[i] = md.getString(MetaData::ATTR_NAME);
       size[i] =  md.getInt(MetaData::ATTR_DATA_SIZE);
       precision[i] = md.getInt(MetaData::ATTR_PRECISION);
       scale[i] =  md.getInt(MetaData::ATTR_SCALE);

       if ( md.getBoolean(MetaData::ATTR_IS_NULL) )
          strcpy (isnull[i], "YES");
       else
          strcpy (isnull[i], "NO");

       if (md.getBoolean(MetaData::ATTR_COL_IS_IDENTITY))
          strcpy (isIdentity[i], "YES");
       else
          strcpy (isIdentity[i], "NO");

       if ( md.getBoolean(MetaData::ATTR_COL_IS_GEN_ALWAYS))
          strcpy (isGenAlways[i], "YES");
       else
          strcpy (isGenAlways[i], "NO");

       if (md.getBoolean(MetaData::ATTR_COL_IS_GEN_BY_DEF_ON_NULL))
          strcpy (isGenOnNull[i], "YES");
       else
          strcpy (isGenOnNull[i], "NO");
    }

    cout << "\n columnName  isNull   isIdentity   isGenAlways"  << "  isGenOnNull "
       << endl;
    cout <<"---------------------------------------------------------" << endl;

    for(int i=0; i < columnCount; ++i) {
       cout << "   " << colNames[i] << "  ";
       printf("%10s%10s%12s%12s\n", isnull[i], isIdentity[i], isGenAlways[i],
          isGenOnNull[i]);
    }

### 6.3 About Describing Database Metadata

Describing database metadata is equivalent to an explicit `DESCRIBE` operation. The object to describe must be an object in the schema. In describing a type, you call the `getMetaData()` method from the connection, passing the name of the object or a `RefAny` object. You must first initialize the environment in the `OBJECT` mode. The `getMetaData()` method returns an object of type `MetaData`. Each type of `MetaData` object has a list of attributes that are part of the describe tree. The describe tree can then be traversed recursively to point to subtrees that contain more information. More information about an object can be obtained by calling the `get``xxx``()` methods.

If you must construct a browser that describes the database and its objects recursively, then you can access information regarding the number of attributes for each object in the database (including the database), the attribute ID listing, and the attribute types listing. By using this information, you can recursively traverse the describe tree from the top node (the database) to the columns in the tables, the attributes of a type, the parameters of a procedure or function, and so on.

For example, consider the typical case of describing a table and its contents. You call the `getMetaData()` method from the connection, passing the name of the table to be described. The `MetaData` object returned contains the table information. Because you are aware of the type of the object you want to describe (table, column, type, collection, function, procedure, and so on), you can obtain the attribute list. You can retrieve the value into a variable of the type specified in the table by calling the corresponding `get``xxx``()` method.

Table 6-1 Attribute Groupings

| Attribute Type                                 | Description                                                            |
|:-----------------------------------------------|:-----------------------------------------------------------------------|
| Parameter Attributes                           | Attributes belonging to all elements                                   |
| Table and View Attributes                      | Attributes belonging to tables and views                               |
| Procedure, Function, and Subprogram Attributes | Attributes belonging to procedures, functions, and package subprograms |
| Package Attributes                             | Attributes belonging to packages                                       |
| Type Attributes                                | Attributes belonging to types                                          |
| Type Attribute Attributes                      | Attributes belonging to type attributes                                |
| Type Method Attributes                         | Attributes belonging to type methods                                   |
| Collection Attributes                          | Attributes belonging to collection types                               |
| Synonym Attributes                             | Attributes belonging to synonyms                                       |
| Sequence Attributes                            | Attributes belonging to sequences                                      |
| Column Attributes                              | Attributes belonging to columns of tables or views                     |
| Argument and Result Attributes                 | Attributes belonging to arguments / results                            |
| List Attributes                                | Attributes that designate the list type                                |
| Schema Attributes                              | Attributes specific to schemas                                         |
| Database Attributes                            | Attributes specific to databases                                       |

This section includes the following topic: Using Metadata (Code Examples).

#### 6.3.1 Using Metadata (Code Examples)

This section provides code examples for using metadata:

- Example 6-2

- Example 6-3

- Example 6-4

- Example 6-5

Example 6-2 How to Obtain Metadata About Attributes of a Simple Database Table

This example demonstrates how to obtain metadata about attributes of a simple database table:

    /* Create an environment and a connection to the HR database */
    .
    .
    /* Call the getMetaData method on the Connection object obtainedv*/
    MetaData emptab_metaData = connection->getMetaData(
          "EMPLOYEES", MetaData::PTYPE_TABLE);
    /* Now that you have the metadata information on the EMPLOYEES table,
       call the getxxx methods using the appropriate attributes */

    /* Call getString */
    cout<<"Schema:"<<
                  (emptab_metaData.getString(MetaData::ATTR_OBJ_SCHEMA))<<endl;

    if(emptab_metaData.getInt(
                  emptab_metaData::ATTR_PTYPE)==MetaData::PTYPE_TABLE)
       cout<<"EMPLOYEES is a table"<<endl;
    else
        cout<<"EMPLOYEES is not a table"<<endl;

    /* Call getInt to get the number of columns in the table */
    int columnCount=emptab_metaData.getInt(MetaData::ATTR_NUM_COLS);
    cout<<"Number of Columns:"<<columnCount<<endl;

    /* Call getTimestamp to get the timestamp of the table object */
    Timestamp tstamp = emptab_metaData.getTimestamp(MetaData::ATTR_TIMESTAMP);
    /* Now that you have the value of the attribute as a Timestamp object,
       you can call methods to obtain the components of the timestamp */
    int year;
    unsigned int month, day;
    tstamp.getData(year, month, day);

    /* Call getVector for attributes of list type, such as ATTR_LIST_COLUMNS */
    vector<MetaData>listOfColumns;
    listOfColumns=emptab_metaData.getVector(MetaData::ATTR_LIST_COLUMNS);

    /* Each of the list elements represents a column metadata,
       so now you can access the column attributes*/
    for (int i=0;i<listOfColumns.size();i++
    {
       MetaData columnObj=listOfColumns[i];
       cout<<"Column Name:"<<(columnObj.getString(MetaData::ATTR_NAME))<<endl;
       cout<<"Data Type:"<<(columnObj.getInt(MetaData::ATTR_DATA_TYPE))<<endl;
       .
       .
       /* and so on to obtain metadata on other column specific attributes */
    }

Example 6-3 How to Obtain Metadata from a Column Containing User-Defined Types

This example demonstrates how to obtain metadata from a column that contains user-defined types database table.

    /* Create an environment and a connection to the HR database */
    ...
    /* Call the getMetaData method on the Connection object obtained */
    MetaData custtab_metaData = connection->getMetaData(
          "CUSTOMERS", MetaData::PTYPE_TABLE);

    /* Have metadata information on CUSTOMERS table; call the getxxx methods */
    /* Call getString */
    cout<<"Schema:"<<(custtab_metaData.getString(MetaData::ATTR_OBJ_SCHEMA))
         <<endl;

    if(custtab_metaData.getInt(custtab_metaData::ATTR_PTYPE)==MetaData::PTYPE_TABLE)

       cout<<"CUSTOMERS is a table"<<endl;
    else
       cout<<"CUSTOMERS is not a table"<<endl;

    /* Call getVector to obtain list of columns in the CUSTOMERS table */
    vector<MetaData>listOfColumns;
    listOfColumns=custtab_metaData.getVector(MetaData::ATTR_LIST_COLUMNS);

    /* Assuming metadata for column cust_address_typ is fourth element in list*/
    MetaData customer_address=listOfColumns[3];

    /* Obtain the metadata for the customer_address attribute */
    int typcode = customer_address.getInt(MetaData::ATTR_TYPECODE);
    if(typcode==OCCI_TYPECODE_OBJECT)
       cout<<"customer_address is an object type"<<endl;
    else
       cout<<"customer_address is not an object type"<<endl;

    string objectName=customer_address.getString(MetaData::ATTR_OBJ_NAME);

    /* Now that you have the name of the address object,
       the metadata of the attributes of the type can be obtained by using
       getMetaData on the connection by passing the object name
    */
    MetaData address = connection->getMetaData(objectName);

    /* Call getVector to obtain the list of the address object attributes */
    vector<MetaData> attributeList =
          address.getVector(MetaData::ATT_LIST_TYPE_ATTRS);

    /* and so on to obtain metadata on other address object specific attributes */

Example 6-4 How to Obtain Object Metadata from a Reference

This example demonstrates how to obtain metadata about an object when using a reference to it:

    Type ADDRESS(street VARCHAR2(50), city VARCHAR2(20));
    Table Person(id NUMBER, addr REF ADDRESS);

    /* Create an environment and a connection to the HR database */
    .
    .
    /* Call the getMetaData method on the Connection object obtained */
    MetaData perstab_metaData = connection->getMetaData(
          "Person", MetaData::PTYPE_TABLE);

    /* Now that you have the metadata information on the Person table,
       call the getxxx methods using the appropriate attributes */
    /* Call getString */
    cout<<"Schema:"<<(perstab_metaData.getString(MetaData::ATTR_OBJ_SCHEMA))<<endl;

    if(perstab_metaData.getInt(perstab_metaData::ATTR_PTYPE)==MetaData::PTYPE_TABLE)
       cout<<"Person is a table"<<endl;
    else
       cout<<"Person is not a table"<<endl;

    /* Call getVector to obtain the list of columns in the Person table*/
    vector<MetaData>listOfColumns;
    listOfColumns=perstab_metaData.getVector(MetaData::ATTR_LIST_COLUMNS);

    /* Each of the list elements represents a column metadata,
       so now get the data type of the column by passing ATTR_DATA_TYPE
       to getInt */
    for(int i=0;i<numCols;i++)
    {
       int dataType=colList[i].getInt(MetaData::ATTR_DATA_TYPE);
       /* If the data type is a reference, get the Ref and obtain the metadata
          about the object by passing the Ref to getMetaData */
       if(dataType==SQLT_REF)
          RefAny refTdo=colList[i].getRef(MetaData::ATTR_REF_TDO);

       /* Now you can obtain the metadata about the object as shown
       MetaData tdo_metaData=connection->getMetaData(refTdo);

       /* Now that you have the metadata about the TDO, you can obtain the metadata
          about the object */
    }

Example 6-5 How to Obtain Metadata About a Select List from a ResultSet Object

This example demonstrates how to obtain metadata about a select list from a `ResultSet`.

    /* Create an environment and a connection to the database */
    ...
    /* Create a statement and associate it with a select clause */
    string sqlStmt="SELECT * FROM EMPLOYEES";
    Statement *stmt=conn->createStatement(sqlStmt);

    /* Execute the statement to obtain a ResultSet */
    ResultSet *rset=stmt->executeQuery();

    /* Obtain the metadata about the select list */
    vector<MetaData>cmd=rset->getColumnListMetaData();

    /* The metadata is a column list and each element is a column metaData */
    int dataType=cmd[i].getInt(MetaData::ATTR_DATA_TYPE);
    ...

The `getMetaData` method is called for the `ATTR_COLLECTION_ELEMENT` attribute only.

### 6.4 Attribute Reference Information

This section describes the following attributes that belong to schema and subschema objects:

- Parameter Attributes

- Table and View Attributes

- Procedure, Function, and Subprogram Attributes

- Package Attributes

- Type Attributes

- Type Attribute Attributes

- Type Method Attributes

- Collection Attributes

- Synonym Attributes

- Sequence Attributes

- Column Attributes

- Argument and Result Attributes

- List Attributes

- Schema Attributes

- Database Attributes

#### 6.4.1 Parameter Attributes

All elements have some attributes specific to that element and some generic attributes. Table 6-2 describes the attributes that belong to all elements:

Table 6-2 Attributes that Belong to All Elements

| Attribute         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Attribute Data Type |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_OBJ_ID`     | Object or schema ID                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | `unsigned int`      |
| `ATTR_OBJ_NAME`   | Object, schema, or database name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | `string`            |
| `ATTR_OBJ_SCHEMA` | Schema where object is located                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | `string`            |
| `ATTR_OBJ_PTYPE`  | Type of information described by the parameter. Possible values are:<br>`PTYPE_TABLE, `Table<br>`PTYPE_VIEW, `View<br>`PTYPE_PROC, `Procedure<br>`PTYPE_FUNC, `Function<br>`PTYPE_PKG, `Package<br>`PTYPE_TYPE, `Type<br>`PTYPE_TYPE_ATTR, `Attribute of a type<br>`PTYPE_TYPE_COLL, `Collection type information<br>`PTYPE_TYPE_METHOD, `A method of a type<br>`PTYPE_SYN, `Synonym<br>`PTYPE_SEQ, `Sequence<br>`PTYPE_COL, `Column of a table or view<br>`PTYPE_ARG, `Argument of a function or procedure<br>`PTYPE_TYPE_ARG, `Argument of a type method<br>`PTYPE_TYPE_RESULT, `Results of a method<br>`PTYPE_SCHEMA, `Schema<br>`PTYPE_DATABASE, `Database | `int`               |
| `ATTR_TIMESTAMP`  | The `TIMESTAMP` of the object this description is based on (Oracle DATE format).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | `Timestamp`         |

The sections that follow list attributes specific to different types of elements.

#### 6.4.2 Table and View Attributes

A parameter for a table or view (type `PTYPE_TABLE` or `PTYPE_VIEW`) has the following type-specific attributes described in Table 6-3:

Table 6-3 Attributes that Belong to Tables or Views

| Attribute           | Description                                                                                                                                                    | Attribute Data Type |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_OBJID`        | Object ID                                                                                                                                                      | `unsigned int`      |
| `ATTR_NUM_COLS`     | Number of columns                                                                                                                                              | `int`               |
| `ATTR_LIST_COLUMNS` | Column list (type `PTYPE_LIST`)                                                                                                                                | `vector<MetaData>`  |
| `ATTR_REF_TDO`      | `REF` to the object type that is being described                                                                                                               | `RefAny`            |
| `ATTR_IS_TEMPORARY` | Identifies whether the table or view is temporary                                                                                                              | `bool`              |
| `ATTR_IS_TYPED`     | Identifies whether the table or view is typed                                                                                                                  | `bool`              |
| `ATTR_DURATION`     | Duration of a temporary table. Values can be:<br>• `DURATION_SESSION` (session)<br>• `DURATION_TRANS` (transaction)<br>• `DURATION_NULL` (table not temporary) | `int`               |

The additional attributes belonging to tables are described in Table 6-4.

Table 6-4 Attributes Specific to Tables

| Attribute          | Description                                 | Attribute Data Type |
|:-------------------|:--------------------------------------------|:--------------------|
| `ATTR_DBA`         | Data block address of the segment header    | `unsigned int`      |
| `ATTR_TABLESPACE`  | Tablespace the table resides on             | `int`               |
| `ATTR_CLUSTERED`   | Identifies whether the table is clustered   | `bool`              |
| `ATTR_PARTITIONED` | Identifies whether the table is partitioned | `bool`              |
| `ATTR_INDEX_ONLY`  | Identifies whether the table is index only  | `bool`              |

#### 6.4.3 Procedure, Function, and Subprogram Attributes

A parameter for a procedure or function (type `PTYPE_PROC` or `PTYPE_FUNC`) has the type-specific attributes described in Table 6-5.

Table 6-5 Attributes that Belong to Procedures or Functions

| Attribute                | Description                                                        | Attribute Data Type |
|:-------------------------|:-------------------------------------------------------------------|:--------------------|
| `ATTR_LIST_ARGUMENTS`    | Argument list; refer to List Attributes .                          | `vector<MetaData>`  |
| `ATTR_IS_INVOKER_RIGHTS` | Identifies whether the procedure or function has invoker's rights. | `int`               |

The additional attributes belonging to package subprograms are described in Table 6-6.

Table 6-6 Attributes that Belong to Package Subprograms

| Attribute          | Description                                                                                                                                                                                      | Attribute Data Type |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_NAME`        | Name of procedure or function                                                                                                                                                                    | `string`            |
| `ATTR_OVERLOAD_ID` | Overloading ID number (relevant in case the procedure or function is part of a package and is overloaded). Values returned may be different from direct query of a PL/SQL function or procedure. | `int`               |

#### 6.4.4 Package Attributes

A parameter for a package (type `PTYPE_PKG`) has the type-specific attributes described in Table 6-7.

Table 6-7 Attributes that Belong to Packages

| Attribute                | Description                                         | Attribute Data Type |
|:-------------------------|:----------------------------------------------------|:--------------------|
| `ATTR_LIST_SUBPROGRAMS`  | Subprogram list; refer to List Attributes.          | `vector<MetaData>`  |
| `ATTR_IS_INVOKER_RIGHTS` | Identifies whether the package has invoker's rights | `bool`              |

#### 6.4.5 Type Attributes

A parameter for a type (type `PTYPE_TYPE`) has attributes described in Table 6-8.

Table 6-8 Attributes that Belong to Types

| Attribute                       | Description                                                                                                                      | Attribute Data Type |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_REF_TDO`                  | Returns the in-memory ref of the type descriptor object for the type, if the column type is an object type.                      | `RefAny`            |
| `ATTR_TYPECODE`                 | Type code. Can be:<br>• `OCCI_TYPECODE_OBJECT`<br>• `OCCI_TYPECODE_NAMEDCOLLECTION`                                              | `int`               |
| `ATTR_COLLECTION_TYPECODE`      | Type code of collection if type is collection; invalid otherwise. Can be:<br>• `OCCI_TYPECODE_VARRAY`<br>• `OCCI_TYPECODE_TABLE` | `int`               |
| `ATTR_VERSION`                  | A `NULL`-terminated string containing the user-assigned version                                                                  | `string`            |
| `ATTR_IS_FINAL_TYPE`            | Identifies whether this is a final type                                                                                          | `bool`              |
| `ATTR_IS_INSTANTIABLE_TYPE`     | Identifies whether this is an instantiable type                                                                                  | `bool`              |
| `ATTR_IS_SUBTYPE`               | Identifies whether this is a subtype                                                                                             | `bool`              |
| `ATTR_SUPERTYPE_SCHEMA_NAME`    | Name of the schema containing the supertype                                                                                      | `string`            |
| `ATTR_SUPERTYPE_NAME`           | Name of the supertype                                                                                                            | `string`            |
| `ATTR_IS_INVOKER_RIGHTS`        | Identifies whether this type is invoker's rights                                                                                 | `bool`              |
| `ATTR_IS_INCOMPLETE_TYPE`       | Identifies whether this type is incomplete                                                                                       | `bool`              |
| `ATTR_IS_SYSTEM_TYPE`           | Identifies whether this is a system type                                                                                         | `bool`              |
| `ATTR_IS_PREDEFINED_TYPE`       | Identifies whether this is a predefined type                                                                                     | `bool`              |
| `ATTR_IS_TRANSIENT_TYPE`        | Identifies whether this is a transient type                                                                                      | `bool`              |
| `ATTR_IS_SYSTEM_GENERATED_TYPE` | Identifies whether this is a system-generated type                                                                               | `bool`              |
| `ATTR_HAS_NESTED_TABLE`         | Identifies whether this type contains a nested table attribute                                                                   | `bool`              |
| `ATTR_HAS_LOB`                  | Identifies whether this type contains a `LOB` attribute                                                                          | `bool`              |
| `ATTR_HAS_FILE`                 | Identifies whether this type contains a `FILE` attribute                                                                         | `bool`              |
| `ATTR_COLLECTION_ELEMENT`       | Handle to collection element<br>Refer to Collection Attributes                                                                   | `MetaData`          |
| `ATTR_NUM_TYPE_ATTRS`           | Number of type attributes                                                                                                        | `unsigned int`      |
| `ATTR_LIST_TYPE_ATTRS`          | List of type attributes<br>Refer to List Attributes                                                                              | `vector<MetaData>`  |
| `ATTR_NUM_TYPE_METHODS`         | Number of type methods                                                                                                           | `unsigned int`      |
| `ATTR_LIST_TYPE_METHODS`        | List of type methods<br>Refer to List Attributes                                                                                 | `vector<MetaData>`  |
| `ATTR_MAP_METHOD`               | Map method of type<br>Refer to Type Method Attributes                                                                            | `MetaData`          |
| `ATTR_ORDER_METHOD`             | Order method of type; refer to Type Method Attributes                                                                            | `MetaData`          |

#### 6.4.6 Type Attribute Attributes

A parameter for an attribute of a type (type `PTYPE_TYPE_ATTR`) has the attributes described in Table 6-9.

Table 6-9 Attributes that Belong to Type Attributes

| Attribute           | Description                                                                                                                                                                                                                                                                                                                     | Attribute Data Type |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_DATA_SIZE`    | Maximum size of the type attribute. This length is returned in bytes and not characters for strings and raws. Returns `22` for `NUMBER`.                                                                                                                                                                                        | `int`               |
| `ATTR_TYPECODE`     | Type code                                                                                                                                                                                                                                                                                                                       | `int`               |
| `ATTR_DATA_TYPE`    | Data type of the type attribute                                                                                                                                                                                                                                                                                                 | `int`               |
| `ATTR_NAME`         | A pointer to a string that is the type attribute name                                                                                                                                                                                                                                                                           | `string`            |
| `ATTR_PRECISION`    | Precision of numeric type attributes. If the precision is nonzero and scale is `-127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply by `NUMBER`.                                                                                                        | `int`               |
| `ATTR_SCALE`        | Scale of numeric type attributes. If the precision is nonzero and scale is` -127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply as `NUMBER`.                                                                                                            | `int`               |
| `ATTR_TYPE_NAME`    | A string that is the type name. The returned value contains the type name if the data type is `SQLT_NTY` or `SQLT_REF`. If the data type is `SQLT_NTY`, then the name of the named data type's type is returned. If the data type is `SQLT_REF`, then the type name of the named data type pointed to by the `REF` is returned. | `string`            |
| `ATTR_SCHEMA_NAME`  | String with the schema name under which the type has been created                                                                                                                                                                                                                                                               | `string`            |
| `ATTR_REF_TDO`      | Returns the in-memory `REF` of the TDO for the type, if the column type is an object type.                                                                                                                                                                                                                                      | `RefAny`            |
| `ATTR_CHARSET_ID`   | Character set ID, if the type attribute is of a string or character type                                                                                                                                                                                                                                                        | `int`               |
| `ATTR_CHARSET_FORM` | Character set form, if the type attribute is of a string or character type                                                                                                                                                                                                                                                      | `int`               |
| `ATTR_FSPRECISION`  | The fractional seconds precision of a datetime or interval                                                                                                                                                                                                                                                                      | `int`               |
| `ATTR_LFPRECISION`  | The leading field precision of an interval                                                                                                                                                                                                                                                                                      | `int`               |

#### 6.4.7 Type Method Attributes

A parameter for a method of a type (type `PTYPE_TYPE_METHOD`) has the attributes described in Table 6-10.

Table 6-10 Attributes that Belong to Type Methods

| Attribute                     | Description                                                                                            | Attribute Data Type |
|:------------------------------|:-------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_NAME`                   | Name of method (procedure or function)                                                                 | `string`            |
| `ATTR_ENCAPSULATION`          | Encapsulation level of the method; can be:<br>• `OCCI_TYPEENCAP_PRIVATE`<br>• `OCCI_TYPEENCAP_PUBLIC)` | `int`               |
| `ATTR_LIST_ARGUMENTS`         | Argument list                                                                                          | `vector<MetaData>`  |
| `ATTR_IS_CONSTRUCTOR`         | Identifies whether the method is a constructor                                                         | `bool`              |
| `ATTR_IS_DESTRUCTOR`          | Identifies whether the method is a destructor                                                          | `bool`              |
| `ATTR_IS_OPERATOR`            | Identifies whether the method is an operator                                                           | `bool`              |
| `ATTR_IS_SELFISH`             | Identifies whether the method is selfish                                                               | `bool`              |
| `ATTR_IS_MAP`                 | Identifies whether the method is a map method                                                          | `bool`              |
| `ATTR_IS_ORDER`               | Identifies whether the method is an order method                                                       | `bool`              |
| `ATTR_IS_RNDS`                | Identifies whether "Read No Data State" is set for the method                                          | `bool`              |
| `ATTR_IS_RNPS`                | Identifies whether "Read No Process State" is set for the method                                       | `bool`              |
| `ATTR_IS_WNDS`                | Identifies whether "Write No Data State" is set for the method                                         | `bool`              |
| `ATTR_IS_WNPS`                | Identifies whether "Write No Process State" is set for the method                                      | `bool`              |
| `ATTR_IS_FINAL_METHOD`        | Identifies whether this is a final method                                                              | `bool`              |
| `ATTR_IS_INSTANTIABLE_METHOD` | Identifies whether this is an instantiable method                                                      | `bool`              |
| `ATTR_IS_OVERRIDING_METHOD`   | Identifies whether this is an overriding method                                                        | `bool`              |

#### 6.4.8 Collection Attributes

A parameter for a collection type (type `PTYPE_COLL`) has the attributes described in Table 6-11.

Table 6-11 Attributes that Belong to Collection Types

| Attribute           | Description                                                                                                                                                                                                                                                                                                                  | Attribute Data Type |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_DATA_SIZE`    | Maximum size of the type attribute. This length is returned in bytes and not characters for strings and raws. Returns `22` for `NUMBER`.                                                                                                                                                                                     | `int`               |
| `ATTR_TYPECODE`     | Typecode.                                                                                                                                                                                                                                                                                                                    | `int`               |
| `ATTR_DATA_TYPE`    | The data type of the type attribute.                                                                                                                                                                                                                                                                                         | `int`               |
| `ATTR_NUM_ELEMENTS` | Number of elements in an array; only valid for collections that are arrays.                                                                                                                                                                                                                                                  | `unsigned int`      |
| `ATTR_NAME`         | A pointer to a string that is the type attribute name                                                                                                                                                                                                                                                                        | `string`            |
| `ATTR_PRECISION`    | Precision of numeric type attributes. If the precision is nonzero and scale is` -127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply as `NUMBER`.                                                                                                     | `int`               |
| `ATTR_SCALE`        | Scale of numeric type attributes. If the precision is nonzero and scale is `-127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply a`s NUMBER`.                                                                                                         | `int`               |
| `ATTR_TYPE_NAME`    | String that is the type name. The returned value contains the type name if the data type is `SQLT_NTY` or `SQLT_REF`. If the data type is `SQLT_NTY`, then the name of the named data type's type is returned. If the data type is `SQLT_REF`, then the type name of the named data type pointed to by the `REF` is returned | `string`            |
| `ATTR_SCHEMA_NAME`  | String with the schema name under which the type has been created                                                                                                                                                                                                                                                            | `string`            |
| `ATTR_REF_TDO`      | Returns the in memory `REF` of the `TDO` for the type.                                                                                                                                                                                                                                                                       | `RefAny`            |
| `ATTR_CHARSET_ID`   | Typecode.                                                                                                                                                                                                                                                                                                                    | `int`               |
| `ATTR_CHARSET_FORM` | The data type of the type attribute.                                                                                                                                                                                                                                                                                         | `int`               |

#### 6.4.9 Synonym Attributes

A parameter for a synonym (type `PTYPE_SYN`) has the attributes described in Table 6-12.

Table 6-12 Attributes that Belong to Synonyms

| Attribute          | Description                                                                         | Attribute Data Type |
|:-------------------|:------------------------------------------------------------------------------------|:--------------------|
| `ATTR_OBJID`       | Object ID                                                                           | `unsigned int`      |
| `ATTR_SCHEMA_NAME` | Null-terminated string containing the schema name of the synonym translation        | `string`            |
| `ATTR_NAME`        | Null-terminated string containing the object name of the synonym translation        | `string`            |
| `ATTR_LINK`        | Null-terminated string containing the database link name of the synonym translation | `string`            |

#### 6.4.10 Sequence Attributes

A parameter for a sequence (type `PTYPE_SEQ`) has the attributes described in Table 6-13.

Table 6-13 Attributes that Belong to Sequences

| Attribute      | Description                                                                                                | Attribute Data Type |
|:---------------|:-----------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_OBJID`   | Object ID                                                                                                  | `unsigned int`      |
| `ATTR_MIN`     | Minimum value (in Oracle number format)                                                                    | `Number`            |
| `ATTR_MAX`     | Maximum value (in Oracle number format)                                                                    | `Number`            |
| `ATTR_INCR`    | Increment (in Oracle number format)                                                                        | `Number`            |
| `ATTR_CACHE`   | Number of sequence numbers cached; zero if the sequence is not a cached sequence (in Oracle number format) | `Number`            |
| `ATTR_ORDER`   | Identifies whether the sequence is ordered                                                                 | `bool`              |
| `ATTR_HW_MARK` | High-water mark (in Oracle number format)                                                                  | `Number`            |

#### 6.4.11 Column Attributes

A parameter for a column of a table or view (type `PTYPE_COL`) has the attributes described in Table 6-14.

Table 6-14 Attributes that Belong to Columns of Tables or Views

| Attribute           | Description                                                                                                                                                                                                                                                                                                                                                 | Attribute Data Type |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_DATA_SIZE`    | Maximum size of the column. This length is returned in bytes and not characters for strings and raws. Returns `22` for `NUMBER`..                                                                                                                                                                                                                           | `int`               |
| `ATTR_DATA_TYPE`    | The data type of the column.                                                                                                                                                                                                                                                                                                                                | `Type`              |
| `ATTR_NAME`         | Pointer to a string that is the column name.                                                                                                                                                                                                                                                                                                                | `string`            |
| `ATTR_PRECISION`    | Returns the precision.                                                                                                                                                                                                                                                                                                                                      | `int`               |
| `ATTR_SCALE`        | Scale of numeric columns. If the precision is nonzero and scale is `-127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then` NUMBER(p, s)` can be represented simply as `NUMBER`.                                                                                                                                                | `int`               |
| `ATTR_IS_NULL`      | Returns `FALSE` if null values are not permitted for the column.                                                                                                                                                                                                                                                                                            | `bool`              |
| `ATTR_TYPE_NAME`    | Returns a string that is the type name. The returned value contains the type name if the data type is `OCCI_SQLT_NTY` or `OCCI_SQLT_REF`. If the data type is `OCCI_SQLT_NTY`, then the name of the named data type's type is returned. If the data type is `OCCI_SQLT_REF`, then the type name of the named data type pointed to by the `REF` is returned. | `string`            |
| `ATTR_SCHEMA_NAME`  | Returns a string with the schema name under which the type has been created.                                                                                                                                                                                                                                                                                | `string`            |
| `ATTR_REF_TDO`      | The `REF` of the TDO for the type, if the column type is an object type.                                                                                                                                                                                                                                                                                    | `RefAny`            |
| `ATTR_CHARSET_ID`   | Character set ID for character column. If not set, the character set ID defaults to the character set ID set in the direct path context.                                                                                                                                                                                                                    | `int`               |
| `ATTR_CHARSET_FORM` | Character set form of the column. Setting this attribute specifies the use of the database or national character set on the client side.                                                                                                                                                                                                                    | `int`               |

#### 6.4.12 Argument and Result Attributes

A parameter for an argument or a procedure or function type (type `PTYPE_ARG`), for a type method argument (type `PTYPE_TYPE_ARG`), or for method results (type `PTYPE_TYPE_RESULT`) has the attributes described in Table 6-15.

Table 6-15 Attributes that Belong to Arguments / Results

| Attribute             | Description                                                                                                                                                                                                                                                                                                                                                                           | Attribute Data Type |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_NAME`           | Returns a pointer to a string which is the argument name                                                                                                                                                                                                                                                                                                                              | `string`            |
| `ATTR_POSITION`       | Position of the argument in the argument list. Always returns `0`.                                                                                                                                                                                                                                                                                                                    | `int`               |
| `ATTR_TYPECODE`       | Typecode.                                                                                                                                                                                                                                                                                                                                                                             | `int`               |
| `ATTR_DATA_TYPE`      | Data type of the argument.                                                                                                                                                                                                                                                                                                                                                            | `int`               |
| `ATTR_DATA_SIZE`      | Size of the data type of the argument. This length is returned in bytes and not characters for strings and raws. Returns` 22` for `NUMBER`.                                                                                                                                                                                                                                           | `int`               |
| `ATTR_PRECISION`      | Precision of numeric arguments. If the precision is nonzero and scale is `-127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply as `NUMBER`.                                                                                                                                                                    | `int`               |
| `ATTR_SCALE`          | Scale of numeric arguments. If the precision is nonzero and scale is `-127`, then it is a `FLOAT`; otherwise a `NUMBER(p, s)`. If precision is `0`, then `NUMBER(p, s)` can be represented simply as `NUMBER`.                                                                                                                                                                        | `int`               |
| `ATTR_LEVEL`          | Data type levels. This attribute always returns `0`.                                                                                                                                                                                                                                                                                                                                  | `int`               |
| `ATTR_HAS_DEFAULT`    | Indicates whether an argument has a default                                                                                                                                                                                                                                                                                                                                           | `int`               |
| `ATTR_LIST_ARGUMENTS` | The list of arguments at the next level (when the argument is of a record or table type)                                                                                                                                                                                                                                                                                              | `vector<MetaData>`  |
| `ATTR_IOMODE`         | Indicates the argument mode; valid values are:<br>• `0` for `IN` (`OCCI_TYPEPARAM_IN`)<br>• `1` for `OUT` (`OCCI_TYPEPARAM_OUT`)<br>• `2` for `IN/OUT` (`OCCI_TYPEPARAM_INOUT`)                                                                                                                                                                                                       | `int`               |
| `ATTR_RADIX`          | Returns a radix (if number type)                                                                                                                                                                                                                                                                                                                                                      | `int`               |
| `ATTR_IS_NULL`        | Returns `FALSE` if `NULL` values are not permitted for the column.                                                                                                                                                                                                                                                                                                                    | bool                |
| `ATTR_TYPE_NAME`      | Returns a string that is the type name (or the package name for local package types). The returned value contains the type name if the data type is `SQLT_NTY` or `SQLT_REF`. If the data type is `SQLT_NTY`, then the name of the named data type's type is returned. If the data type is `SQLT_REF`, then the type name of the named data type pointed to by the `REF` is returned. | `string`            |
| `ATTR_SCHEMA_NAME`    | For `SQLT_NTY` or `SQLT_REF`, returns a string with the schema name under which the type was created (or for local package types, the package name).                                                                                                                                                                                                                                  | `string`            |
| `ATTR_SUB_NAME`       | For `SQLT_NTY` or `SQLT_REF`, returns a string with the type name.                                                                                                                                                                                                                                                                                                                    | `string`            |
| `ATTR_LINK`           | For `SQLT_NTY` or `SQLT_REF`, returns a string with the database link name of the database on which the type exists. This can happen only for package-ocal types, when the package is remote.                                                                                                                                                                                         | `string`            |
| `ATTR_REF_TDO`        | Returns the `REF` of the TDO for the type, if the argument type is an object.                                                                                                                                                                                                                                                                                                         | `RefAny`            |
| `ATTR_CHARSET_ID`     | Returns the character set ID if the argument is of a string or character type.                                                                                                                                                                                                                                                                                                        | `int`               |
| `ATTR_CHARSET_FORM`   | Returns the character set form if the argument is of a string or character type.                                                                                                                                                                                                                                                                                                      | `int`               |

#### 6.4.13 List Attributes

A list type of attribute can be described for all the elements in the list. In case of a function argument list, position `0` has a parameter for return values (`PTYPE_ARG`).

The list is described iteratively for all the elements. The results are stored in a C++ `vector<MetaData>`. Call the `getVector()` method to describe list type of attributes. Table 6-16 displays the list attributes.

Table 6-16 Values for ATTR_LIST_TYPE

| Possible Values             | Description                          |
|:----------------------------|:-------------------------------------|
| `ATTR_LIST_COLUMNS`         | Column list                          |
| `ATTR_LIST_ARGUMENTS`       | Procedure or function arguments list |
| `ATTR_LIST_SUBPROGRAMS`     | Subprogram list                      |
| `ATTR_LIST_TYPE_ATTRIBUTES` | Type attribute list                  |
| `ATTR_LIST_TYPE_METHODS`    | Type method list                     |
| `ATTR_LIST_OBJECTS`         | Object list within a schema          |
| `ATTR_LIST_SCHEMAS`         | Schema list within a database        |

#### 6.4.14 Schema Attributes

A parameter for a schema type (type `PTYPE_SCHEMA`) has the attributes described in Table 6-17.

Table 6-17 Attributes Specific to Schemas

| Attribute           | Description                   | Attribute Data Type |
|:--------------------|:------------------------------|:--------------------|
| `ATTR_LIST_OBJECTS` | List of objects in the schema | `string`            |

#### 6.4.15 Database Attributes

A parameter for a database (type `PTYPE_DATABASE`) has the attributes described in Table 6-18.

Table 6-18 Attributes Specific to Databases

| Attribute                     | Description                                                                                                                                                                                                                                                                                                                                           | Attribute Data Type |
|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| `ATTR_VERSION`                | Database version                                                                                                                                                                                                                                                                                                                                      | `string`            |
| `ATTR_CHARSET_ID`             | Database character set ID from the server handle                                                                                                                                                                                                                                                                                                      | `int`               |
| `ATTR_NCHARSET_ID`            | Database native character set ID from the server handle                                                                                                                                                                                                                                                                                               | `int`               |
| `ATTR_LIST_SCHEMAS`           | List of schemas (type `PTYPE_SCHEMA`) in the database                                                                                                                                                                                                                                                                                                 | `vector<MetaData>`  |
| `ATTR_MAX_PROC_LEN`           | Maximum length of a procedure name                                                                                                                                                                                                                                                                                                                    | `unsigned int`      |
| `ATTR_MAX_COLUMN_LEN`         | Maximum length of a column name                                                                                                                                                                                                                                                                                                                       | `unsigned int`      |
| `ATTR_CURSOR_COMMIT_BEHAVIOR` | How a `COMMIT` operation affects cursors and prepared statements in the database; values are:<br>• `OCCI_CURSOR_OPEN` for preserving cursor state as before the commit operation<br>• `OCCI_CURSOR_CLOSED` for cursors that are closed on `COMMIT`, although the application can execute the statement for the second time without preparing it again | `int`               |
| `ATTR_MAX_CATALOG_NAMELEN`    | Maximum length of a catalog (database) name                                                                                                                                                                                                                                                                                                           | `int`               |
| `ATTR_CATALOG_LOCATION`       | Position of the catalog in a qualified table; values are:<br>• `OCCI_CL_START`<br>• `OCCI_CL_END`                                                                                                                                                                                                                                                     | `int`               |
| `ATTR_SAVEPOINT_SUPPORT`      | Identifies whether the database supports savepoints; values are:<br>• `OCCI_SP_SUPPORTED`<br>• `OCCI_SP_UNSUPPORTED`                                                                                                                                                                                                                                  | `int`               |
| `ATTR_NOWAIT_SUPPORT`         | Identifies whether the database supports the nowait clause; values are:<br>• `OCCI_NW_SUPPORTED`<br>• `OCCI_NW_UNSUPPORTED`                                                                                                                                                                                                                           | `int`               |
| `ATTR_AUTOCOMMIT_DDL`         | Identifies whether the autocommit mode is required for DDL statements; values are:<br>• `OCCI_AC_DDL`<br>• `OCCI_NO_AC_DDL`                                                                                                                                                                                                                           | `int`               |
| `ATTR_LOCKING_MODE`           | Locking mode for the database; values are:<br>• `OCCI_LOCK_IMMEDIATE`<br>• `OCCI_LOCK_DELAYED`                                                                                                                                                                                                                                                        | `int`               |
