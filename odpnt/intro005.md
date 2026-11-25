The following is a simple C# application that connects to Oracle Database and displays its version number before disconnecting using ODP.NET, Unmanaged Driver:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class Sample
    {
      static void Main()
      {
        // Connect to Oracle
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Display Version Number
        Console.WriteLine("Connected to Oracle " + con.ServerVersion);

        // Close and Dispose OracleConnection
        con.Close();
        con.Dispose();
      }
    }

If you are using ODP.NET, Managed Driver or ODP.NET Core, then replace the contents of `Program.cs` with the following C# code. The namespace of ODP.NET, Managed Driver (`Oracle.ManagedDataAccess.*`) is different from the namespace of ODP.NET, Unmanaged Driver (`Oracle.DataAccess.*`)

    // C#
    using System;
    using Oracle.ManagedDataAccess.Client;
    using Oracle.ManagedDataAccess.Types;

    namespace Connect
    {
      class Program
      {
        static void Main(string[] args)
        {
          try
          {
            // Please replace the connection string attribute settings
            string constr = "user id=scott;password=tiger;data source=oracle";

            OracleConnection con = new OracleConnection(constr);
            con.Open();
            Console.WriteLine("Connected to Oracle Database {0}", con.ServerVersion);
            con.Dispose();

            Console.WriteLine("Press RETURN to exit.");
            Console.ReadLine();
          }
          catch (Exception ex)
          {
            Console.WriteLine("Error : {0}", ex);
          }
        }
      }
    }

**Note:**

Additional samples are provided in the `ORACLE_BASE``\``ORACLE_HOME``\``ODACsamples` directory from Oracle Universal Installer ODAC installations. Microsoft Installer (MSI) ODAC installations include managed ODP.NET samples in the Oracle Developer Tools for Visual Studio subdirectory usually located in the `C:\Program Files (x86)` directory.
