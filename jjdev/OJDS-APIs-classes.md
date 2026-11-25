This section describes the following OJDS APIs and classes:

- oracle.aurora.jndi.ojds.OjdsClientContext

- oracle.aurora.jndi.ojds.OjdsServerContext

- oracle.aurora.jndi.ojds.OjdsInitialContextFactory

- oracle.aurora.jndi.ojds.OjdsURLContextFactory

- oracle.aurora.jndi.ojds.OjdsURLContext

### 11.4.1 oracle.aurora.jndi.ojds.OjdsClientContext

This class implements the `javax.naming.directory.DirContext` interface. It establishes connection with the database and performs all functions required to support the OJDS. It supports all the methods described in `[DirContext]` except the following methods:

- `getSchema`

- `getSchemaClassDefintion`

- `modifyAttributes`

- `search`

This class is created automatically when an `InitialDirContext` is created on a JAVA JDK based client. It provides the communication and object transport between the client application and the OJDS.

You must set the following JNDI properties to specific values to complete a connection:

- `java.naming.factory.initial` to `oracle.aurora.jndi.ojds.OjdsIntialContextFactory`

- `java.naming.security.principal` to the name of the connection schema

- `java.naming.security.credentials` to the schema password

- `java.naming.provider.url` to a valid OJDS URL

You can set these properties as shown in the following code snippet:

    Hashtable env = new Hashtable();
    env.put("java.naming.factory.initial", "oracle.aurora.jndi.ojds.OjdsInitialContextFactory");
    env.put(Context.SECURITY_PRINCIPAL, "HR");
    env.put(Context.SECURITY_CREDENTIALS, "<password>");
    env.put(Context.PROVIDER_URL,"ojds://thin:localhost:5521:j3");

### 11.4.2 oracle.aurora.jndi.ojds.OjdsServerContext

This class implements the `javax.naming.directory.DirContext` interface. It uses the internal database connection to communicate with the OJDS persistent store. It supports all the methods described in `[DirContext]` except for the following methods:

- `getSchema`

- `getSchemaClassDefintion`

- `modifyAttributes`

- `search`

This class is created automatically when an `InitialDirContext` is created in a database resident application. It uses the database internal JDBC driver to communicate with the OJDS persistent store.

The four environment properties for the `OjdsClientContext` are ignored for `OjdsServerContext` because the application runs as the `login` schema. The connection is made with the kprb \[JDBC\] internal driver. If the Java stored procedure requires access outside the server, then you must use the OJDS `URLContext` as the value of the `java.naming.provider.url` property.

**Related Topics**

- oracle.aurora.jndi.ojds.OjdsInitialContextFactory

### 11.4.3 oracle.aurora.jndi.ojds.OjdsInitialContextFactory

This class implements the `javax.naming.spi.InitialContextFactory` interface. The JNDI `InitialContext` or `InitialDriContext` classes create either an `OjdsClientContext` or an `OjdsServerContext` depending on the execution environment.

### 11.4.4 oracle.aurora.jndi.ojds.OjdsURLContextFactory

This class supports OJDS style URLs. Depending on the method provided to the URL, this method can return a `DirContext` or an instance of an object stored in the OJDS.

### 11.4.5 oracle.aurora.jndi.ojds.OjdsURLContext

This class is an extension of the `oracle.aurora.jndi.ojds.OjdsClientContext.` It supports extraction of connection information from an OJDS URL and making a connection to the OJDS. It supports the same interfaces as `oracle.aurora.jndi.ojds.OjdsClientContext` class.

You must set the following parameters to use the `OjdsURLContext` class:

- `javax.naming.security.principal` to the connection schema

- `javax.naming.security.credentials` to the password of the connection schema

- `javax.naming.factory.initial` to `oracle.aurora.jndi.ojds.OjdsInitialContextFactory`

You can set these properties as shown in the following code snippet:

    Hashtable env = new Hashtable();
    env.put("java.naming.factory.initial", "oracle.aurora.jndi.ojds.OjdsInitialContextFactory");
    env.put(Context.SECURITY_PRINCIPAL, "HR");
    env.put(Context.SECURITY_CREDENTIALS, "<password>");
    DirContext dir =
    (new InitialContext(env)).lookup(“ojds://thin:localhost:5521:j3/public./mydir");
