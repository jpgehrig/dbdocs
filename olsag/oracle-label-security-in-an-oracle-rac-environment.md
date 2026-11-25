You can use Oracle Label Security in an Oracle Real Application Clusters (Oracle RAC) environment.

- Oracle Label Security Policy Functions in an Oracle RAC Environment
  Policy changes made on one instance are available to other instances in the Oracle Real Application Clusters (Oracle RAC) environment immediately.
- Transparent Application Failover in Oracle Label Security
  Session information is preserved on Transparent Application Failover.

**Parent topic:** [Appendixes](part4.md)

### D.1 Oracle Label Security Policy Functions in an Oracle RAC Environment

Policy changes made on one instance are available to other instances in the Oracle Real Application Clusters (Oracle RAC) environment immediately.

It is not necessary to restart the other instances to pick up the changes.

Important changes made on one database instance are automatically propagated to the other instances. One example would be creating a new policy. Another would be altering the policy options.

Propagating such changes ensures two valuable protections:

- That all users of the table are subject to the same policy

- That if any instance fails, continuation of its work by other instances will use the same policies and parameters that were in force immediately prior to that failure. So, if a policy had been enabled or disabled, it would be seen as such in all instances.

If an administrator changes policy information in one instance by using the policy functions listed in Table D-1, Oracle Label Security stores the relevant information about whatever that function call changed. The new information is immediately available to the other active instances in the Oracle RAC, enabling uniformity among users of the affected policies.

Table D-1 Policy Functions Preserving Status in an Oracle RAC Environment

| Policy Functions           | Description                 |
|:---------------------------|:----------------------------|
| ` SA_SYSDBA.CREATE_POLICY` | Creates a new policy        |
| ` SA_SYSDBA.DROP_POLICY`   | Drops an existing policy    |
| ` SA_SYSDBA.ENABLE_POLICY` | Enables an existing policy  |
| `SA_SYSDBA.DISABLE_POLICY` | Disables an existing policy |
| `SA_SYSDBA.ALTER_POLICY`   | Alters an existing policy   |

**Parent topic:** Oracle Label Security in an Oracle RAC Environment

### D.2 Transparent Application Failover in Oracle Label Security

Session information is preserved on Transparent Application Failover.

Any changes to the session's information by way of session functions listed in Table D-2 are preserved on Transparent Application Failover.

For example, suppose a user `Scott` is logged on with default label `Top Secret`. If he calls sa_session.set_label() to change his session label to `Secret`, and a failover to another instance occurs, he will see no change but his session label remains `Secret`.

Preserving current user session information means that the access permissions and restrictions on what data that user can see or affect remain as they were. Despite the failover, the user can see and affect only the tables and rows accessible before the failover. If preservation were not the case, failing over to another instance could cause or enable the user to see a different set of data.

Whenever one of the session functions listed in Table D-2 is used, Oracle Label Security stores the relevant information about whatever was changed by that function call.

Table D-2 Session Functions Preserving Status in an Oracle RAC Environment

| Session Functions                   | Description                                                                                                         |
|:------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| `SA_SESSION.SET_LABEL`              | Lets the user set a new level and new compartments and groups to which he or she has read access                    |
| `SA_SESSION.SET_ROW_LABEL`          | Lets the user set the default row label that will be applied to new rows                                            |
| `SA_SESSION.SAVE_DEFAULT_LABELS`    | Lets the user store the current session label and row label as the default for future sessions                      |
| `SA_SESSION.RESTORE_DEFAULT_LABELS` | Lets the user reset the current session label and row label to the stored default settings                          |
| `SA_SESSION.SET_ACCESS_PROFILE`     | Sets the Oracle Label Security authorizations and privileges of the database session to those of the specified user |

**Parent topic:** Oracle Label Security in an Oracle RAC Environment
