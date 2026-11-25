To migrate existing Database First Entity Framework 5 applications to Entity Framework 6, use the following instructions. The first four steps are generic to all Entity Framework applications. The last four steps are specific to Oracle deployments.

1.  Uninstall Entity Framework 5 in Visual Studio Package Manager Console. For example,

    `Uninstall-Package EntityFramework`

2.  Install Entity Framework 6 in Package Manager Console. For example,

    `Install-Package EntityFramework -Version 6.0.2`

    This step adds Entity Framework 6 to the `configSections` entry and adds a new section called `entityFramework`.

3.  Delete the following namespaces from your application:

        // C#
        using System.Data.EntityClient;
        using System.Data.Objects;

4.  Add the following namespaces to your application:

        // C#
        using System.Data.Entity.Core.EntityClient;
        using System.Data.Entity.Core.Objects;

5.  Add the Oracle Entity Framework 6 provider configuration information to the .NET config file in the `providers` section. Modify the ODP.NET version if using a version besides 6.121.2.0. If you installed the ODP.NET NuGet package, you can skip this step as the NuGet install has already added made this change.

        <provider invariantName="Oracle.DataAccess.Client" type="Oracle.DataAccess.EntityFramework.EFOracleProviderServices,Oracle.DataAccess.EntityFramework, Version=6.121.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" />

        <provider invariantName="Oracle.ManagedDataAccess.Client" type="Oracle.ManagedDataAccess.EntityFramework.EFOracleProviderServices,Oracle.ManagedDataAccess.EntityFramework, Version=6.121.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" />

6.  Add the `Oracle.ManagedDataAccess.EntityFramework` or `Oracle.DataAccess.EntityFramework` assembly as a reference to the project.

7.  Modify the Oracle data type to .NET data type mappings as required by your application. See "[Entity Framework 6 Mapping and Customization](entityDataTypeMapping.md)" for more details.

8.  Rebuild the application.
