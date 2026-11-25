The schema in which the user runs the SQL installation script owns the tables, views, roles, stored procedures, and synonyms that the SQL script creates.

The following schema objects and their tabled information provide descriptions of what privileges each role provides, as well as the relationship between the ASP.NET service methods and the Oracle stored procedure or function.

This section lists the following objects:

- Tables

- Roles

- Views

- Stored Procedures

- Synonyms

### Tables

Table 1-3 lists the tables that are used by each provider.

Table 1-3 Provider Tables

| Oracle Provider | Table                                                                                                                                        |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| Membership      | `ora_aspnet_Membership`<br>`ora_aspnet_Applications`<br>`ora_aspnet_Users`                                                                   |
| Role            | `ora_aspnet_Roles`<br>`ora_aspnet_UsersInRoles`<br>`ora_aspnet_Applications`<br>`ora_aspnet_Users`                                           |
| Profile         | `ora_aspnet_Profile`<br>`ora_aspnet_Applications`<br>`ora_aspnet_Users`                                                                      |
| Personalization | `ora_aspnet_Paths`<br>`ora_aspnet_PersonaliznAllUsers`<br>`ora_aspnet_PersonaliznPerUser`<br>`ora_aspnet_Applications`<br>`ora_aspnet_Users` |
| Web Events      | `ora_aspnet_WebEvents`                                                                                                                       |
| Site Map        | `ora_aspnet_SiteMap`<br>`ora_aspnet_Applications`                                                                                            |
| Session State   | `ora_aspnet_SessionApplications`<br>`ora_aspnet_Sessions`                                                                                    |

### Roles

There are, at most, three types of database roles created for each provider:

- BasicAccess - Provides a database user with access to the provider's basic functionality.

- ReportAccess - Provides a database user with report-oriented data gathering capabilities for a provider.

- FullAccess - Provides a database user with access to all the database objects associated with a provider.

Table 1-4 lists the roles created for each provider.

Table 1-4 Roles and Privileges

| Oracle Provider | Oracle Database Role                                                                               |
|:----------------|:---------------------------------------------------------------------------------------------------|
| Membership      | `ora_aspnet_Mem_BasicAccess`<br>`ora_aspnet_Mem_ReportAccess`<br>`ora_aspnet_Mem_FullAccess`       |
| Role            | `ora_aspnet_Roles_BasicAccess`<br>`ora_aspnet_Roles_ReportAccess`<br>`ora_aspnet_Roles_FullAccess` |
| Profile         | `ora_aspnet_Prof_BasicAccess`<br>`ora_aspnet_Prof_ReportAccess`<br>`ora_aspnet_Prof_FullAccess`    |
| Personalization | `ora_aspnet_Pers_BasicAccess`<br>`ora_aspnet_Pers_ReportAccess`<br>`ora_aspnet_Pers_FullAccess`    |
| Web Events      | `ora_aspnet_Wevnt_FullAccess`                                                                      |
| Site Map        | `ora_aspnet_Smap_FullAccess`                                                                       |
| Session         | `ora_aspnet_Sessn_FullAccess`                                                                      |

### Views

The following tables show the views that are created for each provider. The tables also list the provider-specific database roles that provide access to these views.

#### OracleMembershipProvider Views

Table 1-5 lists the roles and the view access that the roles provide.

Table 1-5 OracleMembershipProvider

| Role                           | View                                                                              |
|:-------------------------------|:----------------------------------------------------------------------------------|
| `ora_aspnet_Mem_BasicAccess`   | (none)                                                                            |
| `ora_aspnet_Mem_ReportAccess ` | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_MemUsers` |
| `ora_aspnet_Mem_FullAccess`    | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_MemUsers` |

#### OracleRoleProvider Views

Table 1-6 lists the roles and the view access that the roles provide.

Table 1-6 OracleRoleProvider

| Role                            | View                                                                                                  |
|:--------------------------------|:------------------------------------------------------------------------------------------------------|
| `ora_aspnet_Roles_BasicAccess`  | (none)                                                                                                |
| `ora_aspnet_Roles_ReportAccess` | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_Roles`<br>`ora_vw_aspnet_UIR` |
| `ora_aspnet_Roles_FullAccess`   | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_Roles`<br>`ora_vw_aspnet_UIR` |

#### OracleProfileProvider Views

Table 1-7 lists the roles and the view access that the roles provide.

Table 1-7 OracleProfileProvider

| Role                           | View                                                                              |
|:-------------------------------|:----------------------------------------------------------------------------------|
| `ora_aspnet_Prof_BasicAccess`  | (none)                                                                            |
| `ora_aspnet_Prof_ReportAccess` | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_Profiles` |
| `ora_aspnet_Prof_FullAccess`   | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users`<br>`ora_vw_aspnet_Profiles` |

#### OraclePersonalizationProvider Views

Table 1-8 lists the roles and the view access that the roles provide.

Table 1-8 OraclePersonalizationProvider

| Role                           | View                                                  |
|:-------------------------------|:------------------------------------------------------|
| `ora_aspnet_Pers_BasicAccess`  | (none)                                                |
| `ora_aspnet_Pers_ReportAccess` | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users` |
| `ora_aspnet_Pers_FullAccess `  | `ora_vw_aspnet_Applications`<br>`ora_vw_aspnet_Users` |

#### OracleSessionStateStore Views

Table 1-9 lists the roles and the view access that the roles provide.

Table 1-9 OracleSessionStateStore

| Role                          | View                      |
|:------------------------------|:--------------------------|
| `ora_aspnet_Sessn_FullAccess` | `ora_vew_aspnet_sessions` |

### Stored Procedures

The following tables list provider-specific database roles and the stored procedures for which the roles provide execution privilege. The tables also list the corresponding ASP.NET service methods that invoke the stored procedures.

#### OracleMembershipProvider Stored Procedures

Table 1-10 lists the service methods and stored procedures that a user with the `ora_aspnet_Mem_BasicAccess` role can execute.

Table 1-10 ora_aspnet_Mem_BasicAccess Role

| Service Method           | Stored Procedure                                                  |
|:-------------------------|:------------------------------------------------------------------|
| `GetNumberOfUsersOnline` | `ora_aspnet_Mem_GetNumOfUsersOn`                                  |
| `GetPassword`            | `ora_aspnet_Mem_GetPassword`                                      |
| `GetUser`                | `ora_aspnet_Mem_GetUserByUid`<br>`ora_aspnet_Mem_GetUserByName`   |
| `GetUserNameByEmail`     | `ora_aspnet_Mem_GetUserByEml`                                     |
| `UpdateUser`             | `ora_aspnet_Mem_UpdateUser`                                       |
| `ValidateUser`           | `ora_aspnet_Mem_GetPwdWithFmt`<br>`ora_aspnet_Mem_UpdateUserInfo` |

Table 1-11 lists the service methods and stored procedures that a user with the `ora_aspnet_Mem_ReportAccess` role can execute.

Table 1-11 ora_aspnet_Mem_ReportAccess Role

| Service Method           | Stored Procedure                                                |
|:-------------------------|:----------------------------------------------------------------|
| `FindUsersByEmail`       | `ora_aspnet_Mem_FindUsersByEml`                                 |
| `FindUsersByName`        | `ora_aspnet_Mem_FindUsersByName`                                |
| `GetAllUsers`            | `ora_aspnet_Mem_GetAllUsers`                                    |
| `GetNumberOfUsersOnline` | `ora_aspnet_Mem_GetNumOfUsersOn`                                |
| `GetUser`                | `ora_aspnet_Mem_GetUserByUid`<br>`ora_aspnet_Mem_GetUserByName` |
| `GetUserNameByEmail`     | `ora_aspnet_Mem_GetUserByEml`                                   |

Table 1-12 lists the service methods and stored procedures that a user with the `ora_aspnet_Mem_FullAccess` role can execute.

Table 1-12 ora_aspnet_Mem_FullAccess Role

| Service Method         | Stored Procedure                 |
|:-----------------------|:---------------------------------|
| All Membership methods | `ora_aspnet_Mem_ChangePwdQAndA`  |
| All Membership methods | `ora_aspnet_Mem_CreateUser`      |
| All Membership methods | `ora_aspnet_Mem_FindUsersByEml`  |
| All Membership methods | `ora_aspnet_Mem_FindUsersByName` |
| All Membership methods | `ora_aspnet_Mem_GetAllUsers`     |
| All Membership methods | `ora_aspnet_Mem_GetNumOfUsersOn` |
| All Membership methods | `ora_aspnet_Mem_GetPassword`     |
| All Membership methods | `ora_aspnet_Mem_GetPwdWithFmt`   |
| All Membership methods | `ora_aspnet_Mem_GetUserByEml`    |
| All Membership methods | `ora_aspnet_Mem_GetUserByName`   |
| All Membership methods | `ora_aspnet_Mem_GetUserByUid`    |
| All Membership methods | `ora_aspnet_Mem_ResetPassword`   |
| All Membership methods | `ora_aspnet_Mem_SetPassword`     |
| All Membership methods | `ora_aspnet_Mem_UnlockUser`      |
| All Membership methods | `ora_aspnet_Mem_UpdateUser`      |
| All Membership methods | `ora_aspnet_Mem_UpdateUserInfo`  |
| All Membership methods | `ora_aspnet_Users_DeleteUser`    |

#### OracleRoleProvider Stored Procedures

Table 1-13 lists the service methods and stored procedures that a user with the `ora_aspnet_Roles_BasicAccess` role can execute.

Table 1-13 ora_aspnet_Roles_BasicAccess Role

| Service Method    | Stored Procedure                 |
|:------------------|:---------------------------------|
| `GetRolesForUser` | `ora_aspnet_UIR_GetRolesForUser` |
| `IsUserInRole`    | `ora_aspnet_UIR_IsUserInRole`    |

Table 1-14 lists the service methods and stored procedures that a user with the `ora_aspnet_Roles_ReportAccess` role can execute.

Table 1-14 ora_aspnet_Roles_ReportAccess Role

| Service Method    | Stored Procedure                 |
|:------------------|:---------------------------------|
| `FindUsersInRole` | `ora_aspnet_UIR_FindUsersInRole` |
| `GetAllRoles`     | `ora_aspnet_Roles_GetAllRoles`   |
| `GetRolesForUser` | `ora_aspnet_UIR_GetRolesForUser` |
| `GetUsersInRole`  | `ora_aspnet_UIR_GetUsersInRoles` |
| `IsUserInRole`    | `ora_aspnet_UIR_IsUserInRole`    |
| `RoleExists`      | `ora_aspnet_Roles_RoleExists`    |

Table 1-15 lists the service methods and stored procedures that a user with the `ora_aspnet_Roles_FullAccess` role can execute.

Table 1-15 ora_aspnet_Roles_FullAccess Role

| Service Method           | Stored Procedure                 |
|:-------------------------|:---------------------------------|
| All Role Manager methods | `ora_aspnet_Roles_CreateRole`    |
| All Role Manager methods | `ora_aspnet_Roles_DeleteRole`    |
| All Role Manager methods | `ora_aspnet_Roles_GetAllRoles`   |
| All Role Manager methods | `ora_aspnet_Roles_RoleExists`    |
| All Role Manager methods | `ora_aspnet_UIR_AddUsersToRoles` |
| All Role Manager methods | `ora_aspnet_UIR_FindUsersInRole` |
| All Role Manager methods | `ora_aspnet_UIR_GetRolesForUser` |
| All Role Manager methods | `ora_aspnet_UIR_GetUsersInRoles` |
| All Role Manager methods | `ora_aspnet_UIR_IsUserInRole`    |
| All Role Manager methods | `ora_aspnet_UIR_RemUsersFmRoles` |

#### OracleProfileProvider Stored Procedures

Table 1-16 lists the service methods and stored procedures that a user with the `ora_aspnet_Prof_BasicAccess` role can execute.

Table 1-16 ora_aspnet_Prof_BasicAccess Role

| Service Method      | Stored Procedure                |
|:--------------------|:--------------------------------|
| `GetPropertyValues` | `ora_aspnet_Prof_GetProperties` |
| `SetPropertyValues` | `ora_aspnet_Prof_SetProperties` |

Table 1-17 lists the service methods and stored procedures that a user with the `ora_aspnet_Prof_ReportAccess` role can execute.

Table 1-17 ora_aspnet_Prof_ReportAccess Role

| Service Method                   | Stored Procedure                  |
|:---------------------------------|:----------------------------------|
| `GetAllProfiles`                 | `ora_aspnet_Prof_GetProfiles`     |
| `GetAllInactiveProfiles`         | `ora_aspnet_Prof_GetProfiles`     |
| `GetNumberOfInactiveProfiles`    | `ora_aspnet_Prof_GetNumOfInactPf` |
| `FindProfilesByUserName`         | `ora_aspnet_Prof_GetProfiles`     |
| `FindInactiveProfilesByUserName` | `ora_aspnet_Prof_GetProfiles`     |

Table 1-18 lists the service methods and stored procedures that a user with the `ora_aspnet_Prof_FullAccess` role can execute.

Table 1-18 ora_aspnet_Prof_FullAccess Role

| Service Method      | Stored Procedure                  |
|:--------------------|:----------------------------------|
| All Profile methods | `ora_aspnet_Prof_DeleteInactPf`   |
| All Profile methods | `ora_aspnet_Prof_DeleteProfiles`  |
| All Profile methods | `ora_aspnet_Prof_GetNumOfInactPf` |
| All Profile methods | `ora_aspnet_Prof_GetProfiles`     |
| All Profile methods | `ora_aspnet_Prof_GetProperties`   |
| All Profile methods | `ora_aspnet_Prof_SetProperties`   |

#### OraclePersonalizationProvider Stored Procedures

Table 1-19 lists the service methods and stored procedures that a user with the `ora_aspnet_Pers_BasicAccess` role can execute.

Table 1-19 ora_aspnet_Pers_BasicAccess Role

| Service Method               | Stored Procedure                                                     |
|:-----------------------------|:---------------------------------------------------------------------|
| `LoadPersonalizationState`   | `ora_aspnet_PPU_GetPgSettings`<br>`ora_aspnet_PAU_GetPgSettings`     |
| `ResetPersonalizationState ` | `ora_aspnet_PPU_ResetPgSettings`<br>`ora_aspnet_PAU_ResetPgSettings` |
| `SavePersonalizationState `  | `ora_aspnet_PPU_SetPgSettings`<br>`ora_aspnet_PAU_SetPgSettings`     |

Table 1-20 lists the service methods and stored procedures that a user with the `ora_aspnet_Pers_ReportAccess` role can execute.

Table 1-20 ora_aspnet_Pers_ReportAccess Role

| Service Method    | Stored Procedure                |
|:------------------|:--------------------------------|
| `FindState`       | `ora_aspnet_PA_FindState`       |
| `GetCountOfState` | `ora_aspnet_PA_GetCountOfState` |

Table 1-21 lists the service methods and stored procedures that a user with the `ora_aspnet_Pers_FullAccess` role can execute.

Table 1-21 ora_aspnet_Pers_FullAccess Role

| Service Method              | Stored Procedure                 |
|:----------------------------|:---------------------------------|
| All Personalization methods | `ora_aspnet_PA_FindState`        |
| All Personalization methods | `ora_aspnet_PA_GetCountOfState`  |
| All Personalization methods | `ora_aspnet_PA_ResetSharedState` |
| All Personalization methods | `ora_aspnet_PA_ResetUserState`   |
| All Personalization methods | `ora_aspnet_PAU_GetPgSettings`   |
| All Personalization methods | `ora_aspnet_PAU_ResetPgSettings` |
| All Personalization methods | `ora_aspnet_PAU_SetPgSettings`   |
| All Personalization methods | `ora_aspnet_PPU_GetPgSettings`   |
| All Personalization methods | `ora_aspnet_PPU_ResetPgSettings` |
| All Personalization methods | `ora_aspnet_PPU_SetPgSettings`   |

#### OracleWebEventProvider Stored Procedures

Table 1-22 lists the service methods and stored procedures that a user with the `ora_aspnet_Wevnt_FullAccess` role can execute.

Table 1-22 ora_aspnet_Wevnt_FullAccess Role

| Service Method        | Stored Procedure          |
|:----------------------|:--------------------------|
| All Web Event methods | `ora_aspnet_LogWebEvents` |

#### OracleSiteMapProvider Stored Procedures

Table 1-23 lists the service methods and stored procedures that a user with the `ora_aspnet_Smap_FullAccess` role can execute.

Table 1-23 ora_aspnet_Smap_FullAccess Role

| Service Method       | Stored Procedure            |
|:---------------------|:----------------------------|
| All Site Map methods | `ora_aspnet_GetSiteMapData` |

#### OracleSessionStateStore Provider Stored Procedures

Table 1-24 lists the service methods and stored procedures that a user with the `ora_aspnet_Sessn_FullAccess` role can execute.

Table 1-24 ora_aspnet_Sessn_FullAccess Role

| Service Method            | Stored Procedure                 |
|:--------------------------|:---------------------------------|
| All Session State methods | `ora_aspnet_SessnApp_SetAppID`   |
| All Session State methods | `ora_aspnet_Sessn_InsUninitItem` |
| All Session State methods | `ora_aspnet_Sessn_RelStateItmEx` |
| All Session State methods | `ora_aspnet_Sessn_RmStateItem`   |
| All Session State methods | `ora_aspnet_Sessn_ResetTimeout`  |
| All Session State methods | `ora_aspnet_Sessn_UpdStateItem`  |
| All Session State methods | `ora_aspnet_Sessn_InsStateItem`  |
| All Session State methods | `ora_aspnet_Sessn_GetStateItem`  |
| All Session State methods | `ora_aspnet_Sessn_GetStateItmEx` |

### Synonyms

Public synonyms are created for all stored procedures so that they can be executed by any user in the database who is granted proper provider-specific roles by the user that owns the stored procedures.
