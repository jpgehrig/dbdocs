## Continuing Incomplete Installations on First Nodes

To continue an incomplete installation, the first node must finish before the rest of the clustered nodes.

1.  If the OUI failure indicated a need to reboot, by raising error message CLSRSC-400, then reboot the first node (the node where the installation was started). Otherwise, manually fix or clear the error condition that was reported in the error output.
2.  If necessary, log in as the Oracle Installation user for Oracle Grid Infrastructure. Change directory to the Grid home on the first node and run the `gridconfig.bat` command on that node again.
    For example:
        C:\> cd app\19.0.0\grid\crs\config\
        C:\..\config> gridconfig.bat
3.  Complete the installation on all other nodes.
4.  Configure a response file, and provide passwords for the installation.
5.  To complete the installation, log in as the Oracle Installation user for Oracle Grid Infrastructure, and run the following command:
    `setup.exe --executeConfigTools -responseFile ``CRS_home``/install/response/gridinstall.rsp`
    For example, if the response file is named `gridinstall.rsp`:
        C:\> cd app\19.0.0\grid\
        setup.exe --executeConfigTools -gridinstall.rsp CRS_home/install/response/gridinstall.rsp

**Related Topics**

- [Postinstallation Configuration Using the ConfigToolAllCommands Script](postinstall-config-using-configtoolallcommands-script.md)

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
