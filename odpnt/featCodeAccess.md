ODP.NET implements code access security through the `OraclePermission` class. This ensures that application code trying to access the database has the requisite permission to do so.

When a .NET assembly tries to access Oracle Database through ODP.NET, ODP.NET demands `OraclePermission`. The .NET runtime security system checks to see whether the calling assembly, and all other assemblies in the call stack, have `OraclePermission` granted to them. If all assemblies in the call stack have `OraclePermission` granted to them, then the calling assembly can access the database. If any one of the assemblies in the call stack does not have `OraclePermission` granted to it, then a security exception is thrown.

**Note:**

ODP.NET Core does not support Code Access Security.

### Configuring OraclePermission

The `DemandOraclePermission` configuration attribute is used to enable or disable `OraclePermission` demand for an ODP.NET API. The `DemandOraclePermission` value can be specified in the Windows registry for unmanaged ODP.NET only, or an individual application configuration file for both unmanaged and managed ODP.NET.

The following Windows registry key is used to configure the `DemandOraclePermission` configuration attribute:

    HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\ODP.NET\Assembly_Version\DemandOraclePermission

Here `Assembly_Version` is the full assembly version number of `Oracle.DataAccess.dll.` The `DemandOraclePermission` key is of type `REG_SZ`. It can be set to either `1` (enabled) or `0` (disabled).

You can also enable `OraclePermission` demand for an individual application using its application configuration file. The following example enables the `DemandOraclePermission` property in an application configuration file for ODP.NET, Unmanaged Driver:

    <configuration>
      <oracle.dataaccess.client>
        <settings>
          <add name="DemandOraclePermission" value="1"/>
        </settings>
      </oracle.dataaccess.client>
    </configuration>

Similarly, you can use `DemandOraclePermission` to configure ODP.NET, Managed Driver under the settings section for managed provider configuration. See also "[settings section](InstallManagedConfig.md)" for more information.

An application or assembly can successfully access the database if `OraclePermission` has been added to the permission set associated with the assembly's code group. A system administrator can modify the appropriate permission set manually or by using the Microsoft .NET configuration tool (`Mscorcfg.msc`).

Administrators may also use an appropriate .NET Framework Tool, such as the Code Access Security Policy Tool (`Caspol.exe)`, to modify security policy at the machine, user, and enterprise levels for including `OraclePermission`.

`OracleConnection` makes security demands using the `OraclePermission` object when `OraclePermission` demand has been enabled using `DemandOraclePermission` configuration attribute. Application developers should make sure that their code has sufficient permission before using `OracleConnection`.

**See Also:**

- "[OraclePermission Class](OraclePermissionClass.md)"

- "[OraclePermissionAttribute Class](OraclePermissionAttributeClass.md)"

### Configuring OraclePermission for Web Applications with High or Medium Trust Levels

For Web applications operating under high or medium trust, `OraclePermission` needs to be configured in the appropriate `web_``TrustLevel``.config` file, so that the application does not encounter any security errors.

`OraclePermission` can be configured using the `OracProvCfg` tool. `OraProvCfg.exe` adds appropriate entries to the `web_hightrust.config` and `web_mediumtrust.config` files associated with the specified .NET framework version.The following example illustrates using the `OraProvCfg` tool for configuring `OraclePermission` in a .NET 2.0 Web application:

    OraProvCfg.exe /action:config  /product:odp /component:oraclepermission
                   /frameworkversion:v2.0.50727
                   /providerpath:full_path_of_Oracle.DataAccess.dll

On running the preceding command, the following entry is added to the `web_hightrust.config` and `web_mediumtrust.config` files under the ASP.NET permission set:

    <IPermission class="Oracle.DataAccess.Client.OraclePermission, Oracle.DataAccess,
    Version=2.112.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" version="1"
    Unrestricted="true" />

`OraProvCfg` can also be used to remove these entries from the `.config` files when required. The following example illustrates this:

    OraProvCfg.exe /action:unconfig  /product:odp  /component:oraclepermission
                   /frameworkversion:v2.0.50727
                   /providerpath:full_path_of_Oracle.DataAccess.dll

### Configuring OraclePermission for Windows Applications Running in a Partial Trust Environment

For Windows applications operating in a partial trust environment, the `OraclePermission` entry should be specified under the appropriate permission set in the `security.config` file. The `security.config` file is available in the `%windir%\Microsoft.NET\Framework\``{version}``\CONFIG` folder.

The following example specifies the `OraclePermission` entry for a .NET 2.0 Windows application:

    <IPermission class="Oracle.DataAccess.Client.OraclePermission, Oracle.DataAccess,
     Version=2.112.2.0, Culture=neutral, PublicKeyToken=89b483f429c47342" version="1"
     Unrestricted="true" />
