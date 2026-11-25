This preface contains:

- Versioning of Oracle Data Masking and Subsetting

- Changes in Oracle Data Masking and Subsetting Release 13.2

- Changes in Oracle Data Masking and Subsetting Release 13.1

### Versioning of Oracle Data Masking and Subsetting

The Oracle Data Masking and Subsetting version is based on the version of the Oracle Enterprise Manager Database Plug-in.

Oracle Data Masking and Subsetting is a part of the Oracle Enterprise Manager Database Plug-in. In general, multiple Oracle Enterprise Manager Database Plug-in versions are released during the life cycle of the Oracle Enterprise Manager version. For example, Oracle Enterprise Manager Database Plug-in versions 12.1.0.6 and 12.1.0.7 were released during the life cycle of the Oracle Enterprise Manager version 12.1.0.4 and Oracle Enterprise Manager Database Plug-in version 13.1.0.0 was released during the life cycle of the Oracle Enterprise Manager version 13.1.

### Changes in Oracle Data Masking and Subsetting Release 13.2

This section describes the features introduced in Oracle Data Masking and Subsetting Release 13.2.

- Enhanced Support for Discovering Non-Dictionary Based Referential Relationships

- Support for Handling Object Names With Size up to 128 Bytes

- Support for Importing and Exporting the Complete Database

- Support for Retaining the Existing Schema While Importing the Subset Dump

#### Enhanced Support for Discovering Non-Dictionary Based Referential Relationships

With Oracle Data Masking and Subsetting release 13.2, the ability to discover non-dictionary based referential relationships has been enhanced. Users can now discover potential non-dictionary based referential relationships by matching column values, in addition to column names. For more information on using this feature, see the [Creating an ADM](data_modeling.md) section.

#### Support for Handling Object Names With Size up to 128 Bytes

The repository tables in Oracle Data Masking and Subsetting are now compatible to store the target database object names with size up to 128 bytes. Prior releases of Oracle Data Masking and Subsetting could handle target database object names up to 30 bytes only.

#### Support for Importing and Exporting the Complete Database

Oracle Data Masking and Subsetting provides the flexibility to import and export the complete database while simultaneously masking or subsetting some schemas in the database. When a user chooses a Full database In-Export data masking option, the tables in the masking definition are exported as masked, and the remaining tables are exported as they are. Similarly, when a user chooses a Full database In-Export data subsetting option, the tables in the subset definition are subsetted based on the object rules defined in the subset definition, and the remaining tables are exported without applying subsetting.

#### Support for Retaining the Existing Schema While Importing the Subset Dump

Oracle Data Masking and Subsetting allows users to retain the original tables of the schema by selecting the schema remap option while importing a subset dump. In prior releases of Oracle Data Masking and Subsetting, the existing schema was being dropped when users selected the schema remap option. For more information, see the [Importing a Subset Dump](data_subsetting.md) section.

### Changes in Oracle Data Masking and Subsetting Release 13.1

This section describes the features introduced in Oracle Data Masking and Subsetting Release 13.1.

- Support for Non-Dictionary Based Referential Relationships (Application Defined Relationships)

- Subset Data Based on Table Partitions

- Support for Application Data Modeling and Data Masking of Edition View Objects

#### Support for Non-Dictionary Based Referential Relationships (Application Defined Relationships)

Oracle Data Masking and Subsetting supports non-dictionary based referential relationships. The non-dictionary based referential relationships are application-specific referential relationships that are not defined in the Oracle data dictionary. For more information on using this feature, see the [Application Data Modeling](data_modeling.md) chapter.

#### Subset Data Based on Table Partitions

Oracle Data Masking and Subsetting provides the ability to subset data based on partitioning. Subsetting based on partition and sub-partition enables you to include only those rows in the subset that belong to a particular partition or sub-partition of a table. For more information on using this feature, see the [Data Subsetting](data_subsetting.md) chapter.

#### Support for Application Data Modeling and Data Masking of Edition View Objects

Application Data Modeling and Data Masking components have been enhanced to support Edition Views. Support for Edition Views is essential to discover and mask applications such as Oracle E-Business Suite 12.2 or higher, which use edition-based redefinition for patching applications or upgrading databases, with minimal downtime.

You can create an application data model with edition views, and mark the edition view columns as sensitive. Data Masking will mask the base column that the edition view column is referring to.

For more information on Edition Views, see the [Oracle Database Advanced Application Developer's Guide](https://docs.oracle.com/cd/E11882_01/appdev.112/e41502/adfns_editions.htm#ADFNS020).

### Changes in Oracle Data Masking and Subsetting Release 12.1

The following are changes in Oracle Data Masking and Subsetting User's Guide Release 12.1.0.8.

- Support for Secure Shell Key-based Host Authentication

- Support for Data Masking and Subsetting in Oracle Cloud

#### Support for Secure Shell Key-based Host Authentication

Oracle Data Masking and Subsetting supports Secure Shell (SSH) Key-based Host authentication to the target database host. For more information, see the [Oracle Enterprise Manager Cloud Control Security Guide](http://docs.oracle.com/cd/E24628_01/doc.121/e36415/sec_features.htm#CJAFJJEA).

#### Support for Data Masking and Subsetting in Oracle Cloud

Oracle Data Masking and Subsetting provides the ability to model, mask, and subset the databases that are hosted in Oracle Cloud (DBaaS), in addition to the on-premise databases. In order to mask and subset data in Oracle Cloud (DBaaS), you must register the database in Oracle Cloud as a target for Oracle Enterprise Manager. For more information, see the [Oracle Enterprise Manager Cloud Control Administrator's Guide](http://docs.oracle.com/cd/E24628_01/doc.121/e24473/hybrid-cloud.htm).
