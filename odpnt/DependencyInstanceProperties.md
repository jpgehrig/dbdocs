`OracleDependency` properties are listed in Table 9-9.

Table 9-9 OracleDependency Properties

| Properties                                                                      | Description                                                                                                                    |
|:--------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| [DataSource](DependencyInstancePropertiesDataSource.md)                         | Indicates the data source associated with the `OracleDependency` instance                                                      |
| [HasChanges](DependencyInstancePropertiesHasChanges.md)                         | Indicates whether or not there is any change in the database associated with this dependency                                   |
| [Id](DependencyInstancePropertiesId.md)                                         | Represents the unique identifier for the `OracleDependency` instance                                                           |
| [IsEnabled](DependencyInstancePropertiesIsEnabled.md)                           | Specifies whether or not the dependency is enabled between the application and the database                                    |
| [QueryBasedNotification](DependencyInstancePropertiesQueryBasedNotification.md) | Specifies whether the change notification registration is object-based or query-based                                          |
| [RegisteredQueryIDs](DependencyInstancePropertiesRegisteredQueryIDs.md)         | Provides a list of `CHANGE_NOTIFICATION_QUERY_ID`s                                                                             |
| [RegisteredResources](DependencyInstancePropertiesRegisteredResources.md)       | Indicates the database resources that are registered in the notification registration                                          |
| [RowidInfo](DependencyInstancePropertiesRowidInfo.md)                           | Specifies whether or not `ROWID` information is part of change notification events fired whenever data changes on the database |
| [UserName](DependencyInstancePropertiesUserName.md)                             | Indicates the database user name associated with the `OracleDependency` instance                                               |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
