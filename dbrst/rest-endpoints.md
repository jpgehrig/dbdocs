Sort by

Task Path Method

Group by API

Data Dictionary

The operations from the Data Dictionary category.

[Get a database link](op-database-db_links-owner-db_link-get.md)
Method: get

Path: `/database/db_links/{owner},{db_link}`

[Get a partition](op-database-objects-partitions-table_owner-table_name-partition_name-get.md)
Method: get

Path: `/database/objects/partitions/{table_owner},{table_name},{partition_name}`

[Get a procedure that is defined in package](op-database-objects-packages-procedures-object_id-subprogram_id-get.md)
Method: get

Path: `/database/objects/packages/procedures/{object_id},{subprogram_id}`

[Get a specific column](op-database-objects-columns-owner-table_name-column_name-get.md)
Method: get

Path: `/database/objects/columns/{owner},{table_name},{column_name}`

[Get a specific foreign keys](op-database-objects-foreign_keys-owner-constraint_name-get.md)
Method: get

Path: `/database/objects/foreign_keys/{owner},{constraint_name}`

[Get a specific function](op-database-objects-functions-object_id-get.md)
Method: get

Path: `/database/objects/functions/{object_id}`

[Get a specific index](op-database-objects-indexes-owner-index_name-get.md)
Method: get

Path: `/database/objects/indexes/{owner},{index_name}`

[Get a specific object](op-database-objects-owner-object_name-object_type-get.md)
Method: get

Path: `/database/objects/{owner},{object_name},{object_type}`

[Get a specific table](op-database-objects-tables-owner-table_name-get.md)
Method: get

Path: `/database/objects/tables/{owner},{table_name}`

[Get a synonym](op-database-objects-synonyms-owner-synonym_name-get.md)
Method: get

Path: `/database/objects/synonyms/{owner},{synonym_name}`

[Get all arguments for functions and procedures](op-database-objects-arguments-get.md)
Method: get

Path: `/database/objects/arguments/`

[Get all database links](op-database-db_links-get.md)
Method: get

Path: `/database/db_links/`

[Get all database objects](op-database-objects-get.md)
Method: get

Path: `/database/objects/`

[Get all foreign keys](op-database-objects-foreign_keys-get.md)
Method: get

Path: `/database/objects/foreign_keys/`

[Get all functions](op-database-objects-functions-get.md)
Method: get

Path: `/database/objects/functions/`

[Get all indexes](op-database-objects-indexes-get.md)
Method: get

Path: `/database/objects/indexes/`

[Get all materialized view logs](op-database-objects-materialized_view_logs-get.md)
Method: get

Path: `/database/objects/materialized_view_logs/`

[Get all object types](op-database-objects-types-get.md)
Method: get

Path: `/database/objects/types/`

[Get all partitions in the database](op-database-objects-partitions-get.md)
Method: get

Path: `/database/objects/partitions/`

[Get all procedures defined in package](op-database-objects-packages-procedures-get.md)
Method: get

Path: `/database/objects/packages/procedures/`

[Get all synonyms in the database](op-database-objects-synonyms-get.md)
Method: get

Path: `/database/objects/synonyms/`

[Get all table columns](op-database-objects-columns-get.md)
Method: get

Path: `/database/objects/columns/`

[Get all tables](op-database-objects-tables-get.md)
Method: get

Path: `/database/objects/tables/`

[Get an argument](op-database-objects-arguments-object_id-subprogram_id-argument_name-get.md)
Method: get

Path: `/database/objects/arguments/{object_id},{subprogram_id},{argument_name}`

[Get an object type](op-database-objects-types-owner-type_name-get.md)
Method: get

Path: `/database/objects/types/{owner},{type_name}`

[Get information on a specific materialized view log](op-database-objects-materialized_view_logs-log_owner-log_table-get.md)
Method: get

Path: `/database/objects/materialized_view_logs/{log_owner},{log_table}`

Environment

The operations from the Environment category.

[Create a new database in the default Oracle Home](op-environment-databases-post.md)
Method: post

Path: `/environment/databases/`

[Create a new database in the specified Oracle Home](op-environment-homes-homename-databases-post.md)
Method: post

Path: `/environment/homes/{homeName}/databases/`

[Create a new DBCA job in the default Oracle Home](op-environment-dbca-jobs-post.md)
Method: post

Path: `/environment/dbca/jobs/`

[Create a new DBCA job in the Oracle Home](op-environment-homes-homename-dbca-jobs-post.md)
Method: post

Path: `/environment/homes/{homeName}/dbca/jobs/`

[Delete the specified DBCA job in the default Oracle Home](op-environment-dbca-jobs-jobid-delete.md)
Method: delete

Path: `/environment/dbca/jobs/{jobId}/`

[Delete the specified DBCA job in the default Oracle Home](op-environment-homes-homename-dbca-jobs-jobid-delete.md)
Method: delete

Path: `/environment/homes/{homeName}/dbca/jobs/{jobId}/`

[Get a list of the databases defined in an Oracle Home](op-environment-homes-homename-databases-get.md)
Method: get

Path: `/environment/homes/{homeName}/databases/`

[Get a list of the databases defined in the default Oracle Home](op-environment-databases-get.md)
Method: get

Path: `/environment/databases/`

[Get a list of the DBCA database templates defined in an Oracle Home](op-environment-homes-homename-dbca-templates-get.md)
Method: get

Path: `/environment/homes/{homeName}/dbca/templates/`

[Get a list of the DBCA database templates defined in the default Oracle Home](op-environment-dbca-templates-get.md)
Method: get

Path: `/environment/dbca/templates/`

[Get a list of the DBCA jobs created through ORDS Database API in the default Oracle Home](op-environment-dbca-jobs-get.md)
Method: get

Path: `/environment/dbca/jobs/`

[Get a list of the DBCA jobs created through ORDS Database API in the Oracle Home](op-environment-homes-homename-dbca-jobs-get.md)
Method: get

Path: `/environment/homes/{homeName}/dbca/jobs/`

[Get a specific database defined in a specific Oracle Home](op-environment-homes-homename-databases-databasename-get.md)
Method: get

Path: `/environment/homes/{homeName}/databases/{databaseName}`

[Get a specific database defined in the default Oracle Home](op-environment-databases-databasename-get.md)
Method: get

Path: `/environment/databases/{databaseName}`

[Get a specific database template file in a specific Oracle Home](op-environment-homes-homename-dbca-templates-filename-get.md)
Method: get

Path: `/environment/homes/{homeName}/dbca/templates/{filename}`

[Get a specific database template file in the default Oracle Home](op-environment-dbca-templates-filename-get.md)
Method: get

Path: `/environment/dbca/templates/{filename}`

[Get a specified DBCA jobs created through ORDS Database API in the default Oracle Home](op-environment-dbca-jobs-jobid-get.md)
Method: get

Path: `/environment/dbca/jobs/{jobId}/`

[Get a specified DBCA jobs created through ORDS Database API in the specified Oracle Home](op-environment-homes-homename-dbca-jobs-jobid-get.md)
Method: get

Path: `/environment/homes/{homeName}/dbca/jobs/{jobId}/`

[Get database Oracle Homes](op-environment-homes-get.md)
Method: get

Path: `/environment/homes/`

[Get the DBCA log file content for a specified DBCA jobs created through ORDS Database API in the default Oracle Home](op-environment-dbca-jobs-jobid-log-get.md)
Method: get

Path: `/environment/dbca/jobs/{jobId}/log`

[Get the DBCA log file content for a specified DBCA jobs created through ORDS Database API in the specified Oracle Home](op-environment-homes-homename-dbca-jobs-jobid-log-get.md)
Method: get

Path: `/environment/homes/{homeName}/dbca/jobs/{jobId}/log`

Fleet Patching and Provisioning/RHP - Manage Gold Images

You can create gold images and series to manage your deployments.

[Add a new image series](op-series-seriesid-post.md)
Method: post

Path: `/series/{seriesId}`

[Add image to series](op-series-seriesid-images-imageid-post.md)
Method: post

Path: `/series/{seriesId}/images/{imageId}`

[Delete image series](op-series-seriesid-delete.md)
Method: delete

Path: `/series/{seriesId}`

[Deletes the specified image name](op-images-imageid-delete.md)
Method: delete

Path: `/images/{imageId}`

[Display the configuration of the specified image](op-images-imageid-get.md)
Method: get

Path: `/images/{imageId}`

[Get all the series](op-series-get.md)
Method: get

Path: `/series`

[Get image series](op-series-seriesid-get.md)
Method: get

Path: `/series/{seriesId}`

[Lists all the gold images](op-images-get.md)
Method: get

Path: `/images`

[Lists all the gold images that matches the specified query parameters.](op-images-search-get.md)
Method: get

Path: `/images/search`

[Remove image from series](op-series-seriesid-images-imageid-delete.md)
Method: delete

Path: `/series/{seriesId}/images/{imageId}`

[Schedules an import image operation](op-images-post.md)
Method: post

Path: `/images`

[Search series matching certain parameters](op-series-search-get.md)
Method: get

Path: `/series/search`

[Subscribe a user to a series](op-series-seriesid-users-userid-post.md)
Method: post

Path: `/series/{seriesId}/users/{userId}`

[Unsubscribe a user from a series](op-series-seriesid-users-userid-delete.md)
Method: delete

Path: `/series/{seriesId}/users/{userId}`

Fleet Patching and Provisioning/RHP - Manage Operation Results

You can verify the status and retrieve the output messages of any operation that creates a job to handle its scheduled execution like imaging, provisioning, upgrade and patching operations of software homes.

[Get all the jobs](op-jobs-get.md)
Method: get

Path: `/jobs`

[Get job details](op-jobs-jobid-get.md)
Method: get

Path: `/jobs/{jobId}`

[Get the job output and result](op-jobs-jobid-output-get.md)
Method: get

Path: `/jobs/{jobId}/output`

Fleet Patching and Provisioning/RHP - Patch Software homes

You can move from one provisioned copy of a gold image to a provisioned copy of a gold image that is at a higher patch level.

[Patch an Oracle Database Software home](op-workingcopies-workingcopyid-databases-patch.md)
Method: patch

Path: `/workingcopies/{workingCopyId}/databases`

[Patch Grid Infrastructure Software home](op-workingcopies-workingcopyid-gihome-destwcid-patch.md)
Method: patch

Path: `/workingcopies/{workingCopyId}/gihome/{destWcId}`

Fleet Patching and Provisioning/RHP - Patch Unmanaged Software Homes

You can move from one software home that is not a copy of a gold image to a provisioned copy of a gold image that is at a higher patch level than the first software home.

[Patch an unmanaged Oracle Database Software home](op-databases-patch.md)
Method: patch

Path: `/databases`

[Patch unmanaged Grid Infrastructure Software home](op-gihome-destwcid-patch.md)
Method: patch

Path: `/gihome/{destWcId}`

Fleet Patching and Provisioning/RHP - Provisioning Software homes

You can provision a working copy of a gold image.

[Create Oracle Database Software](op-workingcopies-workingcopyid-databases-post.md)
Method: post

Path: `/workingcopies/{workingCopyId}/databases`

[Create working copy](op-workingcopies-post.md)
Method: post

Path: `/workingcopies`

[Delete working copy](op-workingcopies-workingcopyid-delete.md)
Method: delete

Path: `/workingcopies/{workingCopyId}`

[Get all working copies](op-workingcopies-get.md)
Method: get

Path: `/workingcopies`

[Get working copies based on a certain image type](op-workingcopies-imagetypes-imagetype-get.md)
Method: get

Path: `/workingcopies/imagetypes/{imageType}`

[Get working copy details](op-workingcopies-workingcopyid-get.md)
Method: get

Path: `/workingcopies/{workingCopyId}`

[Search working copies](op-workingcopies-search-get.md)
Method: get

Path: `/workingcopies/search`

Fleet Patching and Provisioning/RHP - Upgrade Software homes

You can move from one provisioned copy of a gold image to a provisioned copy of a gold image that is at a higher version.

[Upgrade an Oracle Database Software home](op-workingcopies-workingcopyid-databases-dbuniquename-put.md)
Method: put

Path: `/workingcopies/{workingCopyId}/databases/{dbUniqueName}`

[Upgrade Grid Infrastructure Software home](op-workingcopies-workingcopyid-gihome-destwcid-put.md)
Method: put

Path: `/workingcopies/{workingCopyId}/gihome/{destWcId}`

Fleet Patching and Provisioning/RHP - Upgrade Unmanaged Software Homes

You can move from one software home that is not a copy of a gold image to a provisioned copy of a gold image that is at a higher version level than the first software home.

[Upgrade an unmanaged Oracle Database Software home](op-databases-dbuniquename-put.md)
Method: put

Path: `/databases/{dbUniqueName}`

[Upgrade unmanaged Grid Infrastructure Software home](op-gihome-destwcid-put.md)
Method: put

Path: `/gihome/{destWcId}`

General

The operations from the General category.

[Create a data pump job](op-database-datapump-jobs-post.md)
Method: post

Path: `/database/datapump/jobs/`

[Create an export data pump job](op-database-datapump-export-post.md)
Method: post

Path: `/database/datapump/export`

[Create an import data pump job](op-database-datapump-import-post.md)
Method: post

Path: `/database/datapump/import`

[Get a database component](op-database-components-comp_id-get.md)
Method: get

Path: `/database/components/{comp_id}`

[Get a description of a specific local listener for this database](op-database-connections-host_name-port-service_name-get.md)
Method: get

Path: `/database/connections/{host_name},{port},{service_name}`

[Get a description of all local listeners for this database](op-database-connections-get.md)
Method: get

Path: `/database/connections/`

[Get a file for a specific data pump job](op-database-datapump-jobs-owner_name-job_name-filename-get.md)
Method: get

Path: `/database/datapump/jobs/{owner_name},{job_name}/{filename}`

[Get a specific data pump job](op-database-datapump-jobs-owner_name-job_name-get.md)
Method: get

Path: `/database/datapump/jobs/{owner_name},{job_name}/`

[Get a specific database parameter](op-database-parameters-name-get.md)
Method: get

Path: `/database/parameters/{name}`

[Get a specific database user](op-database-security-users-username-get.md)
Method: get

Path: `/database/security/users/{username}`

[Get a tablespace](op-database-storage-tablespaces-tablespace_name-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/`

[Get a tablespace segment](op-database-storage-tablespaces-tablespace_name-segments-segment_name-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/segments/{segment_name}`

[Get all data pump jobs](op-database-datapump-jobs-get.md)
Method: get

Path: `/database/datapump/jobs/`

[Get all database components](op-database-components-get.md)
Method: get

Path: `/database/components/`

[Get all database parameters](op-database-parameters-get.md)
Method: get

Path: `/database/parameters/`

[Get all database users](op-database-security-users-get.md)
Method: get

Path: `/database/security/users/`

[Get all feature usage statistics](op-database-feature_usage-get.md)
Method: get

Path: `/database/feature_usage/`

[Get all tablespaces](op-database-storage-tablespaces-get.md)
Method: get

Path: `/database/storage/tablespaces/`

[Get data file usage summary for a specific tablespace](op-database-storage-tablespaces-tablespace_name-datafiles_usage-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/datafiles_usage`

[Get data files for a tablespace](op-database-storage-tablespaces-tablespace_name-datafiles-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/datafiles/`

[Get database status](op-database-status-get.md)
Method: get

Path: `/database/status`

[Get database version](op-database-version-get.md)
Method: get

Path: `/database/version`

[Get specific database Oracle Home](op-environment-homes-homename-get.md)
Method: get

Path: `/environment/homes/{homeName}/`

[Get storage statistics](op-database-storage-bytes-get.md)
Method: get

Path: `/database/storage/bytes`

[Get tablespace data file](op-database-storage-tablespaces-tablespace_name-datafiles-file_id-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/datafiles/{file_id}/`

[Get tablespace data file usage](op-database-storage-tablespaces-tablespace_name-datafiles-file_id-usage-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/datafiles/{file_id}/usage`

[Get tablespace segments](op-database-storage-tablespaces-tablespace_name-segments-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/segments/`

[Get tablespace space usage history](op-database-storage-tablespaces-tablespace_name-history-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/history`

[Get tablespace temporary file](op-database-storage-tablespaces-tablespace_name-tempfiles-file_id-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/tempfiles/{file_id}/`

[Get tablespace temporary file usage](op-database-storage-tablespaces-tablespace_name-tempfiles-file_id-usage-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/tempfiles/{file_id}/usage`

[Get temporary file usage summary for a specific tablespace](op-database-storage-tablespaces-tablespace_name-tempfiles_usage-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/tempfiles_usage`

[Get temporary files for a tablespace](op-database-storage-tablespaces-tablespace_name-tempfiles-get.md)
Method: get

Path: `/database/storage/tablespaces/{tablespace_name}/tempfiles/`

[Get usage statistic for a feature](op-database-feature_usage-dbid-name-get.md)
Method: get

Path: `/database/feature_usage/{dbid},{name}`

Monitoring

The operations from the Monitoring category.

[Get a session](op-database-monitoring-sessions-sid-serial_number-get.md)
Method: get

Path: `/database/monitoring/sessions/{sid},{serial_number}/`

[Get a session lock that is blocking other sessions](op-database-monitoring-session_locks-holding-session_id-lock_id1-lock_id2-get.md)
Method: get

Path: `/database/monitoring/session_locks/holding/{session_id},{lock_id1},{lock_id2}`

[Get a specific lock that a session is waiting on](op-database-monitoring-session_locks-waiting-session_id-lock_id1-lock_id2-get.md)
Method: get

Path: `/database/monitoring/session_locks/waiting/{session_id},{lock_id1},{lock_id2}`

[Get a specific session lock record](op-database-monitoring-session_locks-session_id-lock_id1-lock_id2-get.md)
Method: get

Path: `/database/monitoring/session_locks/{session_id},{lock_id1},{lock_id2}`

[Get a specific session wait](op-database-monitoring-session_waits-sid-seq_number-get.md)
Method: get

Path: `/database/monitoring/session_waits/{sid},{seq_number}`

[Get a specific session wait class record](op-database-monitoring-session_wait_classes-sid-serial_number-wait_class_number-get.md)
Method: get

Path: `/database/monitoring/session_wait_classes/{sid},{serial_number},{wait_class_number}`

[Get all alerts](op-database-monitoring-alerts-get.md)
Method: get

Path: `/database/monitoring/alerts/`

[Get all current sessions](op-database-monitoring-sessions-get.md)
Method: get

Path: `/database/monitoring/sessions/`

[Get all locks held in the database](op-database-monitoring-session_locks-get.md)
Method: get

Path: `/database/monitoring/session_locks/`

[Get all locks that are blocking other sessions](op-database-monitoring-session_locks-holding-get.md)
Method: get

Path: `/database/monitoring/session_locks/holding/`

[Get all locks that sessions are waiting on](op-database-monitoring-session_locks-waiting-get.md)
Method: get

Path: `/database/monitoring/session_locks/waiting/`

[Get all long running operations for a session](op-database-monitoring-sessions-sid-serial_number-long_running_operations-get.md)
Method: get

Path: `/database/monitoring/sessions/{sid},{serial_number}/long_running_operations`

[Get all session limits](op-database-monitoring-session_limits-get.md)
Method: get

Path: `/database/monitoring/session_limits`

[Get all session wait class records](op-database-monitoring-session_wait_classes-get.md)
Method: get

Path: `/database/monitoring/session_wait_classes/`

[Get all session waits](op-database-monitoring-session_waits-get.md)
Method: get

Path: `/database/monitoring/session_waits/`

[Get all wait class metrics](op-database-monitoring-wait_class_metrics-get.md)
Method: get

Path: `/database/monitoring/wait_class_metrics`

[Get an alert record](op-database-monitoring-alerts-record_id-get.md)
Method: get

Path: `/database/monitoring/alerts/{record_id}`

[Get count of alerts by message level](op-database-monitoring-alerts_summaries-by_message_level-get.md)
Method: get

Path: `/database/monitoring/alerts_summaries/by_message_level`

[Get count of alerts by message type](op-database-monitoring-alerts_summaries-by_message_type-get.md)
Method: get

Path: `/database/monitoring/alerts_summaries/by_message_type`

[Get count of different session types](op-database-monitoring-session_summaries-by_type-get.md)
Method: get

Path: `/database/monitoring/session_summaries/by_type`

[Get count of recent alerts by message level](op-database-monitoring-alerts_recent_summaries-by_message_level-get.md)
Method: get

Path: `/database/monitoring/alerts_recent_summaries/by_message_level`

[Get count of recent alerts by message type](op-database-monitoring-alerts_recent_summaries-by_message_type-get.md)
Method: get

Path: `/database/monitoring/alerts_recent_summaries/by_message_type`

[Get current active process for a session](op-database-monitoring-sessions-sid-serial_number-process-get.md)
Method: get

Path: `/database/monitoring/sessions/{sid},{serial_number}/process`

[Get time totals for all registered wait classes](op-database-monitoring-wait_class_totals-get.md)
Method: get

Path: `/database/monitoring/wait_class_totals`

[Get wait time summary from recent active session history records](op-database-monitoring-waits_recent-get.md)
Method: get

Path: `/database/monitoring/waits_recent`

Performance

The operations from the Performance category.

[Get a specified sampled session activity in the database](op-database-performance-active_sessions_history-sample_id-get.md)
Method: get

Path: `/database/performance/active_sessions_history/{sample_id}`

[Get all sampled session activity in the database](op-database-performance-active_sessions_history-get.md)
Method: get

Path: `/database/performance/active_sessions_history/`

[Get all SQL statements ordered by CPU time descending](op-database-performance-top_sql_statements-get.md)
Method: get

Path: `/database/performance/top_sql_statements/`

[Get execution plan for an SQL Statement](op-database-performance-sql_statements-sql_id-plan-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/plan`

[Get historical statistics for a SQL statement](op-database-performance-sql_statements-sql_id-history-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/history`

[Get information on a monitored statement](op-database-performance-sql_statements-sql_id-monitor-sql_exec_id-sql_exec_start-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/monitor/{sql_exec_id},{sql_exec_start}/`

[Get monitoring statistics for a SQL Statement](op-database-performance-sql_statements-sql_id-monitor-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/monitor/`

[Get parallel execution information for specific statement execution](op-database-performance-sql_statements-sql_id-monitor-sql_exec_id-sql_exec_start-parallelism-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/monitor/{sql_exec_id},{sql_exec_start}/parallelism`

[Get SQL statement](op-database-performance-sql_statements-sql_id-text-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/text`

[Get SQL statistics for a specific session](op-database-performance-active_sessions_history_waits-sid-seq_number-active_sql-get.md)
Method: get

Path: `/database/performance/active_sessions_history_waits/{sid},{seq_number}/active_sql`

[Get SQL statistics maximum values](op-database-performance-top_sql_statements-maximums-get.md)
Method: get

Path: `/database/performance/top_sql_statements/maximums`

[Get statistics for a SQL statement](op-database-performance-sql_statements-sql_id-get.md)
Method: get

Path: `/database/performance/sql_statements/{sql_id}/`

[Get statistics for all SQL statements](op-database-performance-sql_statements-get.md)
Method: get

Path: `/database/performance/sql_statements/`

[Get the last 10 wait events for each active session](op-database-performance-active_sessions_history_waits-get.md)
Method: get

Path: `/database/performance/active_sessions_history_waits/`

[Get the specified wait event for specific active session](op-database-performance-active_sessions_history_waits-sid-seq_number-get.md)
Method: get

Path: `/database/performance/active_sessions_history_waits/{sid},{seq_number}/`

Pluggable Database Lifecycle Management

The operations from the Pluggable Database Lifecycle Management category.

[Change the state of a PDB](op-database-pdbs-pdb_name-status-post.md)
Method: post

Path: `/database/pdbs/{pdb_name}/status`

[Clone or Unplug operations for PDBs](op-database-pdbs-pdb_name-post.md)
Method: post

Path: `/database/pdbs/{pdb_name}/`

[Create a PDB from PDB\$SEED or XML](op-database-pdbs-post.md)
Method: post

Path: `/database/pdbs/`

[Drop a PDB](op-database-pdbs-pdb_name-delete.md)
Method: delete

Path: `/database/pdbs/{pdb_name}/`

[Get a pluggable database](op-database-pdbs-pdb_name-get.md)
Method: get

Path: `/database/pdbs/{pdb_name}/`

[Get all pluggable databases](op-database-pdbs-get.md)
Method: get

Path: `/database/pdbs/`

[Return status information of a PDB](op-database-pdbs-pdb_name-status-get.md)
Method: get

Path: `/database/pdbs/{pdb_name}/status`
