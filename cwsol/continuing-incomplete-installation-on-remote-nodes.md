Review this information to continue incomplete installation on remote nodes.

1.  If the root script failure indicated a need to reboot, through the message `CLSRSC-400`, then reboot the affected node. Otherwise, manually fix or clear the error condition, as reported in the error output.

2.  If root automation is being used, click Retry on the OUI instance on the first node.

3.  If root automation is not being used, follow these steps:

    1.  Log into the affected node as `root`, and run the `orainstRoot.sh` script on that node. For example:

            $ sudo -s
            [root@node6]# cd /u01/app/oraInventory
            [root@node6]# ./orainstRoot.sh

    2.  Change directory to the Grid home, and run the `root.sh` script on the affected node. For example:

            [root@node6]# cd /u01/app/19.0.0/grid
            [root@node6]# ./root.sh

4.  Continue the installation from the OUI instance on the first node.

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
