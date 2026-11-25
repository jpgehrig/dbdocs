## Continuing Incomplete Upgrade of First Node

Review this information to complete the upgrade, if upgrade of Oracle Grid Infrastructure fails on the first node.

1.  If the root script failure indicated a need to reboot, through the message `CLSRSC-400`, then reboot the first node (the node where the upgrade was started). Otherwise, manually fix or clear the error condition, as reported in the error output.

2.  If necessary, log in as `root` to the first node. Change directory to the new Grid home on the first node, and run the `rootupgrade.sh` script on that node again. For example:

        [root@node1]# cd /u01/app/19.0.0/grid
        [root@node1]# ./rootupgrade.sh

3.  Complete the upgrade of all other nodes in the cluster.

        [root@node2]# ./rootupgrade.sh

4.  Configure a response file, and provide passwords for the installation.

5.  To complete the upgrade, log in as the Grid installation owner, and run `gridSetup.sh`, located in the `Grid_home`, specifying the response file that you created. For example, where the response file is `gridinstall.rsp`:

        [grid@node1]$ /u01/app/19.0.0/grid/gridSetup.sh -executeConfigTools -responseFile
        /u01/app/19.0.0/grid/install/response/gridinstall.rsp

    **Note:**

    When you reupgrade Oracle Grid Infrastructure, you must use the `-all` flag with the `executeConfigTools` command to run all the configuration tools.

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
