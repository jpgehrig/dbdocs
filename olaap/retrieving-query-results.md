This chapter describes how to retrieve the results of a query with an Oracle OLAP Java API `Cursor` and how to gain access to those results. This chapter also describes how to customize the behavior of a `Cursor` to fit your method of displaying the results. For information on the class hierarchies of `Cursor` and its related classes, and for information on the `Cursor` concepts of position, fetch size, and extent, see [Understanding Cursor Classes and Concepts](understanding-cursor-classes-and-concepts.md).

This chapter includes the following topics:

- Retrieving the Results of a Query

- Navigating a CompoundCursor for Different Displays of Data

- Specifying the Behavior of a Cursor

- Calculating Extent and Starting and Ending Positions of a Value

- Specifying a Fetch Size

### 9.1 Retrieving the Results of a Query

A query is an OLAP Java API `Source` that specifies the data that you want to retrieve from the data store and any calculations that you want Oracle OLAP to perform on the data. A `Cursor` is the object that retrieves, or fetches, the result set specified by a `Source`. Creating a `Cursor` for a `Source` involves the following steps:

1.  Get a primary `Source` from an `MdmObject` or create a derived `Source` through operations on a `DataProvider` or a `Source`. For information on getting or creating `Source` objects, see [Understanding Source Objects](understanding-source-objects.md).
2.  If the `Source` is a derived `Source`, then commit the `Transaction` in which you created the `Source`. To commit the `Transaction`, call the `commitCurrentTransaction` method of your `TransactionProvider`. For more information on committing a `Transaction`, see [Using a TransactionProvider](using-transaction-provider.md). If the `Source` is a primary `Source`, then you do not need to commit the `Transaction`.
3.  Create a `CursorManager` by calling a `createCursorManager` method of your `DataProvider` and passing that method the `Source`.
4.  Create a `Cursor` by calling the `createCursor` method of the `CursorManager`.

Example 9-1 Creating a Cursor

This example creates a `Cursor` for the derived `Source` named `querySource`. The example uses a `DataProvider` named `dp`. The example creates a `CursorManager` named `cursorMngr` and a `Cursor` named `queryCursor`.

Finally, the example closes the `CursorManager`. When you have finished using the `Cursor`, you should close the `CursorManager` to free resources.

    CursorManager cursorMngr = dp.createCursorManager(querySource);
    Cursor queryCursor = cursorMngr.createCursor();

    // Use the Cursor in some way, such as to display the values of it.

    cursorMngr.close();

#### 9.1.1 Getting Values from a Cursor

The `Cursor` interface encapsulates the notion of a current position and has methods for moving the current position. The `ValueCursor` and `CompoundCursor` interfaces extend the `Cursor` interface. The Oracle OLAP Java API has implementations of the `ValueCursor` and `CompoundCursor` interfaces. Calling the `createCursor` method of a `CursorManager` returns either a `ValueCursor` or a `CompoundCursor` implementation, depending on the `Source` for which you are creating the `Cursor`.

A `ValueCursor` is returned for a `Source` that has a single set of values. A `ValueCursor` has a value at its current position, and it has methods for getting the value at the current position.

A `CompoundCursor` is created for a `Source` that has more than one set of values, which is a `Source` that has one or more outputs. Each set of values of the `Source` is represented by a child `ValueCursor` of the `CompoundCursor`. A `CompoundCursor` has methods for getting its child `Cursor` objects.

The structure of the `Source` determines the structure of the `Cursor`. A `Source` can have nested outputs, which occurs when one or more of the outputs of the `Source` is itself a `Source` with outputs. If a `Source` has a nested output, then the `CompoundCursor` for that `Source` has a child `CompoundCursor` for that nested output.

The `CompoundCursor` coordinates the positions of the child `Cursor` objects that it contains. The current position of the `CompoundCursor` specifies one set of positions of the child `Cursor` objects.

For an example of a `Source` that has only one level of output values, see Example 9-4. For an example of a `Source` that has nested output values, see Example 9-5.

An example of a `Source` that represents a single set of values is one returned by the `getSource` method of an `MdmDimension`, such as an `MdmPrimaryDimension` that represents product values. Creating a `Cursor` for that `Source` returns a `ValueCursor`. Calling the `getCurrentValue` method returns the product value at the current position of that `ValueCursor`.

Example 9-2 Getting a Single Value from a ValueCursor

This example gets the `Source` from `mdmProdHier`, which is an `MdmLevelHierarchy` that represents product values, and creates a `Cursor` for that `Source`. The example sets the current position to the fifth element of the `ValueCursor` and gets the product value from the `Cursor`. The example then closes the `CursorManager`. In the example, `dp` is the `DataProvider`.

    Source prodSource = mdmProdHier.getSource();
    // Because prodSource is a primary Source, you do not need to
    // commit the current Transaction.
    CursorManager cursorMngr = dp.createCursorManager(prodSource);
    Cursor prodCursor = cursorMngr.createCursor();
    // Cast the Cursor to a ValueCursor.
    ValueCursor prodValues = (ValueCursor) prodCursor;
    // Set the position to the fifth element of the ValueCursor.
    prodValues.setPosition(5);

    // Product values are strings. Get the value at the current position.
    String value = prodValues.getCurrentString();

    // Do something with the value, such as display it.

    // Close the CursorManager.
    cursorMngr.close();

Example 9-3 Getting All of the Values from a ValueCursor

This example uses the same `Cursor` as Example 9-2. This example uses a `do...while` loop and the `next` method of the `ValueCursor` to move through the positions of the `ValueCursor`. The `next` method begins at a valid position and returns `true` when an additional position exists in the `Cursor`. It also advances the current position to that next position.

The example sets the position to the first position of the `ValueCursor`. The example loops through the positions and uses the `getCurrentValue` method to get the value at the current position.

    // prodValues is the ValueCursor for prodSource.
    prodValues.setPosition(1);
    do
    {
      println(prodValues.getCurrentValue);
    } while(prodValues.next());

The values of the result set represented by a `CompoundCursor` are in the child `ValueCursor` objects of the `CompoundCursor`. To get those values, you must get the child `ValueCursor` objects from the `CompoundCursor`.

An example of a `CompoundCursor` is one that is returned by calling the `createCursor` method of a `CursorManager` for a `Source` that represents the values of a measure as specified by selected values from the dimensions of the measure.

Example 9-4 uses a `Source`, named `units`, that results from calling the `getSource` method of an `MdmBaseMeasure` that represents the number of units sold. The dimensions of the measure are `MdmPrimaryDimension` objects representing products, customers, times, and channels. This example uses `Source` objects that represent selected values from the default hierarchies of those dimensions. The names of those `Source` objects are `prodSel`, `custSel`, `timeSel`, and `chanSel`. The creation of the `Source` objects representing the measure and the dimension selections is not shown.

Example 9-4 joins the dimension selections to the measure, which results in a `Source` named `unitsForSelections`. It creates a `CompoundCursor`, named `unitsForSelCursor`, for `unitsForSelections`, and gets the base `ValueCursor` and the outputs from the `CompoundCursor`. Each output is a `ValueCursor`, in this case. The outputs are returned in a `List`. The order of the outputs in the `List` is the inverse of the order in which the outputs were added to the list of outputs by the successive join operations. In the example, `dp` is the `DataProvider`.

Example 9-4 Getting ValueCursor Objects from a CompoundCursor

    Source unitsForSelections = units.join(prodSel)
                                     .join(custSel)
                                     .join(timeSel)
                                     .join(chanSel);
    // Commit the current Transaction (code not shown).

    // Create a Cursor for unitsForSelections.
    CursorManager cursorMngr = dp.createCursorManager(unitsForSelections);
    CompoundCursor unitsForSelCursor = (CompoundCursor)
                                        cursorMngr.createCursor();

    // Get the base ValueCursor.
    ValueCursor specifiedUnitsVals = unitsForSelCursor.getValueCursor();

    // Get the outputs.
    List outputs = unitsForSelCursor.getOutputs();
    ValueCursor chanSelVals = (ValueCursor) outputs.get(0);
    ValueCursor timeSelVals = (ValueCursor) outputs.get(1);
    ValueCursor custSelVals = (ValueCursor) outputs.get(2);
    ValueCursor prodSelVals = (ValueCursor) outputs.get(3);

    // You can now get the values from the ValueCursor objects.
    // When you have finished using the Cursor objects, close the CursorManager.
    cursorMngr.close();

Example 9-5 uses the same units measure as Example 9-4, but it joins the dimension selections to the measure differently. Example 9-5 joins two of the dimension selections together. It then joins the result to the `Source` produced by joining the single dimension selections to the measure. The resulting `Source`, `unitsForSelections`, represents a query has nested outputs, which means it has more than one level of outputs.

The `CompoundCursor` that this example creates for `unitsForSelections` therefore also has nested outputs. The `CompoundCursor` has a child base `ValueCursor` and has as outputs three child `ValueCursor` objects and one child `CompoundCursor`.

Example 9-5 joins the selection of channel dimension values, `chanSel`, to the selection of customer dimension values, `custSel`. The result is `custByChanSel`, a `Source` that has customer values as the base values and channel values as the values of the output. The example joins to `units` the selections of product and time values, and then joins `custByChanSel`. The resulting query is represented by `unitsForSelections`.

The example commits the current `Transaction` and creates a `CompoundCursor`, named `unitsForSelCursor`, for `unitsForSelections`.

The example gets the base `ValueCursor` and the outputs from the `CompoundCursor`. In the example, `dp` is the `DataProvider`.

Example 9-5 Getting Values from a CompoundCursor with Nested Outputs

    Source custByChanSel = custSel.join(chanSel);
    Source unitsForSelections = units.join(prodSel)
                                     .join(timeSel)
                                     .join(custByChanSel);
    // Commit the current Transaction (code not shown).

    // Create a Cursor for unitsForSelections.
    CursorManager cursorMngr = dp.createCursorManager(unitsForSelections);
    Cursor unitsForSelCursor = cursorMngr.createCursor();

    // Send the Cursor to a method that does different operations
    // depending on whether the Cursor is a CompoundCursor or a
    // ValueCursor.
    printCursor(unitsForSelCursor);
    cursorMngr.close();
    // The remaining code of someMethod is not shown.

    // The following code is in from the CursorPrintWriter class.
    // The printCursor method has a do...while loop that moves through the positions
    // of the Cursor passed to it. At each position, the method prints the number of
    // the iteration through the loop and then a colon and a space. The output
    // object is a PrintWriter. The method calls the private _printTuple method and
    // then prints a new line. A "tuple" is the set of output ValueCursor values
    // specified by one position of the parent CompoundCursor. The method prints one
    // line for each position of the parent CompoundCursor.
    private void printCursor(Cursor rootCursor)
    {
      int i = 1;
      do
      {
         print(i++ + ": ");
         _printTuple(rootCursor);
         println();
         flush();
      } while(rootCursor.next());
    }

    // If the Cursor passed to the _printTuple method is a ValueCursor, then
    // the method prints the value at the current position of the ValueCursor.
    // If the Cursor passed in is a CompoundCursor, then the method gets the
    // outputs of the CompoundCursor and iterates through the outputs,
    // recursively calling itself for each output. The method then gets the
    // base ValueCursor of the CompoundCursor and calls itself again.
    private void _printTuple(Cursor cursor)
    {
      if(cursor instanceof CompoundCursor)
      {
        CompoundCursor compoundCursor = (CompoundCursor)cursor;
        // Put an open parenthesis before the value of each output.
        print("(");
        Iterator iterOutputs = compoundCursor.getOutputs().iterator();
        Cursor output = (Cursor)iterOutputs.next();
        _printTuple(output);
        while(iterOutputs.hasNext())
        {
          // Put a comma after the value of each output.
          print(",");
          _printTuple((Cursor)iterOutputs.next());
        }
        // Put a comma after the value of the last output.
        print(",");
        // Get the base ValueCursor.
        _printTuple(compoundCursor.getValueCursor());

        // Put a close parenthesis after the base value to indicate
        // the end of the tuple.
        print(")");
      }
      else if(cursor instanceof ValueCursor)
      {
        ValueCursor valueCursor = (ValueCursor) cursor;
        if (valueCursor.hasCurrentValue())
          print(valueCursor.getCurrentValue());
        else                       // If this position has a null value.
          print("NA");
      }
    }

### 9.2 Navigating a CompoundCursor for Different Displays of Data

With the methods of a `CompoundCursor` you can easily move through, or navigate, the `CompoundCursor` structure and get the values from the `ValueCursor` descendents of the `CompoundCursor`. Data from a multidimensional OLAP query is often displayed in a crosstab format, or as a table or a graph.

To display the data for multiple rows and columns, you loop through the positions at different levels of the `CompoundCursor` depending on the needs of your display. For some displays, such as a table, you loop through the positions of the parent `CompoundCursor`. For other displays, such as a crosstab, you loop through the positions of the child `Cursor` objects.

To display the results of a query in a table view, in which each row contains a value from each output `ValueCursor` and from the base `ValueCursor`, you determine the position of the top-level, or root, `CompoundCursor` and then iterate through its positions. Example 9-6 displays only a portion of the result set at one time. It creates a `Cursor` for a `Source` that represents a query that is based on a measure that has unit cost values. The dimensions of the measure are the product and time dimensions. The creation of the primary `Source` objects and the derived selections of the dimensions is not shown.

The example joins the `Source` objects representing the dimension value selections to the `Source` representing the measure. It commits the current `Transaction` and then creates a `Cursor`, casting it to a `CompoundCursor`. The example sets the position of the `CompoundCursor`, iterates through twelve positions of the `CompoundCursor`, and prints out the values specified at those positions. The `DataProvider` is `dp`.

Example 9-6 Navigating for a Table View

    Source unitPriceByMonth = unitPrice.join(productSel)
                                       .join(timeSel);
    // Commit the current Transaction (code not shown).

    // Create a Cursor for unitPriceByMonth.
    CursorManager cursorMngr = dp.createCursorManager(unitPriceByMonth);
    CompoundCursor rootCursor = (CompoundCursor) cursorMngr.createCursor();

    // Determine a starting position and the number of rows to display.
    int start = 7;
    int numRows = 12;

    println("Month     Product     Unit Price");
    println("-------   --------   ----------");

    // Iterate through the specified positions of the root CompoundCursor.
    // Assume that the Cursor contains at least (start + numRows) positions.
    for(int pos = start; pos < start + numRows; pos++)
    {
      // Set the position of the root CompoundCursor.
      rootCursor.setPosition(pos);
      // Print the local values of the output and base ValueCursors.
      // The getLocalValue method gets the local value from the unique
      // value of a dimension element.
      String timeValue = ((ValueCursor)rootCursor.getOutputs().get(0))
                         .getCurrentString();
      String timeLocVal = getLocalValue(timeValue);
      String prodValue = ((ValueCursor)rootCursor.getOutputs().get(1))
                         .getCurrentString();
      String prodLocVal = getLocalValue(prodValue);
      Object price = rootCursor.getValueCursor().getCurrentValue();
      println(timeLocVal + "   " + prodLocVal + "   " +  price);
    }
    cursorMngr.close();

If the time selection for the query has eight values, such as the first month of each calendar quarter for the years 2001 and 2002, and the product selection has three values, then the result set of the `unitPriceByMonth` query has twenty-four positions. The example displays the following table, which has the values specified by positions 7 through 18 of the `CompoundCursor`.

    Month     Product    Unit Price
    -------   --------   ----------
    2001.07   ENVY ABM   2892.18
    2001.07   ENVY EXE   3155.91
    2001.07   ENVY STD   2505.57
    2001.10   ENVY ABM   2856.86
    2001.10   ENVY EXE   3105.53
    2001.10   ENVY STD   2337.3
    2002.01   ENVY ABM   2896.77
    2002.01   ENVY EXE   3008.95
    2002.01   ENVY STD   2140.71
    2002.04   ENVY ABM   2880.39
    2002.04   ENVY EXE   2953.96
    2002.04   ENVY STD   2130.88

Example 9-7 Navigating for a Crosstab View Without Pages

This example uses the same query as Example 9-6. In a crosstab view, the first row is column headings, which are the values from `prodSel` in this example. The output for `prodSel` is the faster varying output because the `prodSel` dimension selection is the last output in the list of outputs that results from the operations that join the measure to the dimension selections. The remaining rows begin with a row heading. The row headings are values from the slower varying output, which is `timeSel`. The remaining positions of the rows, under the column headings, contain the `unitPrice` values specified by the set of the dimension values. To display the results of a query in a crosstab view, you iterate through the positions of the children of the top-level `CompoundCursor`.

The `DataProvider` is `dp`.

    Source unitPriceByMonth = unitPrice.join(productSel)
                                       .join(timeSel);
    // Commit the current Transaction (code not shown).

    // Create a Cursor for unitPriceByMonth.
    CursorManager cursorMngr = dp.createCursorManager(unitPriceByMonth);
    CompoundCursor rootCursor = (CompoundCursor) cursorMngr.createCursor();

    // Get the outputs and the ValueCursor objects.
    List outputs = rootCursor.getOutputs();
    // The first output has the values of timeSel, the slower varying output.
    ValueCursor rowCursor = (ValueCursor) outputs.get(0);
    // The second output has the faster varying values of productSel.
    ValueCursor columnCursor = (ValueCursor) outputs.get(1);
    // The base ValueCursor has the values from unitPrice.
    ValueCursor unitPriceValues = rootCursor.getValueCursor();

    // Display the values as a crosstab.
    println("                     PRODUCT");
    println("          ---------------------------------");
    print("Month     ");
    do
    {
      String value = ((ValueCursor) columnCursor).getCurrentString();
      print(getContext().getLocalValue(value) + "    ");
    } while (columnCursor.next());
    println("\n-------   --------    --------    --------");

    // Reset the column Cursor to its first element.
    columnCursor.setPosition(1);

    do
    {
      // Print the row dimension values.
      String value = ((ValueCursor) rowCursor).getCurrentString();
      print(getContext().getLocalValue(value) + "    ");
      // Loop over columns.
      do
      {
        // Print data value.
        print(unitPriceValues.getCurrentValue() + "     ");
      } while (columnCursor.next());

      println();

      // Reset the column Cursor to its first element.
      columnCursor.setPosition(1);
      } while (rowCursor.next());

    cursorMngr.close();

The following is a crosstab view of the values from the result set specified by the `unitPriceByMonth` query. The first line labels the rightmost three columns as having product values. The third line labels the first column as having month values and then labels each of the rightmost three columns with the product value for that column. The remaining lines have the month value in the left column and then have the data values from the units measure for the specified month and product.

                         PRODUCT
              ---------------------------------
    Month     ENVY ABM    ENVY EXE    ENVY STD
    -------   --------    --------    --------
    2001.01    3042.22     3223.28     2426.07
    2001.04    3026.12     3107.65     2412.42
    2001.07    2892.18     3155.91     2505.57
    2001.10    2856.86     3105.53     2337.30
    2002.01    2896.77     3008.95     2140.71
    2002.04    2880.39     2953.96     2130.88
    2002.07    2865.14     3002.34     2074.56
    2002.10    2850.88     2943.96     1921.62

Example 9-8 Navigating for a Crosstab View With Pages

This example creates a `Source` that is based on a measure of units sold values. The dimensions of the measure are the customer, product, time, and channel dimensions. The `Source` objects for the dimensions represent selections of the dimension values. The creation of those `Source` objects is not shown.

The query that results from joining the dimension selections to the measure `Source` represents unit sold values as specified by the values of the outputs.

The example creates a `Cursor` for the query and then sends the `Cursor` to the `printAsCrosstab` method, which prints the values from the `Cursor` in a crosstab. That method calls other methods that print page, column, and row values.

The fastest-varying output of the `Cursor` is the selection of products, which has three values (the product items ENVY ABM, ENVY EXE, and ENVY STD). The product values are the column headings of the crosstab. The next fastest-varying output is the selection of customers, which has three values (the customers COMP SERV TOK, COMP WHSE LON, and COMP WHSE SD). Those three values are the row headings. The page dimensions are selections of three time values (the months 2000.01, 2000.02, and 2000.03), and one channel value (DIR, which is the direct sales channel).

The `DataProvider` is `dp`. The `getLocalValue` method gets the local value from a unique dimension value.

    // In someMethod.
    Source unitsForSelections = units.join(prodSel)
                                     .join(custSel)
                                     .join(timeSel)
                                     .join(chanSel);
    // Commit the current Transaction (code not shown).

    // Create a Cursor for unitsForSelections.
    CursorManager cursorMngr = dp.createCursorManager(unitsForSelections);
    CompoundCursor unitsForSelCursor = (CompoundCursor) cursorMngr.createCursor();

    // Send the Cursor to the printAsCrosstab method.
    printAsCrosstab(unitsForSelCursor);

    cursorMngr.close();
    // The remainder of the code of someMethod is not shown.

    private void printAsCrosstab(CompoundCursor rootCursor)
    {
      List outputs = rootCursor.getOutputs();
      int nOutputs = outputs.size();

      // Set the initial positions of all outputs.
      Iterator outputIter = outputs.iterator();
      while (outputIter.hasNext())
        ((Cursor) outputIter.next()).setPosition(1);

      // The last output is fastest-varying; it represents columns.
      // The next to last output represents rows.
      // All other outputs are on the page.
      Cursor colCursor = (Cursor) outputs.get(nOutputs - 1);
      Cursor rowCursor = (Cursor) outputs.get(nOutputs - 2);
      ArrayList pageCursors = new ArrayList();
      for (int i = 0 ; i < nOutputs - 2 ; i++)
      {
        pageCursors.add(outputs.get(i));
      }

      // Get the base ValueCursor, which has the data values.
      ValueCursor dataCursor = rootCursor.getValueCursor();

      // Print the pages of the crosstab.
      printPages(pageCursors, 0, rowCursor, colCursor, dataCursor);
    }

    // Prints the pages of a crosstab.
    private void printPages(List pageCursors, int pageIndex, Cursor rowCursor,
                            Cursor colCursor, ValueCursor dataCursor)
    {
      // Get a Cursor for this page.
      Cursor pageCursor = (Cursor) pageCursors.get(pageIndex);

      // Loop over the values of this page dimension.
      do
      {
        // If this is the fastest-varying page dimension, print a page.
        if (pageIndex == pageCursors.size() - 1)
        {
          // Print the values of the page dimensions.
          printPageHeadings(pageCursors);

          // Print the column headings.
          printColumnHeadings(colCursor);

          // Print the rows.
          printRows(rowCursor, colCursor, dataCursor);

          // Print a couple of blank lines to delimit pages.
          println();
          println();
        }

        // If this is not the fastest-varying page, recurse to the
        // next fastest-varying dimension.
        else
        {
          printPages(pageCursors, pageIndex + 1, rowCursor, colCursor,
                     dataCursor);
        }
      } while (pageCursor.next());

      // Reset this page dimension Cursor to its first element.
      pageCursor.setPosition(1);
    }

    // Prints the values of the page dimensions on each page.
    private void printPageHeadings(List pageCursors)
    {
      // Print the values of the page dimensions.
      Iterator pageIter = pageCursors.iterator();
      while (pageIter.hasNext())
      {
        String value = ((ValueCursor) pageIter.next()).getCurrentString();
        println(getLocalValue(value));
      }
      println();
    }

    // Prints the column headings on each page.
    private void printColumnHeadings(Cursor colCursor)
    {
      do
      {
         print("\t");
         String value = ((ValueCursor) colCursor).getCurrentString();
         print(getLocalValue(value));
      } while (colCursor.next());
      println();
      colCursor.setPosition(1);
    }

    // Prints the rows of each page.
    private void printRows(Cursor rowCursor, Cursor colCursor,
                           ValueCursor dataCursor)
    {
      // Loop over rows.
      do
      {
        // Print row dimension value.
        String value = ((ValueCursor) rowCursor).getCurrentString();
        print(getLocalValue(value));
        print("\t");
        // Loop over columns.
        do
        {
          // Print data value.
          print(dataCursor.getCurrentValue());
          print("\t");
        } while (colCursor.next());
        println();

        // Reset the column Cursor to its first element.
        colCursor.setPosition(1);
      } while (rowCursor.next());

      // Reset the row Cursor to its first element.
      rowCursor.setPosition(1);
    }

The example displays the following values, formatted as a crosstab. The display has added page, column, and row headings to identify the local values of the dimensions.

    Channel DIR
    Month 2001.01
                               Product
                    ------------------------------
    Customer        ENVY ABM   ENVY EXE   ENVY STD
    -------------   --------   --------   --------
    COMP WHSE SD       0          0          1
    COMP SERV TOK         2          4          2
    COMP WHSE LON         1          1          2


    Channel DIR
    Month 2000.02
                               Product
                    ------------------------------
    Customer        ENVY ABM   ENVY EXE   ENVY STD
    -------------   --------   --------   --------
    COMP WHSE SD       1          1          1
    COMP SERV TOK         5          6          6
    COMP WHSE LON         1          2          2


    Channel DIR
    Month 2000.03
                               Product
                    ------------------------------
    Customer        ENVY ABM   ENVY EXE   ENVY STD
    -------------   --------   --------   --------
    COMP WHSE SD       0          2          2
    COMP SERV TOK         2          0          2
    COMP WHSE LON         0          2          3

### 9.3 Specifying the Behavior of a Cursor

You can specify the following aspects of the behavior of a `Cursor`.

- The fetch size of a `Cursor`, which is the number of elements of the result set that the `Cursor` retrieves during one fetch operation.

- Whether or not Oracle OLAP calculates the extent of the `Cursor`. The extent is the total number of positions of the `Cursor`. The extent of a child `Cursor` of a `CompoundCursor` is relative to any of the slower varying outputs of the `CompoundCursor`.

- Whether or not Oracle OLAP calculates the positions in the parent `Cursor` at which the value of a child `Cursor` starts or ends.

To specify the behavior of `Cursor`, you use methods of a `CursorSpecification` that you specify for that `Cursor`. A `CursorSpecification` implements the `CursorInfoSpecification` interface.

You create a `CursorSpecification` for a `Source` by calling the `createCursorInfoSpecification` method of the `DataProvider`. You use methods of the `CursorSpecification` to set the characteristics that you want. You then create a `CursorManager` by calling the appropriate `createCursorManager` method of the `DataProvider`.

**Note:**

Specifying the calculation of the extent or the starting or ending position in a parent `Cursor` of the current value of a child `Cursor` can be a very expensive operation. The calculation can require considerable time and computing resources. You should only specify these calculations when your application needs them.

For more information on the relationships of `Source`, `Cursor`, and `CursorSpecification` objects or the concepts of fetch size, extent, or `Cursor` positions, see [Understanding Cursor Classes and Concepts](understanding-cursor-classes-and-concepts.md).

Example 9-9 creates a `Source`, creates a `CompoundCursorSpecification` for a `Source`, and then gets the child `CursorSpecification` objects from the top-level `CompoundCursorSpecification`.

Example 9-9 Getting CursorSpecification Objects for a Source

    Source unitsForSelections = units.join(prodSel)
                                     .join(custSel)
                                     .join(timeSel)
                                     .join(chanSel);
    // Commit the current Transaction (code not shown).

    // Create a CompoundCursorSpecification for unitsForSelections.
    CompoundCursorSpecification rootCursorSpec = (CompoundCursorSpecification)
                          dp.createCursorInfoSpecification(unitsForSelections);

    // Get the ValueCursorSpecification for the base values.
    ValueCursorSpecification baseValueSpec =
                            rootCursorSpec.getValueCursorSpecification();

    // Get the ValueCursorSpecification objects for the outputs.
    List outputSpecs = rootCursorSpec.getOutputs();
    ValueCursorSpecification chanSelValCSpec =
                           (ValueCursorSpecification) outputSpecs.get(0);
    ValueCursorSpecification timeSelValCSpec =
                           (ValueCursorSpecification) outputSpecs.get(1);
    ValueCursorSpecification prodSelValCSpec =
                           (ValueCursorSpecification) outputSpecs.get(2);
    ValueCursorSpecification custSelValCSpec =
                           (ValueCursorSpecification) outputSpecs.get(3);

Once you have the `CursorSpecification` objects, you can use their methods to specify the behavior of the `Cursor` objects that correspond to them.

### 9.4 Calculating Extent and Starting and Ending Positions of a Value

To manage the display of the result set retrieved by a `CompoundCursor`, you sometimes need to know the extent of the child `Cursor` components. You might also want to know the position at which the current value of a child `Cursor` starts in the parent `CompoundCursor`. You might want to know the span of the current value of a child `Cursor`. The span is the number of positions of the parent `Cursor` that the current value of the child `Cursor` occupies. You can calculate the span by subtracting the starting position of the value from the ending position and subtracting 1.

Before you can get the extent of a `Cursor` or get the starting or ending positions of a value in the parent `Cursor`, you must specify that you want Oracle OLAP to calculate the extent or those positions. To specify the performance of those calculations, you use methods of the `CursorSpecification` for the `Cursor`.

Example 9-10 specifies calculating the extent of a `Cursor`. The example uses the `CompoundCursorSpecification` from Example 9-9.

Example 9-10 Specifying the Calculation of the Extent of a Cursor

    rootCursorSpec.setExtentCalculationSpecified(true);

You can use methods of a `CursorSpecification` to determine whether the `CursorSpecification` specifies the calculation of the extent of a `Cursor` as in the following example.

    boolean isSet = rootCursorSpec.isExtentCalculationSpecified();

Example 9-11 specifies calculating the starting and ending positions of the current value of a child `Cursor` in the parent `Cursor`. The example uses the `CompoundCursorSpecification` from Example 9-9.

Example 9-11 Specifying the Calculation of Starting and Ending Positions in a Parent

    // Get the List of CursorSpecification objects for the outputs.
    // Iterate through the list, specifying the calculation of the extent
    // for each output CursorSpecification.
    Iterator iterOutputSpecs = rootCursorSpec.getOutputs().iterator();
    while(iterOutputSpecs.hasNext())
    {
      ValueCursorSpecification valCursorSpec =
        (ValueCursorSpecification)iterOutputSpecs.next();
      valCursorSpec.setParentStartCalculationSpecified(true);
      valCursorSpec.setParentEndCalculationSpecified(true);
    }

You can use methods of a `CursorSpecification` to determine whether the `CursorSpecification` specifies the calculation of the starting or ending positions of the current value of a child `Cursor` in a parent `Cursor`, as in the following example.

    Iterator iterOutputSpecs = rootCursorSpec.getOutputs().iterator();
    ValueCursorSpecification valCursorSpec =
      (ValueCursorSpecification)iterOutputSpecs.next();
    while(iterOutputSpecs.hasNext())
    {
      if (valCursorSpec.isParentStartCalculationSpecified())
        // Do something.
      if (valCursorSpec.isParentEndCalculationSpecified())
        // Do something.
      valCursorSpec = (ValueCursorSpecification) iterOutputSpecs.next();
    }

Example 9-12 determines the span of the positions in a parent `CompoundCursor` of the current value of a child `Cursor` for two of the outputs of the `CompoundCursor`. The example uses the `unitForSelections` `Source` from Example 9-8.

The example gets the starting and ending positions of the current values of the time and product selections and then calculates the span of those values in the parent `Cursor`. The parent is the root `CompoundCursor`. The `DataProvider` is `dp`.

Example 9-12 Calculating the Span of the Positions in the Parent of a Value

    Source unitsForSelections = units.join(prodSel)
                                     .join(custSel)
                                     .join(timeSel)
                                     .join(chanSel);
    // Commit the current Transaction (code not shown).

    // Create a CompoundCursorSpecification for unitsForSelections.
    CompoundCursorSpecification rootCursorSpec = (CompoundCursorSpecification)
      dp.createCursorInfoSpecification(unitsForSelections);
    // Get the CursorSpecification objects for the outputs.
    List outputSpecs = rootCursorSpec.getOutputs();
    ValueCursorSpecification timeSelValCSpec =
      (ValueCursorSpecification)outputSpecs.get(1); // Output for time.
    ValueCursorSpecification prodSelValCSpec =
     (ValueCursorSpecification)outputSpecs.get(3);  // Output for product.

    // Specify the calculation of the starting and ending positions.
    timeSelValCSpec.setParentStartCalculationSpecified(true);
    timeSelValCSpec.setParentEndCalculationSpecified(true);
    prodSelValCSpec.setParentStartCalculationSpecified(true);
    prodSelValCSpec.setParentEndCalculationSpecified(true);

    // Create the CursorManager and the Cursor.
    CursorManager cursorMngr =
      dp.createCursorManager(unitsForSelections, 100, rootCursorSpec);
    CompoundCursor rootCursor = (CompoundCursor) cursorMngr.createCursor();

    // Get the child Cursor objects.
    ValueCursor baseValCursor = cursor.getValueCursor();
    List outputs = rootCursor.getOutputs();
    ValueCursor chanSelVals = (ValueCursor) outputs.get(0);
    ValueCursor timeSelVals = (ValueCursor) outputs.get(1);
    ValueCursor custSelVals = (ValueCursor) outputs.get(2);
    ValueCursor prodSelVals = (ValueCursor) outputs.get(3);

    // Set the position of the root CompoundCursor.
    rootCursor.setPosition(15);

    // Get the values at the current position and determine the span
    // of the values of the time and product outputs.
    print(chanSelVals.getCurrentValue() + ", ");
    print(timeSelVals.getCurrentValue() + ",\n  ");
    print(custSelVals.getCurrentValue() + ", ");
    print(prodSelVals.getCurrentValue() + ", ");
    print(baseValCursor.getCurrentValue());
    println();

    // Determine the span of the values of the two fastest-varying outputs.
    long span;
    span = (prodSelVals.getParentEnd() - prodSelVals.getParentStart()) +1);
    println("\nThe span of " + prodSelVals.getCurrentValue() +
            " at the current position is " + span + ".")
    span = (timeSelVals.getParentEnd() - timeSelVals.getParentStart()) +1);
    println("The span of " + timeSelVals.getCurrentValue() +
            " at the current position is " + span + ".")
    cursorMngr.close();

This example displays the following text.

    CHANNEL_PRIMARY::CHANNEL::DIR, CALENDAR_YEAR::MONTH::2000.02,
      SHIPMENTS::SHIP_TO::COMP SERV TOK, PRODUCT_PRIMARY::ITEM::ENVY STD, 6.0

    The span of PRODUCT_PRIMARY::ITEM::ENVY STD at the current position is 1.
    The span of CALENDAR_YEAR::MONTH::2000.02 at the current position is 9.

### 9.5 Specifying a Fetch Size

The number of elements of a `Cursor` that Oracle OLAP sends to the client application during one fetch operation depends on the fetch size specified for that `Cursor`. The default fetch size is 100. To change the fetch size, you can set the fetch size on the root `Cursor` for a `Source`.

Example 9-13 Specifying a Fetch Size

This example gets the default fetch size from the `CompoundCursorSpecification` from Example 9-9. The example creates a `Cursor` and sets a different fetch size on it, and then gets the fetch size for the `Cursor`. The `DataProvider` is `dp`.

    println("The default fetch size is "
             + rootCursorSpec.getDefaultFetchSize() + ".");
    Source source = rootCursorSpec.getSource();
    CursorManager cursorMngr = dp.createCursorManager(source);
    Cursor rootCursor = cursorMngr.createCursor();
    rootCursor.setFetchSize(10);
    println("The fetch size is now " + rootCursor.getFetchSize()) + ".";

The example displays the following text.

    The default fetch size is 100.
    The fetch size is now 10.
