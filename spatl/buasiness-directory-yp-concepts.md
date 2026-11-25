## 13  Business Directory (Yellow Pages) Support

Oracle Spatial and Graph provides support for OpenLS business directory (Yellow Pages, or YP) services.

**Note:**

Oracle Spatial and Graph business directory services are not supported in Oracle Autonomous Database both in Serverless and Dedicated deployments.

- Business Directory Concepts
  Business directory services provide lists of businesses in a given area and matching a specified name or category.
- Using the Business Directory Capabilities
  To use the Oracle Spatial business directory capabilities, you must use data provided by a business directory (YP) vendor.
- Data Structures for Business Directory Support
  After you acquire the business directory data and invoke the appropriate procedure to load it into the database, the procedure populates the following tables, all owned by the MDSYS schema, which are used for business directory support.

**Parent topic:** [Spatial Web Services](spatial-web-services.md)

### 13.1 Business Directory Concepts

Business directory services provide lists of businesses in a given area and matching a specified name or category.

Business directory data comes from third-party providers of such data. These providers probably have different business categories, and even different hierarchical structures. A unifying pattern in the various approaches is that businesses are categorized by subject and location. The location component is well understood; for example, for the United States, either a ZIP code or the combination of a city and state, and optionally a specific address, can be used to determine the location from which to start searching.

The categorization of businesses, on the other hand, is not uniformly implemented. Some providers offer a flat list of categories, user-selected by simple substring matching. Others offer a 3-level or 4-level hierarchical organization of subcategories, often with a fanout (maximum number of child categories at a level) of 20 to 50, and sometimes more than 100. A user might start the hierarchy traversal at the root of the hierarchy (by default). Alternatively, a user might enter a keyword that is matched to an appropriate starting point within the hierarchy. Such keyword matching might go beyond simple substring matching and result in more intelligent choices.

**Parent topic:** Business Directory (Yellow Pages) Support

### 13.2 Using the Business Directory Capabilities

To use the Oracle Spatial business directory capabilities, you must use data provided by a business directory (YP) vendor.

The data must be in the format supported by the Oracle Spatial and Graph OpenLS support (see OPENLS_DIR_BUSINESSES Table).

To submit users' directory services requests and to return the responses, use the OpenLS web services API, which is introduced in [OpenLS Application Programming Interfaces](openls-concepts.md). For information about directory services requests and responses, with examples, see [OpenLS Service Support and Examples](openls-concepts.md).

**Parent topic:** Business Directory (Yellow Pages) Support

### 13.3 Data Structures for Business Directory Support

After you acquire the business directory data and invoke the appropriate procedure to load it into the database, the procedure populates the following tables, all owned by the MDSYS schema, which are used for business directory support.

- OPENLS_DIR_BUSINESSES

- OPENLS_DIR_BUSINESS_CHAINS

- OPENLS_DIR_CATEGORIES

- OPENLS_DIR_CATEGORIZATIONS

- OPENLS_DIR_CATEGORY_TYPES

- OPENLS_DIR_SYNONYMS

In some tables, some rows have null values for some columns, because the information does not apply in this instance or because the data provider did not supply a value.

The following sections describe these tables, in alphabetical order by table name.

- OPENLS_DIR_BUSINESSES Table
- OPENLS_DIR_BUSINESS_CHAINS Table
- OPENLS_DIR_CATEGORIES Table
- OPENLS_DIR_CATEGORIZATIONS Table
- OPENLS_DIR_CATEGORY_TYPES Table
- OPENLS_DIR_SYNONYMS Table

**Parent topic:** Business Directory (Yellow Pages) Support

#### 13.3.1 OPENLS_DIR_BUSINESSES Table

The OPENLS_DIR_BUSINESSES table stores information about each business (that is, each business that has an address). If the business is part of a larger business chain, the CHAIN_ID column is a foreign key to the CHAIN_ID column in the OPENLS_DIR_BUSINESS_CHAINS table (described in OPENLS_DIR_BUSINESS_CHAINS Table).

The OPENLS_DIR_BUSINESSES table contains one row for each business, and it contains the columns shown in Table 13-1.

Table 13-1 OPENLS_DIR_BUSINESSES Table

| Column Name                   | Data Type      | Description                                                                                                   |
|:------------------------------|:---------------|:--------------------------------------------------------------------------------------------------------------|
| BUSINESS_ID                   | NUMBER         | Business ID number. (Required)                                                                                |
| BUSINESS_NAME                 | VARCHAR2(128)  | Area name. (Required)                                                                                         |
| CHAIN_ID                      | NUMBER         | ID number of the business chain (in the OPENLS_BIR_BUSINESS_CHAIN table), if the business is part of a chain. |
| DESCRIPTION                   | VARCHAR2(1024) | Description of the business.                                                                                  |
| PHONE                         | VARCHAR2(64)   | Phone number, in an appropriate format for the location.                                                      |
| COUNTRY                       | VARCHAR2(64)   | Country code or name. (Required)                                                                              |
| COUNTRY_SUBDIVISION           | VARCHAR2(128)  | Subdivision of the country, if applicable.                                                                    |
| COUNTRY_SECONDARY_SUBDIVISION | VARCHAR2(128)  | Subdivision within COUNTRY_SUBDIVISION, if applicable.                                                        |
| MUNICIPALITY                  | VARCHAR2(128)  | Municipality name.                                                                                            |
| MUNICIPALITY_SUBDIVISION      | VARCHAR2(128)  | Subdivision within MUNICIPALITY, if applicable.                                                               |
| POSTAL_CODE                   | VARCHAR2(32)   | Postal code (for example, 5-digit ZIP code in the United Stated and Canada). (Required)                       |
| POSTAL_CODE_EXT               | VARCHAR2(32)   | Postal code extension (for example, 4-digit extension if the 5-4 ZIP code format is used).                    |
| STREET                        | VARCHAR2(128)  | Street address, including house or unit number. (Required)                                                    |
| INTERSECTING_STREET           | VARCHAR2(128)  | Name of the street (if any) that intersects STREET at this address.                                           |
| BUILDING                      | VARCHAR2(128)  | Name of the building that includes this address.                                                              |
| PARAMETERS                    | XMLTYPE        | XML document with additional information about the business.                                                  |
| GEOM                          | SDO_GEOMETRY   | Point geometry representing the address of the business.                                                      |

**Parent topic:** Data Structures for Business Directory Support

#### 13.3.2 OPENLS_DIR_BUSINESS_CHAINS Table

The OPENLS_DIR_BUSINESS_CHAINS table stores information about each business chain. A business chain is a business that has multiple associated businesses; for example, a restaurant chain has multiple restaurants that have the same name and offer basically the same menu. If the business is part of a business chain, the row for that business in the OPENLS_DIR_BUSINESSES table (described in OPENLS_DIR_BUSINESSES Table) contains a CHAIN_ID column value that matches a value in the CHAIN_ID column in the OPENLS_DIR_BUSINESS_CHAINS table.

The OPENLS_DIR_BUSINESS_CHAINS table contains one row for each business chain, and it contains the columns shown in Table 13-2.

Table 13-2 OPENLS_DIR_BUSINESS_CHAINS Table

| Column Name | Data Type     | Description                          |
|:------------|:--------------|:-------------------------------------|
| CHAIN_ID    | NUMBER        | Business chain ID number. (Required) |
| CHAIN_NAME  | VARCHAR2(128) | Business chain name.                 |

**Parent topic:** Data Structures for Business Directory Support

#### 13.3.3 OPENLS_DIR_CATEGORIES Table

The OPENLS_DIR_CATEGORIES table stores information about each category into which a business can be placed. If the data provider uses a category hierarchy, this table contains rows for categories at all levels of the hierarchy, using the PARENT_ID column to indicate the parent category of a child category. For example, a Restaurants category might be the parent of several child categories, one of which might be Chinese.

The OPENLS_DIR_CATEGORIES table contains one row for each category, and it contains the columns shown in Table 13-3.

Table 13-3 OPENLS_DIR_CATEGORIES Table

| Column Name      | Data Type     | Description                                                                                                                                                                  |
|:-----------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CATEGORY_ID      | VARCHAR2(32)  | Category ID string. (Required)                                                                                                                                               |
| CATEGORY_TYPE_ID | NUMBER        | Category type ID number. Must match a value in the CATEGORY_TYPE_ID column of the OPENLS_DIR_CATEGORY_TYPES table (described in OPENLS_DIR_CATEGORY_TYPES Table). (Required) |
| CATEGORY_NAME    | VARCHAR2(128) | Category name. (Required)                                                                                                                                                    |
| PARENT_ID        | VARCHAR2(32)  | CATEGORY_ID value of the parent category, if any, for this category.                                                                                                         |
| PARAMETERS       | XMLTYPE       | XML document with additional information about the category.                                                                                                                 |

**Parent topic:** Data Structures for Business Directory Support

#### 13.3.4 OPENLS_DIR_CATEGORIZATIONS Table

The OPENLS_DIR_CATEGORIZATIONS table stores information about associations of businesses with categories. Each business can be in multiple categories; and the categories for a business can be independent of each other or in a parent-child relationship, or both. For example, a store that sells books and music CDs might be in the categories for Bookstores, Music, and its child category Music Stores, in which case there will be three rows for that business in this table.

The OPENLS_DIR_CATEGORIZATIONS table contains one row for each association of a business with a category, and it contains the columns shown in Table 13-4.

Table 13-4 OPENLS_DIR_CATEGORIZATIONS Table

| Column Name                  | Data Type    | Description                                                                                                                                                                                                           |
|:-----------------------------|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BUSINESS_ID                  | NUMBER       | Business ID. Must match a value in the BUSINESS_ID column of the OPENLS_DIR_BUSNESSES table (described in OPENLS_DIR_BUSINESSES Table). (Required)                                                                    |
| CATEGORY_ID                  | VARCHAR2(32) | Category ID string. The CATEGORY_ID and CATEGORY_TYPE_ID values must match corresponding column values in a single row in the OPENLS_DIR_CATEGORIES table (described in OPENLS_DIR_CATEGORIES Table). (Required)      |
| CATEGORY_TYPE_ID             | NUMBER       | Category type ID number. The CATEGORY_ID and CATEGORY_TYPE_ID values must match corresponding column values in a single row in the OPENLS_DIR_CATEGORIES table (described in OPENLS_DIR_CATEGORIES Table). (Required) |
| CATEGORIZATION_TYPE          | VARCHAR2(8)  | `EXPLICIT` (the default) or `IMPLICIT`.                                                                                                                                                                               |
| USER_SPECIFIC_CATEGORIZATION | VARCHAR2(32) | User-specified categorization, if any.                                                                                                                                                                                |
| PARAMETERS                   | XMLTYPE      | XML document with additional information about the association of the business with the category.                                                                                                                     |

**Parent topic:** Data Structures for Business Directory Support

#### 13.3.5 OPENLS_DIR_CATEGORY_TYPES Table

The OPENLS_DIR_CATEGORY_TYPES table stores information about category types. This table contains the columns shown in Table 13-5.

Table 13-5 OPENLS_DIR_CATEGORY_TYPES Table

| Column Name        | Data Type     | Description                                                       |
|:-------------------|:--------------|:------------------------------------------------------------------|
| CATEGORY_TYPE_ID   | NUMBER        | Category type ID number. (Required)                               |
| CATEGORY_TYPE_NAME | VARCHAR2(128) | Name of the category type. (Required)                             |
| PARAMETERS         | XMLTYPE       | XML document with additional information about the category type. |

**Parent topic:** Data Structures for Business Directory Support

#### 13.3.6 OPENLS_DIR_SYNONYMS Table

The OPENLS_DIR_SYNONYMS table stores information about synonyms for categories. Synonyms can be created to expand the number of terms (strings) associated with a category, so that users get more complete and meaningful results from a search.

The OPENLS_DIR_SYNONYMS table contains one row for each synonym definition, and it contains the columns shown in Table 13-6.

Table 13-6 OPENLS_DIR_SYNONYMS Table

| Column Name   | Data Type     | Description                                                                                                 |
|:--------------|:--------------|:------------------------------------------------------------------------------------------------------------|
| STANDARD_NAME | VARCHAR2(128) | Standard name of a category, as the user might enter it.                                                    |
| CATEGORY      | VARCHAR2(128) | Category name, as it appears in the OPENLS_DIR_CATEGORIES table (described in OPENLS_DIR_CATEGORIES Table). |
| AKA           | VARCHAR2(128) | .Additional or alternate name for the category. ("AKA" stands for "also known as.")                         |

**Parent topic:** Data Structures for Business Directory Support
