This property gets or sets the name of the application that groups the profile information.

### Declaration

    // C#
    public override string ApplicationName{get; set;}

### Property Value

The name of the application. If the `applicationName` attribute is not specified in the application configuration file, or if the value is an empty string, then this property is set to the application virtual path.

### Exceptions

`HttpException` - The `ApplicationName` property was set by a caller that does not have high ASP.NET hosting permission.

`System.Configuration.Provider.ProviderException` - The application name supplied exceeds 256 characters.

`ArgumentException` - The application name supplied is an empty string or a null reference.

### Remarks

The string value of the `ApplicationName` property is used for organizing user information.

Multiple ASP.NET applications can use the same data source and create duplicate user names because user information is stored uniquely for each application name. This property can be set programmatically, or it can be set declaratively in the configuration file for the Web application using the `applicationName` attribute. The attribute name in the configuration file is case-sensitive.

The `ApplicationName` property is not thread-safe. It is recommended that application code not allow users to set the `ApplicationName` property in Web applications.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
