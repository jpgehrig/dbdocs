## Starting DBCA on Microsoft Windows Systems

You can either start the Oracle Database Configuration Assistant (DBCA) utility from the command line or from the Windows Start menu.

**Note:**

To run DBCA, you do not have to set operating system environment variables `ORACLE_HOME` to the Oracle RAC database home, or `ORACLE_UNQNAME` to the database unique name.

1.  Log in as an Administrator user.
    The user must also be a member of `ORA_DBA` or `ORA_``Homename``_DBA` group and must also be a member of `ORA_ASMDBA` if Oracle ASM is used as storage for the Oracle RAC database.
    You are prompted to enter the password for the Oracle Home User if you are administering an Administrator-managed Oracle RAC database and chose not to store the password in an Oracle Wallet.
2.  To start DBCA from the command line:
    1.  Open a command prompt window.
    2.  Navigate to the `Oracle_home``\bin` directory.
    3.  Enter the command `dbca`.
3.  To start DBCA from the Start menu:
    1.  Click Start.
    2.  Select Programs.
    3.  Under Programs, select Oracle - Oracle_home name.
    4.  Select Configuration and Migration Tools.
    5.  Select Database Configuration Assistant.
4.  After you have started DBCA, to create an Oracle RAC database, you select the following:
    - Create Database on the Database Operation/Welcome page

    - Advanced Configuration on the Creation Mode page

    - Oracle RAC database on the Deployment Type page

**Related Topics**

- [Deleting an Oracle RAC Database Using DBCA](deleting-an-oracle-rac-database-using-dbca.md)

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
