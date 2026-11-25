## Before You Begin

This 15-minute tutorial shows you how to install the Data Miner repository.

### Background

Oracle Data Miner is a graphical user interface (GUI) and set of tools included as as free extension of Oracle SQL Developer. The Data Miner repository includes data you can use to illustrate the functionality of Data Miner.

- The Data Miner Repository installation routine automatically starts the first time that you activate a SQL Developer connection from the Data Miner tab.
- Once the Data Miner Repository has been installed in the database, other data miner users may be granted the required privileges to the repository by an automated process that is similar to the installation routine examined here.

### What Do You Need?

- Oracle Database 19c Enterprise Edition
- [Oracle SQL Developer version 19.x](https://www.oracle.com/tools/downloads/sqldev-downloads.html)
- A Data Miner user account and SQL Developer connection

------------------------------------------------------------------------

## Add a Data Miner Connection

1.  From the SQL Developer menu, select **Tools \> Data Miner \> Make Visible.**
2.  In the Data Miner tab, click the **Add Connection** tool (green "+" icon).
3.  Select **PDB1-DMUSER** from the Connection list and then click **OK**.

------------------------------------------------------------------------

## Install the Data Miner Repository

1.  Double-click on **PDB1-DMUSER**.
2.  Click **Yes** in the Required Privileges Missing window.
    <figure>
    <img src="img/required-privileges-missing.png" alt="Description of sample-arch-image.png follows" />
    <figcaption>Description of the illustration required-privileges-missing.png</figcaption>
    </figure>
3.  Enter the password for the SYS account and click **OK**.
4.  Click **OK** on the Repository Installation Settings window.
5.  Click **Start** to grant permissions to the Data Miner account and install the demo data.
    <figure>
    <img src="img/install-repository.jpg" alt="Description of install-repository.jpg follows" />
    <figcaption>Description of the illustration install-repository.jpg</figcaption>
    </figure>
6.  Click **Yes** on the Installing Demo Data window.

------------------------------------------------------------------------

## Next Tutorial

In the next tutorial, you'll create a Data Miner workflow.

------------------------------------------------------------------------
