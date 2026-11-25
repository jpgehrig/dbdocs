This property gets the minimum length required for a password.

### Declaration

    // C#
    public override int MinRequiredPasswordLength{get;}

### Property Value

The minimum length required for a password. The default value is 7.

### Remarks

To customize a membership provider, ASP.NET developers can set an integer value for this property through the `web.config` file using the `minRequiredPasswordLength` attribute. The attribute name in the configuration file is case-sensitive.

The `minRequiredPasswordLength` property gets the minimum number of characters that must be entered to create a valid password for the `OracleMembershipProvider` object.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
