You can install Oracle Grid Infrastructure as Oracle Standalone Cluster, Oracle Domain Services Cluster, or Oracle Member Cluster.

Starting with Oracle Grid Infrastructure 12c Release 2 (12.2), the installation media is replaced with a zip file for the Oracle Grid Infrastructure installer. Run the installation wizard after extracting the zip file into the target home path.

At any time during installation, if you have a question about what you are being asked to do, or what input you are required to provide during installation, click the Help button on the installer window.

You should have your network information, storage information, and operating system users and groups available to you before you start installation, and you should be prepared to run root scripts. For Oracle Member Cluster installations, ensure that you have created a Member Cluster Manifest File as explained in this guide.

As the user that owns the software for Oracle Grid Infrastructure for a cluster (`grid`) on the first node, install Oracle Grid Infrastructure for a cluster. Note that the installer uses Secure Shell (SSH) to copy the binary files from this node to the other nodes during the installation. During installation, in the Cluster Node Information window, when you specify the nodes in your cluster, you can click SSH Connectivity and the installer configures SSH connectivity between the specified nodes for you.

**Note:**

These installation instructions assume you do not already have any Oracle software installed on your system.

**Parent topic:** [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-new-cluster.md)
