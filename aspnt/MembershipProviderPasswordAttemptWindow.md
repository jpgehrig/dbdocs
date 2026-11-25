This property gets the number of minutes in which a maximum number of invalid password or password-answer attempts are allowed before the user is locked out.

### Declaration

    // C#
    public override int PasswordAttemptWindow{get;}

### Property Value

The number of minutes in which a maximum number of invalid password or password-answer attempts are allowed before the user is locked out. The default value is 10.

### Remarks

To customize a membership provider, ASP.NET developers can set an integer value for this property through the `web.config` file using the `passwordAttemptWindow` attribute. The attribute name in the configuration file is case-sensitive.

The `PasswordAttemptWindow` property works in conjunction with the `MaxInvalidPasswordAttempts` property. If the number of invalid passwords or password question entries is greater than or equal to the `MaxInvalidPasswordAttempts` property value within the `PasswordAttemptWindow` property value (in minutes), then the user is locked out until the user is unlocked by the `UnlockUser` method. If a valid password or password answer is supplied before the `MaxInvalidPasswordAttempts` value is reached, then the counter that tracks the number of invalid attempts is reset to zero.

Invalid password and password-answer attempts accumulate independently. For example, if the `MaxInvalidPasswordAttempts` property is set to 10, and 6 invalid password attempts are made followed by 3 invalid password-answer attempts, 4 more invalid password attempts or 7 more invalid password-answer attempts must be made within the `PasswordAttemptWindow` value for the user to be locked out.

If the `RequiresQuestionAndAnswer` property is set to `false`, then invalid password-answer attempts are not tracked.

Invalid password and password-answer attempts are tracked in the `ValidateUser`, `ChangePassword`, `ChangePasswordQuestionAndAnswer`, `GetPassword`, and `ResetPassword` methods.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
