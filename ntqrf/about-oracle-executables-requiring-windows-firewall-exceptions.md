If the Oracle Database executables are in use and accepting connections from a remote client computer, then Oracle recommends that you add them to the Windows Firewall exceptions list to ensure correct operation.

Except as noted, these Oracle executables can be found in the `ORACLE_HOME``\bin` directory.

**Note:**

If multiple Oracle homes are in use, then you need several firewall exceptions for the same executable: one for each home from which that executable loads.

- [Configuring Windows Firewall Exceptions for Successful Connections to Oracle Software](configuring-windows-firewall-exceptions-for-successful-connections-to-oracle-software.md)
  Learn about configuring Windows Firewall exceptions.
- [Overview of Different Executables Added to the Windows Firewall Exception List](overview-of-different-executables.md)
  Lists the executables that listen on TCP ports on Windows, along with a brief description of the executable.

**See Also:**

[Oracle Real Application Clusters Installation Guide](../riwin/configure-exceptions-for-the-windows-firewall.md)

**Parent topic:** [Overview of Windows Firewall](overview-of-windows-firewall.md)
