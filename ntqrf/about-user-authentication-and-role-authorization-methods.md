Describes how user login credentials are authenticated and database roles are authorized in Windows domains.

User authentication and role authorization are defined in User Authentication and Role Authorization Defined.

Table 10-1 User Authentication and Role Authorization Defined

| Feature             | Description                                                                                       | More Information                                                                   |
|:--------------------|:--------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|
| User authentication | Process by which the database uses the user's Windows login credentials to authenticate the user. | [Oracle Database 2 Day DBA ](../admqs/administering-user-accounts-and-security.md) |
| Role authorization  | Process of granting an assigned set of roles to authenticated users.                              | [Oracle Database 2 Day DBA ](../admqs/administering-user-accounts-and-security.md) |

Oracle Database supports user authentication and role authorization in Windows domains. Basic Features of User Authentication and Role Authorization describes these basic features.

Table 10-2 Basic Features of User Authentication and Role Authorization

| Feature                          | Description                                                                                                                                                                                                                                                               |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication of external users | Users are authenticated by the database using the user's Windows login credentials enabling them to access Oracle Database without being prompted for additional login credentials.                                                                                       |
| Authorization of external roles  | Roles are authorized using Windows local groups. Once an external role is created, you can grant or revoke that role to a database user. Initialization parameter `OS_ROLES` is set to `false` by default. You must set `OS_ROLES` to `true` to authorize external roles. |

- [About Using Authentication and Authorization Methods](about-using-authentication-and-authorization-methods.md)
  User Authentication and Role Authorization Methods describes user authentication and role authorization methods to use based on your Oracle Database environment:

**Parent topic:** [Authenticating Database Users with Windows](authenticating-database-users-with-windows.md)
