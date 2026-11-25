This chapter describes how to create new metadata objects and map them to relational structures or expressions. It describes how to export and import the definitions of the metadata objects to XML templates. It also describes how to associate the objects with an analytic workspace, and how to build the analytic workspace.

The examples in this chapter are from the `CreateMetadataAndAW.java` example program. That program creates some of the same metadata objects as the `CreateAndBuildAW.java` and `SpecifyAWValues.java` example programs. The `CreateMetadataAndAW` program also exports the analytic workspace to an XML template.

This chapter includes the following topics:

- Overview of Creating and Mapping Metadata

- Creating an Analytic Workspace

- Creating the Dimensions, Levels, and Hierarchies

- Creating Attributes

- Creating Cubes and Measures

- Committing Transactions

- Exporting and Importing XML Templates

- Building an Analytic Workspace

### 4.1 Overview of Creating and Mapping Metadata

The OLAP Java API provides the ability to create persistent metadata objects. The top-level metadata objects exist in the data dictionary of the Oracle Database instance. The API also provides the ability to create transient metadata objects that exist only for the duration of the session. An application can use both types of metadata objects to create queries that retrieve or otherwise use the data in the data store.

Before an OLAP Java API application can create metadata objects, a database administrator must have prepared the Oracle Database instance. The DBA must have set up permanent and temporary tablespaces in the database to support the creation of Oracle OLAP metadata objects and must have granted the privileges that allow the user of the session to create and manage objects. A dimensional metadata model typically includes the objects described in [Understanding OLAP Java API Metadata](understanding-olap-java-api-metadata.md).

You implement the dimensional model by creating OLAP Java API metadata objects. You use classes in the `oracle.olapi.metadata.mapping` package to map the metadata objects to relational source objects and to build analytic workspaces. You use classes in the `oracle.olapi.syntax` package to specify `Expression` objects that you use in mapping the metadata. You use classes in the `oracle.olapi.metadata.deployment` package to deploy the metadata objects in an analytic workspace or in a relational database (ROLAP) organization.

The basic steps for implementing the dimensional model as OLAP Java API objects in an analytic workspace are the following:

1.  Create an `AW` object and `MdmPrimaryDimension` and `MdmCube` objects.

2.  Deploy the `MdmPrimaryDimension` and `MdmCube` objects to the ` AW`.

3.  Create `MdmDimensionLevel`, `MdmHierarchy`, and `MdmAttribute` objects for each `MdmPrimaryDimension`, create `MdmHierarchyLevel` objects to associate `MdmDimensionLevel` objects with an `MdmHierarchy`, and create the `MdmMeasure` and related objects for the `MdmCube` objects.

4.  Map the metadata objects to the relational sources of the base data.

5.  Commit the `Transaction`, which creates persistent objects in the database.

6.  Load data into the objects from the relational sources by building the analytic workspace.

For a list of the topics that describe these steps, see Creating Metadata and Analytic Workspaces.

### 4.2 Creating an Analytic Workspace

An analytic workspace is a container for dimensional objects. It is represented by the `AW` class in the `oracle.olapi.metadata.deployment` package. An analytic workspace is owned by an `MdmDatabaseSchema`.

Example 4-1 demonstrates getting the `MdmDatabaseSchema` for the GLOBAL user and creating an `AW`. For an example that gets the `MdmRootSchema`, see [Discovering Metadata](discovering-metadata.md).

Example 4-1 Creating an AW

    private void createAW(MdmRootSchema mdmRootSchema)
    {
      MdmDatabaseSchema mdmDBSchema = mdmRootSchema.getDatabaseSchema("GLOBAL");
      aw = mdmDBSchema.findOrCreateAW("GLOBAL_AWJ");
    }

### 4.3 Creating the Dimensions, Levels, and Hierarchies

A dimension is a list of unique values that identify and categorize data. Dimensions form the edges of a cube and identify the values in the measures of the cube. A dimension can have one or more levels that categorize the dimension members. It can have one or more hierarchies that further categorize the members. A dimension can also have no levels or hierarchies. However, a dimension must have one or more levels before Oracle OLAP can create a materialized view for it.

A dimension also has attributes that contain information about dimension members. For descriptions of creating attributes, see "Creating Attributes".

The following topics describe how to create objects that represent a dimension and the levels and hierarchies of a dimension.

- Creating and Mapping Dimensions

- Creating and Mapping Dimension Levels

- Creating and Mapping Hierarchies

#### 4.3.1 Creating and Mapping Dimensions

An OLAP dimension is represented by the `MdmPrimaryDimension` class. A dimension is owned by an `MdmDatabaseSchema`. You create a dimension with the `findOrCreateTimeDimension` or the `findOrCreateStandardDimension` method of the `MdmDatabaseSchema`. You can map a dimension that has no levels to a relational data source by creating a `MemberListMap` for the dimension.

Example 4-2 creates a standard dimension that has the name CHANNEL_AWJ. The example creates an `AWPrimaryDimensionOrganization` object to deploy the dimension in an analytic workspace. The `mdmDBSchema` and `aw` objects are created by Example 4-1. The last three lines call the methods of Example 4-3, Example 4-4, and Example 4-9, respectively.

Example 4-2 Creating and Deploying an MdmStandardDimension

    MdmStandardDimension mdmChanDim =
      mdmDBSchema.findOrCreateStandardDimension("CHANNEL_AWJ");
    AWPrimaryDimensionOrganization awChanDimOrg =
      mdmChanDim.findOrCreateAWPrimaryDimensionOrganization(aw);

    createAndMapDimensionLevels(mdmChanDim);
    createAndMapHierarchies();
    commit(mdmChanDim);

#### 4.3.2 Creating and Mapping Dimension Levels

An `MdmDimensionLevel` represents the members of a dimension that are at the same level. Typically, the members of a level are in a column in a dimension table in the relational source. A `MemberListMap` associates the `MdmDimensionLevel` with the relational source.

Example 4-3 creates two `MdmDimensionLevel` objects for the CHANNEL_AWJ dimension and maps the dimension levels to the key columns of the GLOBAL.CHANNEL_DIM table. The example also maps the long description attributes for the dimension levels to columns of that table. The long description attribute, `chanLongDescAttr`, is created by Example 4-6.

Example 4-3 Creating and Mapping an MdmDimensionLevel

    private ArrayList<MdmDimensionLevel> dimLevelList = new ArrayList();
    private ArrayList<String> dimLevelNames = new ArrayList();
    private ArrayList<String> keyColumns = new ArrayList();
    private ArrayList<String> lDescColNames = new ArrayList();

    private void createAndMapDimensionLevels(MdmPrimaryDimension mdmChanDim)
    {
      dimLevelNames.add("TOTAL_CHANNEL");
      dimLevelNames.add("CHANNEL");

      keyColumns.add("GLOBAL.CHANNEL_DIM.TOTAL_ID");
      keyColumns.add("GLOBAL.CHANNEL_DIM.CHANNEL_ID");

      lDescColNames.add("GLOBAL.CHANNEL_DIM.TOTAL_DSC");
      lDescColNames.add("GLOBAL.CHANNEL_DIM.CHANNEL_DSC");

      // Create the MdmDimensionLevel and MemberListMap objects.
      int i = 0;
      for(String dimLevelName : dimLevelNames)
      {
        MdmDimensionLevel mdmDimLevel =
          mdmChanDim.findOrCreateDimensionLevel(dimLevelNames.get(i));
        dimLevelList.add(mdmDimLevel);

        // Create a MemberListMap for the dimension level.
        MemberListMap mdmDimLevelMemListMap =
          mdmDimLevel.findOrCreateMemberListMap();
        ColumnExpression keyColExp =
          (ColumnExpression)SyntaxObject.fromSyntax(keyColumns.get(i),
                                                    metadataProvider);
        mdmDimLevelMemListMap.setKeyExpression(keyColExp);
        mdmDimLevelMemListMap.setQuery(keyColExp.getQuery());

        // Create an attribute map for the Long Description attribute.
        AttributeMap attrMapLong =
          mdmDimLevelMemListMap.findOrCreateAttributeMap(chanLongDescAttr);

        // Create an expression for the attribute map.
        Expression lDescColExp =
          (Expression)SyntaxObject.fromSyntax(lDescColNames.get(i),
                                              metadataProvider);
        attrMapLong.setExpression(lDescColExp);
        i++;
      }
    }

#### 4.3.3 Creating and Mapping Hierarchies

An `MdmHierarchy` represents a hierarchy in the dimensional object model. An `MdmHierarchy` can be an instance of the `MdmLevelHierarchy` or the `MdmValueHierarchy` class. An `MdmLevelHierarchy` has an ordered list of `MdmHierarchyLevel` objects that relate `MdmDimensionLevel` objects to the hierarchy.

##### 4.3.3.1 Creating and Mapping an MdmLevelHierarchy

Example 4-4 creates a hierarchy for the CHANNEL_AWJ dimension. It creates hierarchy levels for the hierarchy and associates attributes with the hierarchy levels. It also maps the hierarchy levels and the attributes to relational sources. The example uses the `ArrayList` objects from Example 4-3. It maps the `MdmHierarchyLevel` objects to the same relational source objects as the `MdmDimensionLevel` objects are mapped.

Example 4-4 Creating and Mapping MdmLevelHierarchy and MdmHierarchyLevel Objects

    private void createAndMapHierarchies()
    {
      MdmLevelHierarchy mdmLevelHier =
        mdmChanDim.findOrCreateLevelHierarchy("CHANNEL_PRIMARY");

      // Create the MdmHierarchyLevel and HierarchyLevelMap objects.
      int i = 0;
      for(String dimLevelName : dimLevelNames)
      {
        MdmDimensionLevel mdmDimLevel =
          mdmChanDim.findOrCreateDimensionLevel(dimLevelName);
        MdmHierarchyLevel mdmHierLevel =
          mdmLevelHier.findOrCreateHierarchyLevel(mdmDimLevel);
        HierarchyLevelMap hierLevelMap =
          mdmHierLevel.findOrCreateHierarchyLevelMap();
        ColumnExpression keyColExp =
          (ColumnExpression)SyntaxObject.fromSyntax(keyColumns.get(i),
                                                    metadataProvider);
        hierLevelMap.setKeyExpression(keyColExp);
        hierLevelMap.setQuery(keyColExp.getQuery());
        i++;
      }
    }

##### 4.3.3.2 Creating and Mapping an MdmValueHierarchy

The GLOBAL_AWJ analytic workspace that is used by the examples in this documentation does not have an `MdmPrimaryDimension` for which an `MdmValueHierarchy` would be sensible. The sample schema for the user `SCOTT` has a table that can serve as an example.

The SCOTT sample schema has a table named EMP. That table has columns for employees and for managers. You could create a dimension for employees. You could then create an `MdmValueHierarchy` in which you map the employee column as the base values for the hierarchy and you map the manager column as the parent relation, as shown in Example 4-5. To be able to create OLAP dimensions, the SCOTT user must be granted the `OLAP_USER` role and the `CREATE SESSION` privilege.

In the example, `mdmDBSchema` is the `MdmDatabaseSchema` for the SCOTT user, `dp` is the `DataProvider`, and `mp` is the `MdmMetadataProvider`. The example does not show the code for connecting to the database or getting the `DataProvider` and creating a `UserSession`, or getting the `MdmMetadataProvider`, the `MdmRootSchema`, or the `MdmDatabaseSchema`. The code is an excerpt from a class that extends the `BaseExample11g` example class. That class uses other example classes that have methods for committing the current `Transaction` and for displaying output. For the complete code, see the `CreateValueHierarchy.java` example program.

Example 4-5 Creating an MdmValueHierarchy

    // Create an analytic workspace object.
    AW aw = mdmDBSchema.findOrCreateAW(awName);
    // Create a dimension and deploy it to the analytic workspace.
    MdmPrimaryDimension mdmEmpDim =
      mdmDBSchema.findOrCreateStandardDimension("EMP_DIM");
    AWPrimaryDimensionOrganization awEmpDimOrg =
      mdmEmpDim.findOrCreateAWPrimaryDimensionOrganization(aw);

    // Get the EMP table and the Query for the table.
    MdmTable empTable = (MdmTable)mdmDBSchema.getTopLevelObject("EMP");
    Query empQuery = empTable.getQuery();

    // Create a value hierarchy.
    MdmValueHierarchy mdmValHier =
     mdmEmpDim.findOrCreateValueHierarchy("EMPVALHIER");
    // Create a map for the hierarchy.
    SolvedValueHierarchyMap solvedValHierMap =
     mdmValHier.findOrCreateSolvedValueHierarchyMap();
    // Specify the Query, the key expression and the parent key expression for
    // the hierarchy.
    solvedValHierMap.setQuery(empQuery);
    Expression keyExp =
     (Expression)SyntaxObject.fromSyntax("SCOTT.EMP.EMPNO", mp);
    solvedValHierMap.setKeyExpression(keyExp);
    Expression parentExp =
     (Expression)SyntaxObject.fromSyntax("SCOTT.EMP.MGR", mp);
    solvedValHierMap.setParentKeyExpression(parentExp);

    // Create an attribute that relates a name to each dimension member.
    MdmBaseAttribute mdmNameAttr =
     mdmEmpDim.findOrCreateBaseAttribute("EMP_NAME");
    SQLDataType sdtVC2 = new SQLDataType("VARCHAR2");
    mdmNameAttr.setSQLDataType(sdtVC2)
    // Create an attribute map for the attribute.
    AttributeMap attrMap =
     solvedValHierMap.findOrCreateAttributeMap(mdmNameAttr);
    // Create and set an expression for the attribute map.
    Expression exp = (Expression)
      SyntaxObject.fromSyntax("SCOTT.EMP.ENAME", mp);
    attrMap.setExpression(exp);
    mdmValHier.addAttribute(mdmNameAttr);

    // Commit the Transaction before building the analytic workspace.
    // The getContext method of BaseExample11g returns a Context11g object,
    // which has a method that commits the Transaction.
    getContext().commit();
    BuildItem bldEmpDim = new BuildItem(mdmEmpDim);
    ArrayList<BuildItem> items = new ArrayList();
    items.add(bldEmpDim);
    BuildProcess bldProc = new BuildProcess(items);

    // Execute the build.
    try
    {
     dp.executeBuild(bldProc, 0);
    }
    catch (Exception ex)
    {
     println("Could not execute the BuildProcess.");
     println("Caught: " + ex);
    }

    //Get the Source objects for the dimension, the hierarchy, and the attribute.
    Source empDim = mdmEmpDim.getSource();
    Source valHier = mdmValHier.getSource();
    Source empNameAttr = mdmNameAttr.getSource();
    // Get the parent attribute and get the Source for it.
    MdmAttribute mdmParentAttr = mdmEmpDim.getParentAttribute();
    Source parentAttr = mdmParentAttr.getSource();

    Source parentByEmpByName = parentAttr.join(valHier.join(empNameAttr));
    // Sort the values in ascending order by employee number of the managers.
    Source sortedParentByEmpByName = parentByEmpByName.sortAscending();

    // Commit the Transaction before creating a Cursor.
    getContext().commit();
    // The displayResult method of the Context11g object creates a Cursor and
    // displays the results.
    println("The managers of the employees are:");
    getContext().displayResult(sortedParentByEmpByName);

The output of the example is the following. It shows the employee name, the employee ID and then the employee ID of the manager. The results are sorted by manager. The employee King does not have a parent and is the highest member of the hierarchy so the manager value for King is null, which appears as `NA` in the output.

    The managers of the employees are:
    1: ((SCOTT,EMPVALHIER::7788),EMPVALHIER::7566)
    2: ((FORD,EMPVALHIER::7902),EMPVALHIER::7566)
    3: ((ALLEN,EMPVALHIER::7499),EMPVALHIER::7698)
    4: ((WARD,EMPVALHIER::7521),EMPVALHIER::7698)
    5: ((MARTIN,EMPVALHIER::7654),EMPVALHIER::7698)
    6: ((TURNER,EMPVALHIER::7844),EMPVALHIER::7698)
    7: ((JAMES,EMPVALHIER::7900),EMPVALHIER::7698)
    8: ((MILLER,EMPVALHIER::7934),EMPVALHIER::7782)
    9: ((ADAMS,EMPVALHIER::7876),EMPVALHIER::7788)
    10: ((JONES,EMPVALHIER::7566),EMPVALHIER::7839)
    11: ((BLAKE,EMPVALHIER::7698),EMPVALHIER::7839)
    12: ((CLARK,EMPVALHIER::7782),EMPVALHIER::7839)
    13: ((SMITH,EMPVALHIER::7369),EMPVALHIER::7902)
    14: ((KING,EMPVALHIER::7839),NA)

### 4.4 Creating Attributes

Attributes contain information about dimension members. An `MdmBaseAttribute` represents values that are based on relational source tables. An `MdmDerivedAttribute` represents values that Oracle OLAP derives from characteristics or relationships of the dimension members. For example, the `getParentAttribute` method of an `MdmPrimaryDimension` returns an `MdmDerivedAttribute` that records the parent of each dimension member.

You create a base attribute for a dimension with the `findOrCreateBaseAttribute` method. You can specify the data type of the attribute, although for many attributes Oracle OLAP can determine the data type from the attribute mapping. With the `setAllowAutoDataTypeChange` method, you can specify that Oracle OLAP determine the data type. Some attributes are used by the dimension in certain ways, such as to provide descriptions of dimension members or to provide date information that can be used in calculations. For example, you can specify an attribute for descriptions with the `setValueDescriptionAttribute` method of the dimension and you can specify an attribute that contains end date time period values with the `setEndDateAttribute` method of an `MdmTimeDimension`.

Example 4-6 creates a long description attribute for the CHANNEL_AWJ dimension and specifies it as the attribute that contains descriptions of the members of the dimension. The example specifies that Oracle OLAP automatically determines a SQL data type for the attribute.

Example 4-6 Creating an MdmBaseAttribute

    private MdmBaseAttribute chanLongDescAttr = null;
    private void createLongDesciptionAttribute(MdmPrimaryDimension mdmChanDim)
    {
    // Create the long description attribute and allow the automatic changing of
    // the SQL data type.
    chanLongDescAttr = mdmChanDim.findOrCreateBaseAttribute("LONG_DESCRIPTION");
    chanLongDescAttr.setAllowAutoDataTypeChange(true));

    // Specifies that the attribute contains descriptions of the dimension members.
    mdmChanDim.setValueDescriptionAttribute(chanLongDescAttr);
    }

An attribute can have different values for the members of different levels of the dimension. In that case the attribute has an attribute mapping for each level. Example 4-3 creates an `AttributeMap` for the long description attribute for each dimension level by calling the `findOrCreateAttributeMap` method of the `MemberListMap` for each dimension level. It specifies a different column for each attribute map.

### 4.5 Creating Cubes and Measures

A cube in a dimensional object model is represented by the `MdmCube` class. An `MdmCube` owns one or more `MdmMeasure` objects. It has a list of the `MdmPrimaryDimension` objects that dimension the measures.

An `MdmCube` has the following objects associated with it.

- `MdmPrimaryDimension` objects that specify the dimensionality of the cube.

- `MdmMeasure` objects that contain data that is identified by the dimensions.

- A `CubeOrganization` that specifies how the cube stores and manages the measure data.

- `CubeMap` objects that associate the cube with relational sources.

- A `ConsistentSolveSpecification` that specifies how to calculate, or solve, the aggregate level data.

The following examples demonstrate creating and mapping a cube and its measures .

- Creating Cubes

- Creating and Mapping Measures

#### 4.5.1 Creating Cubes

Example 4-7 Creating and Mapping an MdmCube

This example creates a cube and some of the objects associated with it. It creates an `MdmCube` that has the name PRICE_CUBE_AWJ. It also creates an `AWCubeOrganization` object to deploy the cube in an analytic workspace. The `mdmDBSchema` and `aw` objects are created by Example 4-1 and the `leafLevel` `ArrayList` is created in Example 4-4. The `mdmTimeDim` and `mdmProdDim` objects are dimensions of time periods and product categories. The `CreateAndBuildAW` program creates those dimensions. The last lines of the example call the methods in Example 4-8 and Example 4-9, respectively.

    private MdmCube createAndMapCube(MdmPrimaryDimension mdmTimeDim,
                                     MdmPrimaryDimension mdmProdDim)
    {
      MdmCube mdmPriceCube = mdmDBSchema.findOrCreateCube("PRICE_CUBE_AWJ");
      // Add dimensions to the cube.
      mdmPriceCube.addDimension(mdmTimeDim);
      mdmPriceCube.addDimension(mdmProdDim);

      AWCubeOrganization awCubeOrg =
        mdmPriceCube.findOrCreateAWCubeOrganization(aw);
      awCubeOrg.setMVOption(AWCubeOrganization.NONE_MV_OPTION);
      awCubeOrg.setMeasureStorage(AWCubeOrganization.SHARED_MEASURE_STORAGE);
      awCubeOrg.setCubeStorageType("NUMBER");

      AggregationCommand aggCommand = new AggregationCommand("AVG");
      ArrayList<ConsistentSolveCommand> solveCommands = new ArrayList();
      solveCommands.add(aggCommand);
      ConsistentSolveSpecification conSolveSpec =
                          new ConsistentSolveSpecification(solveCommands);
      mdmPriceCube.setConsistentSolveSpecification(conSolveSpec);

      // Create and map the measures of the cube.
      createAndMapMeasures(mdmPriceCube);
      // Commit the Transaction.
      commit(mdmPriceCube);
    }

#### 4.5.2 Creating and Mapping Measures

Example 4-8 Creating and Mapping Measures

This example creates measures for a cube and maps the measures to fact tables in the relational database. The example uses the cube created by Example 4-7.

    private void createAndMapMeasures(MdmCube mdmPriceCube)
    {
      ArrayList<MdmBaseMeasure> measures = new ArrayList();
      MdmBaseMeasure mdmCostMeasure =
        mdmPriceCube.findOrCreateBaseMeasure("UNIT_COST");
      MdmBaseMeasure mdmPriceMeasure =
        mdmPriceCube.findOrCreateBaseMeasure("UNIT_PRICE");
      mdmCostMeasure.setAllowAutoDataTypeChange(true);
      mdmPriceMeasure.setAllowAutoDataTypeChange(true);
      measures.add(mdmCostMeasure);
      measures.add(mdmPriceMeasure);
      MdmTable priceCostTable =
        (MdmTable)mdmDBSchema.getTopLevelObject("PRICE_FACT");
      Query cubeQuery = priceCostTable.getQuery();
      ArrayList<String> measureColumns = new ArrayList();
      measureColumns.add("GLOBAL.PRICE_FACT.UNIT_COST");
      measureColumns.add("GLOBAL.PRICE_FACT.UNIT_PRICE");
      CubeMap cubeMap = mdmPriceCube.findOrCreateCubeMap();
      cubeMap.setQuery(cubeQuery);

      // Create MeasureMap objects for the measures of the cube and
      // set the expressions for the measures. The expressions specify the
      // columns of the fact table for the measures.
      int i = 0;
      for(MdmBaseMeasure mdmBaseMeasure : measures)
      {
        MeasureMap measureMap = cubeMap.findOrCreateMeasureMap(mdmBaseMeasure);
        Expression expr =
          (Expression)SyntaxObject.fromSyntax(measureColumns.get(i),
                                              metadataProvider);
        measureMap.setExpression(expr);
        i++;
      }

      // Create CubeDimensionalityMap objects for the dimensions of the cube and
      // set the expressions for the dimensions. The expressions specify the
      // columns of the fact table for the dimensions.

      ArrayList<String> factColNames = new ArrayList();
      factColNames.add("GLOBAL.PRICE_FACT.MONTH_ID");
      factColNames.add("GLOBAL.PRICE_FACT.ITEM_ID");
      List<MdmDimensionality> mdmDimltys = mdmPriceCube.getDimensionality();
      for (MdmDimensionality mdmDimlty: mdmDimltys)
      {
        CubeDimensionalityMap cubeDimMap =
          cubeMap.findOrCreateCubeDimensionalityMap(mdmDimlty);
        MdmPrimaryDimension mdmPrimDim =
          (MdmPrimaryDimension)mdmDimlty.getDimension();
        String columnMap = null;
        if (mdmPrimDim.getName().startsWith("TIME"))
        {
          columnMap = factColNames.get(0);
          i = 0;
        }
        else// (mdmPrimDim.getName().startsWith("PRODUCT"))
        {
          columnMap = factColNames.get(1);
          i = 1;
        }
        Expression expr =
          (Expression)SyntaxObject.fromSyntax(columnMap,metadataProvider);
        cubeDimMap.setExpression(expr);

        // Associate the leaf level of the hierarchy with the cube.
        MdmHierarchy mdmDefHier = mdmPrimDim.getDefaultHierarchy();
        MdmLevelHierarchy mdmLevHier = (MdmLevelHierarchy)mdmDefHier;
        List<MdmHierarchyLevel> levHierList = mdmLevHier.getHierarchyLevels();
        // The last element in the list must be the leaf level of the hierarchy.
        MdmHierarchyLevel leafLevel = levHierList.get(levHierList.size() - 1);
        cubeDimMap.setMappedDimension(leafLevel);
      }
    }

### 4.6 Committing Transactions

To save a metadata object as a persistent entity in the database, you must commit the `Transaction` in which you created the object. You can commit a `Transaction` at any time. Committing the `Transaction` after creating a top-level object and the objects that it owns is a good practice.

Example 4-9 gets the `TransactionProvider` from the `DataProvider` for the session and commits the current `Transaction`.

Example 4-9 Committing Transactions

    private void commit(MdmSource mdmSource)
    {
      try
      {
        System.out.println("Committing the transaction for " +
                            mdmSource.getName() + ".");
        (dp.getTransactionProvider()).commitCurrentTransaction();
      }
      catch (Exception ex)
      {
        System.out.println("Could not commit the Transaction. " + ex);
      }
    }

### 4.7 Exporting and Importing XML Templates

You can save the definition of a metadata object by exporting the object to an XML template. Exporting an object saves the definition of the object and the definitions of any objects that it owns. For example, if you export an `AW` object to XML, then the XML includes the definitions of any `MdmPrimaryDimension` and `MdmCube` objects that the `AW` owns, and the `MdmAttribute`, `MdmMeasure` and other objects owned by the dimensions and cubes.

You can import a metadata object definition as an XML template. After importing, you must build the object.

Example 4-10 Exporting to an XML Template

This example exports metadata objects to an XML template and saves it in a file. The code excerpt at the beginning of the example creates a `List` of the objects to export. It adds to the `List` the `aw` object, which is the analytic workspace created by Example 4-1. It then calls the `exportToXML` method.

     ... // In some method.
    List objectsToExport = new ArrayList();
    objectsToExport.add(aw);
    exportToXML(objectsToExport, "globalawj.xml");
    ...
    public void exportToXML(List objectsToExport, String fileName)
    {
      try
      {
        PrintWriter writer = new PrintWriter(new FileWriter(filename));
        mp.exportFullXML(writer,         // mp is the MdmMetadataProvider
                         objectsToExport,
                         null,           // No Map for renaming objects
                         false);         // Do not include the owner name
        writer.close();
      }
      catch (IOException ie)
      {
        ie.printStackTrace();
      }
    }

### 4.8 Building an Analytic Workspace

After creating and mapping metadata objects, or importing the XML definition of an object, you must perform the calculations that the objects specify and load the resulting data into physical storage structures.

Example 4-11 creates `BuildItem` objects for the dimensions and cubes of the analytic workspace. It creates a `BuildProcess` that specifies the `BuildItem` objects and passes the `BuildProcess` to the `executeBuild` method of the `DataProvider` for the session.

Example 4-11 Building an Analytic Workspace

    BuildItem bldChanDim = new BuildItem(mdmChanDim);
    BuildItem bldProdDim = new BuildItem(mdmProdDim);
    BuildItem bldCustDim = new BuildItem(mdmCustDim);
    BuildItem bldTimeDim = new BuildItem(mdmTimeDim);
    BuildItem bldUnitsCube = new BuildItem(mdmUnitsCube);
    BuildItem bldPriceCube = new BuildItem(mdmPriceCube);
    ArrayList<BuildItem> items = new ArrayList();
    items.add(bldChanDim);
    items.add(bldProdDim);
    items.add(bldCustDim);
    items.add(bldTimeDim);
    items.add(bldUnitsCube);
    items.add(bldPriceCube);
    BuildProcess bldProc = new BuildProcess(items);
    try
    {
      dp.executeBuild(bldProc, 0);
    }
    catch (Exception ex)
    {
      System.out.println("Could not execute the BuildProcess." + ex);
    }
