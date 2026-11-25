This illustration shows a Data Guard configuration during a switchover operation. The San Francisco database (originally the primary database) has changed to the standby role, but the Boston database has not yet changed to the primary role. At this point in time, both the San Francisco and Boston databases are operating in the standby role.

No redo logs are being sent or received over the Oracle Net network. Both of the standby databases are capable of operating in read-only mode.
