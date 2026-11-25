The `OraclePersonalizationProvider` public methods are listed in Table 8-7.

Table 8-7 OraclePersonalizationProvider Public Methods

| Public Methods                                               | Description                                                                                                                          |
|:-------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| [FindState](PersonalizationProviderFindState.md)             | Returns a collection containing zero or more `PersonalizationStateInfo`-derived objects based on scope and specific query parameters |
| [GetCountOfState](PersonalizationProviderGetCountOfState.md) | Returns the number of rows in the underlying Oracle database that are within the specified scope                                     |
| [Initialize](PersonalizationProviderInitialize.md)           | Initializes the Oracle personalization provider                                                                                      |
| `Equals`                                                     | Inherited from `System.Object` (Overloaded)                                                                                          |
| `ResetPersonalizationState`                                  | Inherited from `System.Web.UI.WebControls.WebParts.PersonalizationProvider`                                                          |
| [ResetState](PersonalizationProviderResetState.md)           | Deletes personalization state information from the underlying data source, based on the specified parameters                         |
| [ResetUserState](PersonalizationProviderResetUserState.md)   | Deletes user personalization data from the underlying Oracle data source, based on the specified parameters                          |
| `GetHashCode`                                                | Inherited from `System.Object`                                                                                                       |
| `GetType`                                                    | Inherited from `System.Object`                                                                                                       |
| `ToString`                                                   | Inherited from `System.Object`                                                                                                       |
| `SavePersonalizationState`                                   | Inherited from `System.Web.UI.WebControls.WebParts.PersonalizationProvider`                                                          |
| `DetermineInitialScope`                                      | Inherited from `System.Web.UI.WebControls.WebParts.PersonalizationProvider`                                                          |
| `DetermineUserCapabilities`                                  | Inherited from` System.Web.UI.WebControls.WebParts.PersonalizationProvider`                                                          |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OraclePersonalizationProvider Class](OraclePersonalizationProviderClass.md)

- [OraclePersonalizationProvider Members](OraclePersonalizationProviderMembers.md)
