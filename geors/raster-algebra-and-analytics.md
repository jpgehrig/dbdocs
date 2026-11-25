## 5 Raster Algebra and Analytics

This chapter describes the raster algebra language (PL/SQL and algebraic expressions) and related raster operations, including conditional queries, cell value-based updates or edits, mathematical operations, classify, on-the-fly statistical analysis, logical operations, and their applications in cartographic modeling.

It contains the following major sections.

- Raster Algebra Language
  Raster algebra is commonly used in raster data analysis and GIS modeling. In GeoRaster, raster algebra is supported by the GeoRaster raster algebra language.
- Cell Value-Based Conditional Queries
  Using cell-based conditional queries, you can generate a new GeoRaster object based on a specified condition.
- Cell Value-Based Conditional Updates (Edits)
  You can update raster cell values based on conditions.
- Mathematical Operations
  A major use of raster algebra is to apply mathematical models to raster layers from different sources.
- Classification Operations
  Classification (segmentation) operations can be applied on source GeoRaster objects to generate new objects.
- Statistical Operations
  To apply statistical operations on one or more layers, which are from one or more GeoRaster objects, the following types of operations are available.
- Logical Operations
  A major use of raster algebra is to apply logical models to raster layers from different sources; that is, you can apply logical operations on one or more layers, from one or more GeoRaster objects, to generate a new GeoRaster object.
- Raster Data Scaling and Offsetting
  You can perform raster data scaling and offsetting operations.
- Raster Data Casting
  Raster data casting maps cell values from one data type to another.
- Cartographic Modeling
  Raster algebra is widely used in cartographic modeling and is considered an essential component of GIS systems. Using the PL/SQL and the raster algebra expressions and functions, you can conduct cartographic modeling over a large number of rasters and images of virtually unlimited size.
- Terrain Modeling and Analysis
  You can use the data from input GeoRaster objects to perform terrain modeling and analysis.

### 5.1 Raster Algebra Language

Raster algebra is commonly used in raster data analysis and GIS modeling. In GeoRaster, raster algebra is supported by the GeoRaster raster algebra language.

The GeoRaster raster algebra language is an extension to the Oracle PL/SQL language. PL/SQL provides declarations of variables and constants, general mathematical expressions, basic functions, statements, and programming capabilities. GeoRaster provides a raster algebra expression language and a set of raster algebra functions for raster layer operations. The raster algebra expression language includes general arithmetic, casting, logical, and relational operators and allows any combination of them. The raster algebra functions enable the usage of the expressions and support cell value-based conditional queries, mathematical modeling, classify operations, and cell value-based updates or edits over one or many raster layers from one or many GeoRaster objects.

This combination of the PL/SQL language and GeoRaster algebraic expressions and functions provides an easy-to-use, powerful way to define raster analyses as algebraic expressions, so that users can easily apply algebraic functions on raster data to derive new results. For example, a simple raster operation can use two or more raster layers with the same dimension sizes to produce a new raster layer by using algebraic operations (addition, subtraction, and so on), or a sophisticated raster operation to generate a Normalized Difference Vegetation Index (NDVI) from multiple bands of satellite imagery.

GeoRaster supports raster algebra local operations, so the raster algebra operations work on individual raster cells, or pixels.

The following is the GeoRaster raster algebra expression language definition:

    <arithmeticExpr> ::=
                    <unaryArithmeticExpr>
                  | <binaryArithmeticExpr>
                  | <functionalArithmeticExpr>
                  | <conditionalExpr>
                  | <castingExpr>
                  | <booleanExpr>
                  | <constantNumber>
                  | <identifier>
                  | ( <arithmeticExpr> )

    <unaryArithmeticExpr> ::=
                    ( <unaryArithmeticOp> <arithmeticExpr> )

    <unaryArithmeticOp> ::=
                    +
                  | -

    <binaryArithmeticExpr> ::=
                    <arithmeticExpr> <binaryArithmeticOp> <arithmeticExpr>

    <binaryArithmeticOp> ::=
                    +
                  | -
                  | *
                  | /
                  | %

    <functionalArithmeticExpr> ::=
                    <statisticalFunction> ( )
                  | <numericFunction_with_1_param> ( <arithmeticExpr> )
                  | <numericFunction_with_2_param> ( <arithmeticExpr> , <arithmeticExpr> )
                  | <numericFunction_with_3_param> ( <arithmeticExpr> , <arithmeticExpr> , <arithmeticExpr> )

    <statisticalFunction> ::=
                    min
                  | max
                  | mean
                  | median
                  | std
                  | minority
                  | majority
                  | sum
                  | variety

    <numericFunction_with_1_param> ::=
                    abs
                  | sqrt
                  | exp
                  | exp2
                  | exp10
                  | log
                  | ln
                  | log2
                  | sin
                  | cos
                  | tan
                  | sinh
                  | cosh
                  | tanh
                  | arcsin
                  | arccos
                  | arctan
                  | arcsinh
                  | arccosh
                  | arctanh
                  | ceil
                  | floor
                  | factorial

    <numericFunction_with_2_param> ::=
                    power
                  | max2
                  | min2

    <numericFunction_with_3_param> ::=
                    max3
                  | min3

    <conditionalExpr> ::=
              <conditionalFunction> ( <booleanExpr> , <arithmeticExpr> , <arithmeticExpr> )

    <conditionalFunction> ::=
                    condition

    <castingExpr> ::=
                    <castingFunction> ( <arithmeticExpr> )

    <castingFunction> ::=
                    castint
                  | castonebit
                  | casttwobit
                  | castfourbit
                  | casteightbit
                  | castBoolean

    <booleanExpr> ::=
                    <unaryBooleanExpr>
                  | <binaryBooleanExpr>
                  | ( <booleanExpr> )

    <unaryBooleanExpr> ::=
                    <unaryBooleanOp> <booleanExpr>

    <unaryBooleanOp> ::=
                    !

    <binaryBooleanExpr> ::=
                    <booleanExpr> <binaryBooleanOp> <booleanExpr>
                  | <arithmeticExpr> <comparisonOp> <arithmeticExpr>

    <binaryBooleanOp> ::=
                    &
                  | |
                  | ^

    <comparisonOp> ::=
                    =
                  | <
                  | >
                  | >=
                  | <=
                  | !=

    <constantNumber> ::=
                    <double number>

    <identifier> ::=
                    { <ID> , <band> }
                  | { <band> }

    <ID> ::=
                    <integer number>

    <band> ::=
                    <integer number>

The precedence of the algebraic operators (+, -, \*, /, and so on) in the expression language complies with general conventions. However, in any case where the expression might be misinterpreted, you should use parentheses to clarify which interpretation is intended.

The `booleanExpr` can be used as `arithmeticExpr`, as defined in the GeoRaster raster algebra expression language. In this case, the `TRUE` and `FALSE` evaluation results of `booleanExpr` are cast to numeric values 1 and 0, respectively.

The `identifier` in the expression refers to a raster layer of a GeoRaster object. It is either a single `band` number if there is only one GeoRaster object involved, or a pair of (`ID`, `band`) where `ID` refers to one of GeoRaster objects in the expression and band refers to a specific layer of that GeoRaster object. The `band` number in this language refers to the ordinate number of a layer along the band dimension in the cell space, so it always starts with 0 (zero). The GeoRaster ID number always starts with 0 (zero).

The following procedures provide the main support for raster algebra operations:

- [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) takes `arithmeticExpr` to perform mathematical operations or modeling, `conditionalExpr` and `booleanExpr` to perform logical operations, and `statisticalFunction` expression to perform statistical analysis.

- [SDO_GEOR_RA.findCells](sdo-geor-ra-ref.md) searches/masks cells based on a `booleanExpr` condition.

- [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) applies `arithmeticExpr` to cells and then segments the raster.

- [SDO_GEOR_RA.rasterUpdate](sdo-geor-ra-ref.md) updates cell values of a raster based on different `booleanExpr` conditions.

- [SDO_GEOR_RA.diff](sdo-geor-ra-ref.md) and [SDO_GEOR_RA.over](sdo-geor-ra-ref.md) perform logical operations without using expressions.

- [SDO_GEOR_RA.stack](sdo-geor-ra-ref.md) and many other subprograms perform statistical analysis or generate statistics.

These raster algebra functions take many layers from one or many GeoRaster objects, apply `booleanExpr` and/or `arithmeticExpr` expressions over those layers, do the specific algebraic computation or modeling, and output a new GeoRaster object. The expressions can be defined in any way based on the syntax described earlier in this section.

**Note:**

All raster algebra functions require that the raster layers overlap each other and have the same dimension sizes and resolution if they are georeferenced, or have the same dimension sizes if they are not georeferenced. Before you apply raster algebra operations over two or more GeoRaster objects, you can use the [SDO_GEOR_RA.isOverlap](sdo-geor-ra-ref.md) function to determine if the GeoRaster objects are of the same size and cover the same ground area.

Raster and image databases are generally very large. Querying and manipulating such databases are computationally intensive operations. To improve performance, all GeoRaster raster algebra functions are parallelized. You should always consider applying parallel processing when using multi-CPU or multicore servers.

- Examples of Raster Algebra Expressions

**Parent topic:** Raster Algebra and Analytics

#### 5.1.1 Examples of Raster Algebra Expressions

This section contains examples showing how to define raster algebra expressions.

Example 5-1 Finding Pixels Based on a Comparison (\>)

Example 5-1 finds all pixels that meet the condition defined by algebra expression `'{1}>200'` , because there is only one GeoRaster object involved in the procedure, so `{1}` refers to the cell value of second layer (`{0}` would be for the first layer), and `'{1}>200'` means any pixels whose second layer value is greater than 200. The example assumes that the source GeoRaster object has at least two layers.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
    BEGIN
      select georaster into geor from georaster_table where georid = 1;
      select georaster into geor1 from georaster_table where georid = 5 for update;
      sdo_geor_ra.findcells(geor, '{1}>200','blocking=optimalpadding, blocking=true, blocksize=(512,512,3)',geor1);
      update georaster_table set georaster = geor1 where georid = 5;
      commit;
    END;
    /

Example 5-2 Generating a GeoRaster Object Based on an Expressions Array

Example 5-2 generates a new GeoRaster object `geor2` from two input GeoRaster objects `geor` and `geor1` based on the algebra expressions array `SDO_STRING2_ARRAY('{0,0}-0.5*{1,0}','{0,1}-0.5*{1,1}','{0,2}-0.5*{1,2}')`. The example assumes that both of the source GeoRaster objects are images with three bands.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
      geor2      MDSYS.SDO_GEORASTER;
      geo_array  MDSYS.SDO_GEORASTER_ARRAY;
    BEGIN
      select georaster into geor from georaster_table where georid = 1;
      select georaster into geor1 from georaster_table where georid = 2;
      insert into georaster_table values (17, sdo_geor.init('rdt_1', 17)) returning georaster into geor2;
      geo_array:=MDSYS.SDO_GEORASTER_ARRAY(geor,geor1);
      sdo_geor_ra.rasterMathOp(geo_array,SDO_STRING2_ARRAY('{0,0}-0.5*{1,0}','{0,1}-0.5*{1,1}','{0,2}-0.5*{1,2}'),null,geor2);
      update georaster_table set georaster = geor2 where georid = 17;
      commit;
    END;
    /

In the algebra expressions array in Example 5-2:

- `{0,0}` refers to the cell value of band 0 of the first input GeoRaster object `geor`.

- `{0,1}` refers to the cell value of band 1 of the first input GeoRaster object `geor`.

- `{0,2}` refers to the cell value of band 2 of the first input GeoRaster object `geor`.

- `{1,0}` refers to the cell value of band 0 of the second input GeoRaster object `geor1`.

- `{1,1}` refers to the cell value of band 1 of the second input GeoRaster object `geor1`.

- `{1,2}` refers to the cell value of band 2 of the second input GeoRaster object `geor1`.

In Example 5-2, then, the target GeoRaster object `geor2` will have three bands, and:

- The cell value of band 0 of target GeoRaster object `geor2` is: `{0,0}-0.5*{1,0}`

- The cell value of band 1 of target GeoRaster object `geor2` is: `{0,1}-0.5*{1,1}`

- The cell value of band 2 of target GeoRaster object `geor2` is: `{0,2}-0.5*{1,2}`

Example 5-3 Updating a GeoRaster Object Based on an Expressions Array

Example 5-3 updates cell values of the input GeoRaster object based on the algebra expression array `SDO_STRING2_ARRAY('(abs({0}-{1})=48)&({2}-{1}=-101)','2*{0}-{1}/3=108')`. The example assumes that the source GeoRaster object has three layers.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
    begin
      select georaster into geor from georaster_table where georid = 1;
      sdo_geor_ra.rasterUpdate(geor,0,SDO_STRING2_ARRAY('(abs({0}-{1})=48)&({2}-{1}=-101)','2*{0}-{1}/3=108'),SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')));
    END;
    /

In Example 5-3, for each pixel:

- If `(abs({0}-{1})=48)&({2}-{1}=-101)` is true, then the cell values of the three layers will be updated to `('123','54','89')`.

- If `2*{0}-{1}/3=108` is true, then the cell values of the three layers will be updated to `('98','56','123')`.

**Parent topic:** Raster Algebra Language

### 5.2 Cell Value-Based Conditional Queries

Using cell-based conditional queries, you can generate a new GeoRaster object based on a specified condition.

In addition to their use in space-based queries on rasters (such as with [SDO_GEOR.getRasterSubset](SDO_GEOR-reference.md)), cell value-based queries are particularly useful in analytics and application modeling. To perform cell value based conditional queries and generate a new GeoRaster object based on the specified condition, you can use the [SDO_GEOR_RA.findCells](sdo-geor-ra-ref.md) procedure and specify an appropriate `condition` parameter.

The `condition` parameter must specify a valid `booleanExpr` value (explained in Raster Algebra Language). The procedure computes the `booleanExpr` against each cell in the source GeoRaster object. If the result is `TRUE`, the original cell values are kept in the output GeoRaster object; if the result is `FALSE`, the `bgValues` are used to fill cell values in the output GeoRaster object. This can also be considered as a masking operation.

Example 5-4 Conditional Query

Example 5-4 calls the [SDO_GEOR_RA.findCells](sdo-geor-ra-ref.md) procedure to find all pixels where the value of the second band is greater than 200. Because the bgValues parameter is not specified, the value 0 is used as the background value to fill all pixels that make the condition false. The example assumes that the source GeoRaster object is an image with more than two bands.

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      INSERT into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.findcells(geor, '{ 1 }>200', 'blocking=optimalpadding, blocksize=(512,512,3)', geor1);
      UPDATE georaster_table set georaster = geor1 WHERE georid = 5;
      COMMIT;
    END;
    /

    -- This pixel is set to (0,0,0) because the cell value of the
    -- second band is 136, which is not greater than 200.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1 OR georid=5 ORDER BY georid;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)
    SDO_NUMBER_ARRAY(0, 0, 0)

    2 rows selected.

    -- This pixel keeps the original values because the cell value
    -- of the second band is greater than 200.
    SELECT sdo_geor.getcellvalue(georaster,0,132,116,'') FROM georaster_table WHERE georid =1 OR georid=5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,132,116,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(242, 225, 233)
    SDO_NUMBER_ARRAY(242, 225, 233)

    2 rows selected.

    -- This pixel keeps the original values because the cell value
    -- of the second band is greater than 200.
    SELECT sdo_geor.getcellvalue(georaster,0,261,185,'') FROM georaster_table WHERE georid =1 OR georid=5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,261,185,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(255, 214, 2)
    SDO_NUMBER_ARRAY(255, 214, 2)

Example 5-5 Conditional Query with nodata Parameter

Example 5-5 is basically the same as Example 5-4, except that the `nodata` parameter value is set to `'TRUE'`, so that all NODATA pixels keep their original values from the input GeoRaster object in the output GeoRaster object.

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      INSERT into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.findcells(geor, '{ 1 }>200', null, geor1, null, 'TRUE');
      UPDATE georaster_table set georaster = geor1 WHERE georid = 5;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)

    1 row selected.

    -- This pixel keeps its original cell values because it is nodata, even though
    -- the cell value of the second band is not greater than 200.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid=5;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)

    1 row selected.


Example 5-6 Conditional Query with parallelParam

Example 5-6 finds all pixels that meet all of the following conditions:

- The cell value of the first band is between (100,200).

- The cell value of the second band is between \[50,250\].

- The cell value of the third band is greater than 100.

In addition, because `parallelParam` is specified as `'parallel=4'`, the procedure in Example 5-6 will run in parallel with four processes.

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN
       SELECT georaster INTO geor FROM georaster_table WHERE georid = 2;
       INSERT into georaster_table values (10, sdo_geor.init('rdt_1', 10)) returning georaster into geor1;
       sdo_geor_ra.findcells(geor,'({1}>=50)&({1}<=250)&({0}>100)&({0}<200)&{2}>100) ',null,geor1,null,'false','parallel=4');
       UPDATE georaster_table SET georaster = geor1 WHERE georid = 10;
       COMMIT;
    END;
    /

**Parent topic:** Raster Algebra and Analytics

### 5.3 Cell Value-Based Conditional Updates (Edits)

You can update raster cell values based on conditions.

This section pertains to cell value-based raster updates and not space-based raster updates, both of which types of update are described in [Querying and Updating GeoRaster Cell Data](georaster-data-manipulation.md).

To update raster cell values based on conditions, you can use the [SDO_GEOR_RA.rasterUpdate](sdo-geor-ra-ref.md) procedure and specify appropriate `condition` and `vals` parameters.

The `condition` parameter specifies an array of Boolean expressions, and the `vals` parameter specifies an array of arrays of math expressions. (See the raster algebra operation explanations in Raster Algebra Language). For each cell, if `condition` is `TRUE`, its cell value is updated to the result of the corresponding math expression in the `vals` array.

Example 5-7 Cell Value-Based Update

Example 5-7 assumes that the GeoRaster object to be updated is an image with three bands, and it calls the [SDO_GEOR_RA.rasterUpdate](sdo-geor-ra-ref.md) procedure to do the following:

- For any pixels if abs(first_band_value - second_band_value)=48 and (third_band_value - second_band_value=-101), then the three band values will be updated to (123,54,89), respectively.

- For any pixels if (2\*first_band_value - second_band_value/3)=108, then the three band values will be updated to (98,56,123), respectively.

Example 5-7 also includes several calls to the [SDO_GEOR.getCellValue](SDO_GEOR-reference.md) function to show "before" and "after" values.

    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,130,130,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,130,130,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(64, 60, 48)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,230,230,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,230,230,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(11,11, 11)

    1 row selected.

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN

      SELECT georaster into geor FROM georaster_table WHERE georid = 1;
      sdo_geor_ra.rasterUpdate(geor,0,SDO_STRING2_ARRAY('(abs({0}-{1})=48)&({2}-{1}=-101)','2*{0}-{1}/3=108'),SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')));
    END;
    /

    PL/SQL procedure successfully completed.

    show errors;
    No errors.

    -- This pixel gets updated because it meets the first condition.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(123, 54, 89)

    1 row selected.

    --This pixel gets updated because it meets the second condition.
    SELECT sdo_geor.getcellvalue(georaster,0,130,130,'') FROM georaster_table WHERE georid=1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,130,130,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(98, 56, 123)

    1 row selected.

    -- This pixel keeps its original values because it does not meet any condition
    -- in the "condition" array.
    SELECT sdo_geor.getcellvalue(georaster,0,230,230,'') FROM georaster_table WHERE georid =1;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,230,230,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(11,11, 11)

    1 row selected.

Example 5-8 Cell Value-Based Update with nodata Parameter

Example 5-8 is basically the same as Example 5-7, except that the `nodata` parameter value is set to `'TRUE'`, so that all NODATA pixels keep their original values from the input GeoRaster object in the output GeoRaster object.

    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,130,130,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,130,130,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(64, 60, 48)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,230,230,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,230,230,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(11,11, 11)

    1 row selected.

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN

      SELECT georaster into geor FROM georaster_table WHERE georid = 1;
      sdo_geor.addNODATA(geor, 1,88);
      sdo_geor_ra.rasterUpdate(geor,0,SDO_STRING2_ARRAY('(abs({0}-{1})=48)&({2}-{1}=-101)','2*{0}-{1}/3=108'),SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')),null,'true');
    END;
    /

    PL/SQL procedure successfully completed.

    -- This pixel keeps its original values because it is a NODATA pixel.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)

    1 row selected.

    --This pixel gets updated because it meets the second condition.
    SELECT sdo_geor.getcellvalue(georaster,0,130,130,'') FROM georaster_table WHERE georid=1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,130,130,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(98, 56, 123)

    1 row selected.

**Parent topic:** Raster Algebra and Analytics

### 5.4 Mathematical Operations

A major use of raster algebra is to apply mathematical models to raster layers from different sources.

To apply mathematical operations on one or multiple layers, which could be from one or more GeoRaster objects, to generate a new GeoRaster object, you can use the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure.

For most formats of this procedure, the `operation` parameter specifies an array of `arithmeticExpr` strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object.

Note that `booleanExpr` can be also used as `arithmeticExpr`, as is done in Example 5-8.

Example 5-9 Mathematical Operations (1)

Example 5-9 calls the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure to generate a new 6-layer GeoRaster object from a 3-layer source GeoRaster object, and follows these rules to calculate cell values of the target GeoRaster object:

- The cell value of the first three layers of target GeoRaster object is equal to the value of the corresponding layer of source GeoRaster object, minus 10.

- The cell value of the last three layers of target GeoRaster object is equal to the value of the first three layers of the source GeoRaster object, respectively.

<!-- -->

    DECLARE
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
      geor2  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      INSERT into georaster_table values (16, sdo_geor.init('rdt_1', 16)) returning georaster into geor1;
      sdo_geor_ra.rasterMathOp(geor,SDO_STRING2_ARRAY('{0,0}-10','{0,1}-10','{0,2}-10','{0,0}','{0,1}','{0,2}'),null,geor1);
      UPDATE georaster_table SET georaster = geor1 WHERE georid = 16;
      COMMIT;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=1;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)

    1 row selected.

    --  In the results of the next SELECT statement, note:
    --  171=181-10
    --  153=163-10
    --  149=159-10
    --  181=181
    --  163=163
    --  159=159
    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =16;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(171, 153, 149, 181, 163, 159)

    1 row selected.

Example 5-10 Mathematical Operations (2)

Example 5-10 applies an operation on a 2-element GeoRaster array (containing two 3-layer source GeoRaster objects) to generate a new 3-layer GeoRaster object.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geo_array  SDO_GEORASTER_ARRAY;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      SELECT georaster INTO geor2 FROM georaster_table WHERE georid = 2;
      INSERT into georaster_table values (17, sdo_geor.init('rdt_1', 17)) returning georaster into geor1;
      geo_array:=SDO_GEORASTER_ARRAY(geor,geor2);
      sdo_geor_ra.rasterMathOp(geo_array,SDO_STRING2_ARRAY('{0,0}-0.5*{1,0}','{0,1}-0.5*{1,1}','{0,2}-0.5*{1,2}'),null,geor1,'false',null,'parallel=4');
      UPDATE georaster_table SET georaster = geor1 WHERE georid = 17;
      COMMIT;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=1 or georid=2;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)
    SDO_NUMBER_ARRAY(60, 80, 90)

    2 rows selected.

    -- In the results of the next SELECT statement, note:
    -- 151=181-0.5*60
    -- 123=163-0.5*80
    -- 114=159-0.5*90
    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =17;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(151, 123 114)

    1 row selected.

Example 5-11 Mathematical Operations (3)

Example 5-11 applies a subtraction operation on two 3-layer input GeoRaster objects to generate a new GeoRaster object. The example also includes several calls to the [SDO_GEOR.getCellValue](SDO_GEOR-reference.md) function to show "before" and "after" values.

    SELECT sdo_geor.getcellvalue(georaster,0,10,10,'0-2') FROM georaster_table WHERE georid=1 OR georid=5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,10,10,'0-2')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 137, 32)
    SDO_NUMBER_ARRAY(98, 147, 42)

    2 rows selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'0-2') FROM georaster_table WHERE georid=1 OR georid=5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'0-2')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)
    SDO_NUMBER_ARRAY(191, 173, 169)

    2 rows selected.

    DECLARE
      geor0  SDO_GEORASTER;
      geor   SDO_GEORASTER;
      geor1  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      SELECT georaster INTO geor0 FROM georaster_table WHERE georid = 5;
      INSERT into georaster_table values (6, sdo_geor.init('rdt_1', 6)) returning georaster into geor1;
      sdo_geor_ra.rasterMathOp(geor0,geor,null,sdo_geor_ra.OPERATOR_SUBTRACT,null,geor1);
      UPDATE georaster_table SET georaster = geor1 WHERE georid = 6;
      COMMIT;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,10,10,'0-2') FROM georaster_table WHERE georid=6;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,10,10,'0-2')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(10, 10, 10)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'0-2') FROM georaster_table WHERE georid=6;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'0-2')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(10, 10, 10)

    1 row selected.

**Parent topic:** Raster Algebra and Analytics

### 5.5 Classification Operations

Classification (segmentation) operations can be applied on source GeoRaster objects to generate new objects.

To apply simple classification operations on source GeoRaster objects and generate new GeoRaster objects based on your specifications, you can use the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure and specify the `expression`, `rangeArray`, and `valueArray` parameters. This classification procedure is also called segmentation.

The `expression` parameter is used to compute values that are used to map into the value ranges defined in the `rangeArray` parameter. The `rangeArray` parameter specifies a number array that defines ranges for classifying cell values, and this array must have at least one element. The `valueArray` parameter is a number array that defines the target cell value for each range, and its length must be the length of `rangeArray` plus one.

Example 5-12 Classification

Example 5-12 calls the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure to apply a segmentation operation on the value of the first band of the input GeoRaster object. The example assumes that the GeoRaster object is an image.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      rangeArray SDO_NUMBER_ARRAY;
      valueArray SDO_NUMBER_ARRAY;
    BEGIN
      rangeArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180);
      valueArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180,190);
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      INSERT into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.classify(geor,'{0}',rangeArray,valueArray,null,geor1);
      UPDATE georaster_table SET georaster = geor1 WHERE georid = 5;
      COMMIT;
    END;
    /

    PL/SQL procedure successfully completed.

    -- In the next statement, the target value is 90 because the value of the
    -- first band of source GeoRaster object is 88, which is between 80 and 90.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1 OR georid =5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)
    SDO_NUMBER_ARRAY(90)

    2 rows selected.

    -- In the next statement, the target value is 190 because the value of the
    -- first band of source GeoRaster object is 242, which is greater than 180.
    SELECT sdo_geor.getcellvalue(georaster,0,132,116,'') FROM georaster_table WHERE georid =1 OR georid =5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,132,116,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(242, 225, 233)
    SDO_NUMBER_ARRAY(190)

    2 rows selected.

Example 5-13 Classification with nodata and nodataValue Parameters

Example 5-13 calls the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure to apply a segmentation operation on the value of the first layer of the source GeoRaster object, and to set the `nodata` parameter to `'TRUE'` and the `nodataValue` parameter to 5, so that all NODATA pixels will be set with a NODATA value of 5 in the target GeoRaster object.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      rangeArray SDO_NUMEBR_ARRAY;
      valueArray SDO_NUMEBR_ARRAY;
    BEGIN
      rangeArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180);
      valueArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180,190);
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      sdo_geor.addNODATA(geor, 2,136);
      INSERT into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.classify(geor,'{0}',rangeArray,valueArray,null,geor1,'true',5);
      UPDATE georaster_table SET georaster = geor1 WHERE georid = 5;
    END;
    /

    PL/SQL procedure successfully completed.

    -- In the next statement, the target value of the cell is 5 because the value
    -- of the second layer of the input GeoRaster object is 136, which is nodata.
    SELECT sdo_geor.getcellvalue(georaster,0,30,30,'') FROM georaster_table WHERE georid =1 OR georid =5 ORDER BY georid;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,30,30,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 136, 35)
    SDO_NUMBER_ARRAY(5)

    2 rows selected.

**Parent topic:** Raster Algebra and Analytics

### 5.6 Statistical Operations

To apply statistical operations on one or more layers, which are from one or more GeoRaster objects, the following types of operations are available.

- On-the-Fly Statistical Analysis
- Stack Statistical Analysis

**Parent topic:** Raster Algebra and Analytics

#### 5.6.1 On-the-Fly Statistical Analysis

Many applications require statistical analysis. GeoRaster provides statistical analysis functions that dynamically ("on the fly") compute complete statistical values for a GeoRaster object or the following individual statistical values: minimum, maximum, mean, median, mode, and standard deviation. You can do this without generating a histogram and updating the GeoRaster object metadata.

These subprograms support pyramids, band by band and the aggregation of specified band numbers. Each subprogram returns an SDO_NUMBER_ARRAY object or a number.

See the reference information for explanations and examples of these on-the-fly statistics computation subprograms:

- [SDO_GEOR.generateStatistics](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsMax](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsMean](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsMedian](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsMin](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsMode](SDO_GEOR-reference.md)

- [SDO_GEOR.generateStatisticsSTD](SDO_GEOR-reference.md)

These subprograms do not modify the metadata in the GeoRaster object, except for some formats of [SDO_GEOR.generateStatistics](SDO_GEOR-reference.md) that set statistical data in the GeoRaster object metadata and return a string value of `TRUE` or `FALSE` instead of an SDO_NUMBER_ARRAY object.

GeoRaster also provides statistical analysis functions that compute the area weighted statistical mean value for the cells and sub-cells within a specific window of the input GeoRaster object, and that calculate the three–dimensional (3D) surface area represented by digital elevation model (DEM) data that is stored in a GeoRaster object. See the reference information for explanations and examples of these on-the-fly statistics computation functions:

- [SDO_GEOR.generateAreaWeightedMean](SDO_GEOR-reference.md)

- [SDO_GEOR_UTL.calcSurfaceArea](SDO_GEOR_UTL-reference.md)

These two functions support irregular polygon clipping and sub-cell computation, thus providing very accurate results.

**Parent topic:** Statistical Operations

#### 5.6.2 Stack Statistical Analysis

Stack statistical analysis generates a new one-layer GeoRaster object from one or more layers, which are from one or more GeoRaster objects, by computing one of the following statistical values for each cell: max, min, median, std, sum, minority, majority, or diversity.

To perform stack statistical analysis, you have the following options:

- Use the [SDO_GEOR_RA.stack](sdo-geor-ra-ref.md) procedure.

  This option is more intuitive and does not require constructing raster algebra expressions (especially for GeoRaster objects with many layers), and it allows you to specify a list of layers instead of all layers.

- Use the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure.

  This option is more flexible and powerful, allowing you to perform more comlpicated statistical analysis.

Example 5-14 Using SDO_GEOR_RA.stack

This example uses the first option for performing stack statistical analysis. It calls the [SDO_GEOR_RA.stack](sdo-geor-ra-ref.md) procedure to generate a new GeoRaster object by computing the maximum (max) value of layers 2 and 5 of two 3–layer source GeoRaster objects.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
      geor2      MDSYS.SDO_GEORASTER;
      geom       mdsys.sdo_geometry;
    BEGIN
      geom:= sdo_geometry(2003,82394, NULL,
                          sdo_elem_info_array(1, 1003, 1),
                          sdo_ordinate_array(20283.775, 1011087.9,
                                             18783.775, 1008687.9,
                                             21783.775, 1008687.9,
                                             22683.775+0.001, 1009587.9+0.001,
                                             20283.775, 1011087.9));
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor2 from georaster_table where georid = 102;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      sdo_geor_ra.stack(SDO_GEORASTER_ARRAY(geor,geor2),geom,SDO_NUMBER_ARRAY(2,5),'max',null,geor1,'false',0,'TRUE');
      update georaster_table set georaster = geor1 where georid = 101;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=100;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(121, 66, 181)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=102;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(33, 55, 56)

    1 row selected.

    --  In the results of the next SELECT statement, note:
    --  max(181,56)  ==>  181

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =101;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181)

    1 row selected.

Example 5-15 Using SDO_GEOR_RA.rasterMathOp

This example uses the second option for performing stack statistical analysis. It calls the [sdo_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) specifying a statistical operation (max) to perform an operation similar to the preceding example, except that this example applies to all layers.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
      geor2      MDSYS.SDO_GEORASTER;
      geo_array  MDSYS.SDO_GEORASTER_ARRAY;
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      select georaster into geor2 from georaster_table where georid = 102 for update;
      geo_array:=MDSYS.SDO_GEORASTER_ARRAY(geor,geor1);
      sdo_geor_ra.rasterMathOp(geo_array,SDO_STRING2_ARRAY('max()'),null,geor2);
      update georaster_table set georaster = geor2 where georid = 102;
      commit;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=100;
     SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)
    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=101;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 122, 159) 1 row selected.

    -- In the results of the next SELECT statement, note:
    -- max(181,163,159,181,122,159)  ==> 181

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =102;
     SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
     --------------------------------------------------------------------------------
     SDO_NUMBER_ARRAY(181)
    1 row selected.

**Parent topic:** Statistical Operations

### 5.7 Logical Operations

A major use of raster algebra is to apply logical models to raster layers from different sources; that is, you can apply logical operations on one or more layers, from one or more GeoRaster objects, to generate a new GeoRaster object.

To apply logical operations, you can either use raster algebra procedures with logical expressions, which is more flexible and powerful and mostly be used for some complicated raster logical operations, or use raster algebra procedures only, which are straightforward and do not require constructing complicated logical expressions. However, using raster algebra procedures only (that is, without logical expressions) has some limitations and is mainly used for some specific raster logical operations.

- Using Raster Algebra Procedures with Logical Expressions
- Using Raster Algebra Functions Only

**Parent topic:** Raster Algebra and Analytics

#### 5.7.1 Using Raster Algebra Procedures with Logical Expressions

GeoRaster logical expressions can be conditional expressions, boolean expressions, or both, which can take any combination of unary and binary boolean operators (!, &, \|, ^) and comparison operators (=, \<, \>, \<=, \>=, !=).

To apply logical expressions on the raster data, you must use raster algebra procedures defined in the SDO_GEOR_RA package and specify appropriate parameters with your constructed logical expressions.

Example 5-16 Using SDO_GEOR_RA.rasterMathOp with condition operators

This example implements logic described in the following pseudocode to implement 3–band raster data segmentation:

     if ( (layer1 < 100)
          & (layer2< 1000)
          & (layer3< 500))
     then output = 10
     elsif ( (layer1 < 200)
             & (layer2< 2000)
             & (layer3< 1000))
     then output = 20
     elsif ( (layer1 < 300)
             & (layer2< 3000)
             & (layer3< 1500))
     then output = 30
     elsif ( (layer1 < 400)
             & (layer2< 4000)
             & (layer3< 2000))
     then output = 40
     elsif ( (layer1 < 500)
             & (layer2< 5000)
             & (layer3< 2500))
     then output = 50
     else
          output = 0

The example calls the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure, as follows

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      mycursor   sys_refcursor;
      expr       varchar2(1024);
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      --construct logical expression
      expr :='condition((({0}<100)&({1}<1000)&({2}<500)),'||
                       '10,'||
                       'condition((({0}<200)&({1}<2000)&({2}<1000)),'||
                                 '20,'||
                                 'condition((({0}<300)&({1}<3000)&({2}<1500)),'||
                                           '30,'||
                                           'condition((({0}<400)&({1}<4000)&({2}<2000)),'||
                                                     '40,'||
                                                     'condition((({0}<500)&({1}<5000)&({2}<2500)),'||
                                                               '50,'||
                                                               '0)'||
                                                    ')'||
                                          ')'||
                                ')'||
                      ')';

      sdo_geor_ra.rasterMathOp(geor, sdo_string2_array(expr),null, geor1, 'true', 0, 'parallel=4');
      update georaster_table set georaster = geor1 where georid = 101;
      commit;
    END;
    /

Example 5-17 Using SDO_GEOR_RA.rasterMathOp with a condition operator

This example uses statistical functions and arithmetic operations to implement the simple logic described in the following pseudocode:

    if (sum()>min()*3)
    then
       output = sqrt(layer0+layer2)
    else
       output = layer1*1.5

The example calls the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure, as follows

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      mycursor   sys_refcursor;
      expr       varchar2(1024);
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      --construct logical expression
      expr :='condition(sum()>min()*3,sqrt({0}+{2}),{1}*1.5)';
      sdo_geor_ra.rasterMathOp(geor, sdo_string2_array(expr),null, geor1, 'true', 0, 'parallel=4');
      update georaster_table set georaster = geor1 where georid = 101;
      commit;
    END;
    /

**Parent topic:** Logical Operations

#### 5.7.2 Using Raster Algebra Functions Only

To perform logical operations using only raster algebra functions, you have the following options

- Use the [SDO_GEOR_RA.diff](sdo-geor-ra-ref.md) procedure.

  For example, if a cell value in raster A is different from the cell value in raster B, the cell value in raster A is returned. If the cell values are the same, the value 0 (zero) is returned.

- Use the [SDO_GEOR_RA.over](sdo-geor-ra-ref.md) procedure.

  For example, if a cell value in raster A is not equal to 0 (zero), the cell value in raster A is returned. If the cell value in raster A is equal to 0, the cell value in raster B is returned.

Example 5-18 Using SDO_GEOR_RA.diff

This example calls the [SDO_GEOR_RA.diff](sdo-geor-ra-ref.md) procedure to generate a new GeoRaster object from two 3–layer source GeoRaster objects.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geom       sdo_geometry;
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      select georaster into geor2 from georaster_table where georid = 102 for update;
      geom:=null;
      sdo_geor_ra.diff(geor,geor1,geom,null,geor2);
      update georaster_table set georaster = geor2 where georid = 102;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=100;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=101;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 122, 159)

    1 row selected.

    --  In the results of the next SELECT statement, note:
    --  181 =181  ==>  0
    --  163!=122  ==>  163
    --  159 =159  ==>  0

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =102;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(0, 163, 0)

    1 row selected.

Example 5-19 Using SDO_GEOR_RA.over

This example calls the [SDO_GEOR_RA.over](sdo-geor-ra-ref.md) procedure to generate a new GeoRaster object from two 3–layer source GeoRaster objects.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geom       sdo_geometry;
    BEGIN
      select georaster into geor from georaster_table where georid = 102;
      select georaster into geor1 from georaster_table where georid = 101;
      select georaster into geor2 from georaster_table where georid = 100 for update;
      geom:=null;
      sdo_geor_ra.over(geor,geor1,geom,null,geor2);
      update georaster_table set georaster = geor2 where georid = 100;
    END;
    /

    PL/SQL procedure successfully completed.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=102;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(0, 163, 0)

    1 row selected.

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid=101;

    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 122, 159)

    1 row selected.

    --  In the results of the next SELECT statement, note:
    --  0 =0    ==>  181      result from georid=101
    --  163!=0  ==>  163      result from georid=102
    --  0 =0    ==>  159      result from georid=101

    SELECT sdo_geor.getcellvalue(georaster,0,100,100,'') FROM georaster_table WHERE georid =100;
    SDO_GEOR.GETCELLVALUE(GEORASTER,0,100,100,'')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(181, 163, 159)

    1 row selected.

**Parent topic:** Logical Operations

### 5.8 Raster Data Scaling and Offsetting

You can perform raster data scaling and offsetting operations.

Raster algebra has many applications, such as cartographic modeling (see Cartographic Modeling), vegetation index computing (see [Vegetation Index Computation](image-processing-virtual-mosaic.md)), and tasseled cap transformation (see [Tasseled Cap Transformation](image-processing-virtual-mosaic.md)). Topics in this chapter and in [Image Processing and Virtual Mosaic](image-processing-virtual-mosaic.md) describe a few sample applications of the GeoRaster raster algebra.

Example 5-20 Converting DEM Data from Feet to Meters

The cell value of a GeoRaster object may represent a quantitative attribute of spatial objects, which could be in a specific unit. For example, the elevation data in a DEM GeoRaster object could be in the unit of feet. An application may require you to convert the elevations into another unit, such as meters, for georectification and other operations. You can use the raster algebra to scale the DEM data from feet into meters (that is, unit conversion), as shown in Example 5-20.

    DECLARE
      geor1    SDO_GEORASTER;
      geor2    SDO_GEORASTER;
    BEGIN
      --Source GeoRaster object with a single DEM layer
      select georaster into geor1 from georaster_table where georid = 1;
      --To store the output DEM layer
      select georaster into geor2 from georaster_table where georid = 2 for update;
      --Scale elevation from feet to meters using the unit factor
      sdo_geor_ra.rasterMathOp(geor1,SDO_STRING2_ARRAY('{0} * 0.3048'),null,geor2);
      --Commit changes to the output georaster object
      update georaster_table set georaster = geor2 where georid = 2;
      commit;
    END;
    /

Example 5-21 Offsetting DEM by Geoid Height

The cell data of a GeoRaster object may need to be offset by a constant for further processing. For example, a DEM layer may represent orthometric elevation instead of ellipsoidal elevation. To orthorectify a raw image georeferenced by an RPC model requires ellipsoidal elevation. Example 5-21 offsets the orthometric DEM by the geoid height, resulting in an ellipsoidal DEM.

    DECLARE
      geor1    SDO_GEORASTER;
      geor2    SDO_GEORASTER;
    BEGIN
      --Source GeoRaster object with a single orthometric DEM layer
      select georaster into geor1 from georaster_table where georid = 1;
      --To store the output DEM layer
      select georaster into geor2 from georaster_table where georid = 2 for update;
      --Offset elevation by geoid height to get ellipsoidal elevation
      sdo_geor_ra.rasterMathOp(geor1,SDO_STRING2_ARRAY('{0} - 28.8'),null,geor2);
      --Commit changes to the output GeoRaster object
      update georaster_table set georaster = geor2 where georid = 2;
      commit;
    END;
    /

Example 5-22 Converting (Scaling) and Offsetting

You can combine the operations of Example 5-20 and Example 5-21 into a single simple step, as shown in Example 5-22.

    DECLARE
      geor1    SDO_GEORASTER;
      geor2    SDO_GEORASTER;
    BEGIN
      --Source GeoRaster object with a single DEM layer
      select georaster into geor1 from georaster_table where georid = 1;
      --To store the output DEM layer
      select georaster into geor2 from georaster_table where georid = 2 for update;
      --Scale elevation from feet to meters and offset elevation by geoid height
      sdo_geor_ra.rasterMathOp(geor1,SDO_STRING2_ARRAY('{0} * 0.3048 - 28.8'),null,geor2);
      --Commit changes to the output georaster object
      update georaster_table set georaster = geor2 where georid = 2;
      commit;
    END;
    /

**Parent topic:** Raster Algebra and Analytics

### 5.9 Raster Data Casting

Raster data casting maps cell values from one data type to another.

In GeoRaster, there are two types of casting operations: one uses the `cellDepth` keyword in the `storageParam` parameter of operations, and the other uses the `castingExpr` operation in the GeoRaster raster algebra. (`castingExpr` is one of the `arithmeticExpr` operations, as described in Raster Algebra Language.)

Whenever you apply an operation which stores the raster data result into a new GeoRaster object, you can use the `cellDepth` keyword in the `storageParam` parameter of that operation. (The `cellDepth` keyword and its values are described in [Table 1-1](georaster-overview-and-concepts.md).) If the `cellDepth` is specified, the target GeoRaster object will be created using that `cellDepth` value, and the raster cell data will be automatically cast to that `cellDepth` value for storage. You can directly use `cellDepth` in the `storageParam` parameter to do the casting if the source data is in lower cell depth and the resulting data is in higher cell depth. In this case, the casting is transparent and fast.

However, if you specify a lower cell depth for data in higher cell depth, changing the cell depth using the `cellDepth` keyword in the `storageParam` parameter can cause loss or change of data and reduced precision or quality. To have better control of the precision and accuracy, you can use the Raster Algebra casting operator, `castingExpr`.

For example, assume you have a raster with a cell depth of `32BIT_REAL` and a value range in \[0.0, 100.0). You can use Example 5-23 to perform linear segmentation of the raster into 10 different classes, each of which has a cell value that is a multiple of 10 (0, 10, 20, …, 90), using the `castint` operator. This operation casts all cell values to their closest lower multiple of 10; for example, all numbers from 60 to 69 are cast to 60.

Example 5-23 Linear Segmentation of a Raster

    DECLARE
      geor1    SDO_GEORASTER;
      geor2    SDO_GEORASTER;
    BEGIN
      --Source georaster object with cell value range [0.0,100.0)
      select georaster into geor1 from georaster_table where georid = 1;
      --Target georaster object to store the output layer
      select georaster into geor2 from georaster_table where georid = 2 for update;
      --Linearly segment the source raster into 10 classes and store in 8BIT cell depth
      sdo_geor_ra.rasterMathOp(geor1,
        SDO_STRING2_ARRAY('(castint({0}/10)*10'),
        'celldepth=8BIT',
        geor2);
      --Commit changes to the output georaster object
      update georaster_table set georaster = geor2 where georid = 2;
      commit;
    END;
    /

As shown in Example 5-23, you can combine the usage of the `cellDepth` keyword in the `storageParam` parameter with the raster algebra casting operator, so that the result can be calculated correctly as well as stored in an appropriate and concise way. In Example 5-23, the output cell values are integers equal to or less than 90, so the resulting raster can be stored using `8BIT` cell depth (instead of `32BIT_REAL`), which saves storage space.

**Parent topic:** Raster Algebra and Analytics

### 5.10 Cartographic Modeling

Raster algebra is widely used in cartographic modeling and is considered an essential component of GIS systems. Using the PL/SQL and the raster algebra expressions and functions, you can conduct cartographic modeling over a large number of rasters and images of virtually unlimited size.

For example, a cartographic modeling process for wildfire evaluation might retrieve the elevation, slope, aspect, temperature, wetness, and other information from a series of raster layers and then evaluate the cells one-by-one to create a resulting raster map, which can be further classified to create a thematic map. Change analysis, site selection, suitability analysis, climate modeling, and oil field evaluation using the raster layer overlay technique are other typical cartographic modeling processes. In those cases, arithmetic, relational, and logical operations may need to be combined.

Assume that a hypothetical cartographic model involves seven different raster layers and has an expression as follows. and that the modeling result is a raster map with 0 and 1 as cell values:

    output = 1 if ( (100 < layer1 <= 500)
                    & (layer2 == 3 or layer2 == 10)
                    & ( (layer3+layer4) * log(Layer5) / sqrt(layer5) ) >= layer6)
                    || (layer7 != 1) )
                    is TRUE and
             0 if otherwise

Example 5-24 shows how to run the preceding cartographic model in GeoRaster and store the result as a bitmap.

Example 5-24 Cartographic Modeling

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      mycursor   sys_refcursor;
      expr       varchar2(1024);
    BEGIN
      --7 source GeoRaster objects, each of which contains one source layer in the order of 1 to 7
      OPEN mycursor FOR
        select georaster from georaster_table where georid >0 and georid <=7 order by georid;
      --Output GeoRaster object to contain the result
      insert into georaster_table (georid, georaster) values (8, sdo_geor.init('RDT_1',8))
        returning georaster into geor1;
      --Modeling using arithmeticExpr, booleanExpr, and rasterMathOp
      expr :=
       'condition(
             ( (100<{0,0}) & ({0,0}<=500) )
               & ( ({1,0}=3) | ({1,0}=10) )
               & ( ( ( ({2,0}+{3,0}) * log({4,0} ) / sqrt({4,0}) ) >= {5,0} ) | ({6,0}!=1)
             ),
             1,
             0)';
      sdo_geor_ra.rasterMathOp(mycursor, sdo_string2_array(expr),
                               'celldepth=1BIT', geor1, 'true', 0, 'parallel=4');
      update georaster_table set georaster = geor1 where georid = 8;
      commit;
    END;
    /

The process in Example 5-24 considers NODATA and will assign 0 (zero) to any cell that is a NODATA cell in one or more source layers. It is also parallelized into four processes to leverage multiple CPUs of the database server to improve performance.

**Parent topic:** Raster Algebra and Analytics

### 5.11 Terrain Modeling and Analysis

You can use the data from input GeoRaster objects to perform terrain modeling and analysis.

The [SDO_GEOR_GDAL.dem](SDO_GEOR_GDAL-reference.md) procedure uses the data from an input GeoRaster object to generate output based on the specified `processing` parameter. The input GeoRaster object is usually a Digital Elevation Model, and the `processing` values could be a value such as `hillshade`, `slope`, `aspect`, `color-relief`, or `roughness`.

Example 5-25 Hillshade

If the `processing` parameter value is `hillshade` the procedue generates a grayscale image that represent the shadows of the elevated areas over the adjacent areas, mimicking the visual effect of sunlight.

This example creates a hillshade image.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      select raster into gr1 from imagery where id = 1;
      delete from imagery where id = 2;
      insert into imagery values(2, sdo_geor.init('imagery_rdt',2))
             returning raster into gr2;
      sdo_geor_gdal.dem(gr1, gr2, 'hillshade');
      update imagery set raster = gr2 where id = 2;
      commit;
    END;
    /

Example 5-26 Slope

The procedure can generate a slope or aspect raster based on the elevation values of an input raster. In that case the output pixel values does not produce a visual appealing output, but a useful raster surface that might be used for land use and land allocation analyses. For example, it could be used to define areas good for wine production based on the slope and the angle of exposure to the sun (aspect).

The following example creates a raster representing the slope generated from raster elevation data. The resulting pixel values will be represented in percentage, instead of the default degree output.

    DECLARE
      gr1 sdo_georaster;
      gr3 sdo_georaster;
    BEGIN
      select raster into gr1 from imagery where id = 1;
      delete from imagery where id = 3;
      insert into imagery values(3, sdo_geor.init('imagery_rdt', 3))
             returning raster into gr3;
      sdo_geor_gdal.dem(gr1, gr3, 'slope', 'slopevalue=percent');
      update imagery set raster = gr3 where id = 3;
      commit;
    END;
    /

Example 5-27 Aspect

This example creates a raster representing the aspect o generated from raster elevation data. The pixel representing flat areas will have the value 0 instead of the default -9999.

    DECLARE
      gr1 sdo_georaster;
      gr4 sdo_georaster;
    BEGIN
      select raster into gr1 from imagery where id = 1;
      delete from imagery where id = 4;
      insert into imagery values(4, sdo_geor.init('imagery_rdt', 4))
             returning raster into gr4;
      sdo_geor_gdal.dem(gr1, gr4, 'aspect', 'zeroforflat=yes');
      update imagery set raster = gr4 where id = 4;
      commit;
    END;
    /

Example 5-28 Color-relief

This example creates a raster representing the color-relief generated from raster elevation data using the file colorfile.txt. For this example, the `colorfile.txt` file contains the following "elevation-percent red green blue" values

    0%  180   0 255
    10%  70   0 255
    20%   0  70 255
    30%   0 180 255
    40%   0 255 180
    50%   0 255  70
    60%  70 255   0
    70% 180 255   0
    80% 255 180   0
    90% 255  70   0
    nv    0   0   0

    DECLARE
      gr1 sdo_georaster;
      gr5 sdo_georaster;
    BEGIN
      select raster into gr1 from imagery where id = 1;
      delete from imagery where id = 5;
      insert into imagery values(5, sdo_geor.init('imagery_rdt', 5))
             returning raster into gr5;
      sdo_geor_gdal.dem(inGeoRaster    => gr1,
                        outGeoRaster   => gr5,
                        processing     => 'color-relief',
                        colorDirectory => 'mydir’,
                        colorFilename  => 'colorfile.txt');
      update imagery set raster = gr5 where id = 5;
      commit;
    END;
    /

In addition to the operations shown in these examples, you can use the procedure to generate Terrain Ruggedness Index (TRI) maps, Topographic Position Index (TPI) maps, and roughness maps from DEM GeoRaster objects.

**Parent topic:** Raster Algebra and Analytics
