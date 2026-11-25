Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later release upgrades use digest authentication.

Oracle recommends that when you configure ports, you also configure the authentication for HTTP for accessing Oracle XML DB Repository to take advantage of improved security features.

Starting with Oracle Database 12c, Oracle enhanced database security by supporting digest authentication. Digest authentication is an industry-standard protocol that is commonly used with the HTTP protocol. It is supported by most HTTP clients. Digest authentication ensures that passwords are always transmitted in a secure manner, even when an encrypted (HTTPS) connection is not in use. Support for digest authentication enables organizations to deploy applications that use Oracle XML DB HTTP, without having to worry about passwords being compromised. Digest authentication support in Oracle XML DB also ensures that the Oracle XML DB HTTP server remains compatible with Microsoft Web Folders WebDAV clients.

After installing or upgrading for the new release, you must manually configure the FTP and HTTP ports for Oracle XML DB as follows:

1.  Use `DBMS_XDB_CONFIG.setHTTPPort(``HTTP_port_number``)` to set the HTTP port for Oracle XML DB:

        SQL> exec DBMS_XDB_CONFIG.setHTTPPort(port_number);

2.  Use `DBMS_XDB_CONFIG.setFTPPort(``FTP_port_number``)` to set the FTP port for Oracle XML DB:

        SQL> exec DBMS_XDB_CONFIG.setFTPPort(FTP_port_number);

    **Note:**

    You can query the port numbers to use for FTP and HTTP in the procedure by using `DBMS_XDB_CONFIG.getFTPPort` and `DBMS_XDB_CONFIG.getHTTPPort` respectively.

3.  To see all the used port numbers, query `DBMS_XDB_CONFIG.usedport`.

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/repository-access-using-protocols.md) for more information about accessing the Oracle XML DB Repository data using FTP, HTTP, HTTPS, and WebDAV protocols

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
