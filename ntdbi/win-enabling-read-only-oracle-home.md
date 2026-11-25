## Enabling a Read-Only Oracle Home

Configure your Oracle home as a read-only Oracle home after you have performed a software-only Oracle Database installation.

To enable a read-only Oracle home:

1.  Perform a software-only Oracle Database installation.

2.  Run the `roohctl -enable` script.

    **Note:**

    Do not use the `-disable` flag with the `roohctl` command, as it is not supported.

3.  Run Oracle Database Configuration Assistant (Oracle DBCA) to create a database.

### Software-Only Database Installation

1.  Log in as the Oracle installation owner user account (`oracle`) that you want to own the software binaries.

2.  Download the Oracle Database installation image files (`db_home.zip`) to a directory of your choice. For example, you can download the image files to the `\tmp` directory.

3.  Create the Oracle home directory and extract the image files that you have downloaded into this Oracle home directory.

    **Note:**

    Ensure that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Oracle home directory that you created.

4.  From the Oracle home directory, run the `setup.exe` command to start the Oracle Database installer.

5.  In the Select Configuration Option screen, select Set Up Software Only.

6.  Select your installation type. Installation screens vary depending on the installation option you select. Respond to the configuration prompts as needed.

**Note:**

Click Help if you have any questions about the information you are asked to submit during installation.

### Run the roohctl Script

1.  Go to the `bin` directory

        cd C:\app\oracle\product\19.0.0\dbhome_1\bin

2.  Run the `roohctl` script to enable read-only Oracle home.

        roohctl.bat -enable

### Run Oracle Database Configuration Assistant

1.  Ensure that you are still in the `bin` directory and run Oracle DBCA.

        dbca

2.  In the Select Database Operation screen, select Create a Database.

3.  The configuration screens vary depending on the options you select. Respond to the prompts as needed.

**Note:**

Click Help if you have any questions about the information you are asked to submit during database creation.

**Related Topics**

- [Oracle Database 2 Day DBA](../admqs/installing-oracle-database-creating-database.md)

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes1.md)
