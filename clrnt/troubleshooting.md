This appendix discusses common errors.

Users may encounter various errors while running the PL/SQL wrapper. Causes and recommended actions for such errors are listed below.

ORA-03113: end-of-file on communication channel
Cause: The connection between Client and Server process was broken. It may also happen if the external agent `extproc` crashes for some reason.

Action: There was a communication error that requires further investigation. First, check for network problems and review the SQL\*Net setup. Also, look in the `alert.log` file for any errors. Finally, test to see whether the server process is dead and whether a trace file was generated at failure time. There may be some system calls in the .NET function which might terminate the process. Remove such calls.

ORA-03114: not connected to ORACLE
Cause: The connection between Client and Server process was broken. This may also happen if the external agent `extproc` crashes for some reason.

Action: There was a communication error which requires further investigation. First, check for network problems and review the SQL\*Net setup. Also, look in the `alert.log` file for any errors. Finally, test to see whether the server process is dead and whether a trace file was generated at failure time. There may be some system calls in the .NET function which might terminate the process. Remove such calls.

ORA-20100: System.BadImageFormatException. The format of the file is invalid.
Cause: The .NET Assembly is not in the proper format.

Action: Fix the .NET assembly format that contains the .NET stored procedures or functions. You need to recompile the .NET assembly.

ORA-20100: System.IO.FileNotFoundException. File or assembly name \<assemblyname\>.dll, or one of its dependencies, was not found.
Cause: The .NET Assembly or one of its dependent assemblies is not available in `ORACLE_BASE\\ORACLE_HOME``\bin\clr` or in one of the subdirectories as specified during the creation of the library object by the wizard.

Action: Copy the .NET assembly and all its dependent assemblies to `ORACLE_BASE\\ORACLE_HOME``\bin\clr` or to one of its subdirectories as appropriate.

ORA-20100: System.MissingMethodException
Cause: `MissingMethodException` is thrown for many possible reasons including:

- The stored procedure or function name does not match the actual stored procedure or function name defined in the .NET assembly.

- The number, sequence, and type of parameters passed do not match the actual parameters in the .NET stored procedure.

Action: Check the name of the called stored procedure or function for spelling mistakes or case mismatch (upper or lower). Check the number of parameters and check that the type and sequence of the parameters match those of the stored procedure or function defined in the .NET assembly.

ORA-20100: System.Reflection.TargetException. \<typename\> type not found
Cause: The namespace and/or the class name used in the PL/SQL wrapper is not defined in the .NET Assembly.

Action: Check the class name for spelling mistakes or case mismatch. Check the .NET assembly code for the type.

ORA-20100: System.Security.SecurityException
Cause: .NET stored procedure or function could not be executed with current security level.

Action: Use the appropriate security level. For example, if the .NET stored procedure or function requires file system access, then it should be created with EXTERNAL security level.

ORA-28575: unable to open RPC connection to external procedure agent
Cause: Initialization of a network connection to the `extproc` agent did not succeed. This problem can be caused by network problems, incorrect listener configuration, or incorrect transfer code.

Action: Check listener configuration in `LISTENER.ORA` and `TNSNAMES.ORA`, or check Oracle Names Server. Verify that the multithreaded `extproc` configuration entries are correct.

ORA-28578: protocol error during callback from an external procedure
Cause: An internal protocol error occurred. This could be due to some registration issue during creation of PL/SQL wrapper.

Action: Recreate the PL/SQL wrapper using the wizard.

PLS-00201: identifier 'DBMS_CLR' must be declared
Cause: Either Oracle Database Extensions for .NET is not installed and configured properly or the .NET stored procedure has not been deployed correctly using the Oracle Deployment Wizard for .NET.

Action: Use the Database Configuration Assistant to configure Oracle Database Extensions for .NET, if it has not been installed already. Deploy the .NET stored procedure using the Oracle Deployment Wizard for .NET.
