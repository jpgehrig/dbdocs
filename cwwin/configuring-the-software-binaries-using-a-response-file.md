## Configuring the Software Binaries Using a Response File

When you install or copy Oracle Grid Infrastructure software on any node, you can defer configuration for a later time using the Grid Setup Wizard utility (`setup.exe`).

Use this procedure to complete configuration after the software is installed or copied on nodes.

1.  As the Oracle Installation user for Oracle Grid Infrastructure (for example, `grid`), start Oracle Universal Installer (OUI) in Oracle Grid Infrastructure Grid Setup Wizard mode from the Oracle Grid Infrastructure software-only home. Use the following syntax, where Grid_home is the Oracle Grid Infrastructure home, and filename is the response file name:
        Grid_home\setup.exe [-debug] [-silent -responseFile filename]

    For example:

        C:\> cd Grid_home
        C:\> setup.exe -responseFile C:\app\19.0.0\grid\response\grid_setup.rsp

    The configuration script starts OUI in Grid Setup Wizard mode. Each page shows the same user interface and performs the same validation checks that OUI normally does. However, instead of running an installation, the Grid Setup Wizard mode validates inputs and configures the installation on all cluster nodes.

    When you complete inputs, OUI shows you the Summary page, listing all inputs you have provided for the cluster.
2.  Verify that the summary has the correct information for your cluster, and click Install to start configuration of the local node.
    When configuration of the local node is complete, OUI copies the Oracle Grid Infrastructure configuration file to other cluster member nodes.
3.  OUI checks the cluster configuration status, and starts other configuration tools as needed.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/installing-software-binaries.md) to configure and activate a software-only Oracle Grid Infrastructure installation for a standalone server

- [Running Postinstallation Configuration Using a Response File](running-postinstallation-configuration-using-response-file.md)

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
