The following error messages are displayed when the SQL statement or the ASMCMD command for user replacement fails on Windows:

ORA-15252
user name '%s' does not exist in OS user dictionary

Cause: The specified user name was not a valid operating system user.

Action: Specify a valid operating system user.

ORA-15260
permission denied on ASM disk group

Cause: An attempt was made to perform an operation on an ASM disk group without the appropriate privileges.

Action: Ask the ASM administrator to perform the operation or grant the required privileges.

ORA-15261
user '%s' already exists in disk group '%s'

Cause: The specified UID already existed in the disk group.

Action: Specify a different UID.

ORA-15262
user '%s' does not exist in disk group '%s'

Cause: The specified UID did not exist in the disk group.

Action: Specify a user with a valid UID.

ORA-15263
user name '%s' exceeds limit of %s characters

Cause: The length of the specified user name exceeded the maximum limit.

Action: Reduce the length of the user name to a value within the limit.

ORA-15264
Operating system function returned error %s

Cause: An operating system error occurred.

Action: Correct the operating system error and retry the operation.

ORA-15265
user identification number not in range of \[%s,%s\]

Cause: The operating system user identification number exceeded the maximum value.

Action: Change the user identification number to a value within the accepted range.

ORA-15266
user identification number '%s' is not allowed

Cause: This user identification number is used internally by ASM.

Action: Please choose a different user identification number.

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
