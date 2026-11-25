This property gets a value indicating whether the membership provider is configured to require a unique e-mail address for each user name.

### Declaration

    // C#
    public override bool RequiresUniqueEmail{get;}

### Property Value

Returns `true`, if the membership provider requires a unique e-mail address; otherwise, returns `false`. The default value is `false`.

### Remarks

To customize a membership provider, ASP.NET developers can specify a Boolean value for the `RequiresUniqueEmail` property through the `web.config` file using the `requiresUniqueEmail` attribute. The attribute name in the configuration file is case-sensitive.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
