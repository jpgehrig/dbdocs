You can create a table that has JSON columns. You use SQL condition `is json` as a check constraint to ensure that data inserted into a column is (well-formed) JSON data. Oracle recommends that you always use an `is_json` check constraint when you create a column intended for JSON data.

Example 4-1 and Example 4-2 illustrate this. They create and fill a table that holds data used in examples elsewhere in this documentation.

For brevity, only two rows of data (one JSON document) are inserted in Example 4-2.

**Note:**

SQL/JSON conditions `IS JSON` and `IS NOT JSON` return true or false for any non-`NULL` SQL value. But they both return unknown (neither true nor false) for SQL `NULL`. When used in a check constraint, they do not prevent a SQL `NULL` value from being inserted into the column. (But when used in a SQL `WHERE` clause, SQL `NULL` is never returned.)

It is true that a check constraint can reduce performance for data insertion. If you are sure that your application inserts only well-formed JSON data into a particular column, then consider disabling the check constraint, but do not drop the constraint.

**See Also:**

- [Loading External JSON Data](loading-external-json-data.md) for the creation of the full table `j_purchaseorder`

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about` CREATE TABLE`

Example 4-1 Using IS JSON in a Check Constraint to Ensure JSON Data is Well-Formed

    CREATE TABLE j_purchaseorder
      (id          VARCHAR2 (32) NOT NULL PRIMARY KEY,
       date_loaded TIMESTAMP (6) WITH TIME ZONE,
       po_document VARCHAR2 (23767)
       CONSTRAINT ensure_json CHECK (po_document IS JSON));

Example 4-2 Inserting JSON Data Into a VARCHAR2 JSON Column

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-DEC-2014'),
        '{"PONumber"             : 1600,
          "Reference"            : "ABULL-20140421",
          "Requestor"            : "Alexis Bull",
          "User"                 : "ABULL",
          "CostCenter"           : "A50",
          "ShippingInstructions" :
            {"name"    : "Alexis Bull",
             "Address" : {"street"  : "200 Sporting Green",
                          "city"    : "South San Francisco",
                          "state"   : "CA",
                          "zipCode" : 99236,
                          "country" : "United States of America"},
             "Phone"   : [{"type" : "Office", "number" : "909-555-7307"},
                          {"type" : "Mobile", "number" : "415-555-1234"}]},
          "Special Instructions" : null,
          "AllowPartialShipment" : true,
          "LineItems"            :
            [{"ItemNumber" : 1,
              "Part"       : {"Description" : "One Magic Christmas",
                              "UnitPrice"   : 19.95,
                              "UPCCode"     : 13131092899},
              "Quantity"   : 9.0},
             {"ItemNumber" : 2,
              "Part"       : {"Description" : "Lethal Weapon",
                              "UnitPrice"   : 19.95,
                              "UPCCode"     : 85391628927},
              "Quantity"   : 5.0}]}');

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-DEC-2014'),
        '{"PONumber"             : 672,
          "Reference"            : "SBELL-20141017",
          "Requestor"            : "Sarah Bell",
          "User"                 : "SBELL",
          "CostCenter"           : "A50",
          "ShippingInstructions" : {"name"    : "Sarah Bell",
                                    "Address" : {"street"  : "200 Sporting Green",
                                                 "city"    : "South San Francisco",
                                                 "state"   : "CA",
                                                 "zipCode" : 99236,
                                                 "country" : "United States of America"},
                                    "Phone"   : "983-555-6509"},
          "Special Instructions" : "Courier",
          "LineItems"            :
            [{"ItemNumber" : 1,
              "Part"       : {"Description" : "Making the Grade",
                              "UnitPrice"   : 20,
                              "UPCCode"     : 27616867759},
              "Quantity"   : 8.0},
             {"ItemNumber" : 2,
              "Part"       : {"Description" : "Nixon",
                              "UnitPrice"   : 19.95,
                              "UPCCode"     : 717951002396},
              "Quantity"   : 5},
             {"ItemNumber" : 3,
              "Part"       : {"Description" : "Eric Clapton: Best Of 1981-1999",
                              "UnitPrice"   : 19.95,
                              "UPCCode"     : 75993851120},
              "Quantity"   : 5.0}]}');

- Determining Whether a Column Necessarily Contains JSON Data
  How can you tell whether a given column of a table or view is well-formed JSON data? Whenever this is the case, the column is listed in the following static data dictionary views: `DBA_JSON_COLUMNS`, `USER_JSON_COLUMNS`, and `ALL_JSON_COLUMNS`.

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)

### 4.1 Determining Whether a Column Necessarily Contains JSON Data

How can you tell whether a given column of a table or view is well-formed JSON data? Whenever this is the case, the column is listed in the following static data dictionary views: `DBA_JSON_COLUMNS`, `USER_JSON_COLUMNS`, and `ALL_JSON_COLUMNS`.

Each of these views lists the column name, data type, and format (`TEXT` or `BINARY`); the table or view name (column `TABLE_NAME`); and whether the object is a table or a view (column `OBJECT_TYPE`).

For a table column to be considered JSON data it must have an `is json` check constraint. But in the case of a view, any one of the following criteria suffices for a column to be considered JSON data:

- The underlying data has an `is json` check constraint.

- The column results from the use of SQL/JSON function `json_query`.

- The column results from the use of a JSON generation function, such as `json_object`.

- The column results from the use of SQL function `treat` with keywords `AS JSON`.

If an `is json` check constraint determines that a table column is JSON data, and if that constraint is later deactivated, the column remains listed in the views. If the check constraint is dropped then the column is removed from the views.

**Note:**

If a check constraint combines condition `is json` with another condition using logical condition `OR`, then the column is not listed in the views. In this case, it is not certain that data in the column is JSON data. For example, the constraint `jcol is json` `OR` `length(jcol) < 1000` does not ensure that the data in column `jcol` is JSON data.

**See Also:**

[Oracle Database Reference](../refrn/ALL_JSON_COLUMNS.md) for information about `ALL_JSON_COLUMNS` and the related data-dictionary views

**Parent topic:** Creating a Table With a JSON Column
