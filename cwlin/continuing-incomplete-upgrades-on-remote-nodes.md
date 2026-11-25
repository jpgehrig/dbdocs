## Continuing Incomplete Upgrades on Remote Nodes

Review this information to continue incomplete upgrade on remote nodes.

1.  If the root script failure indicated a need to reboot, through the message `CLSRSC-400`, then reboot the first node (the node where the upgrade was started). Otherwise, manually fix or clear the error condition, as reported in the error output.

2.  If root automation is being used, click Retry on the OUI instance on the first node.

3.  If root automation is not being used, log into the affected node as `root`. Change directory to the Grid home, and run the `rootupgrade.sh` script on that node. For example:

        [root@node6]# cd /u01/app/19.0.0/grid
        [root@node6]# ./rootupgrade.sh

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
