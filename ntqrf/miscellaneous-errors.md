Review miscellaneous errors.

OSD-04500
Illegal option specified

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04501
Internal buffer overflow

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04502
Translations nested too deep

Cause: Program encountered too many intermediate translations while attempting to translate a configuration variable.

Action: Simplify values of configuration parameters to include fewer intermediate translations.

OSD-04503
Text contains no translatable elements

Cause: Program cannot recognize variables in text to be translated.

Action: Check and, if necessary, correct text to be translated.

OSD-04505
stdin not responding

Cause: System cannot receive input from standard input stream.

Action: Verify that process has access to an input device.

OSD-04506
Unable to spawn process through system()

Cause: System is out of memory or executable is invalid.

Action: Shut down unnecessary processes; install more memory in the computer. Verify name of executable.

OSD-04510
Operating system roles are not supported

Cause: An attempt was made to use an operating system role.

Action: Only use roles that were created '`IDENTIFIED` `BY` `PASSWORD`' as opposed to '`IDENTIFIED` `EXTERNALLY`'.

OSD-04511
Unable to get date and time from the operating system

Cause: Unexpected return from GetLocalTime() call.

Action: Verify that system time is correct on the computer.

OSD-04512
Unable to translate the '`USERNAME`' config.ora variable on server

Cause: '`USERNAME`' configuration parameter variable on host is not properly set.

Action: Verify '`USERNAME`' variable is set.

OSD-04513
'remote_os_authent' init.ora variable not set to TRUE

Cause: For remote operating system logon to function, '`REMOTE_OS_AUTHENT`' parameter must be set to `TRUE`.

Action: Shut down and start up instance with '`REMOTE_OS_AUTHENT = TRUE`' in initialization parameter file.

OSD-04514
The Windows Group name is too long for internal buffer

Cause: Windows Group name is too long.

Action: Use a shorter Windows group name.

**Parent topic:** [OSD-04000 to OSD-04599: Windows-Specific Oracle Database Messages](windows-specific-oracle-database-messages.md)
