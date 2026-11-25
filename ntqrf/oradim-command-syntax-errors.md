`ORADIM` is a command-line tool for starting and stopping database instances that is only available on Oracle Database for Windows.

It is not available on any other platform.

| Oradim Errors | DIM-0000 to DIM-00228                                                                              |
|:--------------|:---------------------------------------------------------------------------------------------------|
| 00000         | ORADIM completed with no errors                                                                    |
| 00001         | ORADIM: \<command\> \[options\]. Refer to manual.                                                  |
| 00002         | The specified command was invalid.                                                                 |
| 00003         | An argument is missing for the parameter                                                           |
| 00004         | SID or service name was not specified.                                                             |
| 00005         | SID with more than 64 characters specified.                                                        |
| 00006         | Missing SID                                                                                        |
| 00007         | Missing or invalid `-`STARTMODE parameter. Valid `-`STARTMODE parameter is AUTO or MANUAL.         |
| 00008         | A valid service name is OracleService appended with a SID                                          |
| 00009         | SID name is mandatory.                                                                             |
| 00010         | `SYSTEM\CurrentControlSet\Services\OracleService` key does not exist.                              |
| 00011         | The specified service does not exist.                                                              |
| 00012         | A PFILE is necessary for AUTOSTART option.                                                         |
| 00013         | Service start mode could not be set in the registry.                                               |
| 00014         | Cannot open the Windows Service Control Manager.                                                   |
| 00015         | Cannot start already-running ORACLE - shut it down first.                                          |
| 00016         | Missing or invalid `-`SHUTTYPE parameter. A valid `-`SHUTTYPE parameter is SRVC or INST.           |
| 00017         | Instance shutdown mode must be one of the following: a for abort, i for immediate or n for normal. |
| 00018         | Failed to stop Oracle Service.                                                                     |
| 00019         | Create Service Error.                                                                              |
| 00020         | A service for this name exists.                                                                    |
| 00021         | Registry open failed.                                                                              |
| 00040         | Invalid option for the -NEW command.                                                               |
| 00041         | Invalid option for the -EDIT command.                                                              |
| 00042         | Invalid option for the -DELETE command.                                                            |
| 00043         | Invalid option for the -STARTUP command.                                                           |
| 00044         | Invalid option for the -SHUTDOWN command.                                                          |
| 00045         | Internal error in ORADIM.                                                                          |
| 00046         | Invalid Pfile.                                                                                     |
| 00050         | Instance deleted.                                                                                  |
| 00051         | Instance created.                                                                                  |
| 00075         | Failed to control service.                                                                         |
| 00076         | Failed to delete service.                                                                          |
| 00077         | Failed to change service configuration.                                                            |
| 00078         | Failed to start service.                                                                           |
| 0090          | SID name is invalid.                                                                               |
| 0092          | Unable to determine Oracle service user.                                                           |
| 0093          | Invalid option for the -ACL command.                                                               |
| 0094          | Failed to change ACLs on the object.                                                               |
| 00200         | Enter one of the following commands:                                                               |
| 00201         | Create an instance by specifying the following options:                                            |
| 00202         | -NEW -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \| -APXSID sid\|                     |
| 00203         | -SRVC srvc \| -ASMSRVC srvc \| -MGMTDBSRVC srvc \| -IOSSRVC srvc \|                                |
| 00204         | -APXSRVC srvc \[-SYSPWD pass\] \[-STARTMODE auto\|manual\]                                         |
| 00205         | \[-SRVCSTART system\|demand\] \[-PFILE file \| -SPFILE\]                                           |
| 00206         | \[-SHUTMODE normal\|immediate\|abort\] \[-TIMEOUT secs\] \[-RUNAS osusr/ospass\]                   |
| 00207         | Edit an instance by specifying the following options:                                              |
| 00208         | -EDIT -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \| -APXSID sid                      |
| 00209         | \[-SYSPWD pass\] \[-STARTMODE auto\|manual\] \[-SRVCSTART system\|demand\]                         |
| 00210         | \[-PFILE file \| -SPFILE\] \[-SHUTMODE normal\|immediate\|abort\]                                  |
| 00211         | \[-SHUTTYPE srvc\|inst\] \[-RUNAS osusr/ospass\]                                                   |
| 00212         | Delete instances by specifying the following options:                                              |
| 00213         | -DELETE -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \|                                |
| 00214         | -APXSID sid\| -SRVC srvc \| -ASMSRVC srvc \| -MGMTDBSRVC srvc \|                                   |
| 00215         | -IOSSRVC srvc \| -APXSRVC srvc                                                                     |
| 00216         | Startup services and instance by specifying the following options:                                 |
| 00217         | -STARTUP -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid                                  |
| 00218         | \| -APXSID sid \[-SYSPWD pass\] \[-STARTTYPE srvc\|inst\|srvc,inst\]                               |
| 00219         | \[-PFILE filename \| -SPFILE\]                                                                     |
| 00220         | Shutdown service and instance by specifying the following options:                                 |
| 00221         | -SHUTDOWN -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \|                              |
| 00222         | -APXSID sid \[-SYSPWD pass\] \[-SHUTTYPE srvc\|inst\|srvc,inst\]                                   |
| 00223         | \[-SHUTMODE normal\|immediate\|abort\]                                                             |
| 00224         | Manipulate ACLs by specifying the following options:                                               |
| 00225         | -ACL -setperm\|-addperm\|-removeperm dbfiles\|diag\|registry                                       |
| 00226         | -USER username -OBJTYPE file\|dir\|registry -OBJPATH object-path                                   |
| 00227         | -RECURSE true\|false \[-HOST hostname\]                                                            |
| 00228         | Query for help by specifying the following parameters: -? \| -h \| -help                           |

DIM-00000
ORADIM completed with no errors.

Cause: The specified operation completed successfully.

Action: None.

DIM-00001
ORADIM: \<command\> \[options\]. Refer to manual.

Cause: The specified options were invalid or no arguments were supplied.

Action: Usage: ORADIM \<command\> \[options\]

DIM-00002
The specified command was invalid.

Cause: Valid commands are: -DELETE, -EDIT, -NEW, -STARTUP, and -SHUTDOWN.

Action: Use valid command.

DIM-00003
An argument is missing for the parameter.

Cause: Missing or invalid argument.

Action: Use a valid argument and run the program again.

DIM-00004
SID or service name was not specified.

Cause: Either a SID or service name is mandatory.

Action: Enter a valid `SID` of 64 characters and retry.

DIM-00005
SID with more than 64 characters specified.

Cause: SID with more than 64 characters specified.

Action: Change SID to 64 unique characters and ensure that there is no other service with this name.

DIM-00006
Missing SID.

Cause: SID was not specified in the arguments.

Action: Specify a SID.

DIM-00007
Missing or invalid -STARTMODE parameter. Valid -STARTMODE parameter is AUTO or MANUAL.

Cause: An argument for STARTMODE is missing.

Action: Enter a valid start mode and retry.

DIM-00008
A valid service name is OracleService appended with a SID

Cause: The Oracle service name specified is invalid.

Action: Correct the name of service and retry.

DIM-00009
SID name is mandatory.

Cause: SID was not specified.

Action: Enter the SID and retry.

DIM-00010
SYSTEM\CurrentControlSet\Services\OracleService key does not exist.

Cause: Specified registry key was not found.

Action: Try reinstalling. If the problem persists, contact Oracle Support Services.

DIM-00011
The specified service does not exist.

Cause: An attempt to edit a service failed.

Action: Make sure the service exists or user has enough privileges.

DIM-00012
A PFILE is necessary for AUTOSTART option.

Cause: A parameter file {PFILE} was not specified.

Action: Specify a parameter file.

DIM-00013
Service start mode could not be set in the registry.

Cause: The start mode entry in the registry for the service could not be set.

Action: Check if the user has privileges to modify registry.

DIM-00014
Cannot open the Windows Service Control Manager.

Cause: The Service Control Manager could not be opened.

Action: Check for user privileges.

DIM-00015
Cannot start already-running ORACLE - shut it down first.

Cause: The instance is already started.

Action: Stop the database before restarting.

DIM-00016
Missing or invalid -SHUTTYPE parameter. A valid -SHUTTYPE parameter is SRVC or INST.

Cause: An option for SHUTTYPE was missing or invalid.

Action: Enter parameter to shut down the instance or the service and retry.

DIM-00017
Instance shutdown mode must be one of the following: a for abort, i for immediate or n for normal.

Cause: Invalid option to shut down the instance was specified.

Action: Enter the correct mode and retry.

DIM-00018
Failed to stop Oracle Service.

Cause: An attempt to stop the service failed.

Action: Retry, check for user privileges.

DIM-00019
Create service error.

Cause: Service could not be created.

Action: Check for user privileges and retry.

DIM-00020
A service for this name exists.

Cause: An attempt was made to create a service name when it already existed.

Action: Retry with a different service name or SID.

DIM-00021
Registry open failed

Cause: An attempt to open the registry failed.

Action: Check for user privileges and retry the operation.

DIM-00040
Invalid option for the -NEW command.

Cause: One or more arguments for creating new service is invalid.

Action: Specify required option and retry.

DIM-00041
Invalid option for the -EDIT command.

Cause: One or more arguments for editing existing service is invalid.

Action: Specify required option and retry.

DIM-00042
Invalid option for the -DELETE command.

Cause: One or more arguments for deleting service is invalid.

Action: Specify required option and retry.

DIM-00043
Invalid option for the -STARTUP command.

Cause: One or more arguments for starting the instance is invalid.

Action: Specify required option and retry.

DIM-00044
Invalid option for the -SHUTDOWN command.

Cause: One or more arguments for shutting down the instance is invalid.

Action: Specify required option and retry.

DIM-00045
Internal error in ORADIM

Cause: Unknown.

Action: Contact Oracle Support Services.

DIM-00046
Invalid Pfile.

Cause: The parameter file name is invalid.

Action: Check that the path name is correct.

DIM-00050
Instance deleted

Cause: The request for deleting instance was successful.

Action: None.

DIM-00051
Instance created.

Cause: The request for creating new instance was successful.

Action: None.

DIM-00075
Failed to control service.

Cause: An attempt to control the service failed.

Action: Check additional error, ensure that user has enough privileges.

DIM-00076
Failed to delete service.

Cause: The request for service deletion failed.

Action: Check additional error, ensure that user has enough privileges.

DIM-00077
Failed to change service configuration.

Cause: An attempt to change configuration failed.

Action: Check additional error, ensure that user has enough privileges.

DIM-00078
Failed to start service.

Cause: The request to start service failed.

Action: Check additional error, ensure that user has enough privileges.

DIM-00090
SID name is invalid.

Cause: An invalid SID name was provided.

Action: Enter a valid SID name with no more that 64 characters (alphanumeric) and retry.

DIM-00092
Unable to determine Oracle service user.

Cause: This is an internal Error. The Oracle service user could not be determined for this Oracle home.

Action: Contact Oracle Support Services.

DIM-00093
Invalid option for the -ACL command.

Cause: One or more options for setting ACLs was invalid.

Action: Specify the required option and retry.

DIM-00094
Failed to change ACLs on the object.

Cause: An attempt to change the ACLs on the object failed.

Action: Check additional errors. Make sure that the user has enough privileges.

DIM-00200
Enter one of the following commands:

Cause: Unknown.

Action: None.

DIM-00201
Create an instance by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00202
-NEW -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \| -APXSID sid\|

Cause: Unknown.

Action: None.

DIM-00203
-SRVC srvc \| -ASMSRVC srvc \| -MGMTDBSRVC srvc \| -IOSSRVC srvc \|

Cause: Unknown.

Action: None.

DIM-00204
-APXSRVC srvc \[-SYSPWD pass\] \[-STARTMODE auto\|manual\]

Cause: Unknown.

Action: None.

DIM-00205
\[-SRVCSTART system\|demand\] \[-PFILE file \| -SPFILE\]

Cause: Unknown.

Action: None.

DIM-00206
\[-SHUTMODE normal\|immediate\|abort\] \[-TIMEOUT secs\] \[-RUNAS osusr/ospass\]

Cause: Unknown.

Action: None.

DIM-00207
Edit an instance by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00208
-EDIT -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \| -APXSID sid

Cause: Unknown.

Action: None.

DIM-00209
\[-SYSPWD pass\] \[-STARTMODE auto\|manual\] \[-SRVCSTART system\|demand\]

Cause: Unknown.

Action: None.

DIM-00210
\[-PFILE file \| -SPFILE\] \[-SHUTMODE normal\|immediate\|abort\]

Cause: Unknown.

Action: None.

DIM-00211
\[-SHUTTYPE srvc\|inst\] \[-RUNAS osusr/ospass\]

Cause: Unknown.

Action: None.

DIM-00212
Delete instances by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00213
-DELETE -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \|

Cause: Unknown.

Action: None.

DIM-00214
-APXSID sid\| -SRVC srvc \| -ASMSRVC srvc \| -MGMTDBSRVC srvc \|

Cause: Unknown.

Action: None.

DIM-00215
-IOSSRVC srvc \| -APXSRVC srvc

Cause: Unknown.

Action: None.

DIM-00216
Startup services and instance by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00217
-STARTUP -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid

Cause: Unknown.

Action: None.

DIM-00218
\| -APXSID sid \[-SYSPWD pass\] \[-STARTTYPE srvc\|inst\|srvc,inst\]

Cause: Unknown.

Action: None.

DIM-00219
\[-PFILE filename \| -SPFILE\]

Cause: Unknown.

Action: None.

DIM-00220
Shutdown service and instance by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00221
-SHUTDOWN -SID sid \| -ASMSID sid \| -MGMTDBSID sid \| -IOSSID sid \|

Cause: Unknown.

Action: None.

DIM-00222
-APXSID sid \[-SYSPWD pass\] \[-SHUTTYPE srvc\|inst\|srvc,inst\]

Cause: Unknown.

Action: None.

DIM-00223
\[-SHUTMODE normal\|immediate\|abort\]

Cause: Unknown.

Action: None.

DIM-00224
Manipulate ACLs by specifying the following options:

Cause: Unknown.

Action: None.

DIM-00225
-ACL -setperm\|-addperm\|-removeperm dbfiles\|diag\|registry

Cause: Unknown.

Action: None.

DIM-00226
-USER username -OBJTYPE file\|dir\|registry -OBJPATH object-path

Cause: Unknown.

Action: None.

DIM-00227
-RECURSE true\|false \[-HOST hostname\]

Cause: Unknown.

Action: None.

DIM-00228
Query for help by specifying the following parameters: -? \| -h \| -help

Cause: None.

Action: None.

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
