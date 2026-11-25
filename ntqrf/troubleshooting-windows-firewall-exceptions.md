Perform the following steps to troubleshoot Windows Firewall exceptions.

Perform the following steps to troubleshoot Windows Firewall exceptions:

1.  Examine Oracle configuration files (such as `*.conf` files), the Oracle key in the Windows registry, and network configuration files in `ORACLE_HOME``\network\admin`.
2.  Pay particular attention to any executable listed in `ORACLE_HOME``\network\admin\listener.ora` in a `PROGRAM=` clause. Each of these must be granted an exception in the Windows Firewall, because a connection can be made through the TNS Listener to that executable.
3.  Examine Oracle trace files, log files, and other sources of diagnostic information for details on failed connection attempts. Log and trace files on the database client computer might contain useful error codes or troubleshooting information for failed connection attempts. The Windows Firewall log file on the server might contain useful information as well.
4.  If the preceding troubleshooting steps do not resolve a specific configuration issue, then provide the output from command `netsh firewall show state verbose=enable` to My Oracle Support for diagnosis and problem resolution at:
    [`https://support.oracle.com/`](https://support.oracle.com/)

**Parent topic:** [Overview of Windows Firewall](overview-of-windows-firewall.md)
