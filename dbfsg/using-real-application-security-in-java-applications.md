## 6 Using Real Application Security in Java Applications

This chapter describes how to use Real Application Security in Java applications. This chapter contains the following sections:

- About Initializing the Middle Tier

- About Managing Real Application Security Sessions

- Authenticating Application Users Using Java APIs

- About Authorizing Application Users Using ACLs

- Human Resources Administration Use Case: Implementation in Java

### 6.1 About Initializing the Middle Tier

The `XSSessionManager` class manages the life cycle of the session. It provides methods to create, attach, assign, detach, and destroy sessions. It also provides methods to perform cache activities.

This section describes the following topics:

- About Mid-Tier Configuration Mode

- Using the getSessionManager Method

- About Changing the Middle-Tier Cache Setting

#### 6.1.1 About Mid-Tier Configuration Mode

You can use one mid-tier configuration mode:

- Dispatcher mode - get a session manager with dispatcher connections

In dispatcher mode, the dispatcher user must have session administration and cache access privileges. The application user does not need any session or cache privilege. The two predefined database roles, `xs_session_admin` and `xs_cache_admin`, can be granted to the dispatcher.

For best security practices, the application user should be given the least amount of privilege, therefore dispatcher mode is the recommended mid-tier configuration.

#### 6.1.2 Using the getSessionManager Method

There is one way to get a session manager following the mid-tier configuration mode described in "About Mid-Tier Configuration Mode":

- Pass a connection or a pool of connections of the dispatcher user. In this way, the needed privileges are granted to the dispatcher. The two predefined roles, `xs_session_admin` and `xs_cache_admin`, should be granted to the dispatcher user. The dispatcher user is a direct logon Real Application Security user.

Using the dispatcher mode, you can initiate the Real Application Security middle tier by getting an instance of the session manager (see Example 6-1). Use the `getSessionManager` method (in bold typeface) of the `XSSessionManager` class to get an instance of the session manager. This method initializes a Real Application Security session manager by using either a single connection or a pool of connections. The caller of the `getSessionManager` method should have the Java Authentication and Authorization Service (JAAS) permission `XSSecurityPermission("initSecurityManager")`.

##### Privileges for the Session Manager

Real Application Security session manager is initialized with a connection of a privileged user, who authorizes the session operations on behalf of the regular Real Application Security application users. If the session manager has the session operation privileges, then, each application user under the session manager does not need to have session operation privileges, and the application user's session operations can be performed as a trusted party. The session manager authorizes session operations for a connection, so you do not need to grant the `createSession` and `attachToSession` privileges directly to the regular Real Application Security application user. This session manager must have the following privileges:

- Real Application Security database object privileges to manage cached data in the middle tier.

- Session life cycle management privileges for the session manager to create or attach sessions on behalf of Real Application Security application user and external users.

##### Roles for the Session Manager

The session manager needs the following two roles to have the privileges mentioned in "Privileges for the Session Manager":

- A database role `xs_cache_admin` with the following privileges:

  - Privilege to query Real Application Security entities and to synchronize metadata

  - Privilege to execute code for the key exchange

- A Real Application Security role, `xs_session_admin`, with `ADMIN_SESSION` privilege

These roles are predefined in the system.

Example 6-1 How to Get an Instance of the Session Manager in Java Using a Single Connection

    static XSSessionManager manager;
    static Connection dispatcherConn = null;
    int cacheMaxIdleTime=30;
    int cacheMaxsize=2048000;
    String host;
    String port;
    String sid;
    ...
    dispatcherConn = DriverManager.getConnection("jdbc:oracle:thin:@" + host + ":" + port + ":" + sid, dispatcherUser, dispatcherPassword);
    ...
    manager = XSSessionManager.getSessionManager(dispatcherConn, cacheMaxIdleTime, cacheMaxsize);

#### 6.1.3 About Changing the Middle-Tier Cache Setting

Once the session manager is initialized, it starts to add some data like the ACL and Security class information to the cache. This cache data can be reused. The cache is initialized with its default settings that can be changed later.

This section describes the following topics:

- About Setting the Maximum Cache Idle Time

- About Setting the Maximum Cache Size

- About Getting the Maximum Cache Idle Time

- About Getting the Maximum Cache Size

- About Removing Entries from the Cache

- About Clearing the Cache

##### 6.1.3.1 About Setting the Maximum Cache Idle Time

To set the maximum cache idle time, use the `setCacheMaxIdleTime` method of the `XSSessionManager` class. The `setCacheMaxIdleTime` method sets the maximum number of minutes that the cache can go without updating.

If an attempt is made to fetch objects from the cache and the `XSSessionManager` has not called the `updateCache` method for a period of time equal to the value set by the `setCacheMaxIdleTime` method, then, before returning any objects, the `updateCache` method is invoked forcefully to check that all the cached objects are still valid. The caller of the `setCacheMaxIdleTime` method must have the JAAS permission `XSSecurityPermission("setCacheMaxIdleTime")`.

##### 6.1.3.2 About Setting the Maximum Cache Size

To set the maximum cache size, use the `setCacheMaxSize` method of the `XSSessionManager` class. This method sets the size of the cache on the middle tier.

The default size of the cache is 10MB. The minimum cache size is 1MB. The caller of the `setCacheMaxSize` method must have the JAAS permission` XSSecurityPermission("setCacheMaxSize")`.

##### 6.1.3.3 About Getting the Maximum Cache Idle Time

To get the maximum cache idle time, use the `getCacheMaxIdleTime` method of the `XSSessionManager` class. This method returns the maximum number of minutes for which the cache does not have an `updateCache` call to update the cache. The caller of the `getCachemaxIdleTime` method must have the JAAS permission` XSSecurityPermission("getCacheMaxIdleTime")`.

##### 6.1.3.4 About Getting the Maximum Cache Size

To get the maximum cache size, use the `getCacheMaxSize` method of the `XSSessionManager` class. This method returns the maximum size of the cache in bytes. The caller of the `getCacheMaxSize` method must have the JAAS permission XSSecurityPermission("getCacheMaxSize").

##### 6.1.3.5 About Removing Entries from the Cache

To remove entries from the cache, a cache eviction algorithm is used, along with watermark levels. A watermark level determines how long data should stay in memory cache before being removed. When the cache size reaches the high watermark, then the cache eviction algorithm removes entries until the cache size reaches the low watermark.

This section describes the following activities for removing entries from the cache:

- About Setting the WaterMark

- About Getting the High WaterMark

- About Getting the Low WaterMark

###### 6.1.3.5.1 About Setting the WaterMark

To set the watermark, use the `setWaterMark` method from the `XSSessionManager` class. The caller of the `setWaterMark` method must have the JAAS permission `XSSecurityPermission("setWaterMark")`.

###### 6.1.3.5.2 About Getting the High WaterMark

To get the high watermark for cache, use the `getHighWaterMark` method from the `XSSessionManager` class.

###### 6.1.3.5.3 About Getting the Low WaterMark

To get the low watermark for cache, use the `getLowWaterMark` method from the `XSSessionManager` class.

##### 6.1.3.6 About Clearing the Cache

To clear the cache explicitly from the middle tier, use the `clearCache` method of the `XSSessionManager` class. This method explicitly clears the shared cache from the middle tier. The caller of the `clearCache` method must have the JAAS permission` XSSecurityPermission("clearCache")`.

### 6.2 About Managing Real Application Security Sessions

This section describes the following topics:

- Creating a Real Application Security User Session

- Attaching an Application Session

- Assigning or Switching an Application User

- Enabling Real Application Security Application Roles

- About Performing Namespace Operations as Session User

- About Performing Miscellaneous Session-Related Activities

- Detaching an Application Session

- Destroying A Real Application Security Application Session

#### 6.2.1 Creating a Real Application Security User Session

To create a Real Application Security user session, for example, `lws`, for the application user `lwuser`, use the `createSession` method of the `XSSessionManager` class (see Example 6-2). The `createSession` method (in bold typeface). creates a session on the server with the specified parameters passed. A database round-trip is required to perform this operation.

To create an anonymous Real Application Security application session, use the `createAnonymousSession` method of the `XSSessionManager` class. The application user for this session is a predefined anonymous user, so no user parameter is passed in this method.

Both methods support using a cookie and a namespace.

The cookie, passed as the parameter, can be used to identify the newly created Real Application Security application session in future calls, until the cookie value is changed or the session is destroyed.

The namespace, passed as the parameter, can be used to create a namespace in the session. For details, see "About Performing Namespace Operations as Session User".

It is possible to reassign a specific application user to take over this session. In this case, some of the state of the session for the anonymous user is still preserved. For details, see "Assigning or Switching an Application User".

Example 6-2 How to Create a Real Application Security Session in Java

    Session lws = null;
    static XSSessionManager manager;
    static Connection lwsConn = null;
    static String user = "lwuser";
    String cookie="nst";
    ...
    lws = manager.createSession(lwsConn, user, cookie, null);
    ...

#### 6.2.2 Attaching an Application Session

To attach an application session, use the `attachSession` method of the `XSSessionManager` class (see Example 6-3). The `attachSession` method (in bold typeface) attaches the JDBC connection to the specified Real Application Security application session object. It also enables or disables the dynamic application roles, creates namespaces of the session, and sets the authentication time.

You can also attach to a session by using either ID or cookie as shown in Example 6-4. See [Example 7-2](oracle-fusion-middleware-integration-with-real-application-security.md) for another example of attaching to a session by using a cookie.

Example 6-3 How to Attach a Real Application Security Session in Java

    Session lws = null;
    static Connection lwsConn = null;
    static XSSessionManager manager;
    static String user = "lwuser";
    String cookie = "lwscookie";
    List <String> edynamicRoles = new ArrayList <String>();
    edynamicRoles.add("EDYNROLE001");
    edynamicRoles.add("EDYNROLE002");
    List <String> ddynamicRoles = new ArrayList <String>();
    ddynamicRoles.add("DDYNROLE001");
    ddynamicRoles.add("DDYNROLE002");
    ...
    lws = manager.createSession(lwsConn, user, cookie, null);
    manager.attachSession(lwsConn, lws, edynamicRoles, ddynamicRoles, null, new Timestamp(System.currentTimeMillis()));

Example 6-4 How to Attach Using a Cookie

    Session lws = null;
    static Connection lwsConn = null;
    static XSSessionManager manager;
    ...
    lws = manager.attachSessionByCookie(lwsConn, "myCookie", null, null, null, null, null);

#### 6.2.3 Assigning or Switching an Application User

If you have an anonymous session, you can reassign it to another application user later. Otherwise, if your session is assigned to an application user already, you can switch the session to another application user. In either case, the session must be attached first, before assigning or switching an application user.

To assign a name to a previously anonymous application user, use the `assignUser` method of the `XSSessionManager` class (see Example 6-5). The `assignUser` method (in bold typeface) changes the session context (user and roles) to the given user, for example, `lwuser`, but keeps the existing namespace. It can also change the session at the same time, by any given dynamic roles and namespace parameters, in the same way as the `attachSession` method. The associated session attributes remain in effect unless they are removed through another call.

To change a session user from a named user (non-anonymous) to another named user, use the `switchUser` method of the Session object.

Any request for retaining the dynamic application roles, which were assigned while attaching the session, is disabled. The dynamic application roles are retained for the new application user only when they are also included in the dynamic application roles list for the new application user. The associated session attributes remain in effect unless the session attributes list is reset.

This method changes the session context (user and roles) to the target user (see "[Switching a Current Application User to Another Application User in the Current Application Session](configuring-application-sessions.md)" for details about roles change), but not keeping the existing namespace by default. If you want to retain the existing namespace, you can use the `switchUserKeepState` method of the Session object. It can also change the session at the same time, by any given dynamic roles and namespace parameters, in the same way as the `attachSession` method.

Example 6-6 demonstrates how to switch the application user from `lwuser` to `lwuser1`. The `switchUser` method is in bold typeface.

Example 6-5 How to Assign an Application User to a Session in Java

    Session lws = null;
    static XSSessionManager manager;
    static String user = "lwuser";
    ...
    manager.assignUser(lws, user, null, null, null, new Timestamp(System.currentTimeMillis()));

Example 6-6 How to Switch an Application User in a Session in Java

    Session lws = null;
    Vector<String> listOfNamespaces;
    static String user = "lwuser";
    List<String> nslist1 = new ArrayList<String>();
    ...
    manager.assignUser(lws, user, nslist1, nslist2, nslist3, new Timestamp(System.currentTimeMillis()));
    ...
    lws.switchUser("lwuser1",listOfNamespaces);

#### 6.2.4 Enabling Real Application Security Application Roles

A Real Application Security application role is a role that can be granted only to a Real Application Security application user or to another Real Application Security application role. Real Application Security application roles are granted database privileges through database roles. The database privileges are granted to a database role, which in turn is granted to a Real Application Security application role. For more information about Real Application Security application users and application roles, refer to "[Principals: Users and Roles](indroducing-oracle-database-real-application-security.md)".

This section describes the following operation associated with application roles:

- Enabling a Real Application Security Application Role

- Disabling a Real Application Security Application Role

- Checking If a Real Application Security Application Role Is Enabled

##### 6.2.4.1 Enabling a Real Application Security Application Role

To enable a Real Application Security application role granted to the current application user for the session, use the `enableRole` method of the `Session` interface (see Example 6-7).

The `enableRole` method (in bold typeface) has no effect if the particular application role is currently disabled. This operation requires a database round-trip.

Example 6-7 How to Enable a Real Application Security Application Role in Java

    static Session lws;
    static Roles r1;
    ...
    r1=new Role("HROLE1",null,0);
    lws.enableRole(r1);

##### 6.2.4.2 Disabling a Real Application Security Application Role

To disable a Real Application Security application role granted to the current user for the session, use the `disableRole` method of the `Session` interface (see Example 6-8). This operation requires a database round-trip. The `disableRole` method is in bold typeface.

Example 6-8 How to Disable a Real Application Security Application Role in Java

    static Session lws;
    static Roles r1;
    ...
    r1=new Role("HROLE1",null,0);
    lws.enableRole(r1);
    ...
    lws.disableRole(r1);

##### 6.2.4.3 Checking If a Real Application Security Application Role Is Enabled

To test if the specified application role is enabled in the Real Application Security application session, use the `isRoleEnabled` method of the `Session` interface (see Example 6-9). The `isRoleEnabled` method is in bold typeface.

This method does not have an associated database operation. You must have the `administerSession` Real Application Security application privilege to call this method.

Example 6-9 How to Test If a Real Application Security Application Role Is Enabled in Java

    static Session lws;
    ...
    lws.enableRole("HROLE1");
    ...
    boolean b = lws.isRoleEnabled("HROLE1");

#### 6.2.5 About Performing Namespace Operations as Session User

A namespace is a group of additional attributes of the session context. An application uses a namespace to store application defined attribute-value pairs. The current session user should have `MODIFY_NAMESPACE` (for namespace) and `MODIFY_ATTRIBUTE` (for attribute) application privileges. For more information about namespaces, refer to "[About Using Namespace Templates to Create Namespaces](configuring-application-sessions.md)".

This section describes how to perform the following activities:

- Creating Namespaces

- Deleting Namespaces

- Implicitly Creating Namespaces

- About Using Namespace Attributes

##### 6.2.5.1 Creating Namespaces

To create a namespace in Java, use the `createNamespace` method of the `Session` interface (see Example 6-10). The `createNamespace` method (in bold typeface) creates a new session namespace using the namespace template document, whose name matches with the specified name. If an event handler is specified in the template document, then the specified event handler applies to all the namespaces created using that template.

**Note:**

You can also create a namespace by passing a namespace name as a parameter with the `createSession` and `attachSession` methods discussed in the previous sections.

Example 6-10 How to Create a Namespace in Java

    Session lws = null;
    ...
    SessionNamespace ns = lws.createNamespace("TESTNS1");

##### 6.2.5.2 Deleting Namespaces

To delete a namespace in Java, use the `deleteNamespace` method of the `Session` interface (see Example 6-11). The `deleteNamespace` method (in bold typeface) removes a namespace from a session.

Example 6-11 How to Delete a Namespace in Java

    Session lws = null;
    ...
    SessionNamespace ns = lws.createNamespace("TESTNS1");
    ...
    lws.deleteNamespace("TESTNS1");

##### 6.2.5.3 Implicitly Creating Namespaces

To implicitly create the namespace object to represents the session namespace, use the `getNamespace` method of the `Session` interface (see Example 6-12). The `getNamespace` method is in bold typeface. If the namespace specified already exists, an error is thrown.

To retrieve a String representation of the namespace, use the `toString` method of the `SessionNamespace` interface.

Example 6-12 How to Implicitly Create the Namespace in Java

    Session lws = null;
    ...
    SessionNamespace ns2 = lws.getNamespace("TESTNS1");

##### 6.2.5.4 About Using Namespace Attributes

A session namespace manages the attributes that a single application module stores for the duration of the session. The session namespace stores the attributes in a single namespace, a single set of access control restrictions, or a single event handler procedure that dispatches the attribute change events for that namespace.

This section describes how to perform the following activities:

- Creating a Session Namespace Attribute

- About Setting a Session Namespace Attribute

- Getting a Session Namespace Attribute

- Listing Attributes

- Resetting Attributes

- Deleting Attributes

###### 6.2.5.4.1 Creating a Session Namespace Attribute

To create a session namespace attribute in Java, use the `createAttribute` method of the `SessionNamespace` interface (see Example 6-13). The `createAttribute` method (in bold typeface) creates a new attribute in the namespace.

Example 6-13 How to Create a Session Namespace Attribute in Java

    String name1="empid';
    String value1="JB007";
    SessionNamespace ns;
    ...
    SessionNamespaceAttribute sa1=ns.createAttribute(name1,value1);
    ...

###### 6.2.5.4.2 About Setting a Session Namespace Attribute

To set a session namespace attribute in Java, use the `setAttribute` method of the `SessionNamespace` interface.

###### 6.2.5.4.3 Getting a Session Namespace Attribute

To retrieve a session namespace attribute in Java, use the `getAttribute` method of the `SessionNamespace` interface (see Example 6-14). The `getAttribute` method (in bold typeface) returns the attribute whose name is specified as the parameter.

Example 6-14 How to Retrieve a Session Namespace Attribute in Java

    String name="empid';
    String value="JB007";
    SessionNamespace ns;
    ...
    SessionNamespaceAttribute sa=ns.createAttribute(name,value);
    ...
    String attrvalue =  ns.getAttribute("empid").getValue();
    ns.getAttribute("empid").setValue("newValue");
    ...

###### 6.2.5.4.4 Listing Attributes

To list the attributes in the namespace, use the `listAttributes` method of the `SessionNamespace` interface (see Example 6-15). The `listAttributes` method (in bold typeface) returns a collection of the attribute names in the namespace

Example 6-15 How to List Attributes in Java

    String name1="empid';
    String value1="JB007";
    SessionNamespace ns;
    ...
    SessionNamespaceAttribute sa1=ns.createAttribute(name1,value1);
    ...
    for (Enumeration e = ns.listAttributes() ; e.hasMoreElements() ;) {
     System.out.println("   -- " + e.nextElement());
    }
    ...

###### 6.2.5.4.5 Resetting Attributes

To reset an attribute in Java, use the `resetAttribute` method of the `SessionNamespace` interface (see Example 6-16). The `resetAttribute` method (in bold typeface) resets the attribute in the namespace to its default value.

Example 6-16 How to Reset an Attribute in Java

    String name1="empid';
    String value1="JB007";
    SessionNamespace ns;
    ...
    SessionNamespaceAttribute sa1=ns.createAttribute(name1,value1);
    ...
    ns.resetAttribute("empid");
    ...

###### 6.2.5.4.6 Deleting Attributes

To delete an attribute in Java, use the `deleteAttribute` method of the `SessionNamespace` interface (see Example 6-17). The `deleteAttribute` method (in bold typeface) deletes the particular attribute in the namespace.

Example 6-17 How to Delete an Attribute in Java

    String name1="empid';
    String value1="JB007";
    SessionNamespace ns;
    ...
    SessionNamespaceAttribute sa1=ns.createAttribute(name1,value1);
    ...
    ns.deleteAttribute("empid");
    ...

#### 6.2.6 About Performing Namespace Operations as Session Manager

Each namespace has an associated ACL to determine who can manipulate the namespace and its attributes. If an application does not want the current session user to manipulate the namespace, but allows a session manager to do it, this can be done as session manager `XSSessionManager`.

`XSSessionManager` has a set of overloaded methods as Session, to manage the namespace. The usage is similar to that described for session user in "About Performing Namespace Operations as Session User".

Note that the session manager instance `XSSessionManager` may not be available to the application code; only the trusted infrastructure layer can use the session manager to manipulate such a secured namespace.

#### 6.2.7 About Performing Miscellaneous Session-Related Activities

This section describes the following topics:

- About Getting the Oracle Connection Associated with the Session

- About Getting the Application User ID for the Session

- Getting the Session ID for the Session

- About Getting a String Representation of the Session

- Getting the Session Cookie

- Setting Session Inactivity Timeout as Session Manager

- Setting the Session Cookie as Session Manager

##### 6.2.7.1 About Getting the Oracle Connection Associated with the Session

To get the Oracle connection associated with the session, if it is currently bound to one, use the `getConnection` method of the `Session` interface.

##### 6.2.7.2 About Getting the Application User ID for the Session

To get the application user identifier (ID) for a particular session, use the `getUserId` method of the `Session` interface.

To check if the application user for the session is anonymous, use the `isAnonymous` method of the `Session` interface.

##### 6.2.7.3 Getting the Session ID for the Session

To get the session identifier (ID) for a particular session, use the `getId` method of the `Session` interface (see Example 6-18). The `getId` method is in bold typeface.

Example 6-18 How to Get the Session ID for the Session in Java

    Session lws=null;
    ...
    System.out.println( "The Session ID is" +  lws.getId());

##### 6.2.7.4 About Getting a String Representation of the Session

To get a String representation of the session, use the `toString` method of the `Session` interface.

##### 6.2.7.5 Getting the Session Cookie

To get the secure session cookie used for the session, use the `getSessionCookie` method of the `Session` interface (see Example 6-19). The `getSessionCookie` method is in bold typeface.

Example 6-19 How to Get the Secure Session Cookie in Java

    static Session lws;
    ...
    System.out.println(lws.getSessionCookie());

##### 6.2.7.6 Setting Session Inactivity Timeout as Session Manager

To set the timeout on the session, use the `setInactivityTimeout` method of the `SessionManager` interface. This method sets the session timeout in minutes.

The `setInactivityTimeout` method overrides the normal session timeout configuration. The method is:

    sessionManager.setInactivityTimeout(Session session, int minutes);

##### 6.2.7.7 Setting the Session Cookie as Session Manager

To set the secure session cookie used for the session, use the `setCookie` method of the `SessionManager` interface (see Example 6-20). The `setCookie` method (in bold typeface) returns the secure session cookie used for this session. The method is:

    sessionManager.setCookie(lws,"newCookieValue");

Example 6-20 How to Set the Secure Session Cookie in Java

    static XSSessionManager manager;
    ...
    manager.sessionManager.setCookie(lws,"chocolate chip");

#### 6.2.8 Detaching an Application Session

To detach a Real Application Security application session in Java, use the `detachSession` method of the `XSSessionManager` class (see Example 6-21). The `detachSession` method (in bold typeface) detaches the session whose object it accepts as a parameter. The `detachSession` method call commits all changes in the request at the database level. A database round-trip is required to perform this operation.

Example 6-21 How to Detach a Real Application Security Session in Java

    Session lws = null;
    static XSSessionManager manager;
    static Connection lwsConn = null;
    static String user = "lwuser";
    String cookie;
    ...
    lws = manager.createSession(lwsConn, user, cookie, null);
    manager.attachSession(lwsConn, lws, null, null, null, new Timestamp(System.currentTimeMillis()));
    ...
    manager.detachSession(lws);
    ...

#### 6.2.9 Destroying A Real Application Security Application Session

To destroy a Real Application Security application session in Java, use the `destroySession` method of the `XSSessionManager` class (see Example 6-22). The `destroySession` method (in bold typeface) accepts the database connection object and a session object as parameters. After you call this method, the destroyed session can no longer be accessed from any JVM. A database round-trip is required to perform this operation and for create session as well.

Example 6-22 How to Destroy a Real Application Security Session in Java

    Session lws = null;
    static Connection lwsConn = null;
    static XSSessionManager manager;
    static String user = "lwuser";
    String cookie;
    ...
    lws = manager.createSession(lwsConn, user, cookie, null);
    manager.attachSession(lwsConn, lws, null, null, null, new Timestamp(System.currentTimeMillis()));
    ...
    manager.detachSession(lws);
    manager.destroySession(lwsConn, lws);
    ...

### 6.3 Authenticating Application Users Using Java APIs

Authenticating application users is a main security function needed by applications. The `XSAuthenticationModule` class is used for authenticating application users. The `authenticate` method of the `XSAuthenticationModule` class is used to verify the application user credentials (see Example 6-23). The `authenticate` method is in bold typeface.

Example 6-23 How to Authenticate Application Users in Java

    boolean authOk = false;
    String dbUser;
    String passwd;
    String host;
    String port;
    String sid;
    ...
    authOk = XSAuthenticationModule.authenticate(host + ":" + port + ":" + sid, dbUser, passwd);
    ...

### 6.4 About Authorizing Application Users Using ACLs

Authorization is another main security feature needed by applications. In Real Application Security, the authorization policy comprises of the Access Control Lists (ACLs) and the application privileges. They are defined in the Real Application Security database and managed in a cache in the middle tier. The application privileges are data privileges. Data privileges are used to define the access of a function or operation to data. Once a function attaches a connection to the session, any query passed through the connection is automatically enforced by the database server.

The `AclId` class provides various methods to perform the following:

- Constructing an ACL Identifier

- Using the checkAcl Method

- About Getting Data Privileges Associated with a Specific ACL

#### 6.4.1 Constructing an ACL Identifier

To construct an Access Control List (ACL) identifier, use one of the overloaded parameterized constructors of the `AclId` class (see Example 6-24). If you want to construct an ACL identifier from raw binary data, then use the following constructor:

    public AclId(byte[] raw)

When you invoke this constructor, an ACL identifier, using raw binary returned from the `ora_get_aclids` operator of a query, is created.

If you want to construct an ACL identifier from internal ACL identifiers, then use the following constructor:

    public AclId(java.util.List<java.lang.Long> ids)

When you invoke this constructor, it creates an ACL identifier using internal ACL identifiers.

Example 6-24 How to Construct an ACL Identifier

    Session lws = null;
    static byte[] aclRaw;
    ...
    AclId id = new AclId(aclRaw);
    boolean ret = lws.checkAcl(aclRaw, "UPDATE_INFO");
    ...

#### 6.4.2 Using the checkAcl Method

To check one or more ACLs for specified data privileges, use the `checkAcl` method of the `XSAccessController` class. The data privileges are checked against one or more ACLs defined in the `AclId` object. The `checkAcl` method returns `true` only when all the data privileges are granted in the ACLs. It is important to note that all privileges need not be granted in a single ACL. A session is needed for using the `checkAcl` method as Example 6-25 indicates.

Example 6-25 demonstrates how to get the ACL associated with data privilege `privileges22`.

Example 6-25 How to get an ACL for a Specified Data Privilege

    boolean ret;
    Session lws = null;
    AclId id2 = new AclId(ids);
    List <String> privileges22 = new ArrayList<String>();
    ...
    ret = XSAccessController.checkAcl(lws, id2, privileges22);

#### 6.4.3 About Getting Data Privileges Associated with a Specific ACL

To get a collection of data privileges that are granted in the given ACL, for the given session, use the `getPrivileges` method of the `Session` class.

**Note:**

You use the `checkAcl` method for data security and the `checkPrivilege` method for function security.

### 6.5 Human Resources Administration Use Case: Implementation in Java

This section describes how to verify data security related application privileges at the middle tier. This Java example is based on the Security Human Resources (HR) scenario described in "[Real Application Security: Putting It All Together](configuring-data-security.md)". It uses the `EMPLOYEES` table in the sample `HR` schema. The example uses two Real Application Security application users `DAUSTIN` and `SMAVRIS` to illustrate Real Application Security concepts. The example can be divided into the following modules:

- Setting Up the Mid-Tier Related Configuration

- Setting up the Connection and Initializing the Middle Tier

- Setting up the Session and Authorizing with Middle-Tier API

- Running a Query on the Database

- Performing Cleanup Operations

- The main Method

#### Setting Up the Mid-Tier Related Configuration

To set up the mid-tier configuration involves creating a `DISPATCHER` user and password and granting this user the `xscacfeadmin` and `xsessionadmin` Real Application Security administrator privileges.

    exec xs_principal.create_user(name=>'dispatcher', schema=>'HR');
    exec sys.xs_principal.set_password('dispatcher', 'password');

    exec xs_principal.grant_roles('dispatcher', 'xscacheadmin');
    exec xs_principal.grant_roles('dispatcher', 'xssessionadmin');

#### Setting up the Connection and Initializing the Middle Tier

This example uses the `setupConnection` method to create the connection to the database. The `setupConnection` method accepts a String array as argument, where:

`args[0]`=Database user

`args[1]`=Password

`args[2]`=Host

This method also initializes the middle tier by calling the `getSessionManager` method of the `oracle.security.xs.XSSecurityManager` class.

      public static void setupConnection(String[] args) throws Exception {
        mgrConnection =
            DriverManager.getConnection(args[2], "dispatcher", "password");

        mgr = XSSessionManager.getSessionManager(mgrConnection, 30, 2048000);

        appConnection = DriverManager.getConnection(args[2], args[0], args[1]);
      }

#### Setting up the Session and Authorizing with Middle-Tier API

This example uses `queryAsUser` method to set up the session and authorize with the middle-tier `checkAcl` method. This example creates a session and attaches the session, and then calls the `queryEmployees` method. The `queryEmployees` method in "Running a Query on the Database" checks the ACL for the `UPDATE` privilege, and if `TRUE`, it allows the update; it checks the ACL again for the `VIEW_SALARY` application privilege, and if `TRUE`, it allows access to the `SALARY` column and displays all the employees records including the sensitive data in the `SALARY` column. Then after displaying the employees records, it detaches the session, and destroys the session.

      private static void queryAsUser(String user) throws SQLException {

        System.out.println("\nQuery HR.EMPLOYEES table as user \"" + user + "\"");

        try {
          Session lws = mgr.createSession(appConnection, user, null,null);
          mgr.attachSession(appConnection, lws, null, null, null, null, null);

          queryEmployees(lws);

          mgr.detachSession(lws);
          mgr.destroySession(appConnection, lws);
        } catch (Exception e) {
          e.printStackTrace();
        }
      }

#### Running a Query on the Database

This example uses the `queryEmployees` method to run a query on the HR database.

      public static void queryEmployees(Session lws) throws SQLException {

        Connection conn = lws.getConnection();
        String query =
          " select email, first_name, last_name, department_id, salary, ora_get_aclids(emp) from hr.employees emp where department_id in (40, 60, 100) order by email";

        Statement stmt = null;
        ResultSet rs = null;

        System.out.printf("  EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY\n");

        try {

          stmt = conn.createStatement();
          rs = stmt.executeQuery(query);

          while (rs.next()) {

            String email = rs.getString("EMAIL");
            String first_name = rs.getString("FIRST_NAME");
            String last_name = rs.getString("LAST_NAME");
            String department_id = rs.getString("DEPARTMENT_ID");
            String salary;

            if (((OracleResultSet)rs).getAuthorizationIndicator("SALARY") == AuthorizationIndicator.NONE) {
              salary = rs.getString("SALARY");
            }
            else {
              salary = "*****";
            }

            byte[] aclRaw = rs.getBytes(6);
            String update, viewSalary;
            if (XSAccessController.checkAcl(lws, aclRaw, "UPDATE")) {
              update = "true";
            }
            else {
              update = "false";
            }

            if (XSAccessController.checkAcl(lws, aclRaw, "VIEW_SALARY")) {
              viewSalary = "true";
            }
            else {
              viewSalary = "false";
            }

            System.out.printf("%9s|%12s|%12s|%6s|%8s|%8s|%8s\n", email,
                              first_name, last_name, department_id,
                              salary, update, viewSalary);
           }
        } catch (Exception e) {
          e.printStackTrace();
        } finally {
          try { if (rs != null) rs.close(); } catch (Exception e) {};
          try { if (stmt != null) stmt.close(); } catch (Exception e) {};
        }
      }
    }

The `queryEmployees` method is run for both application users `DAUSTIN` and `SMAVRIS`.

#### Performing Cleanup Operations

This examples uses the `cleanup` method for system cleanup operations.

      public static void cleanupConnection() throws Exception {
        mgrConnection.close();
        appConnection.close();

      }

#### The main Method

This section contains the `main` method for the Java example discussed. This section also contains the different packages that you must import to run the program.

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;


    import java.util.ArrayList;
    import java.util.List;
    import oracle.jdbc.OracleDriver;
    import oracle.jdbc.OracleResultSet;
    import oracle.jdbc.OracleResultSet.AuthorizationIndicator;

    import oracle.security.xs.Role;
    import oracle.security.xs.Session;
    import oracle.security.xs.XSAccessController;
    import oracle.security.xs.XSSessionManager;

    /**
     * HR demo java version, check data security related privilege at mid-tier
     */
    public class HRDemo {

      static Connection mgrConnection = null;
      static Connection appConnection = null;
      static XSSessionManager mgr = null;
      static String user = null;

      public static void main(String[] args)  {

        try {
          DriverManager.registerDriver(new OracleDriver());


          if (args.length >=3) {
            user = args[0];
          } else {
            System.out.println("Usage HRDemo user pwd dbURL");
            System.exit(1);
          }

          setupConnection(args);

          queryAsUser("DAUSTIN");
          queryAsUser("SMAVRIS");

          cleanupConnection();

        } catch (Exception e1) {
          e1.printStackTrace();
        }
      }


1.  Running the Security HR demo in Java assumes that the set up script described in "[Setting Up the Security HR Demo Components](real-application-security-hr-demo.md)" has been run to set up the Real Application Security components.
2.  Compile the Java code.
        $ORACLE_HOME/jdk6/bin/javac -classpath $ORACLE_HOME/rdbms_ho/jlib/xs.jar:$ORACLE_HOME/dbjava/lib/ojdbc6.jar HRdemo.java

    **Note:**

    You must use JDK 6 with `xs.jar` and `ojdbc6.jar`, which are located in the Oracle home directory. Different jars and JDK may not work.
3.  Run the Java code.
        $ORACLE_HOME/jdk6/bin/java -classpath $ORACLE_HOME/rdbms_ho/jlib/xs.jar:$ORACLE_HOME/dbjava/lib/ojdbc6.jar

        HRdemo db_hr db_hr jdbc:oracle:thin:@myserver:myport:mysid

#### 6.5.1 Output

Running the Security HR demo in Java assumes that the set up script described in "[Setting Up the Security HR Demo Components](real-application-security-hr-demo.md)" has been run to set up the Real Application Security components. When you run the Security HR demo, results of two queries are returned.

The first query runs with application user `DAUSTIN`, who has application roles `EMP_ROLE` and `IT_ROLE`, so he can view employee records in the IT department, but he cannot view the `SALARY` column except for his own salary record. The results of the query are as follows:

    Query HR.EMPLOYEES table as user "DAUSTIN"
      EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY
      AHUNOLD|   Alexander|      Hunold|    60|   *****|   false|   false
       BERNST|       Bruce|       Ernst|    60|   *****|   false|   false
      DAUSTIN|       David|      Austin|    60|    4800|   false|    true
     DLORENTZ|       Diana|     Lorentz|    60|   *****|   false|   false
     VPATABAL|       Valli|   Pataballa|    60|   *****|   false|   false

Note that application user `DAUSTIN` can only view the `SALARY` column data for his own record, and no others.

The second query runs with application user SMAVRIS, who has application roles `EMP_ROLE` and `HR_ROLE`, so she can view and update all the employee records. The results of the query are as follows:

    Query HR.EMPLOYEES table as user "SMAVRIS"
      EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY
      AHUNOLD|   Alexander|      Hunold|    60|    9000|    true|    true
       BERNST|       Bruce|       Ernst|    60|    6000|    true|    true
      DAUSTIN|       David|      Austin|    60|    4800|    true|    true
      DFAVIET|      Daniel|      Faviet|   100|    9000|    true|    true
     DLORENTZ|       Diana|     Lorentz|    60|    4200|    true|    true
     ISCIARRA|      Ismael|     Sciarra|   100|    7700|    true|    true
        JCHEN|        John|        Chen|   100|    8200|    true|    true
      JMURMAN| Jose Manuel|       Urman|   100|    7800|    true|    true
        LPOPP|        Luis|        Popp|   100|    6900|    true|    true
     NGREENBE|       Nancy|   Greenberg|   100|   12008|    true|    true
      SMAVRIS|       Susan|      Mavris|    40|    6500|    true|    true
     VPATABAL|       Valli|   Pataballa|    60|    4800|    true|    true

Note that application user `SMAVRIS` can view all the employee records, including all data in the `SALARY` column.
