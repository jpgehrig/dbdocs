`OracleMembershipProvider` members are listed in the following tables.

### OracleMembershipProvider Constructors

The `OracleMembershipProvider` constructor is listed in Table 2-1.

Table 2-1 OracleMembershipProvider Constructor

| Constructor                                                                | Description                                                         |
|:---------------------------------------------------------------------------|:--------------------------------------------------------------------|
| [OracleMembershipProvider Constructors](MembershipProviderConstructors.md) | Instantiates a new instance of the `OracleMembershipProvider` class |

### OracleMembershipProvider Static Methods

`OracleMembershipProvider` static methods are listed in Table 2-2.

Table 2-2 OracleMembershipProvider Static Methods

| Static Methods    | Description                                 |
|:------------------|:--------------------------------------------|
| `Equals`          | Inherited from `System.Object` (Overloaded) |
| `ReferenceEquals` | Inherited from `System.Object`              |

### OracleMembershipProvider Public Properties

`OracleMembershipProvider` public properties are listed in Table 2-3.

Table 2-3 OracleMembershipProvider Public Properties

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

### OracleMembershipProvider Public Methods

`OracleMembershipProvider` public methods are listed in Table 2-4.

Table 2-4 OracleMembershipProvider Public Methods

| Public Methods                                                                          | Description                                                                                                                                 |
|:----------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| [ChangePassword](MembershipProviderChangePassword.md)                                   | Updates the password for a user                                                                                                             |
| [ChangePasswordQuestionAndAnswer](MembershipProviderChangePasswordQuestionAndAnswer.md) | Updates the password question and answer for a user                                                                                         |
| [CreateUser](MembershipProviderCreateUser.md)                                           | Adds a new user to the database                                                                                                             |
| [DeleteUser](MembershipProviderDeleteUser.md)                                           | Removes a user from the database                                                                                                            |
| `Equals`                                                                                | Inherited from `System.Object` (Overloaded)                                                                                                 |
| [FindUsersByEmail](MembershipProviderFindUsersByEmail.md)                               | Returns a collection of users whose e-mail addresses match the specified e-mail address                                                     |
| [FindUsersByName](MembershipProviderFindUsersByName.md)                                 | Returns a collection of users that match the specified user name                                                                            |
| [GeneratePassword](MembershipProviderGeneratePassword.md)                               | Generates a random password that is at least 14 characters in length                                                                        |
| [GetAllUsers](MembershipProviderGetAllUsers.md)                                         | Returns a collection of all the users in the database                                                                                       |
| `GetHashCode`                                                                           | Inherited from `System.Object`                                                                                                              |
| [GetNumberOfUsersOnline](MembershipProviderGetNumberOfUsersOnline.md)                   | Returns the number of users that are currently accessing the application                                                                    |
| [GetPassword](MembershipProviderGetPassword.md)                                         | Returns the password for the specified user name from the database                                                                          |
| `GetType`                                                                               | Inherited from `System.Object`                                                                                                              |
| [GetUser](MembershipProviderGetUserOverloads.md)                                        | Returns user information from the database based on the unique identifier for the user (Overloaded)                                         |
| [GetUserNameByEmail](MembershipProviderGetUserNameByEmail.md)                           | Returns the user name associated with the specified e-mail address                                                                          |
| [Initialize](MembershipProviderInitialize.md)                                           | Initializes the `OracleMembership` provider with the property values specified in the ASP.NET application configuration file (`web.config`) |
| [ResetPassword](MembershipProviderResetPassword.md)                                     | Resets a user's password and returns a new automatically generated password                                                                 |
| `ToString`                                                                              | Inherited from `System.Object`                                                                                                              |
| [UnlockUser](MembershipProviderUnlockUser.md)                                           | Unlocks a user so that the user can be validated                                                                                            |
| [UpdateUser](MembershipProviderUpdateUser.md)                                           | Updates information about a user in the database                                                                                            |
| [ValidateUser](MembershipProviderValidateUser.md)                                       | Validates the user                                                                                                                          |

### OracleMembershipProvider Public Events

`OracleMembershipProvider` public event is listed in Table 2-5.

Table 2-5 OracleMembershipProvider Public Event

| Public Event         | Description                                             |
|:---------------------|:--------------------------------------------------------|
| `ValidatingPassword` | Inherited from `System.Web.Security.MembershipProvider` |

**See Also:**

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)
