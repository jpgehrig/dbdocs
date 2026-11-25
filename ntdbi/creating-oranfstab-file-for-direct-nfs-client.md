## Creating an oranfstab File for Direct NFS Client

Direct NFS uses a configuration file, `oranfstab`, to determine the available mount points.

Create an `oranfstab` file with the following attributes for each NFS server that you want to access using Direct NFS Client:

- `server`

  The NFS server name.

  For NFS setup with Kerberos authentication, the `server` attribute name must be the fully-qualified name of the NFS server. This `server` attribute name is used to create service principal for Ticket Granting Service (TGS) request from the Kerberos server. If you are configuring external storage snapshot cloning, then the NFS `server` name should be a valid host name. For all other scenarios, the NFS `server` name can be any unique name.

- `local`

  Up to four paths on the database host, specified by IP address or by name, as displayed using the `ipconfig` command run on the database host.

- `path`

  Up to four network paths to the NFS server, specified either by IP address, or by name, as displayed using the `ipconfig` command on the NFS server.

- `export`

  The exported path from the NFS server. Use UNIX-style path.

- `mount`

  The corresponding local mount point for the exported volume. Use WINDOWS-style path.

- `Dontroute`

  Specifies that the outgoing messages must not be routed by the operating system, but sent using the IP address to which they are bound.

- `mnt_timeout`

  Specifies (in seconds) the time Direct NFS Client should wait for a successful mount before timing out. This parameter is optional. The default timeout is 10 minutes (600).

- `uid (Optional)`

  The UNIX user ID to be used by Direct NFS Client to access all NFS servers listed in `oranfstab`. The default value is `uid:65534`, which corresponds to `user:nobody` on the NFS server.

- `gid (Optional)`

  The UNIX group ID to be used by Direct NFS Client to access all the NFS servers listed in `oranfstab`. The default value is `gid:65534`, which corresponds to `group:nogroup` on the NFS server.

- `nfs_version`

  Specifies the NFS protocol version used by Direct NFS Client. Acceptable values are nfsv3, nfsv4, nfsv4.1, and pnfs. The default version is nfsv3. If you select nfsv4.x, then you must configure the value in `oranfstab` for `nfs_version`.

- `security_default (Optional) `

  Specifies the default security mode applicable for all the exported NFS server paths for a server entry. The default value is `sys` . See the description of the security parameter for the supported security levels for the security_default parameter.

- `security (Optional) `

  Specifies the security level, to enable security using Kerberos authentication protocol with Direct NFS Client. Specify `security` per export-mount pair. The supported security levels for the security_default and security parameters are:

  - `sys`: UNIX level security AUTH_UNIX authentication based on user identifier (UID) and group identifier (GID) values. This is the default value for security parameters.
  - `krb5`: Direct NFS runs with plain Kerberos authentication. Server is authenticated as the real server which it claims to be.
  - `krb5i`: Direct NFS runs with Kerberos authentication and NFS integrity. Server is authenticated and each of the message transfers is checked for integrity.
  - `krb5p`: Direct NFS runs with Kerberos authentication and NFS privacy. Server is authenticated, and all data is completely encrypted.

  The security parameter, if specified, takes precedence over the security_default parameter. If neither of these parameters are specified, then sys is the default authentication.

  For NFS server Kerberos security setup, review the relevant NFS server documentation. For Kerberos client setup, review the relevant operating system documentation.

- `management`

  Enables Direct NFS Client to use the management interface for SNMP queries. You can use this parameter if SNMP is running on separate management interfaces on the NFS server. The default value is the server parameter value.

- `community`

  Specifies the community string for use in SNMP queries. Default value is `public`.

The following examples show three possible NFS server entries in `oranfstab`. A single `oranfstab` can have multiple NFS server entries.

Example 5-1 Using Local and Path NFS Server Entries

The following example uses both local and path. Because they are in different subnets, you do not have to specify `dontroute`.

    server: MyDataServer1
    local: 192.0.2.0
    path: 192.0.2.1
    local: 192.0.100.0
    path: 192.0.100.1
    export: /vol/oradata1 mount: C:\APP\ORACLE\ORADATA\ORCL

Example 5-2 Using Names in Place of IP Addresses, with Multiple Exports, management and community

    server: MyDataServer2
    local: LocalPath1
    path: NfsPath1
    local: LocalPath2
    path: NfsPath2
    local: LocalPath3
    path: NfsPath3
    local: LocalPath4
    path: NfsPath4
    nfs_version: nfsv3
    dontroute
    export: /vol/oradata2 mount: C:\APP\ORACLE\ORADATA\ORCL2
    export: /vol/oradata3 mount: C:\APP\ORACLE\ORADATA\ORCL3
    export: /vol/oradata4 mount: C:\APP\ORACLE\ORADATA\ORCL4
    export: /vol/oradata5 mount: C:\APP\ORACLE\ORADATA\ORCL5
    management: MgmtPath1
    community: private

Example 5-3 Using Kerberos Authentication with Direct NFS Export

The `security` parameter overrides `security_default`:

    server:  nfsserver
     local: 192.0.2.0
     path: 192.0.2.2
     local: 192.0.2.3
     path: 192.0.2.4
     export: /vol/oradata2 mount: C:\APP\ORACLE\ORADATA\ORCL2 security: krb5
     export: /vol/oradata3 mount: C:\APP\ORACLE\ORADATA\ORCL3 security: krb5p
     export: /vol/oradata3 mount: C:\APP\ORACLE\ORADATA\ORCL4 security: sys
     export: /vol/oradata3 mount: C:\APP\ORACLE\ORADATA\ORCL5
    security_default: krb5i

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
