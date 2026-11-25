You create a query by producing a `Source` that specifies the data that you want to retrieve and any operations that you want to perform on that data. To produce the query, you begin with the primary `Source` objects that represent the metadata of the measures and the dimensions and their attributes that you want to query. Typically, you use the methods of the primary `Source` objects to derive a number of other `Source` objects, each of which specifies a part of the query, such as a selection of dimension members or an operation to perform on the data. You then join the `Source` objects that specify the data and the operations that you want. The result is one `Source` that represents the query. You can then retrieve the data by creating a `Cursor` for the `Source`.

This chapter briefly describes the various kinds of `Source` methods, and discusses some of them in greater detail. It also discusses how to make some typical OLAP queries using these methods and provides examples of some of them.

This chapter includes the following topics:

- Describing the Basic Source Methods

- Using the Basic Methods

- Using Other Source Methods

### 6.1 Describing the Basic Source Methods

The `Source` class has many methods that return a derived `Source`. The elements of the derived `Source` result from operations on the base `Source`, which is the `Source` whose method returns the derived `Source`. Only a few methods perform the most basic operations of the `Source` class.

Many other methods of the `Source` class use one or more of the basic methods to perform operations such as selecting elements of the base `Source` by value or by position, or sorting elements. Many of the examples in this chapter and in [Understanding Source Objects](understanding-source-objects.md), use some of these methods. Other `Source` methods get objects that have information about the `Source`, such as the `getID`, `getInputs`, and `getType` methods, perform comparisons, such as the `ge` and `gt` methods, or convert the values of the `Source` from one data type to another, such as the `toDoubleSource` method.

Table 6-1 The Basic Source Methods

| Method          | Description                                                                                                                                                                                                                                                                |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `alias`         | Returns a `Source` that has the same elements as the base `Source`, but has the base `Source` as the type.                                                                                                                                                                 |
| `distinct`      | Returns a `Source` that has the same elements as the base `Source`, except that any elements that are duplicated in the base appear only once in the derived `Source`.                                                                                                     |
| `join`          | Returns a `Source` that has the elements of the base `Source` that are specified by the `joined`, `comparison`, and `comparisonRule` parameters of the method call. If the `visible` parameter is `true`, then the joined `Source` is an output of the resulting `Source`. |
| `position`      | Returns a `Source` that has the positions of the elements of the base `Source`, and that has the base `Source` as an input.                                                                                                                                                |
| `recursiveJoin` | Similar to the `join` method, except that this method, in the `Source` that it returns, orders the elements of the `Source` hierarchically by parent-child relationships.                                                                                                  |
| `value`         | Returns a `Source` that has the same elements as the base `Source`, but that has the base `Source` as an input.                                                                                                                                                            |

The following topics describe the basic `Source` methods and provide some examples of their use.

- Using the Basic Methods

- Using Other Source Methods

### 6.2 Using the Basic Methods

The following topics provide examples of using some of the basic methods.

- Using the alias Method

- Using the distinct Method

- Using the join Method

- Using the position Method

- Using the recursiveJoin Method

- Using the value Method

#### 6.2.1 Using the alias Method

You use the `alias` method to control the matching of a `Source` to an input. For example, if you want to find out if the measure values specified by a member of a dimension of the measure are greater than the measure values specified by the other members of the same dimension, then you need to match the inputs of the measure twice in the same join operation. To do so, you can derive two `Source` objects that are aliases for the same dimension, make them inputs of two `Source` objects that are derived from the measure, join each derived measure `Source` to the associated aliased dimension `Source` objects, and then compare the results.

Example 6-1 performs such an operation. It produces a `Source` that specifies whether the number of units sold for each value of the CHANNEL_AWJ dimension is greater than the number of units sold for the other values of the CHANNEL_AWJ dimension.

The example joins `units`, which is the `Source` for a measure, to `Source` objects that are selections of single values of three of the dimensions of the measure to produce `unitsSel`. The `unitsSel` `Source` specifies the `units` elements for the dimension values that are specified by the `timeSel`, `custSel`, and `prodSel` objects, which are outputs of `unitsSel`. The `unitsSel` `Source` has the `Source` for CHANNEL_AWJ dimension as an input.

The `timeSel`, `custSel`, and `prodSel` `Source` objects specify single values from hierarchies of the TIME_AWJ, CUSTOMER_AWJ, and PRODUCT_AWJ dimensions, respectively. The `timeSel` value is `CALENDAR_YEAR::MONTH::2001.01`, which identifies the month January, 2001, the `custSel` value is `SHIPMENTS::SHIP_TO::BUSN WRLD SJ`, which identifies the Business World San Jose customer, and the `prodSel` value is `PRODUCT_PRIMARY::ITEM::ENVY ABM`, which identifies the Envoy Ambassador portable PC.

The example next creates two aliases, `chanAlias1` and `chanAlias2`, for `chanHier`, which is the `Source` for the CHANNEL_PRIMARY hierarchy of the CHANNEL_AWJ dimension. It then produces `unitsSel1` by joining `unitsSel` with the `Source` returned by `chanAlias1.value()`. The `unitsSel1` `Source` has the elements and outputs of `unitsSel` and it has `chanAlias1` as an input. Similarly, the example produces `unitsSel2`, which has `chanAlias2` as an input.

The example uses the `gt` method of `unitsSel1`, which determines whether the values of `unitsSel1` are greater than the values of `unitsSel2`. The final join operations match `chanAlias1` with the input of `unitsSel1` and match `chanAlias2` with the input of `unitsSel2`.

Example 6-1 Controlling Input-with-Source Matching with the alias Method

    Source unitsSel = units.join(timeSel).join(custSel).join(prodSel);
    Source chanAlias1 = chanHier.alias();
    Source chanAlias2 = chanHier.alias();
    NumberSource unitsSel1 = (NumberSource)
                              unitsSel.join(chanAlias1.value());
    NumberSource unitsSel2 = (NumberSource)
                              unitsSel.join(chanAlias2.value());
    Source result = unitsSel1.gt(unitsSel2)
                             .join(chanAlias1)   // Output 2, column
                             .join(chanAlias2);  // Output 1, row;

The `result` `Source` specifies the query, "Are the units sold values of `unitsSel1` for the channel values of `chanAlias1` greater than the units sold values of `unitsSel2` for the channel values of `chanAlias2`?" Because `result` is produced by the joining of `chanAlias2` to the `Source` returned by `unitsSel1.gt(unitsSel2).join(chanAlias1)`, `chanAlias2` is the first output of `result`, and `chanAlias1` is the second output of `result`.

A `Cursor` for the `result` `Source` has as values the `boolean` values that answer the query. The values of the first output of the `Cursor` are the channel values specified by `chanAlias2` and the values of the second output are the channel values specified by `chanAlias1`.

The following is a display of the values of the `Cursor` formatted as a crosstab with headings added. The column edge values are the values from `chanAlias1`, and the row edge values are the values from `chanAlias2`. The values of the crosstab cells are the `boolean` values that indicate whether the units sold value for the column channel value is greater than the units sold value for the row channel value. For example, the crosstab values in the first column indicate that the units sold value for the column channel value `Total Channel` is not greater than the units sold value for the row `Total Channel` value but it is greater than the units sold value for the `Direct Sales`, `Catalog`, and `Internet` row values.

                   ----------------- chanAlias1 ----------------
    chanAlias2     TotalChannel  Catalog  Direct Sales    Internet
    ------------   ------------  -------  ------------  --------
    TotalChannel      false       false      false       false
    Catalog           true        false      false       false
    Direct Sales      true        true       false       false
    Internet          true        true       true        false

#### 6.2.2 Using the distinct Method

You use the `distinct` method to produce a `Source` that does not have any duplicated values, as shown in Example 6-2. The example joins two selections of dimension members. Some dimension members exist in both selections. The example uses the `distinct` method to produce a `Source` that contains only unique dimension members, with no duplicated values.

The example gets the `MdmStandardDimension` object for the CUSTOMER_AWJ dimension and gets the `MdmLevelHierarchy` object for the MARKETS hierarchy of that dimension. It gets the `StringSource` object, `mktHier`, for the `MdmLevelHierarchy`. It then uses the `selectValues` method of `mktHier` to produce two selections of members of the hierarchy, `customersToSelect` and `moreCustomersToSelect`. Two of the members of `customersToSelect` are also present in `moreCustomersToSelect`.

The example uses the `appendValues` method to combine the elements of `customersToSelect` and `moreCustomersToSelect` in the `combinedCustomers` `Source`. Finally, the example uses the `distinct` method of `combinedCustomers`, which returns a `Source`, `distinctCombinedCustomers`, that has only the distinct members of the hierarchy.

Example 6-2 Using the distinct Method

    MdmStandardDimension mdmCustDim =
      mdmDBSchema.findOrCreateStandardDimension("CUSTOMER_AWJ");
    MdmLevelHierarchy mdmMktHier =
      mdmCustDim.findOrCreateLevelHierarchy("MARKETS");
    StringSource mktHier = (StringSource)mdmMktHier.getSource();

    Source customersToSelect =
      mktHier.selectValues(new String[] {"MARKETS::SHIP_TO::KOSH ENT BOS",
                                         "MARKETS::SHIP_TO::KOSH ENT TOK",
                                         "MARKETS::SHIP_TO::KOSH ENT WAN"});
    Source moreCustomersToSelect =
      mktHier.selectValues(new String[] {"MARKETS::SHIP_TO::KOSH ENT BOS",
                                         "MARKETS::SHIP_TO::KOSH ENT TOK",
                                         "MARKETS::SHIP_TO::BUSN WRLD NY",
                                         "MARKETS::SHIP_TO::BUSN WRLD SJ"});
    Source combinedCustomers =
      customersToSelect.appendValues(moreCustomersToSelect);

    Source distinctCombinedCustomers = combinedCustomers.distinct();

A `Cursor` for the `combinedCustomers` `Source` has the following values:

    MARKETS::SHIP_TO::KOSH ENT BOS
    MARKETS::SHIP_TO::KOSH ENT TOK
    MARKETS::SHIP_TO::KOSH ENT WAN
    MARKETS::SHIP_TO::KOSH ENT BOS
    MARKETS::SHIP_TO::KOSH ENT TOK
    MARKETS::SHIP_TO::BUSN WRLD NY
    MARKETS::SHIP_TO::BUSN WRLD SJ

A `Cursor` for the `distinctCombinedCustomers` `Source` has the following values:

    MARKETS::SHIP_TO::KOSH ENT BOS
    MARKETS::SHIP_TO::KOSH ENT TOK
    MARKETS::SHIP_TO::KOSH ENT WAN
    MARKETS::SHIP_TO::BUSN WRLD NY
    MARKETS::SHIP_TO::BUSN WRLD SJ

#### 6.2.3 Using the join Method

As described in [Understanding Source Objects](understanding-source-objects.md), you use the `join` method to produce a `Source` that has the elements of the base `Source` that are determined by the `joined`, `comparison`, and `comparisonRule` parameters of the method. The `visible` parameter determines whether the `joined` parameter `Source` is an output of the `Source` produced by the join operation. You also use the `join` method to match a `Source` with an input of the base or `joined` parameter `Source`.

Most of the examples in this chapter use one or more signatures of the `join` method, as do many of the examples in [Understanding Source Objects](understanding-source-objects.md). Example 6-3 uses the full `join` signature and the simplest `join` signature. In the example, the full `join` signature demonstrates the use of `COMPARISON_RULE_DESCENDING` as the `comparisonRule` parameter.

Example 6-3 uses the following `Source` objects.

- `prodSelWithShortDescr`, which is the `Source` produced by joining the short description attribute of the PRODUCT_AWJ dimension with the `Source` for the FAMILY hierarchy level of the PRODUCT_PRIMARY hierarchy of the dimension.

- `salesMeasure`, which is the `Source` for the SALES measure of the UNITS_CUBE_AWJ cube.

- `timeSelWithShortDescr`, which is the `Source` produced by joining the short description attribute of the TIME_AWJ dimension with the `Source` for a selected member of the CALENDAR_YEAR hierarchy of the dimension.

- `custSelWithShortDescr`, which is the `Source` produced by joining the short description attribute of the CUSTOMER_AWJ dimension with the `Source` for a selected member of the SHIPMENTS hierarchy of the dimension.

- `chanSelWithShortDescr`, which is the `Source` produced by joining the short description attribute of the CHANNEL_AWJ dimension with the `Source` for a selected member of the CHANNEL_PRIMARY hierarchy of the dimension.

The first join operation uses the full signature of the `join` method with `prodSelWithShortDescr` as the base `Source`, `salesMeasure` as the joined `Source`, the `Source` for the Number data type as the comparison `Source`, and `COMPARISON_RULE_DESCENDING` as the comparison rule. The `Source` returned by that join operation has the product family level members and related product short description values as base values and an output that has the sales amounts in descending order.

The next three join operations join the single member selections of the other three dimensions of the measure. The `result` `Source` specifies the product family level members in descending order of sales amounts for the month of May, 2001 for all customers and all channels.

Example 6-3 Using COMPARISON_RULE_DESCENDING

    Source result = prodSelWithShortDescr.join(salesMeasure,
                                               salesMeasure.getDataType(),
                                               Source.COMPARISON_RULE_DESCENDING,
                                               true)
                                         .join(timeSelWithShortDescr)
                                         .join(custSelWithShortDescr)
                                         .join(chanSelWithShortDescr);

A `Cursor` for the `result` `Source` has the following values, displayed as a table. The table includes only the short value descriptions of the hierarchy members and the sales amount values, and has headings and formatting added.

    Total Channel
    Total Customer
    MAY-01

    Total Sales Amounts   Product Family
    -------------------   -----------------
       3,580,239.72       Desktop PCs
       2,508,560.92       Portable PCs
         891,807.30       CD/DVD
         632,376.84       Modems/Fax
         444,444.38       Memory
         312,389.39       Accessories
         291,510.88       Monitors
         222,995.92       Operating Systems
          44,479.32       Documentation

#### 6.2.4 Using the position Method

You use the `position` method to produce a `Source` that has the positions of the elements of the base and has the base as an input. Example 6-4 uses the `position` method in producing a `Source` that specifies the selection of the first and last members of the levels of a hierarchy of the TIME_AWJ dimension.

In the example, `mdmTimeDim` is the `MdmPrimaryDimension` for the TIME_AWJ dimension. The example gets the level attribute and the CALENDAR_YEAR hierarchy of the dimension. It then gets `Source` objects for the attribute and the hierarchy.

Next, the example creates an array of `Source` objects and gets a `List` of the `MdmHierarchyLevel` components of the hierarchy. It gets the `Source` object for each level and adds it to the array, and then creates a list `Source` that has the `Source` objects for the levels as element values.

The example then produces `levelMembers`, which is a `Source` that specifies the members of the levels of the hierarchy. Because the `comparison` parameter of the join operation is the `Source` produced by `levelList.value()`, `levelMembers` has `levelList` as an input. Therefore, `levelMembers` is a `Source` that returns the members of each level, by level, when the input is matched in a join operation.

The `range` `Source` specifies a range of elements from the second element to the next to last element of a `Source`.

The next join operation produces the `firstAndLast` `Source`. The base of the operation is `levelMembers`. The `joined` parameter is the `Source` that results from the `levelMembers.position()` method. The `comparison` parameter is the `range` `Source` and the comparison rule is `COMPARISON_RULE_REMOVE`. The value of the `visible` parameter is `true`. The `firstAndLast` `Source` therefore specifies only the first and last members of the levels because it removes all of the other members of the levels from the selection. The `firstAndLast` `Source` still has `levelList` as an input.

The final join operation matches the input of `firstAndLast` with `levelList`.

Example 6-4 Selecting the First and Last Time Elements

    MdmAttribute mdmTimeLevelAttr = mdmTimeDim.getLevelAttribute();
    MdmLevelHierarchy mdmCalHier =
      mdmTimeDim.findOrCreateLevelHierarchy("CALENDAR_YEAR");

    Source levelRel = mdmTimeLevelAttr.getSource();
    StringSource calHier = (StringSource) mdmCalHier.getSource();

    Source[] levelSources = new Source[3];
    List levels = mdmCalHier.getHierarchyLevels();
    for (int i = 0; i < levelSources.length; i++)
    {
      levelSources[i] = ((MdmHierarchyLevel) levels.get(i)).getSource();
    }
    Source levelList = dp.createListSource(levelSources);
    Source levelMembers =  calHier.join(levelRel, levelList.value());
    Source range = dp.createRangeSource(2, levelMembers.count().minus(1));
    Source firstAndLast = levelMembers.join(levelMembers.position(),
                                            range,
                                            Source.COMPARISON_RULE_REMOVE,
                                            true);

    Source result = firstAndLast.join(levelList);

A `Cursor` for the `result` `Source` has the following values, displayed as a table with column headings and formatting added. The left column names the level, the middle column is the position of the member in the level, and the right column is the local value of the member. The TOTAL_TIME level has only one member.

    Level       Member Position in Level  Member Value
    ----------  ------------------------  ------------
    TOTAL_TIME               1              TOTAL
    YEAR                     1              CY1998
    YEAR                    10              CY2007
    QUARTER                  1              CY1998.Q1
    QUARTER                 40              CY2007.Q4
    MONTH                    1              1998.01
    MONTH                  120              2007.12

#### 6.2.5 Using the recursiveJoin Method

You use the `recursiveJoin` method to produce a `Source` that has elements that are ordered hierarchically. You use the `recursiveJoin` method only with the `Source` for an `MdmHierarchy` or with a subtype of such a `Source`. The method produces a `Source` whose elements are ordered hierarchically by the parents and their children in the hierarchy.

Like the `join` method, you use the `recursiveJoin` method to produce a `Source` that has the elements of the base `Source` that are determined by the `joined`, `comparison`, and `comparisonRule` parameters of the method. The `visible` parameter determines whether the joined `Source` is an output of the `Source` produced by the recursive join operation.

The full `recursiveJoin` method has other parameters that specify the parent attribute of the hierarchy, whether the result should have the parents before or after their children, and how to order the elements of the result if the result includes children but not the parent. The `recursiveJoin` method has several signatures that are shortcuts for the full signature.

Example 6-5 uses a `recursiveJoin` method that lists the parents first, restricts the parents to the base, and does not add the joined `Source` as an output. The example first sorts the members of the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension by hierarchical levels and then by the value of the package attribute of each member.

In the first `recursiveJoin` method, the `COMPARISON_RULE_ASCENDING` parameter specifies that the members of the `prodHier` hierarchy be in ascending alphabetical order within each level. The `prodParentAttr` object is the `Source` for the parent attribute of the hierarchy.

The `prodPkgAttr` object in the second `recursiveJoin` method is the `Source` for the package attribute of the dimension. Only the members of the ITEM level have a related package attribute value. Because the members in the aggregate levels TOTAL_PRODUCT, CLASS, and FAMILY, do not have a related package, the package attribute value for members in those levels is `null`, which appears as `NA` in the results. Some of the ITEM level members do not have a related package value, so their values are `NA`, also.

The second `recursiveJoin` method joins the package attribute values to their related hierarchy members and sorts the members hierarchically by level, and then sorts them in ascending alphabetical order in the level by the package attribute value. The `COMPARISON_RULE_ASCENDING_NULLS_FIRST` parameter specifies that members that have a `null` value appear before the other members in the same level. The example then joins the result of the method, `sortedHierAscending`, to the package attribute to produce a `Source` that has the package attribute values as element values and `sortedHierAscending` as an output.

The third `recursiveJoin` method is the same as the second, except that the `COMPARISON_RULE_DESCENDING_NULLS_FIRST` parameter sorts the hierarchy members in descending alphabetical order in the level by package attribute value.

Example 6-5 Sorting Products Hierarchically by Attribute

    Source result1 = prodHier.recursiveJoin(prodDim.value(),
                                            prodHier.getDataType(),
                                            prodParentAttr,
                                            Source.COMPARISON_RULE_ASCENDING);

    Source sortedHierAscending =
      prodHier.recursiveJoin(prodPkgAttr,
                             prodPkgAttr.getDataType(),
                             prodParentAttr,
                             Source.COMPARISON_RULE_ASCENDING_NULLS_FIRST);
    Source result2 = prodPkgAttr.join(sortedHierAscending);

    Source sortedHierDescending =
      prodHier.recursiveJoin(prodPkgAttr,
                             prodPkgAttr.getDataType(),
                             prodParentAttr,
                             Source.COMPARISON_RULE_DESCENDING_NULLS_FIRST);
    Source result3 = prodPkgAttr.join(sortedHierDescending);

A `Cursor` for the `result1` `Source` has the following values, displayed with a heading added. The list contains only the first seventeen values of the `Cursor`.

    Product Primary Hierarchy Value
    -------------------------------------
    PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
    PRODUCT_PRIMARY::CLASS::HRD
    PRODUCT_PRIMARY::FAMILY::DISK
    PRODUCT_PRIMARY::ITEM::EXT CD ROM
    PRODUCT_PRIMARY::ITEM::EXT DVD
    PRODUCT_PRIMARY::ITEM::INT 8X DVD
    PRODUCT_PRIMARY::ITEM::INT CD ROM
    PRODUCT_PRIMARY::ITEM::INT CD USB
    PRODUCT_PRIMARY::ITEM::INT RW DVD
    PRODUCT_PRIMARY::FAMILY::DTPC
    PRODUCT_PRIMARY::ITEM::SENT FIN
    PRODUCT_PRIMARY::ITEM::SENT MM
    PRODUCT_PRIMARY::ITEM::SENT STD
    PRODUCT_PRIMARY::FAMILY::LTPC
    PRODUCT_PRIMARY::ITEM::ENVY ABM
    PRODUCT_PRIMARY::ITEM::ENVY EXE
    PRODUCT_PRIMARY::ITEM::ENVY STD
    ...

A `Cursor` for the `result2` `Source` has the following values, displayed as a table with headings added. The table contains only the first seventeen values of the `Cursor`. The left column has the member values of the hierarchy and the right column has the package attribute value for the member.

The ITEM level members that have a `null` value appear first, and then the other level members appear in ascending order of package value. Since the data type of the package attribute is String, the package values are in ascending alphabetical order.

    Product Primary Hierarchy Value        Package Attribute Value
    -------------------------------------  -----------------------
    PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL     NA
    PRODUCT_PRIMARY::CLASS::HRD               NA
    PRODUCT_PRIMARY::FAMILY::DISK             NA
    PRODUCT_PRIMARY::ITEM::EXT CD ROM         NA
    PRODUCT_PRIMARY::ITEM::INT 8X DVD         NA
    PRODUCT_PRIMARY::ITEM::INT CD USB         NA
    PRODUCT_PRIMARY::ITEM::EXT DVD            Executive
    PRODUCT_PRIMARY::ITEM::INT CD ROM         Laptop Value Pack
    PRODUCT_PRIMARY::ITEM::INT RW DVD         Multimedia
    PRODUCT_PRIMARY::FAMILY::DTPC             NA
    PRODUCT_PRIMARY::ITEM::SENT FIN           NA
    PRODUCT_PRIMARY::ITEM::SENT STD           NA
    PRODUCT_PRIMARY::ITEM::SENT MM            Multimedia
    PRODUCT_PRIMARY::FAMILY::LTPC             NA
    RODUCT_PRIMARY::ITEM::ENVY ABM            NA
    PRODUCT_PRIMARY::ITEM::ENVY EXE           Executive
    PRODUCT_PRIMARY::ITEM::ENVY STD           Laptop Value Pack
    ...

A `Cursor` for the `result3` `Source` has the following values, displayed as a table with headings added. This time the members are in descending order, alphabetically by package attribute value.

    Product Primary Hierarchy Value        Package Attribute Value
    -------------------------------------  -----------------------
    PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL     NA
    PRODUCT_PRIMARY::CLASS::HRD               NA
    PRODUCT_PRIMARY::FAMILY::DISK             NA
    PRODUCT_PRIMARY::ITEM::EXT CD ROM         NA
    PRODUCT_PRIMARY::ITEM::INT 8X DVD         NA
    PRODUCT_PRIMARY::ITEM::INT CD USB         NA
    PRODUCT_PRIMARY::ITEM::INT RW DVD         Multimedia
    PRODUCT_PRIMARY::ITEM::INT CD ROM         Laptop Value Pack
    PRODUCT_PRIMARY::ITEM::EXT DVD            Executive
    PRODUCT_PRIMARY::FAMILY::DTPC             NA
    PRODUCT_PRIMARY::ITEM::SENT FIN           NA
    PRODUCT_PRIMARY::ITEM::SENT STD           NA
    PRODUCT_PRIMARY::ITEM::SENT MM            Multimedia
    PRODUCT_PRIMARY::FAMILY::LTPC             NA
    PRODUCT_PRIMARY::ITEM::ENVY ABM           NA
    PRODUCT_PRIMARY::ITEM::ENVY STD           Laptop Value Pack
    PRODUCT_PRIMARY::ITEM::ENVY EXE           Executive
    ...

#### 6.2.6 Using the value Method

As described in "[Deriving a Source with an Input](understanding-source-objects.md)", you use the `value` method to create a `Source` that has itself as an input. That relationship enables you to select a subset of elements of the `Source`. You can also use the value method to reverse a relation.

The following topics have examples of these operations.

- Selecting Elements of a Source

- Reversing a Relation

##### 6.2.6.1 Selecting Elements of a Source

[Example 5-11](understanding-source-objects.md) and Example 6-6 demonstrate the selection of a subset of the elements of a `Source`. In Example 6-6, `shipHier` is a `Source` for the SHIPMENTS hierarchy of the CUSTOMER_AWJ dimension. The `selectValues` method of `shipHier` produces `custSel`, which is a selection of some of the elements of `shipHier`. The `selectValues` method of `custSel` produces `custSel2`, which is a subset of that selection.

The first `join` method has `custSel` as the base and as the joined `Source`. It has `custSel2` as the comparison `Source`. The elements of the resulting `Source`, `result1`, are the Cartesian product of the base and joined `Source` objects that are specified by the comparison `Source`. The `result1` `Source` has one set of the elements of `custSel` for each element of `custSel` that is in the comparison `Source`. The `true` value of the `visible` parameter causes the joined `Source` to be an output of `result1`.

The second `join` method also has `custSel` as the base and `custSel2` as the comparison `Source`, but it has the `Source` returned by the `custSel.value()` method as the joined `Source`. Because `custSel` is an input of the joined `Source`, the base `Source` matches with that input. That input relationship causes the resulting `Source`, `result2`, to have only those elements of `custSel` that are also in the comparison `Source`.

Example 6-6 Selecting a Subset of the Elements of a Source

    StringSource custSel = shipHier.selectValues(new String[]
                                             {"SHIPMENTS::SHIP_TO::COMP WHSE SIN",
                                              "SHIPMENTS::SHIP_TO::COMP WHSE LON",
                                              "SHIPMENTS::SHIP_TO::COMP WHSE SJ",
                                              "SHIPMENTS::SHIP_TO::COMP WHSE ATL"});

    Source custSel2 = custSel.selectValues(new String[]
                                             {"SHIPMENTS::SHIP_TO::COMP WHSE SIN",
                                              "SHIPMENTS::SHIP_TO::COMP WHSE SJ"});

    Source result1 = custSel.join(custSel, custSel2, true);

    Source  result2 = custSel.join(custSel.value(), custSel2, true);

A `Cursor` for `result1` has the values shown in the following table. The table has formatting and headings that are not in the `Cursor`. The left column has the values of the elements of the output of the `Cursor`. The right column has the base values of the `Cursor`.

              Output Value                        result1 Value
    ---------------------------------   ---------------------------------
    SHIPMENTS::SHIP_TO::COMP WHSE SJ    SHIPMENTS::SHIP_TO::COMP WHSE ATL
    SHIPMENTS::SHIP_TO::COMP WHSE SJ    SHIPMENTS::SHIP_TO::COMP WHSE SJ
    SHIPMENTS::SHIP_TO::COMP WHSE SJ    SHIPMENTS::SHIP_TO::COMP WHSE SIN
    SHIPMENTS::SHIP_TO::COMP WHSE SJ    SHIPMENTS::SHIP_TO::COMP WHSE LON
    SHIPMENTS::SHIP_TO::COMP WHSE SIN   SHIPMENTS::SHIP_TO::COMP WHSE ATL
    SHIPMENTS::SHIP_TO::COMP WHSE SIN   SHIPMENTS::SHIP_TO::COMP WHSE SJ
    SHIPMENTS::SHIP_TO::COMP WHSE SIN   SHIPMENTS::SHIP_TO::COMP WHSE SIN
    SHIPMENTS::SHIP_TO::COMP WHSE SIN   SHIPMENTS::SHIP_TO::COMP WHSE LON

A `Cursor` for `result2` has the following values, displayed as a table with headings added. The left column has the values of the elements of the output of the `Cursor`. The right column has the base values of the `Cursor`.

              Output Value                        result2 Value
    ---------------------------------   ---------------------------------
    SHIPMENTS::SHIP_TO::COMP WHSE SJ    SHIPMENTS::SHIP_TO::COMP WHSE SJ
    SHIPMENTS::SHIP_TO::COMP WHSE SIN   SHIPMENTS::SHIP_TO::COMP WHSE SIN

##### 6.2.6.2 Reversing a Relation

Another use of the `value` method is to reverse a relation, as shown in Example 6-7. The example reverses the ancestor attribute relation of the CUSTOMER_AWJ dimension to produce a `Source`, `marketsDescendants`, that represents a descendants relation. The `marketsDescendants` `Source` has as an input the `Source` for the MARKETS hierarchy of the dimension. When you join `marketsDescendants` with a `Source` that matches with that input, you get a `Source` that specifies the descendants of the participating members of the hierarchy.

Another example of reversing a relation is Example 6-10. It uses the `value` method in reversing the parent attribute to get the children of a parent.

Example 6-7 first gets the `MdmStandardDimension` object for the CUSTOMER_AWJ dimension and the `MdmLevelHierarchy` object for the MARKETS hierarchy of that dimension. It gets the `Source` for the hierarchy.

The example next gets the ancestors attribute of the dimension and the `Source` for it. The ancestors attribute relates each dimension member to the ancestors of that member.

To produce a `Source` that represents the descendants of each member of the dimension, the example reverses the ancestor relation by joining the `Source` for the hierarchy, `mktHier`, with the ancestors attribute, `ancestorsAttr`. The join operation uses `mktHier.value()` as the comparison `Source`, so that the `Source` returned by the join operation, `marketsDescendants`, has `mktHier` as an input. The `marketsDescendants` `Source` specifies, for each element of `ancestorsAttr`, the elements of `mktHier` that have the `ancestorsAttr` element as their ancestor. Because it has `mktHier` as an input, the `marketsDescendants` `Source` functions in the same way as an attribute that represents the descendants relationship for the hierarchy.

The example demonstrates this when it joins `mktHier` to `marketsDescendants` in the following line.

    Source selValDescendants = marketsDescendants.join(mktHier, selVal);

In the join operation, the joined `Source`, `mktHier`, matches with the input of `marketsDescendants`. The comparison `Source` is `selVal`, which specifies a single member of the hierarchy. The join operation returns `selValDescendants`, which specifies the elements of `marketsDescendants` that are the descendants of the `selVal` member. The result also includes the ancestor member itself. The `mktHier` `Source` is not an output of `selValDescendants` because the signature of the `join` method used derives a `Source` that does not have the joined `Source` as an output.

The example next uses the full signature of the `join` method to produce `selValDescendantsOnly`, which contains only the descendants and not the ancestor value. To remove the ancestor value, the example again uses the `value` method, this time to return a `Source` that is the `joined` parameter of the join operation that returns `selValDescendantsOnly`. The comparison `Source` is `selVal`, and the comparison rule is `COMPARISON_RULE_REMOVE`.

Finally, the example uses the `removeValue` method to produce `selValDescendantsOnly2`, which is the same as `selValDescendantsOnly`. This simply demonstrates that the `removeValue` method is a shortcut for the join operation that returned `selValDescendantsOnly`.

Example 6-7 Using the value Method to Reverse a Relation

    MdmStandardDimension mdmCustDim =
      mdmDBSchema.findOrCreateStandardDimension("CUSTOMER_AWJ");
    MdmLevelHierarchy mdmMktHier =
      mdmCustDim.findOrCreateLevelHierarchy("MARKETS");
    StringSource mktHier = (StringSource)mdmMktHier.getSource();
    MdmAttribute mdmAncestorsAttr = mdmCustDim.getAncestorsAttribute();
    Source ancestorsAttr = mdmAncestorsAttr.getSource();

    // Reverse the ancestors relation to get the descendants relation.
    Source marketsDescendants = mktHier.join(ancestorsAttr, mktHier.value());

    Source selVal = mktHier.selectValue("MARKETS::ACCOUNT::BUSN WRLD");

    // Select the descendants of the specified hierarchy member.
    StringSource selValDescendants =
      (StringSource)marketsDescendants.join(mktHier, selVal);

    // Remove the ancestor value so that only the descendants remain.
    Source selValDescendantsOnly =
      selValDescendants.join(selValDescendants.value(),
                             selVal,
                             Source.COMPARISON_RULE_REMOVE),
                             false;

    // Produce the same result using the removeValue method.
    Source selValDescendantsOnly2 =
      selValDescendants.removeValue("MARKETS::ACCOUNT::BUSN WRLD");

A `Cursor` for `selValDescendants` has the following values.

    MARKETS::ACCOUNT::BUSN WRLD
    MARKETS::SHIP_TO::BUSN WRLD HAM
    MARKETS::SHIP_TO::BUSN WRLD NAN
    MARKETS::SHIP_TO::BUSN WRLD NY
    MARKETS::SHIP_TO::BUSN WRLD SJ

A `Cursor` for `selValDescendantsOnly` has the following values.

    MARKETS::SHIP_TO::BUSN WRLD HAM
    MARKETS::SHIP_TO::BUSN WRLD NAN
    MARKETS::SHIP_TO::BUSN WRLD NY
    MARKETS::SHIP_TO::BUSN WRLD SJ

A `Cursor` for `selValDescendantsOnly2` has the following values.

    MARKETS::SHIP_TO::BUSN WRLD HAM
    MARKETS::SHIP_TO::BUSN WRLD NAN
    MARKETS::SHIP_TO::BUSN WRLD NY
    MARKETS::SHIP_TO::BUSN WRLD SJ

### 6.3 Using Other Source Methods

Along with the methods that are various signatures of the basic methods, the `Source` class has many other methods that use combinations of the basic methods. Some methods perform selections based on a single position, such as the `at` and `offset` methods. Others operate on a range of positions, such as the `interval` method. Some perform comparisons, such as `eq` and `gt`, select one or more elements, such as `selectValue` or `removeValue`, or sort elements, such as `sortAscending` or `sortDescendingHierarchically`.

The subclasses of `Source` each have other specialized methods, also. For example, the `NumberSource` class has many methods that perform mathematical functions such as `abs`, `div`, and `cos`, and methods that perform aggregations, such as `average` and `total`.

The following topics have examples that demonstrate the use of some of the `Source` methods. Some of the examples are tasks that an OLAP application typically performs.

- Using the extract Method

- Creating a Cube and Pivoting Edges

- Drilling Up and Down in a Hierarchy

- Sorting Hierarchically by Measure Values

- Using NumberSource Methods To Compute the Share of Units Sold

- Selecting Based on Time Series Operations

- Selecting a Set of Elements Using Parameterized Source Objects

#### 6.3.1 Using the extract Method

You use the `extract` method to extract the values of a `Source` that is the value of an element of another `Source`. If the elements of a `Source` have element values that are not `Source` objects, then the `extract` method operates like the `value` method.

Example 6-8 uses the `extract` method to get the values of the `NumberSource` objects that are themselves the values of the elements of the list `Source` `measDim`. Each of the `NumberSource` objects represents a measure.

The example selects elements from `StringSource` objects for the hierarchies of the dimensions of the UNITS_CUBE_AWJ cube. The `cost`, `units`, and `sales` objects are `NumberSource` objects for the COST, UNITS, and SALES measures of the cube.

Next, the example creates `measDim`, which is a list `Source` that has the three `NumberSource` objects as element values. It then uses the `extract` method to get the values of the `NumberSource` objects. The resulting unnamed `Source` has `measDim` as an extraction input. The first join operation has `measDim.extract()` as the base `Source`. The input of the base `Source` matches with `measDim`, which is the `joined` parameter. The example then matches the other inputs of the measures by joining the dimension selections to produce the `result` `Source`.

Example 6-8 Using the extract Method

    Source prodSel = prodHier.selectValues(new String[]
                                            {"PRODUCT_PRIMARY::ITEM::ENVY STD",
                                             "PRODUCT_PRIMARY::ITEM::ENVY EXE",
                                             "PRODUCT_PRIMARY::ITEM::ENVY ABM"});
    Source chanSel = chanHier.selectValue("CHANNEL_PRIMARY::CHANNEL::DIR");
    Source timeSel = timeHier.selectValue("CALENDAR_YEAR::MONTH::2001.05");
    Source custSel = custHier.selectValue("SHIPMENTS::TOTAL_CUSTOMER::TOTAL");

    Source measDim = dp.createListSource(new Source[] {cost, units, sales});

    Source result = measDim.extract().join(measDim)   // column
                                     .join(prodSel)   // row
                                     .join(timeSel)   // page
                                     .join(chanSel)   // page
                                     .join(custSel);  // page

The following crosstab displays the values of a `Cursor` for the `result` `Source`, with headings and formatting added.

    SHIPMENTS::TOTAL_CUSTOMER::TOTAL
    CHANNEL_PRIMARY::CHANNEL::DIR
    CALENDAR_YEAR::MONTH::2001.05

    ITEM            COST      UNITS SOLD   SALES AMOUNT
    --------     ----------   ----------   -------------
    ENVY ABM      73,316.10       26          77,825.54
    ENVY EXE     111,588.30       37         116,470.45
    ENVY STD      92,692.47       39          93,429.57

#### 6.3.2 Creating a Cube and Pivoting Edges

One typical OLAP operation is the creation of a cube, which is a multi-dimensional array of data. The data of the cube is specified by the elements of the column, row, and page edges of the cube. The data of the cube can be data from a measure that is specified by the members of the dimensions of the measure. The cube data can also be dimension members that are specified by some calculation of the measure data, such as products that have unit sales quantities greater than a specified amount.

Most of the examples in this topic create cubes. Example 6-9 creates a cube that has the quantity of units sold as the data of the cube. The column edge values are initially from a channel dimension hierarchy, the row edge values are from a time dimension hierarchy, and the page edge values are from hierarchies for product and customer dimensions. The product and customer member values on the page edge are represented by parameterized `Source` objects.

The example joins the selections of the hierarchy members to the short value description attributes for the dimensions so that the results include the attribute values. The example then joins the `Source` objects derived from the hierarchies to the `Source` for the measure to produce the `cube` query. It commits the current `Transaction`, and then creates a `Cursor` for the query and displays the values.

After displaying the values of the `Cursor`, the example changes the value of the `Parameter` for the parameterized `Source` for the customer selection, thereby retrieving a different result set using the same `Cursor` in the same `Transaction`. The example resets the position of the `Cursor`, and displays the values of the `Cursor` again.

The example then pivots the column and row edges so that the column values are time members and the row values are channel members. It commits the `Transaction`, creates another `Cursor` for the query, and displays the values. It then changes the value of each `Parameter` object and displays the values of the `Cursor` again.

The `dp` object is the `DataProvider`. The `getContext` method gets a `Context11g` object that has a method that displays the values of the `Cursor` in a crosstab format.

Example 6-9 Creating a Cube and Pivoting the Edges

    // Create Parameter objects with values from the hierarchies
    // of the CUSTOMER_AWJ and PRODUCT_AWJ dimensions.
    StringParameter custParam =
      new StringParameter(dp, "SHIPMENTS::REGION::EMEA");
    StringParameter prodParam =
      new StringParameter(dp, "PRODUCT_PRIMARY::FAMILY::LTPC");

    // Create parameterized Source objects using the Parameter objects.
    Source custParamSrc = custParam.createSource();
    Source prodParamSrc = prodParam.createSource();

    // Select single values from the hierarchies, using the Parameter
    // objects as the comparisons in the join operations.
    Source paramCustSel = custHier.join(custHier.value(), custParamSrc);
    Source paramProdSel = prodHier.join(prodHier.value(), prodParamSrc);

    // Select members from the other dimensions of the measure.
    Source timeSel =
      timeHier.selectValues(new String[] {"CALENDAR_YEAR::YEAR::CY1999"
                                          "CALENDAR_YEAR::YEAR::CY2000",
                                          "CALENDAR_YEAR::YEAR::CY2001"});
    Source chanSel =
      chanHier.selectValues(new String[] {"CHANNEL_PRIMARY::CHANNEL::DIR",
                                          "CHANNEL_PRIMARY::CHANNEL::CAT    ",
                                          "CHANNEL_PRIMARY::CHANNEL::INT"});

    // Join the hierarchy selections to the short description attributes
    // for the dimensions.
    Source columnEdge = chanSel.join(chanShortDescr);
    Source rowEdge = timeSel.join(timeShortDescr);
    Source page1 = paramProdSel.join(prodShortDescr);
    Source page2 = paramCustSel.join(custShortDescr);

    // Join the dimension selections to the measure.
    Source cube = units.join(columnEdge)
                       .join(rowEdge)
                       .join(page2)
                       .join(page1);

    // The following method commits the current Transaction.
    getContext().commit();

    // Create a Cursor for the query.
    CursorManager cursorMngr = dp.createCursorManager(cube);
    CompoundCursor cubeCursor = (CompoundCursor) cursorMngr.createCursor();

    // Display the values of the Cursor as a crosstab.
    getContext().displayCursorAsCrosstab(cubeCursor);

    // Change the customer parameter value.
    custParam.setValue("SHIPMENTS::REGION::AMER");

    // Reset the Cursor position to 1 and display the values again.
    cubeCursor.setPosition(1);
    println();
    getContext().displayCursorAsCrosstab(cubeCursor);

    // Pivot the column and row edges.
    columnEdge = timeSel.join(timeShortDescr);
    rowEdge = chanSel.join(chanShortDescr);

    // Join the dimension selections to the measure.
    cube = units.join(columnEdge)
                .join(rowEdge))
                .join(page2)
                .join(page1);

    // Commit the current Transaction.
    getContext().commit();

    // Create another Cursor.
    cursorMngr = dp.createCursorManager(cube);
    cubeCursor = (CompoundCursor) cursorMngr.createCursor();
    getContext().displayCursorAsCrosstab(cubeCursor);

    // Change the product parameter value.
    prodParam.setValue("PRODUCT_PRIMARY::FAMILY::DTPC");

    // Reset the Cursor position to 1
    cubeCursor.setPosition(1);
    println();
    getContext().displayCursorAsCrosstab(cubeCursor);

The following crosstab has the values of `cubeCursor` displayed by the first `displayCursorAsCrosstab` method.

    Portable PCs
    Europe

            Catalog  Direct Sales  Internet
    1999       1986            86         0
    2000       1777           193        10
    2001       1449           196       215


The following crosstab has the values of `cubeCursor` after the example changed the value of the `custParam` `Parameter` object.

    Portable PCs
    North America

            Catalog  Direct Sales  Internet
    1999       6841           385        0
    2000       6457           622       35
    2001       5472           696      846

The next crosstab has the values of `cubeCursor` after pivoting the column and row edges.

    Portable PCs
    North America

                    1999    2000    2001
    Catalog         6841    6457    5472
    Direct Sales     385     622     696
    Internet           0      35     846

The last crosstab has the values of `cubeCursor` after changing the value of the `prodParam` `Parameter` object.

    Desktop PCs
    North America

                    1999    2000    2001
    Catalog        14057   13210   11337
    Direct Sales     793    1224    1319
    Internet           0      69    1748

#### 6.3.3 Drilling Up and Down in a Hierarchy

Drilling up or down in a dimension hierarchy is another typical OLAP operation. Example 6-10 demonstrates getting the members of one level of a dimension hierarchy, selecting a member, and then getting the parent, children, and ancestors of the member. The example gets the children of a parent by reversing the parent relation to produce the `prodHierChildren` `Source`.

The example uses the following objects.

- `levelSrc`, which is the `Source` for the FAMILY level of the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension.

- `prodHier`, which is the `Source` for the PRODUCT_PRIMARY hierarchy.

- `prodHierParentAttr`, which is the `Source` for the parent attribute of the hierarchy.

- `prodHierAncsAttr`, which is the `Source` for the ancestors attribute of the hierarchy.

- `prodShortLabel`, which is the `Source` for the short value description attribute of the PRODUCT_AWJ dimension.

Example 6-10 Drilling in a Hierarchy

    int pos = 5;
    // Get the element at the specified position of the level Source.
    Source levelElement = levelSrc.at(pos);

    // Get ancestors of the level member.
    Source levelElementAncs = prodHierAncsAttr.join(prodHier, levelElement);
    // Get the parent of the level member.
    Source levelElementParent = prodHierParentAttr.join(prodHier, levelElement);
    // Get the children of a parent.
    Source prodHierChildren = prodHier.join(prodHierParentAttr, prodHier.value());

    // Select the children of the level member.
    Source levelElementChildren = prodHierChildren.join(prodHier, levelElement);

    // Get the short value descriptions for the members of the level.
    Source levelSrcWithShortDescr = prodShortLabel.join(levelSrc);

    // Get the short value descriptions for the children.
    Source levelElementChildrenWithShortDescr =
      prodShortLabel.join(levelElementChildren);

    // Get the short value descriptions for the parents.
    Source levelElementParentWithShortDescr =
      prodShortLabel.join(prodHier, levelElementParent, true);

    // Get the short value descriptions for the ancestors.
    Source levelElementAncsWithShortDescr =
      prodShortLabel.join(prodHier, levelElementAncs, true);

    // Commit the current Transaction.
    getContext().commit();

    // Create Cursor objects and display their values.
    println("Level Source element values:");
    getContext().displayResult(levelSrcWithShortDescr);
    println("\nLevel Source element at position " + pos + ":");
    getContext().displayResult(levelElement);
    println("\nParent of the level member:");
    getContext().displayResult(levelElementParentWithShortDescr);
    println("\nChildren of the level member:");
    getContext().displayResult(levelElementChildrenWithShortDescr);
    println("\nAncestors of the level member:");
    getContext().displayResult(levelElementAncsWithShortDescr);

The following list has the values of the `Cursor` objects created by the `displayResults` methods.

    Level Source element values:
    PRODUCT_PRIMARY::FAMILY::ACC,Accessories
    PRODUCT_PRIMARY::FAMILY::DISK,CD/DVD
    PRODUCT_PRIMARY::FAMILY::DOC,Documentation
    PRODUCT_PRIMARY::FAMILY::DTPC,Portable PCs
    PRODUCT_PRIMARY::FAMILY::LTPC,Desktop PCs
    PRODUCT_PRIMARY::FAMILY::MEM,Memory
    PRODUCT_PRIMARY::FAMILY::MOD,Modems/Fax
    PRODUCT_PRIMARY::FAMILY::MON,Monitors
    PRODUCT_PRIMARY::FAMILY::OS,Operating Systems

    Level Source element at position 5:
    PRODUCT_PRIMARY::FAMILY:LTPC

    Parent of the level member:
    PRODUCT_PRIMARY::CLASS::HRD,Hardware

    Children of the level member:
    PRODUCT_PRIMARY::ITEM::ENVY ABM,Envoy Ambassador
    PRODUCT_PRIMARY::ITEM::ENVY EXE,Envoy Executive
    PRODUCT_PRIMARY::ITEM::ENVY STD,Envoy Standard

    Ancestors of the level member:
    PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL,Total Product
    PRODUCT_PRIMARY::CLASS::HRD,Hardware
    PRODUCT_PRIMARY::FAMILY::LTPC,Portable PCs

#### 6.3.4 Sorting Hierarchically by Measure Values

Example 6-11 uses the `recursiveJoin` method to sort the members of the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension hierarchically in ascending order of the values of the UNITS measure. The example joins the sorted products to the short value description attribute of the dimension, and then joins the result of that operation, `sortedProductsShortDescr`, to `units`.

The successive `joinHidden` methods join the selections of the other dimensions of `units` to produce the `result` `Source`, which has the measure data as element values and `sortedProductsShortDescr` as an output. The example uses the `joinHidden` methods so that the other dimension selections are not outputs of the result.

The example uses the following objects.

- `prodHier`, which is the `Source` for the PRODUCT_PRIMARY hierarchy.

- `units`, which is the `Source` for the UNITS measure of product units sold.

- `prodParentAttr`, which is the `Source` for the parent attribute of the PRODUCT_PRIMARY hierarchy.

- `prodShortDescr`, which is the `Source` for the short value description attribute of the PRODUCT_AWJ dimension.

- `custSel`, which is a `Source` that specifies a single member of the SHIPMENTS hierarchy of the CUSTOMER_AWJ dimension. The member is `SHIPMENTS::TOTAL_CUSTOMER::TOTAL`, which is the total for all customers.

- `chanSel`, which is a `Source` that specifies a single member of the CHANNEL_PRIMARY hierarchy of the CHANNEL_AWJ dimension. The member value is `CHANNEL_PRIMARY::CHANNEL::DIR`, which is the direct sales channel.

- `timeSel`, which is a `Source` that specifies a single member of the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension. The member is `CALENDAR_YEAR::YEAR::CY2001`, which is the year 2001.

Example 6-11 Hierarchical Sorting by Measure Value

    Source sortedProduct =
      prodHier.recursiveJoin(units,
                             units.getDataType(),
                             prodParentAttr,
                             Source.COMPARISON_RULE_ASCENDING,
                             true,  // Parents first
                             true); // Restrict parents to base

    Source sortedProductShortDescr = prodShortDescr.join(sortedProduct);
    Source result = units.join(sortedProductShortDescr)
                         .joinHidden(custSel)
                         .joinHidden(chanSel)
                         .joinHidden(timeSel);

A `Cursor` for the `result` `Source` has the following values, displayed in a table with column headings and formatting added. The left column has the name of the level in the `PRODUCT_PRIMARY` hierarchy. The next column to the right has the product identification value, and the next column has the short value description of the product. The rightmost column has the number of units of the product sold to all customers in the year 2001 through the direct sales channel.

The table contains only the first nine and the last eleven values of the `Cursor`, plus the Software/Other class value. The product values are listed hierarchically and in ascending order by units sold. The Hardware class appears before the Software/Other class because the Software/Other class has a greater number of units sold. In the Hardware class, the Portable PCs family sold the fewest units, so it appears first. In the Software/Other class, the Accessories family has the greatest number of units sold, so it appears last.

    Product Level      ID                 Description           Units Sold
    -------------  ------------   ----------------------------- ----------
    TOTAL_PRODUCT  TOTAL          Total Product                     43,785
    CLASS          HRD            Hardware                          16,543
    FAMILY         LTPC           Portable PCs                       1,192
    ITEM           ENVY ABM       Envoy Ambassador                     330
    ITEM           ENVY EXE       Envoy Executive                      385
    ITEM           ENVY STD       Envoy Standard                       477
    FAMILY         MON            Monitors                           1,193
    ITEM           19 SVGA        Monitor- 19" Super VGA               207
    ITEM           17 SVGA        Monitor- 17"Super VGA                986
    ...
    CLASS          SFT            Software/Other)                   27,242
    ...
    FAMILY         ACC            Accessories                       18,949
    ITEM           ENVY EXT KBD   Envoy External Keyboard              146
    ITEM           EXT KBD        External 101-key keyboard            678
    ITEM           MM SPKR 5      Multimedia speakers- 5" cones        717
    ITEM           STD MOUSE      Standard Mouse                       868
    ITEM           MM SPKR 3      Multimedia speakers- 3" cones      1,120
    ITEM           144MB DISK     1.44MB External 3.5" Diskette      1,145
    TEM            KBRD REST      Keyboard Wrist Rest                2,231
    ITEM           LT CASE        Laptop carrying case               3,704
    ITEM           DLX MOUSE      Deluxe Mouse                       3,884
    ITEM           MOUSE PAD      Mouse Pad                          4,456

#### 6.3.5 Using NumberSource Methods To Compute the Share of Units Sold

Example 6-12 uses the `NumberSource` methods `div` and `times` to produce a `Source` that specifies the share that the Desktop PC and Portable PC families have of the total quantity of product units sold for the selected time, customer, and channel values. The example first uses the `selectValue` method of `prodHier`, which is the `Source` for a hierarchy of the PRODUCT_AWJ dimension, to produce `totalProds`, which specifies a single element with the value `PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL`, which is the highest aggregate level of the hierarchy.

The `joinHidden` method of the `NumberSource` `units` produces `totalUnits`, which specifies the UNITS measure values at the total product level, without having `totalProds` appear as an output of `totalUnits`. The `div` method of `units` then produces a `Source` that represents each units sold value divided by the total quantity of units sold. The `times` method then multiplies the result of that `div` operation by 100 to produce `productShare`, which represents the percentage, or share, that a product member has of the total quantity of units sold. The `productShare` `Source` has the inputs of the `units` measure as inputs.

The `prodFamilies` object is the `Source` for the FAMILY level of the PRODUCT_PRIMARY hierarchy. The `join` method of `productShare`, with `prodFamilies` as the joined `Source`, produces a `Source` that specifies the share that each product family has of the total quantity of products sold.

The `custSel`, `chanSel`, and `timeSel` `Source` objects are selections of single members of hierarchies of the CUSTOMER_AWJ, CHANNEL_AWJ, and TIME_AWJ dimensions. The remaining `join` methods match those `Source` objects to the other inputs of `productShare`, to produce `result`. The `join(Source joined, String comparison)` signature of the `join` method produces a `Source` that does not have the joined `Source` as an output.

The `result` `Source` specifies the share for each product family of the total quantity of products sold to all customers through the direct sales channel in the year 2001.

Example 6-12 Getting the Share of Units Sold

    Source totalProds =
      prodHier.selectValue("PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL");
    NumberSource totalUnits = (NumberSource) units.joinHidden(totalProds);
    Source productShare = units.div(totalUnits).times(100);
    Source result =
      productShare.join(prodFamilies)
                  .join(timeHier, "CALENDAR_YEAR::YEAR::CY2001")
                  .join(chanHier, "CHANNEL_PRIMARY::CHANNEL::DIR")
                  .join(custHier, "SHIPMENTS::TOTAL_CUSTOMER::TOTAL");
    Source sortedResult = result.sortAscending();

A `Cursor` for the `sortedResult` `Source` has the following values, displayed in a table with column headings and formatting added. The left column has the product family value and the right column has the share of the total number of units sold for the product family to all customers through the direct sales channel in the year 2001.

    Product Family Member          Share of Total Units Sold
    -----------------------------  -------------------------
    PRODUCT_PRIMARY::FAMILY::LTPC             2.72%
    PRODUCT_PRIMARY::FAMILY::MON              2.73%
    PRODUCT_PRIMARY::FAMILY::MEM              3.57%
    PRODUCT_PRIMARY::FAMILY::DTPC             5.13%
    PRODUCT_PRIMARY::FAMILY::DOC              6.4%
    PRODUCT_PRIMARY::FAMILY::DISK            11.71%
    PRODUCT_PRIMARY::FAMILY::MOD             11.92%
    PRODUCT_PRIMARY::FAMILY::OS              12.54%
    PRODUCT_PRIMARY::FAMILY::ACC             43.28%

#### 6.3.6 Selecting Based on Time Series Operations

This topic has two examples of using methods that operate on a series of elements of the `MdmLevelHierarchy` for the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension. Example 6-13 uses the `lag` method of `unitPrice`, which is the `Source` for the UNIT_PRICE measure, to produce `unitPriceLag4`, which specifies, for each element of `unitPrice` that matches with a member of the hierarchy, the element of `unitPrice` that matches with the hierarchy member that is four time periods earlier at the same level in the hierarchy.

In the example, `dp` is the `DataProvider`. The `createListSource` method creates `measuresDim`, which has the `unitPrice` and `unitPriceLag4` `Source` objects as element values. The `extract` method of `measuresDim` gets the values of the elements of `measuresDim`. The `Source` produced by the `extract` method has `measuresDim` as an extraction input. The first `join` method matches a `Source`, `measuresDim`, to the input of the `Source` returned by the `extract` method.

The `unitPrice` and `unitPriceLag4` measures both have the `Source` objects for the PRODUCT_AWJ and TIME_AWJ dimensions as inputs. The second `join` method matches `quarterLevel`, which is a `Source` for the QUARTER level of the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension, with the TIME_AWJ dimension input of the measure, and makes it an output of the resulting `Source`.

The `joinHidden` method matches `prodSel` with the PRODUCT_AWJ dimension input of the measure, and does not make `prodSel` an output of the resulting `Source`. The `prodSel` `Source` specifies the single hierarchy member `PRODUCT_PRIMARY::FAMILY::DTPC`, which is Desktop PCs.

The `lagResult` `Source` specifies the aggregate unit prices for the Desktop PC product family for each quarter and the quarter that is four quarters earlier.

Example 6-13 Using the Lag Method

    NumberSource unitPriceLag4 = unitPrice.lag(mdmCalHier, 4);
    Source measuresDim = dp.createListSource(new Source[] {unitPrice,
                                                           unitPriceLag4});

    Source lagResult = measuresDim.extract()
                                  .join(measuresDim)
                                  .join(quarterLevel)
                                  .joinHidden(prodSel);

A `Cursor` for the `lagResult` `Source` has the following values, displayed in a table with column headings and formatting added. The left column has the quarter, the middle column has the total of the unit prices for the members of the Desktop PC family for that quarter, and the right column has the total of the unit prices for the quarter that is four quarters earlier. The first four values in the right column are `NA` because quarter 5, Q1-98, is the first quarter in the CALENDAR_YEAR hierarchy. The table includes only the first eight quarters.

                                                        Unit Price
    Quarter                            Unit Price  Four Quarters Before
    ---------------------------------  ----------  --------------------
    CALENDAR_YEAR::QUARTER::CY1998.Q1    2687.54                NA
    CALENDAR_YEAR::QUARTER::CY1998.Q2    2704.48                NA
    CALENDAR_YEAR::QUARTER::CY1998.Q3    2673.27                NA
    CALENDAR_YEAR::QUARTER::CY1998.Q4    2587.76                NA
    CALENDAR_YEAR::QUARTER::CY1999.Q1    2394.79           2687.54
    CALENDAR_YEAR::QUARTER::CY1999.Q2    2337.18           2704.48
    CALENDAR_YEAR::QUARTER::CY1999.Q3    2348.39           2673.27
    CALENDAR_YEAR::QUARTER::CY1999.Q4    2177.89           2587.76
    ...

Example 6-14 Using the movingTotal Method

This example uses the same `unitPrice`, `mdmCalHier`, `quarterLevel`, and `prodSel` objects as Example 6-13, but it uses the `unitPriceMovingTotal` measure as the second element of `measuresDim`. The `unitPriceMovingTotal` `Source` is produced by the `movingTotal` method of `unitPrice`. That method provides `mdmCalHier`, which is the `MdmLevelHierarchy` for the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension, as the `dimension` parameter and the integers `0` and `3` as the starting and ending offset values.

The `movingTotalResult` `Source` specifies, for each quarter, the aggregate of the unit prices for the members of the Desktop PC family for that quarter and the total of that unit price plus the unit prices for the next three quarters.

    NumberSource unitPriceMovingTotal =
      unitPrice.movingTotal(mdmCalHier, 0, 3);

    Source measuresDim =
      dp.createListSource(new Source[]{unitPrice, unitPriceMovingTotal});

    Source movingTotalResult = measuresDim.extract()
                                          .join(measuresDim)
                                          .join(quarterLevel)
                                          .joinHidden(prodSel);

A `Cursor` for the `movingTotalResult` `Source` has the following values, displayed in a table with column headings and formatting added. The left column has the quarter, the middle column has the total of the unit prices for the members of the Desktop PC family for that quarter, and the left column has the total of the unit prices for that quarter and the next three quarters. The table includes only the first eight quarters.

                                                       Unit Price Moving Total
    Quarter                             Unit Price  Current Plus Next Three Periods
    ---------------------------------   ----------  -------------------------------
    CALENDAR_YEAR::QUARTER::CY1998.Q1     2687.54              10653.05
    CALENDAR_YEAR::QUARTER::CY1998.Q2     2704.48              10360.30
    CALENDAR_YEAR::QUARTER::CY1998.Q3     2673.27               9993.00
    CALENDAR_YEAR::QUARTER::CY1998.Q4     2587.76               9668.12
    CALENDAR_YEAR::QUARTER::CY1999.Q1     2394.79               9258.25
    CALENDAR_YEAR::QUARTER::CY1999.Q2     2337.18               8911.87
    CALENDAR_YEAR::QUARTER::CY1999.Q3     2348.39               8626.48
    CALENDAR_YEAR::QUARTER::CY1999.Q4     2177.89               8291.37
    ...

#### 6.3.7 Selecting a Set of Elements Using Parameterized Source Objects

Example 6-15 uses `NumberParameter` objects to create parameterized `Source` objects. Those objects are the `bottom` and `top` parameters for the `interval` method of `prodHier`. That method returns `paramProdSelInterval`, which is a `Source` that specifies the set of elements of `prodHier` from the `bottom` to the `top` positions of the hierarchy.

The elements of the product `Source` specify the elements of the `units` measure that appear in the `result` `Source`. By changing the values of the `Parameter` objects, you can select a different set of units sold values using the same `Cursor` and without having to produce new `Source` and `Cursor` objects.

The example uses the following objects.

- `dp`, which is the `DataProvider` for the session.

- `prodHier`, which is the `Source` for the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension.

- `prodShortDescr`, which is the `Source` for the short value description attribute of the PRODUCT_AWJ dimension.

- `units`, which is the `Source` for the UNITS measure of product units sold.

- `chanHier`, which is the `Source` for the CHANNEL_PRIMARY hierarchy of the CHANNEL_AWJ dimension.

- `calHier`, which is the `Source` for the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension.

- `shipHier`, which is the `Source` for the SHIPMENTS hierarchy of the CUSTOMER_AWJ dimension.

- The `Context11g` object that is returned by the `getContext` method. The `Context11g` has methods that commit the current `Transaction`, that create a `Cursor` for a `Source`, that display text, and that display the values of the `Cursor`.

The `join` method of `prodShortDescr` gets the short value descriptions for the elements of `paramProdSelInterval`. The next four `join` methods match `Source` objects with the inputs of the `units` measure. The example creates a `Cursor` and displays the result set of the query. Next, the `setPosition` method of `resultCursor` sets the position of the `Cursor` back to the first element.

The `setValue` methods of the `NumberParameter` objects change the values of those objects, which changes the selection of elements of the product `Source` that are specified by the query. The example then displays the values of the `Cursor` again.

Example 6-15 Selecting a Range With NumberParameter Objects

    NumberParameter startParam = new NumberParameter(dp, 1);
    NumberParameter endParam = new NumberParameter(dp, 6);

    NumberSource startParamSrc = (NumberSource)startParam.createSource();
    NumberSource endParamSrc = (NumberSource)endParam.createSource();

    Source paramProdSelInterval =
      prodHier.interval(startParamSrc, endParamSrc);
    Source paramProdSelIntervalShortDescr =
      prodShortDescr.join(paramProdSelInterval);

    NumberSource result =
      (NumberSource)units.join(chanHier, "CHANNEL_PRIMARY::CHANNEL::INT")
                         .join(calHier, "CALENDAR_YEAR::YEAR::CY2001")
                         .join(shipHier, "SHIPMENTS::TOTAL_CUSTOMER::TOTAL")
                         .join(paramProdSelIntervalShortDescr);

    // Commit the current transaction.
    getContext().commit();

    CursorManager  cursorMngr = dp.createCursorManager(result);
    Cursor resultCursor = cursorMngr.createCursor();

    getContext().displayCursor(resultCursor);

    //Reset the Cursor position to 1.
    resultCursor.setPosition(1);

    // Change the value of the parameterized Source.
    startParam.setValue(7);
    endParam.setValue(12);

    // Display the results again.
    getContext().displayCursor(resultsCursor);

The following table displays the values of `resultCursor`, with column headings and formatting added. The left column has the product hierarchy members, the middle column has the short value description, and the right column has the quantity of units sold.

                  Product                       Description        Units Sold
    -------------------------------------  ----------------------  ----------
    PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL   Total Product             55,872
    PRODUCT_PRIMARY::CLASS::HRD             Hardware                  21,301
    PRODUCT_PRIMARY::FAMILY::DISK           Memory                     6,634
    PRODUCT_PRIMARY::ITEM::EXT CD ROM       External 48X CD-ROM          136
    PRODUCT_PRIMARY::ITEM::EXT DVD          External - DVD-RW - 8X     1,526
    PRODUCT_PRIMARY::ITEM::INT 8X DVD       Internal - DVD-RW - 8X     1,543

                  Product                       Description        Units Sold
    -------------------------------------  ----------------------  ----------
    PRODUCT_PRIMARY::ITEM::INT CD ROM       Internal 48X CD-ROM          380
    PRODUCT_PRIMARY::ITEM::INT CD USB       Internal 48X CD-ROM USB      162
    PRODUCT_PRIMARY::ITEM::INT RW DVD       Internal - DVD-RW - 6X     2,887
    PRODUCT_PRIMARY::FAMILY::DTPC           Desktop PCs                2,982
    PRODUCT_PRIMARY::ITEM::SENT FIN         Sentinel Financial         1,015
    PRODUCT_PRIMARY::ITEM::SENT MM          Sentinel Multimedia          875
