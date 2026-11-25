## Installing Oracle Instant Client Using Zip Files

Learn how to download and use zip files to install Oracle Instant Client on Linux x86-64 and Linux for Arm (aarch64) platforms.

1.  Go to the Oracle Instant Client Downloads page:
    <https://www.oracle.com/database/technologies/instant-client/downloads.html>
2.  Download the desired Oracle Instant Client zip file. Select the correct platform, architecture, and packages of your choice. For example, if your application is 64-bit, then ensure that you select 64-bit Instant Client and download the Basic Package zip file.
3.  Unzip each zip file into a single directory such as `/opt/oracle/instantclient_19_27` that is accessible to your application.
    For example, for Linux x86-64:

        $ cd /opt/oracle
        $ unzip instantclient-basic-linux.x64-19.27.0.0.0dbru.zip

    For example, for Oracle Linux 8 on Linux for Arm (aarch64):

        $ cd /opt/oracle
        $ unzip instantclient-basic-linux.arm64-19.27.0.0.0dbru.zip

    The various packages unzip into `/opt/oracle/instantclient_19_27`.
4.  Install the operating system `libaio` package. This is available as `libaio1` on some Linux distributions. For example, on Oracle Linux run:
        $ sudo yum install libaio
5.  If Oracle Instant Client is the only Oracle software installed on your system, then update the runtime link path, for example:
        $ sudo sh -c "echo /opt/oracle/instantclient_19_27 > \
              /etc/ld.so.conf.d/oracle-instantclient.conf"
          $ sudo ldconfig

    Alternatively, set the LD_LIBRARY_PATH environment variable prior to running applications. For example:

        $ export LD_LIBRARY_PATH=/opt/oracle/instantclient_19_27:$LD_LIBRARY_PATH

    Optionally, add the variable to configuration files such as `~/.bash_profile` and to application configuration files such as `/etc/sysconfig/httpd`.
6.  If you intend to colocate optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Oracle Instant Client, then move these files to the `network/admin` subdirectory.
    This is the default Oracle configuration directory for applications linked with this Oracle Instant Client.
    Alternatively, you can move the Oracle configuration files to another, accessible directory. Then set the environment variable TNS_ADMIN to that directory name.
7.  To use binaries such as `sqlplus` from the SQL\*Plus package, unzip the package to the same directory as the Basic package and then update your PATH environment variable. For example:
        $ export PATH=/opt/oracle/instantclient_19_27:$PATH
8.  Start your application.

**Parent topic:** [Installing Oracle Instant Client Packages](instant-client-install-linux.md)
