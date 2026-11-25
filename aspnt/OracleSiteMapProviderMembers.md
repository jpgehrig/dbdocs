`OracleSiteMapProvider` members are listed in the following tables.

### OracleSiteMapProvider Constructors

The `OracleSiteMapProvider` constructor is listed in Table 4-1.

Table 4-1 OracleSiteMapProvider Constructor

| Constructor                                                          | Description                                                      |
|:---------------------------------------------------------------------|:-----------------------------------------------------------------|
| [OracleSiteMapProvider Constructors](SiteMapProviderConstructors.md) | Instantiates a new instance of the `OracleSiteMapProvider` class |

### OracleSiteMapProvider Static Methods

`OracleSiteMapProvider` static methods are listed in Table 4-2.

Table 4-2 OracleSiteMapProvider Static Methods

| Static Methods    | Description                                 |
|:------------------|:--------------------------------------------|
| `Equals`          | Inherited from `System.Object` (Overloaded) |
| `ReferenceEquals` | Inherited from `System.Object`              |

### OracleSiteMapProvider Public Properties

`OracleSiteMapProvider` public properties are listed in Table 4-3.

Table 4-3 OracleSiteMapProvider Public Properties

| Public Properties                            | Description                                                                                                 |
|:---------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| [ApplicationName](SiteMapApplicationName.md) | Gets or sets the name of the application that differentiates site map data for different applications       |
| [CommandTimeout](SiteMapCommandTimeout.md)   | Gets the number of seconds that the command is allowed to execute before it is terminated with an exception |
| `CurrentNode`                                | Inherited from `System.Web.SiteMapProvider` (Read-Only)                                                     |
| `Description`                                | Inherited from `System.Configuration.Provider.Providerbase`                                                 |
| `EnableLocalization`                         | Inherited from `System.Web.SiteMapProvider`                                                                 |
| `Name`                                       | Inherited from `System.Configuration.Provider.Providerbase`                                                 |
| `ParentProvider`                             | Inherited from `System.Web.SiteMapProvider`                                                                 |
| `ResourceKey`                                | Inherited from `System.Web.SiteMapProvider`                                                                 |
| `RootNode`                                   | Inherited from `System.Web.SiteMapProvider` (Read-Only)                                                     |
| `RootProvider`                               | Inherited from `System.Web.SiteMapProvider`                                                                 |
| `SecurityTrimmingEnabled`                    | Inherited from `System.Web.SiteMapProvider`                                                                 |

### OracleSiteMapProvider Public Methods

`OracleSiteMapProvider` public methods are listed in Table 4-4.

Table 4-4 OracleSiteMapProvider Public Methods

| Public Methods                                            | Description                                                                                                                       |
|:----------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------|
| [`BuildSiteMap`](SiteMapProviderBuildSiteMap.md)          | Builds a `SiteMap` tree of the `SiteMapNode` objects by loading site map data from an Oracle database                             |
| [`Dispose`](SiteMapProviderDispose.md)                    | Releases all the resources for this instance                                                                                      |
| `FindSiteMapNode`                                         | Inherited from `System.Web.StaticSiteMapProvider`                                                                                 |
| `FindSiteMapNodeFromKey`                                  | Inherited from `System.Web.StaticSiteMapProvider`                                                                                 |
| `GetChildNodes`                                           | Inherited from `System.Web.StaticSiteMapProvider`                                                                                 |
| `GetCurrentNodeAndHintAncestorNodes`                      | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `GetCurrentNodeAndHintNeighborhoodNodes`                  | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `GetParentNode`                                           | Inherited from `System.Web.StaticSiteMapProvider`                                                                                 |
| `GetParentNodeRelativeToCurrentNodeAndHintDownFromParent` | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `GetParentNodeRelativeToNodeAndHintDownFromParent`        | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `HintAncestorNodes`                                       | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `IsAccessibleToUser`                                      | Inherited from `System.Web.SiteMapProvider`                                                                                       |
| `GetHashCode`                                             | Inherited from `System.Object`                                                                                                    |
| `GetType`                                                 | Inherited from `System.Object`                                                                                                    |
| [`Initialize`](SiteMapProviderInitialize.md)              | Initializes the `OracleSiteMapProvider` instance with the property values specified in the ASP.NET application configuration file |
| `ToString`                                                | Inherited from `System.Objec`t                                                                                                    |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSiteMapProvider Class](OracleSiteMapProviderClass.md)
