## What Is Interoperability for Oracle Database Upgrades?

In the context of upgrading Oracle Database, interoperability is the ability of different releases of Oracle Database to communicate and work in a distributed environment.

A distributed database system can comprise different releases of Oracle Database, and all supported releases of Oracle Database can participate in the distributed database system. However, the applications that work with a distributed database must also be able to interoperate with the features and functions that are available at each node in the system.

Interoperability across disparate operating systems and operating system versions can cause problems (especially during rolling upgrades) because the minimum requirements for the new Oracle Database release may require you to upgrade the operating systems on some or all of your hosts. For this reason, before you start an Oracle Database upgrade, you must check to ensure that drivers, network, and storage are compatible for all the interim upgrade states of the system during the rolling upgrade.

**Note:**

Because Oracle Database Upgrade Guide discusses upgrading and downgrading between different releases of Oracle Database, the definition of interoperability is for Oracle Database releases. Other Oracle documentation may use a broader definition of the term interoperability. For example, interoperability in some cases can describe communication between different hardware platforms and operating systems.

My Oracle Support note 207303.1 "Client / Server / Interoperability Support Between Different Oracle Versions" provides additional information.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=207303.1>

**Parent topic:** [Compatibility and Interoperability Between Oracle Database Releases](compatibility-interoperability-between-database-releases.md)
