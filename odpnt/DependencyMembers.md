`OracleDependency` members are listed in the following tables.

### OracleDependency Constructors

`OracleDependency` constructors are listed in Table 9-1.

Table 9-1 OracleDependency Constructors

| Constructors                                               | Description                                                          |
|:-----------------------------------------------------------|:---------------------------------------------------------------------|
| [OracleDependency Constructors](DependencyConstructors.md) | Instantiates a new instance of `OracleDependency` class (Overloaded) |

### OracleDependency Static Fields

The `OracleDependency` static fields arelisted in Table 9-2.

Table 9-2 OracleDependency Static Fields

| Static Field                                | Description                                                                                                                   |
|:--------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| [Address](DependencyStaticFieldsAddress.md) | Indicates the address that the notification listener listens on, for database notifications<br>Supported in ODP.NET Core only |
| [Port](DependencyStaticFieldsPort.md)       | Indicates the port number that the no tification listener listens on, for database notifications                              |

### OracleDependency Static Methods

`OracleDependency` static methods are listed in Table 9-3.

Table 9-3 OracleDependency Static Methods

| Static Methods                                                       | Description                                                                     |
|:---------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| `Equals`                                                             | Inherited from `System.Object`                                                  |
| [GetOracleDependency](DependencyStaticMethodsGetOracleDependency.md) | Returns an `OracleDependency` instance based on the specified unique identifier |

### OracleDependency Properties

`OracleDependency` properties are listed in Table 9-4.

Table 9-4 OracleDependency Properties

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

### OracleDependency Methods

`OracleDependency` methods are listed in Table 9-5.

Table 9-5 OracleDependency Methods

| Methods                                                                  | Description                                                                     |
|:-------------------------------------------------------------------------|:--------------------------------------------------------------------------------|
| [AddCommandDependency](DependencyInstanceMethodsAddCommandDependency.md) | Binds the `OracleDependency` instance to the specified `OracleCommand` instance |
| `Equals`                                                                 | Inherited from `System.Object`                                                  |
| `GetHashCode`                                                            | Inherited from `System.Object`                                                  |
| `GetType`                                                                | Inherited from `System.Object`                                                  |
| [RemoveRegistration](DependencyInstanceMethodsRemoveRegistration.md)     | Removes the specified dependency between the application and the database       |
| `ToString`                                                               | Inherited from `System.Object`                                                  |

### OracleDependency Events

The `OracleDependency` event is listed in Table 9-6.

Table 9-6 OracleDependency Events

| Event                                   | Description                                                                                                     |
|:----------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| [OnChange](DependencyEventsOnChange.md) | An event that is sent when a database notification associated with the dependency is received from the database |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)
