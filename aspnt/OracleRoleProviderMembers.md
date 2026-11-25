`OracleRoleProvider` members are listed in the following tables.

### OracleRoleProvider Constructors

The `OracleRoleProvider` constructor is listed in Table 3-1.

Table 3-1 OracleRoleProvider Constructor

| Constructor                                                    | Description                                                   |
|:---------------------------------------------------------------|:--------------------------------------------------------------|
| [OracleRoleProvider Constructors](RoleProviderConstructors.md) | Instantiates a new instance of the `OracleRoleProvider` class |

### OracleRoleProvider Static Methods

`OracleRoleProvider` static methods are listed in Table 3-2.

Table 3-2 OracleRoleProvider Static Methods

| Static Methods    | Description                                 |
|:------------------|:--------------------------------------------|
| `Equals`          | Inherited from `System.Object` (Overloaded) |
| `ReferenceEquals` | Inherited from `System.Object`              |

### OracleRoleProvider Public Properties

`OracleRoleProvider` public properties are listed in Table 3-3.

Table 3-3 OracleRoleProvider Public Properties

| Public Properties                                 | Description                                                                                                 |
|:--------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| [ApplicationName](RoleProviderApplicationName.md) | Gets or sets the name of the application that stores the role provider information                          |
| [CommandTimeout](RoleProviderCommandTimeout.md)   | Gets the number of seconds that the command is allowed to execute before it is terminated with an exception |
| `Description`                                     | Inherited from `System.Configuration.Provider.Providerbase`                                                 |
| `Name`                                            | Inherited from `System.Configuration.Provider.Providerbase`                                                 |

### OracleRoleProvider Public Methods

`OracleRoleProvider` public methods are listed in Table 3-4.

Table 3-4 OracleRoleProvider Public Methods

| Public Methods                                              | Description                                                                                                       |
|:------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| [AddUsersToRoles](RoleProviderAddUsersToRoles.md)           | Adds the specified users to the specified roles                                                                   |
| [CreateRole](RoleProviderCreateRole.md)                     | Adds a new role to the database                                                                                   |
| [DeleteRole](RoleProviderDeleteRole.md)                     | Deletes a role in the database                                                                                    |
| `Equals`                                                    | Inherited from `System.Object` (Overloaded)                                                                       |
| [FindUsersInRole](RoleProviderFindUsersInRole.md)           | Returns an array of user names that match the specified user name                                                 |
| [GetAllRoles](RoleProviderGetAllRoles.md)                   | Returns an array of all the roles for an application                                                              |
| `GetHashCode`                                               | Inherited from `System.Object`                                                                                    |
| [GetRolesForUser](RoleProviderGetRolesForUsers.md)          | Returns an array of role names for the specified user                                                             |
| `GetType`                                                   | Inherited from `System.Object`                                                                                    |
| [GetUsersInRole](RoleProviderGetUsersInRole.md)             | Returns an array of users in the specified role name                                                              |
| [Initialize](RoleProviderInitialize.md)                     | Initializes `OracleRoleProvider` with the property values specified in the ASP.NET application configuration file |
| [IsUserInRole](RoleProviderIsUserInRole.md)                 | Indicates whether the specified user is in the specified role                                                     |
| [RemoveUsersFromRoles](RoleProviderRemoveUsersFromRoles.md) | Removes the specified array of users from the specified array of role names                                       |
| [RoleExists](RoleProviderRoleExists.md)                     | Indicates whether the specified role name exists in the database                                                  |
| `ToString`                                                  | Inherited from `System.Object`                                                                                    |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleRoleProvider Class](OracleRoleProviderClass.md)
