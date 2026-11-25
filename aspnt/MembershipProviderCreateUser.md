This method adds a new user to the database.

### Declaration

    // C#
    public override MembershipUser CreateUser(string userName, string password,
       string emailAddress, string passwordQuestion, string passwordAnswer, bool
       isApproved, Object providerUserKey, out MembershipCreateStatus status);

### Parameters

- `userName`

  The user name for the new user.

- `password`

  The password for the new user.

- `emailAddress`

  The email address for the new user.

- `passwordQuestion`

  The password question for the new user.

- `passwordAnswer`

  The password answer for the new user.

- `isApproved`

  A Boolean value that indicates whether the new user is approved to be validated.

- `providerUserKey`

  The unique identifier from the database for the new user.

- `status`

  A `MembershipCreateStatus` enumeration value indicating whether the user was created successfully.

### Return Value

A `MembershipUser` object populated with the information for the newly created user.

### Remarks

This method returns a `MembershipUser` object populated with the information for the newly created user. The `status` parameter returns a `MembershipCreateStatus` value that indicates whether the user was successfully created. If the `CreateUser` method failed, a `MembershipCreateStatus` member indicates the cause of the failure.

### MembershipCreateStatus Enumeration

The `MembershipCreateStatus` enumeration values are listed in Table 2-9.

Table 2-9 MembershipCreateStatus Enumeration Values

| Member Name                | Description                                                                                                |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------|
| `DuplicateEmail`           | The e-mail address for the application already exists in the database.                                     |
| `DuplicateProviderUserKey` | The provider user key for the application already exists in the database.                                  |
| `DuplicateUserName`        | The user name for the application already exists in the database.                                          |
| `InvalidAnswer`            | The password answer is not formatted correctly.                                                            |
| `InvalidEmail`             | The e-mail address is not formatted correctly.                                                             |
| `InvalidPassword`          | The password is not formatted correctly.                                                                   |
| `InvalidProviderUserKey`   | The provider user key is of an invalid type or format.                                                     |
| `InvalidQuestion`          | The password question is not formatted correctly.                                                          |
| `InvalidUserName`          | The user name was not found in the database.                                                               |
| `ProviderError`            | The provider returned an error that is not described by other `MembershipCreateStatus` enumeration values. |
| `Success`                  | The user was successfully created.                                                                         |
| `UserRejected`             | The user was not created, for a reason defined by the provider.                                            |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
