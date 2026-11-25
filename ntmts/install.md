These topics describe installation requirements for the [Microsoft Transaction Server](glossary.md) and Oracle Database environment.

- Installation Introduction

- Installation Requirements for Microsoft Transaction Server

- [Using Oracle Services for MTS with Oracle Data Provider for .NET\_ Managed Driver](https://docs.oracle.com/en/database/oracle/oracle-database/19/ntmts/unresolvable-reference.html)

- Manually Creating an Oracle MTS Recovery Service

### Installation Introduction

You can install [OraMTS](glossary.md) as part of the Oracle Database Client. OraMTS service will be created for the Oracle Home you installed. Beginning in Oracle 12c, each Oracle Home has its own OraMTS recovery Windows service. Also, beginning in Oracle 12c, the OraMTS service runs as the Oracle Home user.

Oracle Home User is the owner of Oracle Services that run from Oracle Home and cannot be changed after installation. It can be a Windows built-in account or a Windows User Account. For enhanced security, Oracle recommends choosing the standard Windows User Account as Oracle Home User for Oracle Database installations rather than a Windows built-in account. The primary purpose of Oracle Home User is to run Windows services with Windows User Account. However, this user account (Oracle Home User) must be a low-privileged user account that should not be used for database administration. This ensures that Oracle Database services running under Oracle Home User have only the minimal privileges required to run Oracle products. The Windows User Account can be a Local User, a Domain User, or a Managed Services Account.

In some cases, such as a software-only install, clone cycles, or an `AddNode` operation on the database, you may need to manually create the OraMTS service.

This topic describes the Oracle and non-Oracle products you must install for OraMTS. Additional installation requirement is as follows. For [Oracle Data Provider for .NET (ODP.NET)](glossary.md) cluster configurations (or any failover configuration), install Microsoft Transaction Server on the node running the [Microsoft Distributed Transaction Coordinator (MS DTC)](glossary.md) component. This ensures that the Oracle MTS Recovery Service migrates with the client application during failover. You can configure this when scheduling recovery transactions.

**See Also:**

- Manually Creating an Oracle MTS Recovery Service

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md)

### Installation Requirements for Microsoft Transaction Server

The Windows computer where Microsoft Transaction Server is installed has the following product requirements:

#### Oracle Products

- [OraMTS](glossary.md)

- Oracle Database Client, included automatically with the OraMTS installation.

- A data access driver that uses Oracle Services for MTS, such as:

  - [Oracle Data Provider for .NET (ODP.NET)](glossary.md)

  - [Oracle Open Database Connectivity (ODBC) Driver](glossary.md)

  - [Oracle Provider for OLE DB](glossary.md)

  - [Oracle Call Interface (OCI)](glossary.md)

- Access to an Oracle Database 11g Release 2 or higher version

**Note:**

- Oracle ODBC Driver, ODP.NET, Oracle Provider for OLE DB, and OCI are only required if you are building or using components with which they are required.

- Depending on the installation, you are prompted to enter the port number on which the Oracle MTS Recovery Service will listen for requests to resolve in-doubt transactions

#### Non-Oracle Products

- Windows operating system

  **See Also:**

  [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/operating-system-checklist-oracle-database-installation-microsoft-windows.md)

- Microsoft Distributed Transaction Coordinator, which is part of the Windows operating system

### Distributed Transactions

A distributed transaction includes one or more statements that, individually or as a group, update data on two or more distinct nodes of a distributed database.

ODP.NET, Managed and Unmanaged Drivers integrate with Microsoft Distributed Transaction Coordinator (MSDTC) and Oracle databases. MSDTC coordinates with all the resource managers that are enlisted to the same `System.Transactions` object, to perform a 2-phrase commit or rollback atomically. With that, Oracle distributed transactions can then be committed or rolled back across networks properly.

ODP.NET only supports the read committed isolation level for distributed transactions.

**Note:**

ODP.NET Core does not support Distributed Transactions.

#### Microsoft Distributed Transaction Coordinator Integration

Managed ODP.NET includes a native fully managed implementation that supports integration with MSDTC for distributed transactions enlistments, commits, and rollbacks.

For unmanaged ODP.NET, Oracle Services for Microsoft Transaction (OraMTS) provides MSDTC integration that allows client components to participate in Oracle database distributed transactions. OraMTS act as a proxy for the Oracle database to MSDTC to ensure that Oracle distributed database transactions commit or rollback together with the rest of the distributed transaction.

Unmanaged ODP.NET can use either a managed or unmanaged OraMTS implementation. Oracle recommends using the managed OraMTS for applications requiring high availability from Oracle RAC or Data Guard.

If a failure occurs in a distributed transaction, such as a network failure or server hardware failure, then it can leave an in-process transaction in-doubt. Both managed and unmanaged ODP.NET use the OraMTS recovery service to resolve these in-doubt transactions. This recovery service runs as a Windows service. Administrators must install and configure the OraMTS Windows recovery service to manage recovery scenarios whether they use managed or unmanaged ODP.NET. Only one recovery service is needed per machine.

It is required to install the OraMTS Recovery Service on all the client machines where ODP.NET is running and participating in MSDTC. As a machine may have multiple IP addresses, administrators for managed ODP.NET applications can specify the host machine name or IP address that has the running recovery service in the application's .NET configuration file. ODP.NET, Unmanaged Driver resolves the IP/machine name for the recovery service automatically.

Table 2-1 Supported ODP.NET Type and .NET Framework Version for Distributed Transaction

| ODP.NET Type | .NET Framework Version | Distributed Transaction Support                                                                                                                                                         |
|:-------------|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Managed      | 4.5.2 and higher       | .NET Framework's native managed implementation for distributed transactions.                                                                                                            |
| Unmanaged    | 4.5.2 and higher       | OraMTS (default) or managed OraMTS implementation. Oracle recommends using managed OraMTS for unmanaged ODP.NET applications requiring high availability from Oracle RAC or Data Guard. |
| Unmanaged    | 3.5                    | OraMTS                                                                                                                                                                                  |

**Note:**

.NET Framework 4.5.1 and lower within the .NET Framework 4 family are no longer supported by Microsoft and Oracle.

**See Also:**

Manually Creating an Oracle MTS Recovery Service in Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows.

#### ODP.NET, Managed Driver Setup

This section explains the setup and configuration steps required for using distributed transactions with ODP.NET, Managed Driver. Follow these steps to configure distributed transactions in these .NET Framework versions:

1.  Create and setup the OraMTS recovery service or make sure an existing recovery service is running.

2.  Set the value of `OMTSRECO_PORT` in the .NET configuration to specify the port number that the OraMTS recovery service is running.

#### ODP.NET, Unmanaged Driver Setup

This section explains the setup and configuration steps required for using distributed transactions with ODP.NET, Unmanaged Driver.

For .NET Framework 4.5.2 and higher, ODP.NET, Unmanaged Driver includes managed OraMTS in its assembly. OraMTS is the default option for ODP.NET, Unmanaged Driver, to ensure implementation continuity during upgrades. However, Oracle recommends the managed OraMTS option when using any high availability FAN operations (HA Events = true) with Oracle Real Application Clusters or Oracle Data Guard. The managed OraMTS option support high availability functionality, while the traditional OraMTS does not.

Applications can set OraMTS (default) or managed OraMTS usage through the `UseOraMTSManaged` parameter in the .NET configuration file.

Install and configure OraMTS, including its recovery service to use traditional OraMTS implementation for ODP.NET, Unmanaged Driver.

To set managed OraMTS up, perform the following steps:

1.  Set `UseOraMTSManaged` to `true` in the .NET configuration file.

2.  Create and setup the OraMTS recovery service or make sure an existing recovery service is running.

**See Also:**

[distributedTransaction section](../odpnt/InstallManagedConfig.md) for more information about .NET configuration setup

### Manually Creating an Oracle MTS Recovery Service

Starting with Oracle Database 12c, Oracle Database on Windows software includes the `oramtsctl.exe` utility to enable manual creation of the OraMTS recovery service. ODP.NET, Managed and Unmanaged Drivers can both opt to use fully managed MS DTC solutions, which eliminates the need for OraMTS. However, in all cases, the OraMTS recovery service is still required to be setup. Every Oracle client machine that uses MS DTC must have one OraMTS recovery service configured. Multiple Oracle applications on the same machine can share using that one service. When run, the service will be created for the current Oracle home and runs as the Oracle Home User.

To manually create an Oracle MTS Recovery Service:

1.  Install an Oracle Database.

2.  Open the command prompt.

3.  Run this command:

<!-- -->

    oramtsctl -new

To delete an Oracle MTS Recovery Service run:

    oramtsctl -new

    oramtsctl -delete

Usage

    oramtsctl <-new|-delete|-start|-stop|-status|-config|-passwd|-trace|-trcdir>
              [-host    <hostname|IP_address> ...]
              [-port    <number>]
              [-ip      <IP_address>]
              [-dtchost <DTC_hostname>]
              [-cluster <on|off>]
              [-default]

     -new

Create and start a new `Oracler1MTSRecoveryService` service.


     -delete [Oracle_home_directory]

Delete `Oracler1MTSRecoveryService` of current home or specified home.


     -start

Start `Oracler1MTSRecoveryService` service.


     -stop

Stop `Oracler1MTSRecoveryService` service.


     -status Query Oracler1MTSRecoveryService

service status.


     -config [-port <number>] [-ip <IP_address>] [-dtchost <DTC_hostname>]
             [-cluster <on|off>] [-default]

Show or set `Oracler1MTSRecoveryService` service configuration.

Use -default to reset `Oracler1MTSRecoveryService` configuration.


     -passwd

Update `Oracler1MTSRecoveryService` service user password.


     -trace  [0-5]

Show traces or set trace level. Set level 0 to turn off tracing.


     -trcdir [trace_directory]

Show or set trace directory.


     -host   <hostname|IP_address> ...

Execute operation on host(s) identified by name(s) or IP address(es).

Local host is used if option not specified.


     -port   <number>

Execute `-new` or `-config` with this option to specify a service port.

Service port is configured automatically if option not specified.


     -ip     <IP_address>

Execute `-new` or `-config` with this option to specify an IP address.


     -default

Execute `-new` or `-config` with this option to set default configuration.


    oramtsctl -new -host host1 host2.domain.com host3 -port 2033

Examples:

Install the service with automatic configuration:

    oramtsctl -new


Install the service on port 2032:

    oramtsctl -new -port 2032


Configure the service to use port 2033:

    oramtsctl -config -port 2033


Update the service user password:

    oramtsctl -passwd


Install the service on several hosts and use uniform port 2033:

    oramtsctl -new -host host1 host2.domain.com host3 -port 2033
