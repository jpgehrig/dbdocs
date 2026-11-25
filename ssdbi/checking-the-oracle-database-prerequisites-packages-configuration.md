Use this procedure to gather information about the Oracle Database prerequisites group package configuration.

1.  To check if `oracle-database-preinstall-19c` is already installed:
        $ pkg list oracle-database-preinstall-19c
2.  To check for the latest version of `oracle-database-preinstall-19c`:
        $ pkg list -n oracle-database-preinstall-19c
3.  Before you install `oracle-database-preinstall-19c`:
    1.  Use the `-n` option to check for errors:
            $ pkg install -n oracle-database-preinstall-19c

        **Note:**

        Use the `-n` option to check for installation errors. If `-n` does not display any errors, then omit the `-n` option when you install `oracle-database-preinstall-19c`.
    2.  If there are no errors, then log in as `root`, and install the group package:
            # pkg install oracle-database-preinstall-19c
    3.  If you have the `oracle` user and other user groups already defined, and do not want to change them:
            # pkg avoid oracle-database-os-configuration
4.  To view what packages will be installed by `oracle-database-preinstall-19c`:
        $ pkg contents -ro type,fmri -t depend oracle-database-preinstall-19c

    A sample output of this command:

        TYPE FMRI
        conditional pkg:/service/oracle-rdbms-stats
        group pkg:/group/prerequisite/oracle/oracle-database-os-configuration
        group pkg:/system/font/truetype/arphic-uming
        group pkg:/system/font/truetype/hanyang-ko-core
        group pkg:/system/header
        group pkg:/system/kernel/oracka
        group pkg:/system/picl
        group pkg:/x11/diagnostic/x11-info-clients
        group pkg:/x11/library/libxi
        group pkg:/x11/library/libxtst
        group pkg:/x11/session/xauth
        require pkg:/compress/unzip
        require pkg:/developer/assembler
        require pkg:/developer/build/make
        require pkg:/system/dtrace
        require pkg:/system/library/openmp

**Related Topics**

- [Adding and Updating Software in Oracle Solaris](http://docs.oracle.com/cd/E36784_01/html/E36802/tspkginstall.html)

**Parent topic:** [Automatically Configuring Oracle Solaris with Oracle Database Prerequisites Packages](automatically-configuring-oracle-solaris-with-oracle-database-prerequisites-packages.md)
