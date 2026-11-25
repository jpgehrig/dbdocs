This property indicates whether the membership provider is configured to allow users to reset their passwords.

### Declaration

    // C#
    public override bool EnablePasswordReset{get;}

### Property Value

Returns `true`, if the membership provider supports password reset; otherwise, it returns `false`. The default is `true`.

### Remarks

To customize the `membership` provider, ASP.NET developers can specify a Boolean value for this property through the `web.config` file using the `enablePasswordReset` attribute. The value indicates whether users can use the `ResetPassword` method to overwrite their current password with a new, randomly generated password. The attribute name in the configuration file is case-sensitive.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
