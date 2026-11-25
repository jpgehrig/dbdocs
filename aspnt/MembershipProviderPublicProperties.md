`OracleMembershipProvider` public properties are listed in Table 2-7.

Table 2-7 OracleMembershipProvider Public Properties

| Public Properties                                                                                 | Description                                                                                                                                                                  |
|:--------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ApplicationName](MembershipProviderApplicationName.md)                                           | Gets or sets the name of the application that is used to group user information                                                                                              |
| [CommandTimeout](MembershipProviderCommandTimeout.md)                                             | Gets the number of seconds that the command is allowed to execute before it is terminated with an exception                                                                  |
| `Description`                                                                                     | Inherited from `System.Configuration.Provider.Providerbase`                                                                                                                  |
| [EnablePasswordReset](MembershipProviderEnablePasswordReset.md)                                   | Indicates whether the membership provider is configured to allow users to reset their passwords                                                                              |
| [EnablePasswordRetrieval](MembershipProviderEnablePasswordRetrieval.md)                           | Indicates whether the membership provider is configured to allow users to retrieve their passwords                                                                           |
| [MaxInvalidPasswordAttempts](MembershipProviderMaxInvalidPasswordAttempts.md)                     | Gets the number of invalid password or password-answer attempts allowed before the user is locked out                                                                        |
| [MinRequiredNonAlphanumericCharacters](MembershipProviderMinRequiredNonAlphanumericCharacters.md) | Gets the minimum number of special characters that must be present in a valid password                                                                                       |
| [MinRequiredPasswordLength](MembershipProviderMinRequiredPasswordLength.md)                       | Gets the minimum length required for a password                                                                                                                              |
| `Name`                                                                                            | Inherited from `System.Configuration.Provider.Providerbase`                                                                                                                  |
| [PasswordAttemptWindow](MembershipProviderPasswordAttemptWindow.md)                               | Gets the number of minutes in which a maximum number of invalid password or password-answer attempts are allowed before the user is locked out                               |
| [PasswordCompatMode](MembershipProviderPasswordCompatMode.md)                                     | Gets the password compatibility mode.                                                                                                                                        |
| [PasswordFormat](MembershipProviderPasswordFormat.md)                                             | Gets a value indicating the format for storing passwords in the membership data source                                                                                       |
| [PasswordStrengthRegularExpression](MembershipProviderPasswordStrengthRegularExpression.md)       | Gets the regular expression used to evaluate a password                                                                                                                      |
| [RequiresQuestionAndAnswer](MembershipProviderRequiresQuestionAndAnswer.md)                       | Gets a value indicating whether the membership provider is configured in such a way that it requires the user to answer a password question for password reset and retrieval |
| [RequiresUniqueEmail](MembershipProviderRequiresUniqueEmail.md)                                   | Gets a value indicating whether the membership provider is configured to require a unique e-mail address for each user name                                                  |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
