Numerics  A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  Z  

------------------------------------------------------------------------

## Numerics

- 3NF [2.3](data-warehouse-logical-design.md)

------------------------------------------------------------------------

## A

- about
  - refresh statistics [9.1](monitoring-materialized-view-refresh.md)
- accessing
  - real-time materialized views [6.7.1.2](advanced-materialized-views.md)
- ADO, and IM column store [2.5.3](data-warehouse-logical-design.md)
- aggregates [5.2.1](basic-materialized-views.md), [12.9.5](advanced-query-rewrite-materialized-views.md)
  - computability check [12.1.3.4](advanced-query-rewrite-materialized-views.md)
- aggregation
  - In-Memory Column Store [20.8.6](sql-aggregation-data-warehouses.md)
  - VECTOR GROUP BY [20.8.6](sql-aggregation-data-warehouses.md)
- alter analytic views [24.8](overview-analytic-views.md)
- altering dimensions [10.6](dimensions.md)
- alternate keys
  - of an attribute dimension level [25.4](analytic-view-attribute-dimensions.md)
- amortization
  - calculating [22.5.6](sql-modeling-data-warehouses.md)
- analytic functions [22.3.5](sql-modeling-data-warehouses.md)
  - concepts [19.1](sql-analysis-reporting-data-warehouses.md)
- analytic processing
  - materialized views [6.2](advanced-materialized-views.md)
- analytic views
  - about [26.1](analytic-view-objects.md)
  - alter or drop [24.8](overview-analytic-views.md)
  - and materialized views [6.2.1](advanced-materialized-views.md)
  - APIs [24.3](overview-analytic-views.md)
  - compilation states [24.4](overview-analytic-views.md)
  - creating [26.3](analytic-view-objects.md)
  - described [24.1](overview-analytic-views.md)
  - example of creating [24.9.4](overview-analytic-views.md)
  - example of filtering facts [26.6.1](analytic-view-objects.md), [26.6.3](analytic-view-objects.md)
  - example of using added measures [26.6.2](analytic-view-objects.md), [26.6.3](analytic-view-objects.md)
  - example scripts [24.9](overview-analytic-views.md)
  - hierarchical attributes [25.2](analytic-view-attribute-dimensions.md)
  - hierarchies [25.1](analytic-view-attribute-dimensions.md)
  - measures [26.2](analytic-view-objects.md)
  - privileges for [24.2](overview-analytic-views.md)
  - sharing with application containers [24.7](overview-analytic-views.md)
  - tables for examples [24.9.1](overview-analytic-views.md)
- application containers, sharing analytic views with [24.7](overview-analytic-views.md)
- applications
  - decision support systems (DSS) [4.1.2](data-warehouse-optimizations-techniques.md)
- APPROX_COUNT function [4.7](data-warehouse-optimizations-techniques.md)
- APPROX_RANK function [19.2.1.2](sql-analysis-reporting-data-warehouses.md)
- APPROX_SUM function [4.7](data-warehouse-optimizations-techniques.md)
- approximate aggregations [19.3.1](sql-analysis-reporting-data-warehouses.md)
- approximate query processing [4.6](data-warehouse-optimizations-techniques.md)
- approximate top-n query processing [4.7](data-warehouse-optimizations-techniques.md)
- approximate values
  - percentile functions [19.3.4.5](sql-analysis-reporting-data-warehouses.md)
- architecture
  - data warehouse [1.4](introduction-data-warehouse-concepts.md)
- attribute-clustered tables [13.1](attribute-clustering.md)
- attribute clustering [13.1](attribute-clustering.md)
  - adding to existing table [13.2.4.1](attribute-clustering.md)
  - advantages [13.1.5](attribute-clustering.md)
  - data dictionary views [13.3](attribute-clustering.md)
  - dropping [13.2.4.3](attribute-clustering.md)
  - guidelines [13.1.4](attribute-clustering.md)
  - methods [13.1.1](attribute-clustering.md)
  - modifying [13.2.4.2](attribute-clustering.md)
  - privileges [13.2.1](attribute-clustering.md)
  - types [13.1.2](attribute-clustering.md)
    - interleaved ordering [13.1.2.2](attribute-clustering.md)
    - linear ordering [13.1.2.1](attribute-clustering.md), [13.2.2](attribute-clustering.md), [13.2.3](attribute-clustering.md)
  - using hints for DML [13.2.4.4](attribute-clustering.md)
- attribute dimensions
  - about [25.1](analytic-view-attribute-dimensions.md)
  - attributes [25.2](analytic-view-attribute-dimensions.md)
  - examples of creating [24.9.2](overview-analytic-views.md)
  - level keys [25.4](analytic-view-attribute-dimensions.md)
  - order of level members [25.3](analytic-view-attribute-dimensions.md)
  - privileges for [24.2](overview-analytic-views.md)
- attributes [2.2](data-warehouse-logical-design.md)
  - attribute dimension [25.2](analytic-view-attribute-dimensions.md)
  - creating hierarchies using [26.5](analytic-view-objects.md)
- automatic big table caching
  - about [2.6](data-warehouse-logical-design.md)

------------------------------------------------------------------------

## B

- base measures
  - examples of [26.3](analytic-view-objects.md)
- bind variables
  - with query rewrite [12.3.12](advanced-query-rewrite-materialized-views.md)
- bitmap indexes [4.1.1](data-warehouse-optimizations-techniques.md)
  - nulls and [4.1.1.1](data-warehouse-optimizations-techniques.md)
  - on partitioned tables [4.1.1.2](data-warehouse-optimizations-techniques.md)
  - parallel query and DML [4.1.2](data-warehouse-optimizations-techniques.md)
- bitmap join indexes [4.1.5](data-warehouse-optimizations-techniques.md)
- B-tree indexes [4.1.6](data-warehouse-optimizations-techniques.md)
  - bitmap indexes versus [4.1.3](data-warehouse-optimizations-techniques.md)
- build methods [5.3.5](basic-materialized-views.md)
- business intelligence [1.1](introduction-data-warehouse-concepts.md)
  - queries [23](advanced-analytical-sql-data-warehouses.md)
- business rules
  - violation of [18.4.1](loading-transformation-date-warehouses.md)

------------------------------------------------------------------------

## C

- calculated measures [26.2](analytic-view-objects.md)
  - examples of [26.4](analytic-view-objects.md), [26.6.2](analytic-view-objects.md), [26.6.3](analytic-view-objects.md)
- CAPTION classification [24.6](overview-analytic-views.md)
- cardinality
  - degree of [4.1.3](data-warehouse-optimizations-techniques.md)
- CASE expressions [19.8.3](sql-analysis-reporting-data-warehouses.md)
- cell referencing [22.2.4](sql-modeling-data-warehouses.md)
- classifications
  - analytic view [24.6](overview-analytic-views.md)
- columns
  - cardinality [4.1.3](data-warehouse-optimizations-techniques.md)
- common joins [12.1.3.1.1](advanced-query-rewrite-materialized-views.md)
- common tasks
  - in data warehouses [1.3](introduction-data-warehouse-concepts.md)
- compilation states
  - of analytic views [24.4](overview-analytic-views.md)
- complete refresh [7.1.1](refreshing-materialized-views.md)
- complex queries
  - snowflake schemas [2.4.3](data-warehouse-logical-design.md)
- composite
  - columns [20.6](sql-aggregation-data-warehouses.md)
- compression
  - See data segment compression [5.3.4](basic-materialized-views.md)
- concatenated groupings [20.7](sql-aggregation-data-warehouses.md)
- concatenated ROLLUP [20.10.1](sql-aggregation-data-warehouses.md)
- constraints [4.2](data-warehouse-optimizations-techniques.md), [10.4](dimensions.md)
  - foreign key [4.2.2.2](data-warehouse-optimizations-techniques.md)
  - RELY [4.2.2.3](data-warehouse-optimizations-techniques.md)
  - states [4.2.1](data-warehouse-optimizations-techniques.md)
  - unique [4.2.2.1](data-warehouse-optimizations-techniques.md)
  - view [4.2.2.7](data-warehouse-optimizations-techniques.md), [12.3.6](advanced-query-rewrite-materialized-views.md)
  - with partitioning [4.2.2.6](data-warehouse-optimizations-techniques.md)
  - with query rewrite [12.9.1](advanced-query-rewrite-materialized-views.md)
- cost-based rewrite [12.1.1](advanced-query-rewrite-materialized-views.md)
- CREATE DIMENSION statement [10.2](dimensions.md)
- CREATE MATERIALIZED VIEW statement [5.3](basic-materialized-views.md)
  - enabling query rewrite [11.2.1](basic-query-rewrite-materialized-views.md)
- creating
  - materialized views with approximate queries [5.5](basic-materialized-views.md)
  - real-time materialized views [6.7.2](advanced-materialized-views.md)
  - zone maps [14.2.2.2](using-zone-maps.md)
    - with attribute clustering [14.2.2.1](using-zone-maps.md)
- CUBE clause [20.3](sql-aggregation-data-warehouses.md)
  - partial [20.3.3](sql-aggregation-data-warehouses.md)
  - when to use [20.3.1](sql-aggregation-data-warehouses.md)
- cubes
  - hierarchical [6.2.2](advanced-materialized-views.md)
  - materialized views [6.2.2](advanced-materialized-views.md)
- CUME_DIST function [19.2.1.4](sql-analysis-reporting-data-warehouses.md)

------------------------------------------------------------------------

## D

- data
  - nonvolatile [1.1](introduction-data-warehouse-concepts.md)
  - purging [7.6.3](refreshing-materialized-views.md)
  - sufficiency check [12.1.3.2](advanced-query-rewrite-materialized-views.md)
  - transformation [18.3](loading-transformation-date-warehouses.md)
  - transportation [17.2.1](transportation-data-warehouses.md)
- database
  - staging [5.1](basic-materialized-views.md)
- data compression [4.4.1](data-warehouse-optimizations-techniques.md)
  - See data segment compression [5.3.4](basic-materialized-views.md)
- data cubes
  - hierarchical [20.7.1](sql-aggregation-data-warehouses.md)
- data densification [19.6](sql-analysis-reporting-data-warehouses.md)
  - time series calculation [19.7](sql-analysis-reporting-data-warehouses.md)
  - with sparse data [19.6.2](sql-analysis-reporting-data-warehouses.md)
- data error handling
  - using SQL [18.4.2.1](loading-transformation-date-warehouses.md)
- data marts [1.4.3](introduction-data-warehouse-concepts.md)
- data rules
  - violation of [18.4.2](loading-transformation-date-warehouses.md)
- data segment compression [3.2.1.2](data-warehouse-physical-design.md)
  - materialized views [5.3.4](basic-materialized-views.md)
  - partitioning [3.2.1.2](data-warehouse-physical-design.md)
- data transformation
  - multistage [18.1.1.1](loading-transformation-date-warehouses.md)
  - pipelined [18.1.1.2](loading-transformation-date-warehouses.md)
- data warehouse [5.1](basic-materialized-views.md)
  - architectures [1.4](introduction-data-warehouse-concepts.md)
  - dimension tables [5.1.6](basic-materialized-views.md)
  - fact tables [5.1.6](basic-materialized-views.md)
  - physical design [3.1](data-warehouse-physical-design.md)
  - refresh tips [7.1.11](refreshing-materialized-views.md)
- data warehouses
  - common tasks [1.3](introduction-data-warehouse-concepts.md)
  - key characteristics of [1.1.1](introduction-data-warehouse-concepts.md)
- date folding
  - with query rewrite [12.3.5](advanced-query-rewrite-materialized-views.md)
- DBMS_ADVISOR
  - TUNE_MVIEW procedure [5.3.6](basic-materialized-views.md)
- DBMS_ERROR package [18.4.2.3](loading-transformation-date-warehouses.md)
- DBMS_MVIEW package [7.1.7](refreshing-materialized-views.md)
  - EXPLAIN_MVIEW procedure [5.10.1](basic-materialized-views.md)
  - EXPLAIN_REWRITE procedure [12.8.2](advanced-query-rewrite-materialized-views.md)
- DBMS_SYNC_REFRESH package [8](synchronous-refresh.md)
- decision support systems (DSS)
  - bitmap indexes [4.1.2](data-warehouse-optimizations-techniques.md)
- degree of cardinality [4.1.3](data-warehouse-optimizations-techniques.md)
- DENSE_RANK function [19.2.1.1](sql-analysis-reporting-data-warehouses.md)
- densification
  - data [19.6](sql-analysis-reporting-data-warehouses.md)
- DESCRIPTION classification [24.6](overview-analytic-views.md)
- design
  - logical [3.1](data-warehouse-physical-design.md)
  - physical [3.1](data-warehouse-physical-design.md)
- DETERMINES
  - clause of an attribute dimension level [25.5](analytic-view-attribute-dimensions.md)
- dimension levels
  - skipping [10.2](dimensions.md)
- dimensions [3.2.6](data-warehouse-physical-design.md), [10.1](dimensions.md), [10.4](dimensions.md)
  - altering [10.6](dimensions.md)
  - analyzing [20.1.1](sql-aggregation-data-warehouses.md)
  - creating [10.2](dimensions.md)
  - definition [10.1](dimensions.md)
  - dimension tables [5.1.6](basic-materialized-views.md)
  - dropping [10.7](dimensions.md)
  - hierarchies [3.2.6.1](data-warehouse-physical-design.md)
  - multiple [20.1.1](sql-aggregation-data-warehouses.md)
  - skipping levels [10.2](dimensions.md)
  - validating [10.5](dimensions.md)
  - with query rewrite [12.9.2](advanced-query-rewrite-materialized-views.md)
- dimension tables [5.1.6](basic-materialized-views.md)
  - normalized [10.2.3](dimensions.md)
- displaying
  - real-time materialized views [6.7.7](advanced-materialized-views.md)
- drilling down [10.1](dimensions.md)
  - hierarchies [10.1](dimensions.md)
- drop analytic views [24.8](overview-analytic-views.md)
- DROP MATERIALIZED VIEW statement
  - prebuilt tables [5.7](basic-materialized-views.md)
- dropping
  - dimensions [10.7](dimensions.md)
  - materialized views [5.9](basic-materialized-views.md)
  - zone maps [14.2.4](using-zone-maps.md)

------------------------------------------------------------------------

## E

- ELT [15.1](etl-overview.md)
- entity [2.2](data-warehouse-logical-design.md)
- error logging [18.4](loading-transformation-date-warehouses.md)
  - table [18.4.2.3](loading-transformation-date-warehouses.md)
- errors
  - handling [18.4](loading-transformation-date-warehouses.md)
- ETL. See extraction, transformation, and loading (ETL) [15.1](etl-overview.md)
- ETL jobs
  - monitoring [18.1.3](loading-transformation-date-warehouses.md)
- examples
  - analytic views [24.9](overview-analytic-views.md)
  - tables for analytic view [24.9.1](overview-analytic-views.md)
  - zone maps
    - join pruning [14.4.2.2](using-zone-maps.md)
    - partition and table scan pruning [14.4.2.1](using-zone-maps.md)
- EXCHANGE PARTITION statement [4.2.2.6](data-warehouse-optimizations-techniques.md)
- execution plans
  - star transformations [4.5.2.2](data-warehouse-optimizations-techniques.md)
- EXPAND_GSET_TO_UNION hint [12.3.9.2](advanced-query-rewrite-materialized-views.md), [12.9.10.4](advanced-query-rewrite-materialized-views.md)
- EXPLAIN_REWRITE procedure [12.8.2](advanced-query-rewrite-materialized-views.md)
- EXPLAIN PLAN statement [12.8.1](advanced-query-rewrite-materialized-views.md)
  - star transformations [4.5.2.2](data-warehouse-optimizations-techniques.md)
- exporting
  - EXP utility [16.3.1.3](extraction-data-warehouses.md)
- expression matching
  - with query rewrite [12.3.11](advanced-query-rewrite-materialized-views.md)
- external tables [18.2.2](loading-transformation-date-warehouses.md)
- extraction, transformation, and loading (ETL) [15.1](etl-overview.md)
  - overview [15.1](etl-overview.md)
  - process [4.2](data-warehouse-optimizations-techniques.md)
- extractions
  - data files [16.3.1](extraction-data-warehouses.md)
  - distributed operations [16.3.2](extraction-data-warehouses.md)
  - full [16.2.1](extraction-data-warehouses.md)
  - incremental [16.2.1](extraction-data-warehouses.md)
  - OCI [16.3.1.2](extraction-data-warehouses.md)
  - online [16.2.2](extraction-data-warehouses.md)
  - overview [16.1](extraction-data-warehouses.md)
  - physical [16.2.2](extraction-data-warehouses.md)
  - Pro\*C [16.3.1.2](extraction-data-warehouses.md)
  - SQL\*Plus [16.3.1.1](extraction-data-warehouses.md)

------------------------------------------------------------------------

## F

- facts [10.1](dimensions.md)
- fast refresh [7.1.2](refreshing-materialized-views.md)
  - restrictions [5.3.8.4](basic-materialized-views.md)
  - with UNION ALL [7.2.4](refreshing-materialized-views.md)
- FETCH
  - row_limiting_clause [19.9](sql-analysis-reporting-data-warehouses.md)
- files
  - ultralarge [3.2.1.1](data-warehouse-physical-design.md)
- filling gaps
  - with data [19.6.6](sql-analysis-reporting-data-warehouses.md)
- FIRST_VALUE function [19.2.5.1](sql-analysis-reporting-data-warehouses.md)
- FIRST/LAST functions [19.3.3](sql-analysis-reporting-data-warehouses.md)
- foreign key
  - constraints [4.2.2.2](data-warehouse-optimizations-techniques.md)
  - joins
    - snowflake schemas [2.4.3](data-warehouse-logical-design.md)
- FOR loops [22.3.1](sql-modeling-data-warehouses.md)
- frequent itemsets [19.8.4](sql-analysis-reporting-data-warehouses.md)
- functions
  - analytic [22.3.5](sql-modeling-data-warehouses.md)
  - APPROX_COUNT [4.7](data-warehouse-optimizations-techniques.md)
  - APPROX_RANK [19.2.1.2](sql-analysis-reporting-data-warehouses.md)
  - APPROX_SUM [4.7](data-warehouse-optimizations-techniques.md)
  - COUNT [4.1.1.1](data-warehouse-optimizations-techniques.md)
  - CUME_DIST [19.2.1.4](sql-analysis-reporting-data-warehouses.md)
  - DENSE_RANK [19.2.1.1](sql-analysis-reporting-data-warehouses.md)
  - FIRST_VALUE [19.2.5.1](sql-analysis-reporting-data-warehouses.md)
  - FIRST/LAST [19.3.3](sql-analysis-reporting-data-warehouses.md)
  - GROUP_ID [20.4.4](sql-aggregation-data-warehouses.md)
  - GROUPING [20.4](sql-aggregation-data-warehouses.md)
  - GROUPING_ID [20.4.3](sql-aggregation-data-warehouses.md)
  - LAG/LEAD [19.2.4](sql-analysis-reporting-data-warehouses.md)
  - LAST_VALUE [19.2.5.1](sql-analysis-reporting-data-warehouses.md)
  - linear regression [19.3.6](sql-analysis-reporting-data-warehouses.md)
  - LISTAGG function [19.3.2](sql-analysis-reporting-data-warehouses.md)
  - NTH_VALUE [19.2.5.2](sql-analysis-reporting-data-warehouses.md)
  - RANK [19.2.1.1](sql-analysis-reporting-data-warehouses.md)
  - ranking [19.2.1](sql-analysis-reporting-data-warehouses.md)
  - RATIO_TO_REPORT [19.2.3.1](sql-analysis-reporting-data-warehouses.md)
  - REGR_INTERCEPT [19.3.6.3](sql-analysis-reporting-data-warehouses.md)
  - REGR_SLOPE [19.3.6.3](sql-analysis-reporting-data-warehouses.md)
  - reporting [19.2.3](sql-analysis-reporting-data-warehouses.md)
  - ROW_NUMBER [19.2.1.7](sql-analysis-reporting-data-warehouses.md)
  - WIDTH_BUCKET [19.8.1](sql-analysis-reporting-data-warehouses.md), [19.8.1.1](sql-analysis-reporting-data-warehouses.md)
  - window [22.3.5](sql-modeling-data-warehouses.md)
  - windowing [19.2.2](sql-analysis-reporting-data-warehouses.md)

------------------------------------------------------------------------

## G

- GROUP_ID function [20.4.4](sql-aggregation-data-warehouses.md)
- grouping
  - compatibility check [12.1.3.3](advanced-query-rewrite-materialized-views.md)
  - conditions [12.9.6](advanced-query-rewrite-materialized-views.md)
- GROUPING_ID function [20.4.3](sql-aggregation-data-warehouses.md)
- GROUPING_SETS expression [20.5](sql-aggregation-data-warehouses.md)
- GROUPING function [20.4](sql-aggregation-data-warehouses.md)
  - when to use [20.4.2](sql-aggregation-data-warehouses.md)

------------------------------------------------------------------------

## H

- hierarchical attributes
  - in a hierarchy [25.2](analytic-view-attribute-dimensions.md)
  - MEMBER_UNIQUE_NAME [25.2](analytic-view-attribute-dimensions.md)
- hierarchical cubes [6.2.2](advanced-materialized-views.md), [20.10.1](sql-aggregation-data-warehouses.md)
  - in SQL [20.10](sql-aggregation-data-warehouses.md)
- hierarchies [10.1](dimensions.md)
  - analytic view [25.1](analytic-view-attribute-dimensions.md)
  - examples of creating [24.9.3](overview-analytic-views.md)
  - hierarchical attributes [25.2](analytic-view-attribute-dimensions.md)
  - how used [3.2.6.1](data-warehouse-physical-design.md)
  - multiple [10.2.2](dimensions.md)
  - overview [3.2.6.1](data-warehouse-physical-design.md)
  - privileges for [24.2](overview-analytic-views.md)
  - rolling up and drilling down [10.1](dimensions.md)
  - using any attribute [26.5](analytic-view-objects.md)
  - validating data of [24.5](overview-analytic-views.md)
- hints
  - EXPAND_GSET_TO_UNION [12.3.9.2](advanced-query-rewrite-materialized-views.md), [12.9.10.4](advanced-query-rewrite-materialized-views.md)
  - NOWRITE [12.9.10.1](advanced-query-rewrite-materialized-views.md)
  - query rewrite [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
  - REWRITE [12.9.10.1](advanced-query-rewrite-materialized-views.md)
  - REWRITE_OR_ERROR [12.9.10.2](advanced-query-rewrite-materialized-views.md)
- histograms
  - creating with user-defined buckets [19.8.3.1](sql-analysis-reporting-data-warehouses.md)
- hypothetical rank [19.3.5](sql-analysis-reporting-data-warehouses.md)

------------------------------------------------------------------------

## I

- IM column store, managing contents [2.5.3](data-warehouse-logical-design.md)
- indexes
  - bitmap indexes [4.1.1.2](data-warehouse-optimizations-techniques.md)
  - bitmap join [4.1.5](data-warehouse-optimizations-techniques.md)
  - B-tree [4.1.6](data-warehouse-optimizations-techniques.md)
  - cardinality [4.1.3](data-warehouse-optimizations-techniques.md)
  - nulls and [4.1.1.1](data-warehouse-optimizations-techniques.md)
  - partitioned tables [4.1.1.2](data-warehouse-optimizations-techniques.md)
- initialization parameters
  - QUERY_REWRITE_ENABLED [11.2.1](basic-query-rewrite-materialized-views.md)
- In-Memory aggregation [20.8.6](sql-aggregation-data-warehouses.md)
- In-Memory Column Store
  - aggregation [20.8.6](sql-aggregation-data-warehouses.md)
- in-memory expressions [2.5.1](data-warehouse-logical-design.md)
- in-memory virtual columns [2.5.2](data-warehouse-logical-design.md)
- integrity constraints [4.2](data-warehouse-optimizations-techniques.md)
- invalidating
  - materialized views [6.5](advanced-materialized-views.md)
- itemsets
  - frequent [19.8.4](sql-analysis-reporting-data-warehouses.md)

------------------------------------------------------------------------

## J

- join compatibility [12.1.3.1](advanced-query-rewrite-materialized-views.md)

------------------------------------------------------------------------

## K

- key lookups [18.5.1](loading-transformation-date-warehouses.md)
- keys [5.1.6](basic-materialized-views.md)
  - of an attribute dimension level [25.4](analytic-view-attribute-dimensions.md)

------------------------------------------------------------------------

## L

- LAG/LEAD functions [19.2.4](sql-analysis-reporting-data-warehouses.md)
- LAST_VALUE function [19.2.5.1](sql-analysis-reporting-data-warehouses.md)
- level relationships [3.2.6.1](data-warehouse-physical-design.md)
  - purpose [3.2.6.1.2](data-warehouse-physical-design.md)
- levels [3.2.6](data-warehouse-physical-design.md), [3.2.6.1.1](data-warehouse-physical-design.md)
  - order of members in [25.3](analytic-view-attribute-dimensions.md)
  - types in an attribute dimension [25.1](analytic-view-attribute-dimensions.md)
- levels in a dimension
  - skipping [10.2](dimensions.md)
- limiting rows returned [19.9](sql-analysis-reporting-data-warehouses.md)
- linear regression functions [19.3.6](sql-analysis-reporting-data-warehouses.md)
- LISTAGG function [19.3.2](sql-analysis-reporting-data-warehouses.md)
- local indexes [4.1.1.2](data-warehouse-optimizations-techniques.md), [4.1.2](data-warehouse-optimizations-techniques.md)
- logging
  - error [18.4](loading-transformation-date-warehouses.md)
- logical design [3.1](data-warehouse-physical-design.md)
- logs
  - materialized views [5.4](basic-materialized-views.md)
- lookup tables
  - See dimension tables [5.1.6](basic-materialized-views.md)

------------------------------------------------------------------------

## M

- managing
  - refresh statistics [9.2](monitoring-materialized-view-refresh.md)
- manual
  - refresh [7.1.7](refreshing-materialized-views.md)
- manual refresh
  - with DBMS_MVIEW package [7.1.7](refreshing-materialized-views.md)
- MATCH_RECOGNIZE clause [21](sql-pattern-matching-data-warehouses.md)
- materialized view logs [5.4](basic-materialized-views.md)
- materialized view refresh
  - online table redefinition [7.1.14](refreshing-materialized-views.md)
- materialized views
  - aggregates [5.2.1](basic-materialized-views.md)
  - altering [6.6](advanced-materialized-views.md)
  - analytic processing [6.2](advanced-materialized-views.md)
  - based on hybrid partitioned tables [5.3.2](basic-materialized-views.md)
  - build methods [5.3.5](basic-materialized-views.md)
  - checking status [7.1.17](refreshing-materialized-views.md)
  - containing only joins [5.2.2](basic-materialized-views.md)
  - creating [5.3](basic-materialized-views.md)
  - cubes [6.2.2](advanced-materialized-views.md)
  - data segment compression [5.3.4](basic-materialized-views.md)
  - delta joins [12.1.3.1.3](advanced-query-rewrite-materialized-views.md)
  - dropping [5.7](basic-materialized-views.md), [5.9](basic-materialized-views.md)
  - invalidating [6.5](advanced-materialized-views.md)
  - logs [16.2.3](extraction-data-warehouses.md)
  - multiple [12.2.8](advanced-query-rewrite-materialized-views.md)
  - naming [5.3.3](basic-materialized-views.md)
  - nested [5.2.3](basic-materialized-views.md)
  - ON STATEMENT refresh [7.1.6](refreshing-materialized-views.md)
  - partition change tracking (PCT) [6.1.1](advanced-materialized-views.md)
  - partitioned tables [7.3](refreshing-materialized-views.md)
  - partitioning [6.1](advanced-materialized-views.md)
  - prebuilt [5.3](basic-materialized-views.md)
  - query rewrite
    - hints [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
    - matching join graphs [5.3.7](basic-materialized-views.md)
    - parameters [11.2.2](basic-query-rewrite-materialized-views.md)
    - privileges [11.2.5](basic-query-rewrite-materialized-views.md)
  - real-time materialized views [6.7.1](advanced-materialized-views.md)
  - refresh dependent [7.1.10](refreshing-materialized-views.md)
  - refreshing [5.3.8.2](basic-materialized-views.md), [7.1](refreshing-materialized-views.md)
  - refreshing all [7.1.9](refreshing-materialized-views.md)
  - registration [5.7](basic-materialized-views.md)
  - restrictions [5.3.7.1](basic-materialized-views.md)
  - rewrites
    - enabling [11.2.1](basic-query-rewrite-materialized-views.md)
  - schema design [5.1.7](basic-materialized-views.md)
  - schema design guidelines [5.1.7](basic-materialized-views.md)
  - security [6.4](advanced-materialized-views.md)
  - set operators [6.2.5](advanced-materialized-views.md)
  - storage characteristics [5.3.4](basic-materialized-views.md)
  - types of [5.2](basic-materialized-views.md)
  - uses for [5.1](basic-materialized-views.md)
  - with VPD [6.4.1](advanced-materialized-views.md)
- materialized viewsCOUNT(DISTINCT) [5.6](basic-materialized-views.md)
- measures [5.1.6](basic-materialized-views.md)
  - analytic view [26.2](analytic-view-objects.md)
  - base [26.3](analytic-view-objects.md)
  - calculated [26.4](analytic-view-objects.md)
- MERGE PARTITION operation [4.4.1](data-warehouse-optimizations-techniques.md)
- MERGE statement [7.6.1](refreshing-materialized-views.md)
- MODEL clause [22.1](sql-modeling-data-warehouses.md)
  - cell referencing [22.2.4](sql-modeling-data-warehouses.md)
  - data flow [22.1.1](sql-modeling-data-warehouses.md)
  - keywords [22.2.3](sql-modeling-data-warehouses.md)
  - parallel execution [22.4.1](sql-modeling-data-warehouses.md)
  - rules [22.2.5](sql-modeling-data-warehouses.md)
- modeling
  - logical design [2](data-warehouse-logical-design.md)
  - physical design [2](data-warehouse-logical-design.md)
- modifying
  - zone maps [14.2.3](using-zone-maps.md)
- monitoring
  - ETL jobs [18.1.3](loading-transformation-date-warehouses.md)
  - refresh [7.1.16](refreshing-materialized-views.md)
- mortgage calculation [22.5.6](sql-modeling-data-warehouses.md)
- MOVE PARTITION operation [4.4.1](data-warehouse-optimizations-techniques.md)
- multiple hierarchies [10.2.2](dimensions.md)
- multiple materialized views [12.2.8](advanced-query-rewrite-materialized-views.md)
- MV_CAPABILITIES_TABLE table [5.10.1.2](basic-materialized-views.md)

------------------------------------------------------------------------

## N

- nested materialized views [5.2.3](basic-materialized-views.md)
  - refreshing [7.2.3](refreshing-materialized-views.md)
  - restrictions [5.2.3.4](basic-materialized-views.md)
- net present value
  - calculating [22.5.3](sql-modeling-data-warehouses.md)
- nonvolatile data [1.1](introduction-data-warehouse-concepts.md)
- NOREWRITE hint [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
- NTH_VALUE function [19.2.5.2](sql-analysis-reporting-data-warehouses.md)
- nulls
  - indexes and [4.1.1.1](data-warehouse-optimizations-techniques.md)

------------------------------------------------------------------------

## O

- OFFSET
  - row_limiting_clause [19.9](sql-analysis-reporting-data-warehouses.md)
- ON COMMIT clause [5.3.8.1](basic-materialized-views.md)
- ON DEMAND clause [5.3.8.1](basic-materialized-views.md)
- online redefinition
  - materialized views [7.1.14](refreshing-materialized-views.md)
- ON STATEMENT clause [5.3.8.1](basic-materialized-views.md)
- optimizations
  - query rewrite
    - enabling [11.2.1](basic-query-rewrite-materialized-views.md)
    - hints [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
    - matching join graphs [5.3.7](basic-materialized-views.md)
  - query rewrites
    - privileges [11.2.5](basic-query-rewrite-materialized-views.md)
- optimizer
  - with rewrite [11.1.1](basic-query-rewrite-materialized-views.md)
- ORDER BY clause [5.3.9](basic-materialized-views.md)
  - in an attribute dimension level [25.3](analytic-view-attribute-dimensions.md)
- outer joins
  - with query rewrite [12.9.3](advanced-query-rewrite-materialized-views.md)
- out-of-place refresh [7.1.4](refreshing-materialized-views.md)

------------------------------------------------------------------------

## P

- packages
  - DBMS_ADVISOR [5.1.4](basic-materialized-views.md)
  - DBMS_DIMENSION [10.3.2](dimensions.md)
  - DBMS_ERROR [18.4.2.3](loading-transformation-date-warehouses.md)
  - DBMS_ERRORLOG [18.4.2.3](loading-transformation-date-warehouses.md), [18.5.3](loading-transformation-date-warehouses.md)
  - DBMS_MVIEW [5.10.1.1](basic-materialized-views.md), [7.1](refreshing-materialized-views.md)
  - DBMS_SYNC_REFRESH [8](synchronous-refresh.md)
- parallel DML
  - bitmap indexes [4.1.2](data-warehouse-optimizations-techniques.md)
- parallel execution [4.3](data-warehouse-optimizations-techniques.md)
- parallelism [4.3](data-warehouse-optimizations-techniques.md)
- parallel query
  - bitmap indexes [4.1.2](data-warehouse-optimizations-techniques.md)
- partition change tracking (PCT) [6.1.1](advanced-materialized-views.md), [7.3.1](refreshing-materialized-views.md), [12.2.7](advanced-query-rewrite-materialized-views.md)
  - refresh [7.1.3](refreshing-materialized-views.md)
  - with Pmarkers [12.2.7.4](advanced-query-rewrite-materialized-views.md)
- partitioned outer join [19.6](sql-analysis-reporting-data-warehouses.md)
- partitioned tables
  - materialized views [7.3](refreshing-materialized-views.md)
- partitioning [16.2.3](extraction-data-warehouses.md)
  - materialized views [6.1](advanced-materialized-views.md)
  - prebuilt tables [6.1.3](advanced-materialized-views.md)
- partitions
  - bitmap indexes [4.1.1.2](data-warehouse-optimizations-techniques.md)
- pattern matching [21](sql-pattern-matching-data-warehouses.md)
  - keywords [21.2.2](sql-pattern-matching-data-warehouses.md)
- patterns
  - in SQL [21](sql-pattern-matching-data-warehouses.md)
- percentile functions
  - approximate results [19.3.4.5](sql-analysis-reporting-data-warehouses.md)
- physical design [3.1](data-warehouse-physical-design.md)
  - structures [3.2.1](data-warehouse-physical-design.md)
- pivoting [18.5.4](loading-transformation-date-warehouses.md), [19.4](sql-analysis-reporting-data-warehouses.md)
  - operations [19.4](sql-analysis-reporting-data-warehouses.md)
- plans
  - star transformations [4.5.2.2](data-warehouse-optimizations-techniques.md)
- Pmarkers
  - with PCT [12.2.7.4](advanced-query-rewrite-materialized-views.md)
- prebuilt materialized views [5.3](basic-materialized-views.md)
- pruning
  - examples [14.4.2.1](using-zone-maps.md), [14.4.2.2](using-zone-maps.md)
  - using zone maps [14.4](using-zone-maps.md)
- purging data [7.6.3](refreshing-materialized-views.md)

------------------------------------------------------------------------

## Q

- queries
  - running with approximate functions [4.6.1](data-warehouse-optimizations-techniques.md)
- QUERY_REWRITE_ENABLED initialization parameter [11.2.1](basic-query-rewrite-materialized-views.md)
- query delta joins [12.1.3.1.2](advanced-query-rewrite-materialized-views.md)
- query rewrite
  - advanced [12.4](advanced-query-rewrite-materialized-views.md)
  - checks made by [12.1.3](advanced-query-rewrite-materialized-views.md)
  - controlling [11.2.3](basic-query-rewrite-materialized-views.md)
  - correctness [11.2.4](basic-query-rewrite-materialized-views.md)
  - date folding [12.3.5](advanced-query-rewrite-materialized-views.md)
  - enabling [11.2](basic-query-rewrite-materialized-views.md), [11.2.1](basic-query-rewrite-materialized-views.md)
  - hints [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
  - matching join graphs [5.3.7](basic-materialized-views.md)
  - materialized view with approximate queries [12.6](advanced-query-rewrite-materialized-views.md)
  - methods [12.1](advanced-query-rewrite-materialized-views.md)
  - parameters [11.2.2](basic-query-rewrite-materialized-views.md)
  - privileges [11.2.5](basic-query-rewrite-materialized-views.md)
  - real-time materialized views [6.7.4](advanced-materialized-views.md), [6.7.5](advanced-materialized-views.md)
  - restrictions [5.3.7.2](basic-materialized-views.md)
  - using equivalences [12.4](advanced-query-rewrite-materialized-views.md)
  - using GROUP BY extensions [12.3.9.1](advanced-query-rewrite-materialized-views.md)
  - using nested materialized views [12.3.1](advanced-query-rewrite-materialized-views.md)
  - using PCT [12.2.7](advanced-query-rewrite-materialized-views.md)
  - VPD [6.4.1.1](advanced-materialized-views.md)
  - when it occurs [11.1.2](basic-query-rewrite-materialized-views.md)
  - with bind variables [12.3.12](advanced-query-rewrite-materialized-views.md)
  - with DBMS_MVIEW package [12.8.2](advanced-query-rewrite-materialized-views.md)
  - with expression matching [12.3.11](advanced-query-rewrite-materialized-views.md)
  - with inline views [12.3.2](advanced-query-rewrite-materialized-views.md)
  - with partially stale materialized views [12.3.11.1](advanced-query-rewrite-materialized-views.md)
  - with selfjoins [12.3.4](advanced-query-rewrite-materialized-views.md)
  - with set operator materialized views [12.3.8](advanced-query-rewrite-materialized-views.md)
  - with view constraints [12.3.6](advanced-query-rewrite-materialized-views.md)

------------------------------------------------------------------------

## R

- range-partitioned table [4.4.1](data-warehouse-optimizations-techniques.md)
- RANK function [19.2.1.1](sql-analysis-reporting-data-warehouses.md)
- ranking functions [19.2.1](sql-analysis-reporting-data-warehouses.md)
- RATIO_TO_REPORT function [19.2.3.1](sql-analysis-reporting-data-warehouses.md)
- real-time materialized views [6.7.1](advanced-materialized-views.md)
  - accessing [6.7.1.2](advanced-materialized-views.md)
  - creating [6.7.2](advanced-materialized-views.md)
  - displaying [6.7.7](advanced-materialized-views.md)
  - for direct query access [6.7.6](advanced-materialized-views.md)
  - guidelines [6.7.8](advanced-materialized-views.md)
  - query rewrite [6.7.4](advanced-materialized-views.md), [6.7.5](advanced-materialized-views.md)
  - restrictions [6.7.1.1](advanced-materialized-views.md)
- reference tables
  - See dimension tables [5.1.6](basic-materialized-views.md)
- refresh
  - monitoring [7.1.16](refreshing-materialized-views.md)
  - options [5.3.8](basic-materialized-views.md)
  - out-of-place [7.1.4](refreshing-materialized-views.md)
  - partition change tracking (PCT) [7.1.3](refreshing-materialized-views.md)
  - scheduling [7.1.18](refreshing-materialized-views.md)
  - synchronous [8](synchronous-refresh.md)
  - with UNION ALL [7.2.4](refreshing-materialized-views.md)
- refreshing
  - materialized views [7.1](refreshing-materialized-views.md)
  - materialized views based on approximate queries [7.1.13](refreshing-materialized-views.md)
  - nested materialized views [7.2.3](refreshing-materialized-views.md)
  - partitioning [7.5](refreshing-materialized-views.md)
  - zone maps [14.3.3](using-zone-maps.md)
- refresh statistics
  - about [9.1](monitoring-materialized-view-refresh.md), [9.4.1](monitoring-materialized-view-refresh.md), [9.5.1](monitoring-materialized-view-refresh.md)
  - analyzing [9.9](monitoring-materialized-view-refresh.md)
  - collecting [9.4.1](monitoring-materialized-view-refresh.md), [9.4.2](monitoring-materialized-view-refresh.md)
  - data dictionary views [9.3](monitoring-materialized-view-refresh.md)
  - managing [9.2](monitoring-materialized-view-refresh.md)
  - modifying collection level [9.4.3](monitoring-materialized-view-refresh.md)
  - modifying retention period [9.5.3](monitoring-materialized-view-refresh.md)
  - purging [9.7](monitoring-materialized-view-refresh.md)
  - retaining [9.5.1](monitoring-materialized-view-refresh.md)
  - retention period [9.5.2](monitoring-materialized-view-refresh.md)
  - setting defaults [9.4.2](monitoring-materialized-view-refresh.md), [9.5.2](monitoring-materialized-view-refresh.md)
  - SQL statements [9.8.4](monitoring-materialized-view-refresh.md)
  - understanding [9.9](monitoring-materialized-view-refresh.md)
  - viewing basic [9.8.1](monitoring-materialized-view-refresh.md)
  - viewing change data [9.8.3](monitoring-materialized-view-refresh.md)
  - viewing detailed [9.8.2](monitoring-materialized-view-refresh.md)
  - viewing settings [9.6](monitoring-materialized-view-refresh.md)
- REGR_INTERCEPT function [19.3.6.3](sql-analysis-reporting-data-warehouses.md)
- REGR_R2 function [19.3.6.4](sql-analysis-reporting-data-warehouses.md)
- REGR_SLOPE function [19.3.6.3](sql-analysis-reporting-data-warehouses.md)
- RELY constraints [4.2.2.3](data-warehouse-optimizations-techniques.md)
- reporting functions [19.2.3](sql-analysis-reporting-data-warehouses.md)
- restrictions
  - fast refresh [5.3.8.4](basic-materialized-views.md)
  - nested materialized views [5.2.3.4](basic-materialized-views.md)
  - query rewrite [5.3.7.2](basic-materialized-views.md)
- result set [4.5.2](data-warehouse-optimizations-techniques.md)
- REWRITE_OR_ERROR hint [12.9.10.2](advanced-query-rewrite-materialized-views.md)
- REWRITE hint [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
- rewrites
  - hints [12.9.10.1](advanced-query-rewrite-materialized-views.md)
  - parameters [11.2.2](basic-query-rewrite-materialized-views.md)
  - privileges [11.2.5](basic-query-rewrite-materialized-views.md)
  - query optimizations
    - hints [11.2.1](basic-query-rewrite-materialized-views.md), [12.9.10.1](advanced-query-rewrite-materialized-views.md)
    - matching join graphs [5.3.7](basic-materialized-views.md)
- rolling up hierarchies [10.1](dimensions.md)
- ROLLUP [20.2](sql-aggregation-data-warehouses.md)
  - concatenated [20.10.1](sql-aggregation-data-warehouses.md)
  - partial [20.2.3](sql-aggregation-data-warehouses.md)
  - when to use [20.2.1](sql-aggregation-data-warehouses.md)
- root level [3.2.6.1.1](data-warehouse-physical-design.md)
- row_limiting_clause clause [19.9](sql-analysis-reporting-data-warehouses.md)
- ROW_NUMBER function [19.2.1.7](sql-analysis-reporting-data-warehouses.md)
- rules
  - in MODEL clause [22.2.5](sql-modeling-data-warehouses.md)
  - in SQL modeling [22.2.5](sql-modeling-data-warehouses.md)
  - order of evaluation [22.2.6](sql-modeling-data-warehouses.md)

------------------------------------------------------------------------

## S

- schemas
  - 3NF [2.3](data-warehouse-logical-design.md)
  - design guidelines for materialized views [5.1.7](basic-materialized-views.md)
  - snowflake [2.2.1](data-warehouse-logical-design.md)
  - star [2.2.1](data-warehouse-logical-design.md)
- set operators
  - materialized views [6.2.5](advanced-materialized-views.md)
- simultaneous equations [22.5.4](sql-modeling-data-warehouses.md)
- skipping levels in a dimension [10.2](dimensions.md)
- SKIP WHEN NULL clause [10.2](dimensions.md)
- snowflake schemas [2.4.3](data-warehouse-logical-design.md)
  - complex queries [2.4.3](data-warehouse-logical-design.md)
- source systems [16.1](extraction-data-warehouses.md)
- sparse data
  - data densification [19.6.2](sql-analysis-reporting-data-warehouses.md)
- SPLIT PARTITION operation [4.4.1](data-warehouse-optimizations-techniques.md)
- SQL modeling [22.1](sql-modeling-data-warehouses.md)
  - cell referencing [22.2.4](sql-modeling-data-warehouses.md)
  - keywords [22.2.3](sql-modeling-data-warehouses.md)
  - order of evaluation [22.2.6](sql-modeling-data-warehouses.md)
  - performance [22.4](sql-modeling-data-warehouses.md)
  - rules [22.2.5](sql-modeling-data-warehouses.md)
  - rules and restrictions [22.3.7](sql-modeling-data-warehouses.md)
- staging
  - areas [1.4.2](introduction-data-warehouse-concepts.md)
  - databases [5.1](basic-materialized-views.md)
  - files [5.1](basic-materialized-views.md)
- star queries
  - star transformation [4.5.2](data-warehouse-optimizations-techniques.md)
- star schemas
  - dimensional model [2.4.1](data-warehouse-logical-design.md)
- star transformations [4.5.2](data-warehouse-optimizations-techniques.md)
  - restrictions [4.5.2.6](data-warehouse-optimizations-techniques.md)
- statistics [12.9.9](advanced-query-rewrite-materialized-views.md)
- storage
  - optimizing [4.4](data-warehouse-optimizations-techniques.md)
- summary management
  - components [5.1.5](basic-materialized-views.md)
- synchronous refresh [8](synchronous-refresh.md)
- sync refresh [8](synchronous-refresh.md)

------------------------------------------------------------------------

## T

- tables
  - attribute-clustered [13.1](attribute-clustering.md)
  - detail tables [5.1.6](basic-materialized-views.md)
  - dimension tables (lookup tables) [5.1.6](basic-materialized-views.md)
  - external [18.2.2](loading-transformation-date-warehouses.md)
  - fact tables [5.1.6](basic-materialized-views.md)
- tablespaces
  - transportable [16.2.2](extraction-data-warehouses.md), [17.2.3](transportation-data-warehouses.md), [17.2.3.2](transportation-data-warehouses.md)
- text match [12.2.1](advanced-query-rewrite-materialized-views.md)
  - with query rewrite [12.9.4](advanced-query-rewrite-materialized-views.md)
- Third Normal Form [2.3](data-warehouse-logical-design.md)
- time series calculations [19.7](sql-analysis-reporting-data-warehouses.md)
- timestamps [16.2.3](extraction-data-warehouses.md)
- Top-N queries [19.9](sql-analysis-reporting-data-warehouses.md)
- transformations [18.1](loading-transformation-date-warehouses.md)
  - scenarios [18.5](loading-transformation-date-warehouses.md)
  - SQL\*Loader [18.2.1](loading-transformation-date-warehouses.md)
  - SQL and PL/SQL [18.3.1](loading-transformation-date-warehouses.md)
- transportable tablespaces [16.2.2](extraction-data-warehouses.md), [17.2.3](transportation-data-warehouses.md), [17.2.3.2](transportation-data-warehouses.md)
- transportation
  - definition [17.1](transportation-data-warehouses.md)
  - distributed operations [17.2.2](transportation-data-warehouses.md)
  - flat files [17.2.1](transportation-data-warehouses.md)
- triggers [16.2.3](extraction-data-warehouses.md)
- types
  - attribute clustering [13.1.2](attribute-clustering.md)
  - zone maps [14.1.3](using-zone-maps.md)

------------------------------------------------------------------------

## U

- ultralarge files [3.2.1.1](data-warehouse-physical-design.md)
- unique
  - constraints [4.2.2.1](data-warehouse-optimizations-techniques.md)
  - identifier [2.2](data-warehouse-logical-design.md), [3.2](data-warehouse-physical-design.md)
- update frequencies [5.1.9](basic-materialized-views.md)
- UPDATE statement [22.2.8](sql-modeling-data-warehouses.md)
- update windows [5.1.9](basic-materialized-views.md)
- UPSERT ALL statement [22.2.8](sql-modeling-data-warehouses.md)
- UPSERT statement [22.2.8](sql-modeling-data-warehouses.md)

------------------------------------------------------------------------

## V

- validating dimensions [10.5](dimensions.md)
- validating hierarchy data [24.5](overview-analytic-views.md)
- VECTOR GROUP BY
  - aggregation [20.8.6](sql-aggregation-data-warehouses.md)
- VECTOR GROUP BY aggregation
  - optimizing star queries [4.5.4](data-warehouse-optimizations-techniques.md)
- view constraints [4.2.2.7](data-warehouse-optimizations-techniques.md), [12.3.6](advanced-query-rewrite-materialized-views.md)
- VPD
  - and materialized views [6.4.1](advanced-materialized-views.md)
  - restrictions with materialized views [6.4.1.2](advanced-materialized-views.md)

------------------------------------------------------------------------

## W

- WIDTH_BUCKET function [19.8.1](sql-analysis-reporting-data-warehouses.md), [19.8.1.1](sql-analysis-reporting-data-warehouses.md)
- window functions [22.3.5](sql-modeling-data-warehouses.md)
- windowing functions [19.2.2](sql-analysis-reporting-data-warehouses.md)

------------------------------------------------------------------------

## Z

- zone maps [14.1](using-zone-maps.md)
  - about [14.1](using-zone-maps.md)
  - about refreshing [14.3.2](using-zone-maps.md)
  - about staleness [14.3.1](using-zone-maps.md)
  - automatic refresh [14.1.6.2](using-zone-maps.md)
  - benefits [14.1.4](using-zone-maps.md)
  - compiling [14.2.5](using-zone-maps.md)
  - creating [14.2.2.2](using-zone-maps.md)
    - with attribute clustering [14.2.2.1](using-zone-maps.md)
  - data dictionary views [14.5](using-zone-maps.md)
  - dropping [14.2.4](using-zone-maps.md)
  - maintaining [14.2.7](using-zone-maps.md)
  - maintenance [14.1.6.1](using-zone-maps.md)
  - modifying [14.2.3](using-zone-maps.md)
  - privileges [14.2.1](using-zone-maps.md)
  - pruning [14.4](using-zone-maps.md)
  - refreshing [14.3.3](using-zone-maps.md)
  - types [14.1.3](using-zone-maps.md)
  - usage for SQL statements [14.2.6.2](using-zone-maps.md)
  - usage for SQL workloads [14.2.6.1](using-zone-maps.md)
  - usage scenarios [14.1.5](using-zone-maps.md)
  - with attribute clustering [14.1.2](using-zone-maps.md)
