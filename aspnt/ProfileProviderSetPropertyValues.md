This method updates the Oracle profile database with the specified profile property values.

### Declaration

    // C#
    public override void SetPropertyValues(SettingsContext settingsContext,
       SettingsPropertyValueCollection settingsPropertyValueCollection);

### Parameters

- `settingsContext`

  The `SettingsContext` object that contains user profile information.

- `settingsPropertyValueCollection`

  A `SettingsPropertyValueCollection` object that contains profile information and values for updating the user profile properties.

### Remarks

ASP.NET profile services use this method to update profile properties and values in the Oracle database for the user profile specified by the context.Property values are set at the data source for the application specified by the `applicationName` attribute in the configuration file. Profile properties and values to be updated are specified as a collection of `SettingsPropertyValue` objects.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
