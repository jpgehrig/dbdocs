A join between the tables for one-to-many relationship is represented through nested columns.

Oracle Data Mining requires a case table in single-record case format, with each record in a separate row. What if some or all of your data is in multi-record case format, with each record in several rows? What if you want one attribute to represent a series or collection of values, such as a student's test scores or the products purchased by a customer?

This kind of one-to-many relationship is usually implemented as a join between tables. For example, you can join your customer table to a sales table and thus associate a list of products purchased with each customer.

Oracle Data Mining supports dimensioned data through nested columns. To include dimensioned data in your case table, create a view and cast the joined data to one of the Data Mining nested table types. Each row in the nested column consists of an attribute name/value pair. Oracle Data Mining internally processes each nested row as a separate attribute.

**Note:**

O-Cluster is the only algorithm that does not support nested data.

**Related Topics**

- [Example: Creating a Nested Column for Market Basket Analysis](using-market-basket-data.md)

### 3.3.1 Nested Object Types

Nested tables are object data types that can be used in place of other data types.

Oracle Database supports user-defined data types that make it possible to model real-world entities as objects in the database. **Collection types** are object data types for modeling multi-valued attributes. Nested tables are collection types. Nested tables can be used anywhere that other data types can be used.

Oracle Data Mining supports the following nested object types:

- `DM_NESTED_BINARY_DOUBLES`
- `DM_NESTED_BINARY_FLOATS`
- `DM_NESTED_NUMERICALS`
- `DM_NESTED_CATEGORICALS`

Descriptions of the nested types are provided in this example.

Example 3-3 Oracle Data Mining Nested Data Types

    describe dm_nested_binary_double
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              BINARY_DOUBLE

    describe dm_nested_binary_doubles
     DM_NESTED_BINARY_DOUBLES TABLE OF SYS.DM_NESTED_BINARY_DOUBLE
     Name                                       Null?    Type
     ------------------------------------------ -------- ---------------------------
     ATTRIBUTE_NAME                                      VARCHAR2(4000)
     VALUE                                               BINARY_DOUBLE

    describe dm_nested_binary_float
     Name                                      Null?    Type
     ----------------------------------------- -------- ---------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              BINARY_FLOAT

    describe dm_nested_binary_floats
     DM_NESTED_BINARY_FLOATS TABLE OF SYS.DM_NESTED_BINARY_FLOAT
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              BINARY_FLOAT

    describe dm_nested_numerical
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              NUMBER

    describe dm_nested_numericals
     DM_NESTED_NUMERICALS TABLE OF SYS.DM_NESTED_NUMERICAL
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              NUMBER

    describe dm_nested_categorical
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              VARCHAR2(4000)

    describe dm_nested_categoricals
     DM_NESTED_CATEGORICALS TABLE OF SYS.DM_NESTED_CATEGORICAL
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ATTRIBUTE_NAME                                     VARCHAR2(4000)
     VALUE                                              VARCHAR2(4000)

**Related Topics**

- [Oracle Database Object-Relational Developer's Guide](../adobj/support-for-collection-data-types.md)

### 3.3.2 Example: Transforming Transactional Data for Mining

Example 3-4 shows data from a view of a sales table. It includes sales for three of the many products sold in four regions. This data is not suitable for mining at the product level because sales for each case (product), is stored in several rows.

Example 3-5 shows how this data can be transformed for mining. The case ID column is `PRODUCT`. `SALES_PER_REGION`, a nested column of type `DM_NESTED_NUMERICALS`, is a data attribute. This table is suitable for mining at the product case level, because the information for each case is stored in a single row.

Oracle Data Mining treats each nested row as a separate model attribute, as shown in Example 3-6.

**Note:**

The presentation in this example is conceptual only. The data is not actually pivoted before being processed.

Example 3-4 Product Sales per Region in Multi-Record Case Format

    PRODUCT   REGION         SALES
    -------   --------   ----------
    Prod1       NE           556432
    Prod2       NE           670155
    Prod3       NE             3111
    .
    .
    Prod1       NW            90887
    Prod2       NW           100999
    Prod3       NW           750437
    .
    .
    Prod1       SE            82153
    Prod2       SE            57322
    Prod3       SE            28938
    .
    .
    Prod1       SW          3297551
    Prod2       SW          4972019
    Prod3       SW           884923
    .
    .

Example 3-5 Product Sales per Region in Single-Record Case Format

    PRODUCT      SALES_PER_REGION
              (ATTRIBUTE_NAME, VALUE)
    ------    --------------------------
    Prod1      ('NE' ,     556432)
               ('NW' ,      90887)
               ('SE' ,      82153)
               ('SW' ,    3297551)
    Prod2      ('NE' ,     670155)
               ('NW' ,     100999)
               ('SE' ,      57322)
               ('SW' ,    4972019)
    Prod3      ('NE' ,       3111)
               ('NW' ,     750437)
               ('SE' ,      28938)
               ('SW' ,     884923)
    .
    .

Example 3-6 Model Attributes Derived From SALES_PER_REGION

    PRODUCT    SALES_PER_REGION.NE    SALES_PER_REGION.NW    SALES_PER_REGION.SE    SALES_PER_REGION.SW
    -------    ------------------    -------------------    ------------------    -------------------
    Prod1                 556432                 90887                  82153                3297551
    Prod2                 670155                100999                  57322                4972019
    Prod3                   3111                 750437                 28938                 884923
    .
    .
