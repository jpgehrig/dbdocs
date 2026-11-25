Consider the columns of each table of `SH` sample schema.

- Table SH.CHANNELS

- Table SH.COSTS

- Table SH.COUNTRIES

- Table SH.CUSTOMERS

- Table SH.PRODUCTS

- Table SH.PROMOTIONS

- Table SH.SALES

- Table SH.TIMES

### 4.11.1 Table SH.CHANNELS

Table 4-28 SH.CHANNELS Table Description

| Column Name        | Null?      | Type           |
|:-------------------|:-----------|:---------------|
| `CHANNEL_ID`       | `NOT NULL` | `NUMBER`       |
| `CHANNEL_DESC`     | `NOT NULL` | `VARCHAR2(20)` |
| `CHANNEL_CLASS`    | `NOT NULL` | `VARCHAR2(20)` |
| `CHANNEL_CLASS_ID` | `NOT NULL` | `NUMBER`       |
| `CHANNEL_TOTAL`    | `NOT NULL` | `VARCHAR2(13)` |
| `CHANNEL_TOTAL_ID` | `NOT NULL` | `NUMBER`       |

### 4.11.2 Table SH.COSTS

Table 4-29 SH.COSTS Table Description

| Column Name  | Null?      | Type           |
|:-------------|:-----------|:---------------|
| `PROD_ID`    | `NOT NULL` | `NUMBER`       |
| `TIME_DESC`  | `NOT NULL` | `DATE`         |
| `PROMO_ID`   | `NOT NULL` | `NUMBER`       |
| `CHANNEL_ID` | `NOT NULL` | `NUMBER`       |
| `UNIT_COST`  | `NOT NULL` | `NUMBER(10,2)` |
| `UNIT_PRICE` | `NOT NULL` | `NUMBER(10,2)` |

### 4.11.3 Table SH.COUNTRIES

Table 4-30 SH.COUNTRIES Table Description

| Column Name            | Null?      | Type           |
|:-----------------------|:-----------|:---------------|
| `COUNTRY_ID`           | `NOT NULL` | `NUMBER`       |
| `COUNTRY_ISO_CODE`     | `NOT NULL` | `CHAR(2)`      |
| `COUNTRY_NAME`         | `NOT NULL` | `VARCHAR2(40)` |
| `COUNTRY_SUBREGION`    | `NOT NULL` | `VARCHAR2(30)` |
| `COUNTRY_SUBREGION_ID` | `NOT NULL` | `NUMBER`       |
| `COUNTRY_REGION`       | `NOT NULL` | `VARCHAR2(20)` |
| `COUNTRY_REGION_ID`    | `NOT NULL` | `NUMBER`       |
| `COUNTRY_TOTAL`        | `NOT NULL` | `VARCHAR2(11)` |
| `COUNTRY_TOTAL_ID`     | `NOT NULL` | `NUMBER`       |
| `COUNTRY_NAME_HIST`    |            | `VARCHAR2(40)` |

### 4.11.4 Table SH.CUSTOMERS

Table 4-31 SH.CUSTOMERS Table Description

| Column Name              | Null?      | Type           |
|:-------------------------|:-----------|:---------------|
| `CUST_ID`                | `NOT NULL` | `NUMBER`       |
| `CUST_FIRST_NAME`        | `NOT NULL` | `VARCHAR2(20)` |
| `CUST_LAST_NAME`         | `NOT NULL` | `VARCHAR2(40)` |
| `CUST_GENDER`            | `NOT NULL` | `CHAR(1)`      |
| `CUST_YEAR_OF_BIRTH`     | `NOT NULL` | `NUMBER(4)`    |
| `CUST_MARITAL_STATUS`    |            | `VARCHAR2(20)` |
| `CUST_STREET_ADDRESS`    | `NOT NULL` | `VARCHAR2(40)` |
| `CUST_POSTAL_CODE`       | `NOT NULL` | `VARCHAR2(10)` |
| `CUST_CITY`              | `NOT NULL` | `VARCHAR2(30)` |
| `CUST_CITY_ID`           | `NOT NULL` | `NUMBER`       |
| `CUST_STATE_PROVINCE`    | `NOT NULL` | `VARCHAR2(40)` |
| `CUST_STATE_PROVINCE_ID` | `NOT NULL` | `NUMBER`       |
| `COUNTRY_ID`             | `NOT NULL` | `NUMBER`       |
| `CUST_MAIN_PHONE_NUMBER` | `NOT NULL` | `VARCHAR2(25)` |
| `CUST_INCOME_LEVEL`      |            | `VARCHAR2(30)` |
| `CUST_CREDIT_LIMIT`      |            | `NUMBER`       |
| `CUST_EMAIL`             |            | `VARCHAR2(30)` |
| `CUST_TOTAL`             | `NOT NULL` | `VARCHAR2(14)` |
| `CUST_TOTAL_ID`          | `NOT NULL` | `NUMBER`       |
| `CUST_SRC_ID`            |            | `NUMBER`       |
| `CUST_EFF_FROM`          |            | `DATE`         |
| `CUST_EFF_TO`            |            | `DATE`         |
| `CUST_VALID`             |            | `VARCHAR2(1)`  |

### 4.11.5 Table SH.PRODUCTS

Table 4-32 SH.PRODUCTS Table Description

| Column Name             | Null?      | Type             |
|:------------------------|:-----------|:-----------------|
| `PROD_ID`               | `NOT NULL` | `NUMBER(6)`      |
| `PROD_NAME`             | `NOT NULL` | `VARCHAR2(50)`   |
| `PROD_DESC`             | `NOT NULL` | `VARCHAR2(4000)` |
| `PROD_SUBCATEGORY`      | `NOT NULL` | `VARCHAR2(50)`   |
| `PROD_SUBCATEGORY_ID`   | `NOT NULL` | `NUMBER`         |
| `PROD_SUBCATEGORY_DESC` | `NOT NULL` | `VARCHAR2(2000)` |
| `PROD_CATEGORY`         | `NOT NULL` | `VARCHAR2(50)`   |
| `PRD_CATEGORY_ID`       | `NOT NULL` | `NUMBER`         |
| `PROD_CATEGORY_DESC`    | `NOT NULL` | `VARCHAR2(2000)` |
| `PROD_WEIGHT_CLASS`     | `NOT NULL` | `NUMBER(3)`      |
| `PROD_UNIT_OF_MEASURE`  |            | `VARCHAR2(20)`   |
| `PRD_PACK_SIZE`         | `NOT NULL` | `VARCHAR2(30)`   |
| `PROD_SUPPLIER_ID`      | `NOT NULL` | `NUMBER(6)`      |
| `PROD_STATUS`           | `NOT NULL` | `VARCHAR2(20)`   |
| `PROD_LIST_PRICE`       | `NOT NULL` | `NUMBER(8,2)`    |
| `PRD_MIN_PRICE`         | `NOT NULL` | `NUMBER(8,2)`    |
| `PROD_TOTAL`            | `NOT NULL` | `VARCHAR2(13)`   |
| `PROD_TOTAL_ID`         | `NOT NULL` | `NUMBER`         |
| `PROD_SRC_ID`           |            | `NUMBER`         |
| `PRD_EFF_FROM`          |            | `DATE`           |
| `PROD_EFF_TO`           |            | `DATE`           |
| `PROD_VALID`            |            | `VARCHAR2(1)`    |

### 4.11.6 Table SH.PROMOTIONS

Table 4-33 SH.PROMOTIONS Table Description

| Column Name            | Null?      | Type           |
|:-----------------------|:-----------|:---------------|
| `PROMO_ID`             | `NOT NULL` | `NUMBER(6)`    |
| `PROMO_NAME`           | `NOT NULL` | `VARCHAR2(30)` |
| `PROMO_SUBCATEGORY`    | `NOT NULL` | `VARCHAR2(30)` |
| `PROMO_SUBCATEGORY_ID` | `NOT NULL` | `NUMBER`       |
| `PROMO_CATEGORY`       | `NOT NULL` | `VARCHAR2(30)` |
| `PRMO_CATEGORY_ID`     | `NOT NULL` | `NUMBER`       |
| `PROMO_COST`           | `NOT NULL` | `NUMBER(10,2)` |
| `PROMO_BEGIN_DATE`     | `NOT NULL` | `DATE`         |
| `PROMO_END_DATE`       | `NOT NULL` | `DATE`         |
| `PROMO_TOTAL`          | `NOT NULL` | `VARCHAR2(15)` |
| `PROMO_TOTAL_ID`       | `NOT NULL` | `NUMBER`       |

### 4.11.7 Table SH.SALES

Table 4-34 SH.SALES Table Description

| Column Name     | Null?      | Type           |
|:----------------|:-----------|:---------------|
| `PROD_ID`       | `NOT NULL` | `NUMBER`       |
| `CUST_ID`       | `NOT NULL` | `NUMBER`       |
| `TIME_ID`       | `NOT NULL` | `DATE`         |
| `CHANNEL_ID`    | `NOT NULL` | `NUMBER`       |
| `PROMO_ID`      | `NOT NULL` | `NUMBER`       |
| `QUANTITY_SOLD` | `NOT NULL` | `NUMBER(10,2)` |
| `AMOUNT_SOLD`   | `NOT NULL` | `NUMBER(10,2)` |

### 4.11.8 Table SH.TIMES

Table 4-35 SH.TIMES Table Description

| Column Name               | Null?      | Type          |
|:--------------------------|:-----------|:--------------|
| `TIME_ID`                 | `NOT NULL` | `DATE`        |
| `DAY_NAME`                | `NOT NULL` | `VARCHAR2(9)` |
| `DAY_NUMBER_IN_WEEK`      | `NOT NULL` | `NUMBER(1)`   |
| `DAY_NUMBER_IN_MONTH`     | `NOT NULL` | `NUMBER(2)`   |
| `CALENDAR_WEEK_NUMBER`    | `NOT NULL` | `NUMBER(2)`   |
| `FISCAL_WEEK_NUMBER`      | `NOT NULL` | `NUMBER(2)`   |
| `WEEK_ENDING_DAY`         | `NOT NULL` | `DATE`        |
| `WEEK_ENDING_DAY_ID`      | `NOT NULL` | `NUMBER`      |
| `CALENDAR_MONTH_NUMBER`   | `NOT NULL` | `NUMBER(2)`   |
| `FISCAL_MONTH_NUMBER`     | `NOT NULL` | `NUMBER(2)`   |
| `CALENDAR_MONTH_DESC`     | `NOT NULL` | `VARCHAR2(8)` |
| `CALENDAR_MONTH_ID`       | `NOT NULL` | `NUMBER`      |
| `FISCAL_MONTH_DESC`       | `NOT NULL` | `VARCHAR2(8)` |
| `FISCAL_MONTH_ID`         | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_CAL_MONTH`       | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_FIS_MONTH`       | `NOT NULL` | `NUMBER`      |
| `END_OF_CAL_MONTH`        | `NOT NULL` | `DATE`        |
| `END_OF_FIS_MONTH`        | `NOT NULL` | `DATE`        |
| `CALENDAR_MONTH_NAME`     | `NOT NULL` | `VARCHAR2(9)` |
| `FISCAL_MONTH_NAME`       | `NOT NULL` | `VARCHAR2(9)` |
| `CALENDAR_QUARTER_DESC`   | `NOT NULL` | `CHAR(7)`     |
| `CALENBDAR_QUARTER_ID`    | `NOT NULL` | `NUMBER`      |
| `FISCAL_QUARTER_DESC`     | `NOT NULL` | `CHAR(7)`     |
| `FISCAL_QUARTER_ID`       | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_CAL_QUARTER`     | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_FIS_QUARTER`     | `NOT NULL` | `NUMBER`      |
| `END_OF_CAL_QUARTER`      | `NOT NULL` | `DATE`        |
| `END_OF_FIS_QUARTER`      | `NOT NULL` | `DATE`        |
| `CALENDAR_QUARTER_NUMBER` | `NOT NULL` | `NUMBER(1)`   |
| `FISCAL_QUARTER_NUMBER`   | `NOT NULL` | `NUMBER(1)`   |
| `CALENDAR_YEAR`           | `NOT NULL` | `NUMBER(4)`   |
| `CALENDAR_YEAR_ID`        | `NOT NULL` | `NUMBER`      |
| `FISCAL_YEAR`             | `NOT NULL` | `NUMBER(4)`   |
| `FISCAL_YEAR_ID`          | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_CAL_YEAR`        | `NOT NULL` | `NUMBER`      |
| `DAYS_IN_FIS_YEAR`        | `NOT NULL` | `NUMBER`      |
| `END_OF_CAL_YEAR`         | `NOT NULL` | `DATE`        |
| `END_OF_FIS_YEAR`         | `NOT NULL` | `DATE`        |
