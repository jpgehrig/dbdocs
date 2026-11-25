## Changes in This Release for Oracle Database Reference

This preface lists changes in Oracle Database Reference:

- Changes in Oracle Database 19c, Release Update 19.28

- Changes in Oracle Database 19c, Release Update 19.26

- Changes in Oracle Database 19c, Release Update 19.23

- Changes in Oracle Database 19c, Release Update 19.22

- Changes in Oracle Database 19c, Release Update 19.16

- Changes in Oracle Database 19c, Release Update 19.13

- Changes in Oracle Database 19c, Release Update 19.11

- Changes in Oracle Database 19c, Release Update 19.10

- Changes in Oracle Database 19c, Release Update 19.6

- Changes in Oracle Database 19c, Release Update 19.4

- Changes in Oracle Database 19c

### Changes in Oracle Database 19c, Release Update 19.28

The following initialization parameters are new in Oracle Database 19c, Release Update 19.28:

- [MFA_DUO_API_HOST](MFA_DUO_API_HOST.md)
- [MFA_OMA_IAM_DOMAIN_URL](MFA_OMA_IAM_DOMAIN_URL.md)
- [MFA_SENDER_EMAIL_DISPLAYNAME](MFA_SENDER_EMAIL_DISPLAYNAME.md)
- [MFA_SENDER_EMAIL_ID](MFA_SENDER_EMAIL_ID.md)
- [MFA_SMTP_HOST](MFA_SMTP_HOST.md)
- [MFA_SMTP_PORT](MFA_SMTP_PORT.md)

The following static data dictionary views are new in Oracle Database 19c, Release Update 19.28:

- [ALL_ANNOTATION_VALUES](ALL_ANNOTATION_VALUES.md), [DBA_ANNOTATION_VALUES](DBA_ANNOTATION_VALUES.md), and [USER_ANNOTATION_VALUES](USER_ANNOTATION_VALUES.md)

- [ALL_ANNOTATIONS](ALL_ANNOTATIONS.md), [DBA_ANNOTATIONS](DBA_ANNOTATIONS.md), and [USER_ANNOTATIONS](USER_ANNOTATIONS.md)

- [ALL_ANNOTATIONS_USAGE](ALL_ANNOTATIONS_USAGE.md), [DBA_ANNOTATIONS_USAGE](DBA_ANNOTATIONS_USAGE.md), and [USER_ANNOTATIONS_USAGE](USER_ANNOTATIONS_USAGE.md)

- [DBA_HIST_SNAPSHOT_DETAILS](DBA_HIST_SNAPSHOT_DETAILS.md)

### Changes in Oracle Database 19c, Release Update 19.26

The following initialization parameter is changed in Oracle Database 19c, Release Update 19.26:

- A new `AUTO` setting is available for the [DB_LOST_WRITE_PROTECT](DB_LOST_WRITE_PROTECT.md) parameter and it is the default setting.

### Changes in Oracle Database 19c, Release Update 19.23

The following initialization parameter is new in Oracle Database 19c, Release Update 19.23:

- [SESSION_EXIT_ON_PACKAGE_STATE_ERROR](SESSION_EXIT_ON_PACKAGE_STATE_ERROR.md)

### Changes in Oracle Database 19c, Release Update 19.22

The following initialization parameter is new in Oracle Database 19c, Release Update 19.22:

- [OGG_ONLINE_DDL](OGG_ONLINE_DDL.md)

The following initialization parameter is changed in Oracle Database 19c, Release Update 19.22:

- The [PRE_PAGE_SGA](PRE_PAGE_SGA.md) initialization parameter is deprecated. The value of [PRE_PAGE_SGA](PRE_PAGE_SGA.md) is always set to `TRUE` on Exadata systems. Any attempt to set this parameter to `FALSE` on an Exadata system will not take effect.

### Changes in Oracle Database 19c, Release Update 19.21

The following initialization parameter is new in Oracle Database 19c, Release Update 19.21:

- [MAIN_WORKLOAD_TYPE](MAIN_WORKLOAD_TYPE.md)

### Changes in Oracle Database 19c, Release Update 19.16

The following initialization parameters are new in Oracle Database 19c, Release Update 19.16:

- [IDENTITY_PROVIDER_CONFIG](IDENTITY_PROVIDER_CONFIG.md)

- [IDENTITY_PROVIDER_TYPE](IDENTITY_PROVIDER_TYPE.md)

- [TABLESPACE_ENCRYPTION](TABLESPACE_ENCRYPTION.md)

### Changes in Oracle Database 19c, Release Update 19.13

#### New AE Analytic Views

Oracle Database 19c, Release Update 19.13, introduces `AE` ("all edition") analytic views. Each new `AE` analytic view corresponds to an existing non-`AE` analytic view. `AE` views have the same columns as their non-`AE` counterparts, plus a column that displays the name of the application edition where the editioned object is defined.

The following table lists the new `AE` analytic views, divided into three categories: analytic view views, attribute dimension views, and hierarchy views. For brevity, only the `ALL_` views are listed. The corresponding `DBA_` and `USER_` views are also available and are documented in this guide.

| Analytic View Views                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Attribute Dimension Views                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Hierarchy Views                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ALL_ANALYTIC_VIEW_ATTR_CLS_AE](ALL_ANALYTIC_VIEW_ATTR_CLS_AE.md)<br>[ALL_ANALYTIC_VIEW_BAS_MEAS_AE](ALL_ANALYTIC_VIEW_BAS_MEAS_AE.md)<br>[ALL_ANALYTIC_VIEW_CLASS_AE](ALL_ANALYTIC_VIEW_CLASS_AE.md)<br>[ALL_ANALYTIC_VIEW_CLC_MEAS_AE](ALL_ANALYTIC_VIEW_CLC_MEAS_AE.md)<br>[ALL_ANALYTIC_VIEW_COLUMNS_AE](ALL_ANALYTIC_VIEW_COLUMNS_AE.md)<br>[ALL_ANALYTIC_VIEW_DIM_CLS_AE](ALL_ANALYTIC_VIEW_DIM_CLS_AE.md)<br>[ALL_ANALYTIC_VIEW_DIMS_AE](ALL_ANALYTIC_VIEW_DIMS_AE.md)<br>[ALL_ANALYTIC_VIEW_HIER_CLS_AE](ALL_ANALYTIC_VIEW_HIER_CLS_AE.md)<br>[ALL_ANALYTIC_VIEW_HIERS_AE](ALL_ANALYTIC_VIEW_HIERS_AE.md)<br>[ALL_ANALYTIC_VIEW_KEYS_AE](ALL_ANALYTIC_VIEW_KEYS_AE.md)<br>[ALL_ANALYTIC_VIEW_LEVELS_AE](ALL_ANALYTIC_VIEW_LEVELS_AE.md)<br>[ALL_ANALYTIC_VIEW_LVL_CLS_AE](ALL_ANALYTIC_VIEW_LVL_CLS_AE.md)<br>[ALL_ANALYTIC_VIEW_LVLGRPS_AE](ALL_ANALYTIC_VIEW_LVLGRPS_AE.md)<br>[ALL_ANALYTIC_VIEW_MEAS_CLS_AE](ALL_ANALYTIC_VIEW_MEAS_CLS_AE.md)<br>[ALL_ANALYTIC_VIEWS_AE](ALL_ANALYTIC_VIEWS_AE.md) | [ALL_ATTRIBUTE_DIM_ATTR_CLS_AE](ALL_ATTRIBUTE_DIM_ATTR_CLS_AE.md)<br>[ALL_ATTRIBUTE_DIM_ATTRS_AE](ALL_ATTRIBUTE_DIM_ATTRS_AE.md)<br>[ALL_ATTRIBUTE_DIM_CLASS_AE](ALL_ATTRIBUTE_DIM_CLASS_AE.md)<br>[ALL_ATTRIBUTE_DIM_JN_PTHS_AE](ALL_ATTRIBUTE_DIM_JN_PTHS_AE.md)<br>[ALL_ATTRIBUTE_DIM_KEYS_AE](ALL_ATTRIBUTE_DIM_KEYS_AE.md)<br>[ALL_ATTRIBUTE_DIM_LEVELS_AE](ALL_ATTRIBUTE_DIM_LEVELS_AE.md)<br>[ALL_ATTRIBUTE_DIM_LVL_ATRS_AE](ALL_ATTRIBUTE_DIM_LVL_ATRS_AE.md)<br>[ALL_ATTRIBUTE_DIM_LVL_CLS_AE](ALL_ATTRIBUTE_DIM_LVL_CLS_AE.md)<br>[ALL_ATTRIBUTE_DIM_ORD_ATRS_AE](ALL_ATTRIBUTE_DIM_ORD_ATRS_AE.md)<br>[ALL_ATTRIBUTE_DIM_TABLES_AE](ALL_ATTRIBUTE_DIM_TABLES_AE.md)<br>[ALL_ATTRIBUTE_DIMENSIONS_AE](ALL_ATTRIBUTE_DIMENSIONS_AE.md) | [ALL_HIER_CLASS_AE](ALL_HIER_CLASS_AE.md)<br>[ALL_HIER_COLUMNS_AE](ALL_HIER_COLUMNS_AE.md)<br>[ALL_HIER_HIER_ATTR_CLASS_AE](ALL_HIER_HIER_ATTR_CLASS_AE.md)<br>[ALL_HIER_HIER_ATTRIBUTES_AE](ALL_HIER_HIER_ATTRIBUTES_AE.md)<br>[ALL_HIER_JOIN_PATHS_AE](ALL_HIER_JOIN_PATHS_AE.md)<br>[ALL_HIER_LEVEL_ID_ATTRS_AE](ALL_HIER_LEVEL_ID_ATTRS_AE.md)<br>[ALL_HIER_LEVELS_AE](ALL_HIER_LEVELS_AE.md)<br>[ALL_HIERARCHIES_AE](ALL_HIERARCHIES_AE.md)<br> |

### Changes in Oracle Database 19c, Release Update 19.11

The following initialization parameter is new in Oracle Database 19c, Release Update 19.11:

- [DRCP_DEDICATED_OPT](DRCP_DEDICATED_OPT.md)

The following static data dictionary views are new in Oracle Database 19c, Release Update 19.11:

- [DBA_ACCHK_EVENTS](DBA_ACCHK_EVENTS.md)

- [DBA_ACCHK_EVENTS_SUMMARY](DBA_ACCHK_EVENTS_SUMMARY.md)

- [DBA_ACCHK_STATISTICS](DBA_ACCHK_STATISTICS.md)

- [DBA_ACCHK_STATISTICS_SUMMARY](DBA_ACCHK_STATISTICS_SUMMARY.md)

- [ALL_IMMUTABLE_TABLES](ALL_IMMUTABLE_TABLES.md), [DBA_IMMUTABLE_TABLES](DBA_IMMUTABLE_TABLES.md), and [USER_IMMUTABLE_TABLES](USER_IMMUTABLE_TABLES.md)

### Changes in Oracle Database 19c, Release Update 19.10

The following initialization parameters are new in Oracle Database 19c, Release Update 19.10:

- [BLOCKCHAIN_TABLE_MAX_NO_DROP](BLOCKCHAIN_TABLE_MAX_NO_DROP.md)

- [CONTAINER_DATA](CONTAINER_DATA.md)

- [MAX_AUTH_SERVERS](MAX_AUTH_SERVERS.md)

- [MIN_AUTH_SERVERS](MIN_AUTH_SERVERS.md)

- [OPTIMIZER_REAL_TIME_STATISTICS](OPTIMIZER_REAL_TIME_STATISTICS.md)

The following static data dictionary views are new in Oracle Database 19c, Release Update 19.10:

- [ALL_BLOCKCHAIN_TABLES](ALL_BLOCKCHAIN_TABLES.md), [DBA_BLOCKCHAIN_TABLES](DBA_BLOCKCHAIN_TABLES.md), and [USER_BLOCKCHAIN_TABLES](USER_BLOCKCHAIN_TABLES.md)

- [ALL_CERTIFICATES](ALL_CERTIFICATES.md), [DBA_CERTIFICATES](DBA_CERTIFICATES.md), and [USER_CERTIFICATES](USER_CERTIFICATES.md)

- [DBA_LOGMNR_DICTIONARY_BUILDLOG](DBA_LOGMNR_DICTIONARY_BUILDLOG.md)

### Changes in Oracle Database 19c, Release Update 19.6

The following initialization parameter is new in Oracle Database 19c, Release Update 19.6:

- [OPTIMIZER_SESSION_TYPE](OPTIMIZER_SESSION_TYPE.md)

### Changes in Oracle Database 19c, Release Update 19.4

The following initialization parameter is new in Oracle Database 19c, Release Update 19.4:

- [IGNORE_SESSION_SET_PARAM_ERRORS](IGNORE_SESSION_SET_PARAM_ERRORS.md)

### Changes in Oracle Database 19c

This section lists changes in Oracle Database Reference for Oracle Database 19c.

See [Oracle Database New Features Guide](../newft/index.md) for a complete list of new features for this release.

#### New Features

This section lists new features in this manual for Oracle Database 19c.

The following changes to initialization parameters are new in Oracle Database 19c:

- On Linux platforms only, Oracle recommends against explicitly setting values for `MEMORY_TARGET` and `MEMORY_MAX_TARGET` in the initialization parameter file at the time of instance startup. Doing so may result in suboptimal small page allocation in the SGA. Furthermore, if the `USE_LARGE_PAGES` parameter is set to `ONLY` and you attempt to set values for `MEMORY_TARGET` and `MEMORY_MAX_TARGET`, the instance will fail to start.

  See [MEMORY_TARGET](MEMORY_TARGET.md), [MEMORY_MAX_TARGET](MEMORY_MAX_TARGET.md), and [USE_LARGE_PAGES](USE_LARGE_PAGES.md).

The following initialization parameters are new in Oracle Database 19c:

- [ADG_REDIRECT_DML](ADG_REDIRECT_DML.md)

- [ALLOW_ROWID_COLUMN_TYPE](ALLOW_ROWID_COLUMN_TYPE.md)

- [CLIENT_STATISTICS_LEVEL](CLIENT_STATISTICS_LEVEL.md)

- [CPU_MIN_COUNT](CPU_MIN_COUNT.md)

- [DATA_GUARD_MAX_IO_TIME](DATA_GUARD_MAX_IO_TIME.md)

- [DATA_GUARD_MAX_LONGIO_TIME](DATA_GUARD_MAX_LONGIO_TIME.md)

- [ENABLE_IMC_WITH_MIRA](ENABLE_IMC_WITH_MIRA.md)

- [LOB_SIGNATURE_ENABLE](lob_signature_enable.md)

- [MAX_DATAPUMP_PARALLEL_PER_JOB](MAX_DATAPUMP_PARALLEL_PER_JOB.md)

- [MAX_IDLE_BLOCKER_TIME](MAX_IDLE_BLOCKER_TIME.md)

- [OPTIMIZER_CAPTURE_SQL_QUARANTINE](OPTIMIZER_CAPTURE_SQL_QUARANTINE.md)

- [OPTIMIZER_USE_SQL_QUARANTINE](OPTIMIZER_USE_SQL_QUARANTINE.md)

- [UNIFIED_AUDIT_COMMON_SYSTEMLOG](UNIFIED_AUDIT_COMMON_SYSTEMLOG.md)

**Note:**

See [Initialization Parameters](initialization-parameters.md) for more information about these initialization parameters.

The following static data dictionary views are new in Oracle Database 19c:

- [ALL_TRIGGERS_AE](ALL_TRIGGERS_AE.md), [DBA_TRIGGERS_AE](DBA_TRIGGERS_AE.md), and [USER_TRIGGERS_AE](USER_TRIGGERS_AE.md)

- [DBA_AUTO_INDEX_CONFIG](DBA_AUTO_INDEX_CONFIG.md)

- [DBA_AUTO_STAT_EXECUTIONS](DBA_AUTO_STAT_EXECUTIONS.md)

- [DBA_PDB_SNAPSHOTFILE](DBA_PDB_SNAPSHOTFILE.md)

- [DBA_RAT_CAPTURE_SCHEMA_INFO](DBA_RAT_CAPTURE_SCHEMA_INFO.md)

- [DBA_REGISTRY_BACKPORTS](DBA_REGISTRY_BACKPORTS.md)

- [DBA_SQL_QUARANTINE](DBA_SQL_QUARANTINE.md)

**Note:**

[Static Data Dictionary Views](static-data-dictionary-views.md) for more information about these static data dictionary views

The following dynamic performance views are new in Oracle Database 19c:

- GV\$AQ_PARTITION_STATS and [V\$AQ_PARTITION_STATS](V-AQ_PARTITION_STATS.md)

- GV\$ASM_ACFSAUTORESIZE and [V\$ASM_ACFSAUTORESIZE](V-ASM_ACFSAUTORESIZE.md)

- GV\$MEMOPTIMIZE_WRITE_AREA and [V\$MEMOPTIMIZE_WRITE_AREA](V-MEMOPTIMIZE_WRITE_AREA.md)

- GV\$SHARED_SERVER_STAT and [V\$SHARED_SERVER_STAT](V-SHARED_SERVER_STAT.md)

- GV\$SQL_TESTCASES and [V\$SQL_TESTCASES](V-SQL_TESTCASES.md)

**Note:**

[GV\$ Views](about-dynamic-performance-views.md) and [Dynamic Performance Views](dynamic-performance-views.md) for more information about these dynamic performance views

#### Deprecated Features

The following features are deprecated in Oracle Database 19c, and may be desupported in a future release:

- The [CLUSTER_DATABASE_INSTANCES](CLUSTER_DATABASE_INSTANCES.md) initialization parameter

- The [PRE_PAGE_SGA](PRE_PAGE_SGA.md) initialization parameter (starting with Oracle Database 19c, Release Update 19.22)

- The [SERVICE_NAMES](SERVICE_NAMES.md) initialization parameter

#### Desupported Features

The following features are desupported in Oracle Database 19c:

- The `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` initialization parameter, for Oracle Data Guard redo transport

- The `EXAFUSION_ENABLED` initialization parameter

- The `O7_DICTIONARY_ACCESSIBILITY` initialization parameter

- Oracle Streams is desupported. As a result, the following views are desupported:
  - `ALL_STREAMS_COLUMNS`
  - `ALL_STREAMS_MESSAGE_RULES`
  - `ALL_STREAMS_RULES`
  - `ALL_STREAMS_UNSUPPORTED`
  - `DBA_STREAMS_ADMINISTRATOR`
  - `DBA_STREAMS_COLUMNS`
  - `DBA_STREAMS_MESSAGE_RULES`
  - `DBA_STREAMS_RULES`
  - `DBA_STREAMS_SPLIT_MERGE`
  - `DBA_STREAMS_SPLIT_MERGE_HIST`
  - `DBA_STREAMS_STMTS`
  - `DBA_STREAMS_STMT_HANDLERS`
  - `DBA_STREAMS_TRANSFORMATIONS`
  - `DBA_STREAMS_UNSUPPORTED`
  - `V$STREAMS_CAPTURE`
  - `V$STREAMS_MESSAGE_TRACKING`
  - `V$STREAMS_TRANSACTION`

- Extended Datatype Support (EDS) is desupported. As a result, the following views are desupported:
  - `DBA_LOGSTDBY_EDS_SUPPORTED`
  - `DBA_LOGSTDBY_EDS_TABLES`

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)
