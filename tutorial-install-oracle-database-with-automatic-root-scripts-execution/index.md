## Before You Begin

This 15-minute tutorial shows you how to install the Oracle Database 19c with automated ` root ` scripts execution.

### Background

In Oracle Database 18c, the installation of the Oracle Database software requires ` root ` scripts to be executed manually.

### What Do You Need?

- Oracle Database 19c software appropriate for your platform that you store in a staging directory

------------------------------------------------------------------------

## Prepare the Directory

1.  Log in to your server as ` root ` and create the directory dedicated for the Oracle Database 19c software.

        mkdir -p /u01/app/oracle/product/19.0.0/dbhome_2

2.  Go to the directory.

        cd /u01/app/oracle/product/19.0.0/dbhome_2

3.  Unzip `db_home.zip` to the directory dedicated for the Oracle Database 19c installation.

        unzip /staging/db_home.zip

4.  Change the group and owner ownership of the directories where the files are unzipped.

        cd /u01

        chown -R oracle *

        chgrp -R oinstall *

5.  Quit the ` root ` session.

        exit

------------------------------------------------------------------------

## Install Oracle Database 19c

In this section, you install the Oracle Database 19c using the Oracle Universal Installer and the automatic ` root ` scripts execution.

1.  Log in to your server as ` oracle ` and go to the directory dedicated for the Oracle Database 19c software.

        cd /u01/app/oracle/product/19.0.0/dbhome_2

2.  Launch ` runInstaller`.

        ./runInstaller

3.  In the `Select Configuration Option ` page, select ` Set Up Software Only `.

4.  In the ` Select Database Installation Option` page, click Next.

5.  In the ` Select Database Edition ` page, click Next.

6.  In the ` Specify Installation Location ` page, click Next.

7.  In the ` Privileged Operating System Groups ` page, click Next.

8.  In the ` Root script execution configuration ` page, check ` Automatically run configuration scripts`, and provide the password for the ` root ` user. Click Next.

9.  In the ` Perform Prerequisite Checks ` page, check `Ignore All` and click Next. If there is a warning message, choose Yes.

10. In the ` Summary ` page, click the ` Save Response File… `. This allows you to observe the way the ` root ` scripts automatic execution is recorded in the response file. Select the `/tmp` directory to save the `db.rsp ` response file. Click Save and then Install.

11. In the ` Install Product `page, the ` Progress `displays the steps executed until the following message appears:
    <figure>
    <img src="./img/root.png" alt="Warning message" />
    <figcaption>Description of the illustration [root.png]</figcaption>
    </figure>

    Click Yes.

12. In the ` Finish ` page, click Close. The installation is complete.

------------------------------------------------------------------------

## Read the Response File

1.  Go to the directory where the response file is created.

        cd /tmp

2.  Read the response file.

        cat db.rsp

    Use the [db.rsp](files/db.rsp) to view the resulting response file.

3.  Read the information that is relevant for the feature.

        oracle.install.db.rootconfig.executeRootScript=true
        #--------------------------------------------------------------------------------------
        # Specify the configuration method to be used for automatic root script execution.
        #
        # Following are the possible choices:
        #   - ROOT
        #   - SUDO
        #--------------------------------------------------------------------------------------
        oracle.install.db.rootconfig.configMethod=ROOT

------------------------------------------------------------------------

## Clean Up the Software Installed

1.  If the OBE was a test for an installation, and if you want to deinstall the installed software, go to the directory where the Oracle Database 19c sotfware is installed.

        cd /u01/app/oracle/product/19.0.0/dbhome_2/deinstall

2.  Launch ` deinstall`.

        ./deinstall

3.  Answer the first question during the deinstallation.

4.  Answer the second question during the deinstallation.

        Oracle Home selected for deinstall is: /u01/app/oracle/product/19.0.0/dbhome_2
        Inventory Location where the Oracle home registered is: /u01/app/oraInventory
        Do you want to continue (y - yes, n - no)? [n]: y

5.  Read the [deinstall_output.txt](files/deinstall_output.txt) file to ensure that the deinstallation completed successfully.

        Oracle Universal Installer cleanup was successful.
        ...
        Oracle deinstall tool successfully cleaned up temporary directories.
        ############# ORACLE DEINSTALL TOOL END #############

6.  Quit the session.

        EXIT

` `

` `
