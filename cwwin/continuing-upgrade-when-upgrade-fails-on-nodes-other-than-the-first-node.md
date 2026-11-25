## Continuing Incomplete Upgrades on Remote Nodes

For nodes other than the first node (the node on which you started the upgrade), use these steps to continue the upgrade process.

1.  If the OUI failure indicated a need to reboot, by raising error message `CLSRSC-400`, then reboot the node with the error condition. Otherwise, manually fix or clear the error condition that was reported in the error output.
2.  On the first node, within OUI, click Retry.
    This instructs OUI to retry the upgrade on the affected node.
3.  Continue the upgrade from the OUI instance on the first node.

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
