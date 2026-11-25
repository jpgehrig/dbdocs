This property gets the minimum number of special characters that must be present in a valid password.

### Declaration

    // C#
    public override int MinRequiredNonAlphanumericCharacters(get;}

### Property Value

The minimum number of special characters that must be present in a valid password. The default value is 1.

### Remarks

To customize a membership provider, ASP.NET developers can set an integer value for this property through the `web.config` file using the `minRequiredNonalphanumericCharacters` attribute. The attribute name in the configuration file is case-sensitive.

The `MinRequiredNonAlphanumericCharacters` property returns the minimum number of special, nonalphabetic characters that must be entered to create a valid password for the `OracleMembershipProvider` object.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
