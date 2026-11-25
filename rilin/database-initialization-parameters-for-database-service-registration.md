## Database Initialization Parameters for Database Service Registration

An Oracle Database 19c database service automatically registers with the listeners specified in the `LOCAL_LISTENER` and `REMOTE_LISTENER` parameters.

During registration, the listener registration (LREG) process sends information such as the service name, instance names, and workload information to the listeners. When a listener starts after the Oracle instance starts, and the listener is available for service registration, registration does not occur until the next time the Oracle Database LREG process starts its discovery routine. By default, the LREG discovery routine is started every 60 seconds. To override the 60-second delay, use the SQL statement `ALTER SYSTEM REGISTER`. This statement forces LREG to register the service immediately.

**Note:**

Oracle recommends that you create a script to run the `ALTER SYSTEM REGISTER` statement immediately after starting the listener. If you run this statement when the instance is registered and all services are currently registered, or while the listener is down, then the statement has no effect.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/understanding-oracle-net-architecture.md) for more information about service registration

**Parent topic:** [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
