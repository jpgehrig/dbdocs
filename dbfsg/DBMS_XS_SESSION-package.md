## 11.1 DBMS_XS_SESSIONS Package

The `DBMS_XS_SESSIONS` package manages an application session.

This section includes the following topics:

- Security Model

- Constants

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of DBMS_XS_SESSIONS Subprograms

### 11.1.1 Security Model

The `DBMS_XS_SESSIONS` package is created in the `SYS` schema. The privilege to execute the package is granted to `PUBLIC`. The executing user must have the appropriate privilege for the particular operation.

### 11.1.2 Constants

The following constants define operation codes passed into namespace event handling functions:

    attribute_first_read_operation CONSTANT PLS_INTEGER := 1;
    modify_attribute_operation     CONSTANT PLS_INTEGER := 2;

The following constants represent bit values that identify events of interest for a particular attribute in a namespace that has an event handling function:

    attribute_first_read_event     CONSTANT PLS_INTEGER := 1;
    modify_attribute_event         CONSTANT PLS_INTEGER := 2;

The following constants define return codes that can be returned by a namespace event handling function:

    event_handling_succeeded       CONSTANT PLS_INTEGER := 0;
    event_handling_failed          CONSTANT PLS_INTEGER := 1;

The following constants are used as input into the `ADD_GLOBAL_CALLBACK`, `DELETE_GLOBAL_CALLBACK`, and `ENABLE_GLOBAL_CALLBACK` procedures:

    create_session_event       CONSTANT PLS_INTEGER := 1;
    attach_session_event       CONSTANT PLS_INTEGER := 2;
    guest_to_user_event        CONSTANT PLS_INTEGER := 3;
    proxy_to_user_event        CONSTANT PLS_INTEGER := 4;
    revert_to_user_event       CONSTANT PLS_INTEGER := 5;
    enable_role_event          CONSTANT PLS_INTEGER := 6;
    disable_role_event         CONSTANT PLS_INTEGER := 7;
    enable_dynamic_role_event  CONSTANT PLS_INTEGER := 8;
    disable_dynamic_role_event CONSTANT PLS_INTEGER := 9;
    detach_session_event       CONSTANT PLS_INTEGER := 10;
    terminate_session_event    CONSTANT PLS_INTEGER := 11;
    direct_login_event         CONSTANT PLS_INTEGER := 12;
    direct_logoff_event        CONSTANT PLS_INTEGER := 13;

### 11.1.3 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    CREATE OR REPLACE TYPE DBMS_XS_NSATTR AS OBJECT (
      --- Member variables
      namespace        varchar2(130),
      attribute        varchar2(4000),
      attribute_value  varchar2(4000),

      --- Constructor for DBMS_XS_NSATTR type
      --- Only namespace name is mandatory
      CONSTRUCTOR FUNCTION DBMS_XS_NSATTR(
         namespace         IN VARCHAR2,
         attribute         IN VARCHAR2 DEFAULT NULL,
         attribute_value   IN VARCHAR2 DEFAULT NULL)
      RETURN SELF AS RESULT);

    CREATE OR REPLACE PUBLIC SYNONYM DBMS_XS_NSATTR FOR SYS.DBMS_XS_NSATTR;
    CREATE OR REPLACE TYPE DBMS_XS_NSATTRLIST AS VARRAY(1000) OF DBMS_XS_NSATTR;
    CREATE OR REPLACE PUBLIC SYNONYM DBMS_XS_NSATTRLIST FOR SYS.DBMS_XS_NSATTRLIST;
    GRANT EXECUTE ON DBMS_XS_NSATTR TO PUBLIC;
    GRANT EXECUTE ON DBMS_XS_NSATTRLIST TO PUBLIC;
    CREATE OR REPLACE PUBLIC SYNONYM DBMS_XS_SESSIONS FOR SYS.DBMS_XS_SESSIONS;
    GRANT EXECUTE ON DBMS_XS_SESSIONS TO PUBLIC;

### 11.1.4 Summary of DBMS_XS_SESSIONS Subprograms

Table 11-2 Summary of DBMS_XS_SESSIONS Subprograms

| Subprogram                       | Description                                                                                                                               |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| CREATE_SESSION Procedure         | Creates a new application session for the specified application user name.                                                                |
| ATTACH_SESSION Procedure         | Attaches the current traditional database session to the application session identified by the session ID.                                |
| ASSIGN_USER Procedure            | Assigns a named user to the currently attached anonymous Real Application Security session.                                               |
| SWITCH_USER Procedure            | Switches the application user in the currently attached session.                                                                          |
| CREATE_NAMESPACE Procedure       | Creates a new application namespace in the currently attached application session.                                                        |
| CREATE_ATTRIBUTE Procedure       | Creates a new custom attribute for the specified application namespace in the currently attached application session.                     |
| SET_ATTRIBUTE Procedure          | Sets a new value for the specified attribute in the namespace in the currently attached application session.                              |
| GET_ATTRIBUTE Procedure          | Gets the value of an attribute in the namespace in the currently attached application session.                                            |
| RESET_ATTRIBUTE Procedure        | Resets an application namespace attribute to its original value in the specified namespace in the currently attached application session. |
| DELETE_ATTRIBUTE Procedure       | Deletes the specified attribute from the specified namespace in the currently attached application session.                               |
| DELETE_NAMESPACE Procedure       | Deletes the specified namespace and its attributes from the currently attached application session.                                       |
| ENABLE_ROLE Procedure            | Enables a real application role in the currently attached application session.                                                            |
| DISABLE_ROLE Procedure           | Disables a real application role from the currently attached application session.                                                         |
| SET_SESSION_COOKIE Procedure     | Sets a new cookie value with the specified session ID.                                                                                    |
| REAUTH_SESSION Procedure         | Updates the last authentication time for the session identified by specified session ID.                                                  |
| SET_INACTIVITY_TIMEOUT Procedure | Sets an inactivity timeout value, in minutes, for the specified session.                                                                  |
| SAVE_SESSION Procedure           | Saves or persists the changes performed in the currently attached session.                                                                |
| DETACH_SESSION Procedure         | Detaches the current traditional database session from the application session to which it is attached.                                   |
| DESTROY_SESSION Procedure        | Destroys or terminates the session specified by the session ID.                                                                           |
| ADD_GLOBAL_CALLBACK Procedure    | Registers an existing event handler with the database.                                                                                    |
| ENABLE_GLOBAL_CALLBACK Procedure | Enables or disables the global callback for the session event specified by the `event_type` parameter.                                    |
| DELETE_GLOBAL_CALLBACK Procedure | Deletes an existing global callback association.                                                                                          |

This section describes the following DBMS_XS_SESSIONS subprograms:

#### 11.1.4.1 CREATE_SESSION Procedure

The `CREATE_SESSION` procedure creates a new application session for the specified user name. It returns a session identifier that you can use to reference the session in future calls.

The session can be created with a regular application user or an external application user. The session can be created in trusted mode or secure mode. In trusted mode, data security checks are bypassed; in secure mode, they are enforced.

The combination of regular session in trusted mode is not supported. Other combinations, regular session in secure mode, external session in trusted mode, or external session in secure mode are supported.

The `namespaces` parameter is a list of triplet namespaces to be created, the attribute to be created, and the attribute value to be set. This is an optional parameter. The default value is `NULL`. The `XS$GLOBAL_VAR` and `XS$SESSION` namespaces and their attributes are always available to the session.

This function does not attach the current traditional session to the newly created application session. Use the ATTACH_SESSION Procedure to perform this task.

The user executing the procedure must have the `CREATE_SESSION` application privilege for the application user specified by the `username` parameter. You can also specify a list of namespaces to be created when the session is created. If you specify namespaces during creation of the session, the caller is required to be granted application privileges `MODIFY_NAMESPACE` or `MODIFY_ATTRIBUTE` on the namespaces, or be granted the `ADMIN_NAMESPACE` system privilege.

##### Syntax

    CREATE_SESSION (
     username      IN  VARCHAR2,
     sessionid     OUT NOCOPY RAW,
     is_external   IN  BOOLEAN DEFAULT FALSE,
     is_trusted    IN  BOOLEAN DEFAULT FALSE,
     namespaces    IN  DBMS_XS_NSATTRLIST DEFAULT NULL,
     cookie        IN  VARCHAR2 DEFAULT NULL);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `username`    | The name of a regular application user or an external application user for which to create the application session.<br>To find a listing of the user names and application roles for the current session, query the [DBA_XS_USERS](real-application-security-data-dictionary-views.md) data dictionary view. To find all application users and roles, query the [DBA_XS_PRINCIPALS](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>Users:<br>`SELECT NAME FROM DBA_XS_USERS;`<br>Roles:<br>`SELECT NAME FROM DBA_XS_ROLES;`<br>`SELECT NAME FROM DBA_XS_DYNAMIC_ROLES;` |
| `sessionid`   | Session ID of the newly created application session. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.                                                                                                                                                                                                                                                                                                                                                           |
| `is_external` | Specifies whether the session is to be created as an external principal session. This is an optional parameter. The default value is `FALSE`, indicating that a regular session is to be created. A `NULL` value is taken to mean `FALSE`.                                                                                                                                                                                                                                                                                                                                                                       |
| `is_trusted`  | Specifies if the session is to be created in trusted mode or secure mode. In trusted mode, data security checks are bypassed; in secure mode, they are enforced. This is an optional parameter. The default value is `FALSE`, indicating secure mode. A `NULL` value is taken to mean `FALSE`.                                                                                                                                                                                                                                                                                                                   |
| `namespaces`  | The list of name, attribute, and attribute value triplet. If the namespace is not accessible to the session or no such namespace template exists, an error is thrown.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `cookie`      | Specifies the server cookie to be set for the session. This is an optional parameter. The default value is `NULL`. The maximum allowed length of the cookie is 1024 bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                       |

##### Examples

    DECLARE
      nsList DBMS_XS_NSATTRLIST;
      sessionid RAW(16);
    BEGIN
        nsList := DBMS_XS_NSATTRLIST(DBMS_XS_NSATTR('ns1'),DBMS_XS_NSATTR('ns2'));
        SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid, FALSE, FALSE, nsList);
    END;

#### 11.1.4.2 ATTACH_SESSION Procedure

The `ATTACH_SESSION` procedure attaches the current traditional database session to the application session identified by the session ID (`session_id`). The attached session enables the roles granted (directly or indirectly) to the application user with which the session was created and the session scope dynamic application roles that were enabled until the last detach of this session. If you execute `ATTACH_SESSION` with a list of dynamic application roles using the optional parameter `enable_dynamic_roles`, the provided dynamic application roles are enabled for the session. To disable a list of dynamic roles, specify the list using the optional parameter `disable_dynamic_roles`.

You can specify a list of triplet values (namespace, attribute, attribute value) during the attach operation. The namespaces and attributes are then created and attribute values set. This is in addition to any namespaces and attributes that were present in the session.

To execute this procedure, the traditional session user must have the `ATTACH_SESSION` application privilege. If you specify namespaces, then the user is required to be granted application privileges `MODIFY_NAMESPACE` or `MODIFY_ATTRIBUTE` on the namespaces, or `ADMIN_NAMESPACE` system privilege.

A self password change is allowed using the SQL\*Plus `PASSWORD` command if invoked from an explicitly attached session (a session attached using the `ATTACH_SESSION` procedure or the `attachSession()` method in Java), provided that session has the `ALTER_USER` privilege and the user name is provided with the `PASSWORD` command.

##### Syntax

    ATTACH_SESSION (
     sessionid              IN RAW,
     enable_dynamic_roles   IN XS$NAME_LIST         DEFAULT NULL,
     disable_dynamic_roles  IN XS$NAME_LIST         DEFAULT NULL,
     external_roles         IN XS$NAME_LIST         DEFAULT NULL,
     authentication_time    IN TIMESTAMP WITH TIME ZONE DEFAULT NULL,
     namespaces             IN DBMS_XS_NSATTRLIST   DEFAULT NULL);

##### Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sessionid`             | Session ID of the application session. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `enable_dynamic_roles`  | A list of dynamic roles to be granted to be enabled in the application session. This is an optional parameter. If any of the dynamic roles specified does not exist, the attach session fails. If the session is an external principal session, a list of external roles can be specified for enabling. These roles will remain enabled until detach and will not be enabled in the next attach by default.<br>To find a listing of the application roles for the current session, query the [DBA_XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view. To find a listing of all dynamic application roles, query the [DBA_XS_PRINCIPALS](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT NAME, TYPE FROM DBA_XS_PRINCIPALS; ` |
| `disable_dynamic_roles` | A list of dynamic roles to be disabled from the session. This is an optional parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `external_roles`        | A list of external roles if the session is an external principal session. This is an optional parameter. These external roles remain enabled until a detach operation and are not enabled again in the next attach by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `authentication_time`   | The updated authentication time for the session. This is an optional parameter. The time must be specified in the following format:<br>`YYYY-MM-DD HH:MI:SS.FF TZR`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `namespaces`            | The list of name, attribute, and attribute value triplet. If the namespace is not accessible to the session or no such namespace template exists, an error is thrown.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

##### Examples

    DECLARE
      nsList DBMS_XS_NSATTRLIST;
      sessionid RAW(16);
    BEGIN
        nsList := DBMS_XS_NSATTRLIST(DBMS_XS_NSATTR('ns1'),DBMS_XS_NSATTR('ns2'));
        SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid);
        SYS.DBMS_XS_SESSIONS.ATTACH_SESSION(sessionid, NULL, NULL, NULL, NULL, nsList);
    END;

#### 11.1.4.3 ASSIGN_USER Procedure

The `ASSIGN_USER` procedure assigns a named application user to the currently attached anonymous application session.

Roles enabled in the current session are retained after this operation. The optional parameters `enable_dynamic_roles` and `disable_dynamic_roles` specify the additional lists of dynamic roles to be enabled or disabled. If the assigned user is external, you can specify a list of external roles to be enabled.

You can specify a list of triplet values (namespace, attribute, attribute value) during the assign operation. The namespaces and attributes are then created in the session and attribute values set. This is in addition to any namespaces and attributes that were already present in the session.

To execute this procedure, the dispatcher or connection user must have the `ASSIGN_USER` application privilege. If you specify namespaces, then the user is required to be granted application privileges `MODIFY_NAMESPACE` or `MODIFY_ATTRIBUTE` on the namespaces, or `ADMIN_NAMESPACE` system privilege.

##### Syntax

    DBMS_XS_SESSIONS.ASSIGN_USER (
     username              IN VARCHAR2,
     is_external           IN BOOLEAN                  DEFAULT FALSE,
     enable_dynamic_roles  IN XS$NAME_LIST             DEFAULT NULL,
     disable_dynamic_roles IN XS$NAME_LIST             DEFAULT NULL,
     external_roles        IN XS$NAME_LIST             DEFAULT NULL,
     authentication_time   IN TIMESTAMP WITH TIME ZONE DEFAULT NULL,
     namespaces            IN DBMS_XS_NSATTRLIST       DEFAULT NULL);

##### Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `username`              | The name of the real application user.<br>To find a listing of existing application users, query the [DBA_XS_PRINCIPALS](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT NAME FROM DBA_XS_PRINCIPALS;`                                                                                                                                                                                                                                                 |
| `is_external`           | Specifies whether the named application user is an external user. This is an optional parameter. The default value is `FALSE`, indicating that a regular application user is assigned. A `NULL` value is taken to mean `FALSE`.                                                                                                                                                                                                                                                                        |
| `enable_dynamic_roles`  | A list of dynamic roles to be enabled in an application session. This is an optional parameter.<br>To find a listing of the application roles for the current session, query the [V\$XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view. To find a listing of all dynamic application roles, query the [DBA_XS_DYNAMIC_ROLES](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT NAME FROM DBA_XS_DYNAMIC_ROLES;` |
| `disable_dynamic_roles` | A list of dynamic roles to be disabled from the session. This is an optional parameter.                                                                                                                                                                                                                                                                                                                                                                                                                |
| `external_roles`        | A list of external roles if the application user is an external application user. This is an optional parameter.                                                                                                                                                                                                                                                                                                                                                                                       |
| `authentication_time`   | The updated authentication time for the session. This is an optional parameter. The time must be specified in the following format:<br>`YYYY-MM-DD HH:MI:SS.FF TZR`                                                                                                                                                                                                                                                                                                                                    |
| `namespaces`            | The list of name, attribute, and attribute value triplet. If the namespace is not accessible to the session or no such namespace template exists, an error is thrown.                                                                                                                                                                                                                                                                                                                                  |

##### Examples

    DECLARE
      nsList DBMS_XS_NSATTRLIST;
      sessionid RAW(16);
    BEGIN
      nsList := DBMS_XS_NSATTRLIST(DBMS_XS_NSATTR('ns1'),DB);
      SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid);
      SYS.DBMS_XS_SESSIONS.ATTACH_SESSION(sessionid);
      SYS.DBMS_XS_SESSIONS.ASSIGN_USER(username => 'lwuser2',
                                       namespaces => nsList);
    END;

#### 11.1.4.4 SWITCH_USER Procedure

The `SWITCH_USER` procedure switches the application user in the currently attached session. The current application user must be a proxy user for the target application user before performing the switch operation by using the `XS_PRINCIPAL.ADD_PROXY_USER` PL/SQL API to acquire the proxy of another application user privilege. The list of filtering application roles of the target user gets enabled in the session.

You can retain current application namespaces of the session or discard them. You can also specify a list of namespaces to be created and attribute values to be set after the switch. If you specify namespaces, then the user is required to be granted application privileges `MODIFY_NAMESPACE` or `MODIFY_ATTRIBUTE` on the namespaces, or `ADMIN_NAMESPACE` system privilege.

##### Syntax

    SWITCH_USER (
     username          IN VARCHAR2,
     keep_state        IN BOOLEAN              DEFAULT FALSE,
     namespaces        IN DBMS_XS_NSATTRLIST   DEFAULT NULL);

##### Parameters

| Parameter    | Description                                                                                                                                                                                                                                                               |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `username`   | User name of the user whose security context you want to switch to.<br>To find a listing of existing application users, query the [DBA_XS_USERS](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT NAME FROM DBA_XS_USERS;` |
| `keep_state` | Controls whether application namespaces are retained.<br>Possible values are:<br>• `TRUE`: Sets all other session states to remain unchanged.<br>• `FALSE`: Clears the previous state in the session. The default value.                                                  |
| `namespaces` | The list of name, attribute, and attribute value triplet. If the namespace is not accessible to the session or no such namespace template exists, an error is thrown.                                                                                                     |

##### Examples

    DECLARE
      nsList := DBMS_XS_NSATTRLIST(DBMS_XS_NSATTR('ns1'),DBMS_XS_NSATTR('ns2'));
      sessionid RAW(16);
    BEGIN
      SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid);
      SYS.DBMS_XS_SESSIONS.ATTACH_SESSION(sessionid);
      SYS.DBMS_XS_SESSIONS.SWITCH_USER(username => 'lwuser2',
                                       keep_state => TRUE,
                                       namespaces => nsList);
    END;

#### 11.1.4.5 CREATE_NAMESPACE Procedure

The `CREATE_NAMESPACE` procedure creates a new namespace in the currently attached application session. The namespace template corresponding to the namespace must exist in the system, else this operation throws an error. After this operation, the namespace along with its attributes as they are created in the template are available to the session.

The calling user must have the `MODIFY_NAMESPACE` application privilege.

##### Syntax

    CREATE_NAMESPACE(
     namespace      IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The name of the namespace to create. There must be an existing namespace template document with this name. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions.<br>You can query the `DBA_XS_NS_TEMPLATES` and `DBA_XS_NS_TEMPLATE_ATTRIBUTES` data dictionary views for a list of namespace templates and attributes. |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.CREATE_NAMESPACE('J_NS1');
    END;

#### 11.1.4.6 CREATE_ATTRIBUTE Procedure

The `CREATE_ATTRIBUTE` procedure creates a new custom attribute in the specified namespace in the currently attached application session. If the namespace is not already available in the session or no such namespace templates exist, an error is thrown.

The calling user is required to be granted the `MODIFY_ATTRIBUTE` application privilege.

##### Syntax

    PROCEDURE create_attribute(
    namespace IN VARCHAR2,
    attribute IN VARCHAR2,
    value     IN VARCHAR2    DEFAULT NULL,
    eventreg  IN PLS_INTEGER DEFAULT NULL);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The namespace in which the attribute gets created. If the namespace does not exist in the session, an error is thrown. The maximum size of the case sensitive character string is 128 characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `attribute` | The name of the attribute to be created. The maximum size of the case sensitive character string is 4000 characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `value`     | The default value for the attribute. The maximum size of the case sensitive character string is 4000 characters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `eventreg`  | The event for which the handler is executed for the attribute. This is an optional parameter. This parameter can take the following values:<br>• `DBMS_XS_SESSIONS.attribute_first_read_event`<br>• The handler function is called whenever an attribute get request is received and the value for the attribute has not been set. This event can be registered only if the default value is set to `NULL`. This value corresponds with the `FIRSTREAD_EVENT` constant in the `XS_NAMESPACE` package or Admin API.<br>• `DBMS_XS_SESSIONS``.modify_attribute_event`:<br>• The handler function is called whenever an attribute set request is received. This value corresponds with the `UPDATE_EVENT` constant in the in the `XS_NAMESPACE` package or Admin API.<br>If the attribute is registered for first read event, then the handler is executed if the attribute is uninitialized, before returning the value. If the update event is registered, the handler gets called whenever the attribute is modified. Events can be registered only if the namespace has an event handler, else an error is thrown. |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.CREATE_ATTRIBUTE('NS1','NS1CUSTOM','NS1CUSTOMDEFAULT');
    END;

    -- Example with firstRead event set
    BEGIN
    SYS.DBMS_XS_SESSIONS.create_Attribute('ns1','attr4',NULL,
                                           DBMS_XS_SESSIONS.attribute_first_read_event);
    END;

#### 11.1.4.7 SET_ATTRIBUTE Procedure

The `SET_ATTRIBUTE` procedure sets a new value for the specified attribute in the namespace associated with the currently attached session. The handler function is called if the `update` event is set for the attribute. If the namespace does not exist or is deleted, an error is thrown. If there is no template corresponding to the namespace that exists, an error is thrown.

The calling user is required to be granted the `MODIFY_ATTRIBUTE` application privilege.

##### Syntax

    SET_ATTRIBUTE (
     namespace    IN VARCHAR2,
     attribute    IN VARCHAR2,
     value        IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | Name of the namespace associated with the attribute. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions.<br>You can query the `DBA_XS_NS_TEMPLATES` and `DBA_XS_NS_TEMPLATE_ATTRIBUTES` data dictionary views for a list of namespace templates and attributes. |
| `attribute` | Name of an existing attribute in an existing namespace.<br>To find a listing of existing namespace attributes, query the [V\$XS_SESSION_NS_ATTRIBUTES](real-application-security-data-dictionary-views.md) data dictionary view.                                                                                                                                                                                                                                                                                                                                          |
| `value`     | New value for the attribute. The maximum size of the case sensitive character string is 4000 characters.<br>To find an listing of existing values associated with the attribute, query the [V\$XS_SESSION_NS_ATTRIBUTES](real-application-security-data-dictionary-views.md) data dictionary view.                                                                                                                                                                                                                                                                        |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.SET_ATTRIBUTE('J_NS','JohnNSAttr1','John bio');
    END;

#### 11.1.4.8 GET_ATTRIBUTE Procedure

The `GET_ATTRIBUTE` procedure gets the value of the specified attribute in the namespace in the currently attached session. If no template corresponding to the namespace exists, an error is thrown. If the specified attribute does not exist, it returns empty string.

If the attribute value is `NULL`, the `firstRead` event is set, and it is the first time that the attribute value is being fetched, then the handler function for the attribute is called.

The calling user is not required to be granted any privileges.

##### Syntax

    GET_ATTRIBUTE (
     namespace   IN         VARCHAR2,
     attribute   IN         VARCHAR2,
     value       OUT NOCOPY VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The namespace of the attribute to retrieve. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions. |
| `attribute` | The name of the attribute to retrieve. The maximum size of the case sensitive character string is 4000 characters. To find a listing of available attributes, query the [V\$XS_SESSION_NS_ATTRIBUTES](real-application-security-data-dictionary-views.md) data dictionary view.                                                                                                                           |
| `value`     | The value of the attribute to retrieve.<br>To find a listing of available attribute values, query the [V\$XS_SESSION_NS_ATTRIBUTES](real-application-security-data-dictionary-views.md) data dictionary view.                                                                                                                                                                                             |

##### Examples

    DECLARE
    attrVal VARCHAR2(4000);

    BEGIN
     SYS.DBMS_XS_SESSIONS.GET_ATTRIBUTE('J_NS1','JohnNS1Attr1',attrVal);
    END;

#### 11.1.4.9 RESET_ATTRIBUTE Procedure

The `RESET_ATTRIBUTE` procedure resets the value of an attribute to its default value (if present) or to `NULL` in the namespace in the current attached session. If the attribute has a default value specified, then the value is reset to the default value. If the attribute was created without a default value and marked for the `attribute_first_read_event`, then the value is set to `NULL` and the attribute is marked as uninitialized. If the attribute was created without a default value and not marked for the `attribute_first_read_event`, then the value is set to `NULL`.

The calling user is required to be granted the `MODIFY_ATTRIBUTE` application privilege.

##### Syntax

    PROCEDURE reset_attribute(
    namespace   IN VARCHAR2,
    attribute   IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The name of the namespace containing the attribute. The maximum size of the case sensitive character string is 128 characters. |
| `attribute` | The name of the attribute to be reset. The maximum size of the case sensitive character string is 4000 characters.             |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.RESET_ATTRIBUTE('ns2','attr1');
    END;

#### 11.1.4.10 DELETE_ATTRIBUTE Procedure

The `DELETE_ATTRIBUTE` procedure deletes the specified attribute and its associated value from the specified namespace in the currently attached session. Only custom attributes can be deleted. Template attributes cannot be deleted. If the specified attribute does not exist, an error is thrown.

The calling application is required to be granted the `MODIFY_ATTRIBUTE` application privilege.

##### Syntax

    DELETE_ATTRIBUTE (
     namespace     IN VARCHAR2,
     attribute     IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The namespace associated with the attribute to delete. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions.<br>You can query the `DBA_XS_NS_TEMPLATES` and `DBA_XS_NS_TEMPLATE_ATTRIBUTES` data dictionary views for a list of namespace templates and attributes. |
| `attribute` | The attribute to delete.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions.                                                                                                                                                                                                                                                                 |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.DELETE_ATTRIBUTE('JohnNS1','JohnNS1Attr1');
    END;

#### 11.1.4.11 DELETE_NAMESPACE Procedure

The `DELETE_NAMESPACE` procedure deletes a namespace and its attributes from the currently attached application session.

The calling user must have the `MODIFY_NAMESPACE` application privilege.

##### Syntax

    DELETE_NAMESPACE (
     namespace   IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The name of the namespace to delete. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of existing namespaces for the current session, once attached, query the `V$XS_SESSION_NS_ATTRIBUTES` data dictionary view. You can query the `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view to find out all the namespaces in all application sessions.<br>You can query the `DBA_XS_NS_TEMPLATES` and `DBA_XS_NS_TEMPLATE_ATTRIBUTES` data dictionary views for a list of namespace templates and attributes. |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.DELETE_NAMESPACE('JohnNS1');
    END;

#### 11.1.4.12 ENABLE_ROLE Procedure

The `ENABLE_ROLE` procedure enables a real application role in the currently attached application session. If the role is already enabled, then `ENABLE_ROLE` procedure performs no action. This procedure can only enable a regular application role directly granted to the current application user. You cannot enable dynamic application roles.

This operation does not require the calling user to have any additional privilege.

##### Syntax

    ENABLE_ROLE (
     role   IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role`    | The name of the role to enable. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of the application roles for the current session, query the [V\$XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view. To find all application roles, query the [DBA_XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT ROLE_NAME FROM V$XS_SESSION_ROLES;`<br>`SELECT SESSIONID, ROLE FROM DBA_XS_SESSION_ROLES;` |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.ENABLE_ROLE('auth2_role');
    END;

#### 11.1.4.13 DISABLE_ROLE Procedure

The `DISABLE_ROLE` procedure disables a real application role from the specified application session. If the role is already disabled or not enabled in the currently attached application session, then `DISABLE_ROLE` performs no action. You cannot disable dynamic application roles. You can only disable a regular application role, which is directly granted to the application user with which the session is created.

This operation does not require the calling user to have any additional privilege.

##### Syntax

    DISABLE_ROLE (
     role   IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role`    | The name of the role to disable. The maximum size of the case sensitive character string is 128 characters.<br>To find a listing of the application roles for the current session, query the [V\$XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view. To find all application roles, query the [DBA_XS_SESSION_ROLES](real-application-security-data-dictionary-views.md) data dictionary view as follows:<br>`SELECT ROLE_NAME FROM V$XS_SESSION_ROLES;`<br>`SELECT SESSIONID, ROLE FROM DBA_XS_SESSION_ROLES;` |

##### Examples

    BEGIN
      SYS.DBMS_XS_SESSIONS.DISABLE_ROLE('auth1_role');
    END;

#### 11.1.4.14 SET_SESSION_COOKIE Procedure

The `SET_SESSION_COOKIE` procedure sets a new cookie value with the specified session ID. If the specified session does not exist or the cookie name is not unique among all the user application sessions, then an error is thrown.

To execute this procedure, the user is required to be granted the `MODIFY_SESSION` application privilege.

##### Syntax

    SET_SESSION_COOKIE (
     cookie      IN VARCHAR2,
     sessionid   IN RAW DEFAULT NULL);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cookie`    | A name for the new cookie. The maximum allowed length for the cookie is 1024 characters. Cookie names must be unique.<br>To find a listing of existing cookies for the current session, query `XS_SYS_CONTEXT(XS$SESSION','COOKIE')`.                                                                                                                                                                          |
| `sessionid` | Session ID of the application session. The default value is `NULL`. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.<br>If you do not specify a session ID or enter `NULL`, then `SET_SESSION_COOKIE` uses the session ID of the current application session. |

##### Examples

    DECLARE
       sessionid RAW(16);
    BEGIN
      SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid);
      SYS.DBMS_XS_SESSIONS.SET_SESSION_COOKIE('cookie1', sessionid);
    END;

#### 11.1.4.15 REAUTH_SESSION Procedure

The `REAUTH_SESSION` procedure updates the last authentication time for the specified session ID as the current time. Applications must call this procedure when it has reauthenticated an application user.

Use the `REAUTH_SESSION` procedure to enable a role that has timed out because of a lack of recent authentication in the application or middle-tier server. You can also call the `reauthSession` Java method.

To execute this function, the user is required to be granted the `MODIFY_SESSION` application privilege.

##### Syntax

    REAUTH_SESSION (
     sessionid IN RAW DEFAULT NULL);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sessionid` | Session ID of the application session. This parameter is optional. The default value is `NULL`. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.<br>If you do not specify a session ID or enter `NULL`, then `REAUTH_SESSION` uses the session ID of the current application session. |

##### Examples

    DECLARE
      sessionid RAW(16);
    BEGIN
     SYS.DBMS_XS_SESSIONS.REAUTH_SESSION(sessionid);
    END;

#### 11.1.4.16 SET_INACTIVITY_TIMEOUT Procedure

The `SET_INACTIVITY_TIMEOUT` procedure sets an inactivity time-out value, in minutes, for the current attached session. The inactivity time-out value represents the maximum period of inactivity allowed before Oracle Database terminates the application session and the resource is reclaimed. Trying to set a negative value for the `time` parameter throws an error. If an invalid session ID is specified or the session does not exist, an error is thrown.

Another way to set the time-out value is to use the `setInactivityTimeout` Java method. You can set a default global time-out value in the `xmlconfig.xml` configuration file. Oracle recommends 240 (4 hours).

An application session cannot time-out due to inactivity while a traditional session is attached. The last access time is updated each time a traditional session attaches to the application session.

To execute this procedure, the calling user is required to be granted the `MODIFY_SESSION` application privilege.

##### Syntax

    SET_INACTIVITY_TIMEOUT (
     time        IN NUMBER,
     sessionid   IN RAW DEFAULT NULL);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `time`      | Inactivity time-out value in minutes. Oracle recommends setting the `time` parameter to `240` (4 hours). A zero (0) value means the value is infinite and that the session never expires due to inactivity.                                                                                                                                                                                                        |
| `sessionid` | Session ID of the application session. The default value is `NULL`. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.<br>If you do not specify a session ID or enter `NULL`, then `SET_INACTIVITY_TIMEOUT` uses the session ID of the current application session. |

##### Examples

    DECLARE
      sessionid RAW(16);
    BEGIN
      SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser1', sessionid);
      SYS.DBMS_XS_SESSIONS.SET_INACTIVITY_TIMEOUT (300, sessionid);
    END;
    /

#### 11.1.4.17 SAVE_SESSION Procedure

The `SAVE_SESSION` procedure saves all changes performed in the currently attached session and remains attached to the session as it was before saving changes.

The calling user requires no privileges to perform this operation.

##### Syntax

    SAVE_SESSION;

##### Parameters

None.

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.SAVE_SESSION;
    END;

#### 11.1.4.18 DETACH_SESSION Procedure

The `DETACH_SESSION` procedure detaches the current traditional database session from the application session to which it is attached. The database sessions goes back to the context it was in prior to attaching to the application session. Any user can execute this procedure as the operation does not require any privileges to execute.

##### Syntax

    DETACH_SESSION (abort IN BOOLEAN DEFAULT FALSE);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                      |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `abort`   | If specified as `TRUE`, it rolls back the changes performed in the current session. If specified as `FALSE`, the default value, all changes performed in the session are persisted. If a `NULL` value is specified for this parameter, it is treated as `FALSE`. |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.DETACH_SESSION;
    END;

#### 11.1.4.19 DESTROY_SESSION Procedure

The `DESTROY_SESSION` procedure destroys the specified session. This procedure also implicitly detaches all traditional sessions from the application session. After the session is destroyed no further attaches can be made to the session. This operation cannot destroy sessions created through direct logon of the application user.

To execute this procedure, the user must have the `TERMINATE_SESSION` application privilege.

##### Syntax

    DESTROY_SESSION (
     sessionid IN RAW,
     force     IN BOOLEAN DEFAULT FALSE);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sessionid` | Session ID of the application session. You can get the session ID by using one of the following methods:<br>• `SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL; `<br>• Using the `DBMS_XS_SESSIONS.GET_ATTRIBUTE` procedure.<br>If you do not specify a session ID or enter `NULL`, then `DESTROY_SESSION` uses the session ID of the current application session. |
| `force`     | If set to `FALSE`, this operation throws an error, in case the specified session is currently attached. If set to `TRUE`, the currently attached application session can be destroyed. This is an optional parameter.                                                                                                                                                          |

##### Examples

    DECLARE
      sessionid RAW(16);
    BEGIN
     SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwtSession1', sessionid);
     SYS.DBMS_XS_SESSIONS.DESTROY_SESSION (sessionid);
    END;

#### 11.1.4.20 ADD_GLOBAL_CALLBACK Procedure

The `ADD_GLOBAL_CALLBACK` procedure registers an existing PL/SQL procedure as the event handler with the session operation specified by the `event_type` parameter. You can add more than one event handler for the same session operation for execution when the associated event occurs. Adding the global callback procedure automatically enables the callback procedure for execution. If more than one callback is added for the same session event, they are executed in according to their registration sequence, that is, the callback procedure that was registered first, is executed first. This procedure throws an error if an invalid event type is specified or the callback procedure does not exist.

Successful execution of this procedure requires the `CALLBACK` application privilege. This role can be obtained through `PROVISIONER` database role.

##### Syntax

    ADD_GLOBAL_CALLBACK(
      event_type         IN PLS_INTEGER,
      callback_schema    IN VARCHAR2,
      callback_package   IN VARCHAR2,
      callback_procedure IN VARCHAR2);

##### Parameters

| Parameter            | Description                                                                                                                                                                                                                                                                                                                                                                                                               |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_type`         | Select from the following event types:<br>• `CREATE_SESSION_EVENT`<br>• `ATTACH_SESSION_EVENT`<br>• `CREATE_NAMESPACE_EVENT`<br>• `GUEST_TO_USER_EVENT`<br>• `PROXY_TO_USER_EVENT`<br>• `REVERT_TO_USER_EVENT`<br>• `ENABLE_ROLE_EVENT`<br>• `DISABLE_ROLE_EVENT`<br>• `ENABLE_DYNAMIC_ROLE_EVENT`<br>• `DISABLE_DYNAMIC_ROLE_EVENT`<br>• `DETACH_SESSION_EVENT`<br>• `TERMINATE_SESSION_EVENT`<br>• `DIRECT_LOGIN_EVENT` |
| `callback_schema`    | Enter the name of the schema in which the callback procedure was created.                                                                                                                                                                                                                                                                                                                                                 |
| `callback_package`   | Enter the name of the package in which the callback procedure was created. If callback procedure is standalone, `NULL` should be passed as `callback_package` parameter. This parameter is optional only if the callback procedure is in a package.                                                                                                                                                                       |
| `callback_procedure` | Enter the name of the procedure that defines the global callback.                                                                                                                                                                                                                                                                                                                                                         |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.ADD_GLOBAL_CALLBACK (
      DBMS_XS_SESSIONS.CREATE_SESSION_EVENT,
      'APPS1_SCHEMA','APPS2_PKG','CREATE_SESSION_CB');
    END;

#### 11.1.4.21 ENABLE_GLOBAL_CALLBACK Procedure

The `ENABLE_GLOBAL_CALLBACK` procedure enables or disables the global callback procedure for execution. If a callback procedure associated with this event is not specified, all callback procedures associated with this global callback are enabled or disabled. If an invalid event type is specified or invalid callback procedure is specified, an error is thrown.

##### Syntax

    ENABLE_GLOBAL_CALLBACK(
      event_type         IN PLS_INTEGER,
      enable             IN BOOLEAN  DEFAULT TRUE,
      callback_schema    IN VARCHAR2 DEFAULT NULL,
      callback_package   IN VARCHAR2 DEFAULT NULL,
      callback_procedure IN VARCHAR2 DEFAULT NULL);

##### Parameters

| Parameter            | Description                                                                                                                                                                                                                                                                                                                                                                                                               |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_type`         | Select from the following event types:<br>• `CREATE_SESSION_EVENT`<br>• `ATTACH_SESSION_EVENT`<br>• `CREATE_NAMESPACE_EVENT`<br>• `GUEST_TO_USER_EVENT`<br>• `PROXY_TO_USER_EVENT`<br>• `REVERT_TO_USER_EVENT`<br>• `ENABLE_ROLE_EVENT`<br>• `DISABLE_ROLE_EVENT`<br>• `ENABLE_DYNAMIC_ROLE_EVENT`<br>• `DISABLE_DYNAMIC_ROLE_EVENT`<br>• `DETACH_SESSION_EVENT`<br>• `TERMINATE_SESSION_EVENT`<br>• `DIRECT_LOGIN_EVENT` |
| `enable`             | Specifies whether the global callback is to be enabled or disabled. The default value is `TRUE`, meaning enable.                                                                                                                                                                                                                                                                                                          |
| `callback_schema`    | Enter the name of the schema in which the global callback was created.                                                                                                                                                                                                                                                                                                                                                    |
| `callback_package`   | Enter the name of the package in which the global callback was created.                                                                                                                                                                                                                                                                                                                                                   |
| `callback_procedure` | Enter the name of the procedure that defines the global callback.                                                                                                                                                                                                                                                                                                                                                         |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.ENABLE_GLOBAL_CALLBACK (
      DBMS_XS_SESSIONS.CREATE_SESSION_EVENT,
      TRUE, 'APPS1_SCHEMA','APPS2_PKG','CREATE_SESSION_CB');
    END;

#### 11.1.4.22 DELETE_GLOBAL_CALLBACK Procedure

The `DELETE_GLOBAL_CALLBACK` procedure removes the global callback from registration. (It does not delete the global callback itself.) If a callback procedure is not specified, all callback procedures associated with this global callback are deleted. If an invalid event type is specified, an error is thrown.

##### Syntax

    DELETE_GLOBAL_CALLBACK(
      event_type         IN PLS_INTEGER,
      callback_schema    IN VARCHAR2 DEFAULT NULL,
      callback_package   IN VARCHAR2 DEFAULT NULL,
      callback_procedure IN VARCHAR2 DEFAULT NULL);

##### Parameters

| Parameter            | Description                                                                                                                                                                                                                                                                                                                                                                                                               |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_type`         | Select from the following event types:<br>• `CREATE_SESSION_EVENT`<br>• `ATTACH_SESSION_EVENT`<br>• `CREATE_NAMESPACE_EVENT`<br>• `GUEST_TO_USER_EVENT`<br>• `PROXY_TO_USER_EVENT`<br>• `REVERT_TO_USER_EVENT`<br>• `ENABLE_ROLE_EVENT`<br>• `DISABLE_ROLE_EVENT`<br>• `ENABLE_DYNAMIC_ROLE_EVENT`<br>• `DISABLE_DYNAMIC_ROLE_EVENT`<br>• `DETACH_SESSION_EVENT`<br>• `TERMINATE_SESSION_EVENT`<br>• `DIRECT_LOGIN_EVENT` |
| `callback_schema`    | Enter the name of the schema in which the global callback was created.                                                                                                                                                                                                                                                                                                                                                    |
| `callback_package`   | Enter the name of the package in which the global callback was created.                                                                                                                                                                                                                                                                                                                                                   |
| `callback_procedure` | Enter the name of the procedure that defines the global callback.                                                                                                                                                                                                                                                                                                                                                         |

##### Examples

    BEGIN
     SYS.DBMS_XS_SESSIONS.DELETE_GLOBAL_CALLBACK (
      DBMS_XS_SESSIONS.CREATE_SESSION_EVENT,
      'APPS1_SCHEMA','APPS2_PKG','CREATE_SESSION_CB');
    END;
