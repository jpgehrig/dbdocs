## Installing Oracle Database Client Using Image File

Extract the image software (client_home.zip) into the directory where you want your Oracle Database Client home to be located.

Starting with 19c, the Oracle Database Client software is also available as an image file for download and installation.

Oracle recommends that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations.

To install Oracle Database Client using image file, perform the following steps:.

1.  Log in to Windows as an Administrator user. If you are installing on a Primary Domain Controller (PDC) or a Backup Domain Controller (BDC), log on as a member of the Domain Administrators group.
2.  Download the Oracle Database Client installation image files `(client_home.zip)` to a directory of your choice. For example, you can download the image files to the \tmp directory.
3.  Create the Oracle home directory and extract the image files that you have downloaded in to this Oracle home directory. For example:
        C:\>md C:\app\oracle\product\19.0.0\clienthome_1
        C:\>cd C:\app\oracle\product\19.0.0\clienthome_1
        C:\app\oracle\product\19.0.0\clienthome_1> unzip \tmp\client_home.zip
4.  From the Oracle home directory, run the `setup.exe` command to start the Oracle Database Client Setup Wizard.
        C:\app\oracle\product\19.0.0\clienthome_1>setup.exe

    **Note:**

    Run the `setup.exe` command from the Oracle home directory only. Do not use the `setup.exe` command that resides at `%ORACLE_HOME%\oui\bin\`, or any other location, to install Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure.
5.  The setup wizard starts an Administrator type installation of Oracle Database Client.
    Installation screens vary depending on the installation option you select. Respond to the configuration prompts as needed.

    **Note:**

    At any time during installation, if you have a question about what you are being asked to do, click Help.

**Parent topic:** [Installing the Oracle Database Client Software](installing-the-oracle-database-client-software.md)
