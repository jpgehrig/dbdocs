This guide explains how to use the programmatic interfaces to Oracle Data Mining and how to use features of Oracle Database to administer Oracle Data Mining. This guide presents the tools and procedures for implementing the concepts that are presented in [Oracle Data Mining Concepts](../dmcon/introductions.md).

This preface contains these topics:

- Audience

- Documentation Accessibility

- Related Documentation

- Conventions

### Audience

This guide is intended for application developers and database administrators who are familiar with SQL programming and Oracle Database administration and who have a basic understanding of data mining concepts.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Diversity and Inclusion

Oracle is fully committed to diversity and inclusion. Oracle respects and values having a diverse workforce that increases thought leadership and innovation. As part of our initiative to build a more inclusive culture that positively impacts our employees, customers, and partners, we are working to remove insensitive terms from our products and documentation. We are also mindful of the necessity to maintain compatibility with our customers' existing technologies and the need to ensure continuity of service as Oracle's offerings and industry standards evolve. Because of these technical constraints, our effort to remove insensitive terms is ongoing and will take time and external cooperation.

### Related Documentation

Oracle Data Mining components associated with Oracle Database are included with the database license. The Oracle Data Mining for SQL documents are available from the Data Warehousing and Business Intelligence page of the Oracle Database online documentation library:

[`Oracle Database Data Warehousing`](../data-warehousing.md)

The following manuals document Oracle Data Mining:

- [Oracle Data Mining Concepts](../dmcon/introductions.md)

- [Oracle Data Mining User’s Guide](data-mining-SQL.md) (this guide)

- Oracle Data Mining API Guide

  **Note:**

  The virtual book combines key passages from the two Data Mining manuals with related reference documentation in Oracle Database PL/SQL Packages and Types Reference, Oracle Database SQL Language Reference, and Oracle Database Reference.

- Oracle Database PL/SQL Packages and Types Reference (PL/SQL packages)

  - [`DBMS_DATA_MINING`](../arpls/DBMS_DATA_MINING.md)

  - [`DBMS_DATA_MINING_TRANSFORM`](../arpls/DBMS_DATA_MINING_TRANSFORM.md)

  - [`DBMS_PREDICTIVE_ANALYTICS`](../arpls/DBMS_PREDICTIVE_ANALYTICS.md)

- Oracle Database Reference (data dictionary views for `ALL_`, `USER_`, and `DBA_`)

  - [`ALL_MINING_MODELS`](../refrn/ALL_MINING_MODELS.md)

  - [`ALL_MINING_MODEL_ATTRIBUTES`](../refrn/ALL_MINING_MODEL_ATTRIBUTES.md)

  - [`ALL_MINING_MODEL_SETTINGS`](../refrn/ALL_MINING_MODEL_SETTINGS.md)

- Oracle Database SQL Language Reference (Data Mining functions)

  - [`CLUSTER_DETAILS`](../sqlrf/CLUSTER_DETAILS.md), [`CLUSTER_DISTANCE`](../sqlrf/CLUSTER_DISTANCE.md), [`CLUSTER_ID`](../sqlrf/CLUSTER_ID.md), [`CLUSTER_PROBABILITY`](../sqlrf/CLUSTER_PROBABILITY.md), [`CLUSTER_SET`](../sqlrf/CLUSTER_SET.md)

  - [`FEATURE_DETAILS`](../sqlrf/FEATURE_DETAILS.md), [`FEATURE_ID`](../sqlrf/FEATURE_ID.md), [`FEATURE_SET`](../sqlrf/FEATURE_SET.md), [`FEATURE_VALUE`](../sqlrf/FEATURE_VALUE.md)

  - [`PREDICTION`](../sqlrf/PREDICTION.md), [`PREDICTION_BOUNDS`](../sqlrf/PREDICTION_BOUNDS.md), [`PREDICTION_COST`](../sqlrf/PREDICTION_COST.md), [`PREDICTION_DETAILS`](../sqlrf/PREDICTION_DETAILS.md), [`PREDICTION_PROBABILITY`](../sqlrf/PREDICTION_PROBABILITY.md), [`PREDICTION_SET`](../sqlrf/PREDICTION_SET.md)

#### Oracle Data Mining Resources on the Oracle Technology Network

The Oracle Data Mining page on the Oracle Technology Network (OTN) provides a wealth of information, including white papers, demonstrations, blogs, discussion forums, and Oracle By Example tutorials:

[`Oracle Data Mining`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dmprg&id=datamining_index)

You can download Oracle Data Miner, the graphical user interface to Oracle Data Mining, from this site:

[`Oracle Data Miner`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dmprg&id=dataminer_wf)

#### Application Development and Database Administration Documentation

For documentation to assist you in developing database applications and in administering Oracle Database, refer to the following:

- [Oracle Database Concepts](../cncpt/oracle-database-administration-and-application-development.md)

- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

- [Oracle Database Development Guide](../adfns/fundamentals.md)

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
