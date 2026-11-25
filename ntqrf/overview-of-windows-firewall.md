All newer Windows operating systems, by default enable the Windows Firewall to block virtually all TCP network ports to the incoming connections.

As a result, any Oracle products that listen for incoming connections on a TCP port do not receive any of those connection requests, and the clients making those connections report errors.

Depending upon which Oracle products are installed and how they are used, the products require some postinstallation configuration of the Windows Firewall to function on these operating systems.

- [About Oracle Executables Requiring Windows Firewall Exceptions](about-oracle-executables-requiring-windows-firewall-exceptions.md)
  If the Oracle Database executables are in use and accepting connections from a remote client computer, then Oracle recommends that you add them to the Windows Firewall exceptions list to ensure correct operation.
- [Configuring the Windows Firewall](configuring-the-windows-firewall-postinstallation.md)
  Oracle recommends configuring the Windows Firewall if the following conditions are true.
- [Troubleshooting Windows Firewall Exceptions](troubleshooting-windows-firewall-exceptions.md)
  Perform the following steps to troubleshoot Windows Firewall exceptions.

**Parent topic:** [Postinstallation Configuration Tasks on Windows](postinstallation-configuration-tasks-on-windows.md)
