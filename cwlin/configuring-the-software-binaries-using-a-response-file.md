## Configuring the Software Binaries Using a Response File

When you install or copy Oracle Grid Infrastructure software on any node, you can defer configuration for a later time. Review this procedure for completing configuration after the software is installed or copied on nodes, using the configuration wizard (`gridSetup.sh`).

To configure the Oracle Grid Infrastructure software binaries using a response file:

1.  As the Oracle Grid Infrastructure installation owner (`grid`), start Oracle Universal Installer in Oracle Grid Infrastructure configuration wizard mode from the Oracle Grid Infrastructure software-only home using the following syntax, where filename is the response file name:

        /u01/app/19.0.0/grid/gridSetup.sh [-debug] [-silent -responseFile filename]

    For example:

        $ cd /u01/app/19.0.0/grid
        $ ./gridSetup.sh -responseFile /u01/app/grid/response/response_file.rsp

2.  When you complete configuring values, OUI shows you the Summary page, listing all information you have provided for the cluster. Verify that the summary has the correct information for your cluster, and click Install to start configuration of the local node.

    When configuration of the local node is complete, OUI copies the Oracle Grid Infrastructure configuration file to other cluster member nodes.

3.  When prompted, run root scripts.

4.  When you confirm that all root scripts are run, OUI checks the cluster configuration status, and starts other configuration tools as needed.

**Parent topic:** [Installing Only the Oracle Grid Infrastructure Software](installing-only-the-oracle-grid-infrastructure-software.md)
