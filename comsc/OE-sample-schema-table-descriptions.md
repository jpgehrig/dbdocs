Consider the tables of the `OE` sample schema.

- Table OE.CUSTOMERS

- Table OE.INVENTORIES

- Table OE.ORDERS

- Table OE.ORDER_ITEMS

- Table OE.PRODUCT_DESCRIPTIONS

- Table OE.PRODUCT_INFORMATION

- Table OE.WAREHOUSES

- Table OE.PURCHASEORDER

### 4.5.1 Table OE.CUSTOMERS

Table 4-12 OE.CUSTOMERS Table Description

| Column Name         | Null?      | Type                 |
|:--------------------|:-----------|:---------------------|
| `CUSTOMER_ID`       | `NOT NULL` | `NUMBER(6)`          |
| `CUST_FIRST_NAME`   | `NOT NULL` | `VARCHAR2(20)`       |
| `CUST_LAST_NAME`    | `NOT NULL` | `VARCHAR2(20)`       |
| `CUST_ADDRESS`      |            | `CUST_ADDRESS_TYP`   |
| `PHONE_NUMBERS`     |            | `PHONE_LIST_TYP`     |
| `NLS_LANGUAGE`      |            | `VARCHAR2(3)`        |
| `NLS_TERRITORY`     |            | `VARCHAR2(30)`       |
| `CREDIT_LIMIT`      |            | `NUMBER(9,2)`        |
| `CUST_EMAIL`        |            | `VARCHAR2(30)`       |
| `ACCOUNT_MGR_ID`    |            | `NUMBER(6)`          |
| `CUST_GEO_LOCATION` |            | `MDSYS.SDO_GEOMETRY` |
| `DATE_OF_BIRTH`     |            | `DATE`               |
| `MARITAL_STATUS`    |            | `VARCHAR2(20)`       |
| `GENDER`            |            | `VARCHAR2(1)`        |
| `INCOME_LEVEL`      |            | `VARCHAR2(20)`       |

### 4.5.2 Table OE.INVENTORIES

Table 4-13 OE.INVENTORIES Table Description

| Column Name        | Null?      | Type        |
|:-------------------|:-----------|:------------|
| `PRODUCT_ID`       | `NOT NULL` | `NUMBER(6)` |
| `WAREHOUSE_ID`     | `NOT NULL` | `NUMBER(3)` |
| `QUANTITY_ON_HAND` | `NOT NULL` | `NUMBER(8)` |

### 4.5.3 Table OE.ORDERS

Table 4-14 OE.ORDERS Table Description

| Column Name    | Null?      | Type                                |
|:---------------|:-----------|:------------------------------------|
| `ORDER_ID`     | `NOT NULL` | `NUMBER(12)`                        |
| `ORDER_DATE`   | `NOT NULL` | `TIMESTAMP(6) WITH LOCAL TIME ZONE` |
| `ORDER_MODE`   |            | `VARCHAR2(8)`                       |
| `CUSTOMER_ID`  | `NOT NULL` | `NUMBER(6)`                         |
| `ORDER_STATUS` |            | `NUMBER(2)`                         |
| `ORDER_TOTAL`  |            | `NUMBER(8,2)`                       |
| `SALES_REP_ID` |            | `NUMBER(6)`                         |
| `PROMOTION_ID` |            | `NUMBER(6)`                         |

### 4.5.4 Table OE.ORDER_ITEMS

Table 4-15 OE.ORDER_ITEMS Table Description

| Column Name    | Null?      | Type          |
|:---------------|:-----------|:--------------|
| `ORDER_ID`     | `NOT NULL` | `NUMBER(12)`  |
| `LINE_ITEM_ID` | `NOT NULL` | `NUMBER(3)`   |
| `PRODUCT_ID`   | `NOT NULL` | `NUMBER(6)`   |
| `UNIT_PRICE`   |            | `NUMBER(8,2)` |
| `QUANTITY`     |            | `NUMBER(8)`   |

### 4.5.5 Table OE.PRODUCT_DESCRIPTIONS

Table 4-16 OE.PRODUCT_DESCRIPTIONS Table Description

| Column Name              | Null?      | Type              |
|:-------------------------|:-----------|:------------------|
| `PRODUCT_ID`             | `NOT NULL` | `NUMBER(6)`       |
| `LANGUAGE_ID`            | `NOT NULL` | `VARCHAR2(3)`     |
| `TRANSLATED_NAME`        | `NOT NULL` | `NVARCHAR2(50)`   |
| `TRANSLATED_DESCRIPTION` | `NOT NULL` | `NVARCHAR2(2000)` |

### 4.5.6 Table OE.PRODUCT_INFORMATION

Table 4-17 OE.PRODUCT_INFORMATION Table Description

| Column Name           | Null?      | Type                        |
|:----------------------|:-----------|:----------------------------|
| `PRODUCT_ID`          | `NOT NULL` | `NUMBER(6)`                 |
| `PRODUCT_NAME`        |            | `VARCHAR2(50)`              |
| `PRODUCT_DESCRIPTION` |            | `VARCHAR2(2000)`            |
| `CATEGORY_ID`         |            | `NUMBER(2)`                 |
| `WEIGHT_CLASS`        |            | `NUMBER(1)`                 |
| `WARRANTY_PERIOD`     |            | `INTERVAL YEAR(2) TO MONTH` |
| `SUPPLIER_ID`         |            | `NUMBER(6))`                |
| `PRODUCT_STATUS`      |            | `VARCHAR2(20)`              |
| `LIST_PRICE`          |            | `NUMBER(8,2)`               |
| `MIN_PRICE`           |            | `NUMBER(8,2)`               |
| `CATALOG_URL`         |            | `VARCHAR2(50)`              |

### 4.5.7 Table OE.WAREHOUSES

Table 4-18 OE.WAREHOUSES Table Description

| Column Name       | Null?      | Type                 |
|:------------------|:-----------|:---------------------|
| `WAREHOUSE_ID`    | `NOT NULL` | `NUMBER(3)`          |
| `WAREHOUSE_SPEC`  |            | `SYS.XMLTYPE`        |
| `WAREHOUSE_NAME`  |            | `VARCHAR2(35)`       |
| `LOCATION_ID`     |            | `NUMBER(4)`          |
| `WH_GEO_LOCATION` |            | `MDSYS.SDO_GEOMETRY` |

Column `warehouse_spec` of table `OE.warehouses` contains `XMLType` data. This data is not based on any XML schema, which means that it can take any form. However, the actual data in column `warehouse_spec` at the outset (before any changes you might have made to it) has a top-level element `Warehouse` with the following child elements:

- `Building`, with text node `Owned` or `Rented`

- `Area`, with text node a number (representing, for example, square feet)

- `Docks`, with text node the number of loading docks (for example, 1, 2, or 3)

- `DockType`, with text node empty or `Rear Load` or `Side Load`

- `WaterAccess`, with text node `Y` or `N`

- `RailAccess`, with text node `Y` or `N`

- `Parking`, with text node `Street` or `Lot`

- `VClearance` (vertical clearance), with text node a number followed by a linear unit (for example, `11.5 ft`)

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/preface.md) for examples using the `XMLType` data in column `warehouse_spec`

### 4.5.8 Table OE.PURCHASEORDER

Table `OE.purchaseorder` is an object-relational table with `XMLType` data. The data conforms to XML schema `purchaseOrder.xsd`.
