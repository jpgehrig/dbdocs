This property gets or sets the name of the application that the personalization information is specific to.

### Declaration

    // C#
    public override string ApplicationName{get; set;}

### Property Value

The name of the application. If the `applicationName` attribute is not specified in the application configuration file, or if the value is an empty string, then this property is set to the application virtual path.

### Exceptions

`HttpException` - The caller does not have high trust for ASP.NET hosting.

`ProviderException` - The `ApplicationName` string is greater than 256 characters.

### Remarks

The main purpose of the `ApplicationName` property is to scope the data managed by `OraclePersonalizationProvider` object. Applications that specify the same `ApplicationName` string when configuring the Web parts personalization service share personalization state, but applications that specify unique `ApplicationName` strings do not. The `OraclePersonalizationProvider` must associate the personalization state with application names so operations performed on personalization data sources can be scoped accordingly.

The following example shows typical code that the `OraclePersonalizationProvider` might use to retrieve the personalization state for a user named `Scott` and an application named `App`:

    SELECT * FROM PersonalizationState
    WHERE UserName='Scott' AND Path='~/Default.aspx'
    AND ApplicationName='App'

The final `AND` in the `WHERE` clause ensures that other applications that contain personalization state keyed by the same user name and path do not conflict with the `App` application.

If no value is specified for the `applicationName` attribute in the configuration file, then the default is the `ApplicationPath` property value for the current request. The attribute name in the configuration file is case-sensitive.

The `ApplicationName` property is not thread-safe. It is recommended that application code not allow users to set the `ApplicationName` property in Web applications.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
