This appendix lists error messages, causes, and corrective actions that are specific to operation of Oracle Database for Fujitsu BS2000. The messages shown in this appendix may be accompanied by additional text when displayed on screen. This text identifies the function that detected the problem, and can include internal status codes, BS2000 SOSD error code, or both. These error codes can be helpful to the Oracle Support Services Representative in determining the cause of a problem. The BS2000 SOSD error code indicates that the error originated in the operating system code. The error code is displayed in hexadecimal, and is structured as follows:

`BS2000 SOSD error 0x8``xxxyyyy`` from`` mmmmmmmm`` : ``text`

Where:

- `xxx` identifies the function reporting the error.

- `yyyy` details the error. It is either an internal code of the function, or a compacted return code of a BS2000 system macro (see subsequent section).

- `mmmmmmmm` is the name of the function.

- `text`, if present, explains the error code. Often it says "`RC FROM ``zzzzz`` MACRO`".

A BS2000 system macro return code is condensed into the 2-byte value `yyyy` as follows:

- For system macros that return a code `bb0000aa`, `yyyy` is `bbaa`

- For I/O calls, `yyyy` is the DMS error code

- In all other cases, `yyyy` contains the right halfword of the return code of the BS2000 macro.

Sometimes, for example, in the early stages of initialization when the message components are not yet available, the Oracle Database cannot issue a regular Oracle message. If this occurs, then Oracle Database calls the ILCS task termination routine, or it issues a `TERM` macro directly, giving the message number as the user termination code. You can use this message number to find the explanation in this appendix.

ORA-05000: ORACLE termination routine called
Cause: The termination routine of the Oracle Database run-time system has been called due to a fatal error.

Action: If you do not know why the Oracle Database program terminated, or how to resolve this problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05001: Unsupported BS2000 Version
Cause: The active version of the BS2000 operating system is not supported by this Oracle Database release.

Action: Upgrade to a more recent BS2000 version.

<!-- -->

ORA-05002: Fatal error: called from non-ILCS program
Cause: In a precompiler or OCI application, the Oracle Database is called from a program that does not run in an ILCS environment. The Oracle Database does not support non-ILCS programs

Action: Ensure that the application program runs in an ILCS mode. Some programming languages, for example, FOR1, PL/I, require specific options for ILCS. Refer to the Fujitsu documentation for further information.

<!-- -->

ORA-05003: Fatal error: ILCS PCD cannot be verified
Cause: In a precompiler or OCI application, Oracle Database is called with a save area that is marked as an ILCS save area but does not point to a proper PCD (ILCS global area). The problem is either that memory has been overwritten, or that Oracle Database is called from a program that does not run in an ILCS environment. Oracle Database does not support non-ILCS programs.

Action: Ensure that the application program runs in an ILCS mode. Some programming languages, for example, FOR1, PL/I, require specific options for ILCS. Refer to the Fujitsu documentation for further information.

<!-- -->

ORA-05004: Fatal error: stack overflow, extension failed
Cause: A call to a function required an extension of the current call stack segment. This extension failed and the corresponding ILCS routine returned the error.

Action: Ensure that the address space limit of the BS2000 user ID is sufficient and that there is no temporary memory saturation. Then re-run the program. If you need further help, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05005: Error: IT0INITS called in PROLOD
Cause: This is an internal error and should not occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05006: sltga already initialized
Cause: The initialization routine for the `sltga` is called more than once.

Action: Check if more than one stub modules (`PROSTUB`, `XAOSTUB`) are linked to the application.

<!-- -->

ORA-05007: failed to load OSNTAB
Cause: This message is usually preceded by a BS2000 BLS-nnnn message. The most likely reason is that the `ORALOAD` library cannot be found.

Action: Contact the Database Administrator about the `ORALOAD` library. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05008: failed to load requested network driver
Cause: This message is usually preceded by a BS2000 `BLS-nnnn` message. The most likely reason is that the `ORALOAD` library cannot be found.

Action: Contact the Database Administrator about the `ORALOAD` library. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05010: bad filename length
Cause: Buffer overflow while building/translating a file name. This could be caused by specifying an excessively long file name in the `ORAENV` file.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05011: bad file size
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05012: bad block size
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05013: bad filename parse
Cause: A file name being analyzed is not well-formed for Oracle Database purposes.

Action: Correct the file name and re-run the program.

<!-- -->

ORA-05014: sfcopy: non-matching block size
Cause: In a partial database file copy, source and target file have different block sizes. This may indicate an internal error and should not normally occur.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05015: text file open failed
Cause: An Oracle Database text or command file cannot be opened. One of the following could cause this error: the file name is wrong, the file has not been properly initialized, or the file is not accessible.

Action: Correct the problem and restart the Oracle Database. If this occurs when you issued the `STARTUP` command, then check the initialization file for the correct specification of the database files.

<!-- -->

ORA-05016: text file close failed
Cause: Attempt to close an Oracle Database file has failed. This is an internal error and should not normally occur.

Action: Contact your Oracle Support Services Representative.

<!-- -->

ORA-05017: file open failed
Cause: An Oracle Database database file cannot be opened. Either the file name is wrong, the file has not been properly initialized, or the file is not accessible.

Action: Correct the problem and restart the Oracle Database. If this occurred when you issued the `STARTUP` command, then check the initialization file for the correct specification of the database files.

<!-- -->

ORA-05018: file seek failed
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05019: file write failed
Cause: An I/O error occurred while writing to an Oracle Database file.

Action: If the error cannot be identified as one caused by a disk malfunction, then either contact the System Administrator, or contact the Oracle Support Services Representative.

<!-- -->

ORA-05020: write block outside of file
Cause: An attempt was made to write a block of an Oracle Database file that does not exist. For example, block number `< 1` or `>` file size. This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05021: file read failed
Cause: An I/O error occurred while reading an Oracle Database file.

Action: If the error cannot be identified as one caused by a disk malfunction, then either contact the System Administrator, or contact the Oracle Support Services Representative.

<!-- -->

ORA-05022: read block outside of file
Cause: An attempt was made to read a block of an Oracle Database file that does not exist. For example, block number `< 1` or `>` file size. This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05023: file close failed
Cause: The attempt to close an Oracle Database file failed. This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05025: sfccf:file mismatch. Trying to reuse a file with different size
Cause: When trying to reuse a database file, the file size specified differs from the actual size of the existing file.

Action: Specify the correct file size (remember to subtract one logical block for the implicit header block), or leave the size unspecified, or use a different file name if you want to create a larger or smaller database file.

<!-- -->

ORA-05026: file does not exist
Cause: An attempt was made to access a database file, which no longer exists.

Action: Contact the Database Administrator who may know why this error has occurred. If the Database Administrator cannot find the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05027: file does exist
Cause: When attempting to create a new file, this error occurs if the file is found and is not empty.

Action: If the error occurred in a `create database`, then retry with the `reuse` option. Otherwise use a different file name or check whether the file can be erased.

<!-- -->

ORA-05028: file is not a dbfile
Cause: The database, or log, or control, file to be opened does not contain the proper identification for such a file.

Action: Check for wrong file specification.

<!-- -->

ORA-05029: illegal use-option
Cause: Internal error. Function `sfccf` was called with an illegal option.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05030: SID not defined
Cause: When the system id was required, typically, to substitute the "?" in names, for example, in file names set by the initialization file, it was not yet defined. This could be caused by a missing `ORAENV` file or a missing `ORASID` in that file.

Action: Ensure that the `ORAENV` file definition is correct and re-run the program.

<!-- -->

ORA-05031: SID translation failure
Cause: The system id is syntactically incorrect.

Action: Ensure that the` ORASID` definition is correct and re-run the program.

<!-- -->

ORA-05032: bad name parse
Cause: The translation of a file name, or other name containing variable parts, failed. The error may be caused by a wrong specification in the `ORAENV` file.

Action: Ensure that the` ORAENV` variable assignments are correct. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05033: bad environment values
Cause: One or more of the values specified in the `ORAENV` file are invalid.

Action: Ensure that you specified legal values in the `ORAENV` file, refer to the [Oracle Environment Variables](oracle-environment-variables.md) in this guide for further information.

<!-- -->

ORA-05034: bad seal
Cause: Internal error. An internal file control structure is found to be corrupt.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05035: host command not executed
Cause: A BS2000 command, argument of a `HOST` or `#HOST` command, is invalid or too long.

Action: Enter a valid `HOST` command.

<!-- -->

ORA-05036: bad user id (length)
Cause: Internal buffer overflow while building a file name from variable components.

Action: Ensure that the `ORAUID` value specified in the `ORAENV` file is correct. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05037: /CANCEL command not executed
Cause: A background job could not be canceled. The background task may have already been terminated.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05038: SID has illegal length
Cause: The system identifier specified in either the `ORAENV` file or as part of a connect string exceeds 4 characters in length.

Action: Specify a correct value.

<!-- -->

ORA-05039: Recursive entry to ssodrv
Cause: Oracle Database kernel has been reentered at the top. This should not happen.

Action: Ensure that the user program does not incorrectly call Oracle Database functions from within an interrupt handling routine (signal routine, contingency). If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05040: no more dynamic memory
Cause: Request memory failed in file-management components. This is probably caused by a user address space that is too small.

Action: Ensure that the address space limit of the BS2000 user ID is sufficient and that there is no temporary memory saturation. Then re-run the program. If you need further help, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05046: Archive control string error
Cause: The archive file name or control parameters are incorrect.

Action: Correct the parameters.

<!-- -->

ORA-05050: PGA (fixed part) could not be allocated
Cause: Probable operating system error or internal error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05051: cannot allocate var. PGA
Cause: During creation of the PGA, required dynamic memory could not be allocated.

Action: Verify that the user address space is large enough and that if an application program produced the error, the program is not consuming excessive memory. Otherwise contact the Oracle Support Services Representative.

<!-- -->

ORA-05052: error deleting var. PGA
Cause: During deletion of the PGA, dynamic memory could not be released. This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05053: invalid or missing PGA_BASE
Cause: An invalid value for the `PGA_BASE` parameter has been specified in the `ORAENV` file.

Action: Use the default value for the `PGA_SIZE` environment variable. If this does not solve the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05054: invalid or missing PGA_SIZE
Cause: An invalid value for the `PGA_SIZE` environment variable has been specified in the `ORAENV` file. You should never need to change the default value for the `PGA_SIZE` environment variable.

Action: Use the default value for the `PGA_SIZE` environment variable. If this does not solve the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05055: address range for PGA (fixed part) is not free
Cause: The address range described by the `PGA_BASE` and `PGA_SIZE ORAENV` variables is not available for allocation. This may be due to overlapping `PGA`, `SGA`, and `KERNEL` areas, or to an application program, which has occupied memory in this area. If you did not specify a value for `PGA_BASE`, the default may be inappropriate for the case.

Action: Refer to [Memory Architecture](concepts-and-architecture.md) for further information.

<!-- -->

ORA-05056: no more context space
Cause: During processing of a SQL statement, dynamic memory could not be allocated. This could happen when very complex requests are being processed and there is not enough memory available.

Action: Verify that the user address space is large enough and that the application program, if the error occurred when you were using an application program, is not using excessive memory. Otherwise, contact the Oracle Support Services Representative.

<!-- -->

ORA-05058: assert failed: SGA not mapped
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05059: assert failed: not in kernel
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05060: SGA not created
Cause: After you run the `STARTUP` command, the SGA shared memory pool could not be created.

Action: Verify that you are not trying to start the database while it is running and that the database system id is not being used for two different databases. Otherwise, contact the Oracle Support Services Representative.

<!-- -->

ORA-05061: SGA attach failed
Cause: Connection to the SGA shared memory pool could not be established. This may have happened if you used the wrong system id, or if the database you expected to be running is not running.

Action: Verify that it is not one of the preceding causes (check with the Database Administrator). Otherwise, contact the Oracle Support Services Representative.

<!-- -->

ORA-05063: SGA base invalid
Cause: An invalid value has been specified for the `SGA_BASE` parameter in the `ORAENV` file.

Action: This value is not normally needed. If specified, it must be a value giving the full virtual address for the SGA memory pool. Correct the value and run the `STARTUP` command.

<!-- -->

ORA-05064: cannot allocate SGA
Cause: After creating the memory pool, the `REQMP` to allocate the space failed. This might be an operating system error.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05065: SGA not deleted
Cause: When attempting to detach from the SGA, the `DISMP` system macro returned an error.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05066: SGA address space conflict
Cause: The SGA cannot be placed at the requested address range, because the range is already partly used. The SGA start address is defined by the `ORAENV` variable, `SGA_BASE`; its size is determined by various initialization file parameters such as processes, buffers, and so on.

Action: Refer to [“Memory Architecture”](concepts-and-architecture.md) and adjust the relevant initialization file and `ORAENV` variables. Check the address space limit of the DBA user ID. Contact the System Administrator to find out about shared subsystems and their placement in the address space. Ensure that you do not overlap with the Oracle Database kernel.

<!-- -->

ORA-05067: SGA: address space saturation
Cause: When the SGA is being allocated, the operating system reported that the virtual address space is saturated.

Action: Contact the System Administrator about paging area size and current overall system load.

<!-- -->

ORA-05068 SGA still active, should not be
Cause: When the SGA is being created during startup, it is found that the SGA memory pool is still in use, although the databases should be shut down. This may be caused by a hanging user task, or a network server task.

Action: Check for such hanging tasks. Cancel these tasks, and then restart the database.

<!-- -->

ORA-05069: Unexpected SGA memory pool problem
Cause: The `ENAMP` macro returned an unexpected error code.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05070: cannot enable TPA ser.item
Cause: Probable operating system error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05071: cannot ENQ on TPA ser.item
Cause: Probable operating system error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05072: cannot enable post/wait item
Cause: Probable operating system error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05073: error in post
Cause: An inter-process communication operation failed.

Action: Check that the database and all required background tasks are running correctly. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05074: error in wait
Cause: An inter-process communication operation failed.

Action: Check that the database and all required background tasks are running correctly. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05075: error in task table manager
Cause: Internal error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05076: error setting spid
Cause: Probable operating system error.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05077: cannot enable HIA event
Cause: Probable operating system error. The HIA (Here I Am) event item is used to check the successful start of an Oracle Database process.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05078: create process failure
Cause: When you issued the `STARTUP` command, a background job could not be started successfully.

Action: Check for the job scheduling problems and that any `BGJPAR` entry in the `ORAENV` file is correct. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05079: internal asynchronous IO error
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05107: POSIX environment variable \<variablename\> not defined
Cause: The specified environment variable is not defined.

Action: Define and export the requested variable in your profile.

<!-- -->

ORA-05108: failed to process BS2000 command \<bs2-command\>
Cause: The BS2000 command processor cannot execute the command.

Action: Test the logged command in the POSIX shell using the POSIX command, `bs2cmd`.

<!-- -->

ORA-05109: failed to initialize environment for POSIX
Cause: An application running under the POSIX shell cannot create links to required files in the BS2000 file system.

Action: Check if the environment variables required for Oracle Database applications under POSIX are set properly.

<!-- -->

ORA-05110: cannot attach to memory pool
Cause: Invalid pool ID parameter` xxx`\_`MPID` or operating system error.

Action: Check the `ORAENV` parameter `xxx`\_`MPID`, at most 4 characters of the set \[A...Z\],\[0...9\]), or contact the Oracle Support Services Representative.

<!-- -->

ORA-05111: error attaching to memory pool
Cause: This error mostly occurs due to an address space conflict. The two low significant bytes of the SOSD error show the return code of the ENAMP macro. For example, 1804.

Action: Refer to the manual Executive Macros of the Fujitsu BS2000 operating system released on the Fujitsu manual server.

This manual contains a description of the SOSD error. This problem usually can be resolved by using a higher base address.

<!-- -->

ORA-05112: error creating memory pool
Cause: This error mostly occurs due to an address space conflict. The two low significant bytes of the SOSD error show the return code of the ENAMP macro. For example, 1804.

Action: Refer to the manual Executive Macros of the Fujitsu BS2000 operating system released on the Fujitsu manual server.

This manual contains a description of the SOSD error. This problem usually can be resolved by using a higher base address

<!-- -->

ORA-05114: bad pool base
Cause: An invalid value for the base address parameter of the shared pool, that is, `CLN_BASE, COM_BASE`, and so on has been specified in the `ORAENV` file.

Action: If this value is specified, it must be a value giving the full virtual address for the base address of a memory pool. Correct the value and restart the database.

<!-- -->

ORA-05116: cannot load shared code into pool
Cause: Shared code could not be loaded into the specified memory pool. The two low significant bytes of the SOSD error show the main return code of the BIND macro, for example, x'0198'.

Action: Refer to the manual Executive Macros of the Fujitsu BS2000 operating system released on the Fujitsu manual server for a description of the SOSD error.

<!-- -->

ORA-05117: cannot attach to socket subsystem
Cause: An application could not be bound to the sockets subsystem. Generally this message is preceded by a BLS-nnnn message from the operating system.

Action: Use the BS2000 command` 'SHOW-SUBSYSTEM-STATUS SOC6'` to verify that the sockets subsystem SOC6 is created.

<!-- -->

ORA-05118: ORACLE PCD slot not accessible
Cause: The current task is trying to attach to the ORACLE PCD slot but cannot find this slot.

This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05119: module verification failed
Cause: The version of the shared loaded module does not match the version of the connection module on the user side.

Action: Mostly this error occurs with user applications. In this case re-link the application with the Oracle Database release in use.

<!-- -->

ORA-05120: waiting for shared module to be loaded timed out
Cause: This is an internal error and should not normally occur.

Action: Set the environment Variable `OSDDBG=INI` and re-start the program. The error and the involved memory pool name will be logged. Ask your BS2000 system administrator if the associated memory pool is locked by a foreign task or user.

<!-- -->

ORA-05121: waiting for initialization of shared module timed out
Cause: This is an internal error and should not normally occur.

Action: Set the environment Variable `OSDDBG=INI` and re-start the program. The error and the involved memory pool name will be logged. Ask your BS2000 system administrator if the associated memory pool is locked by a foreign task or user.

<!-- -->

ORA-05126: Missing IT0PCD address
Cause: The `ILCS` run-time link-library is probably missing.

Action: Contact the System Administrator.

<!-- -->

ORA-05161: TCP/IP can't perform asynchronous test on break socket.
Cause: Select on break socket failed.

Action: Contact the System Administrator about TCP/IP networking problems. If the error persists, contact the Oracle Support Services Representative.

<!-- -->

ORA-05165: function not supported
Cause: Either Oracle Database or BS2000 does not support this function.

Action: None.

<!-- -->

ORA-05167: Defect in data buffer
Cause: This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05170: SID not defined (ORAENV file missing?)
Cause: The system identifier, data base name, is not defined when needed during Oracle Database program initialization. A missing `ORAENV` file or a missing `ORASID` entry in that file could cause this error.

Action: Ensure that the `ORAENV` file definition is correct and re-run the program.

<!-- -->

ORA-05173: bad kernel size
Cause: An invalid value for the `KNL_SIZE` parameter has been specified in the `ORAENV` file.

Action: You should not normally need to specify this variable, as the default value is correct. Contact the Oracle Support Services Representative.

<!-- -->

ORA-05174: bad kernel base
Cause: An invalid value for the `KNL_BASE` parameter has been specified in the `ORAENV` file.

Action: If this value is specified, then it must be a value giving the full virtual address for the kernel memory pool. Correct the value and restart the database.

<!-- -->

ORA-05175: Kernel address space conflict
Cause: The Oracle Database kernel cannot be placed at the requested address range, because the range is already used. The kernel start address is defined by the `ORAENV` parameter, `KNL_BASE`.

Action: Refer to [Memory Architecture](concepts-and-architecture.md) and adjust the relevant initialization file and `ORAENV` parameters. Check the address space limit of the DBA user ID. Contact the System Administrator to learn about shared subsystems and their placement in the address space.

<!-- -->

ORA-05176: Kernel: address space saturation
Cause: When the Oracle Database kernel memory pool was being allocated, the operating system signalled that the virtual address space is currently saturated.

Action: Contact the System Administrator about paging area size and current overall system load.

<!-- -->

ORA-05177: Unexpected Kernel memory pool problem
Cause: The `ENAMP` macro returned an unexpected error code.

Action: Refer to the `ENAMP` macro description in the BS2000 documentation for possible reasons. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05178: Kernel module not yet initialized
Cause: The current task is trying to attach to an Oracle Database kernel which is not yet completely initialized. This can only happen if you try to connect to a database, which is just being started.

Action: Retry after a while. Remember that it may take a few minutes until a database is fully running and ready for the users. If the error persists, then check this issue with the Database Administrator.

<!-- -->

ORA-05181: load/init problem with PRO/OCI interface
Cause: The user-side stub module could not load the PRO/OCI module. In this case, the message is usually preceded by a BS2000 BLS-`nnnn` message, or the loaded module is incompatible with the version of the stub module.

Action: Ensure that the `ORALOAD` link name exists and points to the current `ORALOAD` library. Re-link the application with the current link libraries.

<!-- -->

ORA-05191: symbol translation error for kernel memory pool
Cause: The logical name translation for the kernel memory pool failed. Normally, this indicates an invalid system id, `ORASID` in the `ORAENV` file.

Action: Ensure that the `ORAENV` file definition is correct. Otherwise, contact the Oracle Support Services Representative.

<!-- -->

ORA-05192: cannot create/attach kernel memory pool
Cause: The memory pool for the Oracle Database kernel code could not be enabled. In a user program, a possible cause is that the user program already allocates part of the address range needed for the memory pool.

Action: Ensure that the user program does not request storage excessively, and that any `SGA_BASE` and `KNL_BASE` parameters in the `ORAENV` file are consistent. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05193: Symbol translation error for kernel module or load library
Cause: The logical-name translation for the kernel module or load library failed. This is an internal error and should not normally occur.

Action: Contact the Oracle Support Services Representative.

<!-- -->

ORA-05194: cannot load kernel
Cause: The kernel could not be loaded into the kernel memory pool. In most cases, this message is preceded by a `BLS`-`nnn` message from the operating system.

Action: Ensure that the `ORALOAD` link name identifies the correct `ORALOAD` library, and that the `ORAENV` variable, `KNL_MODULE`, names one of the possible kernels. Then re-issue the` STARTUP` command. If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05195: bad or missing kernel connector
Cause: The loaded kernel could not verify its user-side connector module. This can occur if you use an incorrect kernel version.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05198: associated internal OSD error code %d
Cause: This message precedes ORA-05199, if there is more information available. The first 4 hexadecimal digits can often identify the module, and the last 4 hexadecimal digits are usually a condensed version of an associated system macro code. This code can be helpful in diagnosing the problem.

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.

<!-- -->

ORA-05199: ORACLE ABNORMAL EXIT
Cause: A fatal error occurred, which prevents continuation of execution. In many cases, a preceding message explains the error. The system causes the program execution to stop (`TERM ABNORMAL` with `DUMP` is displayed).

Action: If you cannot identify the cause of the problem, then contact the Oracle Support Services Representative.
