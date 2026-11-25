Run the `rootpre.sh` script only the first time you install Oracle Database on IBM AIX on POWER Systems (64-Bit).

**Note:**

You do not have to run the `rootpre.sh` script on an IBM AIX on POWER Systems (64-Bit) server that has an Oracle Database software already installed.

Use the following procedure to run the rootpre.sh script:

1.  Download the Oracle Database installation image files (`db_home.zip`) and extract the files into a new Oracle home directory. For example:
        $ mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1
        $ chgrp oinstall /u01/app/oracle/product/19.0.0/dbhome_1
        $ cd /u01/app/oracle/product/19.0.0/dbhome_1
        $ unzip -q /tmp/db_home.zip
2.  Switch the user to `root`:
        $ su - root
        password:
        #
3.  Run the `rootpre.sh` script using the following command:
        # $ORACLE_HOME/clone/rootpre.sh
4.  Exit from the `root` account:
        # exit

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
