Learn how to stop an instance and services using ORADIM.

To use ORADIM to stop an instance, enter:

    oradim -SHUTDOWN -SID SID | -ASMSID SID [-SYSPWD password]
    [-SHUTTYPE srvc | inst | srvc,inst] [-SHUTMODE normal | immediate | abort]

For this command, note the following:

- `-SHUTDOWN` indicates that you are stopping an instance. This is a mandatory parameter.

- `-SID` `SID` specifies the name of the instance to stop.

- `-ASMSID ``SID` is the name of the Oracle Automatic Storage Management instance to stop.

- `-SHUTTYPE` `srvc`, `inst` indicates whether to stop the service or the instance. One or both values can be specified. If it is not specified, then the registry is checked for the current setting.

- `-SHUTMODE` specifies how to stop an instance. This is an optional parameter. If you do not specify how to stop an instance, then `immediate` is the default mode.

To stop an instance called `puma`, for example, enter:

    C:\> oradim -SHUTDOWN -SID puma -SHUTTYPE srvc,inst

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
