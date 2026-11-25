Error messages in this section are Oracle Database operating system-dependent (OSD) messages displayed in response to an error condition in Windows.

Each message in this section triggers an Oracle Database error message.

Error messages appear first in summary tables consisting of error numbers and the corresponding error message. Following the tables is a more detailed discussion of errors, including causes and corrective actions.

| File I/O Errors: | OSD-04000 to OSD-04099                                           |
|:-----------------|:-----------------------------------------------------------------|
| 4000             | Logical block size mismatch                                      |
| 4001             | Invalid logical block size                                       |
| 4002             | Unable to open file                                              |
| 4003             | Unable to read file header block                                 |
| 4004             | Invalid file header                                              |
| 4005             | SetFilePointer() failure, unable to read from file               |
| 4006             | ReadFile() failure, unable to read from file                     |
| 4007             | Truncated read                                                   |
| 4008             | WriteFile() failure, unable to write to file                     |
| 4009             | Truncated write                                                  |
| 4010             | \<create\> option specified, file already exists                 |
| 4011             | GetFileInformationByHandle() failure, unable to obtain file info |
| 4012             | File size mismatch                                               |
| 4013             | Unable to read line from file                                    |
| 4014             | Unable to close file                                             |
| 4015             | An asynchronous I/O request returned an error                    |
| 4016             | Error queuing an asynchronous I/O request                        |
| 4017             | Unable to open the specified RAW device                          |
| 4018             | Unable to access the specified directory or device               |
| 4019             | Unable to set file pointer                                       |
| 4020             | Unable to set eof file marker                                    |
| 4021             | Unable to read file                                              |
| 4022             | Unable to write file                                             |
| 4023             | SleepEx() failure, unable to Sleep                               |
| 4024             | Unable to delete file                                            |
| 4025             | Invalid question asked                                           |
| 4026             | Invalid parameter passed                                         |

| Memory Errors: | OSD-04100 to OSD-04199                                   |
|:---------------|:---------------------------------------------------------|
| 4100           | malloc() failure, unable to allocate memory              |
| 4101           | Invalid SGA: SGA not initialized                         |
| 4102           | Unable to open/create file for shared memory object      |
| 4103           | Unable to attach to SGA: SGA does not exist              |
| 4104           | Unable to map shared memory (SGA) into the address space |
| 4105           | Shared memory (SGA) mapped to wrong address              |
| 4106           | Unable to allocate memory with VirtualAlloc              |
| 4107           | Unable to deallocate memory with VirtualFree             |
| 4108           | Unable to protect memory with VirtualProtect             |

| Process Errors: | OSD-04200 to OSD-04299                                         |
|:----------------|:---------------------------------------------------------------|
| 4200            | Unable to begin another thread                                 |
| 4201            | No pid structure supplied to spdcr()                           |
| 4202            | DosSetPriority() failure, unable to set process priority       |
| 4203            | DosKillProcess() failure, unable to kill process               |
| 4204            | Invalid pid                                                    |
| 4205            | CreateProcess() failure, unable to spawn process               |
| 4207            | Invalid priority specified in CONFIG parameter ORACLE_PRIORITY |
| 4208            | OpenProcess() failure, unable to open process handle           |
| 4209            | Incorrect or unknown background image name given to spdcr()    |
| 4210            | Timeout waiting for thread semaphore                           |
| 4211            | Thread information not found                                   |
| 4212            | Maximum number of ORACLE threads reached                       |
| 4213            | ORACLE thread unable to DuplicateHandle()                      |
| 4214            | ORACLE thread unable to CreateEvent()                          |
| 4215            | Bad function code supplied to ssthreadop                       |
| 4216            | Unable to find file handle for that thread                     |
| 4217            | Unable to retrieve system username for current user            |
| 4218            | Cannot post thread                                             |
| 4219            | Bad thread list semaphore                                      |
| 4221            | Target thread is currently busy                                |
| 4222            | Unable to get the threads context                              |
| 4223            | Unable to set the threads context                              |
| 4224            | Unable to suspend the target thread                            |
| 4225            | Unable to resume the target thread                             |

| Loader Errors: | OSD-04300 to OSD-04399                        |
|:---------------|:----------------------------------------------|
| 4300           | Unable to read complete record from data file |
| 4301           | Record size too large                         |
| 4302           | Invalid record type, load options, or both    |

| Semaphore Errors: | OSD-04400 to OSD-04499                                    |
|:------------------|:----------------------------------------------------------|
| 4400              | Unable to acquire internal semaphore for process          |
| 4401              | WaitForSingleObject() failure, unable to obtain semaphore |

| Miscellaneous Errors: | OSD-04500 to OSD-04599                                           |
|:----------------------|:-----------------------------------------------------------------|
| 4500                  | Illegal option specified                                         |
| 4501                  | Internal buffer overflow                                         |
| 4502                  | Translations nested too deep                                     |
| 4503                  | Text contains no translatable elements                           |
| 4505                  | stdin not responding                                             |
| 4506                  | Unable to spawn process through system()                         |
| 4510                  | Operating system roles are not supported                         |
| 4511                  | Unable to get date and time from the operating system            |
| 4512                  | Unable to translate the 'USERNAME' config.ora variable on server |
| 4513                  | 'remote_os_authent' init.ora variable not set to true            |
| 4514                  | The Windows Group name is too long for internal buffer           |
| 4515                  | This command is not implemented at this time                     |

- [File I/O Errors: OSD-04000 to OSD-04099](file-io-errors.md)
  Review File I/O errors.
- [Memory Errors: OSD-04100 to OSD-04199](memory-errors.md)
  Review memory errors.
- [Process Errors: OSD-04200 to OSD-04299](process-errors.md)
  Review process errors.
- [Loader Errors: OSD-04300 to OSD-04399](loader-errors.md)
  Review loader errors.
- [Semaphore Errors: OSD-04400 to OSD-04499](semaphore-errors.md)
  Review Semaphore errors.
- [Miscellaneous Errors: OSD-04500 to OSD-04599](miscellaneous-errors.md)
  Review miscellaneous errors.

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
