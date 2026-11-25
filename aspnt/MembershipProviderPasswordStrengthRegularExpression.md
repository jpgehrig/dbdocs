This property gets the regular expression used to evaluate a password.

### Declaration

    // C#
    public override string PasswordStrengthRegularExpression{get;}

### Property Value

The regular expression that is used to evaluate a password. The default is an empty string.

### Remarks

To customize a membership provider, ASP.NET developers can set a string value for this property through the `web.config` file using the `passwordStrengthRegularExpression` attribute. The attribute name in the configuration file is case-sensitive.

The `PasswordStrengthRegularExpression` property gets the regular expression as criteria to evaluate the password. If the password does not meet the criteria, it is not accepted by the membership provider.

Consider the following example:

    passwordStrengthRegularExpression="(?=.{7,})(?=(.*\d){1,})(?=(.*\W){1,})"

The code in the preceding example validates passwords against the following criteria:

- Has at least 7 characters.

- Contains at least 1 digit.

- Contains at least 1 special (nonalphanumeric) character.

The minimum password length defined in `passwordStrengthRegularExpression` must be equal to or greater than the value of the `minRequiredPasswordLength` attribute.

The minimum number of special (nonalphanumeric) characters defined in the `passwordStrengthRegularExpression` attribute must be equal to or greater than the value of the `minRequiredNonalphanumericCharacters` attribute.

The `passwordStrengthRegularExpression` attribute is not used in automatically generated passwords from the `ResetPassword` method.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
