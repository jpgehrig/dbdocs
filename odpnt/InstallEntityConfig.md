Developers must configure applications to use the Oracle Entity Framework functionality. This consists of creating two entries in the `app.config` or `web.config` file and adding an assembly reference:

- Add entries in the .NET config file

  - Connection string

    A standard ADO.NET connection string is used rather than the Entity Framework connection string used by Database First or Model First paths. The connection string name should match the application context name. The connection string entry is an element of the `connectionStrings` section in the configuration file.

  - Provider registration

    Entity Framework uses the provider registration to determine the assembly to use for Oracle Entity Framework functionality. The provider registration is an element of the `providers` section within the `entityFramework` section in the application configuration file.

- Add Assembly reference

  Add Oracle Entity Framework assembly to the project references.

**Note:**

When using the official ODP.NET, NuGet installation, these preceding sections are created automatically, if they do not already exist. After the NuGet install, the ODP.NET connection string will need to be customized to the application's specific settings.

When using the Oracle Universal Installer or xcopy install, the preceding sections must all be configured manually.

Examples of connection strings are as follows:

- ODP.NET, Unmanaged Driver

      <add name="TestContext" providerName="Oracle.DataAccess.Client" connectionString="User Id=test;Password=testpassword;Data Source=eftest" />

- ODP.NET, Managed Driver

      <add name="TestContext" providerName="Oracle.ManagedDataAccess.Client" connectionString="User Id=test;Password=testpassword;Data Source=eftest" />

Examples of Oracle provider registration are as follows:

- ODP.NET, Unmanaged Driver

      <provider invariantName="Oracle.DataAccess.Client" type="Oracle.DataAccess.EntityFramework.EFOracleProviderServices, Oracle.DataAccess.EntityFramework, Version=6.121.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" />

- ODP.NET, Managed Driver

      <provider invariantName="Oracle.ManagedDataAccess.Client" type="Oracle.ManagedDataAccess.EntityFramework.EFOracleProviderServices, Oracle.ManagedDataAccess.EntityFramework, Version=6.121.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" />

### Entity Framework 6 Code-Based Registration

Entity Framework 6 allows an application to register with an Entity Framework provider without using any configuration file. With ODP.NET, Managed Driver, the code will look as follows:

    // C#
    using Oracle.ManagedDataAccess.EntityFramework;
    ...
    public class ModelConfiguration : DbConfiguration
    {
       public ModelConfiguration()
       {
          SetProviderServices("Oracle.ManagedDataAccess.Client", EFOracleProviderServices.Instance);
       }
    }

For ODP.NET, Unmanaged Driver, replace occurrences of `ManagedDataAccess` with `DataAccess` in the preceding code.

If you are using code-based registration, then the configuration file should not include the registration. The configuration file based registration overrides the code-based registration.
