## 7 Oracle Fusion Middleware Integration with Real Application Security

Real Application Security adds external user and role support for application integration, that can be used, for example, with Oracle Fusion Middleware. For Oracle Fusion Middleware, the users and roles are also externalized to a common, single repository with centralized management and single authentication of the user interface using the Authorization Policy Manager. From a Real Application Security perspective, the integrated users and roles (including application roles) are externalized principals because Oracle Fusion Middleware manages them externally. The mid-tier initialization and authorization operations are the same as those described in [Using Real Application Security in Java Applications](using-real-application-security-in-java-applications.md).

This chapter describes the following topics:

- About External Users and External Roles

- Session APIs for External Users and Roles

### 7.1 About External Users and External Roles

An external user is an end-user accessing a service. User information is stored in the identity store, typically instantiated by the WebLogic Authenticator. This user is neither a database user nor a Real Application Security application user. An external user does not have any footprint in the database. But, an external user needs to access the database for application data. Therefore, a Real Application Security context (session) is established for such a user to control the user's access to the required data.

An anonymous user is an unauthenticated user, or a user whose credentials have not been validated. An anonymous user is permitted to access only unprotected resources such as public data from a database. An application can enable or disable the use of anonymous users.

An external role or group is a collection of users and other groups, which can be hierarchical. For example, a group can include arbitrarily nested groups.

An external application role is a collection of users, groups, and application roles, which can be hierarchical. This role is specific to the application, defined by the application policy, and may not be known to the J2EE container. Application roles are scoped because they are visible only when the application runs. They can be mapped to other application roles defined in the same application scope and also to enterprise users or groups. Application roles are used in authorization decisions.

Similar to external users, external roles and application roles have no footprint in the Real Application Security system. They are used to control the way the Real Application Security ACLs grant data access to an application.

External roles and application roles also enforce the details of data access. External users need some basic database privileges, typically the object privilege to run SELECT on an application table. These privileges can be granted through a Real Application Security dynamic application role, which is enabled when a user session is attached. For example, to grant privileges to an external user or role, specify the principal type as `XS_ACL.PTYPE_EXTERNAL` in an ACE list when creating an ACL. See the "[CREATE_ACL Procedure](XS_ACL-package.md)" for more information.

#### Session Modes for External Users

Real Application Security supports the following two modes of operation for sessions:

- Secure Mode

  In secure mode, data security is enforced at the database server. By default, a session is created in a secure mode for all users.

- Trusted mode

  A trusted mode is a mode in which data security is enforced at the middle tier and not at the database server. In such a mode, the data security implemented by Real Application Security is bypassed. So, creating a session in trusted mode is a privileged operation.

  Trusted mode is allowed only for external users, and only when the dispatcher has `CREATE_TRUSTED_SESSION` privilege. This privilege can be granted to the dispatcher user as follows:

      XS_ADMIN_UTIL.grant_system_privilege('CREATE_TRUSTED_SESSION','dispatcher', XS_ADMIN_UTIL.PTYPE_XS);

### 7.2 Session APIs for External Users and Roles

This section describes the following topics for external users and roles:

- Namespace for External Users

- Creating a Session

- Attaching a Session

- Assigning a User to a Session

- Saving a Session and Aborting a Session

#### 7.2.1 Namespace for External Users

The namespaces for external users are enhanced with attribute manipulation features during creating, attaching, and assigning a session. External users are able to perform the following activities:

- Creating namespace with attributes while creating a session

- Setting namespace attributes while attaching a session and assigning a user

- Saving a session and leaving it as attached

#### 7.2.2 Creating a Session

To create a Real Application Security application session, use the `createSession` method of the `XSSessionManager` class.

For external users, this method creates a Session object on the server as well as its corresponding middle-tier representation with namespaces and attributes. This method also creates the Namespaces and sets corresponding attributes given in the Namespace/AttributeValue. The cookie can be used to identify the newly created Real Application Security application session in future calls, until the cookie value is changed or the session is destroyed.

##### Syntax

    public abstract Session createSession(java.sql.Connection conn,
                                          ExternalUser eUser,
                                          java.lang.String cookie,
                                          java.util.Collection<NamespaceValue> nav)
                                          throws InvalidXSUserException,
                                                 AccessDeniedException,
                                                 java.sql.SQLException,
                                                 XSSessionException,
                                                 InvalidXSNamespaceException

    public abstract Session createSessionTrusted(java.sql.Connection conn,
                                 ExternalUser externalUser,
                                 java.lang.String cookie,
                                 java.util.Collection<NamespaceValue> nameSpaceValues)
                                 throws InvalidXSUserException,
                                 AccessDeniedException,
                                 java.sql.SQLException,
                                 SQLException,
                                 XSException,
                                 InvalidXSNamespaceException

##### Parameter

| Parameter                  | Description                                                                         |
|:---------------------------|:------------------------------------------------------------------------------------|
| `conn`                     | The JDBC connection for database server roundtrip                                   |
| `eUser` or `externalUser`  | The external user associated with the session                                       |
| `cookie`                   | The session cookie used to identify the external user                               |
| `nav` or `nameSpaceValues` | A list of namespaces with corresponding attributes to be created for the namespaces |

##### Example

Example 7-1 demonstrates how to create a Real Application Security session for external users. The `createSession` method is in bold typeface.

Example 7-1 Creating a Real Application Security Session for External Users

    .
    .
    .
    static Connection lws_conn =null;
    static XSSessionManager sm = null;
    lws_conn = DriverManager.getConnection(lws_conn_string, username, password);
    sm = XSSessionManager.getSessionManager(privConn,20,29999999);
    .
    .
    .
    String trituser = "TUSER01";
    String cookie = "some_cookie";
    String extuser = "ExtPrincp";
    String extuuid = "ExtPrincp";

    Session lws = null;

    List<AttributeValue> nsavList = new ArrayList<AttributeValue>();
    AttributeValue nsav1 = new AttributeValue("ATTR01","value1");
    nsavList.add(nsav1);
    AttributeValue nsav2 = new AttributeValue("ATTR02","value2");
    nsavList.add(nsav2);
    NamespaceValue nav = new NamespaceValue("NST01",nsavList);
    List<NamespaceValue> nsList = new ArrayList();
    nsList.add(nav);

    /* create session with external user name in secure mode with namespace attr-vals and cookie */
    lws = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), cookie, nsList);
    sm.destroySession(lws_conn, lws);

    /*Create external user session in secure mode*/
    lws = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), null, null);
    sm.destroySession(lws_conn, lws);

    /*Create external user session in secure mode with namespace attribute values */
    lws = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), null, nsList);
    sm.destroySession(lws_conn, lws);

    /* create session with external user name in secure mode with cookie */
    lws = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), cookie, null);
    sm.destroySession(lws_conn, lws);

    /* create trusted session with only external user name */
    lws = sm.createSessionTrusted(lws_conn, new ExternalUser(extuser, extuuid), null, null);
    sm.destroySession(lws_conn, lws);

    /* create session with RAS user name in secure mode with namespace and cookie */
    lws = sm.createSession(lws_conn, trituser, cookie, nsList);
    sm.destroySession(lws_conn, lws);

#### 7.2.3 Attaching a Session

To attach an application session, use the `attachSession` method of the `XSSessionManager` class.

For external users, this method attaches the JDBC connection to the specified session object. This method also sets the dynamic application roles, external roles, authentication time, and creates namespaces for the session. It also gives a list of a namespace and its corresponding namespace attributes to be created and set. If the namespace does not exist, then this method creates the namespace, and then sets the corresponding attributes.

##### Syntax

    public abstract void attachSession(
                 java.sql.Connection conn,
                 Session session,
                 java.util.Collection<java.lang.String> enabledDynamicRoles,
                 java.util.Collection<java.lang.String> disabledDynamicRoles,
                 java.util.Collection<ExternalRole> externalRoles,
                 java.util.Collection<NamespaceValue> nav,
                 java.sql.Timestamp authenticationTime)
                 throws java.sql.SQLException,
                        AccessDeniedException,
                 InvalidSessionException,
                 XSSessionException,
                 InvalidXSNamespaceException

    public abstract Session attachSessionByCookie(
              java.sql.Connection conn,
              java.lang.String cookie,
              java.util.Collection<java.lang.String> enabledDynamicRoles,
              java.util.Collection<java.lang.String> disabledDynamicRoles,
              java.util.Collection<oracle.security.xs.ExternalRole> externalRoles,
              java.util.Collection<oracle.security.xs.NamespaceValue> namespaceValues,
              java.sql.Timestamp authenticationTime)
              throws java.sql.SQLException,
                     AccessDeniedException,
                     InvalidSessionException,
                     XSException,
                     InvalidXSNamespaceException

    public abstract Session attachSessionByID(
              java.sql.Connection conn,
              java.lang.String id,
              java.util.Collection<java.lang.String> enabledDynamicRoles,
              java.util.Collection<java.lang.String> disabledDynamicRoles,
              java.util.Collection<oracle.security.xs.ExternalRole> externalRoles,
              java.util.Collection<oracle.security.xs.NamespaceValue> namespaceValues,
              java.sql.Timestamp authenticationTime)
              throws java.sql.SQLException,
                     AccessDeniedException,
                     InvalidSessionException,
                     XSException,
                     InvalidXSNamespaceException

##### Parameters

| Parameter                  | Description                                                       |
|:---------------------------|:------------------------------------------------------------------|
| `conn`                     | The database connection to be attached to the application session |
| `session`                  | The Session object to be attached                                 |
| `cookie`                   | The session cookie                                                |
| `id`                       | The session identifier                                            |
| `enabledDynamicRoles`      | A collection of dynamic application role names to be enabled      |
| `disabledDynamicRoles`     | A collection of dynamic application role names to be disabled     |
| `externalRoles`            | A collection of external roles to be enabled                      |
| `nav` or `namespaceValues` | A list of namespaces with corresponding attributes to be set      |
| `authenticationTime`       | The authentication time to be sent to the database server         |

##### Example

Example 7-2 demonstrates how to attach a Real Application Security session for external users. The `attachSession` method is in bold typeface.

##### External Role Behavior while Attaching a Session

- After an external role is enabled for a session, it is stored as part of the session context as an ID. This role ID is used in access control, when you call the `checkAcl` method on both middle tier and database server. This is same as regular Real Application Security application role or dynamic application role.

- A Real Application Security ID is assigned for every external role passed while attaching a session, whether the role is referred by ACL or not.

- The scope of the external role is within the boundary of attaching or detaching a session. An external role cannot be enabled for attaching multiple sessions, and it does not need to be explicitly disabled. So, the roles assigned for attaching the first session will not be automatically enabled while attaching the next session, unless the roles are assigned again.

  This behavior is completely different from the behavior of regular Real Application Security application roles or dynamic application roles, where the application roles assigned for attaching the first session are automatically enabled while attaching the next session.

- After a session is attached, the external role remains consistent till detaching and reattach the session. The role may even be revoked for the user.

Example 7-2 Attaching a Real Application Security Session for External Users

    .
    .
    .
    static Connection lws_conn =null;
    static XSSessionManager sm = null;
    .
    .
    .
    lws_conn = DriverManager.getConnection(lws_conn_string, username, password);
    sm = XSSessionManager.getSessionManager(privConn,20,29999999);
    .
    .
    .
    String cookie = "some_cookie";
    String extuser = "ExtPrincp";
    String extuuid = "ExtPrincp";

    Session lws = null;
    Session lws2 = null

    List<AttributeValue> nsavList = new ArrayList<AttributeValue>();

    AttributeValue nsav1 = new AttributeValue("ATTR01","value1");
    nsavList.add(nsav1);
    AttributeValue nsav2 = new AttributeValue("ATTR02","value2");
    nsavList.add(nsav2);

    NamespaceValue nav = new NamespaceValue("NST01",nsavList);

    List<NamespaceValue> nsList = new ArrayList();
    nsList.add(nav);

    List <String> dynamicRoles = new ArrayList <String>();
    dynamicRoles.add("DYNROLE001");
    dynamicRoles.add("DYNROLE002");

    List <ExternalRole> extRoles = new ArrayList <ExternalRole>();
    extRoles.add(new ExternalRole("EXTPRIN01"));
    extRoles.add(new ExternalRole("MYEXTPRIN02"));

    lws = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), cookie + "secure", nsList, false);
    sm.attachSession(lws_conn, lws, enabledDynamicRoles, disabledDynamicRoles, extRoles, null, null);
    sm.detachSession(lws);
    sm.attachSession(lws_conn, lws, enabledDynamicRoles, disabledDynamicRoles, extRoles, null, new Timestamp(System.currentTimeMillis()));
    sm.detachSession(lws);
    sm.attachSession(lws_conn, lws, enabledDynamicRoles, disabledDynamicRoles, extRoles, nsList, null);
    sm.detachSession(lws);
    sm.attachSession(lws_conn, lws, enabledDynamicRoles, disabledDynamicRoles, extRoles, nsList, new Timestamp(System.currentTimeMillis()));
    sm.detachSession(lws);

    lws2 = sm.createSession(lws_conn, new ExternalUser(extuser, extuuid), cookie + "trusted", nsList, true);
    lws2 = sm.attachSessionByCookie(lws_conn, lws.getSessionCookie(), null, enabledDynamicRoles, disabledDynamicRoles, extRoles, null, null);
    sm.detachSession(lws2);
    lws2 = sm.attachSessionByCookie(lws_conn, lws.getSessionCookie(), null, enabledDynamicRoles, disabledDynamicRoles, extRoles, nsList, new Timestamp(System.currentTimeMillis()));
    sm.detachSession(lws2);

#### 7.2.4 Assigning a User to a Session

To assign a name to a previously anonymous user, use the `assignUser` method of the `XSSessionManager` class.

For external users, this method assigns a named user to a previously anonymous user, sets the dynamic application roles, external role, and authentication time. If a list of Namespace/Attribute values is given, this method creates each namespace that does not exist, and sets the corresponding attributes.

##### Syntax

    public abstract void assignUser(
                          Session session,
                          ExternalUser targetUser,
                          java.util.Collection<java.lang.String> enabledDynamicRoles,
                          java.util.Collection<java.lang.String> disabledDynamicRoles,
                          java.util.Collection<ExternalRole> externalRoles,
                          java.util.Collection<NamespaceValue> naValues,
                          java.sql.Timestamp authenticationTime)
                          throws java.sql.SQLException,
                                 AccessDeniedException,
                                 InvalidSessionException,
                                 XSSessionException,
                                 InvalidXSNamespaceException

##### Parameters

| Parameters             | Description                                                  |
|:-----------------------|:-------------------------------------------------------------|
| `session`              | The session object to assign the user to                     |
| `targetUser`           | An `ExternalUser` object initialized based on authentication |
| `enabledDynamicRoles`  | A list of dynamic application role names to be enabled       |
| `disabledDynamicRoles` | A list of dynamic application role names to be disabled      |
| `externalRoles`        | A collection of external roles to be enabled                 |
| `namespaceValues`      | A list of namespaces with corresponding attributes to be set |
| `authenticationTime`   | The a timestamp indicated when the user authenticated        |

##### Example

Example 7-3 demonstrates how to assign a Real Application Security session to external users. The `assignUser` method is in bold typeface.

Example 7-3 How to Assign a Real Application Security Session to External Users

    .
    .
    .
    static Connection lws_conn =null;
    static XSSessionManager sm = null;
    .
    .
    .
    lws_conn = DriverManager.getConnection(lws_conn_string, username, password);
    sm = XSSessionManager.getSessionManager(privConn,20,29999999);
    .
    .
    .
    String cookie = "some_cookie";
    String extuser = "ExtPrincp";
    String extuuid = "ExtPrincp";

    Session lws = null;

    List<AttributeValue> nsavList = new ArrayList<AttributeValue>();

    AttributeValue nsav1 = new AttributeValue("ATTR01","value1");
    nsavList.add(nsav1);
    AttributeValue nsav2 = new AttributeValue("ATTR02","value2");
    nsavList.add(nsav2);

    NamespaceValue nav = new NamespaceValue("NST01",nsavList);

    List<NamespaceValue> nsList = new ArrayList();
    nsList.add(nav);

    List <String> dynamicRoles = new ArrayList <String>();
    dynamicRoles.add("DYNROLE001");
    dynamicRoles.add("DYNROLE002");

    List <ExternalRole> extRoles = new ArrayList <ExternalRole>();
    extRoles.add(new ExternalRole("EXTPRIN01"));
    extRoles.add(new ExternalRole("MYEXTPRIN02"));

    lws = sm.createAnonymousSession(lws_conn, cookie + "trusted", nsList, true);
    sm.attachSession(lws_conn, lws, null, null, null, null, null);
    sm.assignUser(lws, euser, dynamicRoles, dynamicRoles, extRoles, null, null);
    sm.detachSession(lws);

    lws = sm.createAnonymousSession(lws_conn, cookie + "secure", nsList, false);
    sm.attachSession(lws_conn, lws, null, null, null, null, null);
    sm.assignUser(lws, euser, dynamicRoles, dynamicRoles, extRoles, null, new Timestamp(System.currentTimeMillis()));
    sm.detachSession(lws);

    lws = sm.createAnonymousSession(lws_conn, cookie + "trusted", nsList, true);
    sm.attachSession(lws_conn, lws, null, null, null, null, null);
    sm.assignUser(lws, euser, dynamicRoles, dynamicRoles, null, nsList, null);
    sm.detachSession(lws);

#### 7.2.5 Saving a Session and Aborting a Session

To save the changes of a session at the database server and keep the session still attached, use the `saveSession` method of the `XSSessionManager` class.

For external users, this method saves the current session. Similar to the `detachSession` method, this method commits all session changes to the back end and a database roundtrip is required to perform this operation. But, unlike the `detachSession` method, this method keeps the session attached. This method is mainly used to save an application context (namespace).

To abort the changes of a session at the database server and detach from the session, use the `abortSession` method of the `XSSessionManager` class.

##### Syntax

    public abstract void saveSession(Session session)
                              throws java.sql.SQLException,
                                     NotAttachedException,
                                     XSSessionException

    public abstract void abortSession(Session session)
                              throws java.sql.SQLException,
                                     NotAttachedException,
                                     XSException

##### Example

Example 7-4 demonstrates how to save a Real Application Security external user session. The `saveSession` method is in bold typeface.

Example 7-4 How to Save a Real Application Security External User Session

    .
    .
    .
    static Connection lws_conn =null;
    static XSSessionManager sm = null;
    .
    .
    .
    lws_conn = DriverManager.getConnection(lws_conn_string, username, password);
    sm = XSSessionManager.getSessionManager(privConn,20,29999999);
    .
    .
    .
    String cookie = "some_cookie";
    String extuser = "ExtPrincp";
    String extuuid = "ExtPrincp";

    Session lws = null;

    List<AttributeValue> nsavList = new ArrayList<AttributeValue>();

    AttributeValue nsav1 = new AttributeValue("ATTR01","value1");
    nsavList.add(nsav1);
    AttributeValue nsav2 = new AttributeValue("ATTR02","value2");
    nsavList.add(nsav2);

    NamespaceValue nav = new NamespaceValue("NST01",nsavList);

    List<NamespaceValue> nsList = new ArrayList();
    nsList.add(nav);

    List <String> dynamicRoles = new ArrayList <String>();
    dynamicRoles.add("DYNROLE001");
    dynamicRoles.add("DYNROLE002");

    List <ExternalRole> extRoles = new ArrayList <ExternalRole>();
    extRoles.add(new ExternalRole("EXTPRIN01"));
    extRoles.add(new ExternalRole("MYEXTPRIN02"));

    lws = sm.createAnonymousSession(lws_conn, cookie + "trusted", nsList, true);
    sm.attachSession(lws_conn, lws, null, null, null, null, null);
    sm.assignUser(lws, euser, dynamicRoles, dynamicRoles, extRoles, null, null);
    lws.deleteNamespace("NST01");
    sm.saveSession(lws);
