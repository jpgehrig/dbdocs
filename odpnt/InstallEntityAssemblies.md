ODP.NET now ships with a separate assembly to support Code First and Entity Framework 6. This functionality resides in a dedicated assembly, while the ADO.NET and earlier Entity Framework version functionality resides in the main ODP.NET assembly. This model physically separates Entity Framework 6 functionality from ADO.NET functionality.

This ODP.NET assembly is:

- `Oracle.DataAccess.EntityFramework.dll` for ODP.NET, Unmanaged Driver.

- `Oracle.ManagedDataAccess.EntityFramework.dll` for ODP.NET, Managed Driver.

Whether it is installed using the Oracle Universal Installer or the XCopy package, the Oracle Entity Framework assemblies may be found in the following location after install (where `%ORACLE_HOME%` represents the operating system path to the installation directory):

For Unmanaged Driver:

`%ORACLE_HOME%\odp.net\bin\4\EF6\Oracle.DataAccess.EntityFramework.dll`

For Managed Driver:

`%ORACLE_HOME%\odp.net\managed\common\EF6\Oracle.ManagedDataAccess.EntityFramework.dll`

Both assemblies are compiled as Any CPU and therefore there is no need for separate 32-bit and 64-bit versions of the assemblies. Each assembly is designed to be `bin deployable` meaning that the assembly should be copied into the application's `bin` directory. As such the assemblies are not registered in the Global Assembly Cache (GAC) during installation.

**Note:**

If desired the Oracle Entity Framework 6 assemblies may be registered in the GAC manually but Oracle recommends not doing so.
