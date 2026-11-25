## Continuing Incomplete Upgrade of First Nodes

When the first node cannot be upgraded, use these steps to continue the upgrade process.

1.  If the OUI failure indicated a need to reboot by raising error message `CLSRSC-400`, then reboot the first node (the node on which you started the upgrade). Otherwise, manually fix or clear the error condition, as reported in the error output.
2.  Log in as an Administrator user on the first node.
3.  Change directory to the new Grid home on the first node, and run the `gridconfig.bat —upgrade` command on that node again. For example:
        C:\> cd app\19.0.0\grid\crs\config\
        C:\..\grid> gridconfig.bat -upgrade
4.  Complete the upgrade of all other nodes in the cluster.
        C:\app\19.0.0\grid\crs\config> gridconfig.bat -upgrade
5.  Configure a response file, and provide passwords required for the upgrade.
6.  To complete the upgrade, log in to the first node as the Oracle Installation user for Oracle Grid Infrastructure and run the script `setup.exe`, located in the `Grid_home`, specifying the response file that you created.
    For example, if the response file is named `gridinstall.rsp`:
        C:\> cd Grid_home\crs\config
        C:\Grid_home> setup.exe -executeConfigTools -responseFile Grid_home\install\response\gridinstall.rsp

    **Note:**

    When you reupgrade Oracle Grid Infrastructure, you must use the `-all` flag with the `executeConfigTools` command to run all the configuration tools.

**Related Topics**

- [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstall-config-using-configtoolallcommands-script.md)

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
