## 18 Introducing Network File System (NFS)

NFS protocol is a widely used file system protocol to access storage across network.

**Note:**

Oracle objects exported through OFS server can be accessed by NFS clients by mounting them on the client machines

Topics:

- Prerequisites to Access Storage Through NFS Server

- NFS Security

<!-- -->

- Accessing OFS with an NFS Account
  You can export an OFS mount to a specified list of nodes and NFS mount it on them. This allows users to access the contents of an OFS mount point from a node where the database is not running. The NFS exports may not work in cloud environments due to security reasons, but you can use it in on-premise environments.
- Prerequisites to Access Storage Through NFS Server
- NFS Security

**Parent topic:** [Oracle File System (OFS) Server](oracle-file-system.md)

### 18.1 Accessing OFS with an NFS Account

You can export an OFS mount to a specified list of nodes and NFS mount it on them. This allows users to access the contents of an OFS mount point from a node where the database is not running. The NFS exports may not work in cloud environments due to security reasons, but you can use it in on-premise environments.

NFS v3 is a stateless protocol because of which it encapsulates each `readdir` request between `opendir` and `releasedir` calls. This may lead to poor performance when you want to list directories that have a large number of files. Therefore, OFS maintains a directory cache which persists across the `opendir` and `releasedir` calls. Do not use the `no_rbt_cache` mount option to avoid inconsistent directory cache listing and to utilize the benefits of directory cache.

**Parent topic:** Introducing Network File System (NFS)

### 18.2 Prerequisites to Access Storage Through NFS Server

The prerequisites to access storage through NFS server are as follows:

- DBFS file system must be created before using OFS.

- You should be able to mount the file systems exported by the database.

- NFS server must be configured with `KERNEL` module.

  **Note:**

  The `KERNEL` module is supported through `FUSE` driver for Linux.

**Parent topic:** Introducing Network File System (NFS)

### 18.3 NFS Security

Starting from Oracle Database 12c Release 2 (12.2.0.1), OFS will use the OS authentication model to authorize NFS client users. If the user is accessing a local node (where the Oracle instance is running), the access to each file in the file system is controlled through Unix Access Control List set for each object. On Linux, OFS uses FUSE to receive file system requests from the OS kernel or NFS client. This requires `user_allow_other` parameter to be set in `/etc/fuse.conf` configuration file if an OS user other than the `root` user and oracle user need to access the file system.

**Note:**

Users can also be configured with an Oracle password to log into Oracle client tools like `SQL* Plus` to execute SQL's.

If the network is not secure, the customer is advised to setup Kerberos to authenticate the user using OS NFS.

**Note:**

- The Kerberos authentication is available from NFS version 4 onwards. If the OFS is exported via NFS version 3, the authentication is performed using `AUTH_SYS`.

- For local node, the authentication is performed using `AUTH_SYS` irrespective of how the OFS is exported (NFS version 3 or NFS version 4).

This section contains the following topic:

- About Kerberos

<!-- -->

- About Kerberos
  Kerberos uses encryption technology, Key Distribution Center (KDC), and an arbitrator to perform secure authentication on open networks.
- Configuring Kerberos Server
  To configure a Kerberos Server in a Linux system:

**Parent topic:** Introducing Network File System (NFS)

#### 18.3.1 About Kerberos

Kerberos uses encryption technology, Key Distribution Center (KDC), and an arbitrator to perform secure authentication on open networks.

Kerberos is the widely used security mechanism that provides all three flavors of security:

- Authentication

- Integrity check

- Privacy

Kerberos Infrastructure consists of Kerberos software, secured authentication servers, centralized account and password store, and systems configured to authenticate through the Kerberos protocol. The OS NFS server handles the complete authentication and integrity checks by using kerberos principal name as the user name. Once the authentication is performed, the requests passed to the Oracle kernel are handled based on the user name passed through the VFS I/O request.

**Parent topic:** NFS Security

#### 18.3.2 Configuring Kerberos Server

To configure a Kerberos Server in a Linux system:

1.  Install Kerberos software in the Linux system.

2.  Check if the daemons are running using the following commands.
        # /sbin/chkconfig krb5kdc on
        # /sbin/chkconfig kadmin on

3.  If the daemons are not running use the following commands to start the daemons manually:
        # /etc/rc.d/init.d/krb5kdc start
        # /etc/rc.d/init.d/kadmin start

4.  Add user principal using the `kadmin.local` command.

    Example:
        kadmin.local: addprinc <scott>

**Parent topic:** NFS Security
