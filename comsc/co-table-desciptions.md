Consider the columns of each table of `CO` sample schema.

- Table CO.CUSTOMERS
- Table CO.STORES
- Table CO.PRODUCTS
- Table CO.ORDERS
- Table CO.ORDER_ITEMS

### 4.13.1 Table CO.CUSTOMERS

The table below lists `CO.CUSTOMERS` table description.

Table 4-38 CO.CUSTOMERS Table Description

| Column Name     | Nulls Allowed? | Type                 |
|:----------------|:---------------|:---------------------|
| `CUSTOMER_ID`   | `NO`           | `INTEGER`            |
| `EMAIL_ADDRESS` | `NO`           | `VARCHAR2(255 CHAR)` |
| `FULL_NAME`     | `NO`           | `VARCHAR2(255 CHAR)` |

### 4.13.2 Table CO.STORES

The table below lists `CO.STORES` table description.

Table 4-39 Table CO.STORES Table Description

| Column Name         | Nulls Allowed? | Type                 |
|:--------------------|:---------------|:---------------------|
| `STORE_ID`          | `NO`           | `INTEGER`            |
| `STORE_NAME`        | `NO`           | `VARCHAR2(255 CHAR)` |
| `WEB_ADDRESS`       | `YES`          | `VARCHAR2(100 CHAR)` |
| `PHYSICAL_ADDRESS`  | `YES`          | `VARCHAR2(512 CHAR)` |
| `LATITUDE`          | `YES`          | `NUMBER`             |
| `LONGITUDE`         | `YES`          | `NUMBER`             |
| `LOGO`              | `YES`          | `BLOB`               |
| `LOGO_MIME_TYPE`    | `YES`          | `VARCHAR2(512 CHAR)` |
| `LOGO_FILENAME`     | `YES`          | `VARCHAR2(512 CHAR)` |
| `LOGO_CHARSET`      | `YES`          | `VARCHAR2(512 CHAR)` |
| `LOGO_LAST_UPDATED` | `YES`          | `DATE`               |

**Note:**

The table has a constraint to verify either `WEB_ADDRESS` or `PHYSICAL ADDRESS` is `NOT NULL`.

### 4.13.3 Table CO.PRODUCTS

The table below lists `CO.PRODUCTS` table description.

Table 4-40 Table CO.PRODUCTS Table Description

| Column Name          | Nulls Allowed? | Type                 |
|:---------------------|:---------------|:---------------------|
| `PRODUCT_ID`         | `NO`           | `INTEGER`            |
| `PRODUCT_NAME`       | `NO`           | `VARCHAR2(255 CHAR)` |
| `UNIT_PRICE`         | `YES`          | `NUMBER(10,2)`       |
| `PRODUCT_DETAILS`    | `YES`          | `BLOB`               |
| `PRODUCT_IMAGE`      | `YES`          | `BLOB`               |
| `IMAGE_MIME_TYPE`    | `YES`          | `VARCHAR2(512 CHAR)` |
| `IMAGE_FILENAME`     | `YES`          | `VARCHAR2(512 CHAR)` |
| `IMAGE_CHARSET`      | `YES`          | `VARCHAR2(512 CHAR)` |
| `IMAGE_LAST_UPDATED` | `YES`          | `DATE`               |

### 4.13.4 Table CO.ORDERS

The table below lists `CO.ORDERS` table description.

Table 4-41 Table CO.ORDERS Table Description

| Column Name      | Nulls Allowed? | Type                |
|:-----------------|:---------------|:--------------------|
| `ORDER_ID`       | `NO`           | `INTEGER`           |
| `ORDER_DATETIME` | `NO`           | `TIMESTAMP`         |
| `CUSTOMER_ID`    | `NO`           | `INTEGER`           |
| `ORDER_STATUS`   | `NO`           | `VARCHAR2(10 CHAR)` |
| `STORE_ID`       | `NO`           | `INTEGER`           |

### 4.13.5 Table CO.ORDER_ITEMS

The table below lists `CO.ORDER_ITEMS` table description.

Table 4-42 Table CO.ORDER_ITEMS Table Description

| Column Name    | Nulls Allowed? | Type           |
|:---------------|:---------------|:---------------|
| `ORDER_ID`     | `NO`           | `INTEGER`      |
| `LINE_ITEM_ID` | `NO`           | `INTEGER`      |
| `PRODUCT_ID`   | `NO`           | `INTEGER`      |
| `UNIT_PRICE`   | `NO`           | `NUMBER(10,2)` |
| `QUANTITY`     | `NO`           | `INTEGER`      |
