The `orabasetab` file is used to define fundamental directories based on \$ORACLE_HOME, ORACLE_BASE, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG.

The `orabasetab` file resides in `ORACLE_HOME/install/orabasetab`. To determine if an ORACLE_HOME is read-only or read/write, you can check for the presence of the `orabasetab` file. The `orabasetab` file also defines the ORACLE_BASE and the HOME_NAME of the Oracle home. HOME_NAME is the internal name for ORACLE_HOME.

The last line in the `orabasetab` file, which starts with \$ORACLE_HOME, defines the directories for \$ORACLE_HOME. The last line consists of four fields, each separate by a colon delimiter`(:).`

1.  The first field matches the current \$ORACLE_HOME.

2.  The second field defines the ORACLE_BASE for the current ORACLE_HOME.

3.  The third field defines the HOME_NAME which is used in constructing the ORACLE_BASE_HOME path in a read-only ORACLE_HOME.

4.  The fourth field displays `N` in a read/write ORACLE_HOME and `Y` in a read-only ORACLE_HOME.

In a read-only ORACLE_HOME, the ORACLE_BASE_HOME path is `ORACLE_BASE/homes/HOME_NAME` and ORACLE_BASE_CONFIG is the same as ORACLE_BASE.

In a read/write ORACLE_HOME, ORACLE_HOME, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG are all the same.

### Viewing an orabasetab File

1.  Log in as the Oracle installation owner user account (`oracle`).

2.  Go to the `$ORACLE_HOME/install` directory.

        $ cd /u01/app/oracle/product/19.0.0/dbhome_1/install

3.  View the contents of the `orabasetab` file.

        $ cat orabasetab
        /u01/app/oracle/product/19.0.0/dbhome_1:/u01/app/oracle:OraDB19Home1:Y:

    In this example, a `Y` in the fourth field at the end of the line indicates you have a read-only Oracle home.

**Parent topic:** [Evolution of Oracle Homes](understanding-read-only-oracle-homes.md)
