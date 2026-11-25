Review the error messages that are displayed when trying to modify the ownership, group membership, or permission of a file fails while changing a file's owner.

The following error messages are displayed:

ORA-15301
cannot change %s of the open file '%s'

Cause: A SET OWNERSHIP or SET PERMISSION command was attempted on an open file.

Action: Close the file and retry the SQL command.

ORA-15302
active use of files owned by user '%s' precludes its drop

Cause: A DROP USER command specified a user owning files that were in use.

Action: Close all files owned by this user.

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
