This property gets a value indicating whether the membership provider is configured in such a way that it requires the user to answer a password question for password reset and retrieval.

### Declaration

    // C#
    public override bool RequiresQuestionAndAnswer{get;}

### Property Value

Returns `true`, if a password answer is required for password reset and retrieval; otherwise, returns `false`. The default value is `true`.

### Remarks

To customize a membership provider, ASP.NET developers can set a Boolean value for this property through the `web.config` file by using the `requiresQuestionAndAnswer` attribute. The value indicates whether users must supply a password answer in order to retrieve their password using the `GetPassword` method, or reset their password using the `ResetPassword` method. The attribute name in the configuration file is case-sensitive.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
