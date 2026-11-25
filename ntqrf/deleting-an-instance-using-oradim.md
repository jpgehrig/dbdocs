Learn how to delete an instance using ORADIM.

To use ORADIM to delete an instance, enter:

    oradim -DELETE -SID SID | -ASMSID SID | -SRVC service_name | -ASMSRVC service_name

For this command, note the following:

- `-DELETE` indicates that you are deleting an instance or service. This is a mandatory parameter.

- `-SID` `SID` specifies the name of the `SID` to delete.

- `-SRVC` `service_name` specifies the name of the service to delete (`OracleService``SID`). The user must specify either `SID` or `SRVC`.

- `-ASMSID ``SID` is the name of the Oracle Automatic Storage Management instance to delete.

- `-ASMSRVC ``service_name` is the name of the Oracle Automatic Storage Management service to delete.

To delete an instance called `prod`, for example, enter:

    C:\> oradim -DELETE -SID prod

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
