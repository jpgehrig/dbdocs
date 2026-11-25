Become familiar with the faceted navigation feature.

- About Faceted Navigation

- Defining Sections As Facets

- Refining Queries by Using Facets As Filters

- Multivalued Facets

### 14.1 About Faceted Navigation

This feature implements group counts, also known as facets, which are frequently used in e-commerce or catalog applications. In various applications, it is preferable not only to display the list of hits returned by a query, but also to categorize the results.

For example, an e-commerce application wants to display all products matching a query for the term management along with faceting information. The facets include ‘type of product’ (books or DVDs), ‘author’, and ‘date’. For each facet, the application displays the unique values (books or DVDs) and their counts. You can quickly assess that most of the product offerings of interest fall under the ‘books’ category. You can further refine the search by selecting the ‘books’ value under ‘type of product’.

A group count is defined as the number of documents that have a certain value. If a value is repeated within the same document, the document contributes a count of 1 to the total group count for the value. Group counts or facets are supported for `SDATA` sections that use `optimized_for search` `SDATA.` To request a computation of facets for a query, use the Result Set Interface.

### 14.2 Defining Sections As Facets

`SDATA` refers to structured data. Group counts or facets are supported for `SDATA` sections that you create with the `optimized_for` attribute set to either ‘search’ or ‘sort and search’. In the `MULTI_COLUMN_DATASTORE` preference, when data appears between tags or columns that are specified as `optimized_for search`` SDATA,` the data is automatically indexed as the facet data. Any data that does not match its declared type is handled according to the same framework that currently handles indexing errors for a specific row.

#### Examples

In the following statements, some tagged data is inserted into a `VARCHAR2` column of a table. You can later define `SDATA` sections to collect the data based on the tags used here.

- Binary float or binary double with tag price:

  `insert into mytab values (1, 'red marble' <price>1.23</price>');`

- Time stamp with tag T:

  `insert into mytab values (1,'blue marbles <T>2012-12-05T05:20:00</T>');`

In the following statements, a section group is created and various `SDATA` section groups are added. The section definition includes the section group to which it belongs, the name of the section, the tag to be looked for, and the data type.

    exec ctx_ddl.create_section_group('sg','BASIC_SECTION_GROUP')
    exec ctx_ddl.add_SDATA_section('sg','sec01','name', 'varchar2')
    exec ctx_ddl.add_SDATA_section('sg','sec02','count', 'number')
    exec ctx_ddl.add_SDATA_section('sg','sec03','date', 'date')
    exec ctx_ddl.add_SDATA_section('sg','sec04','timestamp', 'timestamp')
    exec ctx_ddl.add_SDATA_section('sg','sec05','new price', 'binary_double')
    exec ctx_ddl.add_SDATA_section('sg','sec06','old price','binary_float')
    exec ctx_ddl.add_SDATA_section('sg','sec07','timestamp','timestamp with time zone')

The name given to the facet is `‘sec01’` and the `‘name’` tag is the actual tag name that occurs inside the document that is to be indexed. The `‘date’`, `‘timestamp’`, and `‘timestamp with time zone’` data types require the input data to be in the standard ISO format.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md) for more information about the standard ISO formats

Example 14-1 Using Faceted Navigation

The following statements create a table named `products:`

    drop table products;

    create table products(name varchar2(60), vendor varchar2(60), rating number, price number, mydate date);

The following statement inserts values into `products:`

    insert all
     into products values ('cherry red shoes', 'first vendor', 5, 129, sysdate)
     into products values ('bright red shoes', 'first vendor', 4, 109, sysdate)
     into products values ('more red shoes', 'second vendor', 5, 129, sysdate)
     into products values ('shoes', 'third vendor', 5, 109, sysdate)
    select * from dual;

The following statements create a `MULTI_COLUMN_DATASTORE` preference named `ds` to bring various other columns into the index (`name`) to be used as facets:

    /*A MULTI_COLUMN_DATASTORE automatically adds tags by default so that the text to be indexed looks like
    '<name>cherry red shoes</name><vendor>first vendor</vendor><rating> .... '*/

    exec ctx_ddl.drop_preference  ('ds')
    exec ctx_ddl.create_preference('ds', 'MULTI_COLUMN_DATASTORE')
    exec ctx_ddl.set_attribute    ('ds', 'COLUMNS', 'name, vendor, rating, price, mydate')

**Note:**

Oracle does not allow table columns with `binary_float, binary_double, timestamp,` and `timestamp with timezone` data types. It is therefore difficult to use such data types with `MULTI_COLUMN_DATASTORE.` You can still create facets if the document contains tagged data for these data types. Alternatively, you can convert 'timestamp' columns to 'date' and you can store `binary_float` and `binary_double` as 'number'.

The following statements create a section group named `sg` and enable the `optimized_for search` attribute for each column to be treated as a facet:

    /* A Section Group is created to specify the data type of each column (varchar2 is the default) and
    how each column that is brought into the index should be used.*/

    exec ctx_ddl.drop_section_group   ('sg')
    exec ctx_ddl.create_section_group ('sg', 'BASIC_SECTION_GROUP')

    exec ctx_ddl.add_sdata_section    ('sg', 'vendor', 'vendor', 'VARCHAR2')
    exec ctx_ddl.add_sdata_section    ('sg', 'rating', 'rating', 'NUMBER')
    exec ctx_ddl.add_sdata_section    ('sg', 'price', 'price', 'NUMBER')
    exec ctx_ddl.add_sdata_section    ('sg', 'mydate', 'mydate', 'DATE')

    exec ctx_ddl.set_section_attribute('sg', 'vendor', 'optimized_for', 'SEARCH')
    exec ctx_ddl.set_section_attribute('sg', 'rating', 'optimized_for', 'SEARCH')
    exec ctx_ddl.set_section_attribute('sg', 'price',  'optimized_for', 'SEARCH')
    exec ctx_ddl.set_section_attribute('sg', 'mydate', 'optimized_for', 'SEARCH')

The following statement creates an index on `name` and specifies the preferences by using the `PARAMETERS` clause:

    CREATE INDEX product_index ON products (name)
    INDEXTYPE IS ctxsys.context
    PARAMETERS ('datastore ds section group sg');

The following statements query for a product name, ‘red shoes’ and the facets for computation can be specified. The `count` attribute shows the total number of items that match the query for the product. The Result Set Interface specifies various requirements, such as the top vendors that have the largest number of matching items, the lowest available prices, and the latest arrivals:

    set long 500000
    set pagesize 0

    variable displayrs clob;

    declare
      rs clob;
    begin
       ctx_query.result_set('product_index', 'red shoes', '<ctx_result_set_descriptor>
            <count/>
            <group sdata="vendor" topn="5" sortby="count" order="desc">
            <count exact="true"/>
            </group>
            <group sdata="price" topn="3" sortby="value" order="asc">
            <count exact="true"/>
            </group>
            <group sdata="mydate" topn="3" sortby="value" order="desc">
            <count exact="true"/>
            </group>
            </ctx_result_set_descriptor>',
            rs);

    /* Pretty-print the result set (rs) for display purposes.
    It is not required if you are going to manipulate it in XML.*/

       select xmlserialize(Document XMLType(rs) as clob indent size=2) into :displayrs from dual;
       dbms_lob.freetemporary(rs);
    end;
    /
    select :displayrs from dual;

The following is output:

    <ctx_result_set>
      <count>3</count>

      <groups sdata="VENDOR">
        <group value="first vendor">
          <count>2</count>
        </group>
        <group value="second vendor">
          <count>1</count>
        </group>
      </groups>

      <groups sdata="PRICE">
        <group value="109">
          <count>1</count>
        </group>
        <group value="129">
          <count>2</count>
        </group>
      </groups>

      <groups sdata="MYDATE">
        <group value="2017-12-06 05:44:54">
          <count>3</count>
        </group>
      </groups>
    </ctx_result_set>

### 14.3 Querying Facets by Using the Result Set Interface

Starting with Oracle Database Release 18c, the group-counting operation for a specified list of facets is provided. You can obtain the group counts for each single value by using the `bucketby` attribute with its value set to `single.` The `topn,` `sortby,` and `order` attributes are also supported.

bucketby Attribute

- The only valid attribute is `single` in this release.

- The 'single' mode produces a list of all unique values for the facet and a document count for each value.

topn Attribute

- Valid attribute values are non-negative numbers greater than zero.

- This attribute specifies that only top `n` facet values and their counts are returned.

- Group count determines the top `n` values to return unless the `sortby` attribute is set to `value.` In that case, the values are sorted according to the data type and the top `n` results of the sort are returned. The order attribute is respected for the sort.

- By default, the results are sorted by the group count in descending order.

- If a tie occurs in the count, the ordering of the facet values within this tie is not guaranteed.

Single Count

The following statements insert a few rows into the table `mytab.` Some rows have two values for the facet `<B>,` and some rows have a single value.

    begin
        insert into mytab values (1, '<B>1.234</B><B>5</B>');
        insert into mytab values (2, '<B>1.432</B>');
        insert into mytab values (3, '<B>2.432</B><B>6</B>');
        insert into mytab values (4, '<B>2.432</B>');
    end;

Single counts show each unique value and the number of documents that have this value:

    <ctx_result_set>
        <groups sdata="SEC01">
            <group value="2.432"><count>2</count></group>
            <group value="1.234"><count>1</count></group>
            <group value="5"><count>1</count></group>
            <group value="6"><count>1</count></group>
            <group value="1.432"><count>1</count></group>
        </groups>
    </ctx_result_set>

If document 1 is deleted, you see the following result:

    <ctx_result_set>
        <groups sdata="SEC01">
            <group value="2.432"><count>2</count></group>
            <group value="6"><count>1</count></group>
            <group value="1.432"><count>1</count></group>
        </groups>
    </ctx_result_set>

sortby and order Attributes

- `sortby` supports the “count” and “value” attribute values.

  - `count` sorts by group counts (numbers). This is the default.

  - `value` sorts by value depending on the data type.

- `order` supports `ASC` (ascending order) and `DESC` (descending order), which is the default.

- If there is no selection, the default is count `DESC.`

This example shows the grouping of a number facet if `bucketby` is set to `single,` where `mytab_idx` is the name of the index, `text` is the query, and group `SDATA` requests the facets:

    begin
         ctx_query.result_set('mytab_idx', 'text',
                            '<ctx_result_set_descriptor>
         <group sdata="sec01" topn = "4" sortby = "value" order="asc" bucketby="single">
         <count/>
         </group>
         </ctx_result_set_descriptor>'
         :rs);
    end;

The following is a sample output showing that the values are listed in alphabetical order because the `sortby` attribute is set to `value` instead of `count.` The values are also displayed in ascending order (ABC to XYZ) because the `order` attribute is set to `asc.` Only four values are displayed because the `topn` attribute is set to `4.`

    <ctx_result_set>
         <group SDATA="SEC01">
             <group value="ABC"><count>2</count>
         </group>
             <group value="DEF"><count>1</count>
         </group>
             <group value="GHI"><count>10</count>
         </group>
             <group value="XYZ"><count>1</count>
         </group>
    </ctx_result_set>

### 14.4 Refining Queries by Using Facets As Filters

The facet implementation now supports `CONTAINS` queries with the standard set of database comparison operators available for SDATA. The following example is based on the ‘name’ varchar2 section. When you use it with numbers, do not use quotation marks around the numeric term to be searched.

    contains (text, 'SDATA(sec01 = "run")', 1) > 0
    contains (text, 'SDATA(sec01 > "run")', 1) > 0
    contains (text, 'SDATA(sec01 >= "run")', 1) > 0
    contains (text, 'SDATA(sec01 < "run")', 1) > 0
    contains (text, 'SDATA(sec01 <= "run")', 1) > 0
    contains (text, 'SDATA(sec01 <> "run")', 1) > 0
    contains (text, 'SDATA(sec01 != "run")', 1) > 0
    contains (text, 'SDATA(sec01 between "run1" and "run2")', 1) > 0
    contains (text, 'SDATA(sec01 not between "run1" and "run2")', 1) > 0
    contains (text, 'SDATA(sec01 is null)', 1) > 0
    contains (text, 'SDATA(sec01 is not null)', 1) > 0
    contains (text, 'SDATA(sec01 like "%run")', 1) > 0
    contains (text, 'SDATA(sec01 like "run%")', 1) > 0
    contains (text, 'SDATA(sec01 like "%run%")', 1) > 0
    contains (text, 'SDATA(sec01 not like "%run")', 1) > 0
    contains (text, 'SDATA(sec01 not like "run%")', 1) > 0
    contains (text, 'SDATA(sec01 not like "%run%")', 1) > 0

    contains (text, 'SDATA(sec02 = 9)', 1) > 0
    contains (text, 'SDATA(sec02 < 10)', 1) > 0
    contains (text, 'SDATA(sec02 between 2 and  20)', 1) > 0

The comparison operators behave according to the current `optimized_for search` `SDATA` behavior for the various data types.

### 14.5 Multivalued Facets

If multiple values are in an `optimized for search`` SDATA` section within the same document, then each value is indexed if the value is enclosed in its own tag corresponding to the SDATA section. Values that are not enclosed within separate section tags, but that appear together within the same section tag, are treated as a single value.

For example, in a document, `<car>First Car, Second Car</car>` is treated as a single string of value ‘First Car, Second Car’. However, `<car>First Car</car><car>Second Car</car>` is treated as two separate values for the document.
