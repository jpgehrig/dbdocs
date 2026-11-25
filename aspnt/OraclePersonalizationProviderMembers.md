`OraclePersonalizationProvider` members are listed in the following tables.

### OraclePersonalizationProvider Constructors

The `OraclePersonalizationProvider` constructor is listed in Table 8-1.

Table 8-1 OraclePersonalizationProvider Constructor

| Constructor                                                                          | Description                                                              |
|:-------------------------------------------------------------------------------------|:-------------------------------------------------------------------------|
| [OraclePersonalizationProvider Constructors](PersonalizationProviderConstructors.md) | Instantiates a new instance of the `OraclePersonalizationProvider` class |

### OraclePersonalizationProvider Static Methods

`OraclePersonalizationProvider` static methods are listed in Table 8-2.

Table 8-2 OraclePersonalizationProvider Static Methods

| Static Methods    | Description                    |
|:------------------|:-------------------------------|
| `Equals`          | Inherited from `System.Object` |
| `ReferenceEquals` | Inherited from `System.Object` |

### OraclePersonalizationProvider Public Properties

`OraclePersonalizationProvider` public properties are listed in Table 8-3.

Table 8-3 OraclePersonalizationProvider Public Properties

| Public Properties                                            | Description                                                                                                             |
|:-------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| [ApplicationName](PersonalizationProviderApplicationName.md) | Gets or sets the name of the application that is used to specify personalization information specific to an application |
| [CommandTimeout](PersonalizationProviderCommandTimeout.md)   | Gets the number of seconds that the command is allowed to execute before it is terminated with an exception             |
| `Description`                                                | Inherited from `System.Configuration.Provider.Providerbase`                                                             |
| `Name`                                                       | Inherited from `System.Configuration.Provider.Providerbase`                                                             |

### OraclePersonalizationProvider Public Methods

`OraclePersonalizationProvider` public methods are listed in Table 8-4.

Table 8-4 OraclePersonalizationProvider Public Methods

| Public Methods                                               | Description                                                                                                                          |
|:-------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| [FindState](PersonalizationProviderFindState.md)             | Returns a collection containing zero or more `PersonalizationStateInfo`-derived objects based on scope and specific query parameters |
| [GetCountOfState](PersonalizationProviderGetCountOfState.md) | Returns the number of rows in the underlying Oracle database that are within the specified scope                                     |
| [Initialize](PersonalizationProviderInitialize.md)           | Initializes the Oracle personalization provider                                                                                      |
| `Equals`                                                     | Inherited from `System.Object` (Overloaded)                                                                                          |
| `ResetPersonalizationState`                                  | Inherited from `System.Web.UI.WebControls.WebParts. PersonalizationProvider`                                                         |
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
