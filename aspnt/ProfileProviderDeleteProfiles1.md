This method deletes profile properties and information from the data source for the supplied profile collection.

### Declaration

    // C#
    public override int DeleteProfiles(ProfileInfoCollection profileInfoCollection);

### Parameters

- `profileInfoCollection`

  A `ProfileInfoCollection` object that contains profile information for profiles to be deleted.

### Return Value

An integer value indicating the number of profiles that were deleted from the data source.

### Exceptions

`ArgumentException` - One of the following conditions exists:

- The value of `Count` in the `profileInfoCollection` parameter is 0.

- One of the `ProfileInfo` objects in the `profileInfoCollection` collection has an invalid `UserName` property, such as an empty string, exceeds 256 characters, or contains a comma.

`ArgumentNullException` - One of the following conditions exists:

- The `profileInfoCollection` parameter is a null reference.

- One of the `ProfileInfo` objects in `profileInfoCollection` collection has a `UserName` property that is a null reference.

### Remarks

This method deletes all profile properties and information for the supplied profile collection from the data source for the application specified by the `applicationName` attribute in the configuration file. A `ProfileInfoCollection` object can be obtained from the `GetAllProfiles`, `GetAllInactiveProfiles`, `FindProfilesByUserName`, and `FindInactiveProfilesByUserName` methods.

The value returned may be different from the `Count` value of the supplied collection, because some of the profiles in the supplied collection are no longer found in the data source.

The delete profiles operation is a transactional operation. If an error is encountered, the transaction is rolled back and no changes are made.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
