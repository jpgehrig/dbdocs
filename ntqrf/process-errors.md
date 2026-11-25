Review process errors.

OSD-04200
Unable to begin another thread

Cause: Program has run out of system resources.

Action: Shut down all unnecessary processes; install more memory in the computer.

OSD-04201
No pid structure supplied to spdcr()

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04202
DosSetPriority() failure, unable to set process priority

Cause: Unexpected return from Windows system service DosSetPriority().

Action: Check operating system error code and operating system documentation.

OSD-04203
DosKillProcess() failure, unable to kill process

Cause: Unexpected return from Windows system service DosKillProcess().

Action: Check operating system error code and operating system documentation.

OSD-04204
Invalid pid

Cause: Process ID not recognized by system; process previously terminated.

Action: Verify that process ID is correct and that process is active.

OSD-04205
CreateProcess() failure, unable to spawn process

Cause: Unexpected return from Windows system service CreateProcess().

Action: Check operating system error code and operating system documentation.

OSD-04207
Invalid priority specified in CONFIG parameter `ORACLE_PRIORITY`

Cause: Priority specified is invalid or out of range.

Action: Specify a valid setting for `ORACLE_PRIORITY`.

OSD-04208
OpenProcess() failure, unable to open process handle

Cause: Unexpected return from Windows system service OpenProcess().

Action: Check operating system error code and operating system documentation.

OSD-04209
Incorrect or unknown background image name given to spdcr()

Cause: Unexpected background name given to spdcr().

Action: Contact Oracle Support Services.

OSD-04210
Timeout waiting for thread semaphore

Cause: An Oracle Database thread died holding the semaphore.

Action: Restart Oracle Database instance.

OSD-04211
Thread information not found

Cause: An Oracle Database thread died without deleting its information.

Action: Restart Oracle Database instance.

OSD-04212
Maximum number of Oracle threads reached

Cause: Maximum number of Oracle Database threads for the instance is reached.

Action: Wait until some connections exit before trying again.

OSD-04213
Oracle thread unable to DuplicateHandle()

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04214
Oracle thread unable to CreateEvent()

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04215
Bad function code supplied to ssthreadop

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04216
Unable to find file handle for that thread

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04217
Unable to retrieve system username for current user

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04218
Cannot post thread

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04219
Bad thread list semaphore

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04221
Target thread is currently busy

Cause: Target thread is processing an Oracle Database utility command.

Action: Wait and resend command.

OSD-04222
Unable to get the threads context

Cause: Check operating system error code.

Action: Remedy operating system error.

OSD-04223
Unable to set the threads context

Cause: Check operating system error code.

Action: Remedy operating system error.

OSD-04224
Unable to suspend the target thread

Cause: Check operating system error code.

Action: Remedy operating system error.

OSD-04225
Unable to resume the target thread

Cause: Check operating system error code.

Action: Remedy operating system error.

**Parent topic:** [OSD-04000 to OSD-04599: Windows-Specific Oracle Database Messages](windows-specific-oracle-database-messages.md)
