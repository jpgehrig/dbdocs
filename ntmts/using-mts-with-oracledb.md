These topics describe [Microsoft Transaction Server](glossary.md) and Oracle Database integration.

- Microsoft Transaction Server Overview

- Microsoft Transaction Server and Oracle Integration Overview

- Getting Started with Microsoft Transaction Server and Oracle

### Microsoft Transaction Server Overview

Microsoft Transaction Server is a proprietary [component object model (COM)](glossary.md) transaction processing system that runs on an Internet or network server. Microsoft Transaction Server deploys and manages application and database transaction requests on behalf of a client computer. Microsoft Transaction Server provides:

- ActiveX/[distributed component object model (DCOM)](glossary.md) programming model to develop distributed applications and a runtime environment in which to deploy these applications.

- [Atomicity\_ Consistency\_ Isolation\_ and Durability (ACID)](glossary.md) properties for components in transactions.

- Access to performance-enhancing features such as component caching and database connection pooling.

Microsoft Transaction Server is a component of the three-tiered, server-centric architecture model. This model lets you separate the presentation, business logic, and data elements of applications onto different computers connected in a network. Microsoft Transaction Server functionality is also implemented in COM+ and Enterprise Services. Oracle Services for Microsoft Transaction Server, or [OraMTS](glossary.md), support Microsoft Transaction Server, COM+, and Enterprise Services.

**See Also:**

Microsoft documentation for additional information about Microsoft Transaction Server

### Microsoft Transaction Server and Oracle Integration Overview

Without any special integration, you can deploy applications that were created using Win32, Win64, COM, or [Microsoft .NET](glossary.md) with a Microsoft Transaction Server that connects to an Oracle Database. To use either of the following features, however, you must install [Oracle Services for Microsoft Transaction Server (OraMTS)](glossary.md):

- Register the Win32, Win64, COM or .NET application as transactional and have Microsoft Transaction Server control the transaction. You can do this by using the Properties dialog box of the component in the Microsoft Management Console Explorer.

- Use client-side connection pooling in Microsoft Transaction Server.

After you have installed Oracle Services for Microsoft Transaction Server, an [Oracle MTS Recovery Service](glossary.md) is also automatically installed on the same computer. The Oracle MTS Recovery Service helps in the recovery of in-doubt transactions left in Oracle Database instances that originated from this computer. On each connected database:

- Create the Microsoft Transaction Server administrator user account.

- Schedule a database-level transaction recovery job.

This enables the database to participate in Microsoft Transaction Server-started transactions.

Create the COM component with any of the following Oracle products:

- [Oracle Data Provider for .NET (ODP.NET)](glossary.md).

- [Oracle Open Database Connectivity (ODBC) Driver](glossary.md)

- [Oracle Provider for OLE DB](glossary.md)

- [Oracle Call Interface (OCI)](glossary.md)

#### Oracle Services for Microsoft Transaction Server Support for DTC

Oracle Services for Microsoft Transaction Server works with Microsoft Distributed Transaction Coordinator (DTC), which is part of the Windows operating system. DTC implements a two-phase commit protocol that makes sure that the transaction outcome is consistent across all data resources involved in a transaction.

#### Distributed Transactions on Real Application Clusters (Oracle RAC)

With Oracle Database Release 11.1, the database now redirect all the branches of a distributed transaction to a single Oracle RAC instance automatically. Previously developers needed to manually manage this process, individually redirecting all the branches to a single Oracle RAC instance.

**See Also:**

Oracle Real Application Clusters Administration and Deployment Guide to learn more about distributed transactions in Real Application Clusters.

#### Promotable Local Transactions

Promotable local transactions allow all transactions to remain local until more than one database is brought into the transaction, at which point, they are promoted to distributed transactions.

The flexibility of the promotable transaction feature ensures more efficient resource usage for transactional applications. Distributed transactions require significant overhead versus local transactions. Therefore, local transactions are preferred if only one database is used. At design-time, it may not be known when transactions are local or distributed. Prior to this feature, developers always had to use distributed transactions, even if local ones occurred most of the time, leading to unnecessary resource usage.

This feature is supported with Oracle Database 11g Release 1 and higher. Earlier database versions and other resource managers can participate in a promotable transaction as long as the first connection is to an Oracle Database 11g Release 1 data source or higher.

**See Also:**

[Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featOraCommand.md) for more information on `System.Transactions` support

#### Read-Committed and Serializable Transactions

Oracle Services for Microsoft Transaction Server supports distributed transactions set to a serializable or read-committed isolation level.

### Getting Started with Microsoft Transaction Server and Oracle

You are now ready to use Microsoft Transaction Server with a database. To get started quickly, follow these steps:

1.  Install the Oracle and Microsoft products required for Microsoft Transaction Server and database integration.
    See [Installing Oracle Services for Microsoft Transaction Server](install.md) .
2.  Create the Microsoft Transaction Server administrator user account.
    See [Managing Recovery Scenarios](managing-recovery-scenarios.md).
3.  Schedule a Microsoft Transaction Server transaction recovery job.
    See [Managing Recovery Scenarios](managing-recovery-scenarios.md).
4.  Create Microsoft Transaction Server-hosted applications.
    See [Programming with Microsoft Transaction Server and an Oracle Database](program.md) for instructions on using OCI, Oracle ODBC Driver, or Oracle Provider for OLE DB with COM-based applications.
5.  Learn about using Microsoft Transaction Server on the different Windows operating systems.
