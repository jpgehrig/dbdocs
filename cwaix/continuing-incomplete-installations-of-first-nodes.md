Review this information to continue an incomplete installation of Oracle Grid Infrastructure, if installation fails on the first node.

1.  If the root script failure indicated a need to reboot, through the message `CLSRSC-400`, then reboot the first node (the node where the installation was started). Otherwise, manually fix or clear the error condition, as reported in the error output.

2.  If necessary, log in as `root` to the first node. Run the `orainstRoot.sh` script on that node again. For example:

        $ sudo -s
        [root@node1]# cd /u01/app/oraInventory
        [root@node1]# ./orainstRoot.sh

3.  Change directory to the Grid home on the first node, and run the `root` script on that node again. For example:

        [root@node1]# cd /u01/app/19.0.0/grid
        [root@node1]# ./root.sh

4.  Complete the installation on all other nodes.

5.  Configure a response file, and provide passwords for the installation.

6.  To complete the installation, log in as the Grid installation owner, and run `gridSetup.sh`, located in the Oracle Grid Infrastructure home, specifying the response file that you created. For example, where the response file is `gridinstall.rsp`:

        [grid@node1]$ /u01/app/19.0.0/grid/gridSetup.sh -executeConfigTools -responseFile /u01/app/19.0.0/grid/install/response/gridinstall.rsp

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
