## 9  SQL\*Plus Security

This chapter describes the available methods for controlling access to database tables, and SQL\*Plus commands. It covers the following topics:

- Disabling SQL\*Plus\_ SQL\_ and PL/SQL Commands

- About Creating and Controlling Roles

- About Disabling Commands with SQLPLUS -RESTRICT

- About Program Argument Security

### 9.1 Disabling SQL\*Plus, SQL, and PL/SQL Commands

**Note:**

Starting with Oracle Database 19c, the SQL\*Plus table PRODUCT_USER_PROFILE (PUP table) is desupported. Oracle recommends that you protect data by using Oracle Database settings, so that you ensure consistent security across all client applications.

To disable a SQL or SQL\*Plus command for a given user, insert a row containing the user's username in the Userid column, the command name in the Attribute column, and DISABLED in the Char_Value column. The Scope, Numeric_Value, and Date_Value columns should contain NULL. For example:

    PRODUCT    USERID  ATTRIBUTE  SCOPE   NUMBERIC    CHAR       DATE    LONG
                                          VALUE       VALUE      VALUE   VALUE
    -------    ------  ---------  -----   --------    ------     -----   -----
    SQL*Plus   HR      HOST                           DISABLED
    SQL*Plus   %       INSERT                         DISABLED
    SQL*Plus   %       UPDATE                         DISABLED
    SQL*Plus   %       DELETE                         DISABLED

To re-enable commands, delete the row containing the restriction.

SQL\*Plus commands that can be disabled:

- ACCEPT

- DEFINE

- PASSWORD

- SHUTDOWN

- APPEND

- DEL

- PAUSE

- SPOOL

- ARCHIVE LOG

- DESCRIBE

- PRINT

- START (@, @@)

- ATTRIBUTE

- DISCONNECT

- PROMPT

- STARTUP

- BREAK

- EDIT

- RECOVER

- STORE

- BTITLE

- EXECUTE

- REMARK

- TIMING

- CHANGE

- EXIT/QUIT

- REPFOOTER

- TTITLE

- CLEAR

- GET

- REPHEADER

- UNDEFINE

- COLUMN

- HELP (?)

- RUN

- VARIABLE

- COMPUTE

- HOST

- SAVE

- WHENEVER OSERROR

- CONNECT

- INPUT

- SET

- WHENEVER SQLERROR

- COPY

- LIST (;)

- SHOW

- XQUERY

SQL commands that can be disabled:

- ALTER

- ANALYZE

- ASSOCIATE

- AUDIT

- CALL

- COMMENT

- COMMIT

- CREATE

- DELETE

- DISASSOCIATE

- DROP

- EXPLAIN

- FLASHBACK

- GRANT

- INSERT

- LOCK

- MERGE

- NOAUDIT

- PURGE

- RENAME

- REVOKE

- ROLLBACK

- SAVEPOINT

- SELECT

- SET CONSTRAINTS

- SET ROLE

- SET TRANSACTION

- TRUNCATE

- UPDATE

- VALIDATE

You can disable the following PL/SQL commands:

- BEGIN

- DECLARE

**Note:**

- Disabling HOST disables the operating system alias for HOST, such as \$ on Windows, and ! on UNIX.

- Disabling LIST disables ; and numbers (numbers entered to go to that line in a script).

- You must disable HELP and ? separately to disable access to command-line help.

- Disabling the SQL\*Plus SET command also disables SQL SET CONSTRAINTS, SET ROLE and SET TRANSACTION.

- Disabling SQL\*Plus START also disables @ and @@.

- Disabling BEGIN and DECLARE does not prevent the use of SQL\*Plus EXECUTE to run PL/SQL. EXECUTE must be disabled separately.

- Disabling EXIT/QUIT is not recommended. If disabled, terminate a command-line session by sending an EOF character such as Ctrl+D in UNIX or Ctrl+Z in Windows. Otherwise, terminate a session by terminating the SQL\*Plus process. If disabled, the EXIT operation in WHENEVER OSERROR and WHENEVER SQLERROR is also disabled.

1.  Log in as SYSTEM with the command
        SQLPLUS SYSTEM
2.  Insert a row into the PUP table with the command:
        INSERT INTO PRODUCT_USER_PROFILE
        VALUES ('SQL*Plus', 'HR', 'SELECT', NULL, NULL, 'DISABLED', NULL, NULL);
3.  Connect as HR and try to SELECT something:
        CONNECT HR
        SELECT * FROM EMP_DETAILS_VIEW;

    This command causes the following error message:

        SP2-0544: Command SELECT disabled in Product User Profile
4.  To delete this row and remove the restriction from the user HR, CONNECT again as SYSTEM and enter:
        DELETE FROM PRODUCT_USER_PROFILE WHERE USERID = 'HR';

### 9.2 About Creating and Controlling Roles

You can use SQL commands to create and control access to roles to provide security for your database tables. By creating a role and then controlling who has access to it, you can ensure that only certain users have access to particular database privileges.

Roles are created and used with the SQL CREATE, GRANT, and SET commands:

- To create a role, you use the CREATE command. You can create roles with or without passwords.

- To grant access to roles, you use the GRANT command. In this way, you can control who has access to the privileges associated with the role.

- To access roles, you use the SET ROLE command. If you created the role with a password, the user must know the password in order to access the role.

#### 9.2.1 About Disabling SET ROLE

From SQL\*Plus, users can submit any SQL command. In certain situations, this can cause security problems. Unless you take proper precautions, a user could use SET ROLE to access privileges obtained through an application role. With these privileges, they might issue SQL statements from SQL\*Plus that could wrongly change database tables.

To prevent application users from accessing application roles in SQL\*Plus, you can use the PUP table to disable the SET ROLE command. You also need to disable the BEGIN and SQL\*Plus EXECUTE commands to prevent application users setting application roles through a PL/SQL block. This gives a SQL\*Plus user only those privileges associated with the roles enabled when they started SQL\*Plus. For more information about the creation and usage of user roles, see your [Oracle Database SQL Language Reference](../sqlrf/index.md) and [Oracle Database Administrator's Guide](../admin/index.md).

#### 9.2.2 About Disabling User Roles

To disable a role for a given user, insert a row in the PUP table containing the user's username in the Userid column, "ROLES" in the Attribute column, and the role name in the Char_Value column.

**Note:**

When you enter "PUBLIC" or "%" for the Userid column, you disable the role for all users. You should only use "%" or "PUBLIC" for roles which are granted to "PUBLIC". If you try to disable a role that has not been granted to a user, none of the roles for that user are disabled.

The Scope, Numeric_Value, and Date_Value columns should contain NULL. For example:

    PRODUCT    USERID  ATTRIBUTE  SCOPE   NUMERIC     CHAR      DATE     LONG
                                          VALUE       VALUE     VALUE    VALUE
    -------    ------  ---------  -----   --------    ------    -----    -----
    SQL*Plus   HR      ROLES                          ROLE1
    SQL*Plus   PUBLIC  ROLES                          ROLE2

During login, these table rows are translated into the command

    SET ROLE ALL EXCEPT ROLE1, ROLE2

To ensure that the user does not use the SET ROLE command to change their roles after login, you can disable the SET ROLE command.

To re-enable roles, delete the row containing the restriction.

See About Disabling SET ROLE for more information.

### 9.3 About Disabling Commands with SQLPLUS -RESTRICT

The RESTRICT option enables you to disable certain commands that interact with the operating system. However, commands disabled with the -RESTRICT option are disabled even when no connection to a server exists, and remain disabled until SQL\*Plus terminates.

The following table shows which commands are disabled in each restriction level.

| Command | Level 1  | Level 2  | Level 3  |
|:--------|:---------|:---------|:---------|
| EDIT    | disabled | disabled | disabled |
| GET     |          |          | disabled |
| HOST    | disabled | disabled | disabled |
| SAVE    |          | disabled | disabled |
| SPOOL   |          | disabled | disabled |
| START   |          |          | disabled |
| STORE   |          | disabled | disabled |

**Note:**

- Disabling HOST also disables your operating system's alias for HOST, such as \$ on Windows, and ! on UNIX.

- Disabling the SQL\*Plus START command will also disable the SQL\*Plus @ and @@ commands.

For more information about the RESTRICT option, see the SQLPLUS [RESTRICT Option](starting-SQL-Plus.md).

### 9.4 About Program Argument Security

Some operating systems allow any user to see what programs are being run. If the display also shows command-line arguments, it may be possible to view the usernames and passwords of other SQL\*Plus users.

For example, on many UNIX or Linux systems the ps command shows program arguments. To stop passwords being displayed depends on how you use SQL\*Plus.

- To run SQL\*Plus interactively, always wait for SQL\*Plus to prompt for connection information, particularly your password.

- To run a batch SQL script from a UNIX shell script, set environment variables MYUSERNAME and MYPASSWORD to the appropriate values. Run a shell script containing:

      sqlplus /nolog <<EOF
      connect $MYUSERNAME/$MYPASSWORD
      select ...
      EOF

- To run a batch SQL script, hard code the username and password as the first line of the SQL script. Then call the script with:

      sqlplus @myscript.sql

When SQL\*Plus is started like this, it uses the first line of the script as the username/password@connection_identifier string.

Avoid storing your username and password in files or scripts. If you do store your username and password in a file or script, ensure that the file or script is secured from non-authorized access.
