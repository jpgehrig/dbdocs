These topics describe the steps that are required to develop and deploy a .NET stored procedure or function into an Oracle Database.

- Step 1: Develop the Stored Procedure or Function and Build it into an Assembly

- Step 2: Run the Oracle Deployment Wizard for .NET

- Step 3: Choose the Procedure or Function to Deploy and Security Level

- Step 4: Determine the Appropriate Parameter Type Mappings

- Step 5: Deploy the Procedure or Function

- Step 6: Test the Procedure or Function

- Step 7: Debug the Procedure or Function

### Step 1: Develop the Stored Procedure or Function and Build it into an Assembly

Write the stored procedure or function using Microsoft Visual Studio with an appropriate .NET language.

Use Oracle Data Provider for .NET (`Oracle.DataAccess.Client` and `Oracle.DataAccess.Types`) in a .NET stored procedure or function to provide data access.

Build the stored procedure or function into an assembly as a DLL, and not as an EXE. This is typically accomplished using a Class Library project.

Keep in mind the Oracle Data Provider for .NET limitations and restrictions, especially concerning connections and transactional semantics, when designing and developing a .NET procedure or function that uses data access.

### Step 2: Run the Oracle Deployment Wizard for .NET

Run Oracle Deployment Wizard for .NET from Microsoft Visual Studio. Oracle Deployment Wizard for .NET is installed as part of the Oracle Developer Tools for Visual Studio. This wizard requires `SYSDBA` credentials, the name of the assembly to be deployed, and the database it is being deployed to.

### Step 3: Choose the Procedure or Function to Deploy and Security Level

Choose the procedure or function to be deployed when the Oracle Deployment Wizard for .NET displays the list of methods for that assembly.

Also, choose the security level.

Oracle Database Extensions for .NET executes .NET stored procedures or functions at a specific security level. The security level dictates the Code Access Permissions granted to a .NET stored procedure or function. By default, .NET stored procedures or functions are executed with the SAFE security level.

The security levels are:

- Safe

  In Safe level, the .NET stored procedure or function is allowed to access only database resources. Access to any external resources such as local files, networks, and so on, is not allowed.

- External

  In External level, the .NET stored procedure or function is allowed to read or write to local files, and to access network resources such as sockets and internet nodes, and so on.

- Unsafe

  In Unsafe level, the .NET stored procedure or function is allowed unrestricted execution including execution of unmanaged code. It is a superset of all other security levels.

**Note:**

If ODP.NET is installed with non-machine wide configuration, then .NET stored procedures will need to be deployed and configured with the 'Unsafe' security level.

**See Also:**

"[Step 3: Choose the Function to Deploy](demo.md)" for the process of entering security level

### Step 4: Determine the Appropriate Parameter Type Mappings

Determine the correct mapping between .NET and Oracle data types for creating a PL/SQL wrapper for the .NET stored procedure or function. The Oracle Deployment Wizard for .NET provides default mappings, but they can be overridden.

In case of overloaded .NET stored procedures or functions, you need to provide distinct names for the PL/SQL wrappers.

Tables in Appendix A provides conversion information.

**See Also:**

"[Data Type Conversion](datatype-conversion.md)"

### Step 5: Deploy the Procedure or Function

Deploy the procedure or function in the database. The wizard performs the following steps:

1.  Connects as `SYSDBA`.
2.  Copies the user assembly to the `ORACLE_BASE\\ORACLE_HOME``\bin\CLR` directory or its subdirectory.
3.  Creates an Oracle library object and grants execute privilege on this library object to the database user:
        CREATE OR REPLACE LIBRARY CLRLIBRARY1_DLL AS '$ORACLE_HOME\
            bin\clr\CLRLibrary1_dll;
        GRANT EXECUTE ON CLRLIBRARY1_DLL TO SCOTT;
4.  Creates a PL/SQL wrapper in the user's database schema for each procedure or function, according to the parameter type mappings defined by the user.

### Step 6: Test the Procedure or Function

Test the .NET stored procedure or function by calling the PL/SQL wrapper.

The PL/SQL wrapper can be located and executed easily using Oracle Developer Tools for Visual Studio, or from a tool like SQL\*Plus.

### Step 7: Debug the Procedure or Function

Whenever a .NET stored procedure or function is invoked, the Oracle database listener redirects the request to a multithreaded CLR external procedure agent, `extproc.exe`. Each .NET stored procedure or function is executed in the context of the `extproc.exe` process.

1.  Ensure that the debug versions of the .NET assembly representing the .NET stored procedure or function and its `pdb` file and dependency DLLs, and their respective `pdb` files are copied to the `ORACLE_BASE\\ORACLE_HOME``\bin\clr` directory or one of its subdirectories, based on the path provided while creating the library.
2.  Attach the debugger to the `extproc.exe` process. Note that the debugger should be capable of debugging .NET code. If Visual Studio is used for debugging, select the Native and Common Language Runtime options in the Attach to Process dialog box. The Native option can be deselected if any .NET stored procedure has already been run in the context of the same `extproc.exe` process.
3.  When the debugger is attached, open the .NET stored procedure or function source code and set any breakpoints that are needed, at the required locations.
4.  Debug the .NET stored procedure.

**Note:**

You can use Oracle Data Provider for .NET tracing mechanism to troubleshoot application issues. Please see Debug Tracing section in[ Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/features.md).
