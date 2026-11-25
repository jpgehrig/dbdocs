When you install Oracle Database, a special Windows local group called `ORA_DBA` is created (if it does not already exist from an earlier Oracle Database installation) and the Oracle Installation User is automatically added to it.

Members of local group `ORA_DBA` automatically receive the SYSDBA privilege. The `ORA_DBA` group is also created for each Oracle home called `ORA_``HOMENAME``_DBA` group. This group is automatically populated with the Oracle Home User for the Oracle home.

**Note:**

If you use a domain account for database administration, then that domain account must be granted local administrative privileges and ORA_DBA membership explicitly. It is not sufficient for the domain account to inherit these memberships from another group. You must ensure that the user performing the installation is in the same domain as this domain account. If not, it results in an NTS authentication failure.

Membership in `ORA_DBA` enables you to:

- Connect to local Oracle Database servers without a password with the command

      SQL> CONNECT / AS SYSDBA

- Connect to remote Oracle Database servers without a password with the command

      SQL> CONNECT /@net_service_name AS SYSDBA

  where `net_service_name` is the net service name of the remote Oracle Database server

- Perform database administration procedures such as starting and shutting down local databases

- Add additional Windows users to `ORA_DBA`, enabling them to have the `SYSDBA` privilege

**Parent topic:** [Authenticating Database Users with Windows](authenticating-database-users-with-windows.md)
