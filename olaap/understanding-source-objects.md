This chapter describes `Source` objects, which you use to specify a query. With a `Source`, you specify the data that you want to retrieve from the data store and the analytical or other operations that you want to perform on the data. [Making Queries Using Source Methods](making-queries-using-source-methods.md), provides examples of using `Source` objects. [Creating Dynamic Queries](creating-dynamic-queries.md), describes using `Template` objects to make modifiable queries.

This chapter includes the following topics:

- Overview of Source Objects

- Kinds of Source Objects

- Characteristics of Source Objects

- Inputs and Outputs of a Source

- Describing Parameterized Source Objects

### 5.1 Overview of Source Objects

You use `Source` objects to create a query that specifies the data that you want to retrieve from the database. As a query, a `Source` is similar to a SQL `SELECT` statement.

To create a query, you typically use the classes in the `oracle.olapi.metadata.mdm` package to get `MdmSource` objects that represent OLAP metadata objects. From an `MdmSource` object, you can get a `Source` object. You can also create other kinds of `Source` objects with methods of a `DataProvider`. You can then use these `Source` objects to create a query. To retrieve the data specified by the query, you create a `Cursor` for the `Source`.

With the methods of a `Source`, you can specify selections of dimension members, attribute values, or measure values. You can also specify operations on the elements of the `Source`, such as mathematical calculations, comparisons, and ordering, adding, or removing elements of a query.

The `Source` class has a few basic methods and many shortcut methods that use one or more of the basic methods. The most complex basic methods are the `join(Source joined, Source comparison, int comparisonRule, boolean visible)` method and the `recursiveJoin(Source joined, Source compariso4n, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase, int maxIterations, boolean visible)` method. The many other signatures of the `join` and `recursiveJoin` methods are shortcuts for certain operations of the basic methods.

In this chapter, the information about the `join` method applies equally to the `recursiveJoin` method, except where otherwise noted. With the `join` method you can relate the elements of one `Source` to those of another `Source` by joining a `Source` with an input to a `Source` that matches with that input. For example, to specify the dimension members that are required to retrieve the data of a measure that has the dimension as an input, you use a `join` method to relate the dimension members to the measure. The `join` method and the inputs of a `Source` are described in "Inputs and Outputs of a Source".

A `Source` has certain characteristics, such as a type and a data type, and it can have one or more inputs or outputs. This chapter describes these concepts. It also describes the different kinds of `Source` objects and how you get them, and the `join` method and other `Source` methods and how you use those methods to specify a query.

### 5.2 Kinds of Source Objects

The kinds of `Source` objects that you use to specify data and to perform analysis, and the ways that you get them, are the following:

- Primary `Source` objects, which are returned by the `getSource` method of an `MdmSource` object such as an `MdmDimension` or an `MdmDimensionedObject`. A primary `Source` provides access to the data that the `MdmSource` represents. Getting primary `Source` objects is usually the first step in creating a query. You then typically select elements from the primary `Source` objects, thereby producing derived `Source` objects.

- Derived `Source` objects, which you get by calling some of the methods of a `Source` object. Methods such as `join` return a new `Source` that is derived from the `Source` on which you call the method. All queries on the data store, other than a simple list of values specified by the primary `Source` for an `MdmDimension`, are derived `Source` objects.

- Fundamental `Source` objects, which are returned by the `getSource` method of a `FundamentalMetadataObject`. These `Source` objects represent the OLAP Java API data types.

- List or range `Source` objects, which are returned by the `createConstantSource`, `createListSource`, or `createRangeSource` methods of a `DataProvider`. Typically, you use this kind of `Source` as the `joined` or `comparison` parameter to a `join` method.

- Empty, null, or void `Source` objects. The empty and void `Source` objects are returned by the `getEmptySource` or `getVoidSource` method of a `DataProvider`, and the null `Source` object is returned by the `nullSource` method of a `Source`. The empty `Source` has no elements. The void `Source` and a null `Source` each has one element that has the value of `null`. The difference between the void `Source` and a null `Source` is that the type of the void `Source` is the `FundamentalMetadataObject` for the Value data type and the type of a null `Source` is the `Source` whose `nullSource` method returned it. Typically, you use these kinds of `Source` objects as the `joined` or `comparison` parameter to a `join` method.

- Dynamic `Source` objects, which are returned by the `getSource` method of a `DynamicDefinition`. A dynamic `Source` is usually a derived `Source`. It is generated by a `Template`, which you use to create a dynamic query that you can revise after interacting with an end user.

- Parameterized `Source` objects, which are returned by the `createSource` methods of a `Parameter`. Like a list or range `Source`, you use a parameterized `Source` as a parameter to the `join` method. Unlike a list or range `Source`, however, you can change the value that the `Parameter` represents after the join operation and thereby change the selection that the derived `Source` represents. You can create a `Cursor` for that derived `Source` and retrieve the results of the query. You can then change the value of the `Parameter`, and, without having to create a new `Cursor` for the derived `Source`, use that same `Cursor` to retrieve the results of the modified query.

The `Source` class has the following subclasses:

- `BooleanSource`

- `DateSource`

- `NumberSource`

- `StringSource`

These subclasses have different data types and implement `Source` methods that require those data types. Each subclass also implements methods unique to it, such as the `implies` method of a `BooleanSource` or the `indexOf` method of a `StringSource`.

### 5.3 Characteristics of Source Objects

A `Source` has a data type, a type, and an identifier (ID), and all `Source` objects except the empty `Source` have one or more elements. The following topics describe these concepts.

- Elements and Values of a Source

- Data Type of a Source

- Type of a Source

- Source Identification and SourceDefinition of a Source

Some `Source` objects have one or more inputs or outputs. Those complex concepts are discussed in "Inputs and Outputs of a Source".

#### 5.3.1 Elements and Values of a Source

All `Source` objects, except the empty `Source`, have one or more elements. An element of a `Source` has a value, which can be null. For example, the `Source` for the `MdmPrimaryDimension` object for the CHANNEL_AWJ dimension has four elements. The values of those elements are the unique values of the members of the dimension, which are the following.

    CHANNEL_PRIMARY::CHANNEL::TOTAL
    CHANNEL_PRIMARY::CHANNEL::CAT
    CHANNEL_PRIMARY::CHANNEL::DIR
    CHANNEL_PRIMARY::CHANNEL::INT

#### 5.3.2 Data Type of a Source

The `FundamentalMetadataObject` class represents the data type of the values of the elements of an `MdmSource`. The data type of a `Source` is represented by a fundamental `Source`. For example, a `BooleanSource` has elements that have Java `boolean` values. The data type of a `BooleanSource` is the fundamental `Source` that represents OLAP Java API Boolean values.

To get the fundamental `Source` that represents the data type of a `Source`, call the `getDataType` method of the `Source`. You can also get a fundamental `Source` by calling the `getSource` method of a `FundamentalMetadataObject`.

The data type for a primary `Source` is related to the SQL data type of the associated metadata object. For example, an `MdmBaseAttribute` that has a SQL data type of `VARCHAR2(30)` would produce a `Source` whose data type is the fundamental `Source` that represents OLAP Java API String values. The following code gets that fundamental `Source`.

    fmp.getStringDataType().getSource(); // fmp is the FundamentalMetadataProvider.

A typical use of a `Source` for a data type is as the comparison `Source` for a join or a recursive join operation. As such it represents the set of all values of that data type. For examples of the use of the `getDataType` method, see [Example 6-3](making-queries-using-source-methods.md), [Example 6-5](making-queries-using-source-methods.md), and [Example 6-11](making-queries-using-source-methods.md).

#### 5.3.3 Type of a Source

Along with a data type, a `Source` has a type, which is the `Source` from which the elements of the `Source` are drawn. The type of a `Source` determines whether the `join` method can match the `Source` with the input of another `Source`. The only `Source` that does not have a type is the fundamental `Source` for the OLAP Java API Value data type, which represents the set of all values, and from which all other `Source` objects ultimately descend. You can find the type by calling the `getType` method of a `Source`.

The type of a fundamental `Source` is the data type of the `Source`. The type of a list or range `Source` is the data type of the values of the elements of the list or range `Source`.

The type of a primary `Source` is one of the following:

- The fundamental `Source` that represents the data type of the values of the elements of the primary `Source`. For example, the type of the `Source` returned by the `getSource` method of a typical numeric `MdmMeasure` is the fundamental `Source` that represents the set of all OLAP Java API number values.

- The `Source` for the object that contains the primary `Source`. For example, the type of the `Source` returned by the `getSource` method of an `MdmLevelHierarchy` is the `Source` for the `MdmPrimaryDimension` that contains the hierarchy.

The type of a derived `Source` is one of the following:

- The base `Source`, which is the `Source` whose method returned the derived `Source`. A `Source` returned by the `alias`, `distinct`, `extract`, `join`, `recursiveJoin`, or `value` methods, or one of their shortcuts, has the base `Source` as the type.

- A fundamental `Source`. The type of the `Source` returned by methods such as `position` and `count` is the fundamental `Source` for the OLAP Java API Integer data type. The type of the `Source` returned by methods that make comparisons, such as `eq`, `le`, and so on, is the fundamental `Source` for the Boolean data type. The type of the `Source` returned by methods that perform aggregate functions, such as the `NumberSource` methods `total` and `average`, is a fundamental `Source` that represents the function.

A derived `Source` that has the base `Source` as the type is a subtype of the `Source` from which it is derived. A derived Source that has a fundamental `Source` as the type is a subtype of the fundamental `Source`. You can use the `isSubtypeOf` method to determine if a `Source` is a subtype of another `Source`.

For example, in Example 5-1 the `myList` object is a list `Source`. The example uses `myList` to select values from `prodHier`, a `Source` for an `MdmLevelHierarchy` of the `MdmPrimaryDimension` for the PRODUCT_AWJ dimension. In the example, `dp` is the `DataProvider`.

Example 5-1 Using the isSubtypeOf Method

    Source myList = dp.createListSource(new String[] {
                                         "PRODUCT_PRIMARY::FAMILY::LTPC",
                                         "PRODUCT_PRIMARY::FAMILY::DTPC",
                                         "PRODUCT_PRIMARY::FAMILY::ACC",
                                         "PRODUCT_PRIMARY::FAMILY::MON"});
    Source prodSel = prodHier.selectValues(myList);
    if (prodSel.isSubtypeOf(prodHier))
      println("prodSel is a subtype of prodHier.");
    else
      println("prodSel is not a subtype of prodHier.");

Because `prodSel` is a subtype of `prodHier`, the condition in the `if` statement is true and the example displays the following:

    prodSel is a subtype of prodHier.

The type of `myList` is the fundamental String `Source`. The type of `prodHier` is the `Source` for the PRODUCT_AWJ dimension. The type of `prodSel` is `prodHier` because the elements of `prodSel` are derived from the elements of `prodHier`.

The supertype of a `Source` is the type of the type of a `Source`, and so on, up through the types to the `Source` for the fundamental Value data type. For example, the fundamental Value `Source` is the type of the fundamental String `Source`, which is the type of `prodHier`, which is the type of `prodSel`. The fundamental Value `Source` and the fundamental String `Source` are both supertypes of `prodSel`. The `prodSel` `Source` is a subtype of `prodHier`, and of the fundamental String `Source`, and of the fundamental Value `Source`.

#### 5.3.4 Source Identification and SourceDefinition of a Source

A `Source` has an identification, an ID, which is a `String` that uniquely identifies it during the current connection to the database. You can get the identification by calling the `getID` method of a `Source`. For example, the following code gets the identification of the `Source` for the `MdmPrimaryDimension` for the PRODUCT_AWJ dimension and displays the value.

    println("The Source ID of prodDim is " + prodDim.getID());

The preceding code displays the following:

    The Source ID of prodDim is Hidden..GLOBAL.PRODUCT_AWJ

Each `Source` also has a `SourceDefinition` object, which records information about the `Source`. Oracle OLAP uses this information internally. For example, the `SourceDefinition` of a derived `Source` records the parameters of the join operation that produced the `Source`, such as the base `Source`, the joined `Source`, the comparison `Source`, the comparison rule, and the value of the `visible` parameter.

The `DynamicDefinition` class is a subclass of `SourceDefinition`. An OLAP Java API client application uses the `DynamicDefinition` of a `Template` to get the dynamic `Source` of the `Template`.

### 5.4 Inputs and Outputs of a Source

An input of a `Source` indicates that the elements of the `Source` have a relation to those of another `Source`. An output of a `Source` contains elements from which values of the `Source` with the output are derived. A `Source` with one or more outputs is somewhat like an array of arrays.

A `Source` can have inputs and it can have outputs. The inputs and the outputs of a `Source` are other `Source` objects.

The inputs and outputs of a base `Source` influence the elements of a `Source` that you derive from that base `Source`. To derive a `Source`, you use methods of the base `Source`. The derived `Source` can have outputs or inputs or both or neither, depending on the method and the parameters of the method.

Some `Source` methods, such as the `value` and `position` methods, return a `Source` that has an input. The `join` and `recursiveJoin` methods can return a `Source` that has an output. If the join operation involves a `Source` with an input and a `Source` that matches with that input, then the input acts as a filter in producing the elements of the derived `Source`.

The following topics describe the `join` method, the concepts of outputs and inputs, and the matching of inputs. They provide examples of producing `Source` objects that have outputs, `Source` objects that have inputs, and join operations that match an input with a `Source`.

- Describing the join Method

- Outputs of a Source

- Inputs of a Source

- Matching a Source with an Input

#### 5.4.1 Describing the join Method

With the `join` method, you join the elements of one `Source` with those of another `Source` to produce a derived `Source`. The derived `Source` could have inputs or outputs. The elements of the derived `Source`, and whether it has any inputs or outputs, depend on the values of the parameters that you pass to the `join` method.

The full signature of the `join` method is the following.

    Source join(Source joined,
                Source comparison,
                int comparisonRule,
                boolean visible)

The `Source` on which you call the `join` method is the base of the join operation. The parameters of the method are the following.

##### 5.4.1.1 Describing the joined Parameter

The `joined` parameter is a `Source` object. The `join` method joins the elements of the base `Source` and the elements of the joined `Source`, with results that are determined by the values of the other `join` parameters. If the values of the joined `Source` are not related to the values of the base `Source`, that is, if neither the joined `Source` nor the base `Source` matches with an input of the other, then the join produces a Cartesian product of the elements of the base and the joined `Source` objects. The examples in the "Outputs of a Source" topic demonstrate this kind of join operation.

If the values of the joined `Source` are related to the values of the base `Source`, that is, if either the joined `Source` or the base `Source` is an input of the other, then the elements of the derived `Source` are the result of the matching of the input. The examples in "Matching a Source with an Input" demonstrate this kind of join operation.

##### 5.4.1.2 Describing the comparison Parameter

The `comparison` parameter is another `Source` object. The join operation compares the values of the elements of the comparison `Source` to the values of the joined `Source`. The values that are the same in the joined and comparison objects participate in the join operation or are removed from participation, depending on the value of the `comparisonRule` parameter.

##### 5.4.1.3 Describing the comparisonRule Parameter

The value of the `comparisonRule` parameter specifies which values of the joined `Source` participate in the join operation. The `comparisonRule` value also determines the sort order of the participating values. The comparison rule is one of the static constant fields of the `Source` class. The basic comparison rules are the following.

- `COMPARISON_RULE_SELECT`, which specifies that only the elements of the joined `Source` that are also in the comparison `Source` participate in the join operation.

- `COMPARISON_RULE_REMOVE`, which specifies that only the elements of the joined `Source` that are not in the comparison `Source` participate in the join operation.

The other comparison rules are all select operations that sort the resulting values in various ways. Those rules are the following.

- `COMPARISON_RULE_ASCENDING`

- `COMPARISON_RULE_ASCENDING_NULLS_FIRST`

- `COMPARISON_RULE_ASCENDING_NULLS_LAST`

- `COMPARISON_RULE_DESCENDING`

- `COMPARISON_RULE_DESCENDING_NULLS_FIRST`

- `COMPARISON_RULE_DESCENDING_NULLS_LAST`

##### 5.4.1.4 Describing the visible Parameter

The `visible` parameter is a `boolean` value that specifies whether the joined `Source` appears as an output of the `Source` that is derived by the join operation. If the value of the `visible` parameter is `true`, then the derived `Source` has an output that contains the elements drawn from the joined `Source`. If the value is `false`, then the derived `Source` does not have an output for the joined `Source`.

#### 5.4.2 Outputs of a Source

The `join` method returns a derived `Source` that has the values of the elements of the base `Source` that are specified by the parameters of the method. Those values are the base values of the derived `Source`.

If the value of the `visible` parameter of the `join` method is `true`, then the joined `Source` becomes an output of the derived `Source`. The elements of the derived `Source` then have the values of the output and the base values, as specified by the other parameters of the join operation.

A derived `Source` can have from zero to many outputs. A `Source` that is an output can itself have outputs. You can get the outputs of a `Source` by calling the `getOutputs` method, which returns a `List` of `Source` objects.

The examples in the following topics all have simple join operations that produce `Source` objects that have one or more outputs. Because none of the `Source` objects in the join operations have inputs, the values of the derived `Source` objects produced by the join operations are the Cartesian products of the base and the joined `Source` objects.

- Producing a Source with an Output

- Using COMPARISON_RULE_SELECT

- Using COMPARISON_RULE_REMOVE

- Producing a Source with Two Outputs

- Hiding an Output

Very different results occur from a join operation that involves a `Source` that has an input and a `Source` that matches with that input. For examples of `Source` objects with inputs and the matching of inputs, see the following topics.

- Inputs of a Source

- Matching a Source with an Input

##### 5.4.2.1 Producing a Source with an Output

Example 5-2 A Simple Join That Produces a Source with an Output

This example uses the simplest signature of the `join` method to produce a `Source` that has one output. The example creates a list `Source`, `letters`, that has three elements, the values of which are A, B, and C. It also creates a list `Source`, `names`, that has three elements, the values of which are Stephen, Leo, and Molly.

    Source letters = dp.createListSource(new String[] {"A", "B", "C"});
    Source names = dp.createListSource(new String[] {"Stephen", "Leo", "Molly"});
    Source lettersWithNames = letters.join(names);

    // Oracle OLAP translates this shortcut signature of the join method into the
    // following full signature, where dp is the DataProvider for the session.
    // Source letters.join(names,
    //                     dp.getEmptySource(),
    //                     Source.COMPARISON_RULE_REMOVE,
    //                     true);

The `letters.join(names)` operation joins the elements of the base `Source`, `letters`, and the joined `Source`, `names`. Because the comparison `Source` has no elements, the join operation does not remove any of the elements that are in the joined `Source` in producing the derived `Source`. (The comparison `Source` is the empty `Source` that is returned by the `dp.getEmptySource()` parameter of the full `join` signature shown in the example.) The resulting derived `Source`, `lettersWithNames`, is the Cartesian product of the elements of the base `letters` and the joined `names`. Because both `letters` and `names` have three elements, the number of elements in `lettersWithNames` is nine.

Because the `visible` parameter of `letters.join(names)` is `true`, the derived `Source` has an output. Because no `elements` were removed from the joined `Source`, the derived `Source` has the values of all of the elements of the joined `Source`.

A `Cursor` for a `Source` has the same structure as the `Source`. A `Cursor` for the `lettersWithNames` `Source` has a `ValueCursor` for the base values of the derived `Source` and a `ValueCursor` for the output values. The following table presents the values of the `ValueCursor` objects. The table includes headings that are not in the `ValueCursor` objects.

    Output Values     Base Values
       Stephen             A
       Stephen             B
       Stephen             C
       Leo                 A
       Leo                 B
       Leo                 C
       Molly               A
       Molly               B
       Molly               C

##### 5.4.2.2 Using COMPARISON_RULE_SELECT

Example 5-3 A Simple Join That Selects Elements of the Joined Source

This example demonstrates using a comparison `Source` that has values and the comparison rule `COMPARISON_RULE_SELECT`. The example uses the `letter` and `names` `Source` objects from Example 5-2 and adds the `someNames` `Source`. It uses `someNames` as the comparison `Source`. The output of the `Source` derived from the join operation has only the names that are in both the joined `Source` and the comparison `Source`.

    Source someNames = dp.createListSource(new String[] {"Stephen", "Molly"});
    Source lettersAndSelectedNames =
      letters.join(names, someNames, Source.COMPARISON_RULE_SELECT, true);

A `Cursor` for the `lettersAndSelectedNames` `Source` has the values specified by the `Source`. The following table presents the `Cursor` values and has headings added.

    Output Values     Base Values
       Stephen             A
       Stephen             B
       Stephen             C
       Molly               A
       Molly               B
       Molly               C

##### 5.4.2.3 Using COMPARISON_RULE_REMOVE

Example 5-4 A Simple Join That Removes Elements of the Joined Source

This example demonstrates using a comparison `Source` that has values and the comparison rule `COMPARISON_RULE_REMOVE`. That comparison rule removes from participation in the join operation those values that are the same in the joined and in the comparison `Source` objects. The output of the derived `Source` therefore has only the name from the joined `Source` that is not in the comparison `Source`.

The example has the same base, joined, and comparison `Source` objects as Example 5-3.

    Source lettersAndNamesWithoutRemovedNames =
      letters.join(names,
                   someNames,
                   Source.COMPARISON_RULE_REMOVE,
                   true);

A `Cursor` for the `lettersAndNamesWithoutRemovedNames` `Source` has the values specified by the `Source`. The following table presents the values and has headings added.

    Output Values     Base Values
       Leo                 A
       Leo                 B
       Leo                 C

##### 5.4.2.4 Producing a Source with Two Outputs

Example 5-5 A Simple Join That Produces a Source with Two Outputs

If you join a `Source` to a `Source` that has an output, and if the `visible` `parameter` is `true`, then the join operation produces a `Source` that has the joined `Source` as an additional output. The additional output becomes the first output, as shown in this example.

The example uses the `Source` objects from Example 5-3 and creates another list `Source`, `colors`, that contains the names of two colors. The example joins the `colors` `Source` to the `lettersWithSelectedNames` `Source` to produce the `lettersWithSelectedNamesAndColors` `Source`.

The `lettersWithSelectedNames` `Source` has `names` as an output. The `lettersWithSelectedNamesAndColors` `Source` has both `colors` and `names` as outputs. The first output is `colors` and the second output is `names`.

    Source colors = dp.createListSource(new String[] {"Green", "Maroon"});

    Source lettersWithSelectedNames =
      letters.join(names,
                   someNames,
                   Source.COMPARISON_RULE_SELECT,
                   true);
    Source lettersWithSelectedNamesAndColors =
      lettersWithSelectedNames.join(colors);

A `Cursor` for the `lettersWithSelectedNamesAndColors` `Source` has the values shown in the following table. The table has headings added.

    Output 1 Values     Output 2 Values     Base Values
          Green            Stephen               A
          Green            Stephen               B
          Green            Stephen               C
          Green            Molly                 A
          Green            Molly                 B
          Green            Molly                 C
          Maroon           Stephen               A
          Maroon           Stephen               B
          Maroon           Stephen               C
          Maroon           Molly                 A
          Maroon           Molly                 B
          Maroon           Molly                 C

##### 5.4.2.5 Hiding an Output

Example 5-6 A Simple Join That Hides An Output

If the `visible` parameter of a `join` method is `false`, then the joined `Source` participates in the join operation but does not appear as an output of the `Source` derived by the join. This example uses the `joinHidden` shortcut method to join the `lettersWithSelectedNames` and the `colors` `Source` objects from Example 5-5. The example includes in a comment the full `join` signature for the `joinHidden` shortcut.

    Source lettersWithSelectedNamesAndHiddenColors =
      lettersWithSelectedNames.joinHidden(colors);

    // The full signature of the joinHidden shortcut method is
    // Source result = base.join(joined,
    //                           dp.getEmptySource(),
    //                           Source.COMPARISON_RULE_REMOVE,
    //                           false);
    // So if Source base = lettersWithSelectedNames and
    // Source joined = colors, then the result Source is the same as the
    // lettersWithSelectedNamesAndHiddenColors Source.

A `Cursor` for the `lettersWithSelectedNamesAndHiddenColors` `Source` has the values shown in the following table. The table has headings added.

Note that the derived `lettersWithSelectedNamesAndHiddenColors` `Source` still has twelve elements, even though the values for the `colors` `Source` do not appear as output values. The derived `Source` has one set of the six values of the `lettersWithSelectedNames` `Source` for each value of the hidden `colors` `Source`.

The example displays the following output.

    Output Values     Base Values
       Stephen             A
       Stephen             B
       Stephen             C
       Molly               A
       Molly               B
       Molly               C
       Stephen             A
       Stephen             B
       Stephen             C
       Molly               A
       Molly               B
       Molly               C

#### 5.4.3 Inputs of a Source

The examples in the "Outputs of a Source" topic all produce derived `Source` objects that have elements that are the Cartesian product of the unrelated base and joined `Source` objects. While such an operation can be useful, a more powerful aspect of `Source` objects is the ability to relate the elements of one `Source` to another `Source`. When such a relationship exists, you can derive other `Source` objects that are the result of operations between the related elements. For example, you can derive a `Source` that contains only selected elements of another `Source`. This relationship between elements is represented by the input of a `Source`.

A `Source` with an input is an incomplete specification of data. The input represents the type of `Source` that can have the elements that a join operation requires to complete the data specification. Before you can retrieve the data with a `Cursor`, you must match the input with a `Source` that has the elements that complete the specification.

You match an input with a `Source` by using the `join` or `recursiveJoin` method. The match occurs between the base `Source` and the joined `Source`.

The matching of an input acts as a filter so that the `Source` derived by the join operation has only the elements of the base `Source` whose values are related to those of the elements of the joined `Source`. The rules related to matching a `Source` with an input are described in "Matching a Source with an Input". That topic has examples that produce derived `Source` objects that are the result of the matching of an input.

A `Source` can have from zero to many inputs. You can get all of the inputs of a `Source` by calling the `getInputs` method.

Some primary `Source` objects have inputs. You can derive a `Source` that has an input by using some methods of the `Source` class.

##### 5.4.3.1 Primary Source Objects with Inputs

The primary `Source` objects for the `MdmDimensionedObject` subclasses `MdmAttribute` and `MdmMeasure` have inputs. The primary `Source` for an `MdmAttribute` has one input. The primary `Source` for an `MdmMeasure` has one or more inputs.

The inputs of an `MdmAttribute` or an `MdmMeasure` are the `Source` objects for the `MdmPrimaryDimension` objects that dimension the attribute or measure. To get the value of an attribute or a measure, you must join the attribute or measure with a `Source` that contains the related dimension members. The join operation matches the input of the attribute or measure with the `Source` that contains the dimension members. Example 5-7 matches the input of an attribute with the dimension of that attribute. Example 5-8 matches the inputs of a measure with the dimensions of that measure.

##### 5.4.3.2 Deriving a Source with an Input

Some `Source` methods always return a `Source` that has an input. The `Source` returned by the `extract`, `position`, or `value` method has the base `Source` as an input. You can use these methods to produce a `Source` whose elements are derived, or filtered, from the elements of another `Source`.

The `value` method returns a `Source` that has the elements of the base `Source` and has the base `Source` as an input. You typically use the `Source` returned by the `value` method as the base or joined `Source` of a `join` method, or sometimes as the comparison `Source`. Several examples in this chapter and in [Making Queries Using Source Methods](making-queries-using-source-methods.md) use the `value` method.

The `position` method returns a `Source` that has the position of each element of the base `Source` and that has the base `Source` as an input. For an example of using the `position` method, see [Example 6-4](making-queries-using-source-methods.md).

You use the `extract` method when elements of the `Source` objects that you want to join have `Source` objects as values. For examples of using the `extract` method, see Example 5-12, [Example 6-8](making-queries-using-source-methods.md), [Example 6-13](making-queries-using-source-methods.md), and [Example 6-14](making-queries-using-source-methods.md).

##### 5.4.3.3 Type of Inputs

The input of a `Source` derived by the `position` or `value` method, and an input intrinsic to an `MdmDimensionedObject`, are regular inputs. A regular input relates the elements of the `Source` with the input to the elements of the `Source` that matches with the input. You can get the regular inputs by calling the `getRegularInputs` method.

The input of a `Source` returned by the `extract` method is an extraction input. You can get the extraction inputs by calling the `getExtractionInputs` method.

#### 5.4.4 Matching a Source with an Input

In a join operation, the matching of a `Source` with an input occurs only between the base `Source` and the joined `Source`. A `Source` matches with an input if one of the following conditions is true.

1.  The `Source` is the same object as the input or it is a subtype of the input.

2.  The `Source` has an output that is the same object as the input or the output is a subtype of the input.

The join operation looks for the conditions in the order shown in the preceding list. It searches the list of outputs of the `Source` recursively, including any outputs of an output, looking for a match with the input. The search ends with the first matching `Source`. An input can match with only one `Source`.

When a `Source` with an input is joined to a `Source` that matches with the input, the derived `Source` returned by the `join` method has the elements of the base that are related to the elements specified by the parameters of the method. The derived `Source` does not have the input.

Matching a `Source` with an input does not affect the outputs of the base `Source` or the joined `Source`. If a base `Source` has an output that matches with the input of the joined `Source`, then the resulting `Source` does not have the input but it does have the output. If the base `Source` or the joined `Source` in a join operation has an input that is not matched in the operation, then the unmatched input is an input of the resulting `Source`.

The comparison `Source` of a `join` method does not participate in the input matching. If the comparison `Source` has an input, then that input is not matched and the `Source` returned by the `join` method has that same input.

The examples in the following topics demonstrate matching a `Source` with an input.

- Matching the Input of the Source for an MdmAttribute

- Matching the Inputs of a Measure

- Using the value Method to Derive a Source with an Input

- Using the value Method to Select Values of a Source

- Using the extract Method to Combine Elements of Source Objects

##### 5.4.4.1 Matching the Input of the Source for an MdmAttribute

Example 5-7 demonstrates the joining of the `Source` for an `MdmBaseAttribute` to the `Source` for an `MdmPrimaryDimension`. The example gets the local value attribute from the `MdmPrimaryDimension` for the CHANNEL_AWJ dimension. The `Source` for the attribute, `locValAttr`, has the `Source` for the `MdmPrimaryDimension` as an input.

In the example, `locValAttr` is the base `Source` of the join operation and `chanDim` is the joined `Source`. Because `chanDim` is an instance of the `Source` for the `MdmPrimaryDimension` for the CHANNEL_AWJ dimension, `chanDim` matches with the input of `locValAttr`. The result of the join is `dimMembersWithLocalValue`, which has `chanDim` as an output and does not have any inputs.

The `locValAttr` `Source` has four elements because each of the four members of the CHANNEL_AWJ dimension has a different local value. The `Source` derived by the join operation, `dimMembersWithLocalValue`, has four elements. The value of each element is the dimension member and the related attribute value. The dimension member is a value from the output and the attribute value is from the base.

Example 5-7 demonstrates matching the input of a base `Source` with the joined `Source`. In the example, `mdmDBSchema` is the `MdmDatabaseSchema` for the GLOBAL schema.

A `Cursor` for the `dimMembersWithLocalValue` `Source` has the values shown in the following table. The output values are the unique dimension member values derived from the joined `Source`, `chanDim`. The base values are derived from the base `Source`, `locValAttr`. The table has headings added.

               Output Values                 Base Values
    CHANNEL_PRIMARY::TOTAL_CHANNEL::TOTAL       TOTAL
    CHANNEL_PRIMARY::CHANNEL::CAT               CAT
    CHANNEL_PRIMARY::CHANNEL::DIR               DIR
    CHANNEL_PRIMARY::CHANNEL::INT               INT

Example 5-7 Getting an Attribute for a Dimension Member

    MdmStandardDimension mdmChanDim =
      mdmDBSchema.findOrCreateStandardDimension("CHANNEL_AWJ");
    Source chanDim = mdmChanDim.getSource();
    Source locValAttr = mdmChanDim.getLocalValueAttribute().getSource();
    Source dimMembersWithLocalValue = locValAttr.join(chanDim);

##### 5.4.4.2 Matching the Inputs of a Measure

Example 5-8 demonstrates getting values from a measure. The example gets the `MdmCube` that contains the UNIT_PRICE measure and gets the `MdmBaseMeasure` for the measure from that cube. The cube, and the measures of the cube, are dimensioned by the PRODUCT_AWJ and TIME_AWJ dimensions. The example gets the `MdmPrimaryDimension` objects for those dimensions and gets the `Source` objects for those metadata objects.

The `Source` for the measure, `unitPrice`, has the `Source` objects for the two `MdmPrimaryDimension` objects as inputs. The example joins the `Source` for the measure with the `Source` objects for the dimensions. The join operations match the inputs of the measure with the `Source` objects for the dimensions.

The example first joins the `Source` for the PRODUCT_AWJ dimension to the `Source` for the measure. That `unitPrice.join(prodDim)` operation derives a `Source` that has base values from `unitPrice` and has `prodDim` as an output. It also has the `Source` for the TIME_AWJ dimension as an input. The next join operation joins the `Source` derived by `unitPrice.join(prodDim)` with `timeDim`, the `Source` for the TIME_AWJ dimension. That join operation matches the input of the `Source` derived by `unitPrice.join(prodDim)` with `timeDim`.

The `Source` derived by the second join operation is `pricesByProductAndTime`. That `Source` has no inputs and has the `Source` objects for the PRODUCT_AWJ and TIME_AWJ dimensions as outputs. A `Cursor` for `pricesByProductAndTime` contains the price of each product value for every time value.

The example finally calls the `count` method of `pricesByProductAndTime`. That method returns the `NumberSource` `numPricesByProductAndTime`, which contains the number of elements of the `pricesByProductAndTime` `Source`. A `Cursor` for the `numPricesByProductAndTime` `Source` contains the value 4998, which is the number of measure values for the product and time tuples.

To produce a `Source` that contains only the measure values for certain products and times, you need to join the `Source` for the measure with `Source` objects that specify the dimension values that you want. You can produce such a selection by using methods of the primary `Source` for the dimension. One means of producing a `Source` that represents a selection of values of a `Source` is to use the `value` method.

Example 5-8 Getting Measure Values

This example demonstrates matching the inputs of the base `Source` with the joined `Source`. In the example, `mdmDBSchema` is the `MdmDatabaseSchema` for the GLOBAL schema.

    MdmCube mdmPriceCube =
      mdmDBSchema.findOrCreateCube("PRICE_CUBE_AWJ");
    MdmBaseMeasure mdmUnitPrice =
      mdmPriceCube.findOrCreateBaseMeasure("UNIT_PRICE");
    MdmStandardDimension mdmProdDim =
      mdmDBSchema.findOrCreateStandardDimension("PRODUCT_AWJ");
    MdmTimeDimension mdmTimeDim =
      mdmDBSchema.findOrCreateTimeDimension("TIME_AWJ");

    Source prodDim = mdmProdDim.getSource();
    Source timeDim = mdmTimeDim.getSource();
    Source unitPrice = mdmUnitPrice.getSource();

    Source pricesByProductAndTime = unitPrice.join(prodDim).join(timeDim);
    NumberSource numPricesByProductAndTime = pricesByProductAndTime.count();

##### 5.4.4.3 Using the value Method to Derive a Source with an Input

Example 5-9 Using the value Method to Relate a Source to Itself

In this example, the `lettersValue` `Source` is returned by the `letters.value()` method. The `lettersValue` `Source` has `letters` as an input. The input represents a relation between the values of the `Source` with the input and the values of the `Source` that matches with the input.

The join operation has `letters` as the base `Source` and `lettersValue` as the joined `Source`. The base `Source`, `letters`, matches with the input of `lettersValue`, which is also `letters`, because they are the same. The `Source` produced by the join operation, `lettersByLettersValue` has `lettersValue` as an output. It does not have an input. Each element of `lettersByLettersValue` has a base value from `letters` and the related value from `lettersValue`.

    Source letters = dp.createListSource(new String[] {"A", "B", "C"});
    Source lettersValue = letters.value();
    Source lettersByLettersValue = letters.join(lettersValue);

A `Cursor` for the `lettersByLettersValue` `Source` has the values shown in the following table. The table has headings added.

    Output Values     Base Values
           A               A
           B               B
           C               C

Because `lettersByLettersValue` contains only those values of the base and joined `Source` objects that are related, the base values of the `Cursor` for `lettersByLettersValue` `Source` are the same as the output values. If the base and joined `Source` objects had been unrelated, as in `letters.join(letters)`, then the `Source` produced by the join operation would contain the Cartesian product of the base and joined `Source` objects.

##### 5.4.4.4 Using the value Method to Select Values of a Source

Example 5-10 Using the value Method to Select Elements of a Source

By using the `value` method, you can derive a `Source` that is a selection of the elements of another `Source`. This example selects two elements from the `Source` for the PRODUCT_AWJ dimension from Example 5-7. This example demonstrates a base `Source` matching with the input of the joined `Source`.

    Source productsToSelect = dp.createListSource(new String[]
                                      {"PRODUCT_PRIMARY::ITEM::ENVY EXE",
                                       "PRODUCT_PRIMARY::ITEM::ENVY STD"});
    Source selectedProducts = prodDim.join(prodDim.value(),
                                           productsToSelect,
                                           Source.COMPARISON_RULE_SELECT,
                                           false);  // Hide the output.

A `Cursor` for the `productsToSelect` `Source` has the following values.

    PRODUCT_PRIMARY::ITEM::ENVY EXE
    PRODUCT_PRIMARY::ITEM::ENVY STD

A `Cursor` for the `selectedProducts` `Source` has the following values.

    PRODUCT_PRIMARY::ITEM::ENVY EXE
    PRODUCT_PRIMARY::ITEM::ENVY STD

The two `Source` objects contain the same values. However, the types of the objects are different. The type of the `productsToSelect` `Source` is the `Source` for the `FundamentalMetadataObject` for the String data type. The type of the `selectedProducts` `Source` is `prodDim` because `selectedProducts` is derived from `prodDim`. Therefore, `selectedProducts` is a subtype of `prodDim` and as such it can match with a `Source` that has the `Source` for the PRODUCT_AWJ dimension as an input, as shown in the next example.

Example 5-11 Using Derived Source Objects to Select Measure Values

This example selects elements from the `Source` objects for two dimensions and then gets the measure values for the selected dimension members. The example uses the same dimensions and measure as in Example 5-8. In this example, however, the `Source` objects that match with the inputs of the `Source` for the measure are not the `Source` objects for the dimensions. Instead they are subtypes of the `Source` objects for the dimensions. The subtypes specify selected members of the dimensions. The `Source` that is derived by joining the measure with the dimensions, `pricesForSelectedProductsAndTimes`, has six elements, which specify only the measure values for the two products for the three time values, instead of the 4998 elements of the `pricesByProductAndTime` `Source` in Example 5-8. In this example, `mdmDBSchema` is the `MdmDatabaseSchema` for the GLOBAL schema.

    // Create lists of product and time dimension members.
    Source productsToSelect = dp.createListSource(new String[]
                                               {"PRODUCT_PRIMARY::ITEM::ENVY EXE",
                                                "PRODUCT_PRIMARY::ITEM::ENVY STD"});
    Source timesToSelect = dp.createListSource(new String[]
                                               {"CALENDAR_YEAR::MONTH::2000.01",
                                                "CALENDAR_YEAR::MONTH::2001.01",
                                                "CALENDAR_YEAR::MONTH::2002.01"});
    // Get the PRICE_CUBE_AWJ cube.
    MdmCube mdmPriceCube = mdmDBSchema.findOrCreateCube("PRICE_CUBE_AWJ");
    // Get the UNIT_PRICE measure from the cube.
    MdmBaseMeasure mdmUnitPrice =
      mdmPriceCube.findOrCreateBaseMeasure("UNIT_PRICE");
    // Get the PRODUCT_AWJ and TIME_AWJ dimensions.
    MdmStandardDimension mdmProdDim =
      mdmDBSchema.findOrCreateStandardDimension("PRODUCT_AWJ");
    MdmTimeDimension mdmTimeDim =
      mdmDBSchema.findOrCreateTimeDimension("TIME_AWJ");
    // Get the Source objects for the dimensions and the measure.
    Source prodDim = mdmProdDim.getSource();
    Source timeDim = mdmTimeDim.getSource();
    Source unitPrice = mdmUnitPrice.getSource();
    // Using the value method, derive Source objects that specify the selected
    // dimension members.
    Source selectedProducts = prodDim.join(prodDim.value(),
                                           productsToSelect,
                                           Source.COMPARISON_RULE_SELECT,
                                           false);
    Source selectedTimes = timeDim.join(timeDim.value(),
                                        timesToSelect,
                                        Source.COMPARISON_RULE_SELECT,
                                        false);
    // Derive a Source that specifies the unitPrice values for the selected products
    // and times.
    Source pricesForSelectedProductsAndTimes = unitPrice.join(selectedProducts)
                                                        .join(selectedTimes);

A `Cursor` for the `pricesForSelectedProductsAndTimes` `Source` has the values shown in the following table. The table has headings added.

                Month                         Product                Price
    -----------------------------  -------------------------------  -------
    CALENDAR_YEAR::MONTH::2000.01  PRODUCT_PRIMARY::ITEM::ENVY EXE  3358.02
    CALENDAR_YEAR::MONTH::2000.01  PRODUCT_PRIMARY::ITEM::ENVY STD  3000.11
    CALENDAR_YEAR::MONTH::2001.01  PRODUCT_PRIMARY::ITEM::ENVY EXE  3223.28
    CALENDAR_YEAR::MONTH::2001.01  PRODUCT_PRIMARY::ITEM::ENVY STD  2426.07
    CALENDAR_YEAR::MONTH::2002.01  PRODUCT_PRIMARY::ITEM::ENVY EXE  3008.95
    CALENDAR_YEAR::MONTH::2002.01  PRODUCT_PRIMARY::ITEM::ENVY STD  2140.71

##### 5.4.4.5 Using the extract Method to Combine Elements of Source Objects

The `extract` method derives a `Source` that has the base `Source` as an input. You use the `extract` method when the values of the elements of a `Source` are `Source` objects themselves.

Example 5-12 Extracting Elements of a Source

This example uses the `selectValues` method to derive two selections of elements from a `StringSource` for the PRODUCT_AWJ dimension. The `selectValues` method is a shortcut for the full `join` signature of the methods in Example 5-10 and Example 5-11 that produce the `selectedProducts` and `selectedTimes` `Source` objects.

This example creates a list `Source`, `sourcesToCombine`, that has the two derived `Source` objects as element values. The `sourcesToCombine.extract()` method produces `sourcesToCombineWithAnInput`, which is a `Source` that has `sourcesToCombine` as an input. The join operation `sourcesToCombineWithAnInput.joinHidden(sourcesToCombine)` matches the input of `sourcesToCombineWithAnInput` with the joined `sourcesToCombine` and produces `combinedSources`, which has no inputs or outputs. A shortcut for this combining of `Source` elements is the `appendValues` method.

    MdmStandardDimension mdmProdDim =
      mdmDBSchema.findOrCreateStandardDimension("PRODUCT_AWJ");
    StringSource prodDim = (StringSource) mdmProdDim.getSource();
    Source productsToSelect = prodDim.selectValues(new String[]
                                               {"PRODUCT_PRIMARY::ITEM::ENVY ABM",
                                                "PRODUCT_PRIMARY::ITEM::ENVY EXE",
                                                "PRODUCT_PRIMARY::ITEM::ENVY STD"});
    Source moreProductsToSelect = prodDim.selectValues(new String[]
                                               {"PRODUCT_PRIMARY::ITEM::SENT FIN",
                                                "PRODUCT_PRIMARY::ITEM::SENT MM",
                                                "PRODUCT_PRIMARY::ITEM::SENT STD"});
    Source sourcesToCombine =
      dp.createListSource(new Source[] {productsToSelect, moreProductsToSelect});
    Source sourcesToCombineWithAnInput = sourcesToCombine.extract();
    Source combinedProducts =
      sourcesToCombineWithAnInput.joinHidden(sourcesToCombine);

A `Cursor` for the `combinedProducts` `Source` has the following values.

    PRODUCT_PRIMARY::ITEM::ENVY ABM
    PRODUCT_PRIMARY::ITEM::ENVY EXE
    PRODUCT_PRIMARY::ITEM::ENVY STD
    PRODUCT_PRIMARY::ITEM::SENT FIN
    PRODUCT_PRIMARY::ITEM::SENT MM
    PRODUCT_PRIMARY::ITEM::SENT STD

### 5.5 Describing Parameterized Source Objects

Parameterized `Source` objects provide a way of specifying a query and retrieving different result sets for the query by changing the set of elements specified by the parameterized `Source`. You create a parameterized `Source` with a `createSource` method of the `Parameter`. The `Parameter` supplies the value that the parameterized `Source` specifies.

The example in this topic is a very simple demonstration of using a `Parameter` object. A typical use of a `Parameter` is to specify the page edges of a cube, as shown in [Example 6-9](making-queries-using-source-methods.md). Another use of a `Parameter` is to fetch from the server only the set of elements that you currently need. [Example 6-15](making-queries-using-source-methods.md) demonstrates using `Parameter` objects to fetch different sets of elements.

When you create a `Parameter` object, you supply an initial value for the `Parameter`. You then create the parameterized `Source` using the `Parameter`. You include the parameterized `Source` in specifying a query. You create a `Cursor` for the query. You can change the value of the `Parameter` with the `setValue` method, which changes the set of elements that the query specifies. Using the same `Cursor`, you can then retrieve the new set of values.

This example demonstrates the use of a `Parameter` and a parameterized `Source` to specify a member in a dimension. The example gets the `MdmStandardDimension` for the PRODUCT_AWJ dimension and gets the `Source` for the `MdmStandardDimension` cast as a `StringSource`.

The example creates a `StringParameter` object that has a dimension member as the initial value. It then creates a parameterized `Source`, `paramProdSel`, by using the `createSource` method of the `StringParameter`. Next it uses `paramProdSel` as the comparison `Source` in a join operation that selects the dimension member.

The example gets the `Source` for the local value attribute of the dimension. It joins that `Source`, `locValAttr`, with `paramProdSel`. That join operation produces the `dimMemberWithLocalValue` `Source`.

The example creates a `Cursor` for `dimMemberWithLocalValue` and displays the value of the `Cursor`. After resetting the `Cursor` position and changing the value of the `prodParam` `StringParameter`, the example displays the value of the `Cursor` again.

The `dp` object is the `DataProvider`. The `getContext` method gets a `Context11g` object that has a method that commits the current `Transaction` and a method that displays the values of a `Cursor`.

Example 5-13 Using a Parameterized Source to Change a Dimension Selection

    MdmStandardDimension mdmProdDim =
      mdmDBSchema.findOrCreateStandardDimension("PRODUCT_AWJ");
    StringSource prodDim = (StringSource) mdmProdDim.getSource();

    StringParameter prodParam =
      new StringParameter(dp, "PRODUCT_PRIMARY::FAMILY::LTPC");
    Source prodParamSrc = prodParam.createSource();
    Source paramProdSel = prodDim.join(prodDim.value(), prodParamSrc);

    Source locValAttr = mdmProdDim.getLocalValueAttribute().getSource();
    Source dimMemberWithLocalValue = locValAttr.join(paramProdSel);

    // Commit the Transaction.
    getContext().commit();

    // Create a Cursor for the Source.
    CursorManager  cursorMngr = dp.createCursorManager(dimMemberWithLocalValue);
    Cursor cursor = cursorMngr.createCursor();

    // Display the value of the Cursor.
    getContext().displayCursor(cursor);

    // Change the product parameter value.
    prodParam.setValue("PRODUCT_PRIMARY::FAMILY::DTPC");

    // Reset the Cursor position to 1
    cursor.setPosition(1);

    // Display the value of the Cursor again.
    getContext().displayCursor(cursor);

The `Cursor` for `dimMemberWithLocalValue` displays the following.

    PRODUCT_PRIMARY::FAMILY::LTPC,LTPC

After changing the value of the `StringParameter` and resetting the position of the `Cursor`, the `Cursor` for `dimMemberWithLocalValue` displays the following.

    PRODUCT_PRIMARY::FAMILY::DTPC,DTPC
