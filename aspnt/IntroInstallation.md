Oracle Providers for ASP.NET is part of Oracle Data Access Components (ODAC), which can be downloaded from OTN.

- NuGet

  NuGet is software packaging method for Microsoft .NET. It provides an automated install and setup method popular with developers and administrators that now can be used to install Oracle Providers for ASP.NET.

- Microsoft Windows Installer

  Microsoft Windows Installer (MSI) is the popular, standard installation method for Windows-based software. It can be used to deploy Oracle Providers for ASP.NET.

- XCopy

  Administrators use XCopy to deploy Oracle Providers for ASP.NET to a large number of computers for production deployments. It has a small footprint and fine grain control during installation and setup.

- Oracle Universal Installer

  Developers or users use Oracle Universal Installer for automatic GUI installation. It includes documentation and code samples that are not part of XCopy deployment.

### Machine-Wide Configuration

Machine-wide configuration was once available as an install option in Oracle Universal Installer and XCopy. It is no longer available in current ODAC and Oracle Client installations. If machine-wide Oracle Providers for ASP.NET configuration was chosen in a previous version, that particular ASP.NET providers installation had:

- updated the `machine.config` to use an older `Oracle.Web.dll` version,

- placed that older `Oracle.Web.dll` into the `GAC_MSIL`,

- placed policy DLLs into the `GAC_MSIL` that redirects AnyCPU application to use the older `Oracle.Web.dll`.

Thus, existing applications will continue to use these older Oracle ASP.NET providers unless these changes are reversed through deinstalling the old providers or manual configuration steps, such as what is described in the next section.

Machine-wide configuration changes occurred for both Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4.

### Non-Machine-Wide Configuration

Non-machine-wide Oracle Providers for ASP.NET configuration is the only install option now available. This install option will:

- not update the `machine.config` to use `Oracle.Web.dll`,

- not place `Oracle.Web.dll` into the `GAC_MSIL`,

- not place policy DLLs into the `GAC_MSIL` that redirects AnyCPU application to use the new `Oracle.Web.dll`.

Unless some manual changes are made to existing applications, they will continue to use their current Oracle Providers for ASP.NET assembly version if configured machine-wide, not the newly installed version.

The following manual steps are required in order for your application to use the newly installed `Oracle.Web.dll` if machine-wide configuration is not chosen.

The `Oracle.Web.dll` and either `Oracle.ManagedDataAccess.dll` or `Oracle.DataAccess.dll` will need to be copied to your application directory for your application to use the newer version of `Oracle.Web.dll` since it was chosen not to be placed into the GAC.

Proper configuration is needed in the `web.config` to refer to the new `Oracle.Web.dll`. Here's an example of what the `web.config` will look if it's desired to have all the providers configured to use `Oracle.Web.dll` version 4.122.19.1:

    <configuration>
      <system.web>
        <membership>
          <providers>
            <add name="OracleMembershipProvider" type="Oracle.Web.Security.OracleMembershipProvider, Oracle.Web, Version=4.122.19.1,
             Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString" applicationName=""
             enablePasswordRetrieval="false" enablePasswordReset="true" requiresQuestionAndAnswer="true" requiresUniqueEmail="false"
             passwordFormat="Hashed" maxInvalidPasswordAttempts="5" minRequiredPasswordLength="7"
             minRequiredNonalphanumericCharacters="1" passwordAttemptWindow="10" passwordStrengthRegularExpression="" />
          </providers>
        </membership>
        <profile>
          <providers>
            <add name="OracleProfileProvider" type="Oracle.Web.Profile.OracleProfileProvider, Oracle.Web, Version=4.122.19.1,
              Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString" applicationName="" />
          </providers>
        </profile>
        <roleManager>
          <providers>
            <add name="OracleRoleProvider" type="Oracle.Web.Security.OracleRoleProvider, Oracle.Web, Version=4.122.19.1,
               Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString" applicationName="" />
          </providers>
        </roleManager>
        <siteMap>
          <providers>
            <add name="OracleSiteMapProvider" type="Oracle.Web.SiteMap.OracleSiteMapProvider, Oracle.Web, Version=4.122.19.1,
              Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString"
              applicationName="" securityTrimmingEnabled="true" />
          </providers>
        </siteMap>
        <webParts>
          <personalization>
            <providers>
              <add name="OraclePersonalizationProvider" type="Oracle.Web.Personalization.OraclePersonalizationProvider, Oracle.Web,
                Version=4.122.19.1, Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString"
                applicationName="" />
            </providers>
          </personalization>
        </webParts>
        <healthMonitoring>
          <providers>
            <add name="OracleWebEventProvider" type="Oracle.Web.Management.OracleWebEventProvider, Oracle.Web, Version=4.122.19.1,
              Culture=neutral, PublicKeyToken=89b483f429c47342" connectionStringName="OraAspNetConString" buffer="true"
              bufferMode="OracleNotification" />
          </providers>
        </healthMonitoring>
      </system.web>
    </configuration>

Please note that the application can be updated to use the newer `Oracle.Web.dll` version and the `web.config` can be configured automatically by installing the NuGet package for Oracle Providers for ASP.NET.

Additionally, Oracle Providers for ASP.NET Dynamic Help is registered with Visual Studio, providing context-sensitive online help that is seamlessly integrated with the Visual Studio Dynamic Help. With Dynamic Help, the user can access Oracle Providers for ASP.NET documentation within Visual Studio by placing the cursor on an Oracle Providers for ASP.NET keyword and pressing the F1 function key.

Once you have installed Oracle Providers for ASP.NET, two additional setup tasks are required, as follows:

- Database Server Setup

- ASP.NET Client Setup

**See Also:**

- "ASP.NET Client Setup" for more details

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/overview-of-oracle-database-installation.md) for installation instructions

### Database Server Setup

The following sections explain how to configure the providers:

- Database Privileges for Setup

- Configuring All Oracle Providers for ASP.NET

- Configuring Oracle Providers for ASP.NET Individually

- General Setup Information

#### Database Privileges for Setup

To set up the Oracle database, database administrators must grant the following database privileges to the Oracle Providers for ASP.NET schema. These privileges grant the schema privileges to create the tables, views, stored procedures, and other database objects the Oracle Providers for ASP.NET require. These scripts must be run against the database from which the ASP.NET providers will retrieve their stored state information. These SQL scripts can be run using SQL\*Plus or within Oracle Developer Tools for Visual Studio.

Oracle Providers for ASP.NET requires the following privileges during setup:

- Change notification

- Create job

- Create procedure

- Create public synonym

- Create role

- Create session

- Create table

- Create view

- Drop public synonym

- Grant access to and allocate space in an Oracle tablespace

Not all database privileges are required for Oracle Providers for ASP.NET runtime operations. Database administrators may selectively grant and revoke privileges as required. For runtime operations, all providers require that the `CREATE` `SESSION` privilege be granted to the schema user. In addition, the Site Map and Cache Dependency providers require the `CHANGE` `NOTIFICATION` privilege during runtime. The remaining privileges can be granted to the schema user just for installation and deinstallation, then revoked for runtime operations.

Errors that occur during the setup script execution may indicate that the user needs to be granted the above privileges. If this is the case, the database administrator must grant these privileges. The Oracle Session State Provider for ASP.NET requires the `CREATE JOB` privilege when Oracle Database 10g or later is the database.

#### Configuring All Oracle Providers for ASP.NET

To configure all providers in the database at once, run `InstallAllOracleASPNETProviders.sql`. This script is found in the `ORACLE_BASE\\ORACLE_HOME``\ASP.NET\sql` directory.

#### Configuring Oracle Providers for ASP.NET Individually

Applications may not require all Oracle Providers for ASP.NET. Providers can be set up individually. Except for the Oracle Session State Provider and Oracle Cache Dependency Provider, the following install script must be executed before any other install scripts: `InstallOracleASPNETCommon.sql`. Then, for each Oracle Provider for ASP.NET, a SQL script specific for that provider must be executed (in any order).

These install scripts are found in the `ORACLE_BASE\\ORACLE_HOME``\ASP.NET\sql` directory.

Table 1-2 Install Scripts

| Provider                         | Required Installation Script                                                                                                                                                                            |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Membership Provider       | `InstallOracleMembership.sql`                                                                                                                                                                           |
| Oracle Personalization Provider  | `InstallOraclePersonalization.sql`                                                                                                                                                                      |
| Oracle Profile Provider          | `InstallOracleProfile.sql`                                                                                                                                                                              |
| Oracle Role Provider             | `InstallOracleRoles.sql`                                                                                                                                                                                |
| Oracle Session State Provider    | `InstallOracleSessionState.sql`<br>Note: This provider requires the execution of only the `InstallOracleSessionState.sql` script. It does not require the execution of `InstallOracleASPNETCommon.sql`. |
| Oracle Site Map Provider         | `InstallOracleSiteMap.sql`                                                                                                                                                                              |
| Oracle Web Events Provider       | `InstallOracleWebEvents.sql`                                                                                                                                                                            |
| Oracle Cache Dependency Provider | No script execution needed                                                                                                                                                                              |

#### General Setup Information

When Oracle Providers for ASP.NET installation scripts run, they execute, in turn, corresponding `.plb` scripts that are located in the same directory. The `.plb` scripts create the stored procedures and functions that the providers use. The installation `.sql` scripts must execute where the .`plb` file can be accessed.

Each provider also provides corresponding uninstall scripts to remove database objects that were created from the install scripts. These scripts are prefixed with the word `Uninstall`.

The install and uninstall scripts are the same for Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

### ASP.NET Client Setup

After installation, developers must provide the connection information to the database schema that stores and retrieves the ASP.NET state information. This step requires developers to supply the `User` `Id`, `Password`, `Data` `Source`, and other connection string information if necessary. In the `machine.config` file, developers can provide an entry similar to the example below.

    <connectionStrings>
    <add name="OraAspNetConString" connectionString="User Id=aspnet;Password=aspnet;Data Source=oracle; " />
    </connectionStrings>


Optionally, developers can customize the properties of each ASP.NET provider from within the `<system.web>` section of the `machine.config`.

While machine-wide configuration automatically configures the `machine.config`, developers can apply more fine grained application-level control over the Oracle Providers for ASP.NET by using the `web.config` file. This file overrides entries from the `machine.config` file, but only for the specific web application it is a part of. Developers can set up their `web.config` file with the same XML syntax as the `machine.config` file.

Developers can use standard ASP.NET management tools to configure the Oracle Providers for ASP.NET. Specifically, developers can use the Internet Information Services management console. In the ASP.NET Configuration Settings of the console, developers can modify the Oracle provider settings. Alternatively, in a Web Site project in Visual Studio, the ASP.NET Configuration choice under the Website menu item allows developers to set these settings for their specific Web Site projects.

A machine-wide configuration installation automatically sets up `machine`.`config` with default values, but administrators can modify the setup. Users can use the `OraProvCfg` utility to configure the provider-specific entry in the `machine.config` file as follows:

**Note:**

To configure Oracle Providers for ASP.NET 2.0, use the `OraProvCfg` utility under `ORACLE_BASE\ORACLE_HOME\``ASP.NET\Bin\2.x.`

To configure Oracle Providers for ASP.NET 4, use the `OraProvCfg` utility under `ORACLE_BASE\ORACLE_HOME\``ASP.NET\Bin\4.`

- To display the `OraProvCfg` utility help:

      OraProvCfg -help

- To add Oracle Providers for ASP.NET-specific entries to the `machine.config` file:

       OraProvCfg  /action:config  /product:aspnet  /component:all
                   /frameworkversion:v2.0.50727
                   /providerpath:c:\Oracle\odp.net\bin\2.x\Oracle.Web.dll

  Where Framework version and Provider path (especially) may need to change accordingly.

- To remove the Oracle Providers for ASP.NET-specific entries from the `machine.config` file:

      OraProvCfg  /action:unconfig  /product:aspnet  /component:all
                  /frameworkversion:v2.0.50727

Where Framework version may need to change accordingly.
