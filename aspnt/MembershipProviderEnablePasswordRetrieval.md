This property indicates whether the membership provider is configured to allow users to retrieve their passwords.

### Declaration

    // C#
    public override bool EnablePasswordRetrieval{get;}

### Property Value

Returns `true`, if the membership provider is configured to support password retrieval; otherwise, returns `false`. The default is `false`.

### Remarks

To customize a membership provider, ASP.NET developers can set a Boolean value for this property through the `web.config` file using the `enablePasswordRetrieval` attribute. The value indicates whether users can use the `GetPassword` method to retrieve their current password from the database. The attribute name in the configuration file is case-sensitive.

If the custom membership provider supports hashed passwords, then the `GetPassword` method returns an exception if the `EnablePasswordRetrieval` property is set to `true` and the password format is set to `Hashed`. In other words, hashed passwords cannot be retrieved.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
