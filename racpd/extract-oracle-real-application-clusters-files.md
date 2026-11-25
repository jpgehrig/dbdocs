## Extract the Oracle Real Application Clusters Files

To prepare for installation, log in to `racnode1` as the Oracle Software Owner account (`oracle`), and extract the software.

1.  From the client, use SSH to log in to the Oracle RAC Container (`racnode1`) as the `oracle` user:

        # ssh -X oracle@10.0.20.150

2.  When prompted for a password, provide the `oracle` user password, and then export the display inside the `racnode1` container to the client, where `display_computer` is the client system, and `port` is the port for the display:

        $ export DISPLAY=display_computer:port

3.  Unzip the Oracle Database files with the following commands:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ unzip -q /software/stage/LINUX.X64_193000_db_home.zip

4.  As the Oracle user, unzip the new Opatch version in the Oracle Database (Oracle home) to replace the existing one. For example, where `OPATCH-patch-zip-file` is the Opatch zip file:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ mv OPatch Opatch_19.3
        $ unzip -q /software/stage/OPATCH-patch-zip-file

    For example, for the OPatch 12.2.0.1.32 for DB 19.0.0.0.0 (Jul 2022) Product Oracle Global Lifecycle Management OPatch utility:

        $ cd /u01/app/oracle/product/19c/dbhome_1
        $ mv Opatch Opatch_19.3
        $ unzip -q /software/stage/p6880880_190000_Linux-x86-64.zip

    After you unzip the OPatch zip file, you can remove the `OPatch_19.3` directory.

**Parent topic:** [Run the Oracle RAC Database Installer](run-oracle-rac-database-installer.md)
