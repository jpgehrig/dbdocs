To create dynamic queries, you use the Oracle OLAP Java API `Template` class and other related classes. The following topics describe these classes and provide examples of implementations of them.

- About Template Objects

- Overview of Template and Related Classes

- Designing and Implementing a Template

### 10.1 About Template Objects

The `Template` class is the basis of a very powerful feature of the Oracle OLAP Java API. You use `Template` objects to create modifiable `Source` objects. With those `Source` objects, you can create dynamic queries that can change in response to end-user selections. `Template` objects also offer a convenient way for you to translate user-interface elements into OLAP Java API operations and objects.

For information on the `Transaction` objects that you use to make changes to the dynamic `Source` and to either save or discard those changes, see [Using a TransactionProvider](using-transaction-provider.md).

#### 10.1.1 About Creating a Dynamic Source

The main feature of a `Template` is the ability to produce a dynamic `Source`. That ability is based on two of the other objects that a `Template` uses: instances of the `DynamicDefinition` and `MetadataState` classes.

When a `Source` is created, Oracle OLAP automatically associates a `SourceDefinition` with it. The `SourceDefinition` has information about the `Source`. Once created, the `Source` and the associated `SourceDefinition` are associated immutably. The `getSource` method of a `SourceDefinition` returns the `Source` associated with it.

`DynamicDefinition` is a subclass of `SourceDefinition`. A `Template` creates a `DynamicDefinition`, which acts as a proxy for the `SourceDefinition` of the `Source` produced by the `Template`. This means that instead of always getting the same immutably associated `Source`, the `getSource` method of the `DynamicDefinition` gets whatever `Source` is currently produced by the `Template`. The instance of the `DynamicDefinition` does not change even though the `Source` that it gets is different.

The `Source` that a `Template` produces can change because the values, including other `Source` objects, that the `Template` uses to create the `Source` can change. A `Template` stores those values in a `MetadataState`. A `Template` provides methods to get the current state of the `MetadataState`, to get or set a value, and to set the state. You use those methods to change the data values that the `MetadataState` stores.

You use a `DynamicDefinition` to get the `Source` produced by a `Template`. If your application changes the state of the values that the `Template` uses to create the `Source`, for example, in response to end-user selections, then the application uses the same `DynamicDefinition` to get the `Source` again, even though the new `Source` defines a result set different than the previous `Source`.

The `Source` produced by a `Template` can be the result of a series of `Source` operations that create other `Source` objects, such as a series of selections, sortings, calculations, and joins. You put the code for those operations in the `generateSource` method of a `SourceGenerator` for the `Template`. That method returns the `Source` produced by the `Template`. The operations use the data stored in the `MetadataState`.

You might build an extremely complex query that involves the interactions of dynamic `Source` objects produced by many different `Template` objects. The end result of the query building is a `Source` that defines the entire complex query. If you change the state of any one of the `Template` objects that you used to create the final `Source`, then the final `Source` represents a result set that is different from that of the previous `Source`. You can thereby modify the final query without having to reproduce all of the operations involved in defining the query.

#### 10.1.2 About Translating User Interface Elements into OLAP Java API Objects

You design `Template` objects to represent elements of the user interface of an application. Your `Template` objects turn the selections that the end user makes into OLAP Java API query-building operations that produce a `Source`. You then create a `Cursor` to fetch from Oracle OLAP the result set defined by the `Source`. You get the values from the `Cursor` and display them to the end user. When an end user makes changes to the selections, you change the state of the `Template`. You then get the `Source` produced by the `Template`, create a new `Cursor`, get the new values, and display them.

### 10.2 Overview of Template and Related Classes

In the OLAP Java API, several classes work together to produce a dynamic `Source`. In designing a `Template`, you must implement or extend the following:

- The `Template` abstract class

- The `MetadataState` interface

- The `SourceGenerator` interface

Instances of those three classes, plus instances of the `DataProvider` and `DynamicDefinition` classes, work together to produce the `Source` that the `Template` defines.

#### 10.2.1 What Is the Relationship Between the Classes That Produce a Dynamic Source?

The classes that produce a dynamic `Source` work together as follows:

- A `Template` has methods that create a `DynamicDefinition` and that get and set the current state of a `MetadataState`. An extension to the `Template` abstract class adds methods that get and set the values of fields on the `MetadataState`.

- The `MetadataState` implementation has fields for storing the data to use in generating the `Source` for the `Template`. When you create a new `Template`, you pass the `MetadataState` to the constructor of the `Template`. When you call the `getSource` method of the `DynamicDefinition`, the `MetadataState` is passed to the `generateSource` method of the `SourceGenerator`.

- The `DataProvider` is used in creating a `Template` and by the `SourceGenerator` in creating new `Source` objects.

- The `SourceGenerator` implementation has a `generateSource` method that uses the current state of the data in the `MetadataState` to produce a `Source` for the `Template`. You pass in the `SourceGenerator` to the `createDynamicDefinition` method of the `Template` to create a `DynamicDefinition`.

- The `DynamicDefinition` has a `getSource` method that gets the `Source` produced by the `SourceGenerator`. The `DynamicDefinition` serves as a proxy for the `SourceDefinition` that is immutably associated with the `Source`.

#### 10.2.2 Template Class

You use a `Template` to produce a modifiable `Source`. A `Template` has methods for creating a `DynamicDefinition` and for getting and setting the current state of the `Template`. In extending the `Template` class, you add methods that provide access to the fields on the `MetadataState` for the `Template`. The `Template` creates a `DynamicDefinition` that you use to get the `Source` produced by the `SourceGenerator` for the `Template`.

For an example of a `Template` implementation, see Example 10-1.

#### 10.2.3 MetadataState Interface

An implementation of the `MetadataState` interface stores the current state of the values for a `Template`. A `MetadataState` must include a `clone` method that creates a copy of the current state.

When instantiating a new `Template`, you pass a `MetadataState` to the `Template` constructor. The `Template` has methods for getting and setting the values stored by the `MetadataState`. The `generateSource` method of the `SourceGenerator` for the `Template` uses the `MetadataState` when the method produces a `Source` for the `Template`.

For an example of a `MetadataState` implementation, see Example 10-2.

#### 10.2.4 SourceGenerator Interface

An implementation of `SourceGenerator` must include a `generateSource` method, which produces a `Source` for a `Template`. A `SourceGenerator` must produce only one type of `Source`, such as a `BooleanSource`, a `NumberSource`, or a `StringSource`. In producing the `Source`, the `generateSource` method uses the current state of the data represented by the `MetadataState` for the `Template`.

To get the `Source` produced by the `generateSource` method, you create a `DynamicDefinition` by passing the `SourceGenerator` to the `createDynamicDefinition` method of the `Template`. You then get the `Source` by calling the `getSource` method of the `DynamicDefinition`.

A `Template` can create more than one `DynamicDefinition`, each with a differently implemented `SourceGenerator`. The `generateSource` methods of the different `SourceGenerator` objects use the same data, as defined by the current state of the `MetadataState` for the `Template`, to produce `Source` objects that define different queries.

For an example of a `SourceGenerator` implementation, see Example 10-3.

#### 10.2.5 DynamicDefinition Class

`DynamicDefinition` is a subclass of `SourceDefinition`. You create a `DynamicDefinition` by calling the `createDynamicDefinition` method of a `Template` and passing it a `SourceGenerator`. You get the `Source` produced by the `SourceGenerator` by calling the `getSource` method of the `DynamicDefinition`.

A `DynamicDefinition` created by a `Template` is a proxy for the `SourceDefinition` of the `Source` produced by the `SourceGenerator`. The `SourceDefinition` is immutably associated with the `Source`. If the state of the `Template` changes, then the `Source` produced by the `SourceGenerator` is different. Because the `DynamicDefinition` is a proxy, you use the same `DynamicDefinition` to get the new `Source` even though that `Source` has a different `SourceDefinition`.

The `getCurrent` method of a `DynamicDefinition` returns the `SourceDefinition` immutably associated with the `Source` that the `generateSource` method currently returns. For an example of the use of a `DynamicDefinition`, see Example 10-4.

### 10.3 Designing and Implementing a Template

The design of a `Template` reflects the query-building elements of the user interface of an application. For example, suppose you want to develop an application that allows the end user to create a query that requests a number of values from the top or bottom of a list of values. The values are from one dimension of a measure. The other dimensions of the measure are limited to single values.

The user interface of your application has a dialog box that allows the end user to do the following:

- Select a radio button that specifies whether the data values should be from the top or bottom of the range of values.

- Select a measure from a drop-down list of measures.

- Select a number from a field. The number specifies the number of data values to display.

- Select one of the dimensions of the measure as the base of the data values to display. For example, if the user selects the product dimension, then the query specifies some number of products from the top or bottom of the list of products. The list is determined by the measure and the selected values of the other dimensions.

- Click a button to bring up a dialog box through which the end user selects the single values for the other dimensions of the selected measure. After selecting the values of the dimensions, the end user clicks an OK button on the second dialog box and returns to the first dialog box.

- Click an OK button to generate the query. The results of the query appear.

To generate a `Source` that represents the query that the end user creates in the first dialog box, you design a `Template` called `TopBottomTemplate`. You also design a second `Template`, called `SingleSelectionTemplate`, to create a `Source` that represents the end user's selections of single values for the dimensions other than the base dimension. The designs of your `Template` objects reflect the user interface elements of the dialog boxes.

In designing the `TopBottomTemplate` and its `MetadataState` and `SourceGenerator`, you do the following:

- Create a class called `TopBottomTemplate` that extends `Template`. To the class, you add methods that get the current state of the `Template`, set the values specified by the user, and then set the current state of the `Template`.

- Create a class called `TopBottomTemplateState` that implements `MetadataState`. You provide fields on the class to store values for the `SourceGenerator` to use in generating the `Source` produced by the `Template`. The values are set by methods of the `TopBottomTemplate`.

- Create a class called `TopBottomTemplateGenerator` that implements `SourceGenerator`. In the `generateSource` method of the class, you provide the operations that create the `Source` specified by the end user's selections.

Using your application, an end user selects units sold as the measure and products as the base dimension in the first dialog box. The end user also selects the Asia Pacific region, the first quarter of 2001, and the direct sales channel as the single values for each of the remaining dimensions.

The query that the end user has created requests the ten products that have the highest total amount of units sold through the direct sales channel to customers in the Asia Pacific region during the calendar year 2001.

For examples of implementations of the `TopBottomTemplate`, `TopBottomTemplateState`, and `TopBottomTemplateGenerator` classes, and an example of an application that uses them, see Example 10-1, Example 10-2, Example 10-3, and Example 10-4. The `TopBottomTemplateState` and `TopBottomTemplateGenerator` classes are implemented as inner classes of the `TopBottomTemplate` outer class.

#### 10.3.1 Implementing the Classes for a Template

The examples in this topic implement the `Template`, `MetadataState`, and `SourceGenerator` classes.

Example 10-1 Implementing a Template

This example is an implementation of the `TopBottomTemplate` class.

    import oracle.olapi.data.source.DataProvider;
    import oracle.olapi.data.source.DynamicDefinition;
    import oracle.olapi.data.source.Source;
    import oracle.olapi.data.source.SourceGenerator;
    import oracle.olapi.data.source.Template;
    import oracle.olapi.transaction.metadataStateManager.MetadataState;

    /**
     * Creates a TopBottomTemplateState, a TopBottomTemplateGenerator,
     * and a DynamicDefinition.
     * Gets the current state of the TopBottomTemplateState and the values
     * that it stores.
     * Sets the data values stored by the TopBottomTemplateState and sets the
     * changed state as the current state.
     */
    public class TopBottomTemplate extends Template
    {
    // Constants for specifying the selection of elements from the
    // beginning or the end of the result set.
      public static final int TOP_BOTTOM_TYPE_TOP = 0;
      public static final int TOP_BOTTOM_TYPE_BOTTOM = 1;

      // Variable to store the DynamicDefinition.
      private DynamicDefinition dynamicDef;

      /**
       * Creates a TopBottomTemplate with a default type and number values
       * and the specified base dimension.
       */
      public TopBottomTemplate(Source base, DataProvider dataProvider)
      {
        super(new TopBottomTemplateState(base, TOP_BOTTOM_TYPE_TOP, 0),
                                         dataProvider);
        // Create the DynamicDefinition for this Template. Create the
        // TopBottomTemplateGenerator that the DynamicDefinition uses.
        dynamicDef =
        createDynamicDefinition(new TopBottomTemplateGenerator(dataProvider));
      }

      /**
       * Gets the Source produced by the TopBottomTemplateGenerator
       * from the DynamicDefinition.
       */
      public final Source getSource()
      {
        return dynamicDef.getSource();
      }

      /**
       * Gets the Source that is the base of the elements in the result set.
       * Returns null if the state has no base.
       */
      public Source getBase()
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        return state.base;
      }

      /**
       * Sets a Source as the base.
       */
      public void setBase(Source base)
      {
         TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        state.base = base;
        setCurrentState(state);
      }

      /**
       * Gets the Source that specifies the measure and the single
       * selections from the dimensions other than the base.
       */
      public Source getCriterion()
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        return state.criterion;
      }

      /**
       * Specifies a Source that defines the measure and the single values
       * selected from the dimensions other than the base.
       * The SingleSelectionTemplate produces such a Source.
       */
      public void setCriterion(Source criterion)
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        state.criterion = criterion;
        setCurrentState(state);
      }

      /**
       * Gets the type, which is either TOP_BOTTOM_TYPE_TOP or
       * TOP_BOTTOM_TYPE_BOTTOM.
       */
      public int getTopBottomType()
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        return state.topBottomType;
      }

      /**
       * Sets the type.
       */
      public void setTopBottomType(int topBottomType)
      {
        if ((topBottomType < TOP_BOTTOM_TYPE_TOP) ||
            (topBottomType > TOP_BOTTOM_TYPE_BOTTOM  ))
          throw new IllegalArgumentException("InvalidTopBottomType");
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        state.topBottomType = topBottomType;
        setCurrentState(state);
      }

      /**
       * Gets the number of values selected.
       */
      public float getN()
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        return state.N;
      }

      /**
       * Sets the number of values to select.
       */
      public void setN(float N)
      {
        TopBottomTemplateState state = (TopBottomTemplateState) getCurrentState();
        state.N = N;
        setCurrentState(state);
      }
    }

Example 10-2 Implementing a MetadataState

This example is an implementation of the `TopBottomTemplateState` inner class.

    /**
     * Stores data that can be changed by a TopBottomTemplate.
     * The data is used by a TopBottomTemplateGenerator in producing
     * a Source for the TopBottomTemplate.
     */
    private static final class TopBottomTemplateState
         implements Cloneable, MetadataState
    {
      public int topBottomType;
      public float N;
      public Source criterion;
      public Source base;

      /**
       * Creates a TopBottomTemplateState.
       */
      public TopBottomTemplateState(Source base, int topBottomType, float N)
      {
        this.base = base;
        this.topBottomType = topBottomType;
        this.N = N;
      }

      /**
       * Creates a copy of this TopBottomTemplateState.
       */
      public final Object clone()
      {
        try
        {
          return super.clone();
        }
        catch(CloneNotSupportedException e)
        {
          return null;
        }
      }
    }

Example 10-3 Implementing a SourceGenerator

This example is an implementation of the `TopBottomTemplateGenerator` inner class.

    /**
     * Produces a Source for a TopBottomTemplate based on the data
     * values of a TopBottomTemplateState.
     */
    private final class TopBottomTemplateGenerator
          implements SourceGenerator
    {
      // Store the DataProvider.
      private DataProvider _dataProvider;

      /**
       * Creates a TopBottomTemplateGenerator.
       */
      public TopBottomTemplateGenerator(DataProvider dataProvider)
      {
        _dataProvider = dataProvider;
      }

      /**
       * Generates a Source for a TopBottomTemplate using the current
       * state of the data values stored by the TopBottomTemplateState.
       */
      public Source generateSource(MetadataState state)
      {
        TopBottomTemplateState castState = (TopBottomTemplateState) state;
        if (castState.criterion == null)
          throw new NullPointerException("CriterionParameterMissing");
        Source sortedBase = null;

        // Depending on the topBottomType value, select from the base Source
        // the elements specified by the criterion Source and sort the
        // elements in ascending or descending order.
        // For descending order, specify that null values are last.
        // For ascending order, specify that null values are first.

        if (castState.topBottomType == TOP_BOTTOM_TYPE_TOP)
          sortedBase = castState.base.sortDescending(castState.criterion, false);
        else
          sortedBase = castState.base.sortAscending(castState.criterion, true);
        return sortedBase.interval(1, Math.round(castState.N));
      }
    }

#### 10.3.2 Implementing an Application That Uses Templates

After you have stored the selections made by the end user in the `MetadataState` for the `Template`, use the `getSource` method of the `DynamicDefinition` to get the dynamic `Source` created by the `Template`. This topic provides an example of an application that uses the `TopBottomTemplate` described in Example 10-1. For brevity, the code does not contain much exception handling.

The `BaseExample11g` class creates and stores an instance of the `Context11g` class, which has methods that do the following:

- Connect to an Oracle Database instance as the user in the command line arguments.

- Create `Cursor` objects and displays their values.

Example 10-4 does the following:

- Gets the `MdmMetadataProvider` and the `MdmRootSchema`.

- Gets the `DataProvider`.

- Gets the `MdmDatabaseSchema` for the user.

- Gets the `MdmCube` that has the COSTS, UNITS and SALES measures. From the cube, the example gets the UNITS and SALES measures and the dimensions associated with the cube.

- Creates a `SingleSelectionTemplate` for selecting single values from some of the dimensions of the measure. For the code of the `SingleSelectionTemplate` class that this example uses, see [SingleSelectionTemplate Class](SingleSelectionTemplate-class.md).

- Creates a `TopBottomTemplate` and stores selections made by the end user.

- Gets the `Source` produced by the `TopBottomTemplate`.

- Uses the `Context11g` object to create a `Cursor` for that `Source` and to display the `Cursor` values.

The complete code for [Example 7-3](using-transaction-provider.md) includes some of the same code that is in Example 10-4. The example does not show this code, which extends from the beginning of Example 10-4 to the following comment in the example:

    // End of code not shown in
    //Example 7-3.

Example 10-4 Getting the Source Produced by the Template

    import oracle.olapi.data.source.DataProvider;
    import oracle.olapi.data.source.Source;
    import oracle.olapi.examples.*;
    import oracle.olapi.metadata.mdm.MdmAttribute;
    import oracle.olapi.metadata.mdm.MdmBaseMeasure;
    import oracle.olapi.metadata.mdm.MdmCube;
    import oracle.olapi.metadata.mdm.MdmDatabaseSchema;
    import oracle.olapi.metadata.mdm.MdmDimensionLevel;
    import oracle.olapi.metadata.mdm.MdmDimensionMemberInfo;
    import oracle.olapi.metadata.mdm.MdmHierarchyLevel;
    import oracle.olapi.metadata.mdm.MdmLevelHierarchy;
    import oracle.olapi.metadata.mdm.MdmMetadataProvider;
    import oracle.olapi.metadata.mdm.MdmPrimaryDimension;
    import oracle.olapi.metadata.mdm.MdmRootSchema;

    /**
     * Creates a query that specifies a number of elements from the top
     * or bottom of a selection of dimension members, creates a Cursor
     * for the query, and displays the values of the Cursor.
     * The selected dimension members are those that have measure values
     * that are specified by selected members of the other dimensions of
     * the measure.
     */
    public class TopBottomTest extends BaseExample11g
    {
      /**
       * Gets the MdmMetadataProvider, the DataProvider, the MdmRootSchema, and the
       * MdmDatabaseSchema for the current user.
       * Gets the UNITS_CUBE_AWJ MdmCube.
       * From the cube, gets the MdmBaseMeasure objects for the UNITS and SALES
       * measures and the MdmPrimaryDimension objects that dimension them.
       * Gets a hierarchy of the PRODUCT_AWJ dimension and the leaf level of the
       * dimension.
       * Gets the short description attribute of the dimension.
       * Creates a SingleSelectionTemplate and adds selections to it.
       * Creates a TopBottomTemplate and sets the properties of it.
       * Gets the Source produced by the TopBottomTemplate, creates a Cursor
       * for it, and displays the values of the Cursor.
       * Changes the state of the SingleSelectionTemplate and the
       * TopBottomTemplate, creates a new Cursor for the Source produced by the
       * TopBottomTemplate, and displays the values of that Cursor.
       */
      public void run() throws Exception
      {
        // Get the MdmMetadataProvider from the superclass.
        MdmMetadataProvider metadataProvider = getMdmMetadataProvider();
        // Get the DataProvider from the Context11g object of the superclass.
        DataProvider dp = getContext().getDataProvider();

        // Get the MdmRootSchema and the MdmDatabaseSchema for the user.
        MdmRootSchema mdmRootSchema =
          (MdmRootSchema)metadataProvider.getRootSchema();
        MdmDatabaseSchema mdmDBSchema =
          mdmRootSchema.getDatabaseSchema(getContext().getUser());

        MdmCube unitsCube =
          (MdmCube)mdmDBSchema.getTopLevelObject("UNITS_CUBE_AWJ");
        MdmBaseMeasure mdmUnits = unitsCube.findOrCreateBaseMeasure("UNITS");
        MdmBaseMeasure mdmSales = unitsCube.findOrCreateBaseMeasure("SALES");

        // Get the Source objects for the measures.
        Source units = mdmUnits.getSource();
        Source sales = mdmSales.getSource();

        // Get the MdmPrimaryDimension objects for the dimensions of the cube.
        List<MdmPrimaryDimension> cubeDims = unitsCube.getDimensions();
        MdmPrimaryDimension mdmTimeDim = null;
        MdmPrimaryDimension mdmProdDim = null;
        MdmPrimaryDimension mdmCustDim = null;
        MdmPrimaryDimension mdmChanDim = null;

        for(MdmPrimaryDimension mdmPrimDim : cubeDims)
        {
          if (mdmPrimDim.getName().startsWith("TIME"))
            mdmTimeDim = mdmPrimDim;
          else if (mdmPrimDim.getName().startsWith("PROD"))
            mdmProdDim = mdmPrimDim;
          else if (mdmPrimDim.getName().startsWith("CUST"))
            mdmCustDim = mdmPrimDim;
          else if (mdmPrimDim.getName().startsWith("CHAN"))
            mdmChanDim = mdmPrimDim;
        }

        // Get the hierarchy of the PRODUCT_AWJ dimension.
        MdmLevelHierarchy mdmProdHier =
          mdmProdDim.findOrCreateLevelHierarchy("PRODUCT_PRIMARY");

        // Get the detail dimenson level of the PRODUCT_AWJ dimension.
        MdmDimensionLevel mdmItemDimLevel =
          mdmProdDim.findOrCreateDimensionLevel("ITEM");
        // Get the hierarchy level of the dimension level.
        MdmHierarchyLevel mdmItemHierLevel =
                           mdmProdHier.findOrCreateHierarchyLevel(mdmItemDimLevel);
        // Get the Source for the hierarchy level.
        Source itemLevel = mdmItemHierLevel.getSource();

        // Get the short description attribute for the PRODUCT_AWJ dimension and
        // the Source for the attribute.
        MdmAttribute mdmProdShortDescrAttr =
          mdmProdDim.getShortValueDescriptionAttribute();
        Source prodShortDescrAttr = mdmProdShortDescrAttr.getSource();

        // Create a SingleSelectionTemplate to produce a Source that
        // represents the measure values specified by single members of each of
        // the dimensions of the measure other than the base dimension.
        SingleSelectionTemplate singleSelections =
          new SingleSelectionTemplate(units, dp);

        // Create MdmDimensionMemberInfo objects for single members of the
        // other dimensions of the measure.
        MdmDimensionMemberInfo timeMemInfo =
          new MdmDimensionMemberInfo(mdmTimeDim, "CALENDAR_YEAR::YEAR::CY2001");
        MdmDimensionMemberInfo custMemInfo =
          new MdmDimensionMemberInfo(mdmCustDim, "SHIPMENTS::REGION::APAC");
        MdmDimensionMemberInfo chanMemInfo =
          new MdmDimensionMemberInfo(mdmChanDim, "CHANNEL_PRIMARY::CHANNEL::DIR");

        // Add the dimension member information objects to the
        // SingleSelectionTemplate.
        singleSelections.addDimMemberInfo(custMemInfo);
        singleSelections.addDimMemberInfo(chanMemInfo);
        singleSelections.addDimMemberInfo(timeMemInfo);

        // Create a TopBottomTemplate specifying, as the base, the Source for a
        // a level of a hierarchy.
        TopBottomTemplate topNBottom = new TopBottomTemplate(itemLevel, dp);

        // Specify whether to retrieve the elements from the beginning (top) or the
        // end (bottom) of the selected elements of the base dimension.
        topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_TOP);

        // Set the number of elements of the base dimension to retrieve.
        topNBottom.setN(10);
        // Get the Source produced by the SingleSelectionTemplate and specify it as
        // the criterion object.
        topNBottom.setCriterion(singleSelections.getSource());

        // End of code not shown in
        // Example 7-3.

        // Display a description of the result.
        String resultDescription = " products with the most units sold \nfor";
        displayResultDescr(singleSelections, topNBottom, resultDescription);

        // Get the Source produced by the TopBottomTemplate.
        Source result = topNBottom.getSource();

        // Join the Source produced by the TopBottomTemplate with the short
        // value descriptions. Use the joinHidden method so that the
        // dimension member values do not appear in the result.
        Source result = prodShortDescrAttr.joinHidden(topNBottomResult);

        // Commit the current transaction.
        getContext().commit();  // Method of Context11g.

        // Create a Cursor for the result and display the values of the Cursor.
        getContext().displayTopBottomResult(result);

        // Change a dimension member selection of the SingleSelectionTemplate.
        timeMemInfo.setUniqueValue("CALENDAR_YEAR::YEAR::CY2000");
        singleSelections.changeSelection(timeMemInfo);

        // Change the number of elements selected and the type of selection.
        topNBottom.setN(5);
        topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_BOTTOM);

        // Join the Source produced by the TopBottomTemplate to the short
        // description attribute.
        result = prodShortDescrAttr.joinHidden(topNBottomResult);

        // Commit the current transaction.
        getContext().commit();

        // Display a description of the result.
        resultDescription = " products with the fewest units sold \nfor";
        displayResultDescr(singleSelections, topNBottom, resultDescription);

        // Create a new Cursor for the Source produced by the TopBottomTemplate
        // and display the Cursor values.
        getContext().displayTopBottomResult(result);

        // Now change the measure to SALES, and get the top and bottom products by
        // SALES.
        singleSelections.setMeasure(sales);
        // Change the number of elements selected.
        topNBottom.setN(7);
        // Change the type of selection back to the top.
        topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_TOP);

        resultDescription = " products with the highest sales amounts \nfor";
        displayResultDescr(singleSelections, topNBottom, resultDescription);

        topNBottomResult = topNBottom.getSource();
        result = prodShortDescrAttr.joinHidden(topNBottomResult);

        // Commit the current transaction.
        getContext().commit();
        getContext().displayTopBottomResult(result);

        // Change the type of selection back to the bottom.
        topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_BOTTOM);

        resultDescription = " products with the lowest sales amounts \nfor";
        displayResultDescr(singleSelections, topNBottom, resultDescription);

        topNBottomResult = topNBottom.getSource();
        result = prodShortDescrAttr.joinHidden(topNBottomResult);

        // Commit the current transaction.
        getContext().commit();
        getContext().displayTopBottomResult(result);

      }

      /**
       * Displays a description of the results of the query.
       *
       * @param singleSelections The SingleSelectionsTemplate used by the query.
       *
       * @param topNBottom The TopBottomTemplate used by the query.
       *
       * @param resultDescr A String that contains a description of the query.
       */
      private void displayResultDescr(SingleSelectionTemplate singleSelections,
                                      TopBottomTemplate topNBottom,
                                      String resultDescr)
      {
        DataProvider dp = getContext().getDataProvider();

        // Get the short descriptions of the dimension members of the
        // SingleSelectionTemplate.
        StringBuffer shortDescrsForMemberVals =
          singleSelections.getMemberShortDescrs(dp);

        // Display the number of dimension members selected, the result description,
        // and the short descriptions of the single selection dimension members.
        println("\nThe " + Math.round(topNBottom.getN()) + resultDescr
                + shortDescrsForMemberVals +" are:\n");
      }

      /**
       * Runs the TopBottomTest application.
       *
       * @param args An array of String objects that provides the arguments
       *             required to connect to an Oracle Database instance, as
       *             specified in the Context11g class.
       */
      public static void main(String[] args)
      {
        new TopBottomTest().execute(args);
      }

}

The `TopBottomTest` program produces the following output.

    The 10 products with the most units sold
    for Asia Pacific, Direct Sales, 2001 are:

     1. Mouse Pad
     2. Unix/Windows 1-user pack
     3. Deluxe Mouse
     4. Laptop carrying case
     5. 56Kbps V.90 Type II Modem
     6. 56Kbps V.92 Type II Fax/Modem
     7. Keyboard Wrist Rest
     8. Internal - DVD-RW - 6X
     9. O/S Documentation Set - English
    10. External - DVD-RW - 8X

    The 5 products with the fewest units sold
    for Asia Pacific, Direct Sales, 2000 are:

     1. Envoy External Keyboard
     2. O/S Documentation Set - Italian
     3. External 48X CD-ROM
     4. O/S Documentation Set - Spanish
     5. Internal 48X CD-ROM USB

    The 7 products with the highest sales amounts
    for Asia Pacific, Direct Sales, 2000 are:

     1. Sentinel Financial
     2. Sentinel Standard
     3. Envoy Executive
     4. Sentinel Multimedia
     5. Envoy Standard
     6. Envoy Ambassador
     7. 56Kbps V.90 Type II Modem

    The 7 products with the lowest sales amounts
    for Asia Pacific, Direct Sales, 2000 are:

     1. Envoy External Keyboard
     2. Keyboard Wrist Rest
     3. Mouse Pad
     4. O/S Documentation Set - Italian
     5. O/S Documentation Set - Spanish
     6. Standard Mouse
     7. O/S Documentation Set - French
