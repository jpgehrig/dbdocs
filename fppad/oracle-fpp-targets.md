## Targets of Oracle Fleet Patching and Provisioning

Computers of which Oracle Fleet Patching and Provisioning (Oracle FPP) is aware are known as `rhpclient`-less targets, which do not have the `rhpclient` component enabled.

Oracle FPP Servers can create new `rhpclient`-less targets, and can also install and configure Oracle Grid Infrastructure on such targets with only an operating system installed. Subsequently, Oracle FPP Server can provision database and other software on those `rhpclient`-less targets, perform maintenance, scale the cluster, in addition to many other operations. All Oracle FPP commands are run on the Oracle FPP Server.

`rhpclient`-less targets running the Oracle FPP Client in Oracle Clusterware 12c release 2 (12.2), and later, may also run many of the Oracle FPP commands to request new software from the Oracle FPP Server and initiate maintenance themselves, among other tasks.

**Note:**

The Oracle FPP Server communicates with Oracle Grid Infrastructure Clusters at version 12.2.0.1 and later through an Oracle FPP Client that can be configured and started up on the destination cluster. The Oracle FPP Client is not supported for `rhpclient`-less targets on Oracle Grid Infrastructure version 12.1 and earlier, on all versions of Oracle Restart and database standalone `rhpclient`-less targets, such as database homes without an Oracle Grid Infrastructure home.

**Parent topic:** [Fleet Patching and Provisioning Architecture](oracle-fpp-architecture.md)
