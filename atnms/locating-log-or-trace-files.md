Use the following table to locate a specific log or trace file for Oracle Database QoS Management.

Table 10-1 Log or Trace Files

| Log File                                                                                               | Location                                                                  |
|:-------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|
| Oracle Database QoS Management server operations log file                                              | `Oracle_Base``/crsdata/``node_name``/qos/logs/dbwlm/auditing/log0.xml`    |
| Oracle Database QoS Management server trace log file                                                   | `Oracle_Base``/crsdata/``node_name``/qos/logs/dbwlm/logging/log0.xml`     |
| Standard out log file and the trace file for the Server Manager (SRVM) component of Oracle Clusterware | `Oracle_Base``/crsdata/``node_name``/qos/logs/qosmserver_stdout.trc.``n`  |
| `qosmserver` standard error log file                                                                   | `Oracle_Base``/crsdata/``node_name``/qos/logs/catalina.``timestamp``.log` |
| Start and stop log file for the DBWLM component of Oracle Database QoS Management                      | `Oracle_Base``/crsdata/``node_name``/qos/logs/catalina.``timestamp``.log` |

**Parent topic:** [Troubleshooting Oracle Database QoS Management](troubleshooting-oracle-database-qos-management.md)
