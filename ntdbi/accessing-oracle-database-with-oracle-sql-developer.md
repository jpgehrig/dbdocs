## Accessing Oracle Database with Oracle SQL Developer

You can use SQL Developer to issue SQL and PL/SQL statements. All SQL and PL/SQL commands are supported as they are passed directly from the SQL Worksheet to the Oracle Database.

All SQL and PL/SQL commands are supported as they are passed directly from the SQL Worksheet to the Oracle Database.

To start SQL Developer:

1.  From the Start menu, select All Programs, then Oracle - HOMENAME, then Application Development, and then SQL Developer.
2.  If you are prompted to enter the full path name for java.exe, click Browse and find `java.exe`. For example, `C:\Program Files\Java\jdk1.6.0_25\bin\java.exe`.
3.  Once SQL Developer starts, perform the following steps:
    - Right-click Connections.

    - Select New Connection.

    - In the New/Select Database Connection dialog box, enter a Connection name, username, password, and for the host string, the name of the database to which you want to connect.

    - Click Connect.

Once connected, you can view, create, modify, and delete the database objects using the Connection Navigator or issue any SQL or PL/SQL command using a SQL Worksheet (From the Tools menu, select SQL Worksheet).

SQL\*Plus commands have to be interpreted by the SQL Worksheet before being passed to the database. The SQL Worksheet currently supports many SQL\*Plus commands. SQL\*Plus commands which are not supported by the SQL Worksheet are ignored and are not sent to the Oracle Database.

**See Also:**

[Oracle SQL Developer User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntdbi&id=RPTUG10710)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
