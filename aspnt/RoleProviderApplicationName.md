This property gets or sets the name of the application that stores the role provider information.

### Declaration

    // C#
    public override string ApplicationName{get; set;};

### Property Value

The name of the application. If the `applicationName` attribute is not specified in the application configuration file, or if the value is an empty string, then this property is set to the application virtual path.

### Exceptions

`HttpException` - The user setting the `ApplicationName` property does not have high ASP.NET hosting permission.

`System.Configuration.Provider.ProviderException` - The `ApplicationName` property is set to a string greater than 256 characters.

### Remarks

The string value of the `ApplicationName` property is used to associate user names and role names with different applications. Multiple applications can use the same database to store user names and role names without running into any conflict between duplicate names. This property can be set programmatically, or it can be set declaratively in the Web application configuration file using the `applicationName` attribute. The attribute name in the configuration file is case-sensitive.

The `ApplicationName` property is not thread-safe. It is recommended that the programming code not allow users to set the `ApplicationName` property in Web applications.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)

- [OracleRoleProvider Members](OracleRoleProviderMembers.md)
