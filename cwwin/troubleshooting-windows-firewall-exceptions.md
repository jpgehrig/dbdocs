## Troubleshooting Windows Firewall Exceptions

If you cannot establish certain connections even after granting exceptions to the executable files, then follow these steps to troubleshoot the installation.

1.  Examine Oracle configuration files (such as `*.conf` files), the Oracle key in the Windows registry, and network configuration files in `%ORACLE_HOME%\network\admin`.
2.  Grant an exception in the Windows Firewall to any executable listed in `%ORACLE_HOME%\network\admin\listener.ora` in a `PROGRAM=` clause.
    Each of these executables must be granted an exception in the Windows Firewall because a connection can be made through the TNS listener to that executable.
3.  Examine Oracle trace files, log files, and other sources of diagnostic information for details on failed connection attempts.
    Log and trace files on the database client computer may contain useful error codes or troubleshooting information for failed connection attempts. The Windows Firewall log file on the server may contain useful information as well.
4.  If the preceding troubleshooting steps do not resolve a specific configuration issue on Windows, then provide the output from the following command to Oracle Support for diagnosis and problem resolution:
        netsh firewall show state verbose=enable

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
