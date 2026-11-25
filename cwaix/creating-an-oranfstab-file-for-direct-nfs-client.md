Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.

Create an `oranfstab` file with the following attributes for each NFS server that you want to access using Direct NFS Client:

- `server`

  The NFS server name.

  For NFS setup with Kerberos authentication, the `server` attribute name must be the fully-qualified name of the NFS server. This `server` attribute name is used to create service principal for Ticket Granting Service (TGS) request from the Kerberos server. If you are configuring external storage snapshot cloning, then the NFS `server` name should be a valid host name. For all other scenarios, the NFS `server` name can be any unique name.

- `local`

  Up to four paths on the database host, specified by IP address or by name, as displayed using the `ifconfig` command run on the database host.

- `path`

  Up to four network paths to the NFS server, specified either by IP address, or by name, as displayed using the `ifconfig` command on the NFS server.

- `export`

  The exported path from the NFS server.

- `mount`

  The corresponding local mount point for the exported volume.

- `mnt_timeout`

  Specifies (in seconds) the time Direct NFS Client should wait for a successful mount before timing out. This parameter is optional. The default timeout is 10 minutes (600).

- `nfs_version`

  Specifies the NFS protocol version used by Direct NFS Client. Possible values are NFSv3, NFSv4, NFSv4.1, and pNFS. The default version is NFSv3. If you select NFSv4.x, then you must configure the value in `oranfstab` for `nfs_version`.

  Specify `nfs_version` as `pNFS`, if you want to use Direct NFS with Parallel NFS. Direct NFS supports only the default `sys` security authentication with Parallel NFS. Direct NFS does not support Parallel NFS when combined with any of the Kerberos authentication parameters.

- `security_default`

  Specifies the default security mode applicable for all the exported NFS server paths for a server entry. This parameter is optional. `sys` is the default value. See the description of the security parameter for the supported security levels for the security_default parameter.

- `security`

  Specifies the security level, to enable security using Kerberos authentication protocol with Direct NFS Client. This optional parameter can be specified per export-mount pair. The supported security levels for the security_default and security parameters are:

  - `sys`: UNIX level security AUTH_UNIX authentication based on user identifier (UID) and group identifier (GID) values. This is the default value for security parameters.
  - `krb5`: Direct NFS runs with plain Kerberos authentication. Server is authenticated as the real server which it claims to be.
  - `krb5i`: Direct NFS runs with Kerberos authentication and NFS integrity. Server is authenticated and each of the message transfers is checked for integrity.
  - `krb5p`: Direct NFS runs with Kerberos authentication and NFS privacy. Server is authenticated, and all data is completely encrypted.

  The security parameter, if specified, takes precedence over the security_default parameter. If neither of these parameters are specified, then sys is the default authentication.

  For NFS server Kerberos security setup, review the relevant NFS server documentation. For Kerberos client setup, review the relevant operating system documentation.

- `dontroute`

  Specifies that outgoing messages should not be routed by the operating system, but instead sent using the IP address to which they are bound.

  **Note:**

  The `dontroute` option is a POSIX option, which sometimes does not work on Linux systems with multiple paths in the same subnet.

- `management`

  Enables Direct NFS Client to use the management interface for SNMP queries. You can use this parameter if SNMP is running on separate management interfaces on the NFS server. The default value is the server parameter value.

- `community`

  Specifies the community string for use in SNMP queries. Default value is `public`.

The following examples show three possible NFS server entries in `oranfstab`. A single `oranfstab` can have multiple NFS server entries.

Example 7-1 Using Local and Path NFS Server Entries

The following example uses both local and path. Because they are in different subnets, you do not have to specify `dontroute`.

    server: MyDataServer1
    local: 192.0.2.0
    path: 192.0.2.1
    local: 192.0.100.0
    path: 192.0.100.1
    export: /vol/oradata1 mount: /mnt/oradata1

Example 7-2 Using Local and Path in the Same Subnet, with dontroute

Local and path in the same subnet, where `dontroute` is specified:

    server: MyDataServer2
    local: 192.0.2.0
    path: 192.0.2.128
    local: 192.0.2.1
    path: 192.0.2.129
    dontroute
    export: /vol/oradata2 mount: /mnt/oradata2

Example 7-3 Using Names in Place of IP Addresses, with Multiple Exports, management and community

    server: MyDataServer3
    local: LocalPath1
    path: NfsPath1
    local: LocalPath2
    path: NfsPath2
    local: LocalPath3
    path: NfsPath3
    local: LocalPath4
    path: NfsPath4
    dontroute
    export: /vol/oradata3 mount: /mnt/oradata3
    export: /vol/oradata4 mount: /mnt/oradata4
    export: /vol/oradata5 mount: /mnt/oradata5
    export: /vol/oradata6 mount: /mnt/oradata6
    management: MgmtPath1
    community: private

Example 7-4 Using Kerberos Authentication with Direct NFS Export

The `security` parameter overrides `security_default`:

    server:  nfsserver
     local: 192.0.2.0
     path: 192.0.2.2
     local: 192.0.2.3
     path: 192.0.2.4
     export: /private/oracle1/logs  mount: /logs  security: krb5
     export: /private/oracle1/data  mount: /data  security: krb5p
     export: /private/oracle1/archive mount: /archive security: sys
     export: /private/oracle1/data1 mount: /data1
     security_default: krb5i

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-for-oracle-grid-infrastructure.md)
