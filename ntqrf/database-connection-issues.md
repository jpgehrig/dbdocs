Review database connection issues.

The following are the common Oracle Database connection error codes, their causes, and suggested remedies.

TNS-12203
TNS: unable to connect to destination

Cause: OracleServiceSID service, OracleHOMENAMETNSListener service, or both are not running.

Action: Ensure that both services are started.

ORA-12560
TNS: lost contact

Cause: OracleServiceSID service, OracleHOMENAMETNSListener service, or both are not running. You receive this error if you attempt to use any Oracle Database utilities, such as SQL\*Plus. This error is analogous to the following Oracle7 error: `ORA-09352:` `Windows` `32-bit` `Two-Task` `driver` `unable` `to spawn` `new` `ORACLE` `task`.

Action: Ensure that both services are started.

ORA-28575
unable to open RPC connection to external procedure agent

Cause: `tnsnames.ora `and `listener.ora` files have not been correctly configured to use external procedures.

Action: Reconfigure services.

ORA-06512
at "APPLICATIONS.OSEXEC", line 0

Cause: `tnsnames.ora `and listener.ora` `files have not been correctly configured to use external procedures.

Action: Reconfigure services.

ORA-06512
at "APPLICATIONS.TEST", line 4

Cause: `tnsnames.ora `and `listener.ora `files have not been correctly configured to use external procedures.

Action: Reconfigure services.

ORA-06512
at line 2

Cause: `tnsnames.ora `and `listener.ora `files have not been correctly configured to use external procedures.

Action: Reconfigure services.

ORA-01031 and LCC-00161
Both codes appear at startup

Cause: Parameter file (init.ora) or Windows services are damaged. These errors usually appear when the parameter file cannot be read by Oracle Database at database startup.

Action: Delete and re-create the SID and services. Make sure you are logged on as the user Administrator, or a user within the Windows Administrator's Group with full administrative rights. At the command prompt, enter: `oradim -delete -sid ``sid` where `sid` is the name of your database (for example, `orcl`). Re-create the SID and services by entering: `oradim -new -sid ``sid`` -startmode auto -pfile ``full_path_to_init.ora`

**Parent topic:** [Error Messages on Windows](error-messages-on-windows.md)
