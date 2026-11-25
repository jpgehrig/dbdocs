## Oracle Fleet Patching and Provisioning Clients and Targets

The Oracle Fleet Patching and Provisioning (Oracle FPP) Client is part of Oracle Clusterware. Users operate on an Oracle FPP Client to perform tasks such as requesting deployment of Oracle homes and listing available gold images.

**Note:**

The Oracle FPP Server release must be later than or equal to the Oracle FPP Client software release, including the Release Update (RU). For example, if Oracle FPP Server is 23.4, the Oracle FPP Client must also be 23.4.

When a user requests an Oracle home specifying a gold image, the Oracle FPP Client communicates with the Oracle FPP Server to pass on the request. The Oracle FPP Server processes the request by instantiating a working copy of the gold image and making it available to the Oracle FPP Client using Oracle ACFS or a different local file system.

Oracle FPP Client has Oracle Clusterware and the additional `rhpclient` component enabled. This additional `rhpclient` component enables the Oracle FPP Client to initiate the tasks.

The Oracle FPP Client:

- Provides a list of available homes from the Oracle FPP Server.

- Has full functionality in Oracle Clusterware 12c release 2 (12.2) and can communicate with Oracle FPP Servers from Oracle Clusterware 12c release 2 (12.2), or later.

### Oracle Fleet Patching and Provisioning Targets

Computers of which Oracle Fleet Patching and Provisioning (Oracle FPP) is aware are known as `rhpclient`-less targets, which do not have the `rhpclient` component enabled.

Oracle FPP Servers can create new `rhpclient`-less targets, and can also install and configure Oracle Grid Infrastructure on such targets with only an operating system installed. Subsequently, Oracle FPP Server can provision database and other software on those `rhpclient`-less targets, perform maintenance, scale the cluster, in addition to many other operations. All Oracle FPP commands are run on the Oracle FPP Server.

`rhpclient`-less targets running the Oracle FPP Client in Oracle Clusterware 12c release 2 (12.2), and later, may also run many of the Oracle FPP commands to request new software from the Oracle FPP Server and initiate maintenance themselves, among other tasks.

**Note:**

The Oracle FPP Server communicates with Oracle Grid Infrastructure Clusters at version 12.2.0.1 and later through an Oracle FPP Client that can be configured and started up on the destination cluster. The Oracle FPP Client is not supported for `rhpclient`-less targets on Oracle Grid Infrastructure version 12.1 and earlier, on all versions of Oracle Restart and database standalone `rhpclient`-less targets, such as database homes without an Oracle Grid Infrastructure home.

**Related Topics**

- [Creating a Fleet Patching and Provisioning Client](creating-oracle-fpp-client.md)

**Parent topic:** [Fleet Patching and Provisioning Architecture](oracle-fpp-architecture.md)
