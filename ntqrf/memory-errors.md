Review memory errors.

OSD-04100
Malloc() failure, unable to allocate memory

Cause: Program is out of memory.

Action: Shut down all unnecessary processes or install more memory in the computer.

OSD-04101
Invalid SGA: SGA not initialized

Cause: System Global Area (SGA) has been allocated but not initialized.

Action: Wait until STARTUP has completed before attempting to connect.

OSD-04102
Unable to open/create file for shared memory object

Cause: Unexpected return from Windows system service CreateFile().

Action: Check operating system error code and operating system documentation.

OSD-04103
Unable to attach to SGA: SGA does not exist

Cause: SGA does not exist.

Action: Start up an Oracle Database instance.

OSD-04104
Unable to map shared memory (SGA) into the address space

Cause: Unexpected return from Windows system service MapViewOfFileEx().

Action: Check operating system error code and operating system documentation.

OSD-04105
Shared memory (SGA) mapped to wrong address

Cause: Unexpected return from Windows system service MapViewOfFileEx().

Action: Check operating system error code and operating system documentation.

OSD-04106
Unable to allocate memory with VirtualAlloc

Cause: Program is out of memory.

Action: Shut down all unnecessary processes or install more memory in the computer.

OSD-04107
Unable to deallocate memory with VirtualFree

Cause: Unexpected return from Windows system service VirtualFree().

Action: Check operating system error code and operating system documentation.

OSD-04108
Unable to protect memory with VirtualProtect

Cause: Unexpected return from Windows system service VirtualProtect().

Action: Check operating system error code and operating system documentation.

**Parent topic:** [OSD-04000 to OSD-04599: Windows-Specific Oracle Database Messages](windows-specific-oracle-database-messages.md)
