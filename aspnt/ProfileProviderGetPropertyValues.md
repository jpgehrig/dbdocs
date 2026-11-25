This method retrieves profile properties and values from the Oracle profile database.

### Declaration

    // C#
    public override SettingsPropertyValueCollection GetPropertyValues(SettingsContext
      settingsContext, SettingsPropertyCollection settingsPropertyCollection);

### Parameters

- `settingsContext`

  The `SettingsContext` object that contains user profile information.

- `settingsPropertyCollection`

  The `SettingsPropertyCollection` object that contains profile information for the properties to be retrieved.

### Return Value

A `SettingsPropertyValueCollection` object that contains profile property information and values.

### Remarks

This method retrieves profile properties and values from the Oracle database for the user profile specified by the context. Profile properties and values are returned as a collection of `SettingsPropertyValue` objects.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
