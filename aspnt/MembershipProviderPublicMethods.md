`OracleMembershipProvider` public methods are listed in Table 2-8.

Table 2-8 OracleMembershipProvider Public Methods

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

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
