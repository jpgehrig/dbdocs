This method returns the number of users that are currently accessing the application.

### Declaration

    // C#
    public override int GeNumberOfUsersOnline();

### Return Value

An integer value indicating the total number of users currently accessing the application.

### Remarks

The `GetNumberOfUsersOnline` method returns the number of users of the current application whose last activity date and time is greater than the current date and time less the value (in minutes) of the `Membership.UserIsOnlineTimeWindow` property.

The count includes only users that are associated with the configured `applicationName`.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleMembershipProvider Class](OracleMembershipProviderClass.md)

- [OracleMembershipProvider Members](OracleMembershipProviderMembers.md)
