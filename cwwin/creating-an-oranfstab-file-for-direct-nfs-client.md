## Creating an oranfstab File for Direct NFS Client

If you use Direct NFS Client, then you must create a configuration file, `oranfstab`, to specify the options, attributes, and parameters that enable Oracle Database to use Direct NFS Client.

Direct NFS Client looks for the mount point entries in `oranfstab`. It uses the first matched entry as the mount point.

1.  Create an `oranfstab` file and specify configurable attributes for each NFS server that the Direct NFS Client accesses.
    For a server:

    The NFS server name.

    For NFS setup with Kerberos authentication, the `server` attribute name must be the fully-qualified name of the NFS server. This `server` attribute name is used to create service principal for Ticket Granting Service (TGS) request from the Kerberos server. If you are configuring external storage snapshot cloning, then the NFS `server` name should be a valid host name. For all other scenarios, the NFS `server` name can be any unique name.

    The mount point specified in the `oranfstab` file represents the local path where the database files would reside normally, as if Direct NFS Client was not used. For example, if the location for the data files is `C:\app\oracle\oradata\orcl` and Direct NFS Client is not used, then specify `C:\app\oracle\oradata\orcl` as NFS virtual mount point in the corresponding `oranfstab` file.
2.  Save the file to the `Oracle_home``\dbs` directory.
    When the `oranfstab` file is placed in `Oracle_home``\dbs`, the entries in the file are specific to a single database.
3.  If you have a nonshared Oracle home, copy the `oranfstab` file to the `Oracle_home``\dbs` directory on all nodes in the cluster.
    All instances that use the shared Oracle home use the same `Oracle_home``\dbs\oranfstab` file.

For a nonshared Oracle home, you must keep the `oranfstab` file synchronized on all the nodes.

**Note:**

- Direct NFS Client ignores a `uid` or `gid` value of 0. The exported path from the NFS server must be accessible for `read/write/execute` by the user with the `uid`, `gid` specified in `oranfstab`. If neither `uid` nor `gid` is listed, then the exported path must be accessible by the user with `uid:65534` and `gid:65534`.

- If you remove an NFS path from `oranfstab`, you must make the change in all `oranfstab` files used by the Oracle RAC database. Then, you must restart the database for the change to be effective. The mount point that you use for the file system must be identical on each node.

The following examples show three possible NFS server entries in `oranfstab`. A single `oranfstab` can have multiple NFS server entries.

Example 8-1 oranfstab File Using Local and Path NFS Server Entries

The following example of an `oranfstab` file shows an NFS server entry, where the NFS server, `MyDataServer1`, uses two network paths specified with IP addresses.

    server: MyDataServer1
    local: 192.0.2.0
    path: 192.0.2.1
    local: 192.0.100.0
    path: 192.0.100.1
    nfs_version: nfsv3
    export: /vol/oradata1 mount: C:\APP\ORACLE\ORADATA\ORADATA1

Example 8-2 oranfstab File Using Network Names in Place of IP Addresses, with Multiple Exports, management and community

The following example of an `oranfstab` file shows an NFS server entry, where the NFS server, `MyDataServer2`, uses four network paths specified by the network interface to use, or the network connection name. Multiple export paths are also used in this example.

    server: MyDataServer2
    local: LocalInterface1
    path: NfsPath1
    local: LocalInterface2
    path: NfsPath2
    local: LocalInterface3
    path: NfsPath3
    local: LocalInterface4
    path: NfsPath4
    nfs_version: nfsv4
    export: /vol/oradata2 mount: C:\APP\ORACLE\ORADATA\ORADATA2
    export: /vol/oradata3 mount: C:\APP\ORACLE\ORADATA\ORADATA3
    management: MgmtPath1
    community: private

Example 8-3 oranfstab File Using Kerberos Authentication with Direct NFS Export

In this example, when specified, the `security` parameter overrides the value of the `security_default` parameter.

    server:  nfsserver
     local: 198.51.100.02
     path: 10.0.0.0
     local: 198.51.100.03
     path: 10.0.0.3
     export: /private/oracle1/logs  mount: C:\APP\ORACLE\ORADATA\logs  security: krb5
     export: /private/oracle1/data  mount: C:\APP\ORACLE\ORADATA\data  security: krb5p
     export: /private/oracle1/archive mount: C:\APP\ORACLE\ORADATA\archive security: sys
     export: /private/oracle1/data1 mount: C:\APP\ORACLE\ORADATA\data1
     security_default: krb5i

**Related Topics**

- [Enabling Direct NFS Client](enabling-direct-nfs-client.md)
- [Configurable Attributes for the oranfstab File](configurable-attributes-for-the-oranfstab-file.md)

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
