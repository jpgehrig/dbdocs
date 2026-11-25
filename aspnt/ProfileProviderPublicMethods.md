`OracleProfileProvider` public methods are listed in Table 6-7.

Table 6-7 OracleProfileProvider Public Methods

| Public Methods                                                                     | Description                                                                                                                                      |
|:-----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| [DeleteInactiveProfiles](ProfileProviderDeleteInactiveProfiles.md)                 | Deletes user profile data that has its last activity date on or before the specified date and time                                               |
| [DeleteProfiles](ProfileProviderDeleteProfilesOverloads.md)                        | Deletes profile properties and information from the data source for the supplied profile collection or list of user names (Overloaded)           |
| `Equals`                                                                           | Inherited from `System.Object` (Overloaded)                                                                                                      |
| [FindInactiveProfilesByUserName](ProfileProviderFindInactiveProfilesByUserName.md) | Retrieves inactive profile information for the specified user name                                                                               |
| [FindProfilesByUserName](ProfileProviderFindProfilesByUserName.md)                 | Retrieves profile information for the specified user name                                                                                        |
| [GetAllInactiveProfiles](ProfileProviderGetAllInactiveProfiles.md)                 | Retrieves all profile information for profiles with the last activity date on or before the specified date and time                              |
| [GetAllProfiles](ProfileProviderGetAllProfilesMethod.md)                           | Retrieves all profile information from the data source                                                                                           |
| `GetHashCode`                                                                      | Inherited from `System.Object`                                                                                                                   |
| [GetNumberOfInactiveProfiles](ProfileProviderGetNumberOfInactiveProfiles.md)       | Returns the count of profiles where the last activity date is on or before the specified date and time                                           |
| [GetPropertyValues](ProfileProviderGetPropertyValues.md)                           | Retrieves profile properties and values from the Oracle profile database                                                                         |
| `GetType`                                                                          | Inherited from `System.Object`                                                                                                                   |
| [Initialize](ProfileProviderInitialize.md)                                         | Initializes the `OracleProfileProvider` instance with the property values specified in the ASP.NET application configuration file (`web.config`) |
| [SetPropertyValues](ProfileProviderSetPropertyValues.md)                           | Updates the Oracle profile database with the specified profile property values                                                                   |
| `ToString`                                                                         | Inherited from `System.Object`                                                                                                                   |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleProfileProvider Class](OracleProfileProviderClass.md)

- [OracleProfileProvider Members](OracleProfileProviderMembers.md)
