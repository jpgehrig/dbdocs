This chapter describes the Oracle OLAP Java API `Transaction` and `TransactionProvider` interfaces and describes how you use implementations of those interfaces in an application. You get a `TransactionProvider` from a `DataProvider`. You use the `commitCurrentTransaction` method of the `TransactionProvider` to save a metadata object in persistent storage in the database. You also use that method after creating a derived `Source` and before creating a `Cursor` for the `Source`. For examples of committing a `Transaction` after creating a metadata object, see [Creating Metadata and Analytic Workspaces](creating-metadata-and-analytic-workspaces.md).

This chapter includes the following topics:

- About Creating a Metadata Object or a Query in a Transaction

- Using TransactionProvider Objects

### 7.1 About Creating a Metadata Object or a Query in a Transaction

The Oracle OLAP Java API is transactional. Creating metadata objects or `Source` objects for a query occurs in the context of a `Transaction`. A `TransactionProvider` provides `Transaction` objects to the application and commits or discards those `Transaction` objects.

The `TransactionProvider` ensures the following:

- A `Transaction` is isolated from other `Transaction` objects. Operations performed in a `Transaction` are not visible in, and do not affect, other `Transaction` objects.

- If an operation in a `Transaction` fails, then the effects of the operation are undone (the `Transaction` is rolled back).

- The effects of a completed `Transaction` persist.

When you create a `DataProvider` and `UserSession`, the session does not at first have a `Transaction`. The first `Transaction` in a session is a root `Transaction`. You can explicitly create a root `Transaction` by calling the `createRootTransaction` method of the `TransactionProvider`. If you do not explicitly created one, then Oracle OLAP automatically creates a root `Transaction` the first time that you create or modify an `MdmObject` or a derived `Source`. To make permanent the changes to an `MdmObject`, you must commit the root `Transaction` in which you made the changes.

A single-user application does not need to explicitly create a root `Transaction`. The ability to create multiple root `Transaction` objects is provided for use by multithreaded, middle-tier applications. If your application uses multiple root `Transaction` objects, the changes that the application makes in one root `Transaction` can be overwritten by changes the application makes in another root `Transaction`. The changes that occur in the last root `Transaction` that the application commits are the changes that persist.

When you or Oracle OLAP creates the initial root `Transaction`, it is the current `Transaction`. If you create another root `Transaction`, it becomes the current `Transaction`.

Oracle OLAP creates other `Transaction` objects as you create `Source` objects or child `Transaction` objects under a root `Transaction`. You must commit the root `Transaction` for the Oracle Database to add to persistent storage any metadata objects that you have created in any `Transaction` in the session.

When you create a derived `Source` by calling a method of another `Source`, the derived `Source` is created in the context of the current `Transaction`. The `Source` is active in the `Transaction` in which you create it or in a child `Transaction` of that `Transaction`.

You get or set the current `Transaction`, or begin a child `Transaction`, by calling methods of a `TransactionProvider`. In a child `Transaction` you can alter a query, for example by changing the selection of dimension elements or by performing a different mathematical or analytical operation on the data, which changes the state of a `Template` that you created in the parent `Transaction`. By displaying the data specified by the `Source` produced by the `Template` in the parent `Transaction` and also displaying the data specified by the `Source` produced by the `Template` in the child `Transaction`, you can provide the end user of your application with the means of easily altering a query and viewing the results of different operations on the same set of data, or the same operations on different sets of data.

#### 7.1.1 Types of Transaction Objects

The OLAP Java API has the following two types of `Transaction` objects:

- A read `Transaction`. Initially, the current `Transaction` is a read `Transaction`. A read `Transaction` is required for creating a `Cursor` to fetch data from Oracle OLAP. For more information on `Cursor` objects, see [Retrieving Query Results](retrieving-query-results.md).

- A write `Transaction`. A write `Transaction` is required for creating a derived `Source` or for changing the state of a `Template`. For more information on creating a derived `Source`, see [Understanding Source Objects](understanding-source-objects.md). For information on `Template` objects, see [Creating Dynamic Queries](creating-dynamic-queries.md).

In the initial read `Transaction`, if you create a derived `Source` or if you change the state of a `Template` object, then a child write `Transaction` is automatically generated. That child `Transaction` becomes the current `Transaction`.

If you then create another derived `Source` or change the `Template` state again, then that operation occurs in the same write `Transaction`. You can create any number of derived `Source` objects, or make any number of `Template` state changes, in that same write `Transaction`. You can use those `Source` objects, or the `Source` produced by the `Template`, to define a complex query.

Before you can create a `Cursor` to fetch the result set specified by a derived `Source`, you must move the `Source` from the child write `Transaction` into the parent read `Transaction`. To do so, you commit the `Transaction`.

#### 7.1.2 Committing a Transaction

To move a `Source` that you created in a child `Transaction` into the parent read `Transaction`, call the `commitCurrentTransaction` method of the `TransactionProvider`. When you commit a child write `Transaction`, a `Source` you created in the child `Transaction` moves into the parent read `Transaction`. The child `Transaction` disappears and the parent `Transaction` becomes the current `Transaction`. The `Source` is active in the current read `Transaction` and you can therefore create a `Cursor` for it.

Example 7-1 Committing the Current Transaction

In this example, `commit()` is a method that commits the current `Transaction`. In the example, `dp` is the `DataProvider`.

    private void commit()
    {
      try
      {
        (dp.getTransactionProvider()).commitCurrentTransaction();
      }
      catch (Exception ex)
      {
        System.out.println("Could not commit the Transaction. " + ex);
      }
    }

#### 7.1.3 About Transaction and Template Objects

Getting and setting the current `Transaction`, beginning a child `Transaction`, and rolling back a `Transaction` are operations that you use to allow an end user to make different selections starting from a given state of a dynamic query.

To present the end user with alternatives based on the same initial query, you do the following:

1.  Create a `Template` in a parent `Transaction` and set the initial state for the `Template`.

2.  Get the `Source` produced by the `Template`, create a `Cursor` to retrieve the result set, get the values from the `Cursor`, and then display the results to the end user.

3.  Begin a child `Transaction` and modify the state of the `Template`.

4.  Get the `Source` produced by the `Template` in the child `Transaction`, create a `Cursor`, get the values, and display them.

You can then replace the first `Template` state with the second one or discard the second one and retain the first.

#### 7.1.4 Beginning a Child Transaction

To begin a child read `Transaction`, call the `beginSubtransaction` method of the `TransactionProvider` you are using. In the child read `Transaction`, if you change the state of a `Template`, then a child write `Transaction` begins automatically. The write `Transaction` is a child of the child read `Transaction`.

To get the data specified by the `Source` produced by the `Template`, you commit the write `Transaction` into the parent read `Transaction`. You can then create a `Cursor` to fetch the data. The changed state of the `Template` is not visible in the original parent. The changed state does not become visible in the parent until you commit the child read `Transaction` into the parent read `Transaction`.

After beginning a child read `Transaction`, you can begin a child read `Transaction` of that child, or a grandchild of the initial parent `Transaction`. For an example of creating child and grandchild `Transaction` objects, see Example 7-3.

#### 7.1.5 About Rolling Back a Transaction

You roll back, or undo, a `Transaction` by calling the `rollbackCurrentTransaction` method of the `TransactionProvider` you are using. Rolling back a `Transaction` discards any changes that you made during that `Transaction` and makes the `Transaction` disappear.

Before rolling back a `Transaction`, you must close any `CursorManager` objects you created in that `Transaction`. After rolling back a `Transaction`, any `Source` objects that you created or `Template` state changes that you made in the `Transaction` are no longer valid. Any `Cursor` objects you created for those `Source` objects are also invalid.

Once you roll back a `Transaction`, you cannot commit that `Transaction`. Likewise, once you commit a `Transaction`, you cannot roll it back.

Example 7-2 Rolling Back a Transaction

This example uses the `TopBottomTemplate` and `SingleSelectionTemplate` classes that are described in [Creating Dynamic Queries](creating-dynamic-queries.md). In creating the `TopBottomTemplate` and `SingleSelectionTemplate` objects, the example uses the same code that appears in [Example 10-4](creating-dynamic-queries.md). This example does not show that code. It sets the state of the `TopBottomTemplate`. It begins a child `Transaction` that sets a different state for the `TopBottomTemplate` and then rolls back the child `Transaction`. The `println` method displays text through a `CursorPrintWriter` object and the `getContext` method gets a `Context11g` object that has methods that create `Cursor` objects and display their values through the `CursorPrintWriter`. The `CursorPrintWriter` and `Context11g` classes are used by the example programs in this documentation.

    // The current Transaction is a read Transaction, t1.
    // Create a TopBottomTemplate using a hierarchy of the PRODUCT_AWJ dimension
    // as the base and dp as the DataProvider.
    TopBottomTemplate topNBottom = new TopBottomTemplate(prodHier, dp);

    // Changing the state of a Template requires a write Transaction, so a
    // write child Transaction, t2, is automatically started.
    topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_TOP);
    topNBottom.setN(10);
    topNBottom.setCriterion(singleSelections.getSource());

    // Get the TransactionProvider and commit the Transaction t2.
    TransactionProvider tp = dp.getTransactionProvider();
    try
    {
      tp.commitCurrentTransaction();           // t2 disappears
    }
    catch(Exception e)
    {
      println("Cannot commit the Transaction. " + e);
    }

    // The current Transaction is now t1.
    // Get the dynamic Source produced by the TopBottomTemplate.
    Source result = topNBottom.getSource();

    // Create a Cursor and display the results
    println("\nThe current state of the TopBottomTemplate" +
            "\nproduces the following values:\n");
    getContext().displayTopBottomResult(result);

    // Start a child Transaction, t3. It is a read Transaction.
    tp.beginSubtransaction();          // t3 is the current Transaction

    // Change the state of topNBottom. Changing the state requires a
    // write Transaction so Transaction t4 starts automatically.
    topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_BOTTOM);
    topNBottom.setN(15);

    // Commit the Transaction.
    try
    {
      tp.commitCurrentTransaction();           // t4 disappears
    }
    catch(Exception e)
    {
      println("Cannot commit the Transaction. " + e);
    }

    // Create a Cursor and display the results. // t3 is the current Transaction
    println("\nIn the child Transaction, the state of the" +
            "\nTopBottomTemplate produces the following values:\n");
    getContext().displayTopBottomResult(result);
    // The displayTopBottomResult method closes the CursorManager for the
    // Cursor created in t3.

    // Undo t3, which discards the state of topNBottom that was set in t4.
    tp.rollbackCurrentTransaction();        // t3 disappears

    // Transaction t1 is now the current Transaction and the state of
    // topNBottom is the one defined in t2.

    // To show the current state of the TopNBottom template Source, commit
    // the Transaction, create a Cursor, and display the Cursor values.
    try
    {
      tp.commitCurrentTransaction();
    }
    catch(Exception e)
    {
      println("Cannot commit the Transaction. " + e);
    }

    println("\nAfter rolling back the child Transaction, the state of"
            + "\nthe TopBottomTemplate produces the following values:\n");
    getContext().displayTopBottomResult(result);

The example produces the following output.

    The current state of the TopBottomTemplate
    produces the following values:

     1. PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
     2. PRODUCT_PRIMARY::CLASS::SFT
     3. PRODUCT_PRIMARY::FAMILY::ACC
     4. PRODUCT_PRIMARY::CLASS::HRD
     5. PRODUCT_PRIMARY::FAMILY::MOD
     6. PRODUCT_PRIMARY::FAMILY::OS
     7. PRODUCT_PRIMARY::FAMILY::DISK
     8. PRODUCT_PRIMARY::ITEM::MOUSE PAD
     9. PRODUCT_PRIMARY::ITEM::OS 1 USER
    10. PRODUCT_PRIMARY::ITEM::DLX MOUSE

    In the child Transaction, the state of the
    TopBottomTemplate produces the following values:

     1. PRODUCT_PRIMARY::ITEM::EXT CD ROM
     2. PRODUCT_PRIMARY::ITEM::OS DOC ITA
     3. PRODUCT_PRIMARY::ITEM::OS DOC SPA
     4. PRODUCT_PRIMARY::ITEM::INT CD USB
     5. PRODUCT_PRIMARY::ITEM::ENVY EXT KBD
     6. PRODUCT_PRIMARY::ITEM::19 SVGA
     7. PRODUCT_PRIMARY::ITEM::OS DOC FRE
     8. PRODUCT_PRIMARY::ITEM::OS DOC GER
     9. PRODUCT_PRIMARY::ITEM::ENVY ABM
    10. PRODUCT_PRIMARY::ITEM::INT CD ROM
    11. PRODUCT_PRIMARY::ITEM::ENVY EXE
    12. PRODUCT_PRIMARY::ITEM::OS DOC KAN
    13. PRODUCT_PRIMARY::ITEM::ENVY STD
    14. PRODUCT_PRIMARY::ITEM::1GB USB DRV
    15. PRODUCT_PRIMARY::ITEM::SENT MM

    After rolling back the child Transaction, the state of
    the TopBottomTemplate produces the following values:

     1. PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
     2. PRODUCT_PRIMARY::CLASS::SFT
     3. PRODUCT_PRIMARY::FAMILY::ACC
     4. PRODUCT_PRIMARY::CLASS::HRD
     5. PRODUCT_PRIMARY::FAMILY::MOD
     6. PRODUCT_PRIMARY::FAMILY::OS
     7. PRODUCT_PRIMARY::FAMILY::DISK
     8. PRODUCT_PRIMARY::ITEM::MOUSE PAD
     9. PRODUCT_PRIMARY::ITEM::OS 1 USER
    10. PRODUCT_PRIMARY::ITEM::DLX MOUSE

#### 7.1.6 Getting and Setting the Current Transaction

You get the current `Transaction` by calling the `getCurrentTransaction` method of the `TransactionProvider` you are using, as in the following example.

    Transaction t1 = tp.getCurrentTransaction();

To make a previously saved `Transaction` the current `Transaction`, you call the `setCurrentTransaction` method of the `TransactionProvider`, as in the following example.

    tp.setCurrentTransaction(t1);

### 7.2 Using TransactionProvider Objects

In the Oracle OLAP Java API, a `DataProvider` provides an implementation of the `TransactionProvider` interface. The `TransactionProvider` provides `Transaction` objects to your application.

As described in "Committing a Transaction", you use the `commitCurrentTransaction` method to make a derived `Source` that you created in a child write `Transaction` visible in the parent read `Transaction`. You can then create a `Cursor` for that `Source`.

If you are using `Template` objects in your application, then you might also use the other methods of `TransactionProvider` to do the following:

- Begin a child `Transaction`.

- Get the current `Transaction` so you can save it.

- Set the current `Transaction` to a previously saved one.

- Rollback, or undo, the current `Transaction`, which discards any changes made in the `Transaction`. Once a `Transaction` has been rolled back, it is invalid and cannot be committed. Once a `Transaction` has been committed, it cannot be rolled back. If you created a `Cursor` for a `Source` in a `Transaction`, then you must close the `CursorManager` before rolling back the `Transaction`.

Example 7-3 demonstrates the use of `Transaction` objects to modify dynamic queries. Like Example 7-2, this example uses the same code to create `TopBottomTemplate` and `SingleSelectionTemplate` objects as does [Example 10-4](creating-dynamic-queries.md). This example does not show that code.

To help track the `Transaction` objects, this example saves the different `Transaction` objects with calls to the `getCurrentTransaction` method. In the example, the `tp` object is the `TransactionProvider`. The `println` method displays text through a `CursorPrintWriter` and the `getContext` method gets a `Context11g` object that has methods that create `Cursor` objects and display their values through the `CursorPrintWriter`. The `commit` method is the method from Example 7-1.

Example 7-3 Using Child Transaction Objects

    // The parent Transaction is the current Transaction at this point.
    // Save the parent read Transaction as parentT1.
    Transaction parentT1 = tp.getCurrentTransaction();

    // Get the dynamic Source produced by the TopBottomTemplate.
    Source result = topNBottom.getSource();

    // Create a Cursor and display the results.
    println("\nThe current state of the TopBottomTemplate" +
            "\nproduces the following values:\n");
    getContext().displayTopBottomResult(result);

    // Begin a child Transaction of parentT1.
    tp.beginSubtransaction();  // This is a read Transaction.

    // Save the child read Transaction as childT2.
    Transaction childT2 = tp.getCurrentTransaction();

    // Change the state of the TopBottomTemplate. This starts a
    // write Transaction, a child of the read Transaction childT2.
    topNBottom.setN(12);
    topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_BOTTOM);

    // Save the child write Transaction as writeT3.
    Transaction writeT3 = tp.getCurrentTransaction();

    // Commit the write Transaction writeT3.
    commit();

    // The commit moves the changes made in writeT3 into its parent,
    // the read Transaction childT2. The writeT3 Transaction
    // disappears. The current Transaction is now childT2
    // again but the state of the TopBottomTemplate has changed.

    // Create a Cursor and display the results of the changes to the
    // TopBottomTemplate that are visible in childT2.
    try
    {
      println("\nIn the child Transaction, the state of the" +
              "\nTopBottomTemplate produces the following values:\n");

      getContext().displayTopBottomResult(result);
    }
    catch(Exception e)
    {
      println("Cannot display the results of the query. " + e);
    }

    // Begin a grandchild Transaction of the initial parent.
    tp.beginSubtransaction();  // This is a read Transaction.

    // Save the grandchild read Transaction as grandchildT4.
    Transaction grandchildT4 = tp.getCurrentTransaction();

    // Change the state of the TopBottomTemplate. This starts another
    // write Transaction, a child of grandchildT4.
    topNBottom.setTopBottomType(TopBottomTemplate.TOP_BOTTOM_TYPE_TOP);

    // Save the write Transaction as writeT5.
    Transaction writeT5 = tp.getCurrentTransaction();

    // Commit writeT5.
    commit();

    // Transaction grandchildT4 is now the current Transaction and the
    // changes made to the TopBottomTemplate state are visible.

    // Create a Cursor and display the results visible in grandchildT4.
    try
    {
      println("\nIn the grandchild Transaction, the state of the" +
              "\nTopBottomTemplate produces the following values:\n");
      getContext().displayTopBottomResult(result);
    }
    catch(Exception e)
    {
      println(""Cannot display the results of the query. " + e);
    }

    // Commit the grandchild into the child.
    commit();

    // Transaction childT2 is now the current Transaction.
    // Instead of preparing and committing the grandchild Transaction,
    // you could rollback the Transaction, as in the following
    // method call:
    //   rollbackCurrentTransaction();
    // If you roll back the grandchild Transaction, then the changes
    // you made to the TopBottomTemplate state in the grandchild
    // are discarded and childT2 is the current Transaction.

    // Commit the child into the parent.
    commit();

    // Transaction parentT1 is now the current Transaction. Again,
    // you can roll back the childT2 Transaction instead of committing it.
    // If you do so, then the changes that you made in childT2 are discarded.
    // The current Transaction is be parentT1, which has the original state
    // of the TopBottomTemplate, without any of the changes made in the
    // grandchild or the child transactions.

Example 7-3 produces the following output.

    The current state of the TopBottomTemplate
    produces the following values:

     1. PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
     2. PRODUCT_PRIMARY::CLASS::SFT
     3. PRODUCT_PRIMARY::FAMILY::ACC
     4. PRODUCT_PRIMARY::CLASS::HRD
     5. PRODUCT_PRIMARY::FAMILY::MOD
     6. PRODUCT_PRIMARY::FAMILY::OS
     7. PRODUCT_PRIMARY::FAMILY::DISK
     8. PRODUCT_PRIMARY::ITEM::MOUSE PAD
     9. PRODUCT_PRIMARY::ITEM::OS 1 USER
    10. PRODUCT_PRIMARY::ITEM::DLX MOUSE

    In the child Transaction, the state of the
    TopBottomTemplate produces the following values:

     1. PRODUCT_PRIMARY::ITEM::EXT CD ROM
     2. PRODUCT_PRIMARY::ITEM::OS DOC ITA
     3. PRODUCT_PRIMARY::ITEM::OS DOC SPA
     4. PRODUCT_PRIMARY::ITEM::INT CD USB
     5. PRODUCT_PRIMARY::ITEM::ENVY EXT KBD
     6. PRODUCT_PRIMARY::ITEM::19 SVGA
     7. PRODUCT_PRIMARY::ITEM::OS DOC FRE
     8. PRODUCT_PRIMARY::ITEM::OS DOC GER
     9. PRODUCT_PRIMARY::ITEM::ENVY ABM
    10. PRODUCT_PRIMARY::ITEM::INT CD ROM
    11. PRODUCT_PRIMARY::ITEM::ENVY EXE
    12. PRODUCT_PRIMARY::ITEM::OS DOC KAN

    In the grandchild Transaction, the state of the
    TopBottomTemplate produces the following values:

     1. PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
     2. PRODUCT_PRIMARY::CLASS::SFT
     3. PRODUCT_PRIMARY::FAMILY::ACC
     4. PRODUCT_PRIMARY::CLASS::HRD
     5. PRODUCT_PRIMARY::FAMILY::MOD
     6. PRODUCT_PRIMARY::FAMILY::OS
     7. PRODUCT_PRIMARY::FAMILY::DISK
     8. PRODUCT_PRIMARY::ITEM::MOUSE PAD
     9. PRODUCT_PRIMARY::ITEM::OS 1 USER
    10. PRODUCT_PRIMARY::ITEM::DLX MOUSE
    11. PRODUCT_PRIMARY::ITEM::LT CASE
    12. PRODUCT_PRIMARY::ITEM::56KPS MODEM
