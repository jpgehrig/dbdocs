This property gets the number of seconds that the command is allowed to execute before it is terminated with an exception.

### Declaration

    // C#
    public int CommandTimeout {get;}


### Property Value

An `int`.

### Remarks

To customize a provider, ASP.NET developers can set an integer value for this property through the `web.config` file using the `commandTimeout` attribute.

The default value is 30 seconds. The attribute name in the configuration file is case-sensitive.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
