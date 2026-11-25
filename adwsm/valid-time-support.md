This chapter describes the support for valid time, also known as effective dating, with version-enabled tables.

It contains the following major sections:

- Valid Time Support: Introduction and Example
  Some applications need to store data with an associated time range that indicates the validity of the data. That is, each record is valid only within the time range associated with the record.
- WM_PERIOD Data Type
  The `WM_PERIOD` data type is used to specify a valid time range for the session or workspace, and for a row in a version-enabled table.
- Valid Time Constants
  The following table lists constants that can be used in the `validFrom` and `validTill` timestamps of a `WM_PERIOD` specification.
- API Features for Valid Time Support
  The following table lists DBMS_WM subprograms that are devoted to valid time support or that have parameters related to valid time support.
- Operators for Valid Time Support
  Workspace Manager provides relationship checking operators and set operators that accept two time period parameters and that can be used to apply valid time filters in a query.
- Queries and DML Operations with Valid Time Support
  This section describes some behaviors and considerations for queries and data manipulation language (insert, update, and delete) operations related to valid time support.
- Constraint Management for Valid Time Support
  This section describes considerations related to valid time support that affect referential integrity constraints and unique constraints.
- Locking with Valid Time Support
  If a row in a version-enabled table with valid time support is locked, it is automatically locked for its entire valid time period. There is no way to lock a row for a specified time period.
- Static Data Dictionary Views Affected by Valid Time Support
  This section describes the effect on valid time support on Workspace Manager static data dictionary views.
- Adding Valid Time Support to an Existing Table
  You can add valid time support to an existing version-enabled table.
- Merging and Refreshing Workspaces for Tables with Valid Time Support
  When tables that have valid time support are merged or refreshed, you can determine the resulting rows by considering the distinct cases when there is an intersection between rows for the same primary key value.

**Parent topic:** [Conceptual and Usage Information](workspace-manager-concepts-usage.md)

### 3.1 Valid Time Support: Introduction and Example

Some applications need to store data with an associated time range that indicates the validity of the data. That is, each record is valid only within the time range associated with the record.

You can enable valid time support when you version-enable a table. (You can also add valid time support to an existing version-enabled table, as explained in Adding Valid Time Support to an Existing Table.) If you enable valid time support, each row contains an added column to hold the valid time period associated with the row. You can specify a valid time range for the session, and Workspace Manager will ensure that queries and insert, update, and delete operations correctly reflect and accommodate the valid time range. The valid time range specified can be in the past or the future, or it can include the past, present, and future.

Example 3-1 presents a simple example of valid time support. The example does the following:

1.  Creates a table of employees and their salaries.

2.  Version-enables the table, specifying valid time support, which causes a column named `WM_VALID` to be added to the table automatically.

3.  Inserts rows into the table. For each row, it specifies the employee name, salary, and valid time period.

4.  Sets the valid time range for the session.

5.  Updates a row, specifying a new salary and valid time period for an employee.

6.  Disables versioning on the table.

Example 3-1:

- Refers to valid time support concepts and techniques that will be explained in other sections of this chapter.

- Assumes that you are familiar with the Workspace Manager concepts and techniques explained in [Introduction to Workspace Manager](introduction-to-workspace-manager.md).

- Does not create workspaces or savepoints. (These are shown in [Example: Marketing Budget Options](introduction-to-workspace-manager.md) and [Example: Warehouse Expansion Options](introduction-to-workspace-manager.md) in [Simplified Examples Using Workspace Manager](introduction-to-workspace-manager.md).)

Example 3-1 Valid Time Support

    -- Create a very simple employees table (deliberately oversimplified
    -- for purposes of illustration).
    CREATE TABLE employees (
      name VARCHAR2(16) PRIMARY KEY,
      salary NUMBER
    );

    -- Version-enable the table. Specify TRUE for valid time support.
    EXECUTE DBMS_WM.EnableVersioning ('employees', 'VIEW_WO_OVERWRITE', FALSE, TRUE);

    INSERT INTO employees VALUES(
      'Adams',
      30000,
      WMSYS.WM_PERIOD(TO_DATE('01-01-1990', 'MM-DD-YYYY'),
                      TO_DATE('01-01-2005', 'MM-DD-YYYY'))
    );
    INSERT INTO employees VALUES(
      'Baxter',
      40000,
      WMSYS.WM_PERIOD(TO_DATE('01-01-2000', 'MM-DD-YYYY'), DBMS_WM.UNTIL_CHANGED)
    );

    INSERT INTO employees VALUES(
      'Coleman',
      50000,
      WMSYS.WM_PERIOD(TO_DATE('01-01-2003', 'MM-DD-YYYY'),
                      TO_DATE('12-31-9999', 'MM-DD-YYYY'))
    );

    COMMIT;

    -- Set valid time period to virtually all time.
    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-1900', 'MM-DD-YYYY'),
      TO_DATE('01-01-9999', 'MM-DD-YYYY'));

    -- Update the salary for an existing employee. Perform "sequenced" update, so
    -- that existing time-related information is preserved. This results in two rows
    -- for Baxter.
    -- First, set valid time to the intended range for Baxter's raise.
    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-2003', 'MM-DD-YYYY'), DBMS_WM.UNTIL_CHANGED);
    -- Give Baxter a raise, effective 01-Jan-2003 until changed.
    UPDATE employees SET salary = 45000 WHERE name = 'Baxter';

    -- Disable versioning. By default (keepWMValid parameter value of TRUE),
    -- the WM_VALID column is kept, with all its data.
    COMMIT;
    EXECUTE DBMS_WM.DisableVersioning ('employees');

**Parent topic:** Workspace Manager Valid Time Support

### 3.2 WM_PERIOD Data Type

The `WM_PERIOD` data type is used to specify a valid time range for the session or workspace, and for a row in a version-enabled table.

The `WM_PERIOD` type is defined as follows:

    CREATE TYPE WM_PERIOD AS OBJECT  (
      validFrom  TIMESTAMP WITH TIME ZONE,
      validTill  TIMESTAMP WITH TIME ZONE,
    MAP member function wm_period_map return varchar2);

The `validFrom` date is inclusive, and the `validTill` period is exclusive; that is, the valid date range starts on the `validFrom` date and extends up to but not including the `validTill` date.

The `wm_period_map` member function enables ordering (sorting) and the use of `DISTINCT` on columns of type `WM_PERIOD`.

Example 3-2 Setting the Session Valid Time to a Specific Date

Example 3-2 sets the session valid time range to 01-Jan-2003.

    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-2003', 'MM-DD-YYYY'), TO_DATE('01-02-2003', 'MM-DD-YYYY'));

Example 3-3 inserts a row that is valid from 01-Jan-2003 until it is changed.

Example 3-3 Inserting a Row Valid for a Time Range

    INSERT INTO employees VALUES(
      'Baxter',
      40000,
      WMSYS.WM_PERIOD(TO_DATE('01-01-2003', 'MM-DD-YYYY'), DBMS_WM.UNTIL_CHANGED)
    );

If you want the valid time range to be stored in views created on tables with valid time support, using two columns of type `TIMEZONE WITH TIMESTAMP` instead of a single column of type `WM_VALID`, you can set the Workspace Manager system parameter `USE_SCALAR_TYPES_FOR_VALIDTIME` to `ON`, as explained in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).

**Parent topic:** Workspace Manager Valid Time Support

### 3.3 Valid Time Constants

The following table lists constants that can be used in the `validFrom` and `validTill` timestamps of a `WM_PERIOD` specification.

(Workspace Manager uses these as constants, but they are implemented as functions.)

Table 3-1 Constants for Valid Time Support

| Constant              | Explanation                                                                                                                                       |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| DBMS_WM.MIN_TIME      | The minimum (earliest) timestamp value supported by Workspace Manager. Currently the beginning of the day on 01-Jan in the year -4712 (4712 BCE). |
| DBMS_WM.MAX_TIME      | The maximum (latest) timestamp value supported by Workspace Manager. Currently the end of the day (11:59.999999000 pm) on 31-Dec-9999.            |
| DBMS_WM.UNTIL_CHANGED | A timestamp that is treated as DBMS_WM.MAX_TIME until a subsequent modification overrides the value.                                              |

**Parent topic:** Workspace Manager Valid Time Support

### 3.4 API Features for Valid Time Support

The following table lists DBMS_WM subprograms that are devoted to valid time support or that have parameters related to valid time support.

Table 3-2 API Features for Valid Time Support

| Subprogram                                      | Valid Time Support                                                                                                                                                                                                                                                                                                            |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [EnableVersioning](DBMS_WM-reference.md)        | If the `validTime` parameter value is TRUE, the table is version-enabled `with` valid time support. A column named `WM_VALID` of type WM_PERIOD is added to the table. For any existing rows, the `WM_VALID` column is set with a `validFrom` timestamp of SYSTIMESTAMP and a `validTill` timestamp of DBMS_WM.UNTIL_CHANGED. |
| [DisableVersioning](DBMS_WM-reference.md)       | The `keepWMValid` parameter determines whether to keep (the default) or delete the `WM_VALID` column and its data when the table is version-disabled.                                                                                                                                                                         |
| [GetValidFrom](DBMS_WM-reference.md)            | Returns the `validFrom` timestamp from the session valid time period.                                                                                                                                                                                                                                                         |
| [GetValidTill](DBMS_WM-reference.md)            | Returns the `validTill` timestamp from the session valid time period.                                                                                                                                                                                                                                                         |
| [SetValidTime](DBMS_WM-reference.md)            | Sets the session valid time period to the specified range. You can execute the procedure with no parameters (to have the valid time range set as from the current time and until changed), with only the `validFrom` parameter, or with both the `validFrom` and `validTill` parameters.                                      |
| [SetValidTimeFilterOFF](DBMS_WM-reference.md)   | Removes the valid time filter for the current session.                                                                                                                                                                                                                                                                        |
| [SetValidTimeFilterON](DBMS_WM-reference.md)    | Sets a valid time filter for the current session (that is, a time to be applied to version-enabled tables.                                                                                                                                                                                                                    |
| [SetWMValidUpdateModeOFF](DBMS_WM-reference.md) | Disables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support.                                                                                                                                                                                                 |
| [SetWMValidUpdateModeON](DBMS_WM-reference.md)  | Enables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support.                                                                                                                                                                                                  |

**Parent topic:** Workspace Manager Valid Time Support

### 3.5 Operators for Valid Time Support

Workspace Manager provides relationship checking operators and set operators that accept two time period parameters and that can be used to apply valid time filters in a query.

The relationship checking operators return the integer value 1 if the relationship between the two periods exists, and 0 if the relationship does not exist. The following relationship checking operators for are provided for valid time support:

- WM_OVERLAPS checks if two periods overlap.

- WM_CONTAINS checks if the first period contains the second period.

- WM_MEETS checks if the end of the first period is the start of the second period.

- WM_EQUALS checks if the two periods are equal (that is, their start and end times are the same).

- WM_LESSTHAN checks if the end of the first period is less than (that is, earlier than) the start of the second period.

- WM_GREATERTHAN checks if the start of the first period is greater than (that is, later than) the end of the second period.

The set operators return the period reflecting the relationship between the two periods, or a null value if the two periods do not have the specified relationship. The following set operators for are provided for valid time support:

- WM_INTERSECTION returns the intersection of the two periods, that is, the time range common to both periods.

- WM_LDIFF returns the difference between the two periods on the left (that is, earlier in time).

- WM_RDIFF returns the difference between the two periods on the right (that is, later in time).

You can use the relationship checking operators as alternatives to using the wm_valid.validFrom and wm_valid.validTill attributes of the row. For example, the following two queries, which select data valid on 01-Jan-1991, are equivalent:

    SELECT * FROM employees e WHERE WM_CONTAINS (e.wm_valid,
       WMSYS.WM_PERIOD(TO_DATE('01-01-1991', 'MM-DD-YYYY'),
                       TO_DATE('01-02-1991', 'MM-DD-YYYY')) = 1;
    SELECT * from employees e
       WHERE e.wm_valid.validFrom <= TO_DATE('01-01-1991', 'MM-DD-YYYY')
         AND e.wm_valid.validTill > TO_DATE('01-03-1991', 'MM-DD-YYYY');

The rest of this section contains additional information about each operator. The operators are listed in alphabetical order.

- WM_CONTAINS
- WM_EQUALS
- WM_GREATERTHAN
- WM_INTERSECTION
- WM_LDIFF
- WM_LESSTHAN
- WM_MEETS
- WM_OVERLAPS
- WM_RDIFF

**Parent topic:** Workspace Manager Valid Time Support

#### 3.5.1 WM_CONTAINS

The WM_CONTAINS operator checks if the first period contains the second period. `WM_CONTAINS(p1, p2)` returns `1` only if the period `p1` contains the period `p2`; otherwise, it returns `0`.

For example:

    WM_CONTAINS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1988', 'MM-DD-YYYY'))) = 1

    WM_CONTAINS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY'))) = 0

Example 3-4 returns all rows in the `EMPLOYEES` table that were valid on 01-Jan-1995 (that is, where the `WM_VALID` column value contains the period for 01-Jan-1995).

Example 3-4 WM_CONTAINS Operator

    SELECT * FROM employees e
      WHERE WM_CONTAINS(e.wm_valid,
        wm_period(TO_DATE('01-01-1995', 'MM-DD-YYYY'),
                  TO_DATE('01-02-1995', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Adams                 30000
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.2 WM_EQUALS

The WM_EQUALS operator checks if the first period is equal to (that is, the same as) the second period. `WM_CONTAINS(p1, p2)` returns `1` only if the period `p1` is equal to the period `p2`; otherwise, it returns `0`.

For example:

    WM_EQUALS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY'))) = 1

    WM_EQUALS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY'))) = 0

Example 3-5 returns all rows in the `EMPLOYEES` table that are valid from 01-Jan-1990 until 01-Jan-2005 (that is, where the `WM_VALID` column value is equal to that period).

Example 3-5 WM_EQUALS Operator

    SELECT * FROM employees e
      WHERE WM_EQUALS(e.wm_valid,
        wm_period(TO_DATE('01-01-1990', 'MM-DD-YYYY'),
                  TO_DATE('01-01-2005', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Adams                 30000
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.3 WM_GREATERTHAN

The WM_GREATERTHAN operator checks if the first period is greater than (that is, occurs after) the second period. `WM_CONTAINS(p1, p2)` returns `1` only if the entire period `p1` is later than the period `p2`; otherwise, it returns `0`.

For example:

    WM_GREATERTHAN(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1970', 'MM-DD-YYYY'),
          TO_DATE('01-01-1980', 'MM-DD-YYYY'))) = 1

    WM_GREATERTHAN(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1970', 'MM-DD-YYYY'),
          TO_DATE('01-01-1981', 'MM-DD-YYYY'))) = 0

Example 3-6 returns all rows in the `EMPLOYEES` table that are valid only after 01-Jan-2001 (that is, where the `WM_VALID` column timestamps are both after 01-Jan-2001).

Example 3-6 WM_GREATERTHAN Operator

    SELECT * FROM employees e
      WHERE WM_GREATERTHAN(e.wm_valid,
        wm_period(TO_DATE('01-01-2001', 'MM-DD-YYYY'),
                  TO_DATE('01-02-2001', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Coleman               50000
    WM_PERIOD('01-JAN-2003 12:00:00 -04:00', '31-DEC-9999 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.4 WM_INTERSECTION

The WM_INTERSECTION operator returns the intersection of the two periods, that is, the period common to both specified periods. `WM_INTERSECTION(p1, p2)` returns a period that is the intersection of periods `p1` and `p2`.

The following example returns the period between 01-Jan-1985 to 01-Jan-1988:

    WM_INTERSECTION(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1988', 'MM-DD-YYYY')))

The following example returns the period between 01-Jan-1985 to 01-Jan-1990:

    WM_INTERSECTION(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY')))

The following example returns a null value, because there is no intersection of the periods:

    WM_INTERSECTION(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1992', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY')))

Example 3-7 returns, for each row in the `EMPLOYEES` table, the employee name and the period in which the `WM_PERIOD` column value intersects the period on 01-Jan-1995.

Example 3-7 WM_INTERSECTION Operator

    SELECT e.name, WM_INTERSECTION(e.wm_valid,
      wm_period(TO_DATE('01-01-1995', 'MM-DD-YYYY'),
                TO_DATE('01-02-1995', 'MM-DD-YYYY')))
     FROM employees e;

    NAME
    ----------------
    WM_INTERSECTION(E.WM_VALID,WM_PERIOD(TO_DATE('01-01-1995','MM-DD-
    --------------------------------------------------------------------------------
    Adams
    WM_PERIOD('01-JAN-1995 12:00:00 -04:00', '02-JAN-1995 12:00:00 -04:00')

    Baxter


    Coleman

As you can see in the output of Example 3-7, only Adams has a row that is valid on 01-Jan-1995.

**Parent topic:** Operators for Valid Time Support

#### 3.5.5 WM_LDIFF

The WM_LDIFF operator returns the difference between the two periods on the left (that is, earlier in time). `WM_LDIFF(p1, p2)` returns a period that is the difference between periods `p1` and `p2` on the left.

The following example returns the period between 01-Jan-1980 to 01-Jan-1985:

    WM_LDIFF(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1988', 'MM-DD-YYYY')))

The following example returns a null value because `p1.validFrom` is greater than `p2.validFrom`:

    WM_LDIFF(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1975', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY')))

The following example returns a null value because `p2` is completely outside (in this case, later than) `p1`:

    WM_LDIFF(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1992', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY')))

Example 3-8 returns, for each row in the `EMPLOYEES` table, the employee name and the period in which the `WM_PERIOD` column value is different on the left from 01-Jan-1995.

Example 3-8 WM_LDIFF Operator

    SELECT e.name, WM_LDIFF(e.wm_valid,
      wm_period(TO_DATE('01-01-1995', 'MM-DD-YYYY'),
                TO_DATE('01-02-1995', 'MM-DD-YYYY')))
     FROM employees e;

    NAME
    ----------------
    WM_LDIFF(E.WM_VALID,WM_PERIOD(TO_DATE('01-01-1995','MM-DD-YYYY'),
    --------------------------------------------------------------------------------
    Adams
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-1995 12:00:00 -04:00')

    Baxter


    Coleman

As you can see in the output of Example 3-8, only Adams has a row that is valid during the period of difference on the left.

**Parent topic:** Operators for Valid Time Support

#### 3.5.6 WM_LESSTHAN

The WM_LESSTHAN operator checks if the first period is less than (that is, occurs before) the second period. `WM_CONTAINS(p1, p2)` returns `1` only if the entire period `p1` is less than the period `p2`; otherwise, it returns `0`.

For example:

    WM_LESSTHAN(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1991', 'MM-DD-YYYY'),
          TO_DATE('01-01-1992', 'MM-DD-YYYY'))) = 1

    WM_LESSTHAN(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1989', 'MM-DD-YYYY'),
          TO_DATE('01-01-1992', 'MM-DD-YYYY'))) = 0

Example 3-9 returns all rows in the `EMPLOYEES` table that are valid only before 01-Jan-2010 (that is, where the `WM_VALID` column timestamps are both before 01-Jan-2001).

Example 3-9 WM_LESSTHAN Operator

    SELECT * FROM employees e
      WHERE WM_LESSTHAN(e.wm_valid,
        wm_period(TO_DATE('01-01-2010', 'MM-DD-YYYY'),
                  TO_DATE('01-02-2010', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Adams                 30000
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.7 WM_MEETS

The WM_MEETS operator checks if the end of the first period is the start of the second period. `WM_MEETS(p1, p2)` returns `1` only if `p1.validTill = p2.validFrom`; otherwise, it returns `0`.

For example:

    WM_MEETS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1990', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY'))) = 1

    WM_MEETS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1992', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY'))) = 0

Example 3-10 returns all rows in the `EMPLOYEES` table that are valid only if the ending timestamp of the valid date period is the same as the start of the period from 01-Jan-2005 until 01-Jan-2006 (that is, if `WM_VALID`.validTill is equal to the start of the specified period).

Example 3-10 WM_MEETS Operator

    SELECT * FROM employees e
      WHERE WM_MEETS(e.wm_valid,
        wm_period(TO_DATE('01-01-2005', 'MM-DD-YYYY'),
                  TO_DATE('01-01-2006', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Adams                 30000
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.8 WM_OVERLAPS

The WM_OVERLAPS operator checks if two periods overlap. `WM_OVERLAPS(p1, p2)` returns `1` if the periods `p1` and `p2` overlap; otherwise, it returns `0`.

For example:

    WM_OVERLAPS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY'))) = 1

    WM_OVERLAPS(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1970', 'MM-DD-YYYY'),
          TO_DATE('01-01-1980', 'MM-DD-YYYY'))) = 0

Example 3-11 returns all rows in the `EMPLOYEES` table whose valid date range overlaps the period from 01-Jan-1990 until 01-Jan-2000.

Example 3-11 WM_OVERLAPS Operator

    SELECT * FROM employees e
      WHERE WM_OVERLAPS(e.wm_valid,
        wm_period(TO_DATE('01-01-1990', 'MM-DD-YYYY'),
                  TO_DATE('01-01-2000', 'MM-DD-YYYY'))) = 1;

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Adams                 30000
    WM_PERIOD('01-JAN-1990 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

**Parent topic:** Operators for Valid Time Support

#### 3.5.9 WM_RDIFF

The WM_RDIFF operator returns the difference between the two periods on the right (that is, later in time). `WM_RDIFF(p1, p2)` returns a period that is the difference between periods `p1` and `p2` on the right.

The following example returns the period between 01-Jan-1988 to 01-Jan-1990:

    WM_RDIFF(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1985', 'MM-DD-YYYY'),
          TO_DATE('01-01-1988', 'MM-DD-YYYY')))

The following example returns a null value because `p1.validTill` is less than `p2.validTill`:

    WM_RDIFF(
       WM_PERIOD(
          TO_DATE('01-01-1980', 'MM-DD-YYYY'),
          TO_DATE('01-01-1990', 'MM-DD-YYYY')),
       WM_PERIOD(
          TO_DATE('01-01-1975', 'MM-DD-YYYY'),
          TO_DATE('01-01-1995', 'MM-DD-YYYY')))

Example 3-12 returns, for each row in the `EMPLOYEES` table, the employee name and the period in which the `WM_PERIOD` column value is different on the right from 01-Jan-1995.

Example 3-12 WM_RDIFF Operator

    SELECT e.name, WM_RDIFF(e.wm_valid,
      wm_period(TO_DATE('01-01-1995', 'MM-DD-YYYY'),
                TO_DATE('01-02-1995', 'MM-DD-YYYY')))
     FROM employees e;

    NAME
    ----------------
    WM_RDIFF(E.WM_VALID,WM_PERIOD(TO_DATE('01-01-1995','MM-DD-YYYY'),
    --------------------------------------------------------------------------------
    Adams
    WM_PERIOD('02-JAN-1995 12:00:00 -04:00', '01-JAN-2005 12:00:00 -04:00')

    Baxter


    Coleman
    WM_PERIOD('01-JAN-2003 12:00:00 -04:00', '31-DEC-9999 12:00:00 -04:00')

As you can see in the output of Example 3-12, only Adams and Coleman have rows that are valid during the period of difference on the right.

**Parent topic:** Operators for Valid Time Support

### 3.6 Queries and DML Operations with Valid Time Support

This section describes some behaviors and considerations for queries and data manipulation language (insert, update, and delete) operations related to valid time support.

- Queries
- Data Manipulation (DML) Operations

**Parent topic:** Workspace Manager Valid Time Support

#### 3.6.1 Queries

All queries issued against a version-enabled table with valid time support take into account the current session's valid time setting (set using the [SetValidTime](DBMS_WM-reference.md) or [SetValidTimeFilterON](DBMS_WM-reference.md) procedure). Unless the query specifies otherwise (for example, by using one of the valid time support operators described in Operators for Valid Time Support), each query displays all rows from the underlying table having a valid time range that overlaps the session valid time or valid time filter, and that satisfy the other conditions of the query.

By default (that is, if the [SetValidTime](DBMS_WM-reference.md) procedure has not been invoked in the session or if it was invoked with no parameters), all rows that are valid at the current time are considered valid, and the valid time period is considered to be from the current time forward without limit.

**Parent topic:** Queries and DML Operations with Valid Time Support

#### 3.6.2 Data Manipulation (DML) Operations

All DML statements (INSERT, UPDATE, and DELETE) issued against a version-enabled table with valid time support take into account the current session's valid time setting and update mode. (The update mode is controlled by the [SetWMValidUpdateModeON](DBMS_WM-reference.md) and [SetWMValidUpdateModeOFF](DBMS_WM-reference.md) procedures.) The DML statements can affect all rows that are valid for the valid time period.

By default (that is, if the [SetValidTime](DBMS_WM-reference.md) procedure has not been invoked in the session or if it was invoked with no parameters), all rows that are valid at the current time can be affected by DML statements, and all modified rows have their valid time range timestamps set as from the current time until changed.

The following sections describe additional considerations that apply to specific kinds of DML operations.

- Update Operations
- Insert Operations

**Parent topic:** Queries and DML Operations with Valid Time Support

##### 3.6.2.1 Update Operations

Update operations to version-enabled tables with valid time support can be sequenced or nonsequenced.

A sequenced update operation occurs when you do not specify a change to the `WM_VALID` column in the UPDATE statement. In a sequenced update operation, the `WM_VALID.ValidTill` value for the row is changed to the `ValidFrom` timestamp of the current session valid time range, and a new row is created in which the `WM_VALID` period reflects the current session valid time range. Sequenced updates ensure that no duplicate records are created by an UPDATE statement, because the `WM_VALID` column values are different.

Example 3-13 shows a sequenced update operation, in which employee Baxter is given a raise. Before the update, there is one row for Baxter, with a salary of 40000 and a valid time period from 01-Jan-2000 until changed.

Example 3-13 Sequenced Update Operation

    -- Update the salary for an existing employee. Perform "sequenced" update, so
    -- that existing time-related information is preserved. This results in two rows
    -- for Baxter.
    -- First, set valid time to the intended range for Baxter's raise.
    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-2003', 'MM-DD-YYYY'),
      DBMS_WM.UNTIL_CHANGED);
    -- Give Baxter a raise, effective 01-Jan-2003 until changed.
    UPDATE employees SET salary = 45000 WHERE name = 'Baxter';

The update operation in Example 3-13 modifies the `WM_VALID` value of the existing row and creates a new row with the new salary value and the `WM_VALID` value reflecting the session valid time range, as shown by the following statements:

    -- Set valid time to encompass virtually all time.
    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-1900', 'MM-DD-YYYY'), TO_DATE('01-02-9999', 'MM-DD-YYYY'));

    -- See what data exists for Baxter.
    SELECT * FROM employees WHERE name = 'Baxter';

    NAME                 SALARY
    ---------------- ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
    Baxter                45000
    WM_PERIOD('01-JAN-2003 12:00:00 -04:00', NULL)

    Baxter                40000
    WM_PERIOD('01-JAN-2000 12:00:00 -04:00', '01-JAN-2003 12:00:00 -04:00')

A sequenced delete operation deletes the portion of a row that falls within the session valid time range; that is, a new row is created in which the `WM_VALID` period reflects the current session valid time range, and then that row is deleted. If the UPDATE statement in Example 3-13 had instead been `DELETE FROM employees WHERE name = 'Baxter';`, the new row for Baxter, valid from 01-Jan-2003 until changed, would have been deleted, but any rows for Baxter valid before 01-Jan-2003 would not be affected. There is no concept of a non-sequenced delete operation; for example, if a valid time was not set in Example 3-13, a delete operation `WHERE name = 'Baxter'` would delete all rows for Baxter.

Sequenced update and delete operations are enabled when a table is version-enabled with valid time support or when valid time support is added to a version-enabled table. However, you can disable support for sequenced update and delete operations (as well as for nonsequenced update operations) by using the [SetWMValidUpdateModeOFF](DBMS_WM-reference.md) procedure, and you can re-enable support by using the [SetWMValidUpdateModeON](DBMS_WM-reference.md) procedure. (Both procedures are described in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .)

A nonsequenced update operation occurs when you specify a change to the `WM_VALID` column in the UPDATE statement. In a nonsequenced update operation, no additional row is created, and the `WM_VALID` column value of the updated row or rows reflects what you specified in the UPDATE statement. You must ensure that a nonsequenced update operation will not result in multiple rows with the same primary key value being valid in the period specified in the UPDATE statement; otherwise, the update fails because of a primary key constraint violation.

If the UPDATE statement in Example 3-13 had been a nonsequenced update operation, the result would have been only one row for Baxter: the existing row would have had the salary set to 45000 and the `WM_VALID` column set to the period specified in the UPDATE statement.

**Parent topic:** Data Manipulation (DML) Operations

##### 3.6.2.2 Insert Operations

When you insert a row into a version-enabled table with valid time support, you can specify a valid time period for the row. If you specify null timestamps for the period, the session valid time period is used.

When a row is inserted into a version-enabled table with valid time support, Workspace Manager checks to ensure that no existing rows with the same primary key value have a valid time range that overlaps the valid time range of the newly inserted row. If such a row is found, an exception is raised. Example 3-14 shows an attempted insert operation that violates a primary key constraint because overlapping valid time periods.

Example 3-14 Insert Operation Failing Because of Overlapping Time Periods

    -- Insert. Should violate primary key constraint, because of overlapping times:
    -- existing Coleman row is valid from 01-Jan-2003 until 31-Dec-9999.
    INSERT INTO employees VALUES(
      'Coleman',
      55000,
      WMSYS.WM_PERIOD(TO_DATE('01-01-2004', 'MM-DD-YYYY'),
                      TO_DATE('12-31-9999', 'MM-DD-YYYY'))
    );
    )
    *
    ERROR at line 6:
    ORA-20010: unique key violation
    ORA-06512: at "WM_DEVELOPER.OVM_INSERT_10", line 1
    ORA-04088: error during execution of trigger 'WM_DEVELOPER.OVM_INSERT_10'

To make the statement in Example 3-14 succeed, first change the WM_VALID.ValidTill attribute for the Coleman row to a timestamp reflecting 01-Jan-2004 or an earlier date.

**Parent topic:** Data Manipulation (DML) Operations

### 3.7 Constraint Management for Valid Time Support

This section describes considerations related to valid time support that affect referential integrity constraints and unique constraints.

- Referential Integrity Constraints
- Unique Constraints

**Parent topic:** Workspace Manager Valid Time Support

#### 3.7.1 Referential Integrity Constraints

If a referential integrity constraint exists between two version-enabled tables that have valid time support, the valid time periods of rows are considered when the constraint is enforced. For example, assume that a `DEPARTMENTS` table has a `MANAGER_ID` column that is a foreign key referencing the `EMPLOYEE_ID` column in an `EMPLOYEES` table (that is, the department manager must be an existing employee). If both tables are version-enabled with valid time support, and if an insert or update operation would result in a new `DEPARTMENTS.MANAGER_ID` value, the operation will fail if the `D``EPARTMENTS.WM_VALID` value is not within the range of the `EMPLOYEES.WM_VALID` value for the employee who is being made the department manager. (That is, the operation will fail if the new department manager is not a valid employee for the time period specified or defaulted for the insert or update operation.)

If either or both tables in a referential integrity constraint are not version-enabled with valid time support, valid time periods are ignored in enforcing the constraint.

**Parent topic:** Constraint Management for Valid Time Support

#### 3.7.2 Unique Constraints

If a unique constraint exists in a version-enabled table with valid time support, the valid time periods of rows are considered when the constraint is enforced. For example, assume that an `EMPLOYEES` table has an `EMPLOYEE_ID` column that has a unique constraint. If an insert or update operation would result in a new `EMPLOYEE_ID` value that is the same as an existing `EMPLOYEE_ID` value, the operation will fail if the `WM_VALID` values of the existing and inserted rows overlap. (That is, the operation will fail if the new employee and an existing employee have the same ID numbers and their rows are both valid at any given time. However, the operation will succeed if the valid time periods for the two employees do not overlap.)

**Parent topic:** Constraint Management for Valid Time Support

### 3.8 Locking with Valid Time Support

If a row in a version-enabled table with valid time support is locked, it is automatically locked for its entire valid time period. There is no way to lock a row for a specified time period.

Any updates in a pessimistically locked workspace will lock the rows seen from an ancestor workspace as the updates are performed in the workspace. The locked rows in ancestor workspaces will not be further updatable in their valid time periods as long as they are locked.

For an explanation of Workspace Manager locking, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).

**Parent topic:** Workspace Manager Valid Time Support

### 3.9 Static Data Dictionary Views Affected by Valid Time Support

This section describes the effect on valid time support on Workspace Manager static data dictionary views.

These views are documented in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) .

- xxx_CONF Views and Valid Time Support
- xxx_DIFF Views and Valid Time Support
- xxx_HIST Views and Valid Time Support
- xxx_LOCK Views and Valid Time Support
- xxx_MW Views and Valid Time Support

**Parent topic:** Workspace Manager Valid Time Support

#### 3.9.1 xxx_CONF Views and Valid Time Support

For a versioned-enabled table with valid time support, the xxx\_CONF view (described in [xxx_CONF Views](workspace-manager-views.md)) will include any temporal conflicts. Such a conflict results when the valid time of a row in a parent workspace, containing the same key as a row in its child workspace, overlaps with the valid time of that row in the child workspace. Setting the session context valid time has no effect on the results of the xxx\_CONF views, because all applicable conflicts are displayed for the entire time dimension.

For a version-enabled table with valid time support, a column named `WM_VALID`, of type `WM_PERIOD`, is added to the xxx\_CONF view, to indicate the time period during which the row is valid. A column named `WM_CONFLICTPERIOD`, of type `WM_PERIOD`, is also added to the view, to indicate the overlapping period of the rows for which conflicts were detected.

**Parent topic:** Static Data Dictionary Views Affected by Valid Time Support

#### 3.9.2 xxx_DIFF Views and Valid Time Support

For a version-enabled table with valid time support, the xxx\_DIFF view (described in [xxx_DIFF Views](workspace-manager-views.md)) will include temporal differences for a primary key between two distinct workspaces or savepoints. Such a difference occurs when a row is modified (inserted, updated, or deleted) in either a parent or child workspace. If two rows with the same primary key value are modified in both a parent and child workspace, the two rows are only correlated in the xxx\_DIFF view when the valid time ranges of the rows overlap. Setting the session context valid time has no effect on the results of the xxx\_DIFF views, because all applicable differences are displayed for the entire time dimension.

For a version-enabled table with valid time support, a column named `WM_VALID`, of type `WM_PERIOD`, is added to the xxx\_DIFF view, to indicate the time period during which the row is valid. A column named `WM_DIFFPERIOD`, of type `WM_PERIOD`, is also added to the view, to indicate the overlapping period of the rows for which a difference was detected.

**Parent topic:** Static Data Dictionary Views Affected by Valid Time Support

#### 3.9.3 xxx_HIST Views and Valid Time Support

The xxx\_HIST views (described in [xxx_HIST Views](workspace-manager-views.md)) include information about both valid times and transaction times. It also includes audit information, such as the name of the user that created the row. For a version-enabled table with valid time support, a column named `WM_VALID`, of type `WM_PERIOD`, is added to the xxx\_HIST view, to indicate the time period during which the row is valid.

**Parent topic:** Static Data Dictionary Views Affected by Valid Time Support

#### 3.9.4 xxx_LOCK Views and Valid Time Support

For a version-enabled table with valid time support, a column named `WM_VALID`, of type `WM_PERIOD`, is added to the xxx\_LOCK view (described in [xxx_LOCK Views](workspace-manager-views.md)), to indicate the time period during which the row is valid. The row is locked for its entire valid time period, so this is also the locking period.

**Parent topic:** Static Data Dictionary Views Affected by Valid Time Support

#### 3.9.5 xxx_MW Views and Valid Time Support

For a version-enabled table with valid time support, a column named `WM_VALID`, of type `WM_PERIOD`, is added to the xxx\_MW view (described in [xxx_MW Views](workspace-manager-views.md)), to indicate the time period during which the row is valid. To see only the rows that are valid during a specific period, use the WM_OVERLAPS operator.

**Parent topic:** Static Data Dictionary Views Affected by Valid Time Support

### 3.10 Adding Valid Time Support to an Existing Table

You can add valid time support to an existing version-enabled table.

To do so, use the [AlterVersionedTable](DBMS_WM-reference.md) procedure. You can specify a valid time period to be set in the WM_VALID column of all existing rows, or you can accept the default period of the current timestamp until changed.

Example 3-15 creates a table named `MY_TABLE`, version-enables it without valid time support, and then adds valid time support. After the valid time support is added, the `WM_VALID` column contains the default valid time period.

Example 3-15 Adding Valid Time Support to an Existing Version-Enabled Table

    CREATE TABLE my_table (id NUMBER PRIMARY KEY);
    EXECUTE DBMS_WM.EnableVersioning ('my_table');
    INSERT INTO my_table VALUES (1);
    SELECT * FROM my_table;

            ID
    ----------
             1

    EXECUTE DBMS_WM.AlterVersionedTable('my_table', 'ADD_VALID_TIME');
    SELECT * FROM my_table;

            ID
    ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
             1
    WM_PERIOD('09-JUN-2003 10:04:13 -04:00', NULL)

**Parent topic:** Workspace Manager Valid Time Support

### 3.11 Merging and Refreshing Workspaces for Tables with Valid Time Support

When tables that have valid time support are merged or refreshed, you can determine the resulting rows by considering the distinct cases when there is an intersection between rows for the same primary key value.

To determine if two row intersect, you can use the WM_OVERLAPS operator.

In the `validTill` cases shown in Table 3-3:

- For a merge operation, the target workspace is the parent workspace.

- For a refresh operation, the target workspace is the child workspace of the specified workspace.

- Because of the intersecting nature of the rows, conflict resolution was performed before the merge or refresh operation. (A single source row might conflict with multiple target rows, and a single target row might conflict with multiple source rows.)

Table 3-3 validTill Values and Intersection Result from Merge or Refresh Operation

| validTill Values                                                                                                                     | Intersection Result                                                                                                            |
|:-------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| Both the source and the target rows have a `validTill` value that is not `DBMS_WM.UNTIL_CHANGED`.                                    | The intersecting portion of the row is modified in the target workspace to equal that of the source row.                       |
| The `validTill` value of the source row is not `DBMS_WM.UNTIL_CHANGED`, and the value for the target is `DBMS_WM.UNTIL_CHANGED`.     | The intersecting portion of the row is modified and the resulting row has a `validTill` value equal to that of the source row. |
| The `validTill` value of the source row is `DBMS_WM.UNTIL_CHANGED`, and the value for the target row is not `DBMS_WM.UNTIL_CHANGED`. | The intersecting portion of the row is modified and the resulting row has a `validTill` value equal to that of the target row. |
| The `validTill` value of both the source and target rows are both `DBMS_WM.UNTIL_CHANGED`.                                           | The intersecting portion is modified and the resulting row has a `validTill` value of DBMS_WM.UNTIL_CHANGED.                   |

For all cases in Table 3-3, any non-intersecting portion of the target row is left unchanged. When there is no overlapping row in the target workspace, then no special consideration needs to be made; the row is merged or refreshed as is without any additional changes.

**Parent topic:** Workspace Manager Valid Time Support
