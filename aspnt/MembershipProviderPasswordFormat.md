This property gets a value indicating the format for storing passwords in the membership data source.

### Declaration

    // C#
    public override MembershipPasswordFormat PasswordFormat{get;}

### Property Value

The format for storing passwords in the data source. The format can be any one of the `MembershipPasswordFormat` values, such as `Clear`, `Hashed`, or `Encrypted`. The default value is `Hashed`.

### Remarks

To customize a membership provider, ASP.NET developers can specify a `MembershipPasswordFormat` enumerated value for this property through the `web.config` file using the `passwordFormat` attribute. The attribute name in the configuration file is case-sensitive.

The `PasswordFormat` property indicates that passwords are stored in any one of the following formats: `Clear`, `Encrypted`, or `Hashed`. The format name is case-sensitive. For example, `Clear` is valid, but `clear` is invalid.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
