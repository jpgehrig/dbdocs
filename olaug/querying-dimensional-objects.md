Oracle OLAP adds power to your SQL applications by providing extensive analytic content and fast query response times. A SQL query interface enables any application to query cubes and dimensions without any knowledge of OLAP.

The OLAP option automatically generates a set of relational views on cubes, dimensions, and hierarchies. SQL applications query these views to display the information-rich contents of these objects to analysts and decision makers. You can also create custom views that follow the structure expected by your applications, using the system-generated views like base tables.

In this chapter, you learn the basic methods for querying dimensional objects in SQL. It contains the following topics:

- Exploring the OLAP Views

- Creating Basic Queries

- Creating Hierarchical Queries

- Using Calculations in Queries

- Using Attributes for Aggregation

- Joining Cubes to Tables and Views

- Viewing Execution Plans

- Querying the Data Dictionary

**See Also:**

- "[Developing Reports and Dashboards Using SQL Tools and Application Builders](overview.md)" for a sample dashboard created using Oracle Application Express

- "[Overview of the Dimensional Data Model](overview.md)" for a discussion of cubes, dimensions, and hierarchies

### 4.1 Exploring the OLAP Views

The system-generated views are created in the same schema as the analytic workspace. Oracle OLAP provides three types of views:

- Cube views

- Dimension views

- Hierarchy views

These views are related in the same way as fact and dimension tables are in a star schema. Cube views serve the same function as fact tables, and hierarchy views and dimension views serve the same function as dimension tables. Typical queries join a cube view with either a hierarchy view or a dimension view.

#### 4.1.1 Cube Views

Each cube has a cube view that presents the data for all the measures and calculated measures in the cube. You can use a cube view like a fact table in a star or snowflake schema. However, the cube view contains all the summary data in addition to the detail level data.

##### 4.1.1.1 Discovering the Names of the Cube Views

The default name for a cube view is `cube``_VIEW`. To find the view for `UNITS_CUBE` in your schema, you might issue a query like this one:

    SELECT view_name FROM user_views WHERE view_name LIKE 'UNITS_CUBE%';

    VIEW_NAME
    ------------------------------
    UNITS_CUBE_VIEW

The next query returns the names of all the cube views in your schema from `USER_CUBE_VIEWS`:

    SELECT view_name FROM user_cube_views;

    VIEW_NAME
    ------------------------------
    UNITS_CUBE_VIEW
    PRICE_CUBE_VIEW

##### 4.1.1.2 Discovering the Columns of a Cube View

Like a fact table, a cube view contains a column for each measure, calculated measure, and dimension in the cube. In the following example, `UNITS_CUBE_VIEW` has columns for the `SALES`, `UNITS`, and `COST` measures, for several calculated measures on `SALES`, and for the `TIME`, `CUSTOMER`, `PRODUCT`, and `CHANNEL` dimensions.

    DESCRIBE units_cube_view
    Name                                      Null?    Type
    ----------------------------------------- -------- ----------------------------
    SALES                                              NUMBER
    UNITS                                              NUMBER
    COST                                               NUMBER
    SALES_PP                                           NUMBER
    SALES_CHG_PP                                       NUMBER
    SALES_PCTCHG_PP                                    NUMBER
    SALES_PROD_SHARE_PARENT                            NUMBER
    SALES_PROD_SHARE_TOTAL                             NUMBER
    SALES_PROD_RANK_PARENT_PP                          NUMBER
    TIME                                               VARCHAR2(100)
    CUSTOMER                                           VARCHAR2(100)
    PRODUCT                                            VARCHAR2(100)
    CHANNEL                                            VARCHAR2(100)

The `USER_CUBE_VIEW_COLUMNS` data dictionary view describes the columns of a cube view, as shown by the following query.

    SELECT column_name, column_type FROM user_cube_view_columns
         WHERE view_name = 'UNITS_CUBE_VIEW';

    COLUMN_NAME                    COLUMN_TYPE
    ------------------------------ --------------
    SALES                          MEASURE
    UNITS                          MEASURE
    COST                           MEASURE
    SALES_PP                       MEASURE
    SALES_CHG_PP                   MEASURE
    SALES_PCTCHG_PP                MEASURE
    SALES_PROD_SHARE_PARENT        MEASURE
    SALES_PROD_SHARE_TOTAL         MEASURE
    SALES_PROD_RANK_PARENT_PP      MEASURE
    TIME                           KEY
    CUSTOMER                       KEY
    PRODUCT                        KEY
    CHANNEL                        KEY

    13 rows selected.

##### 4.1.1.3 Displaying the Contents of a Cube View

You can display the contents of a cube view quickly with a query like this one. All levels of the data are contained in the cube, from the detail level to the top.

    SELECT sales, units, time, customer, product, channel
         FROM units_cube_view WHERE ROWNUM < 15;

         SALES      UNITS TIME       CUSTOMER   PRODUCT    CHANNEL
    ---------- ---------- ---------- ---------- ---------- --------
    1120292752    4000968 TOTAL      TOTAL      TOTAL      TOTAL
     134109248     330425 CY1999     TOTAL      TOTAL      TOTAL
     130276514     534069 CY2003     TOTAL      TOTAL      TOTAL
     100870877     253816 CY1998     TOTAL      TOTAL      TOTAL
     136986572     565718 CY2005     TOTAL      TOTAL      TOTAL
     140138317     584929 CY2006     TOTAL      TOTAL      TOTAL
     144290686     587419 CY2004     TOTAL      TOTAL      TOTAL
     124173522     364233 CY2000     TOTAL      TOTAL      TOTAL
      92515295     364965 CY2002     TOTAL      TOTAL      TOTAL
     116931722     415394 CY2001     TOTAL      TOTAL      TOTAL
    31522409.5      88484 CY2000.Q1  TOTAL      TOTAL      TOTAL
    27798426.6      97346 CY2001.Q2  TOTAL      TOTAL      TOTAL
    29691668.2     105704 CY2001.Q3  TOTAL      TOTAL      TOTAL
    32617248.6     138953 CY2005.Q3  TOTAL      TOTAL      TOTAL

    14 rows selected.

#### 4.1.2 Dimension and Hierarchy Views

Each dimension has one dimension view plus a hierarchy view for each hierarchy associated with the dimension. For example, a Time dimension might have these three views:

- Time dimension view

- Calendar hierarchy view

- Fiscal hierarchy view

You can use dimension views and hierarchy views like dimension tables in a star schema.

##### 4.1.2.1 Discovering the Names of Dimension and Hierarchy Views

`USER_CUBE_DIM_VIEWS` identifies the dimension views for all dimensions. The default name for a dimension view is `dimension``_VIEW`.

    SELECT * FROM user_cube_dim_views;

    DIMENSION_NAME                 VIEW_NAME
    ------------------------------ ------------------------------
    PRODUCT                        PRODUCT_VIEW
    CUSTOMER                       CUSTOMER_VIEW
    CHANNEL                        CHANNEL_VIEW
    TIME                           TIME_VIEW

`USER_CUBE_HIER_VIEWS` identifies the hierarchy views for all the dimensions. For a hierarchy view, the default name is `dimension_hierarchy``_VIEW`. The following query returns the dimension, hierarchy, and view names.

    SELECT * FROM user_cube_hier_views ORDER BY dimension_name;

    DIMENSION_NAME  HIERARCHY_NAME  VIEW_NAME
    --------------- --------------- ------------------------------
    CHANNEL         PRIMARY         CHANNEL_PRIMARY_VIEW
    CUSTOMER        MARKET          CUSTOMER_MARKET_VIEW
    CUSTOMER        SHIPMENTS       CUSTOMER_SHIPMENTS_VIEW
    PRODUCT         PRIMARY         PRODUCT_PRIMARY_VIEW
    TIME            FISCAL          TIME_FISCAL_VIEW
    TIME            CALENDAR        TIME_CALENDAR_VIEW

##### 4.1.2.2 Discovering the Columns of a Dimension View

Like a dimension table, a dimension view contains a key column, level name, level keys for every level of every hierarchy associated with the dimension, and attribute columns. In the following example, `TIME_VIEW` has a column for the dimension keys, the level name, and the dimension attributes.

    DESCRIBE time_view
    Name                                      Null?    Type
    ----------------------------------------- -------- ----------------------------
    DIM_KEY                                            VARCHAR2(100)
    LEVEL_NAME                                         VARCHAR2(30)
    DIM_ORDER                                          NUMBER
    END_DATE                                           DATE
    LONG_DESCRIPTION                                   VARCHAR2(100)
    SHORT_DESCRIPTION                                  VARCHAR2(100)
    TIME_SPAN                                          NUMBER

`USER_CUBE_DIM_VIEW_COLUMNS` describes the information in each column, as shown in this query.

    SELECT column_name, column_type FROM user_cube_dim_view_columns
         WHERE view_name ='TIME_VIEW';

    COLUMN_NAME                    COLUMN_TYPE
    ------------------------------ --------------------
    DIM_KEY                        KEY
    LEVEL_NAME                     LEVEL_NAME
    DIM_ORDER                      DIM_ORDER
    END_DATE                       ATTRIBUTE
    TIME_SPAN                      ATTRIBUTE
    LONG_DESCRIPTION               ATTRIBUTE
    SHORT_DESCRIPTION              ATTRIBUTE

##### 4.1.2.3 Displaying the Contents of a Dimension View

The following query displays the level and attributes of each dimension key.

    SELECT dim_key, level_name, long_description description, time_span, end_date
         FROM time_view WHERE dim_key LIKE '%2005%';

    DIM_KEY      LEVEL_NAME           DESCRIPTION   TIME_SPAN END_DATE
    ------------ -------------------- ------------ ---------- ---------
    CY2005       CALENDAR_YEAR        2005                365 31-DEC-05
    CY2005.Q2    CALENDAR_QUARTER     Q2.05                91 30-JUN-05
    CY2005.Q4    CALENDAR_QUARTER     Q4.05                92 31-DEC-05
    CY2005.Q3    CALENDAR_QUARTER     Q3.05                92 30-SEP-05
    CY2005.Q1    CALENDAR_QUARTER     Q1.05                90 31-MAR-05
    2005.01      MONTH                JAN-05               31 31-JAN-05
    2005.05      MONTH                MAY-05               31 31-MAY-05
    2005.07      MONTH                JUL-05               31 31-JUL-05
    2005.03      MONTH                MAR-05               31 31-MAR-05
    2005.04      MONTH                APR-05               30 30-APR-05
    2005.08      MONTH                AUG-05               31 31-AUG-05
    2005.09      MONTH                SEP-05               30 30-SEP-05
    2005.02      MONTH                FEB-05               28 28-FEB-05
    2005.11      MONTH                NOV-05               30 30-NOV-05
    2005.06      MONTH                JUN-05               30 30-JUN-05
    2005.10      MONTH                OCT-05               31 31-OCT-05
    2005.12      MONTH                DEC-05               31 31-DEC-05
    FY2005       FISCAL_YEAR          FY2005              365 30-JUN-05
    FY2005.Q4    FISCAL_QUARTER       Q4 FY-05             91 30-JUN-05
    FY2005.Q1    FISCAL_QUARTER       Q1 FY-05             92 30-SEP-04
    FY2005.Q2    FISCAL_QUARTER       Q2 FY-05             92 31-DEC-04
    FY2005.Q3    FISCAL_QUARTER       Q3 FY-05             90 31-MAR-05

    22 rows selected.

##### 4.1.2.4 Discovering the Columns of a Hierarchy View

Like the dimension views, the hierarchy views also contain columns for the dimension key, level name, and level keys. However, all of the rows and columns are associated with the dimension keys that belong to the hierarchy.

    DESCRIBE time_calendar_view
    Name                                      Null?    Type
    ----------------------------------------- -------- ----------------------------
    DIM_KEY                                            VARCHAR2(100)
    LEVEL_NAME                                         VARCHAR2(30)
    DIM_ORDER                                          NUMBER
    HIER_ORDER                                         NUMBER
    LONG_DESCRIPTION                                   VARCHAR2(100)
    SHORT_DESCRIPTION                                  VARCHAR2(100)
    END_DATE                                           DATE
    TIME_SPAN                                          NUMBER
    PARENT                                             VARCHAR2(100)
    TOTAL                                              VARCHAR2(100)
    CALENDAR_YEAR                                      VARCHAR2(100)
    CALENDAR_QUARTER                                   VARCHAR2(100)
    MONTH                                              VARCHAR2(100)

##### 4.1.2.5 Displaying the Contents of a Hierarchy View

The following query displays the dimension keys, parent key, and the full ancestry for calendar year 2005.

    SELECT dim_key, long_description description, parent, calendar_year year,
           calendar_quarter quarter, month FROM time_calendar_view
           WHERE calendar_year='CY2005'
           ORDER BY level_name, end_date;

    DIM_KEY      DESCRIPTION  PARENT       YEAR         QUARTER      MONTH
    ------------ ------------ ------------ ------------ ------------ ------------
    CY2005.Q1    Q1.05        CY2005       CY2005       CY2005.Q1
    CY2005.Q2    Q2.05        CY2005       CY2005       CY2005.Q2
    CY2005.Q3    Q3.05        CY2005       CY2005       CY2005.Q3
    CY2005.Q4    Q4.05        CY2005       CY2005       CY2005.Q4
    CY2005       2005         TOTAL        CY2005
    2005.01      JAN-05       CY2005.Q1    CY2005       CY2005.Q1    2005.01
    2005.02      FEB-05       CY2005.Q1    CY2005       CY2005.Q1    2005.02
    2005.03      MAR-05       CY2005.Q1    CY2005       CY2005.Q1    2005.03
    2005.04      APR-05       CY2005.Q2    CY2005       CY2005.Q2    2005.04
    2005.05      MAY-05       CY2005.Q2    CY2005       CY2005.Q2    2005.05
    2005.06      JUN-05       CY2005.Q2    CY2005       CY2005.Q2    2005.06
    2005.07      JUL-05       CY2005.Q3    CY2005       CY2005.Q3    2005.07
    2005.08      AUG-05       CY2005.Q3    CY2005       CY2005.Q3    2005.08
    2005.09      SEP-05       CY2005.Q3    CY2005       CY2005.Q3    2005.09
    2005.10      OCT-05       CY2005.Q4    CY2005       CY2005.Q4    2005.10
    2005.11      NOV-05       CY2005.Q4    CY2005       CY2005.Q4    2005.11
    2005.12      DEC-05       CY2005.Q4    CY2005       CY2005.Q4    2005.12

    17 rows selected.

### 4.2 Creating Basic Queries

Querying a cube is similar to querying a star schema. In a star schema, you join a fact table to a dimension table. The fact table provides the numeric business measures, and the dimension table provides descriptive attributes that give meaning to the data. Similarly, you join a cube view with either a dimension view or a hierarchy view to provide fully identified and meaningful data to your users.

For dimensions with no hierarchies, use the dimension views in your queries. For dimensions with hierarchies, use the hierarchy views, because they contain more information than the dimension views.

When querying a cube, remember these guidelines:

- Apply a filter to every dimension.

  The cube contains both detail level and aggregated data. A query with an unfiltered dimension typically returns more data than users need, which negatively impacts performance.

- Let the cube aggregate the data.

  Because the aggregations are calculated in the cube, a typical query does not need a `GROUP BY` clause. Simply select the aggregations you want by using the appropriate filters on the dimension keys or attributes.

#### 4.2.1 Applying a Filter to Every Dimension

To create a level filter, you must know the names of the dimension levels. You can easily acquire them by querying the dimension or hierarchy views:

    SELECT DISTINCT level_name FROM time_calendar_view;

    LEVEL_NAME
    ------------------------------
    CALENDAR_YEAR
    CALENDAR_QUARTER
    MONTH
    TOTAL

Several data dictionary views list the names of the levels. The following example queries `USER_CUBE_HIER_LEVELS`.

    SELECT level_name FROM user_cube_hier_levels
         WHERE dimension_name = 'TIME' AND hierarchy_name ='CALENDAR';

    LEVEL_NAME
    --------------------
    TOTAL
    CALENDAR_YEAR
    CALENDAR_QUARTER
    MONTH

Example 4-1 Displaying Aggregates at All Levels of Time

To see the importance of applying a filter to every dimension, consider the query in this example, which has no filter on the time dimension.

    /* Select key descriptions and facts */
    SELECT t.long_description time,
         ROUND(f.sales) sales
    /* From dimension views and cube view */
      FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
    /* No filter on Time */
      WHERE p.level_name = 'TOTAL'
         AND cu.level_name = 'TOTAL'
         AND ch.level_name = 'TOTAL'
    /* Join dimension views to cube view */
         AND t.dim_key = f.time
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
      ORDER BY t.end_date;

Without a filter on the Time dimension, the query returns values for every level of time. This is more data than users typically want to see, and the volume of data returned can negatively impact performance.

    TIME            SALES
    ---------- ----------
    JAN-98        8338545
    FEB-98        7972132
    Q1.98        24538588
    MAR-98        8227911
    APR-98        8470315
    MAY-98        8160573
    JUN-98        8362386
    Q2.98        24993273
    JUL-98        8296226
    AUG-98        8377587
    SEP-98        8406728
    Q3.98        25080541
    OCT-98        8316169
    NOV-98        8984156
    Q4.98        26258474
    1998        100870877
                    .
                    .
                    .

Example 4-2 Basic Cube View Query

Now consider the results when a filter restricts Time to yearly data. This example shows a basic query. It selects the Sales measure from `UNITS_CUBE_VIEW`, and joins the keys from the cube view to the hierarchy views to get descriptions of the keys.

    /* Select key descriptions and facts */
    SELECT t.long_description time,
         ROUND(f.sales) sales
    /* From dimension views and cube view */
      FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
    /* Create level filters */
      WHERE t.level_name = 'CALENDAR_YEAR'
         AND p.level_name = 'TOTAL'
         AND cu.level_name = 'TOTAL'
         AND ch.level_name = 'TOTAL'
    /* Join dimension views to cube view */
         AND t.dim_key = f.time
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
      ORDER BY t.end_date;

The example selects the following rows. For `CUSTOMER`, `PRODUCT`, and `CHANNEL`, only one value is at the top level. `TIME` has a value for each calendar year.

    TIME          SALES
    -------- ----------
    1998      100870877
    1999      134109248
    2000      124173522
    2001      116931722
    2002       92515295
    2003      130276514
    2004      144290686
    2005      136986572
    2006      140138317

Example 4-3 Selecting Data with Attribute Filters

Dimension attributes also provide a useful way to select the data for a query. The `WHERE` clause in this example uses attributes values to filter all of the dimensions.

    /* Select key descriptions and facts */
    SELECT t.long_description time,
         p.long_description product,
         cu.long_description customer,
         ch.long_description channel,
         ROUND(f.sales) sales
    /* From dimension views and cube view */
    FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
    /* Create attribute filters */
    WHERE t.long_description in ('2005', '2006')
        AND p.package = 'Laptop Value Pack'
        AND cu.long_description LIKE '%Boston%'
        AND ch.long_description = 'Internet'
    /* Join dimension views to cube view */
        AND t.dim_key = f.time
        AND p.dim_key = f.product
        AND cu.dim_key = f.customer
        AND ch.dim_key = f.channel
    ORDER BY time, customer;

The query selects two calendar years, the products in the Laptop Value Pack, the customers in Boston, and the Internet channel.

    TIME   PRODUCT                        CUSTOMER              CHANNEL       SALES
    ------ ------------------------------ --------------------- -------- ----------
    2005   Laptop carrying case           KOSH Entrpr Boston    Internet       5936
    2005   56Kbps V.92 Type II Fax/Modem  KOSH Entrpr Boston    Internet      45285
    2005   Internal 48X CD-ROM            KOSH Entrpr Boston    Internet       2828
    2005   Standard Mouse                 KOSH Entrpr Boston    Internet        638
    2005   Envoy Standard                 Warren Systems Boston Internet      19359
    2005   Laptop carrying case           Warren Systems Boston Internet      13434
    2005   Standard Mouse                 Warren Systems Boston Internet        130
    2006   Standard Mouse                 KOSH Entrpr Boston    Internet        555
    2006   Laptop carrying case           KOSH Entrpr Boston    Internet       6357
    2006   56Kbps V.92 Type II Fax/Modem  KOSH Entrpr Boston    Internet      38042
    2006   Internal 48X CD-ROM            KOSH Entrpr Boston    Internet       3343
    2006   Envoy Standard                 Warren Systems Boston Internet      24198
    2006   Laptop carrying case           Warren Systems Boston Internet      13153
    2006   Standard Mouse                 Warren Systems Boston Internet         83

    14 rows selected.

#### 4.2.2 Allowing the Cube to Aggregate the Data

A cube contains all of the aggregate data. As shown in this chapter, a query against a cube just selects the aggregate data. It does not calculate the values.

The following is a basic query against a fact table:

    /* Querying a fact table */
    SELECT t.calendar_year_dsc time,
         SUM(f.sales) sales
      FROM time_dim t, units_fact f
      WHERE t.calendar_year_dsc IN ('2005', '2006')
         AND t.month_id = f.month_id
      GROUP BY t.calendar_year_dsc;

The next query fetches the exact same results from a cube using filters:

    /* Querying a cube */
    SELECT t.long_description time, f.sales sales
      FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
    /* Apply filters to every dimension */
      WHERE t.long_description IN ('2005', '2006')
         AND p.level_name = 'TOTAL'
         AND cu.level_name = 'TOTAL'
         AND ch.level_name = 'TOTAL'
    /* Join dimension views to cube view */
         AND t.dim_key = f.TIME
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
      ORDER BY time;

Both queries return these results:

    TIME       SALES
    ----- ----------
    2005   136986572
    2006   140138317

The query against the cube does not compute the aggregate values with a `SUM` operator and `GROUP BY` clause. Because the aggregates exist in the cube, this would re-aggregate previously aggregated data. Instead, the query selects the aggregates directly from the cube and specifies the desired aggregates by applying the appropriate filter to each dimension.

#### 4.2.3 Query Processing

The most efficient queries allow the OLAP engine to filter the data, so that the minimum number of rows required by the query are returned to SQL.

The following are among the `WHERE` clause operations that are pushed into the OLAP engine for processing:

- `=`

- `!=`

- `>`

- `!>`

- `<`

- `!<`

- `IN`

- `NOT IN`

- `IS NULL`

- `LIKE`

- `NOT LIKE`

The OLAP engine also processes nested character functions, including `INSTR`, `LENGTH`, `NVL`, `LOWER`, `UPPER`, `LTRIM`, `RTRIM`, `TRIM`, `LPAD`, `RPAD`, and `SUBSTR`.

SQL processes other operations and functions in the `WHERE` clause, and all operations in other parts of the `SELECT` syntax.

### 4.3 Creating Hierarchical Queries

Drilling is an important capability in business analysis. In a dashboard or an application, users click a dimension key to change the selection of data. Decision makers frequently want to drill down to see the contributors to a data value, or drill up to see how a particular data value contributes to the whole. For example, the Boston regional sales manager might start at total Boston sales, drill down to see the contributions of each sales representative, then drill up to see how the Boston region contributes to the New England sales total.

The hierarchy views include a `PARENT` column that identifies the parent of every dimension key. This column encapsulates all of the hierarchical information of the dimension: If you know the parent of every key, then you can derive the ancestors, the children, and the descendants.

For level-based hierarchies, the `LEVEL_NAME` column supplements this information by providing a convenient way to identify all the keys at the same depth in the hierarchy, from the top to the base. For value-based hierarchies, the `PARENT` column provides all the information about the hierarchy.

**See Also:**

[Developing Reports and Dashboards](developing-reports-and-dashboards.md) about using bind variables to support drilling

#### 4.3.1 Drilling Down to Children

You can use the `PARENT` column of a hierarchy view to select only the children of a particular value. The following `WHERE` clause selects the children of calendar year `2005`.

    /* Select children of calendar year 2005 */
    WHERE  t.parent = 'CY2005'
       AND p.dim_key = 'TOTAL'
       AND cu.dim_key = 'TOTAL'
       AND ch.dim_key = 'TOTAL'

The query drills down from Year to Quarter. The four quarters `Q1-05` to `Q4-05` are the children of year `CY2005` in the Calendar hierarchy.

    TIME          SALES
    -------- ----------
    Q1.05      31381338
    Q2.05      37642741
    Q3.05      32617249
    Q4.05      35345244

#### 4.3.2 Drilling Up to Parents

The `PARENT` column of a hierarchy view identifies the parent of each dimension key. Columns of level keys identify the full heritage. The following `WHERE` clause selects the parent of a Time key based on its `LONG_DESCRIPTION` attribute.

    /* Select the parent of a Time key*/
    WHERE t.dim_key =
       (SELECT DISTINCT parent
          FROM time_calendar_view
          WHERE long_description='JAN-05')
       AND p.dim_key= 'TOTAL'
       AND cu.dim_key = 'TOTAL'
       AND ch.dim_key = 'TOTAL'

The query drills up from Month to Quarter. The parent of month `JAN-05` is the quarter `Q1-05` in the Calendar hierarchy.

    TIME          SALES
    -------- ----------
    Q1.05      31381338

#### 4.3.3 Drilling Down to Descendants

The following `WHERE` clause selects the descendants of calendar year `2005` by selecting the rows with a `LEVEL_NAME` of `MONTH` and a `CALENDAR_YEAR` of `CY2005`.

    /* Select Time level and ancestor */
    WHERE t.level_name = 'MONTH'
        AND t.calendar_year = 'CY2005'
        AND p.dim_key = 'TOTAL'
        AND cu.dim_key = 'TOTAL'
        AND ch.dim_key = 'TOTAL'

The query drills down two levels, from year to quarter to month. The 12 months `Jan-05` to `Dec-05` are the descendants of year `2005` in the Calendar hierarchy.

    TIME          SALES
    -------- ----------
    JAN-05     12093518
    FEB-05     10103162
    MAR-05      9184658
    APR-05      9185964
    MAY-05     11640216
    JUN-05     16816561
    JUL-05     11110903
    AUG-05      9475807
    SEP-05     12030538
    OCT-05     11135032
    NOV-05     11067754
    DEC-05     13142459

#### 4.3.4 Drilling Up to Ancestors

The hierarchy views provide the full ancestry of each dimension key, as shown in "Displaying the Contents of a Hierarchy View". The following `WHERE` clause uses the `CALENDAR_YEAR` level key column to identify the ancestor of a `MONTH` dimension key.

    /* Select the ancestor of a Time key based on its Long Description attribute */
    WHERE t.dim_key =
       (SELECT calendar_year
          FROM time_calendar_view
          WHERE long_description = 'JAN-05')
       AND p.dim_key = 'TOTAL'
       AND cu.dim_key = 'TOTAL'
       AND ch.dim_key = 'TOTAL'

The query drills up two levels from month to quarter to year. The ancestor of month `Jan-05` is the year `2005` in the Calendar hierarchy.

    TIME          SALES
    -------- ----------
    2005      136986572

### 4.4 Using Calculations in Queries

A DBA can create calculated measures in Analytic Workspace Manager, so they are available to all applications. This not only simplifies application development, but ensures that all applications use the same name for the same calculation.

Nonetheless, you may want to develop queries that include your own calculations. In this case, you can use an inner query to select aggregate data from the cube, then perform calculations in an outer query. You can select data from cubes that use any type of aggregation operators, and you can use any functions or operators in the query. You must ensure only that you select the data from the cube at the appropriate levels for the calculation, and that the combination of operators in the cube and in the query create the calculation you want.

Example 4-4 Calculating Average Sales Across Customers

This example shows a query that answers the question, What was the average sales of Sentinel Standard computers to Government customers for the third quarter of fiscal year 2005. `UNITS_CUBE` is summed over all dimensions, so that `FY2005.Q3` is a total for July, August, and September. The inner query extracts the data for these months, and the outer query uses the `MIN`, `MAX`, and `AVG` operators and a `GROUP BY` clause to calculate the averages.

    SELECT customer, ROUND(MIN(sales)) minimum, ROUND(MAX(sales)) maximum,
       ROUND(AVG(sales)) average
    FROM
       (SELECT cu.long_description customer,
           t.month_long_description time
           f.sales sales
       FROM time_fiscal_view t,
         product_primary_view p,
         customer_market_view cu,
         channel_primary_view ch,
         units_cube_view f
       WHERE t.parent = 'FY2005.Q3'
         AND p.dim_key = 'SENT STD'
         AND cu.parent = 'GOV'
         AND ch.level_name = 'TOTAL'
         AND t.dim_key = f.time
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
       )
    GROUP BY customer
    ORDER BY customer;

This is the data extracted from the cube by the inner query:

    CUSTOMER                                 TIME          SALES
    ---------------------------------------- -------- ----------
    Dept. of Labor                           JAN-05      1553.26
    Dept. of Labor                           MAR-05       1555.6
    Ministry of Intl Trade                   JAN-05      1553.26
    Ministry of Intl Trade                   FEB-05      1554.56
    Ministry of Intl Trade                   MAR-05       1555.6
    Royal Air Force                          JAN-05      1553.26
    Royal Air Force                          FEB-05      6218.23
    UK Environmental Department              JAN-05      4659.78
    UK Environmental Department              FEB-05      3109.12

The outer query calculates the minimum, maximum, and average sales for each customer:

    CUSTOMER                          MINIMUM    MAXIMUM    AVERAGE
    ------------------------------ ---------- ---------- ----------
    Dept. of Labor                       1553       1556       1554
    Ministry of Intl Trade               1553       1556       1554
    Royal Air Force                      1553       6218       3886
    UK Environmental Department          3109       4660       3884

### 4.5 Using Attributes for Aggregation

An OLAP cube aggregates the data within its hierarchies, using the parent-child relationships revealed in the hierarchy views. The OLAP engine does not calculate aggregates over dimension attribute values.

Nonetheless, you may want to aggregate products over color or size, or customers by age, zip code, or population density. This is the situation when you can use a `GROUP BY` clause when querying a cube. Your query can extract data from the cube, then use SQL to aggregate by attribute value.

The cube must use the same aggregation operator for all dimensions, and the aggregation operator in the `SELECT` list of the query must match the aggregation operator of the cube. You can use a `GROUP BY` clause to query cubes that use these operators:

- First Non-NA Value

- Last Non-NA Value

- Maximum

- Minimum

- Sum

#### 4.5.1 Aggregating Measures Over Attributes

Example 4-5 shows a query that aggregates over an attribute named Package. It returns these results:

    TIME   PACKAGE                 SALES
    ------ ------------------ ----------
    2005   All                1809157.64
    2005   Multimedia         18083256.3
    2005   Executive            19836977
    2005   Laptop Value Pack  9547494.81

Units Cube uses the `SUM` operator for all dimensions, and the query uses the `SUM` operator to aggregate over Sales. The Package attribute applies only to the Item level of the Product dimension, so the query selects the Item level of Product. It also eliminates nulls for Package, so that only products that belong to a package are included in the calculation. The `GROUP BY` clause breaks out Total Sales by Time and Package.

Example 4-5 Aggregating Over an Attribute

    SELECT t.long_description time,
         p.package package,
         SUM(f.sales) sales
      FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
    /* Select Product by level and attribute */
      WHERE p.level_name = 'ITEM'
         AND p.package IS NOT NULL
         AND t.long_description = '2005'
         AND cu.level_name = 'TOTAL'
         AND ch.level_name = 'TOTAL'
    /* Join dimensions and cube */
         AND t.dim_key = f.time
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
      GROUP BY t.long_description, p.package;

#### 4.5.2 Aggregating Calculated Measures Over Attributes

Before using the technique described in "Aggregating Measures Over Attributes", ensure that the calculation is meaningful. For example, the common calculation Percent Change might be defined as a calculated measure in a cube. Summing over Percent Change would produce unexpected results, because the calculation for Percent Change (`(a-b)/b`,) is not additive.

Consider the following rows of data. The correct Total Percent Change is `.33`, whereas the sum of the percent change for the first two rows is `.75`.

| Row   | Sales | Sales Prior Period | Percent Change |
|:------|:------|:-------------------|:---------------|
| 1     | `15`  | `10`               | `.50`          |
| 2     | `25`  | `20`               | `.25`          |
| Total | `40`  | `30`               | `.33`          |

Example 4-6 shows a query that aggregates over the Package attribute and calculates Percent Change From Prior Period. The inner query aggregates Sales and Sales Prior Period over the attributes, and the outer query uses the results to compute the percent change. These are the results of the query, which show the expected results for `PCT_CHG_PP`:

    TIME   PACKAGE                 SALES PRIOR_PERIOD PCT_CHG_PP
    ------ ------------------ ---------- ------------ ----------
    2005   All                1809157.64   1853928.06 -.02414895
    2006   All                1720399.03   1809157.64 -.04906074
    2005   Executive            19836977   20603879.8 -.03722128
    2006   Executive          19580638.4     19836977 -.01292226
    2005   Laptop Value Pack  9547494.81   10047298.6 -.04974509
    2006   Laptop Value Pack  9091450.58   9547494.81 -.04776585
    2005   Multimedia         18083256.3   19607675.5 -.07774604
    2006   Multimedia         18328678.7   18083256.3 .013571806

    8 rows selected.

Example 4-6 Querying Over Attributes Using Calculated Measures

    /* Calculate Percent Change */
    SELECT TIME, package, sales, prior_period,
         ((sales - prior_period) / prior_period) pct_chg_pp
    FROM
    /* Fetch data from the cube and aggregate over Package */
         (SELECT t.long_description time,
              p.package package,
              SUM(f.sales) sales,
              SUM(f.sales_pp) prior_period
           FROM time_calendar_view t,
              product_primary_view p,
              customer_shipments_view cu,
              channel_primary_view ch,
              units_cube_view f
    /* Create filters */
           WHERE p.level_name = 'ITEM'
              AND p.package IS NOT NULL
              AND t.long_description IN ('2005', '2006')
              AND cu.level_name = 'TOTAL'
              AND ch.level_name = 'TOTAL'
    /* Join dimension views to cube view */
              AND t.dim_key = f.time
              AND p.dim_key = f.product
              AND cu.dim_key = f.customer
              AND ch.dim_key = f.channel
           GROUP BY t.long_description, p.package
           ORDER BY p.package);

### 4.6 Joining Cubes to Tables and Views

You can join cubes to other cubes and to relational objects such as:

- Tables

- Views including external tables and PL/SQL table functions

- Other row source types, like other joins

Typically, you do not need a fully aggregated cube when joining it to a table or view, and a `CUBE JOIN` operation limits the number of fetched values to improve performance automatically. The cube must be on the right side of the equation. If the query does not support `CUBE JOIN`, then the more expensive `HASH JOIN`, `MERGE JOIN`, or `NESTED LOOPS` are commonly used.

You can use hints in the query to influence the use of `CUBE JOIN`:

- `USE_CUBE` forces a `CUBE JOIN` if possible.

- `NO_USE_CUBE` prevents a `CUBE JOIN`.

See "Viewing Execution Plans" for more information about `CUBE JOIN`.

Example 4-7 joins a table that contains French descriptions of the Customer dimension to a cube that supports only English. The query returns these results:

    CUSTOMER                                        SALES
    ---------------------------------------- ------------
    La Marine des USA Washington                   600.34
    Monolith Motor Co. Chattanooga               17946.51
    Piedmont, Inc. San Jose                      24874.41
    Ministere du Commerce Int. Nagano            27595.97
    Depart. des commun. - Stuttgart              30706.10
    Min. Env. Brit. Londres                      38125.77
    Departement de travail Nouvelle-Orleans      42507.50
    Ministere des Finances Sorbonne              43607.58
    Monolith Motor Co. Knoxville                 50874.53
    Serv. des USA de recherche Wyo               54497.19
    Depart. des commun. - Bonn                   58944.97
         .
         .
         .

Example 4-7 Joining a Cube and a Table

    SELECT cu.ship_to_dsc_french customer,
         f.sales sales
    FROM time_calendar_view t,
         product_primary_view p,
         customer_dim cu,
         channel_primary_view ch,
         units_cube_view f
    WHERE t.dim_key = 'CY2006'
        AND p.level_name = 'TOTAL'
        AND ch.level_name = 'TOTAL'
        AND t.dim_key = f.TIME
        AND p.dim_key = f.product
        AND cu.ship_to_id = f.customer
        AND ch.dim_key = f.channel
    ORDER BY f.sales;

### 4.7 Viewing Execution Plans

You can generate and view execution plans for queries against cubes and dimensions the same as for those against relational tables.

The SQL `EXPLAIN PLAN` command creates a table with the content of the explain plan. The default table name is `PLAN_TABLE`.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/index.md) for a complete discussion of execution plans

#### 4.7.1 Generating Execution Plans

The following command creates an execution plan for a basic query on a cube:

    EXPLAIN PLAN FOR
      SELECT t.long_description time,
         p.long_description product,
         cu.long_description customer,
         ch.long_description channel,
         f.sales sales
      FROM time_calendar_view t,
         product_primary_view p,
         customer_shipments_view cu,
         channel_primary_view ch,
         units_cube_view f
      WHERE t.level_name = 'CALENDAR_YEAR'
         AND p.level_name = 'TOTAL'
         AND cu.level_name = 'TOTAL'
         AND ch.level_name = 'TOTAL'
         AND t.dim_key = f.TIME
         AND p.dim_key = f.product
         AND cu.dim_key = f.customer
         AND ch.dim_key = f.channel
      ORDER BY t.end_date;

Example 4-8 Execution Plan for a Cube Query

The `DISPLAY` table function of the `DBMS_XPLAN` PL/SQL package formats and displays information from an execution plan, as shown in this example.

    SQL> SELECT plan_table_output FROM TABLE(dbms_xplan.display());

    PLAN_TABLE_OUTPUT
    ------------------------------------------------------------------------------------------
    Plan hash value: 1667678335

    ----------------------------------------------------------------------------------------------
    | Id  | Operation                       | Name       | Rows  | Bytes | Cost (%CPU)| Time     |
    ----------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                |            |     1 |   100 |   104   (3)| 00:00:02 |
    |   1 |  SORT ORDER BY                  |            |     1 |   100 |   104   (3)| 00:00:02 |
    |   2 |   JOINED CUBE SCAN PARTIAL OUTER|            |       |       |            |          |
    |   3 |    CUBE ACCESS                  | UNITS_CUBE |       |       |            |          |
    |   4 |    CUBE ACCESS                  | CHANNEL    |       |       |            |          |
    |   5 |    CUBE ACCESS                  | CUSTOMER   |       |       |            |          |
    |   6 |    CUBE ACCESS                  | PRODUCT    |       |       |            |          |
    |*  7 |    CUBE ACCESS                  | TIME       |     1 |   100 |   103   (2)| 00:00:02 |
    ----------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       7 - filter(SYS_OP_ATG(VALUE(KOKBF$),12,13,2)='CALENDAR_YEAR' AND
                  SYS_OP_ATG(VALUE(KOKBF$),43,44,2)='TOTAL' AND
                  SYS_OP_ATG(VALUE(KOKBF$),33,34,2)='TOTAL' AND
                  SYS_OP_ATG(VALUE(KOKBF$),23,24,2)='TOTAL')

    22 rows selected.

Example 4-9 Execution Plan for a Cube Join

This example shows an execution plan for a query that joins a cube and a table. See "Joining Cubes to Tables and Views" for the query.

    PLAN_TABLE_OUTPUT
    -------------------------------------------------------------------------------------------------
    Plan hash value: 3634608218
    -------------------------------------------------------------------------------------------------
    | Id  | Operation                        |Name        |Rows | Bytes |TempSpc|Cost (%CPU)| Time    |
    --------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                 |            |1464 |   128K|       | 1524  (94)| 00:00:19|
    |   1 |  SORT ORDER BY                   |            |1464 |   128K|   152K| 1524  (94)| 00:00:19|
    |*  2 |   CUBE JOIN                      |            |1464 |   128K|       | 1422 (100)| 00:00:18|
    |   3 |    TABLE ACCESS FULL             |CUSTOMER_DIM|  61 |  2379 |       |    4   (0)| 00:00:01|
    |   4 |    JOINED CUBE SCAN PARTIAL OUTER|            |     |       |       |           |         |
    |   5 |     CUBE ACCESS                  |UNITS_CUBE  |     |       |       |           |         |
    |   6 |     CUBE ACCESS                  |CHANNEL     |     |       |       |           |         |
    |   7 |     CUBE ACCESS                  |PRODUCT     |     |       |       |           |         |
    |*  8 |     CUBE ACCESS                  |TIME        |2520 |   125K|       | 1417 (100)| 00:00:18|
    --------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------
       2 - access("CU"."SHIP_TO_ID"=SYS_OP_ATG(VALUE(KOKBF$),76,77,2))
       8 - filter(SYS_OP_ATG(VALUE(KOKBF$),32,33,2)='CY2006' AND
                  SYS_OP_ATG(VALUE(KOKBF$),85,86,2)='TOTAL' AND
                  SYS_OP_ATG(VALUE(KOKBF$),65,66,2)='TOTAL')

    22 rows selected.

#### 4.7.2 Types of Execution Plans

Table 4-1 describes the types of execution plans for cubes.

Table 4-1 Descriptions of Execution Plans for Cubes and Dimensions

| Operation   | Option          | Description                                                                                                                                                                                                                                                                                                      |
|:------------|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CUBE JOIN` | --              | Joins a table or view on the left and a cube on the right.                                                                                                                                                                                                                                                       |
| `CUBE JOIN` | `ANTI`          | Uses an antijoin for a table or view on the left and a cube on the right.                                                                                                                                                                                                                                        |
| `CUBE JOIN` | `ANTI SNA`      | Uses an antijoin (Single-sided Null Aware) for a table or view on the left and a cube on the right. The join column on the right (cube side) is `NOT NULL`. For example:<br>`SELECT cols FROM table `<br>`   WHERE table.c1 NOT IN `<br>`      (SELECT col FROM cube `<br>`         WHERE cube.col IS NOT NULL)` |
| `CUBE JOIN` | `OUTER`         | Uses an outer join for a table or view on the left and a cube on the right.                                                                                                                                                                                                                                      |
| `CUBE JOIN` | `RIGHT SEMI`    | Uses a right semijoin for a table or view on the left and a cube on the right.                                                                                                                                                                                                                                   |
| `CUBE SCAN` | --              | Uses inner joins for all cube access.                                                                                                                                                                                                                                                                            |
| `CUBE SCAN` | `PARTIAL OUTER` | Uses an outer join for least one dimension, and inner joins for the other dimensions.                                                                                                                                                                                                                            |
| `CUBE SCAN` | `OUTER`         | Uses outer joins for all cube access.                                                                                                                                                                                                                                                                            |

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Joins.md) for descriptions of these join types.

### 4.8 Querying the Data Dictionary

If you are developing a generic application -- that is, one where the names of the dimensional objects are not known -- then your application can retrieve this information from the data dictionary.

Among the static views of the database data dictionary are those that provide information about dimensional objects. All OLAP metadata is stored in the data dictionary. A few of the data dictionary views were introduced previously in this chapter.

Table 4-2 provides brief descriptions of the `ALL` views. There are corresponding `DBA` and `USER` views.

Table 4-2 Static Data Dictionary Views for OLAP

| View                                                                     | Description                                                                        |
|:-------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|
| [`ALL_CUBE_ATTR_VISIBILITY`](../refrn/ALL_CUBE_ATTR_VISIBILITY.md)       | Describes the visibility of the attributes for cube dimensions.                    |
| [`ALL_CUBE_ATTRIBUTES`](../refrn/ALL_CUBE_ATTRIBUTES.md)                 | Describes the attributes for cube dimensions.                                      |
| [`ALL_CUBE_BUILD_PROCESSES`](../refrn/ALL_CUBE_BUILD_PROCESSES.md)       | Describes the cube build processes and maintenance scripts.                        |
| [`ALL_CUBE_CALCULATED_MEMBERS`](../refrn/ALL_CUBE_CALCULATED_MEMBERS.md) | Describes the calculated members (keys) for cube dimensions.                       |
| [`ALL_CUBE_DIM_LEVELS`](../refrn/ALL_CUBE_DIM_LEVELS.md)                 | Describes the cube dimension levels.                                               |
| [`ALL_CUBE_DIM_MODELS`](../refrn/ALL_CUBE_DIM_MODELS.md)                 | Describes the models for cube dimensions.                                          |
| [`ALL_CUBE_DIM_VIEW_COLUMNS`](../refrn/ALL_CUBE_DIM_VIEW_COLUMNS.md)     | Describes the columns of the system-generated relational views of cube dimensions. |
| [`ALL_CUBE_DIM_VIEWS`](../refrn/ALL_CUBE_DIM_VIEWS.md)                   | Describes the system-generated relational views of OLAP dimensions.                |
| [`ALL_CUBE_DIMENSIONALITY`](../refrn/ALL_CUBE_DIMENSIONALITY.md)         | Describes the dimension order of the OLAP cubes.                                   |
| [`ALL_CUBE_DIMENSIONS`](../refrn/ALL_CUBE_DIMENSIONS.md)                 | Describes the cube dimensions.                                                     |
| [`ALL_CUBE_HIER_LEVELS`](../refrn/ALL_CUBE_HIER_LEVELS.md)               | Describes the hierarchy levels for cube dimensions.                                |
| [`ALL_CUBE_HIER_VIEW_COLUMNS`](../refrn/ALL_CUBE_HIER_VIEW_COLUMNS.md)   | Describes the columns of relational hierarchy views of cube dimensions.            |
| [`ALL_CUBE_HIER_VIEWS`](../refrn/ALL_CUBE_HIER_VIEWS.md)                 | Describes the hierarchies for cube dimensions.                                     |
| [`ALL_CUBE_HIERARCHIES`](../refrn/ALL_CUBE_HIERARCHIES.md)               | Describes the OLAP dimension hierarchies.                                          |
| [`ALL_CUBE_MEASURES`](../refrn/ALL_CUBE_MEASURES.md)                     | Describes the measures in the OLAP cubes.                                          |
| [`ALL_CUBE_VIEW_COLUMNS`](../refrn/ALL_CUBE_VIEW_COLUMNS.md)             | Describes the columns of the relational views of OLAP cubes.                       |
| [`ALL_CUBE_VIEWS`](../refrn/ALL_CUBE_VIEWS.md)                           | Describes the system-generated relational views of OLAP cubes.                     |
| [`ALL_CUBES`](../refrn/ALL_CUBES.md)                                     | Describes the OLAP cubes.                                                          |
| [`ALL_MEASURE_FOLDER_CONTENTS`](../refrn/ALL_MEASURE_FOLDER_CONTENTS.md) | Describes the contents of OLAP measure folders.                                    |
| [`ALL_MEASURE_FOLDERS`](../refrn/ALL_MEASURE_FOLDERS.md)                 | Describes the OLAP measure folders.                                                |

**See Also:**

[Oracle Database Reference](../refrn/ALL_CUBE_ATTR_VISIBILITY.md) for full descriptions of data dictionary views.
