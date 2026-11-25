## audit Commands

Use commands with the `audit` keyword to delete, modify, and query audit records.

- rhpctl delete audit
  Deletes the Fleet Patching and Provisioning audit records.
- rhpctl modify audit
  Modifies the maximum number of audit records to store.
- rhpctl query audit
  Displays the Fleet Patching and Provisioning audit records.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl delete audit

Deletes the Fleet Patching and Provisioning audit records.

#### Syntax

    rhpctl delete audit [-to timestamp]

#### Usage Notes

Optionally, you can specify a date up to which audit records will be deleted, in the format `YYYY-MM-DD`. Otherwise, this command deletes all audit records.

**Parent topic:** audit Commands

### rhpctl modify audit

Modifies the maximum number of audit records to store.

#### Syntax

    rhpctl modify audit -maxrecord number

#### Usage Notes

Specify the maximum number of audit records to store.

**Parent topic:** audit Commands

### rhpctl query audit

Displays the Fleet Patching and Provisioning audit records.

#### Syntax

    rhpctl query audit [[[-operation {add | delete | modify | grant | revoke | move | verify | discover
      | upgrade | allow | disallow | deleteimage | insertimage | promote | addnode | deletenode | register | unregister | export | import | query
      | subscribe | unsubscribe}]
      [-entity {client | role | audit | image | imagetype | useraction | series | workingcopy | database | server | user | audit | imagetype | useraction}]
      | [-user user_name] [-client cluster_name] | [-from timestamp -to timestamp]
      | -before timestamp | -since timestamp | -first number | -last number]
      | -record record_id | -config]

#### Parameters

Table A-1 rhpctl query audit Command Parameters

| Parameter                                                                                                                                                                                                                                              | Description                                                                                                                                     |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `-operation {add | delete | modify | grant | revoke | move | verify | discover | upgrade | allow | disallow | deleteimage | insertimage | promote | addnode | deletenode | register | unregister | export | import | query | subscribe | unsubscribe}` | Specify the type of operation for which you want an audit query.                                                                                |
| `-entity {client | role | image | series | workingcopy | database | server | user | audit | imagetype | useraction}`                                                                                                                                   | Specify the entity for which you want an audit query.                                                                                           |
| `-user ``user_name`                                                                                                                                                                                                                                    | Optionally, you can choose to run a query audit on a particular user who performed Fleet Patching and Provisioning operations.                  |
| `-client ``cluster_name`                                                                                                                                                                                                                               | Optionally, you can choose to run a query audit on a particular client cluster where Fleet Patching and Provisioning operations were performed. |
| `-from ``timestamp`` -to ``timestamp`                                                                                                                                                                                                                  | Optionally, you can specify a time interval for which to run an audit query. Timestamps must be in the format `YYYY-MM-DD`.                     |
| `-before ``timestamp`                                                                                                                                                                                                                                  | Optionally, you can specify a time before which to run an audit query. Timestamp must be in the format `YYYY-MM-DD`.                            |
| `-since ``timestamp`                                                                                                                                                                                                                                   | Optionally, you can specify a time after which to run an audit query. Timestamp must be in the format `YYYY-MM-DD`.                             |
| `-first ``number`                                                                                                                                                                                                                                      | Optionally, you can specify a number of the first audit records for a given time.                                                               |
| `-last ``number`                                                                                                                                                                                                                                       | Optionally, you can specify a number of the last audit records for a given time.                                                                |
| `-record ``record_id`                                                                                                                                                                                                                                  | Optionally, you can specify a particular audit record ID.                                                                                       |
| `–config`                                                                                                                                                                                                                                              | You can choose this parameter to show the maximum record configuration.                                                                         |

**Parent topic:** audit Commands
