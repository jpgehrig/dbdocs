## Installing Oracle Instant Client Using the Setup Wizard

Use the `runInstaller` command to start the Oracle Instant Client installation.

1.  Log in as the Oracle installation owner user account (`oracle`).
2.  Use any browser to access the Oracle Database Software Downloads page:
    <https://www.oracle.com/database/technologies/oracle-database-software-downloads.html>
3.  Download the Oracle Database Client installation zip file to a directory of your choice. For example, you can download the zip file to the `/tmp` directory.
4.  Extract the client zip file and use the `runInstaller` command to start the installation.
        $ ./runInstaller
5.  In the Select Installation Type screen, select Instant Client. Click Next.
6.  In the Specify Installation Location screen, enter an OFA-compliant Oracle home directory path like `/u01/app/oracle/product/19.0.0/client_1`. Click Next.
7.  Note the information in the Summary screen and click Next.
8.  The Finish screen displays the status of the Oracle Instant Client installation. Click Close to complete the installation and exit the installer.
9.  The Oracle Instant Client shared libraries like `libociei.so`, `libclntsh.so.19.1`, `libclntshcore.so.19.1`, and `libnnz19.so` are available in the Oracle client home directory `/u01/app/oracle/product/19.0.0/client_1`
10. Set the operating system shared library path LD_LIBRARY_PATH environment variable to the Oracle client home directory.
        $ export LD_LIBRARY_PATH=/u01/app/oracle/product/19.0.0/client_1:$LD_LIBRARY_PATH
11. If you intend to colocate optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Oracle Instant Client, then move these files to the `network/admin` subdirectory.
    This is the default Oracle configuration directory for applications linked with this Oracle Instant Client.
    Alternatively, you can move the Oracle configuration files to another, accessible directory. Then set the environment variable TNS_ADMIN to that directory name.
12. To use binaries such as `sqlplus` from the SQL\*Plus package, unzip the package to the same directory as the Basic package and then update your PATH environment variable. For example:
        $ export PATH=/u01/app/oracle/product/19.0.0/client_1:$PATH
13. Start your application.

To remove this Oracle Instant Client installation use the `runInstaller` command along with the `-deinstall -home` options:

    $ ./runInstaller -deinstall -home /u01/app/oracle/product/19.0.0/client_1

**Parent topic:** [Installing Oracle Instant Client Packages](instant-client-install-linux.md)
