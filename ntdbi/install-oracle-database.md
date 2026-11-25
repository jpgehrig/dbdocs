## Installing the Oracle Database Software

This topic explains how to run Oracle Universal Installer to perform most database installations.

**Note:**

- If you plan to use Oracle Restart or Oracle ASM, then you must install Oracle Grid Infrastructure for a standalone server before you install and create the database. Otherwise, you must manually register the database with Oracle Restart.

- You may have to shut down existing Oracle processes before you start the database installation.

- You can install Oracle Database by using the silent or response file installation method, without the GUI. This method is useful to perform multiple installations of Oracle Database.

1.  Login as an `Administrator` user. Follow the Oracle Optimal Flexible Architecture (OFA) recommendations and specify the correct owner, group, and permissions for this directory.
        C:\>md C:\app\oracle
        C:\>icacls oracle:oinstall C:\app\oracle

    If you are installing on a Primary Domain Controller (PDC) or a Backup Domain Controller (BDC), log on as a member of the Domain Administrators group.
2.  If you are installing Oracle Database on a computer with multiple Network Interface Cards or multiple aliases, use System in the Control Panel to create the `ORACLE_HOSTNAME` system environment variable. Set this variable to point to the host name of the computer on which you are installing Oracle Database.
3.  Log in to the Oracle Database server as the Oracle Database software owner user (`oracle`).
4.  Download the Oracle Database 19c release 19.3 installation image file (`db_home.zip`) from Oracle Software Delivery Cloud website to a directory of your choice.
    <https://edelivery.oracle.com/>
5.  Create an OFA-compliant Oracle home directory on the local file system and extract the image files that you have downloaded in to this Oracle home directory. For example:
        C:\>md C:\app\oracle\product\19.0.0\dbhome_1
        C:\>cd C:\app\oracle\product\19.0.0\dbhome_1
        C:\app\oracle\product\19.0.0\dbhome_1> unzip \tmp\db_home.zip
6.  From the Oracle home directory, run the `setup.exe` command to start the Oracle Database Setup Wizard.
        C:\app\oracle\product\19.0.0\dbhome_1>setup.exe

    **Note:**

    Run the `setup.exe` command from the Oracle home directory only. Do not use the `setup.exe` command that resides at `%ORACLE_HOME%\oui\bin\`, or any other location, to install Oracle Database.
7.  In the Select Configuration Option screen, select Set Up Software Only.
8.  In the Select Database Installation Option screen, select Single instance database installation.
9.  In the Select Database Edition screen, select Enterprise Edition.
10. Respond to the configuration prompts as needed.
    **Note:**

    Click Help if you have any questions about the information you are asked to submit during installation.
11. When the Configuration Assistant tasks are complete, click Finish, click Exit, then click Yes to exit from Oracle Universal Installer.

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
