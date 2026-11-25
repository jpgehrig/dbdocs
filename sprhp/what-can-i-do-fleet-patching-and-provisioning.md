Understand how you can get started and use Fleet Patching and Provisioning in your standard deployment.

### How Do I Get Started with Fleet Patching and Provisioning?

You must create and configure a Fleet Patching and Provisioning Server where you can create and store gold images of Oracle Database, Oracle Grid Infrastructure, and other software homes. For detailed steps on creating an Fleet Patching and Provisioning Server see My Oracle Support Note 2097026.1.

<https://support.oracle.com/rs?type=doc&id=2097026.1>

To set up the Fleet Patching and Provisioning Server, ensure that your hardware meets the requirements described in My Oracle Support Note 2126710.1 available at:

<https://support.oracle.com/rs?type=doc&id=2126710.1>

### How can I Use Fleet Patching and Provisioning in my Standard Operating Environment?

Review these topics for step-by-step procedures to provision, patch, and upgrade your software using Fleet Patching and Provisioning.

| Task                                                                  | Description                                                                                                                                                                                                                  |
|:----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create an Oracle Grid Infrastructure 12c Release 2 Deployment         | Provision and configure Oracle Grid Infrastructure software on two nodes that do not currently have a Grid home, and then configure Oracle Grid Infrastructure to form a multi-node Oracle Grid Infrastructure installation. |
| Provision Oracle Database Home Software and Create a Database         | Provision Oracle Database 12c release 2 (12.2) software and create Oracle Database instances.                                                                                                                                |
| Upgrade to Oracle Grid Infrastructure 12c Release 2                   | Upgrade your Oracle Grid Infrastructure cluster from 11g release 2 (11.2.0.4) to 12c release 2 (12.2) with two Fleet Patching and Provisioning commands.                                                                     |
| Patch Oracle Grid Infrastructure without changing your Grid Home Path | Use Fleet Patching and Provisioning to enable Oracle Layered File System (OLFS) for a single Oracle home for change management.                                                                                              |
| Patch Oracle Grid Infrastructure and Oracle Databases Simultaneously  | Patch Oracle Grid Infrastructure and Oracle Databases on the cluster to the latest patch level without cluster downtime.                                                                                                     |
| Patch Oracle Database 12c Release 1 Without Downtime                  | Patch Oracle Database 12c release 1 (12.1) with the latest patching without bringing down the database.                                                                                                                      |
| Upgrade to Oracle Database 12c Release 2                              | Upgrade an Oracle Database from 11.2 to 12c release 2 with a single command, using Fleet Patching and Provisioning, both for managed and unmanaged Oracle homes.                                                             |
| Add a Node to a Cluster and Scale an Oracle RAC Database to the Node  | To your two-node cluster, add a new node, and extend an Oracle RAC Database to the new node, using Fleet Patching and Provisioning.                                                                                          |
| Create a Fleet Patching and Provisioning Image                        | Create gold images of software home and store them on the Fleet Patching and Provisioning Server, to use later for creating working copies.                                                                                  |
| Create a User Action to Deploy an Apache Web Server                   | You can install and configure any type of software using Fleet Patching and Provisioning user actions. Review this procedure to automate deployment of Apache Web Server using Fleet Patching and Provisioning.              |

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
