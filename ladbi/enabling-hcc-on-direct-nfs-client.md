## Enabling Hybrid Columnar Compression on Direct NFS Client

Perform these steps to enable Hybrid Columnar Compression (HCC) on Direct NFS Client:

1.  Ensure that SNMP is enabled on the ZFS storage server. For example:
        $ snmpget -v1 -c public server_name .1.3.6.1.4.1.42.2.225.1.4.2.0
        SNMPv2-SMI::enterprises.42.2.225.1.4.2.0 = STRING: "Sun Storage 7410"
2.  If SNMP is enabled on an interface other than the NFS server, then configure `oranfstab` using the management parameter.
3.  If SNMP is configured using a community string other than public, then configure `oranfstab` file using the community parameter.
4.   Ensure that `libnetsnmp.so` is installed by checking if `snmpget` is available.

**Parent topic:** [Deploying Oracle Direct NFS](deploying-dnfs.md)
