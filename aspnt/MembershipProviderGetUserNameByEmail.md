This method returns the user name associated with the specified e-mail address.

### Declaration

    // C#
    public override string GetUserNameByEmail(string emailAddress);

### Parameters

- `emailAddress`

  The email address to search for.

### Return Value

The user name associated with the specified e-mail address. If no match is found, then it returns a null reference.

### Exceptions

`ArgumentException` - E-mail address exceeds 256 characters.

`System.Configuration.Provider.ProviderException` - More than one user with the same e-mail address exists in the database and the `RequiresUniqueEmail` property is `true`.

### Remarks

If the value of the `RequiresUniqueEmail` property is `true`, then a unique e-mail address must be associated with each user name.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
