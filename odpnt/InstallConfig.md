The settings for specific versions of ODP.NET, can be configured in several ways for specific effects on precedence:

- The Windows registry entries are machine-wide settings for a particular version of ODP.NET.

  Windows registry based configuration is not supported for ODP.NET, Managed Driver.

- The `machine.config` settings are .NET framework-wide settings that override the Windows registry values.

- The application or web config file settings are application-specific settings that override the `machine.config` settings and the Windows registry settings.

  **Note:**

  There is one exception to `app/web/config` settings overriding `machine.config`. For `oracle.manageddataaccess.client` and `oracle.unmanageddataaccess.client` sections, a `machine.config` with a specific ODP.NET version subsection, that is, `<version number="4.121.2.0">`, will override an `app/web.config` subsection that references all versions generically, that is, `<version number="*">`. To override the `machine.config` subsection, create a subsection for that version in the `app/web/config` file, that is, `<version number="4.121.2.0">`.

- Any attribute settings that are equivalent to the connection string override everything.

The application or web config file can be useful and sometimes essential in scenarios where more than one application on a computer use the same version of ODP.NET, but each application needs a different ODP.NET configuration. The Windows registry value settings for a given version of ODP.NET affect all the applications that use that version of ODP.NET. However, having ODP.NET configuration values in the application or web config file assure that these settings are applied only for that application, thus providing more granularities.

For example, if the application or `web.config` file has a `StatementCacheSize` configuration setting of `100`, this application-specific setting forces the version of ODP.NET that is loaded by that application to use `100` for the `StatementCacheSize` and overrides any setting in the `machine.config` and in the registry. Note that for any setting that does not exist in a config file (`machine.config` or application/web config), the value in the registry for a loaded version of ODP.NET is used, as in previous releases.

Note that ODP.NET reads the `machine.config` files from the version of the .NET Framework on which ODP.NET runs, not from the version of ODP.NET.

ODP.NET only reads the Windows Registry and the XML configuration file when it is loaded into memory, thus any configuration changes made after that are not read or used until the application is re-started.

All boolean attributes in ODP.NET .NET configuration settings accept `true`, `false`, `1`, and `0` as valid values. `1` is equivalent to `true` and `0` is equivalent to `false`.

**Note:**

ODP.NET Core does not support the Windows registry nor .NET configuration files. ODP.NET Core configuration can be set using .NET Configuration API, `sqlnet.ora` file, and `tnsnames.ora` file.

### Oracle Client Configuration File Automated Setup During Installation

When installing Oracle Data Access Components (ODAC) in a new Oracle Home, Oracle Universal Installer (OUI) automatically copies the Oracle local naming (tnsnames.ora), profile (sqlnet.ora), and directory (ldap.ora) parameter files and settings from an existing Oracle home into the newly installed ODAC home, as long as they share the same bitness. That is, they are both 32-bit installations or they are both 64-bit installations.

Alternatively, existing `*.ora` files can be copied over from another existing Oracle home, besides the last active one, to the new ODAC Oracle home. OUI provides location information for these files from up to three other existing Oracle homes if they exist. The `*.ora` files can be customized if the new Oracle home uses a different configuration from the previous Oracle home from which the files were copied over.

If you install into an existing ODAC or RDBMS Oracle home, then no new `*.ora` files is copied or created.

If you install onto a computer without any previous Oracle homes present, then OUI prompts the user for the database connection alias information. OUI then automatically creates the `tnsnames.ora` file. If no alias information is provided, then no `tnsnames.ora` file is created. Even if the user does not have all the database connection information readily available, Oracle recommends inserting placeholder values during the install process, then modifying the `tnsnames.ora` file later with actual values to replace the placeholders.

### Oracle Client Configuration File Settings

ODP.NET `tnsnames.ora`, `sqlnet.ora`, and `ldap.ora` parameter values can be set in a .NET configuration file or within the `*.ora `file itself. The `*.ora` file location can be a location different from the standard `ORACLE_HOME``/network/admin` directory. The `*.ora` settings order of precedence is similar to ODP.NET's settings order of precedence. The main difference is that the `*.ora` files themselves are included in the search order. The `tnsnames.ora` and `sqlnet.ora` precedence order is as follows:

1.  `app.config `or `web.config`

2.  `machine.config`

3.  File location specified by `TNS_ADMIN` setting

4.  The current `.EXE `or web application root directory

5.  `%ORACLE_HOME``%\network\admin` if using ODP.NET, Unmanaged Driver

The` ldap.ora` precedence order is as follows:

1.  `app.config `or `web.config`

2.  `machine.config`

3.  File location specified by `TNS_ADMIN` setting in .NET config file

4.  File location specified by `LDAP_ADMIN` setting in .NET config file

5.  The current `.EXE `or web application root directory

6.  `%ORACLE_HOME``%\network\admin` if using ODP.NET, Unmanaged Driver

7.  `%ORACLE_HOME``%\ldap\admin` if using ODP.NET, Unmanaged Driver

Oracle recommends using an `app.config` or `web.config` file to store all these Oracle Client configuration parameter settings.

Once the first `tnsnames.ora`, `sqlnet.ora`, and `ldap.ora` are found and read, no additional `*.ora` file lower in the precedence order is read. That means all Oracle Client configuration settings must be made in the `app.config`, `web.config`, `machine.config`, or the first set of `*.ora` files found. Additional parameter values set in `*.ora` files lower in the precedence order will not be read.

### Configuring .NET Framework to Use ODP.NET

Automatic ODP.NET machine-wide configuration upon installation is no longer available as of ODAC 18c. This change improves compatibility when applications on the same machine use different ODP.NET versions and/or depend on application-specific configuration settings instead of machine-wide assembly registration and configuration.

Nonetheless, administrators can still manually place managed and unmanaged ODP.NET in the Global Assembly Cache (GAC), as well as add configurations for section handler, `DbProviderFactories`, `TNS_ADMIN`, `LDAP_ADMIN`, and assembly redirection (in place of policy DLLs), into `machine.config`, if desired.

Most ODP.NET settings in machine.config can be overridden by local settings in `app.config` or `web.config`. However, conflicts between the `machine.config` and, `app.config` or `web.config` can prevent applications from running properly. Care should be taken when configuring ODP.NET at both the `machine.config` level and application level using `app.config` or `web.config`.

To avoid such issues, Oracle recommends ODP.NET application configuration settings reside in the `app.config` or `web.config`. The following sections explore how to set up these ODP.NET configuration sections and provide sample configuration sections and files.

#### Configuration Section Handler

In order for the application to read the ODP.NET configuration section, a section handler must be configured. The following entry should be added to the .NET configuration file to enable applications to add an `oracle.manageddataaccess.client` section for ODP.NET, Managed Driver-specific configuration:

    <configuration>
      <configSections>

      </configSections>
    </configuration>

**Note:**

In all the examples in this section, the version of the ODP.NET assembly is understood to be 4.122.19.1. This version number should be modified appropriately if you are using another version.

The unmanaged ODP.NET equivalent section handler is as follows:

    <configuration>
      <configSections>

      </configSections>
    </configuration>

One of the configuration entries that either has to match between `machine.config` and, `app.config` or `web.config`, or only exist in the `app.config` or `web.config` to avoid any conflict is the configuration for the section handler. For example, if your application is a web application and the above entry was added to a `web.config` and the same configuration section handler for `oracle.manageddataaccess.client` also exists in `machine.config` but the `Version` attribute values are different, an error message of "There is a duplicate `oracle.manageddataaccess.client` section defined." may be observed at runtime. To avoid this issue, the configuration section handler entry in the `machine.config` for `oracle.manageddataaccess.client` has to be removed from the `machine.config` or the ODP.NET config section handler entry in `machine.config` and `web.config` has to match exactly. If there are other applications on the machine that depend on this entry in the `machine.config`, then this section handler entry will need to be moved to all local applications’ .NET configuration files.

#### DbProviderFactories

The following entry should be added in the `app.config` or `web.config` for applications that use `DbProviderFactories` and `DbProviderFactory` classes. Also, any `DbProviderFactories` entry for `Oracle.ManagedDataAccess.Client` in the `machine.config` will be ignored due to the `<remove>` entry:

    <configuration>
      <system.data>
        <DbProviderFactories>
          <remove invariant="Oracle.ManagedDataAccess.Client" />
          <add name="ODP.NET, Managed Driver" invariant="Oracle.ManagedDataAccess.Client" description="Oracle Data Provider for .NET, Managed Driver" type="Oracle.ManagedDataAccess.Client.OracleClientFactory, Oracle.ManagedDataAccess, Version=4.122.19.1, Culture=neutral, PublicKeyToken=89b483f429c47342" />
        </DbProviderFactories>
      </system.data>
    </configuration>

The equivalent for unmanaged ODP.NET is as follows:

    <configuration>
      <system.data>
        <DbProviderFactories>
          <remove invariant="Oracle.DataAccess.Client" />
          <add name="Oracle Data Provider for .NET" invariant="Oracle.DataAccess.Client" description="Oracle Data Provider for .NET" type="Oracle.DataAccess.Client.OracleClientFactory, Oracle.DataAccess, Version=4.122.191, Culture=neutral, PublicKeyToken=89b483f429c47342" />
        </DbProviderFactories>
      </system.data>
    </configuration>

#### Dependent Assembly

For users accustomed to the policy DLLs that were registered automatically upon installation, the same can be accomplished through configuration. The following is an example configuration that redirects the application that depends on 4.122 version of ODP.NET and higher to be redirected to use ODP.NET 4.122.19.1. Note that in this example, an entry is added to ignore policy ODP.NET DLLs that are registered in the GAC:

    <configuration>
      <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
          <dependentAssembly>
            <publisherPolicy apply="no" />
            <assemblyIdentity name="Oracle.ManagedDataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />
            <bindingRedirect oldVersion="4.122.0.0 - 4.65535.65535.65535" newVersion="4.122.19.1" />
          </dependentAssembly>
        </assemblyBinding>
      </runtime>
    </configuration>

The equivalent for unmanaged ODP.NET is as follows:

    <configuration>
      <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
          <dependentAssembly>
            <publisherPolicy apply="no" />
            <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />
            <bindingRedirect oldVersion="4.122.0.0 - 4.65535.65535.65535" newVersion="4.122.19.1" />
          </dependentAssembly>
        </assemblyBinding>
      </runtime>
    </configuration>
