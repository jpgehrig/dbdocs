## 14  Advanced Design Considerations

There are design considerations for more advanced application development issues.

Topicss:

- Opening Persistent LOBs with the OPEN and CLOSE Interfaces

- Read-Consistent Locators

- LOB Locators and Transaction Boundaries

- LOBs in the Object Cache

- Terabyte-Size LOB Support

- Guidelines for Creating Gigabyte LOBs

<!-- -->

- Opening Persistent LOBs with the OPEN and CLOSE Interfaces
- Read-Consistent Locators
- LOB Locators and Transaction Boundaries
- LOBs in the Object Cache
- Terabyte-Size LOB Support
- Guidelines for Creating Gigabyte LOBs

**Parent topic:** [Application Design with LOBs](application-design-with-LOBs.md)

### 14.1 Opening Persistent LOBs with the OPEN and CLOSE Interfaces

The `OPEN` and `CLOSE `interfaces enable you to explicitly open a persistent LOB instance.

When you open a LOB instance with the `OPEN` interface, the instance remains open until you explicitly close the LOB using the `CLOSE` interface. The `ISOPEN` interface enables you to determine whether a persistent LOB is open.

Note that the open state of a LOB is associated with the LOB instance, not the LOB locator. The locator does not save any information indicating whether the LOB instance that it points to is open.

**See Also:**

"[LOB Open and Close Operations0.](working-with-LOBs.md)".

Topics:

- Index Performance Benefits of Explicitly Opening a LOB

- Closing Explicitly Open LOB Instances

<!-- -->

- Index Performance Benefits of Explicitly Opening a LOB
- Closing Explicitly Open LOB Instances

**Parent topic:** Advanced Design Considerations

#### 14.1.1 Index Performance Benefits of Explicitly Opening a LOB

Explicitly opening a LOB instance can benefit performance of a persistent LOB in an indexed column.

If you do not explicitly open the LOB instance, then every modification to the LOB implicitly opens and closes the LOB instance. Any triggers on a domain index are fired each time the LOB is closed. Note that in this case, any domain indexes on the LOB are updated as soon as any modification to the LOB instance is made; the domain index is always valid and can be used at any time.

When you explicitly open a LOB instance, index triggers do not fire until you explicitly close the LOB. Using this technique can increase performance on index columns by eliminating unneeded indexing events until you explicitly close the LOB. Note that any index on the LOB column is not valid until you explicitly close the LOB.

**Parent topic:** Opening Persistent LOBs with the OPEN and CLOSE Interfaces

#### 14.1.2 Closing Explicitly Open LOB Instances

If you explicitly open a LOB instance, then you must close the LOB before you commit the transaction.

Committing a transaction on the open LOB instance causes an error. When this error occurs, the LOB instance is closed implicitly, any modifications to the LOB instance are saved, and the transaction is committed, but any indexes on the LOB column are not updated. In this situation, you must rebuild your indexes on the LOB column.

If you subsequently rollback the transaction, then the LOB instance is rolled back to its previous state, but the LOB instance is no longer explicitly open.

You must close any LOB instance that you explicitly open:

- Between DML statements that start a transaction, including `SELECT` ... `FOR` `UPDATE` and `COMMIT`

- Within an autonomous transaction block

- Before the end of a session (when there is no transaction involved)

  If you do not explicitly close the LOB instance, then it is implicitly closed at the end of the session and no index triggers are fired.

Keep track of the open or closed state of LOBs that you explicitly open. The following actions cause an error:

- Explicitly opening a LOB instance that has been explicitly open earlier.

- Explicitly closing a LOB instance that is has been explicitly closed earlier.

This occurs whether you access the LOB instance using the same locator or different locators.

**Parent topic:** Opening Persistent LOBs with the OPEN and CLOSE Interfaces

### 14.2 Read-Consistent Locators

Oracle Database provides the same read consistency mechanisms for LOBs as for all other database reads and updates of scalar quantities.

Read consistency has some special applications to LOB locators that you must understand. The following sections discuss read consistency and include examples which should be looked at in relationship to each other.

**See Also:**

- [Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md) for general information about read consistency

- [Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md)

Topics:

- A Selected Locator Becomes a Read-Consistent Locator

- Example of Updating LOBs and Read-Consistency

- Example of Updating LOBs Through Updated Locators

- Example of Updating a LOB Using SQL DML and DBMS_LOB

- Example of Using One Locator to Update the Same LOB Value

- Example of Updating a LOB with a PL/SQL (DBMS_LOB) Bind Variable

<!-- -->

- A Selected Locator Becomes a Read-Consistent Locator
- Example of Updating LOBs and Read-Consistency
- Example of Updating LOBs Through Updated Locators
- Example of Updating a LOB Using SQL DML and DBMS_LOB
- Example of Using One Locator to Update the Same LOB Value
- Example of Updating a LOB with a PL/SQL (DBMS_LOB) Bind Variable
- Example of Deleting a LOB Using Locator
  Learn about deleting a LOB with a PL/SQL bind variable in this section.

**Parent topic:** Advanced Design Considerations

#### 14.2.1 A Selected Locator Becomes a Read-Consistent Locator

A selected locator, regardless of the existence of the `FOR` `UPDATE` clause, becomes a read-consistent locator, and remains a read-consistent locator until the LOB value is updated through that locator.

A read-consistent locator contains the snapshot environment as of the point in time of the `SELECT` operation.

This has some complex implications. Suppose you have created a read-consistent locator (`L1`) by way of a `SELECT` operation. In reading the value of the persistent LOB through `L1`, note the following:

- The LOB is read as of the point in time of the `SELECT` statement even if the `SELECT` statement includes a `FOR` `UPDATE`.

- If the LOB value is updated through a different locator (`L2`) in the same transaction, then `L1` does not see the `L2` updates.

- `L1` does not see committed updates made to the LOB through another transaction.

- If the read-consistent locator `L1` is copied to another locator `L2` (for example, by a PL/SQL assignment of two locator variables — `L2:= L1`), then `L2` becomes a read-consistent locator along with `L1` and any data read is read as of the point in time of the `SELECT` for `L1`.

You can use the existence of multiple locators to access different transformations of the LOB value. However, in doing so, you must keep track of the different values accessed by different locators.

**Parent topic:** Read-Consistent Locators

#### 14.2.2 Example of Updating LOBs and Read-Consistency

Read-consistent locators provide the same LOB value regardless of when the `SELECT` occurs.

The following example demonstrates the relationship between read-consistency and updating in a simple example. Using the `print_media` table described in "[Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md)" and PL/SQL, three `CLOB` instances are created as potential locators: `clob_selected`, `clob_update`, and `clob_copied`.

Observe these progressions in the code, from times `t1` through `t6`:

- At the time of the first `SELECT` `INTO` (at `t1`), the value in `ad_sourcetext`is associated with the locator `clob_selected`.

- In the second operation (at `t2`), the value in `ad_sourcetext`is associated with the locator `clob_updated`. Because there has been no change in the value of `ad_sourcetext`between `t1` and `t2`, both `clob_selected` and `clob_updated` are read-consistent locators that effectively have the same value even though they reflect snapshots taken at different moments in time.

- The third operation (at `t3`) copies the value in `clob_selected` to `clob_copied`. At this juncture, all three locators see the same value. The example demonstrates this with a series of `DBMS_LOB`.`READ()` calls.

- At time `t4`, the program uses `DBMS_LOB`.`WRITE()` to alter the value in `clob_updated`, and a `DBMS_LOB`.`READ()` reveals a new value.

- However, a `DBMS_LOB`.`READ()` of the value through `clob_selected` (at `t5`) reveals that it is a read-consistent locator, continuing to refer to the same value as of the time of its `SELECT`.

- Likewise, a `DBMS_LOB`.`READ()` of the value through `clob_copied` (at `t6`) reveals that it is a read-consistent locator, continuing to refer to the same value as `clob_selected`.

Example 14-1

    INSERT INTO PRINT_MEDIA VALUES (2056, 20020, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    COMMIT;

    DECLARE
      num_var           INTEGER;
      clob_selected     CLOB;
      clob_updated      CLOB;
      clob_copied       CLOB;
      read_amount       INTEGER;
      read_offset       INTEGER;
      write_amount      INTEGER;
      write_offset      INTEGER;
      buffer            VARCHAR2(20);

    BEGIN
      -- At time t1:
      SELECT ad_sourcetext INTO clob_selected
         FROM Print_media
         WHERE ad_id = 20020;

      -- At time t2:
      SELECT ad_sourcetext INTO clob_updated
         FROM Print_media
         WHERE ad_id = 20020
         FOR UPDATE;

      -- At time t3:
      clob_copied := clob_selected;
      -- After the assignment, both the clob_copied and the
      -- clob_selected have the same snapshot as of the point in time
      -- of the SELECT into clob_selected

      -- Reading from the clob_selected and the clob_copied does
      -- return the same LOB value. clob_updated also sees the same
      -- LOB value as of its select:
      read_amount := 10;
      read_offset := 1;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_selected value: ' || buffer);
      -- Produces the output 'abcd'

      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcd'

      read_amount := 10;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t4:
      write_amount := 3;
      write_offset := 5;
      buffer := 'efg';
      dbms_lob.write(clob_updated, write_amount, write_offset, buffer);

      read_amount := 10;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcdefg'

      -- At time t5:
      read_amount := 10;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_selected value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t6:
      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcd'
    END;
    /

**Parent topic:** Read-Consistent Locators

#### 14.2.3 Example of Updating LOBs Through Updated Locators

When you update the value of the persistent LOB through the LOB locator (`L1`), `L1` is updated to contain the current snapshot environment.

This snapshot is as of the time after the operation was completed on the LOB value through locator `L1`. `L1` is then termed an updated locator. This operation enables you tosee your own changes to the LOB value on the next read through the same locator, `L1`.

**Note:**

The snapshot environment in the locator is not updated if the locator is used to merely read the LOB value. It is only updated when you modify the LOB value through the locator using the PL/SQL `DBMS_LOB` package or the OCI LOB APIs.

Any committed updates made by a different transaction are seen by L1 only if your transaction is a read-committed transaction and if you use L1 to update the LOB value after the other transaction committed.

**Note:**

When you update a persistent LOB value, the modification is always made to the most current LOB value.

Updating the value of the persistent LOB through any of the available methods, such as OCI LOB APIs or PL/SQL `DBMS_LOB` package, updates the LOB value and then reselects the locator that refers to the new LOB value.

**Note:**

Once you have selected out a LOB locator by whatever means, you can read from the locator but not write into it.

Note that updating the LOB value through SQL is merely an `UPDATE` statement. It is up to you to do the reselect of the LOB locator or use the `RETURNING` clause in the `UPDATE` statement so that the locator can see the changes made by the `UPDATE` statement. Unless you reselect the LOB locator or use the `RETURNING` clause, you may think you are reading the latest value when this is not the case. For this reason you should avoid mixing SQL DML with `OCI` and `DBMS_LOB` piecewise operations.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/overview.md)

**Parent topic:** Read-Consistent Locators

#### 14.2.4 Example of Updating a LOB Using SQL DML and DBMS_LOB

Using the `Print_media` table in the following example, a `CLOB` locator is created as `clob_selected`. Note the following progressions in the example, from times `t1` through `t3`:

- At the time of the first `SELECT` `INTO` (at `t1`), the value in `ad_sourcetext` is associated with the locator `clob_selected`.

- In the second operation (at `t2`), the value in `ad_sourcetext` is modified through the `SQL` `UPDATE` statement, without affecting the `clob_selected` locator. The locator still sees the value of the LOB as of the point in time of the original `SELECT`. In other words, the locator does not see the update made using the SQL `UPDATE` statement. This is illustrated by the subsequent `DBMS_LOB`.`READ()` call.

- The third operation (at `t3`) re-selects the LOB value into the locator `clob_selected`. The locator is thus updated with the latest snapshot environment which allows the locator to see the change made by the previous SQL `UPDATE` statement. Therefore, in the next `DBMS_LOB`.`READ()`, an error is returned because the LOB value is empty, that is, it does not contain any data.

<!-- -->

    INSERT INTO Print_media VALUES (3247, 20010, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    COMMIT;

    DECLARE
      num_var           INTEGER;
      clob_selected     CLOB;
      read_amount       INTEGER;
      read_offset       INTEGER;
      buffer            VARCHAR2(20);

    BEGIN

      -- At time t1:
      SELECT ad_sourcetext INTO clob_selected
      FROM Print_media
      WHERE ad_id = 20010;

      read_amount := 10;
      read_offset := 1;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_selected value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t2:
      UPDATE Print_media SET ad_sourcetext = empty_clob()
          WHERE ad_id = 20010;
      -- although the most current LOB value is now empty,
      -- clob_selected still sees the LOB value as of the point
      -- in time of the SELECT

      read_amount := 10;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_selected value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t3:
      SELECT ad_sourcetext INTO clob_selected FROM Print_media WHERE
           ad_id = 20010;
      -- the SELECT allows clob_selected to see the most current
      -- LOB value

      read_amount := 10;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      -- ERROR: ORA-01403: no data found
    END;
    /

**Parent topic:** Read-Consistent Locators

#### 14.2.5 Example of Using One Locator to Update the Same LOB Value

**Note:**

Avoid updating the same LOB with different locators. You may avoid many pitfalls if you use only one locator to update a given LOB value.

In the following example, using table `Print_media`, two `CLOB`s are created as potential locators: clob_updated and clob_copied.

Note these progressions in the example at times t1 through t5:

- At the time of the first `SELECT` `INTO` (at `t1`), the value in `ad_sourcetext` is associated with the locator `clob_updated`.

- The second operation (at time `t2`) copies the value in `clob_updated` to `clob_copied`. At this time, both locators see the same value. The example demonstrates this with a series of `DBMS_LOB`.`READ()` calls.

- At time `t3`, the program uses `DBMS_LOB`.`WRITE()` to alter the value in `clob_updated`, and a `DBMS_LOB.READ()` reveals a new value.

- However, a `DBMS_LOB`.`READ()` of the value through `clob_copied` (at time` t4`) reveals that it still sees the value of the LOB as of the point in time of the assignment from `clob_updated` (at `t2`).

- It is not until `clob_updated` is assigned to `clob_copied` (`t5`) that `clob_copied` sees the modification made by `clob_updated`.

<!-- -->

    INSERT INTO PRINT_MEDIA VALUES (2049, 20030, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    COMMIT;

    DECLARE
      num_var          INTEGER;
      clob_updated     CLOB;
      clob_copied      CLOB;
      read_amount      INTEGER;
      read_offset      INTEGER;
      write_amount     INTEGER;
      write_offset     INTEGER;
      buffer           VARCHAR2(20);
    BEGIN

    -- At time t1:
      SELECT ad_sourcetext INTO clob_updated FROM PRINT_MEDIA
          WHERE ad_id = 20030
          FOR UPDATE;

      -- At time t2:
      clob_copied := clob_updated;
      -- after the assign, clob_copied and clob_updated see the same
      -- LOB value

      read_amount := 10;
      read_offset := 1;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcd'

      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t3:
      write_amount := 3;
      write_offset := 5;
      buffer := 'efg';
      dbms_lob.write(clob_updated, write_amount, write_offset,
            buffer);

      read_amount := 10;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcdefg'

      -- At time t4:
      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t5:
      clob_copied := clob_updated;

      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcdefg'
    END;
    /

**Parent topic:** Read-Consistent Locators

#### 14.2.6 Example of Updating a LOB with a PL/SQL (DBMS_LOB) Bind Variable

When a LOB locator is used as the source to update another persistent LOB (as in a SQL `INSERT` or `UPDATE` statement, the `DBMS_LOB`.`COPY` routine, and so on), the snapshot environment in the source LOB locator determines the LOB value that is used as the source.

If the source locator (for example `L1`) is a read-consistent locator, then the LOB value as of the time of the `SELECT` of `L1` is used. If the source locator (for example `L2`) is an updated locator, then the LOB value associated with the `L2` snapshot environment at the time of the operation is used.

In the following example, three `CLOB`s are created as potential locators: `clob_selected`, clob_updated, and clob_copied.

Note these progressions in the example at times `t1` through `t5`:

- At the time of the first `SELECT` `INTO` (at `t1`), the value in `ad_sourcetext` is associated with the locator `clob_updated`.

- The second operation (at `t2`) copies the value in `clob_updated` to `clob_copied`. At this juncture, both locators see the same value.

- Then (at `t3`), the program uses `DBMS_LOB`.`WRITE()` to alter the value in` clob_updated`, and a `DBMS_LOB`.`READ()` reveals a new value.

- However, a `DBMS_LOB`.`READ()` of the value through `clob_copied` (at `t4`) reveals that `clob_copied` does not see the change made by `clob_updated`.

- Therefore (at `t5`), when `clob_copied` is used as the source for the value of the `INSERT` statement, the value associated with `clob_copied` (for example, without the new changes made by `clob_updated`) is inserted. This is demonstrated by the subsequent `DBMS_LOB`.`READ()` of the value just inserted.

<!-- -->

    INSERT INTO PRINT_MEDIA VALUES (2056, 20020, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    COMMIT;

    DECLARE
      num_var           INTEGER;
      clob_selected     CLOB;
      clob_updated      CLOB;
      clob_copied       CLOB;
      read_amount       INTEGER;
      read_offset       INTEGER;
      write_amount      INTEGER;
      write_offset      INTEGER;
      buffer            VARCHAR2(20);
    BEGIN

      -- At time t1:
      SELECT ad_sourcetext INTO clob_updated FROM PRINT_MEDIA
          WHERE ad_id = 20020
          FOR UPDATE;

      read_amount := 10;
      read_offset := 1;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t2:
      clob_copied := clob_updated;

      -- At time t3:
      write_amount := 3;
      write_offset := 5;
      buffer := 'efg';
      dbms_lob.write(clob_updated, write_amount, write_offset, buffer);

      read_amount := 10;
      dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_updated value: ' || buffer);
      -- Produces the output 'abcdefg'
      -- note that clob_copied does not see the write made before
      -- clob_updated

      -- At time t4:
      read_amount := 10;
      dbms_lob.read(clob_copied, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_copied value: ' || buffer);
      -- Produces the output 'abcd'

      -- At time t5:
      -- the insert uses clob_copied view of the LOB value which does
      -- not include clob_updated changes
      INSERT INTO PRINT_MEDIA VALUES (2056, 20022, EMPTY_BLOB(),
        clob_copied, EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL)
        RETURNING ad_sourcetext INTO clob_selected;

      read_amount := 10;
      dbms_lob.read(clob_selected, read_amount, read_offset, buffer);
      dbms_output.put_line('clob_selected value: ' || buffer);
      -- Produces the output 'abcd'
    END;
    /

**Parent topic:** Read-Consistent Locators

#### 14.2.7 Example of Deleting a LOB Using Locator

Learn about deleting a LOB with a PL/SQL bind variable in this section.

The following example illustrates that LOB content through a locator selected at a given point of time is available even though the LOB is deleted in the same transaction.

In the following example, using table `print_media`, two CLOBs are created as potential locators:`clob_selected` and `clob_copied`.

Note these progressions in the example at times `t1` through `t3`:

- At the time of the first `SELECT` `INTO` (at `t1`), the value in`ad_sourcetext` for `ad_id` value 20020 is associated with the locator `clob_selected`. The value in `ad_sourcetext` for `ad_id` value 20021 is associated with the locator `clob_copied`.
- The second operation (at `t2`) deletes the row with `ad_id` value 20020. However, a `DBMS_LOB.READ()` of the value through `clob_selected` (at `t1`) reveals that it is a read-consistent locator, continuing to refer to the same value as of the time of its SELECT.
- The third operation (at `t3`), copies the LOB data read through `clob_selected` into the LOB `clob_copied`. `DBMS_LOB.READ()` of the value through `clob_selected` and `clob_copied` are now the same and refer to the same value as of the time of `SELECT` of `clob_selected`.

<!-- -->

    INSERT INTO PRINT_MEDIA VALUES (2056, 20020, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    INSERT INTO PRINT_MEDIA VALUES (2057, 20021, EMPTY_BLOB(),
        'cdef', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    DECLARE
      clob_selected CLOB;
      clob_copied CLOB;
      buffer VARCHAR2(20);
      read_amount INTEGER := 20;
      read_offset INTEGER := 1;

    BEGIN
      -- At time t1:
      SELECT ad_sourcetext INTO clob_selected
          FROM PRINT_MEDIA
          WHERE ad_id = 20020
          FOR UPDATE;

      SELECT ad_sourcetext INTO clob_copied
          FROM PRINT_MEDIA
          WHERE ad_id = 20021
          FOR UPDATE;

      dbms_lob.read(clob_selected, read_amount, read_offset,buffer);
      dbms_output.put_line(buffer);
      -- Produces the output 'abcd'

      dbms_lob.read(clob_copied, read_amount, read_offset,buffer);
      dbms_output.put_line(buffer);
      -- Produces the output 'cdef'

      -- At time t2: Delete the CLOB associated with clob_selected
      DELETE FROM PRINT_MEDIA WHERE ad_id = 20020;

      dbms_lob.read(clob_selected, read_amount, read_offset,buffer);
      dbms_output.put_line(buffer);
      -- Produces the output 'abcd'

      -- At time t3:
      -- Copy using clob_selected
      dbms_lob.copy(clob_copied, clob_selected, 4000, 1, 1);
      dbms_lob.read(clob_copied, read_amount, read_offset,buffer);
      dbms_output.put_line(buffer);
      -- Produces the output 'abcd'

    END;
    /

**Parent topic:** Read-Consistent Locators

### 14.3 LOB Locators and Transaction Boundaries

LOB locators can be used in transactions and transaction IDs.

**See Also:**

[LOB Locators and BFILE Locators](working-with-LOBs.md) for more information about LOB locators

Topics:

- About LOB Locators and Transaction Boundaries

- Read and Write Operations on a LOB Using Locators

- Selecting the Locator Outside of the Transaction Boundary

- Selecting the Locator Within a Transaction Boundary

- LOB Locators Cannot Span Transactions

- Example of Locator Not Spanning a Transaction

<!-- -->

- About LOB Locators and Transaction Boundaries
- Read and Write Operations on a LOB Using Locators
- Selecting the Locator Outside of the Transaction Boundary
- Selecting the Locator Within a Transaction Boundary
- LOB Locators Cannot Span Transactions
- Example of Locator Not Spanning a Transaction

**Parent topic:** Advanced Design Considerations

#### 14.3.1 About LOB Locators and Transaction Boundaries

Note the following regarding LOB locators and transactions:

- Locators contain transaction IDs when:

  You Begin the Transaction, Then Select Locator: If you begin a transaction and subsequently select a locator, then the locator contains the transaction ID. Note that you can implicitly be in a transaction without explicitly beginning one. For example, `SELECT`... `FOR` `UPDATE` implicitly begins a transaction. In such a case, the locator contains a transaction ID.

- Locators Do Not Contain Transaction IDs When...

  - You are Outside the Transaction, Then Select Locator:By contrast, if you select a locator outside of a transaction, then the locator does not contain a transaction ID.

  - When Selected Prior to DML Statement Execution: A transaction ID is not assigned until the first DML statement executes. Therefore, locators that are selected prior to such a DML statement do not contain a transaction ID.

**Parent topic:** LOB Locators and Transaction Boundaries

#### 14.3.2 Read and Write Operations on a LOB Using Locators

You can always read LOB data using the locator irrespective of whether or not the locator contains a transaction ID.

- Cannot Write Using Locator:

  If the locator contains a transaction ID, then you cannot write to the LOB outside of that particular transaction.

- Can Write Using Locator:

  If the locator does not contain a transaction ID, then you can write to the LOB after beginning a transaction either explicitly or implicitly.

- Cannot Read or Write Using Locator With Serializable Transactions:

  If the locator contains a transaction ID of an older transaction, and the current transaction is serializable, then you cannot read or write using that locator.

- Can Read, Not Write Using Locator With Non-Serializable Transactions:

  If the transaction is non-serializable, then you can read, but not write outside of that transaction.

The examples Selecting the Locator Outside of the Transaction Boundary, Selecting the Locator Within a Transaction Boundary, LOB Locators Cannot Span Transactions, and Example of Locator Not Spanning a Transaction show the relationship between locators and non-serializable transactions

**Parent topic:** LOB Locators and Transaction Boundaries

#### 14.3.3 Selecting the Locator Outside of the Transaction Boundary

Two scenarios describe techniques for using locators in non-serializable transactions when the locator is selected outside of a transaction.

##### First Scenario:

1.  Select the locator with no current transaction. At this point, the locator does not contain a transaction id.

2.  Begin the transaction.

3.  Use the locator to read data from the LOB.

4.  Commit or rollback the transaction.

5.  Use the locator to read data from the LOB.

6.  Begin a transaction. The locator does not contain a transaction id.

7.  Use the locator to write data to the LOB. This operation is valid because the locator did not contain a transaction id prior to the write. After this call, the locator contains a transaction id.

##### Second Scenario:

1.  Select the locator with no current transaction. At this point, the locator does not contain a transaction id.
2.  Begin the transaction. The locator does not contain a transaction id.
3.  Use the locator to read data from the LOB. The locator does not contain a transaction id.
4.  Use the locator to write data to the LOB. This operation is valid because the locator did not contain a transaction id prior to the write. After this call, the locator contains a transaction id. You can continue to read from or write to the LOB.
5.  Commit or rollback the transaction. The locator continues to contain the transaction id.
6.  Use the locator to read data from the LOB. This is a valid operation.
7.  Begin a transaction. The locator contains the previous transaction id.
8.  Use the locator to write data to the LOB. This write operation fails because the locator does not contain the transaction id that matches the current transaction.

**Parent topic:** LOB Locators and Transaction Boundaries

#### 14.3.4 Selecting the Locator Within a Transaction Boundary

Two scenarios describe techniques for using locators in non-serializable transactions when the locator is selected within a transaction.

##### First Scenario:

1.  Select the locator within a transaction. At this point, the locator contains the transaction id.

2.  Begin the transaction. The locator contains the previous transaction id.

3.  Use the locator to read data from the LOB. This operation is valid even though the transaction id in the locator does not match the current transaction.

    **See Also:**

    "Read-Consistent Locators" for more information about using the locator to read LOB data.

4.  Use the locator to write data to the LOB. This operation fails because the transaction id in the locator does not match the current transaction.

##### Second Scenario:

1.  Begin a transaction.
2.  Select the locator. The locator contains the transaction id because it was selected within a transaction.
3.  Use the locator to read from or write to the LOB. These operations are valid.
4.  Commit or rollback the transaction. The locator continues to contain the transaction id.
5.  Use the locator to read data from the LOB. This operation is valid even though there is a transaction id in the locator and the transaction was previously committed or rolled back.
6.  Use the locator to write data to the LOB. This operation fails because the transaction id in the locator is for a transaction that was previously committed or rolled back.

**Parent topic:** LOB Locators and Transaction Boundaries

#### 14.3.5 LOB Locators Cannot Span Transactions

Modifying a persistent LOB value through the LOB locator using `DBMS_LOB`, OCI, or SQL `INSERT` or `UPDATE` statements changes the locator from a read-consistent locator to an updated locator.

The `INSERT` or `UPDATE` statement automatically starts a transaction and locks the row. Once this has occurred, the locator cannot be used outside the current transaction to modify the LOB value. In other words, LOB locators that are used to write data cannot span transactions. However, the locator can be used to read the LOB value unless you are in a serializable transaction.

**See Also:**

"LOB Locators and Transaction Boundaries ", for more information about the relationship between LOBs and transaction boundaries.

In Example of Locator Not Spanning a Transaction , a `CLOB` locator is created: `clob_updated`

- At the time of the first `SELECT` `INTO` (at t1), the value in `ad_sourcetext` is associated with the locator `clob_updated`.

- The second operation (at t2), uses the `DBMS_LOB`.`WRITE` function to alter the value in `clob_updated`, and a `DBMS_LOB`.`READ` reveals a new value.

- The `commit` statement (at t3) ends the current transaction.

- Therefore (at t4), the subsequent `DBMS_LOB`.`WRITE` operation fails because the `clob_updated` locator refers to a different (already committed) transaction. This is noted by the error returned. You must re-select the LOB locator before using it in further `DBMS_LOB` (and OCI) modify operations.

**Parent topic:** LOB Locators and Transaction Boundaries

#### 14.3.6 Example of Locator Not Spanning a Transaction

The example uses the `print_media` table described in "[Table for LOB Examples: The PM Schema print_media Table](working-with-LOBs.md)"

    INSERT INTO PRINT_MEDIA VALUES (2056, 20010, EMPTY_BLOB(),
        'abcd', EMPTY_CLOB(), EMPTY_CLOB(), NULL, NULL, NULL, NULL);

    COMMIT;

    DECLARE
      num_var          INTEGER;
      clob_updated     CLOB;
      read_amount      INTEGER;
      read_offset      INTEGER;
      write_amount     INTEGER;
      write_offset     INTEGER;
      buffer           VARCHAR2(20);

    BEGIN
              -- At time t1:
         SELECT      ad_sourcetext
         INTO        clob_updated
         FROM        PRINT_MEDIA
         WHERE       ad_id = 20010
         FOR UPDATE;
         read_amount := 10;
         read_offset := 1;
         dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
         dbms_output.put_line('clob_updated value: ' || buffer);
         -- This produces the output 'abcd'

         -- At time t2:
         write_amount := 3;
         write_offset := 5;
         buffer := 'efg';
         dbms_lob.write(clob_updated, write_amount, write_offset, buffer);
         read_amount := 10;
         dbms_lob.read(clob_updated, read_amount, read_offset, buffer);
         dbms_output.put_line('clob_updated value: ' || buffer);
         -- This produces the output 'abcdefg'

        -- At time t3:
        COMMIT;

         -- At time t4:
        dbms_lob.write(clob_updated , write_amount, write_offset, buffer);
        -- ERROR: ORA-22990: LOB locators cannot span transactions
    END;
    /

**Parent topic:** LOB Locators and Transaction Boundaries

### 14.4 LOBs in the Object Cache

When you copy one object to another in the object cache with a LOB locator attribute, only the LOB locator is copied.

This means that the LOB attribute in these two different objects contain exactly the same locator which refers to one and the same LOB value. Only when the target object is flushed is a separate, physical copy of the LOB value made, which is distinct from the source LOB value.

**See Also:**

"Example of Updating LOBs and Read-Consistency" for a description of what version of the LOB value is seen by each object if a write is performed through one of the locators.

Therefore, in cases where you want to modify the LOB that was the target of the copy, you must flush the target object, refresh the target object, and then write to the LOB through the locator attribute.

Consider these object cache issues for internal and external LOB attributes:

- Persistent LOB attributes: Creating an object in object cache, sets the LOB attribute to empty.

  When you create an object in the object cache that contains a persistent LOB attribute, the LOB attribute is implicitly set to empty. You may not use this empty LOB locator to write data to the LOB. You must first flush the object, thereby inserting a row into the table and creating an empty LOB — that is, a LOB with 0 length. Once the object is refreshed in the object cache (use `OCI_PIN_LATEST`), the real LOB locator is read into the attribute, and you can then call the OCI LOB API to write data to the LOB.

- External LOB (`BFILE`) attributes: Creating an object in object cache, sets the `BFILE` attribute to `NULL`.

  When creating an object with an external LOB (`BFILE)` attribute, the `BFILE` is set to `NULL`. It must be updated with a valid directory object name and file name before reading from the `BFILE`.

**Parent topic:** Advanced Design Considerations

### 14.5 Terabyte-Size LOB Support

Terabyte-size LOBs are LOBs that are up to a maximum size of 8 to 128 terabytes depending on database block size.

Topics:

- About Terabyte-Size LOB Support

- Maximum Storage Limit for Terabyte-Size LOBs

- Using Terabyte-Size LOBs with JDBC

- Using Terabyte-Size LOBs with the DBMS_LOB Package

- Using Terabyte-Size LOBs with OCI

<!-- -->

- About Terabyte-Size LOB Support
- Maximum Storage Limit for Terabyte-Size LOBs
- Using Terabyte-Size LOBs with JDBC
- Using Terabyte-Size LOBs with the DBMS_LOB Package
- Using Terabyte-Size LOBs with OCI

**Parent topic:** Advanced Design Considerations

#### 14.5.1 About Terabyte-Size LOB Support

Terabyte-size LOBs are supported by the following APIs:

- Java using JDBC (Java Database Connectivity)

- PL/SQL using the DBMS_LOB Package

- C using OCI (Oracle Call Interface)

You cannot create and use LOB instances of size greater than 4 gigabytes "terabyte-size LOBs"— in the following programmatic environments:

- COBOL using the Pro\*COBOL Precompiler

- C or C++ using the Pro\*C/C++ Precompiler

**Note:**

Oracle Database does not support `BFILE`s larger than 2^64-1 bytes (`UB8MAXVAL` in OCI) in any programmatic environment. Any additional file size limit imposed by your operating system also applies to `BFILE`s.

**Parent topic:** Terabyte-Size LOB Support

#### 14.5.2 Maximum Storage Limit for Terabyte-Size LOBs

In supported environments, you can create and manipulate LOBs that are up to the maximum storage size limit for your database configuration.

Oracle Database lets you create tablespaces with block sizes different from the database block size, and the maximum size of a LOB depends on the size of the tablespace blocks. `CHUNK` is a parameter of LOB storage whose value is controlled by the block size of the tablespace in which the LOB is stored.

**Note:**

The `CHUNK` parameter does not apply to SecureFiles. It is only used for BasicFiles LOBs.

When you create a LOB column, you can specify a value for `CHUNK`, which is the number of bytes to be allocated for LOB manipulation. The value must be a multiple of the tablespace block size, or Oracle Database rounds up to the next multiple. (If the tablespace block size is the same as the database block size, then `CHUNK` is also a multiple of the database block size.)

The maximum allowable storage limit for your configuration depends on the tablespace block size setting, and is calculated as (4 gigabytes - 1) times the value obtained from `DBMS_LOB.GETCHUNKSIZE` or `OCILobGetChunkSize()`. This value, in number of bytes for `BLOB`s or number of characters for `CLOB`s, is actually less than the size of the `CHUNK` parameter due to internal storage overhead. With the current allowable range for the tablespace block size from 2K to 32K, the storage limit ranges from 8 terabytes to 128 terabytes.

For example, suppose your database block size is 32K bytes and you create a tablespace with a nonstandard block size of 8K. Further suppose that you create a table with a LOB column and specify a CHUNK size of 16K (which is a multiple of the 8K tablespace block size). Then the maximum size of a LOB in this column is (4 gigabytes - 1) \* 16K.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for details on the initialization parameter setting for your database installation

- "[CHUNK](LOB-storage-with-applications.md)"

This storage limit applies to all LOB types in environments that support terabyte-size LOBs. However, note that `CLOB` and `NCLOB` types are sized in characters, while the `BLOB` type is sized in bytes.

**Parent topic:** Terabyte-Size LOB Support

#### 14.5.3 Using Terabyte-Size LOBs with JDBC

You can use the LOB APIs included in the Oracle JDBC classes to access terabyte-size LOBs.

**See Also:**

"[Using Java (JDBC) to Work With LOBs](overview-of-supplied-LOB-APIs.md)"

**Parent topic:** Terabyte-Size LOB Support

#### 14.5.4 Using Terabyte-Size LOBs with the DBMS_LOB Package

You can access terabyte-size LOBs with all APIs in the DBMS_LOB PL/SQL package.

Use `DBMS_LOB.GETCHUNKSIZE` to obtain the value to be used in reading and writing LOBs. The number of bytes stored in a chunk is actually less than the size of the `CHUNK` parameter due to internal storage overhead. The `DBMS_LOB.GET_STORAGE_LIMIT` function returns the storage limit for your database configuration. This is the maximum allowable size for LOBs. `BLOB`s are sized in bytes, while `CLOB`s and `NCLOB`s are sized in characters.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)for details on the initialization parameter setting for your database installation.

**Parent topic:** Terabyte-Size LOB Support

#### 14.5.5 Using Terabyte-Size LOBs with OCI

The Oracle Call Interface API provides a set of functions for operations on LOBs of all sizes.

`OCILobGetChunkSize()` returns the value, in bytes for `BLOB`s, or in characters for `CLOB`s, to be used in reading and writing LOBs. For varying-width character sets, the value is the number of Unicode characters that fit. The number of bytes stored in a chunk is actually less than the size of the `CHUNK` parameter due to internal storage overhead. The function `OCILobGetStorageLimit()` returns the maximum allowable size, in bytes, of internal LOBs in the current database installation. If streaming mode is used, where the whole LOB is read, there is no requirement to get the chunk size.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/lobs-and-bfile-operations.md) for details about OCI functions that support LOBs

**Parent topic:** Terabyte-Size LOB Support

### 14.6 Guidelines for Creating Gigabyte LOBs

To create gigabyte LOBs in supported environments, use the following guidelines to make use of all available space in the tablespace for LOB storage:

- Single Data File Size Restrictions:

  There are restrictions on the size of a single data file for each operating system. For example, Solaris 2.5 only allows operating system files of up to 2 gigabytes. Hence, add more data files to the tablespace when the LOB grows larger than the maximum allowed file size of the operating system on which your Oracle Database runs.

- Set PCT INCREASE Parameter to Zero:

  `PCTINCREASE` parameter in the LOB storage clause specifies the percent growth of the new extent size. When a LOB is being filled up piece by piece in a tablespace, numerous new extents get created in the process. If the extent sizes keep increasing by the default value of 50 percent every time, then extents become unmanageable and eventually waste space in the tablespace. Therefore, the `PCTINCREASE` parameter should be set to zero or a small value.

- Set MAXEXTENTS to a Suitable Value or UNLIMITED:

  The `MAXEXTENTS` parameter limits the number of extents allowed for the LOB column. A large number of extents are created incrementally as the LOB size grows. Therefore, the parameter should be set to a value that is large enough to hold all the LOBs for the column. Alternatively, you could set it to `UNLIMITED`.

- Use a Large Extent Size:

  For every new extent created, Oracle generates undo information for the header and other metadata for the extent. If the number of extents is large, then the rollback segment can be saturated. To get around this, choose a large extent size, say 100 megabytes, to reduce the frequency of extent creation, or commit the transaction more often to reuse the space in the rollback segment.

<!-- -->

- Creating a Tablespace and Table to Store Gigabyte LOBs

**Parent topic:** Advanced Design Considerations

#### 14.6.1 Creating a Tablespace and Table to Store Gigabyte LOBs

The following example illustrates how to create a tablespace and table to store gigabyte LOBs.

    CREATE TABLESPACE lobtbs1 DATAFILE '/your/own/data/directory/lobtbs_1.dat'
    SIZE 2000M REUSE ONLINE NOLOGGING DEFAULT STORAGE (MAXEXTENTS UNLIMITED);
    ALTER TABLESPACE lobtbs1 ADD DATAFILE
    '/your/own/data/directory/lobtbs_2.dat' SIZE 2000M REUSE;

    CREATE TABLE print_media_backup
      (product_id NUMBER(6),
       ad_id NUMBER(6),
       ad_composite BLOB,
       ad_sourcetext CLOB,
       ad_finaltext CLOB,
       ad_fltextn NCLOB,
       ad_textdocs_ntab textdoc_tab,
       ad_photo BLOB,
       ad_graphic BLOB,
       ad_header adheader_typ)
       NESTED TABLE ad_textdocs_ntab STORE AS textdocs_nestedtab5
       LOB(ad_sourcetext) STORE AS (TABLESPACE lobtbs1 CHUNK 32768 PCTVERSION 0
                                    NOCACHE NOLOGGING
                                    STORAGE(INITIAL 100M NEXT 100M MAXEXTENTS
                                    UNLIMITED PCTINCREASE 0));

Note the following with respect to this example:

- The storage clause in this example is specified in the `CREATE TABLESPACE` statement.

- You can specify the storage clause in the `CREATE TABLE` statement as an alternative.

- The storage clause is not allowed in the `CREATE TEMPORARY TABLESPACE `statement.

- Setting the `PCTINCREASE` parameter to 0 is recommended for gigabyte LOBs. For small, or medium size lobs, the default `PCTINCREASE` value of 50 is recommended as it reduces the number of extent allocations.

**Parent topic:** Guidelines for Creating Gigabyte LOBs
