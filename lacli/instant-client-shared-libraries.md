## Instant Client Libraries for OCI

Learn about the Oracle Database client-side files required to deploy Oracle Call Interface (OCI) applications.

Table 6-5 Instant Client Basic Package Shared Libraries for OCI

| File Name                                      | Description                            |
|:-----------------------------------------------|:---------------------------------------|
| `libclntsh.so.19.1`<br>`libclntshcore.so.19.1` | Client code library                    |
| `libociei.so`                                  | OCI Instant Client Data Shared Library |
| `libnnz19.so`                                  | Security Library                       |

Table 6-6 Instant Client Basic Light Package Shared Libraries for OCI

| File Name                                       | Description                            |
|:------------------------------------------------|:---------------------------------------|
| `libclntsh.so.19.1`<br>`libclntshcore.so.19.1 ` | Client code library                    |
| `libociicus.so`                                 | OCI Instant Client Data Shared Library |
| `libnnz19.so`                                   | Security Library                       |

### Guidelines for Basic and Basic Light Packages

- The libraries must reside in the same directory in order to use Oracle Instant Client.
- Other libraries and utilities are available when you install Oracle Instant Client, but are not needed for OCI runtime use. For example, you can delete files such as `liboramysql19.so` and `ojdbc8.jar`.
- In general, all OCI functionality is available to applications run using Oracle Instant Client, except that the Instant Client is for client-side operations only. Therefore, server-side external procedures cannot use Oracle Instant Client libraries.
- OCI applications, by default, look for the OCI Data Shared Library, `libociei.so` in the runtime library search path, for example, in \$LD_LIBRARY_PATH to determine if the application should operate in the Instant Client mode. If the OCI Data Shared Library is not found, then OCI tries to load the Oracle Instant Client Basic Light Data Shared Library `libociicus.so`.

### Guidelines for Running OCI Applications

- If you have multiple directories containing Oracle Client libraries, then only one such directory should be in the operating system library search path.

- If Oracle Instant Client is the only Oracle software installed on your system, then update the runtime link path using `ldconfig`. For example:

  For Oracle Linux 8 and Oracle Linux 9:

      $ sudo sh -c "echo /opt/oracle/instantclient_19_27 > \
          /etc/ld.so.conf.d/oracle-instantclient.conf"
      $ sudo ldconfig

  For Oracle Linux 7:

      $ sudo sh -c "echo /opt/oracle/instantclient_19_10 > \
          /etc/ld.so.conf.d/oracle-instantclient.conf"
      $ sudo ldconfig

  Alternatively, to run OCI applications using Oracle Instant Client, set the operating system library search path, for example LD_LIBRARY_PATH, to the directory with the Oracle Instant Client libraries.

- If an Oracle Database installation or full Oracle Database Client installation exists on the same system, then you should not have `$ORACLE_HOME/lib` and the Oracle Instant Client directory on the operating system library search path simultaneously regardless of the order in which they appear in the operating system library search path. Either the `$ORACLE_HOME/lib` directory (for non-Instant Client operations) or Oracle Instant Client directory (for Oracle Instant Client operations) should be in the operating system library search path variable, but not both.

- If you intend to colocate optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Oracle Instant Client, then move these files to the `network/admin` subdirectory.

**Parent topic:** [Installing Oracle Instant Client](installing-instant-client.md)
