Sort by

Task Path Method

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
