Perform the steps to enable Hybrid Columnar Compression (HCC) on Direct NFS Client.

1.  Ensure that SNMP is enabled on the ZFS storage server. For example:
        # snmpinfo -m get -c public -v -h server_name 1.3.6.1.4.1.42.2.225.1.4.2.0
        enterprises.42.2.225.1.4.2.0 = 53:75:6e:20:53:74:6f:72:61:67:65:20:37:34:31:30

    The above sequence of bytes `53:75:6e:....:31:30` is an ascii character representation for Sun Storage 7410.
2.  If SNMP is enabled on an interface other than the NFS server, then configure `oranfstab` using the management parameter.
3.  If SNMP is configured using a community string other than public, then configure `oranfstab` file using the community parameter.
4.   Ensure that `libnetsnmp.so` is installed. If `libnetsnmp.so` is not installed, download and install it from the following URL:
    <https://oss.oracle.com/netsnmp/>

**Note:**

On IBM AIX on POWER Systems (64-bit), HCC is not supported for block based devices.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
