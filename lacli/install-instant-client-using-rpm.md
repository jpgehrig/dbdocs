## Installing Oracle Instant Client Using RPMs

Learn how to install Oracle Instant Client on Linux x86-64 and Linux for Arm (aarch64) platforms by downloading the RPMs using the `dnf install` or the `yum install` command.

**Note:**

Starting with 19c, by default, you can install only one version of the Oracle Instant Client RPM packages at a time. If you need multiple versions, use the Oracle Instant Client zip files.

### Installing Oracle Instant Client From the yum Server

If you are using Oracle Linux and have configured your Oracle Linux `yum` server, then you can install Oracle Instant Client using the `yum install` command for Oracle Linux 7 and `dnf install` for Oracle Linux 8 and Oracle Linux 9.

1.  Install the Oracle Linux release package to configure repository definitions for Oracle Instant Client:

    For Oracle Linux 9:

        $ sudo dnf install oracle-release-el9

    For Oracle Linux 8:

        $ sudo dnf install oracle-release-el8

    For Oracle Linux 7:

        $ sudo yum install oracle-release-el7

2.  Go to the Oracle Instant Client repositories to view available Oracle Instant Client packages:

    For Oracle Linux 9 on Linux x86-64:

    <https://yum.oracle.com/repo/OracleLinux/OL9/oracle/instantclient/x86_64/index.html>

    For Oracle Linux 8 on Linux x86-64:

    <https://yum.oracle.com/repo/OracleLinux/OL8/oracle/instantclient/x86_64/index.html>

    For Oracle Linux 7 on Linux x86-64:

    <https://yum.oracle.com/repo/OracleLinux/OL7/oracle/instantclient/x86_64/index.html>

    For Oracle Linux 8 on Linux for Arm (aarch64):

    <https://yum.oracle.com/repo/OracleLinux/OL8/oracle/instantclient/aarch64/index.html>

    For Oracle Linux 7 on Linux for Arm (aarch64):

    <https://yum.oracle.com/repo/OracleLinux/OL7/oracle/instantclient/aarch64/index.html>

    All installations require a Basic or Basic Light package. All other packages are optional.

3.  Install Oracle Instant Client using `yum` for Oracle Linux 7 and `dnf` for Oracle Linux 8 and Oracle Linux 9. For example:

    For Oracle Linux 8 and Oracle Linux 9 on Linux x86-64 and Linux for Arm (aarch64):

        $ sudo dnf install oracle-instantclient19.27-basic

    For Oracle Linux 7 on Linux x86-64:

        $ sudo yum install oracle-instantclient19.27-basic

    For Oracle Linux 7 on Linux for Arm (aarch64):

        $ sudo yum install oracle-instantclient19.10-basic

4.  To install other Oracle Instant Client packages like SQL\*Plus, run:

    For Oracle Linux 8 and Oracle Linux 9 on Linux x86-64 and Linux for Arm (aarch64):

        $ sudo dnf install oracle-instantclient19.27-sqlplus

    For Oracle Linux 7 on Linux x86-64:

        $ sudo yum install oracle-instantclient19.27-sqlplus

    For Oracle Linux 7 on Linux for Arm (aarch64):

        $ sudo yum install oracle-instantclient19.10-sqlplus

### Manually Downloading and Installing Oracle Instant Client RPM Packages

An alternative to installing Oracle Instant Client is to manually download and install the Oracle Instant Client packages.

1.  Go to the Oracle Instant Client Downloads page:

    <https://www.oracle.com/database/technologies/instant-client/downloads.html>

2.  Download the desired Oracle Instant Client RPM package. Select the correct platform, architecture, and packages of your choice. For example, if your application is 64-bit, then ensure that you select 64-bit Instant Client and download the Basic Package RPM file.

3.  Install the packages using `yum` for Oracle Linux 7 and `dnf` for Oracle Linux 8 and Oracle Linux 9. For example:

    For Oracle Linux 8 and Oracle Linux 9 on Linux x86-64:

        $ sudo dnf install oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm

    For Oracle Linux 7 on Linux x86-64:

        $ sudo yum install oracle-instantclient19.27-basic-19.27.0.0.0-1.x86_64.rpm

    For Oracle Linux 8 on Linux for Arm (aarch64):

        $ sudo dnf install oracle-instantclient19.27-basic-19.27.0.0.0-1.aarch64.rpm

    For Oracle Linux 7 on Linux for Arm (aarch64):

        $ sudo yum install oracle-instantclient19.10-basic-19.10.0.0.0-1.aarch64.rpm

Additionally, you may have to perform the following tasks before you start your application:

- If you intend to colocate optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Oracle Instant Client, then move these files to the `/usr/lib/oracle/19.27/client64/lib/network/admin` or `/usr/lib/oracle/19.10/client64/lib/network/admin` subdirectory.

  This is the default Oracle configuration directory for applications linked with this Oracle Instant Client.

  Alternatively, you can move the Oracle configuration files to another, accessible directory. Then set the environment variable TNS_ADMIN to that directory name.

- To use binaries from the tools package, use `yum` to install the package and then update your PATH environment variable. For example:

  For Oracle Linux 8 and Oracle Linux 9:

      $ export PATH=/usr/lib/oracle/19.27/client64/bin:$PATH

  For Oracle Linux 7:

      $ export PATH=/usr/lib/oracle/19.10/client64/bin:$PATH

**Parent topic:** [Installing Oracle Instant Client Packages](instant-client-install-linux.md)
