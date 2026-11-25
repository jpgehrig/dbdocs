A distributed transaction includes one or more statements that, individually or as a group, update data on two or more distinct nodes of a distributed database.

ODP.NET, Managed and Unmanaged Drivers integrate with Microsoft Distributed Transaction Coordinator (MSDTC) and Oracle databases. MSDTC coordinates with all the resource managers that are enlisted to the same `System.Transactions` object, to perform a 2-phrase commit or rollback atomically. With that, Oracle distributed transactions can then be committed or rolled back across networks properly.

ODP.NET only supports the read committed isolation level for distributed transactions.

**Note:**

ODP.NET Core does not support Distributed Transactions.

### Microsoft Distributed Transaction Coordinator Integration

Managed ODP.NET includes a native fully managed implementation that supports integration with MSDTC for distributed transactions enlistments, commits, and rollbacks.

For unmanaged ODP.NET, Oracle Services for Microsoft Transaction (OraMTS) provides MSDTC integration that allows client components to participate in Oracle database distributed transactions. OraMTS act as a proxy for the Oracle database to MSDTC to ensure that Oracle distributed database transactions commit or rollback together with the rest of the distributed transaction.

Unmanaged ODP.NET can use either a managed or unmanaged OraMTS implementation. Oracle recommends using the managed OraMTS for applications requiring high availability from Oracle RAC or Data Guard.

If a failure occurs in a distributed transaction, such as a network failure or server hardware failure, then it can leave an in-process transaction in-doubt. Both managed and unmanaged ODP.NET use the OraMTS recovery service to resolve these in-doubt transactions. This recovery service runs as a Windows service. Administrators must install and configure the OraMTS Windows recovery service to manage recovery scenarios whether they use managed or unmanaged ODP.NET. Only one recovery service is needed per machine.

It is required to install the OraMTS Recovery Service on all the client machines where ODP.NET is running and participating in MSDTC. As a machine may have multiple IP addresses, administrators for managed ODP.NET applications can specify the host machine name or IP address that has the running recovery service in the application's .NET configuration file. ODP.NET, Unmanaged Driver resolves the IP/machine name for the recovery service automatically.

Table 2-9 Supported ODP.NET Type and .NET Framework Version for Distributed Transaction

| ODP.NET Type | .NET Framework Version | Distributed Transaction Support                                                                                                                                                         |
|:-------------|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Managed      | 4.5.2 and higher       | .NET Framework's native managed implementation for distributed transactions.                                                                                                            |
| Unmanaged    | 4.5.2 and higher       | OraMTS (default) or managed OraMTS implementation. Oracle recommends using managed OraMTS for unmanaged ODP.NET applications requiring high availability from Oracle RAC or Data Guard. |
| Unmanaged    | 3.5                    | OraMTS                                                                                                                                                                                  |

**Note:**

.NET Framework 4.5.1 and lower within the .NET Framework 4 family are no longer supported by Microsoft and Oracle.

**See Also:**

Manually Creating an Oracle MTS Recovery Service in [Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/install.md).

### ODP.NET, Managed Driver Setup

This section explains the setup and configuration steps required for using distributed transactions with ODP.NET, Managed Driver. Follow these steps to configure distributed transactions in these .NET Framework versions:

1.  Create and setup the OraMTS recovery service or make sure an existing recovery service is running.

2.  Set the value of `OMTSRECO_PORT` in the .NET configuration to specify the port number that the OraMTS recovery service is running.

### ODP.NET, Unmanaged Driver Setup

This section explains the setup and configuration steps required for using distributed transactions with ODP.NET, Unmanaged Driver.

For .NET Framework 4.5.2 and higher, ODP.NET, Unmanaged Driver includes managed OraMTS in its assembly. OraMTS is the default option for ODP.NET, Unmanaged Driver, to ensure implementation continuity during upgrades. However, Oracle recommends the managed OraMTS option when using any high availability FAN operations (HA Events = true) with Oracle Real Application Clusters or Oracle Data Guard. The managed OraMTS option support high availability functionality, while the traditional OraMTS does not.

Applications can set OraMTS (default) or managed OraMTS usage through the `UseOraMTSManaged` parameter in the .NET configuration file.

Install and configure OraMTS, including its recovery service to use traditional OraMTS implementation for ODP.NET, Unmanaged Driver.

To set managed OraMTS up, perform the following steps:

1.  Set `UseOraMTSManaged` to `true` in the .NET configuration file.

2.  Create and setup the OraMTS recovery service or make sure an existing recovery service is running.

**See Also:**

[distributedTransaction section](InstallManagedConfig.md) for more information about .NET configuration setup
