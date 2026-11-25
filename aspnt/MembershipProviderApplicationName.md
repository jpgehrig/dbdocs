This property gets or sets the name of the application that is used to group user information.

### Declaration

    // C#
    public override string ApplicationName{get; set;}

### Property Value

The name of the application. If the `applicationName` attribute is not specified in the application configuration file, or if the value is an empty string, then this property is set to the application virtual path.

### Exceptions

`ArgumentException` - The application name supplied is an empty string or a null reference.

`ProviderException` - The application name supplied exceeds 256 characters.

### Remarks

The string value of the `ApplicationName` property is used for organizing user information. Multiple ASP.NET applications can use the same database and create duplicate user names because user information is stored uniquely for each application name. This property can be set programmatically, or it can be set declaratively in the Web application configuration file using the `applicationName` attribute. The attribute name in the configuration file is case-sensitive.

The `ApplicationName` property is not thread-safe. It is recommended that the programming code not allow users to set the `ApplicationName` property in Web applications.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
