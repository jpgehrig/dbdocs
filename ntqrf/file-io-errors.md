Review File I/O errors.

OSD-04000
Logical block size mismatch

Cause: Database block size specified in the initialization parameter file does not match block size of actual database files.

Action: Use matching logical block sizes.

OSD-04001
Invalid logical block size

Cause: Logical block size is not a multiple of 512 bytes, or it is too large.

Action: Change the value of `DB_BLOCK_SIZE` in the initialization parameter file.

OSD-04002
Unable to open file

Cause: Specified path or file name is invalid, or destination device is full. This error can also be caused by insufficient Windows file handles.

Action: Make sure path and file exist, and device has free space. If this fails, then increase number of Windows file handles.

OSD-04003
Unable to read file header block

Cause: Media has been damaged.

Action: Recover file, if necessary, and verify that Windows is functioning correctly.

OSD-04004
Invalid file header

Cause: File is damaged.

Action: Recover file.

OSD-04005
SetFilePointer() failure, unable to read from file

Cause: Unexpected return from Windows system service SetFilePointer().

Action: Check operating system error code and operating system documentation.

OSD-04006
ReadFile() failure, unable to read from file

Cause: Unexpected return from Windows system service ReadFile().

Action: Check operating system error code and operating system documentation.

OSD-04007
Truncated read

Cause: System encountered an unexpected end-of-file, which is due to damaged media.

Action: Verify that file is not damaged.

OSD-04008
WriteFile() failure, unable to write to file

Cause: Unexpected return from Windows system service WriteFile().

Action: Check operating system error code and operating system documentation.

OSD-04009
Truncated write

Cause: Destination device is full, or media is damaged.

Action: Verify that device has free space and that file is not damaged.

OSD-04010
\<create\> option specified, file already exists

Cause: File you attempted to create already exists.

Action: Delete existing file or use `REUSE` option in SQL statement.

OSD-04011
GetFileInformationByHandle() failure, unable to obtain file info

Cause: Unexpected return from Windows system service GetFileInformationByHandle().

Action: Check operating system error code and operating system documentation.

OSD-04012
File size mismatch

Cause: File to be re-used is either too large or too small.

Action: Specify correct file size or delete existing file.

OSD-04013
Unable to read line from file

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04014
Unable to close file

Cause: Media has been damaged.

Action: Recover file, if necessary, and verify that Windows is functioning correctly.

OSD-04015
Asynchronous I/O request returned an error

Cause: Unexpected return from Windows system service.

Action: Check operating system error code and operating system documentation.

OSD-04016
Error queuing an asynchronous I/O request

Cause: Unexpected return from Windows system service.

Action: Check operating system error code and operating system documentation.

OSD-04017
Unable to open the specified RAW device

Cause: An invalid path or file name was specified, or device is full.

Action: Make sure file exists and device is not full; verify that operating system is functioning correctly.

OSD-04018
Unable to access the specified directory or device

Cause: An invalid path name was specified.

Action: Make sure directory or device exists and is accessible.

OSD-04019
Unable to set file pointer

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04020
Unable to set eof file marker

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04021
Unable to read file

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04022
Unable to write file

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04023
SleepEx() failure, unable to Sleep

Cause: Unexpected return from Windows system service.

Action: Check operating system error code and operating system documentation.

OSD-04024
Unable to delete file

Cause: This error is caused by an operating system error or by damaged media.

Action: Check operating system error code (if available) and operating system documentation. If no operating system error code is presented, then verify that media is not damaged.

OSD-04025
Invalid question asked

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

OSD-04026
Invalid parameter passed

Cause: This is an internal error, not normally expected to occur.

Action: Contact Oracle Support Services.

**Parent topic:** [OSD-04000 to OSD-04599: Windows-Specific Oracle Database Messages](windows-specific-oracle-database-messages.md)
