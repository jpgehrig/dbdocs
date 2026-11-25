## Provisioning Oracle Grid Infrastructure Software

Fleet Patching and Provisioning has several methods to provision and, optionally, configure Oracle Grid Infrastructure and Oracle Restart homes.

Fleet Patching and Provisioning can provision and configure Oracle Grid Infrastructure on one or more nodes that do not currently have a Grid home, and then configure Oracle Grid Infrastructure to form a single-node or multi-node Oracle Grid Infrastructure installation.

Use the `rhpctl add workingcopy` command to install and configure Oracle Grid Infrastructure, and to enable repeatable creation of standardized deployments.

The Fleet Patching and Provisioning Server can also provision an Oracle Grid Infrastructure home to a node or cluster that is currently running Oracle Grid Infrastructure. The currently running Grid home can be a home that Fleet Patching and Provisioning did not provision (an unmanaged home) or a home that Fleet Patching and Provisioning did provision (a managed home).

You can also provision an Oracle Restart to a node in the cluster.

In either case, use the `-softwareonly` parameter of the `rhpctl add workingcopy` command. This provisions but does not activate the new Grid home, so that when you are ready to switch to that new home, you can do so with a single command.

- To inform Fleet Patching and Provisioning the nodes on which to install Oracle Grid Infrastructure, and to configure Oracle Grid Infrastructure, you provide directions in a response file, as in the following example:
      $ rhpctl add workingcopy -workingcopy GI_HOME_11204_WCPY -image GI_HOME_11204 –responsefile /u01/app/rhpinfo/GI_11204_install.rsp
        {authentication_option}

  The preceding command provisions the `GI_HOME_11204_WCPY` working copy based on the `GI_HOME_11204` gold image to a destination server specified in the `GI_11204_install.rsp` response file. In addition to identifying the destination nodes, the response file specifies information about the Oracle Grid Infrastructure configuration, such as Oracle ASM and GNS parameters.
  **Note:**

  The `oracle.install.crs.rootconfig.executeRootScript=``xxx` response file parameter is overridden and always set to `false` for Fleet Patching and Provisioning, regardless of what you specify in the response file.
- To provision an Oracle Grid Infrastructure home to a node or cluster that is currently running Oracle Grid Infrastructure:
      $ rhpctl add workingcopy -workingcopy GI_HOME_12201_PATCHED_WCPY -image GI_HOME_12201_PSU1 –client CLUST_002 -softwareonly

  The preceding command provisions a new working copy based on the `GI_HOME_12201_PSU1` gold image to the Fleet Patching and Provisioning Client (that is running Oracle Grid Infrastructure 12c release 2 (12.2)) named `CLUST_002`. When you provision to an `rhpclient`-less target that is not running Oracle Grid Infrastructure 12c release 2 (12.2) (such as, a node running Oracle Grid Infrastructure 12c release 1 (12.1) or Oracle Grid Infrastructure 11g release 2 (11.2)), use the `-targetnode` parameter instead of `-client`.
- Specify an `rhpclient`-less target node on which you want to provision an Oracle Restart, as follows:
      $ rhpctl add workingcopy -workingcopy SIHA_GI -image goldimage -targetnode remote_node_name -responsefile Oracle_Restart_response_file {authentication_option}

**Related Topics**

- [Authentication Options for Oracle Fleet Patching and Provisioning Operations](authentication-options-for-oracle-fpp.md)

**Parent topic:** [Provisioning Oracle Grid Infrastructure Homes](provisioning-oracle-grid-homes.md)
