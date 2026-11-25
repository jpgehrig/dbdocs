A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  V  W  

------------------------------------------------------------------------

## A

- Active Data Guard
  - about [13.1](deploying-im-column-store-with-adg.md)
  - configuring IM column store [13.2](deploying-im-column-store-with-adg.md)
  - how IM column store works [13.1.2](deploying-im-column-store-with-adg.md)
  - purpose [13.1.1](deploying-im-column-store-with-adg.md), [13.1.1.1](deploying-im-column-store-with-adg.md)
- Active Session History (ASH) [1.6.2](intro-to-in-memory-column-store.md)
- advisors
  - In-Memory Advisor [1.6.2](intro-to-in-memory-column-store.md)
  - Oracle Compression Advisor [1.6.4](intro-to-in-memory-column-store.md), [3.2](enabling-the-im-column-store.md)
- ALL_HEAT_MAP_SEGMENT view [6.1.3.1](configuring-memory-management.md)
- ALL_JSON_COLUMNS view [7.1.2.1](optimizing-in-memory-expressions.md)
- ALTER MATERIALIZED VIEW statement [4.1.3.1.3](populating-objects-in-memory.md), [4.5](populating-objects-in-memory.md)
- ALTER TABLESPACE statement [4.1.3.1.4](populating-objects-in-memory.md)
- ALTER TABLE statement [2.2.1.1](in-memory-column-store-architecture.md), [4.1.3.1.1](populating-objects-in-memory.md), [4.1.3.1.2](populating-objects-in-memory.md), [4.1.3.3](populating-objects-in-memory.md), [4.2.2](populating-objects-in-memory.md)
- analytic indexes [1.3.3](intro-to-in-memory-column-store.md)
- analytic queries [1.1](intro-to-in-memory-column-store.md), [1.3](intro-to-in-memory-column-store.md), [1.3.2](intro-to-in-memory-column-store.md), [1.3.2.1](intro-to-in-memory-column-store.md), [1.3.3](intro-to-in-memory-column-store.md)
- Auto DOP [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
- Automatic Data Optimization (ADO) [6.2.1](configuring-memory-management.md)
  - Automatic In-Memory [6](configuring-memory-management.md)
  - enabling [6.1](configuring-memory-management.md)
  - Heat Map [6.1.3.1](configuring-memory-management.md)
  - how policies work [6.1.3.2](configuring-memory-management.md)
  - In-Memory Column Store [6.1.5](configuring-memory-management.md)
  - policies [6.1.1](configuring-memory-management.md)
  - purpose [6.1.2](configuring-memory-management.md)
  - user interface [6.1.4](configuring-memory-management.md)
- Automatic In-Memory
  - , setting the time interval [6.2.5](configuring-memory-management.md)
  - configuring [6](configuring-memory-management.md), [6.2](configuring-memory-management.md)
  - controlling [6.2.4](configuring-memory-management.md)
  - how it works [6.2.2](configuring-memory-management.md)
  - purpose [6.2.1](configuring-memory-management.md)

------------------------------------------------------------------------

## B

- Bloom filters [1.3.2.2](intro-to-in-memory-column-store.md), [8.1](optimizing-queries-with-join-groups.md), [9.1.2](optimizing-in-memory-aggregation.md), [9.1.3.1](optimizing-in-memory-aggregation.md)

------------------------------------------------------------------------

## C

- columnar data pool [2.1.1.2](in-memory-column-store-architecture.md)
- columnar format [2](in-memory-column-store-architecture.md), [2.1](in-memory-column-store-architecture.md), [2.2.1](in-memory-column-store-architecture.md)
  - benefits [1.3.2.1](intro-to-in-memory-column-store.md)
  - single-format approach [1.2](intro-to-in-memory-column-store.md)
- Column Compression Units (CUs)
  - FastStart area [11.1.2.1](managing-im-faststart-for-im-column-store.md)
  - local dictionary [2.2.1.2](in-memory-column-store-architecture.md)
  - row modifications [10.2.1](repopulation-and-dml.md)
- common dictionaries [8.4.1](optimizing-queries-with-join-groups.md), [8.5](optimizing-queries-with-join-groups.md)
- COMPATIBLE initialization parameter [3.3](enabling-the-im-column-store.md), [4.3.1](populating-objects-in-memory.md), [4.3.2](populating-objects-in-memory.md), [6.1.4](configuring-memory-management.md)
- compression [3.2](enabling-the-im-column-store.md)
  - effect on repopulation [10.3.2](repopulation-and-dml.md)
  - Hybrid Columnar Compression [2.2.1.1.2](in-memory-column-store-architecture.md)
  - In-Memory Column Store [2.2.1.1.2](in-memory-column-store-architecture.md)
  - methods [4.1.3.3](populating-objects-in-memory.md)
- conventional DML [10.2.1](repopulation-and-dml.md)
- CPU_COUNT initialization parameter [4.1.2.2](populating-objects-in-memory.md)
- CPU architecture [10.5](repopulation-and-dml.md)
  - SIMD vector processing [1.3.2.1](intro-to-in-memory-column-store.md), [9.1.2](optimizing-in-memory-aggregation.md)
- CREATE MATERIALIZED VIEW statement [4.1.3.1.3](populating-objects-in-memory.md), [4.5](populating-objects-in-memory.md)
- CREATE TABLE AS SELECT statement [10.2.2](repopulation-and-dml.md)
- CREATE TABLESPACE statement [4.1.3.1.4](populating-objects-in-memory.md)
- CREATE TABLE statement [4.1.3.1.1](populating-objects-in-memory.md), [4.1.3.1.2](populating-objects-in-memory.md), [4.1.3.3](populating-objects-in-memory.md)
- CUs
  - See: Column Compression Units (CUs)

------------------------------------------------------------------------

## D

- database buffer cache [2.1.2](in-memory-column-store-architecture.md)
- Database In-Memory [1.3](intro-to-in-memory-column-store.md)
  - about [1.3.1](intro-to-in-memory-column-store.md)
  - introduction [1](intro-to-in-memory-column-store.md)
  - principal tasks [1.5](intro-to-in-memory-column-store.md)
  - tools for [1.6](intro-to-in-memory-column-store.md)
- database instances
  - multiple IM column stores [12.1.1](deploying-in-memory-in-oracle-rac.md)
- Database Resource Manager [2.4.3.1](in-memory-column-store-architecture.md), [2.4.3.2.1](in-memory-column-store-architecture.md)
- data flow operator (DFO) [9.1.3](optimizing-in-memory-aggregation.md)
- data loading, into IM column store [10.2](repopulation-and-dml.md)
- DBA_EXPRESSION_STATISTICS view [15](views-related-to-im-column-store.md)
- DBA_FEATURE_USAGE_STATISTICS view [15](views-related-to-im-column-store.md)
- DBA_HEAT_MAP_SEGMENT view [6.1.1](configuring-memory-management.md), [15](views-related-to-im-column-store.md)
- DBA_ILMDATAMOVEMENTPOLICIES view [15](views-related-to-im-column-store.md)
- DBA_IM_EXPRESSIONS view [7.1](optimizing-in-memory-expressions.md), [15](views-related-to-im-column-store.md)
- DBA_INMEMORY_AIMTASKDETAILS [15](views-related-to-im-column-store.md)
- DBA_INMEMORY_AIMTASKDETAILS view [6.2.3](configuring-memory-management.md)
- DBA_INMEMORY_AIMTASKS [15](views-related-to-im-column-store.md)
- DBA_INMEMORY_AIMTASKS view [6.2.3](configuring-memory-management.md)
- DBA_JOINGROUPS view [15](views-related-to-im-column-store.md)
- DBA_TABLES view [4.1.3.1](populating-objects-in-memory.md), [12.1.2.1](deploying-in-memory-in-oracle-rac.md), [15](views-related-to-im-column-store.md)
- DBMS_COMPRESSION PL/SQL package [3.2](enabling-the-im-column-store.md), [4.1.3.4](populating-objects-in-memory.md)
- DBMS_HEATMAP PL/SQL package [6.1.4](configuring-memory-management.md)
- DBMS_ILM_ADMIN PL/SQL package [6.1.4](configuring-memory-management.md)
- DBMS_ILM PL/SQL package [6.1.4](configuring-memory-management.md), [6.1.5](configuring-memory-management.md)
- DBMS_INMEMORY_ADMIN package [7.1](optimizing-in-memory-expressions.md), [7.1.2.2](optimizing-in-memory-expressions.md), [7.1.3.2](optimizing-in-memory-expressions.md), [7.1.4](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md), [7.4](optimizing-in-memory-expressions.md), [11.1.2](managing-im-faststart-for-im-column-store.md), [11.4](managing-im-faststart-for-im-column-store.md)
  - AIM_GET_PARAMETER procedure [6.2.5](configuring-memory-management.md)
  - AIM_SET_PARAMETER procedure [6.2.3](configuring-memory-management.md), [6.2.5](configuring-memory-management.md)
  - FASTSTART_DISABLE procedure [11.5](managing-im-faststart-for-im-column-store.md)
  - POPULATE_WAIT function [5.1](populating-the-imcs-manually.md), [5.1.3](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
- DBMS_INMEMORY package [7.1](optimizing-in-memory-expressions.md), [7.1.3.2](optimizing-in-memory-expressions.md), [7.4](optimizing-in-memory-expressions.md)
  - POPULATE procedure [5.1](populating-the-imcs-manually.md), [5.1.2](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
  - REPOPULATE procedure [5.1](populating-the-imcs-manually.md), [5.1.4](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md), [10.3](repopulation-and-dml.md), [10.4](repopulation-and-dml.md)
- DBMS_SQLTUNE PL/SQL package [8.7](optimizing-queries-with-join-groups.md)
- dense keys [9.1.3.2](optimizing-in-memory-aggregation.md)
  - dense grouping keys [9.1.3](optimizing-in-memory-aggregation.md), [9.1.3.2](optimizing-in-memory-aggregation.md)
  - dense join keys [9.1.3.2](optimizing-in-memory-aggregation.md)
- dictionaries
  - common [8.4.1](optimizing-queries-with-join-groups.md)
  - local [2.2.1.2.2](in-memory-column-store-architecture.md)
- direct path loads
  - into IM column store [10.2.2](repopulation-and-dml.md)
- DISTRIBUTE clause of CREATE TABLE [12.1.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.3](deploying-in-memory-in-oracle-rac.md)
- DISTRIBUTE FOR SERVICE subclause of CREATE TABLE [12.2.2](deploying-in-memory-in-oracle-rac.md), [13.2](deploying-im-column-store-with-adg.md)
- DML
  - conventional [10.2.1](repopulation-and-dml.md)
  - direct path loads [10.2.2](repopulation-and-dml.md)
  - double buffering [10.2.1.2](repopulation-and-dml.md)
  - staleness threshold [10.2.1.1](repopulation-and-dml.md)
- double buffering [10.2.1.2](repopulation-and-dml.md), [10.3.2](repopulation-and-dml.md)
- DUPLICATE clause of CREATE TABLE [12.1.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.4](deploying-in-memory-in-oracle-rac.md), [12.2.3](deploying-in-memory-in-oracle-rac.md)
- duplication, Oracle RAC [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)

------------------------------------------------------------------------

## E

- Enterprise Manager Cloud Control (Cloud Control) [1.6.3](intro-to-in-memory-column-store.md)
- Exadata Smart Flash Cache [2.5.3](in-memory-column-store-architecture.md)
- Exadata Smart Scan [2.5](in-memory-column-store-architecture.md)
- execution plans
  - In-Memory Dynamic Scans [2.4.3.3](in-memory-column-store-architecture.md)
- expressions, In-Memory [2.2.3](in-memory-column-store-architecture.md), [7](optimizing-in-memory-expressions.md), [7.1.3.1](optimizing-in-memory-expressions.md)
- Expression Statistics Store (ESS) [2.2](in-memory-column-store-architecture.md), [2.3](in-memory-column-store-architecture.md), [7.1.2.3](optimizing-in-memory-expressions.md)
- external tables
  - INMEMORY subclause [4.1.3.1.2](populating-objects-in-memory.md)
  - populating [4.2.3.3](populating-objects-in-memory.md), [5.3.4](populating-the-imcs-manually.md)

------------------------------------------------------------------------

## F

- FASTSTART_DISABLE procedure [11.5](managing-im-faststart-for-im-column-store.md)
- FASTSTART_ENABLE procedure [11.1.2](managing-im-faststart-for-im-column-store.md), [11.2](managing-im-faststart-for-im-column-store.md)
- FASTSTART_MIGRATE_STORAGE procedure [11.4](managing-im-faststart-for-im-column-store.md)
- FastStart area [11.1.2.1](managing-im-faststart-for-im-column-store.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)
  - disabling [11.5](managing-im-faststart-for-im-column-store.md)
  - migrating [11.4](managing-im-faststart-for-im-column-store.md)
- FOR SERVICE subclause of CREATE TABLE [12.2.4](deploying-in-memory-in-oracle-rac.md)
- FULL hint [5.1.1](populating-the-imcs-manually.md)

------------------------------------------------------------------------

## G

- granules [2.2.1.1.3](in-memory-column-store-architecture.md)

------------------------------------------------------------------------

## H

- HEAT_MAP initialization parameter [6.1.4](configuring-memory-management.md)
- Heat Map [6](configuring-memory-management.md), [6.1.2](configuring-memory-management.md), [6.1.3.1](configuring-memory-management.md)
- High Availability [1.3.5](intro-to-in-memory-column-store.md)
  - benefits of the DUPLICATE ALL clause [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md)
  - benefits of the NO DUPLICATE clause [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
  - IM column store [1.3.1.3](intro-to-in-memory-column-store.md), [IV](high-availability-and-the-im-column-store.md)
- hints
  - VECTOR_TRANSFORM_DIMS [9.1.4](optimizing-in-memory-aggregation.md)
  - VECTOR_TRANSFORM_FACT [9.1.4](optimizing-in-memory-aggregation.md)
- Hybrid Columnar Compression [2.2.1.1.2](in-memory-column-store-architecture.md)

------------------------------------------------------------------------

## I

- ILM clause of ALTER TABLE [6.1.5](configuring-memory-management.md)
- IMCO
  - See: In-Memory Coordinator Process (IMCO)
- IM column store
  - See: In-Memory Column Store In-Memory Column Store
- IMCU
  - See: In-Memory Compression Units (IMCUs)
- IM dynamic scans [2.4.3](in-memory-column-store-architecture.md)
  - See also: In-Memory Dynamic Scans
- IME_CAPTURE_EXPRESSIONS procedure [7.1.2.4](optimizing-in-memory-expressions.md), [7.1.3.2](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md)
- IME_CLOSE_CAPTURE_WINDOW procedure [7.1.3.2](optimizing-in-memory-expressions.md)
- IME_DROP_ALL_EXPRESSIONS procedure [7.1.2.2](optimizing-in-memory-expressions.md), [7.1.3.2](optimizing-in-memory-expressions.md), [7.4](optimizing-in-memory-expressions.md)
- IME_DROP_EXPRESSIONS procedure [7.1.2.2](optimizing-in-memory-expressions.md), [7.1.3.2](optimizing-in-memory-expressions.md), [7.4](optimizing-in-memory-expressions.md)
- IME_GET_CAPTURE_STATE procedure [7.1.3.2](optimizing-in-memory-expressions.md)
- IME_OPEN_CAPTURE_WINDOW procedure [7.1.3.2](optimizing-in-memory-expressions.md)
- IME_POPULATE_EXPRESSIONS procedure [7.1.3.2](optimizing-in-memory-expressions.md)
- IMEUs
  - See: In-Memory Expression Units (IMEUs)
- IM expressions [7.1](optimizing-in-memory-expressions.md), [7.1.2](optimizing-in-memory-expressions.md)
  - administering [7.1.3.2](optimizing-in-memory-expressions.md)
  - basic tasks [7.1.4](optimizing-in-memory-expressions.md)
  - benefits [7.1.1](optimizing-in-memory-expressions.md)
  - capturing [7.1.2.2](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md)
  - configuring [7.2](optimizing-in-memory-expressions.md)
  - dropping [7.4](optimizing-in-memory-expressions.md)
  - Expression Statistics Store (ESS) [2.3](in-memory-column-store-architecture.md), [7.1.2.3](optimizing-in-memory-expressions.md)
  - JSON columns [7.1.3.1](optimizing-in-memory-expressions.md)
  - JSON optimizations [7.1.2.1](optimizing-in-memory-expressions.md)
  - materialized views [7.1.1](optimizing-in-memory-expressions.md)
  - modes of operation [7.1.3.1](optimizing-in-memory-expressions.md)
  - overview [2.2.3](in-memory-column-store-architecture.md), [7](optimizing-in-memory-expressions.md)
  - populating [7.1.2.4](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md)
  - storage in IMEUs [7.1.2.5](optimizing-in-memory-expressions.md)
  - user interfaces [7.1.3](optimizing-in-memory-expressions.md)
  - virtual columns [7.1.2.1](optimizing-in-memory-expressions.md)
- IM FastStart
  - See: In-Memory FastStart
- IM storage indexes [2.2.1.3](in-memory-column-store-architecture.md)
- indexes, analytic [1.3.3](intro-to-in-memory-column-store.md)
- INMEMORY_AUTOMATIC_LEVEL initialization parameter [6.2.3](configuring-memory-management.md), [6.2.4](configuring-memory-management.md)
- INMEMORY_CLAUSE_DEFAULT initialization parameter [14](init-parameters-for-im-column-store.md)
- INMEMORY_EXPRESSIONS_USAGE initialization parameter [7.1.2.1](optimizing-in-memory-expressions.md), [7.1.2.4](optimizing-in-memory-expressions.md), [7.1.3.1](optimizing-in-memory-expressions.md), [7.1.4](optimizing-in-memory-expressions.md), [7.2](optimizing-in-memory-expressions.md), [14](init-parameters-for-im-column-store.md)
- INMEMORY_FORCE initialization parameter [14](init-parameters-for-im-column-store.md)
- INMEMORY_MAX_POPULATE_SERVERS initialization parameter [4.1.2.2](populating-objects-in-memory.md), [10.3.1](repopulation-and-dml.md), [10.4](repopulation-and-dml.md), [14](init-parameters-for-im-column-store.md)
- INMEMORY_OPTIMIZED_ARITHMETIC initialization parameter [9.2.2](optimizing-in-memory-aggregation.md), [14](init-parameters-for-im-column-store.md)
- INMEMORY_QUERY initialization parameter [14](init-parameters-for-im-column-store.md)
- INMEMORY_SIZE initialization parameter [1.3.6](intro-to-in-memory-column-store.md), [2.1.1.1](in-memory-column-store-architecture.md), [3.1](enabling-the-im-column-store.md), [3.3](enabling-the-im-column-store.md), [3.4](enabling-the-im-column-store.md), [3.5](enabling-the-im-column-store.md), [6.1.4](configuring-memory-management.md), [6.1.5](configuring-memory-management.md), [7.1.3.1](optimizing-in-memory-expressions.md), [7.2](optimizing-in-memory-expressions.md), [9.1.1](optimizing-in-memory-aggregation.md), [12.2.4](deploying-in-memory-in-oracle-rac.md), [13.1.1.1](deploying-im-column-store-with-adg.md), [13.1.1.2](deploying-im-column-store-with-adg.md), [13.1.1.3](deploying-im-column-store-with-adg.md), [14](init-parameters-for-im-column-store.md)
- INMEMORY_TRICKLE_POPULATE_SERVERS_PERCENT initialization parameter [14](init-parameters-for-im-column-store.md)
- INMEMORY_TRICKLE_REPOPULATE_SERVERS_PERCENT initialization parameter [10.3.1](repopulation-and-dml.md), [10.3.2](repopulation-and-dml.md), [10.4](repopulation-and-dml.md), [10.5](repopulation-and-dml.md)
- INMEMORY_VIRTUAL_COLUMNS initialization parameter [4.3.1](populating-objects-in-memory.md), [4.3.2](populating-objects-in-memory.md), [7.1.2.4](optimizing-in-memory-expressions.md), [14](init-parameters-for-im-column-store.md)
- In-Memory Advisor [1.6.2](intro-to-in-memory-column-store.md)
- In-Memory Aggregation [1.3.1](intro-to-in-memory-column-store.md), [1.3.2.3](intro-to-in-memory-column-store.md), [9.1](optimizing-in-memory-aggregation.md), [9.1.2.2](optimizing-in-memory-aggregation.md)
  - about [9.1.1](optimizing-in-memory-aggregation.md)
  - controls [9.1.4](optimizing-in-memory-aggregation.md)
  - how it works [9.1.3](optimizing-in-memory-aggregation.md)
  - phases [9.1.3.3](optimizing-in-memory-aggregation.md)
  - purpose [9.1.2](optimizing-in-memory-aggregation.md)
  - scenario [9.1.3.4](optimizing-in-memory-aggregation.md)
  - when it occurs [9.1.3.1](optimizing-in-memory-aggregation.md)
- In-Memory Area
  - columnar data pool [2.1.1.2](in-memory-column-store-architecture.md)
  - estimating size [3.2](enabling-the-im-column-store.md)
  - metadata pool [2.1.1.2](in-memory-column-store-architecture.md)
  - setting size [3.3](enabling-the-im-column-store.md)
  - size [2.1.1.1](in-memory-column-store-architecture.md)
  - Snapshot Metadata Units (SMUs) [2.2.2.1](in-memory-column-store-architecture.md)
- INMEMORY clause of ALTER TABLE [4.2.2](populating-objects-in-memory.md), [13.1.1.1](deploying-im-column-store-with-adg.md), [13.1.1.2](deploying-im-column-store-with-adg.md), [13.1.1.3](deploying-im-column-store-with-adg.md)
- INMEMORY clause of CREATE TABLE [4.2.1](populating-objects-in-memory.md)
- INMEMORY clause of CREATE TABLESPACE [4.4](populating-objects-in-memory.md)
- In-Memory column store
  - ineligible for population [4.1.3.1](populating-objects-in-memory.md)
- In-Memory Column Store [1](intro-to-in-memory-column-store.md)
  - about [1.1](intro-to-in-memory-column-store.md)
  - Active Data Guard [13.1](deploying-im-column-store-with-adg.md), [13.1.1](deploying-im-column-store-with-adg.md), [13.1.1.1](deploying-im-column-store-with-adg.md), [13.1.1.2](deploying-im-column-store-with-adg.md), [13.1.1.3](deploying-im-column-store-with-adg.md), [13.2](deploying-im-column-store-with-adg.md)
  - advantages [1.3](intro-to-in-memory-column-store.md)
  - architecture [2.2](in-memory-column-store-architecture.md)
  - Automatic Data Optimization [6.1.5](configuring-memory-management.md)
  - benefits [1.3.6](intro-to-in-memory-column-store.md)
  - columnar format [2](in-memory-column-store-architecture.md)
  - compression [2.2.1.1.2](in-memory-column-store-architecture.md), [3.2](enabling-the-im-column-store.md), [4.1.3.3](populating-objects-in-memory.md)
  - compression units [1.3.2.1](intro-to-in-memory-column-store.md), [2.2.1](in-memory-column-store-architecture.md)
  - consistency with buffer cache [2.1.2](in-memory-column-store-architecture.md)
  - disabling [3.5](enabling-the-im-column-store.md)
  - disabling tables [4.2.2](populating-objects-in-memory.md)
  - dual memory formats [2.1](in-memory-column-store-architecture.md), [2.1.2](in-memory-column-store-architecture.md)
  - enabling existing tables [4.2.2](populating-objects-in-memory.md)
  - enabling for a database [3.3](enabling-the-im-column-store.md)
  - enabling for materialized views [4.5](populating-objects-in-memory.md)
  - enabling for tablespaces [4.4](populating-objects-in-memory.md)
  - enabling new tables [4.2.1](populating-objects-in-memory.md)
  - estimating size [3.2](enabling-the-im-column-store.md)
  - FastStart tablespace [11.1.2](managing-im-faststart-for-im-column-store.md)
  - High Availability [IV](high-availability-and-the-im-column-store.md)
  - IM expressions [2.2.3](in-memory-column-store-architecture.md), [7](optimizing-in-memory-expressions.md), [7.1](optimizing-in-memory-expressions.md), [7.1.1](optimizing-in-memory-expressions.md), [7.1.2.2](optimizing-in-memory-expressions.md), [7.1.3.1](optimizing-in-memory-expressions.md)
  - IM FastStart [11.1](managing-im-faststart-for-im-column-store.md), [11.1.1](managing-im-faststart-for-im-column-store.md), [11.2](managing-im-faststart-for-im-column-store.md), [11.3](managing-im-faststart-for-im-column-store.md), [11.4](managing-im-faststart-for-im-column-store.md), [11.5](managing-im-faststart-for-im-column-store.md)
  - IM storage indexes [2.2.1.3](in-memory-column-store-architecture.md)
  - increasing dynamically [3.4](enabling-the-im-column-store.md)
  - initialization parameters [14](init-parameters-for-im-column-store.md)
  - In-Memory Advisor [1.6.2](intro-to-in-memory-column-store.md)
  - In-Memory Area [1.3.1](intro-to-in-memory-column-store.md), [2.1.1](in-memory-column-store-architecture.md), [3.1](enabling-the-im-column-store.md), [4.3.2](populating-objects-in-memory.md)
  - join groups [8.2](optimizing-queries-with-join-groups.md)
  - JSON optimizations [7.1.2.1](optimizing-in-memory-expressions.md)
  - Oracle Data Pump [1.6.5](intro-to-in-memory-column-store.md)
  - Oracle Enterprise Manager Cloud Control [A](using-im-column-store-in-enterprise-manager.md)
  - Oracle RAC [12](deploying-in-memory-in-oracle-rac.md), [12.1](deploying-in-memory-in-oracle-rac.md), [12.1.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.3](deploying-in-memory-in-oracle-rac.md), [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
  - overview [12.1](deploying-in-memory-in-oracle-rac.md)
  - performance benefits [1.3.2](intro-to-in-memory-column-store.md)
  - population [4.1](populating-objects-in-memory.md), [4.1.1](populating-objects-in-memory.md), [4.1.2](populating-objects-in-memory.md), [4.1.2.1](populating-objects-in-memory.md), [4.1.2.2](populating-objects-in-memory.md)
  - population of data at startup [11.1.2](managing-im-faststart-for-im-column-store.md)
  - population of external tables [4.2.3.3](populating-objects-in-memory.md), [5.3.4](populating-the-imcs-manually.md)
  - prioritization of data population [4.1.3.2](populating-objects-in-memory.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)
  - prioritization of In-Memory population [4.1.2.1](populating-objects-in-memory.md)
  - priority options [4.1.3.2](populating-objects-in-memory.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)
  - repopulation [10.1](repopulation-and-dml.md), [10.2.2](repopulation-and-dml.md)
  - SIMD vector processing [2.5](in-memory-column-store-architecture.md), [9.1.2](optimizing-in-memory-aggregation.md)
  - storage units [2.2](in-memory-column-store-architecture.md)
  - trickle repopulation [10.3.1](repopulation-and-dml.md)
  - VECTOR GROUP BY [9.1.2](optimizing-in-memory-aggregation.md), [9.1.2.2](optimizing-in-memory-aggregation.md)
  - vector joins [8.1](optimizing-queries-with-join-groups.md)
  - virtual columns [4.3.1](populating-objects-in-memory.md), [7.1.2.2](optimizing-in-memory-expressions.md)
- In-Memory Compression Units (IMCUs) [1.3.2.1](intro-to-in-memory-column-store.md), [2.2.1](in-memory-column-store-architecture.md), [4.1.2.2](populating-objects-in-memory.md), [11.1.2](managing-im-faststart-for-im-column-store.md)
  - Column Compression Units (CUs) [2.2.1.2](in-memory-column-store-architecture.md)
  - common dictionaries [8.4.1](optimizing-queries-with-join-groups.md), [8.5](optimizing-queries-with-join-groups.md)
  - double buffering [10.2.1.2](repopulation-and-dml.md)
  - FastStart area [11.1.2.1](managing-im-faststart-for-im-column-store.md)
  - In-Memory Expression Units (IMEUs) [2.2.3](in-memory-column-store-architecture.md)
  - mirroring [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
  - relationship to IMEUs [7.1.2.5](optimizing-in-memory-expressions.md)
  - row subsets [2.2.1.1.3](in-memory-column-store-architecture.md)
  - schema objects and [2.2.1.1](in-memory-column-store-architecture.md)
  - Snapshot Metadata Units (SMUs) [2.2.2.1](in-memory-column-store-architecture.md)
  - transaction journals [2.2.2.2](in-memory-column-store-architecture.md)
- In-Memory Coordinator Process (IMCO) [2.4.1](in-memory-column-store-architecture.md), [6.1.3.2](configuring-memory-management.md), [7.1.2.4](optimizing-in-memory-expressions.md), [10.3.1](repopulation-and-dml.md)
- In-Memory data affinity
  - Oracle RAC [12.1.3](deploying-in-memory-in-oracle-rac.md)
- In-Memory Dynamic Scans [2.4.3](in-memory-column-store-architecture.md)
  - execution plans [2.4.3.3](in-memory-column-store-architecture.md)
  - how they work [2.4.3.2](in-memory-column-store-architecture.md)
  - lightweight threads [2.4.3.2](in-memory-column-store-architecture.md), [2.4.3.2.1](in-memory-column-store-architecture.md), [2.4.3.2.3](in-memory-column-store-architecture.md)
  - parallel queries [12.1.3.1](deploying-in-memory-in-oracle-rac.md)
  - purpose [2.4.3.1](in-memory-column-store-architecture.md)
- In-Memory Expressions
  - See: IM expressions
- In-Memory Expression Units (IMEUs) [2.2.3](in-memory-column-store-architecture.md), [7.1.2.4](optimizing-in-memory-expressions.md), [7.1.2.5](optimizing-in-memory-expressions.md)
- In-Memory FastStart [11.1](managing-im-faststart-for-im-column-store.md), [12.1](deploying-in-memory-in-oracle-rac.md)
  - See: IM FastStart

  <!-- -->

  - disabling [11.5](managing-im-faststart-for-im-column-store.md)
  - enabling [11.2](managing-im-faststart-for-im-column-store.md)
  - FastStart area [11.1.1](managing-im-faststart-for-im-column-store.md), [11.1.2](managing-im-faststart-for-im-column-store.md), [11.1.2.1](managing-im-faststart-for-im-column-store.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)
  - managing [11](managing-im-faststart-for-im-column-store.md)
  - migrating tablespace [11.4](managing-im-faststart-for-im-column-store.md)
  - Oracle RAC [12.1.4](deploying-in-memory-in-oracle-rac.md)
  - purpose [11.1.1](managing-im-faststart-for-im-column-store.md)
  - retrieving tablespace name [11.3](managing-im-faststart-for-im-column-store.md)
- In-Memory Optimized Arithmetic [9.2](optimizing-in-memory-aggregation.md)
  - about [9.2.1](optimizing-in-memory-aggregation.md)
  - enabling and disabling [9.2.2](optimizing-in-memory-aggregation.md)
  - INMEMORY_OPTIMIZED_ARITHMETIC initialization parameter [14](init-parameters-for-im-column-store.md)
  - SIMD vector processing [2.5](in-memory-column-store-architecture.md), [2.5.2](in-memory-column-store-architecture.md)
- In-Memory process architecture [2.4](in-memory-column-store-architecture.md)
  - In-Memory Coordinator Process (IMCO) [2.4.1](in-memory-column-store-architecture.md)
  - Space Management Worker Processes (Wnnn) [2.4.2](in-memory-column-store-architecture.md)
- INMEMORY subclause [4.1.3.1](populating-objects-in-memory.md)
- In-Memory virtual columns [4.3.1](populating-objects-in-memory.md), [7.1.2.2](optimizing-in-memory-expressions.md)
  - enabling [4.3.2](populating-objects-in-memory.md)

------------------------------------------------------------------------

## J

- join groups [8](optimizing-queries-with-join-groups.md)
  - benefits [8.3](optimizing-queries-with-join-groups.md)
  - common dictionaries [8.4.1](optimizing-queries-with-join-groups.md), [8.5](optimizing-queries-with-join-groups.md)
  - creating [8.6](optimizing-queries-with-join-groups.md)
  - how they work [8.4](optimizing-queries-with-join-groups.md)
  - In-Memory Column Store [8.2](optimizing-queries-with-join-groups.md)
  - monitoring [8.7](optimizing-queries-with-join-groups.md)
  - scan optimization [8.4.2](optimizing-queries-with-join-groups.md)
  - single-column [8.2](optimizing-queries-with-join-groups.md)
- joins
  - Bloom filters [1.3.2.2](intro-to-in-memory-column-store.md), [8.1](optimizing-queries-with-join-groups.md), [9.1.3.1](optimizing-in-memory-aggregation.md)
  - join groups [8.2](optimizing-queries-with-join-groups.md)
  - star queries [8.1](optimizing-queries-with-join-groups.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md)
- JSON [7.1.3.1](optimizing-in-memory-expressions.md)
  - IM expressions infrastructure [7.1.2.1](optimizing-in-memory-expressions.md)

------------------------------------------------------------------------

## K

- key vectors [9.1.3.2](optimizing-in-memory-aggregation.md)

------------------------------------------------------------------------

## L

- lightweight threads [2.4.3.2.1](in-memory-column-store-architecture.md)
- LOBs [2.5](in-memory-column-store-architecture.md), [2.5.1](in-memory-column-store-architecture.md)
- local dictionaries [2.2.1.2](in-memory-column-store-architecture.md), [2.2.1.2.2](in-memory-column-store-architecture.md)

------------------------------------------------------------------------

## M

- materialized views
  - IM expressions [7.1.1](optimizing-in-memory-expressions.md)
  - In-Memory Column Store [4.5](populating-objects-in-memory.md)
  - INMEMORY subclause [4.1.3.1.3](populating-objects-in-memory.md)
- MEMCOMPRESS clause of CREATE TABLE [4.1.3.3](populating-objects-in-memory.md), [4.3.3](populating-objects-in-memory.md)
- metadata pool [2.1.1.2](in-memory-column-store-architecture.md)
  - Snapshot Metadata Units (SMUs) [2.2.2.1](in-memory-column-store-architecture.md)

------------------------------------------------------------------------

## N

- NO DUPLICATE clause of CREATE TABLE [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
- NUMBER data type [2.5](in-memory-column-store-architecture.md), [2.5.2](in-memory-column-store-architecture.md), [9.2](optimizing-in-memory-aggregation.md), [9.2.1](optimizing-in-memory-aggregation.md), [9.2.2](optimizing-in-memory-aggregation.md), [14](init-parameters-for-im-column-store.md)

------------------------------------------------------------------------

## O

- optimizer
  - ESS statistics [7.1.2.3](optimizing-in-memory-expressions.md)
- OPTIMIZER_INMEMORY_AWARE initialization parameter [14](init-parameters-for-im-column-store.md)
- Oracle Compression Advisor [3.2](enabling-the-im-column-store.md), [4.1.3.4](populating-objects-in-memory.md)
- Oracle Database In-Memory
  - See: Database In-Memory
- Oracle Data Guard [1.3.5](intro-to-in-memory-column-store.md)
  - configure IM column store [13.2](deploying-im-column-store-with-adg.md)
- Oracle Data Pump
  - In-Memory Column Store [1.6.5](intro-to-in-memory-column-store.md)
- Oracle Engineered Systems [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md)
- Oracle Enterprise Manager Cloud Control
  - In-Memory Column Store [A](using-im-column-store-in-enterprise-manager.md)
- Oracle RAC
  - Auto DOP [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
  - deploying IM column stores [12](deploying-in-memory-in-oracle-rac.md)
  - distribution and duplication of data [12.1.2](deploying-in-memory-in-oracle-rac.md)
  - distribution by rowid [12.1.2.1.3](deploying-in-memory-in-oracle-rac.md)
  - distribution of partitions [12.1.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.1](deploying-in-memory-in-oracle-rac.md)
  - distribution of subpartitions [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md)
  - duplication [12.1.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
  - IM column store [12.1](deploying-in-memory-in-oracle-rac.md)
  - IM FastStart [12.1.4](deploying-in-memory-in-oracle-rac.md)
  - In-Memory data affinity [12.1.3](deploying-in-memory-in-oracle-rac.md)
  - serial queries [12.1.3.1](deploying-in-memory-in-oracle-rac.md)
  - services [12.2](deploying-in-memory-in-oracle-rac.md), [12.2.1](deploying-in-memory-in-oracle-rac.md), [12.2.2](deploying-in-memory-in-oracle-rac.md), [12.2.3](deploying-in-memory-in-oracle-rac.md)
  - shared-nothing architecture [12.1.1](deploying-in-memory-in-oracle-rac.md)
- Oracle Real Application Clusters (Oracle RAC) [1.3.5](intro-to-in-memory-column-store.md)
  - See: Oracle RAC

------------------------------------------------------------------------

## P

- PARALLEL_DEGREE_LIMIT initialization parameter [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
- PARALLEL_DEGREE_POLICY initialization parameter [12.1.3.1](deploying-in-memory-in-oracle-rac.md), [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
- PARALLEL_INSTANCE_GROUP initialization parameter [12.2.1](deploying-in-memory-in-oracle-rac.md), [12.2.2](deploying-in-memory-in-oracle-rac.md), [13.2](deploying-im-column-store-with-adg.md)
- PARALLEL_MIN_TIME_THRESHOLD initialization parameter [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
- parallel queries [1.6.2](intro-to-in-memory-column-store.md), [12.1.3.1](deploying-in-memory-in-oracle-rac.md), [12.1.3.2](deploying-in-memory-in-oracle-rac.md)
  - Oracle RAC [12.1.3](deploying-in-memory-in-oracle-rac.md)
- partitioned tables [12.1.2.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
  - distributing in Oracle RAC [12.1.2.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.1](deploying-in-memory-in-oracle-rac.md), [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md)
  - repopulating [10.2.3](repopulation-and-dml.md)
- partition exchange loads [10.2.3](repopulation-and-dml.md)
- policies, ADO [6](configuring-memory-management.md), [6.1.1](configuring-memory-management.md), [6.1.3.2](configuring-memory-management.md), [6.2.1](configuring-memory-management.md)
- POPULATE_WAIT function [5.1](populating-the-imcs-manually.md), [5.1.3](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
- POPULATE procedure [5.1](populating-the-imcs-manually.md), [5.1.2](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
- population, In-Memory
  - about [5.1](populating-the-imcs-manually.md), [5.1.1](populating-the-imcs-manually.md), [5.1.2](populating-the-imcs-manually.md), [5.1.3](populating-the-imcs-manually.md), [5.1.4](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
  - forcing [5.2](populating-the-imcs-manually.md)
  - ineligible objects [4.1.3.1](populating-objects-in-memory.md)
  - initiating [5.1](populating-the-imcs-manually.md), [5.1.1](populating-the-imcs-manually.md), [5.1.2](populating-the-imcs-manually.md), [5.1.3](populating-the-imcs-manually.md), [5.1.4](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
  - purpose [4.1.1](populating-objects-in-memory.md)
- primary databases, Active Data Guard [13.1.1](deploying-im-column-store-with-adg.md), [13.1.1.1](deploying-im-column-store-with-adg.md), [13.1.1.2](deploying-im-column-store-with-adg.md), [13.1.1.3](deploying-im-column-store-with-adg.md), [13.2](deploying-im-column-store-with-adg.md)
- prioritization, of In-Memory population [4.1.2.1](populating-objects-in-memory.md), [4.1.3.2](populating-objects-in-memory.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)
- PRIORITY clause of CREATE TABLE [4.1.3.2](populating-objects-in-memory.md), [11.1.2.2](managing-im-faststart-for-im-column-store.md)

------------------------------------------------------------------------

## Q

- queries, analytic [1.1](intro-to-in-memory-column-store.md), [1.3](intro-to-in-memory-column-store.md), [1.3.2](intro-to-in-memory-column-store.md), [1.3.2.1](intro-to-in-memory-column-store.md), [1.3.3](intro-to-in-memory-column-store.md)
- query transformations
  - In-Memory Aggregation [9.1](optimizing-in-memory-aggregation.md)

------------------------------------------------------------------------

## R

- REPOPULATE procedure [5.1](populating-the-imcs-manually.md), [5.1.4](populating-the-imcs-manually.md), [5.2](populating-the-imcs-manually.md)
- repopulation
  - controlling [10.4](repopulation-and-dml.md)
  - data loading [10.2](repopulation-and-dml.md)
  - definition [10.1](repopulation-and-dml.md)
  - direct path loads [10.2.2](repopulation-and-dml.md)
  - double buffering [10.2.1.2](repopulation-and-dml.md), [10.3.2](repopulation-and-dml.md)
  - factors affecting [10.3.2](repopulation-and-dml.md)
  - IMEUs [7.1.2.5](optimizing-in-memory-expressions.md)
  - partition exchange load [10.2.3](repopulation-and-dml.md)
  - staleness threshold [10.2.1.1](repopulation-and-dml.md)
  - threshold-based [10.2.1.1](repopulation-and-dml.md), [10.2.1.2](repopulation-and-dml.md), [10.3.1](repopulation-and-dml.md)
  - trickle [10.2.1.2](repopulation-and-dml.md), [10.3.1](repopulation-and-dml.md)
  - tutorial [10.5](repopulation-and-dml.md)
  - when it occurs [10.3](repopulation-and-dml.md)
- REPORT_SQL_MONITOR_XML function [8.7](optimizing-queries-with-join-groups.md)
- row format [2.1](in-memory-column-store-architecture.md)
- rowids
  - distributing by in Oracle RAC [12.1.2.1.3](deploying-in-memory-in-oracle-rac.md)

------------------------------------------------------------------------

## S

- SecureFiles LOBs [11.1.2](managing-im-faststart-for-im-column-store.md), [11.1.2.1](managing-im-faststart-for-im-column-store.md)
- services, Oracle RAC [12.2](deploying-in-memory-in-oracle-rac.md), [12.2.1](deploying-in-memory-in-oracle-rac.md), [12.2.2](deploying-in-memory-in-oracle-rac.md), [12.2.3](deploying-in-memory-in-oracle-rac.md), [12.2.4](deploying-in-memory-in-oracle-rac.md)
- SGA_TARGET initialization parameter [2.1.1.1](in-memory-column-store-architecture.md)
- SGA (system global area)
  - In-Memory Area [1.3.1](intro-to-in-memory-column-store.md), [2.1.1](in-memory-column-store-architecture.md), [3.1](enabling-the-im-column-store.md), [4.3.2](populating-objects-in-memory.md)
  - In-Memory Column Store [2](in-memory-column-store-architecture.md)
- SIMD [2.5.3](in-memory-column-store-architecture.md)
- SIMD vector processing [1.3.2.1](intro-to-in-memory-column-store.md), [2.5](in-memory-column-store-architecture.md), [2.5.1](in-memory-column-store-architecture.md), [4.3.2](populating-objects-in-memory.md), [9.1.2](optimizing-in-memory-aggregation.md)
- SMUs
  - See: Snapshot Metadata Units (SMUs)
- Snapshot Metadata Units (SMUs) [2.2.2](in-memory-column-store-architecture.md), [10.1](repopulation-and-dml.md), [10.2.1](repopulation-and-dml.md), [10.2.1.1](repopulation-and-dml.md), [10.3.1](repopulation-and-dml.md)
  - In-Memory Compression Units (IMCUs) [2.2.2.1](in-memory-column-store-architecture.md)
  - transaction journals [2.2.2.2](in-memory-column-store-architecture.md)
- Space Management Slave Processes (Wnnn) [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md)
- Space Management Worker Processes (Wnnn) [2.4.2](in-memory-column-store-architecture.md), [4.1.2.2](populating-objects-in-memory.md), [7.1.2.4](optimizing-in-memory-expressions.md), [10.3.1](repopulation-and-dml.md), [10.5](repopulation-and-dml.md), [11.1.2](managing-im-faststart-for-im-column-store.md), [11.1.2.1](managing-im-faststart-for-im-column-store.md)
- SRVCTL [12.2.4](deploying-in-memory-in-oracle-rac.md)
- standby databases, Active Data Guard [13.1.1](deploying-im-column-store-with-adg.md), [13.1.1.1](deploying-im-column-store-with-adg.md), [13.1.1.2](deploying-im-column-store-with-adg.md), [13.1.1.3](deploying-im-column-store-with-adg.md), [13.2](deploying-im-column-store-with-adg.md)
- star queries [8.1](optimizing-queries-with-join-groups.md), [9.1.3.4.1](optimizing-in-memory-aggregation.md), [12.1.2.2.2](deploying-in-memory-in-oracle-rac.md), [12.1.2.2.3](deploying-in-memory-in-oracle-rac.md)
- storage mirroring [12.1.2.2](deploying-in-memory-in-oracle-rac.md)
- subpartitioned tables [12.1.2.1.2](deploying-in-memory-in-oracle-rac.md)
- SYS_IME virtual columns [7.1.2.2](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md)
- SYSAUX tablespace [11.1.2.1](managing-im-faststart-for-im-column-store.md)

------------------------------------------------------------------------

## T

- TABLE ACCESS IN MEMORY FULL operation [2.1.2](in-memory-column-store-architecture.md)
- tables
  - external [4.1.3.1.2](populating-objects-in-memory.md), [4.2.3.3](populating-objects-in-memory.md), [5.3.4](populating-the-imcs-manually.md)
  - In-Memory Column Store [4.2.1](populating-objects-in-memory.md), [4.2.2](populating-objects-in-memory.md)
  - INMEMORY subclause [4.1.3.1.1](populating-objects-in-memory.md)
- table scan processes [2.4.3.2.1](in-memory-column-store-architecture.md)
- tablespaces
  - In-Memory Column Store [4.4](populating-objects-in-memory.md)
  - INMEMORY subclause [4.1.3.1.4](populating-objects-in-memory.md)
- threshold-based repopulation [10.2.1.1](repopulation-and-dml.md), [10.2.1.2](repopulation-and-dml.md), [10.3.1](repopulation-and-dml.md)
- transaction journals [2.2.2.2](in-memory-column-store-architecture.md), [10.1](repopulation-and-dml.md), [10.2.1](repopulation-and-dml.md), [10.2.1.1](repopulation-and-dml.md), [10.3.1](repopulation-and-dml.md)
- transformations
  - VECTOR GROUP BY [1.3.2.3](intro-to-in-memory-column-store.md), [9.1.2](optimizing-in-memory-aggregation.md)
- trickle repopulation [10.3.1](repopulation-and-dml.md), [10.5](repopulation-and-dml.md)
  - factors affecting repopulation [10.3.2](repopulation-and-dml.md)

------------------------------------------------------------------------

## V

- V\$HEAT_MAP_SEGMENT view [15](views-related-to-im-column-store.md)
- V\$IM_ADOTASKDETAILS view [6.2.3](configuring-memory-management.md)
- V\$IM_ADOTASKS view [6.2.3](configuring-memory-management.md)
- V\$IM_COLUMN_LEVEL view [4.3.3](populating-objects-in-memory.md), [15](views-related-to-im-column-store.md)
- V\$IM_SEGMENTS view [4.1.2.1](populating-objects-in-memory.md), [10.2.2](repopulation-and-dml.md), [15](views-related-to-im-column-store.md)
  - estimating memory [3.2](enabling-the-im-column-store.md)
- V\$INMEMORY_AREA view [2.1.1.1](in-memory-column-store-architecture.md), [2.1.1.2](in-memory-column-store-architecture.md), [15](views-related-to-im-column-store.md)
- V\$INMEMORY_FASTSTART_AREA view [11.3](managing-im-faststart-for-im-column-store.md), [11.5](managing-im-faststart-for-im-column-store.md)
- V\$SESSION view [8.7](optimizing-queries-with-join-groups.md)
- V\$SGA view [2.1.1.1](in-memory-column-store-architecture.md), [15](views-related-to-im-column-store.md)
- VECTOR_TRANSFORM_DIMS hint [9.1.4](optimizing-in-memory-aggregation.md)
- VECTOR_TRANSFORM_FACT hint [9.1.4](optimizing-in-memory-aggregation.md)
- vector aggregation
  - See: In-Memory Aggregation
- VECTOR GROUP BY aggregation
  - IM column store [9.1.2.2](optimizing-in-memory-aggregation.md)
  - scenarios [9.1.2.1](optimizing-in-memory-aggregation.md)
- VECTOR GROUP BY transformations [1.3.2.3](intro-to-in-memory-column-store.md)
- vector joins
  - In-Memory Column Store [8.1](optimizing-queries-with-join-groups.md)
- vector processing, SIMD [2.5](in-memory-column-store-architecture.md), [4.3.2](populating-objects-in-memory.md)
- virtual columns [4.3.1](populating-objects-in-memory.md), [7.1.2.5](optimizing-in-memory-expressions.md), [7.3](optimizing-in-memory-expressions.md)
  - hidden [7.1.2.2](optimizing-in-memory-expressions.md), [7.1.2.3](optimizing-in-memory-expressions.md)
  - IMEU storage [7.1.2.5](optimizing-in-memory-expressions.md)
  - IM expressions infrastructure [7.1.2.1](optimizing-in-memory-expressions.md)

------------------------------------------------------------------------

## W

- Wnnn processes
  - See: Space Management Worker Processes (Wnnn)
