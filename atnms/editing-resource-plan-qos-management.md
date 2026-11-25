You can perform limited editing of the Resource Manager plans used by Oracle Database Quality of Service Management.

Oracle Database QoS Management activates a resource plan named `APPQOS_PLAN`, which is a complex, multilevel resource plan. Oracle Database QoS Management also creates consumer groups that represent Performance Classes and resource plan directives for each consumer group.

You can modify some of the sections of the `APPQOS_PLAN`, or `ORA$QOS_PLAN` and `ORA$QOS_CDB_PLAN` for Multitenant databases, but only as specified in the following table:

| Plan Component | Modifiable?           | Description                                                                                                                                                                                                                                                                     |
|:---------------|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| General        | DO NOT EDIT           | This section must not be edited as it is key to the QoS Management modeling and recommendation engine. If you modify this section, the change will be detected. In that case, Oracle Enterprise Manager Cloud Control reports a database error on the QoS Management dashboard. |
| Parallelism    | Limited edits allowed | This section can be edited however all values set for the `ORA$APPQOS*` consumer groups must be the same within each column due to the reason stated above.                                                                                                                     |
| Thresholds     | Limited edits allowed | This section can be edited however all values set for the `ORA$APPQOS*` consumer groups must be the same within each column due to the reason stated above. In addition, none of the "Switch to \*" actions should be selected for these groups.                                |
| Idle Time      | Limited edits allowed | This section can be edited however all values set for the `ORA$APPQOS*` consumer groups must be the same within each column due to the reason stated above.                                                                                                                     |

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md)

**Parent topic:** [Administering the Oracle Database QoS Management System](administering-oracle-database-qos-management-system.md)
