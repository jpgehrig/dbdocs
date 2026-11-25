This section describes the implementation requirements for JNDI support in the Oracle JVM. This section is divided into the following sections:

- Namespace

- Oracle Java Directory Service JNDI Name Space Provider

- Namespace Browser

### 11.2.1 Namespace

The namespace is represented similarly as in the typical Unix File System structure. The root directory and the directory separator are represented by the slash symbol (/). The root directory is owned by `SYS` and only `SYS` can create new subdirectories under it.

The following two directories (`DirContexts`) are created during the installation process of OJDS:

- `/public` directory

  The `/public` directory is a public area for testing and any user can bind, delete, or lookup objects in this directory.

- `/etc` directory

  The `/etc` directory is an area for the deployment of all production type objects that a client may need and is protected from any update or removal. The `/etc` directory is writable only by the `SYS` user, but is readable by all users.

#### 11.2.1.1 Object permissions

You can assign permissions to the objects stored in the directory structure. These permissions are a union of the following permissions:

- Read

- Write

- Execute

The following table describes the permissions that you can assign to the objects stored in the directory structure:

| Action               | Parent Context Permissions | Child (obj/ctx) Permissions |
|:---------------------|:---------------------------|:----------------------------|
| `bind`               | Write                      | NA                          |
| `unbind`             | Write                      | Write                       |
| `createSubcontext`   | Write                      | NA                          |
| `getAttributes`      | Read                       | Read                        |
| `rebind`             | Write                      | Write                       |
| `destroySub context` | Write                      | Write                       |
| `list`               | Read                       | Read                        |
| `listBindings`       | Read                       | Read                        |
| `lookup`             | Read                       | Read                        |
| `lookupLink`         | Read                       | Read                        |
| `rename (target)`    | Write                      | Write (if exists)           |
| `rename (source)`    | Read                       | Read                        |

**Note:**

All parent contexts must have Execute permission for operations to succeed.

#### 11.2.1.2 Persistent Storage Tables, Indexes, and Sequences

The database tables owned by `OJVMSYS` store the following details for each object:

- Namespace metadata

- Bound names

- Attributes

- Permissions

- Stored object representations

#### 11.2.1.3 Initial Contexts and Permissions

The following table shows the contexts that are created by default at the time of installation:

| Name    | Owner | Read   | Write  | Execute |
|:--------|:------|:-------|:-------|:--------|
| /       | SYS   | PUBLIC | SYS    | PUBLIC  |
| /public | SYS   | PUBLIC | PUBLIC | PUBLIC  |
| /etc    | SYS   | PUBLIC | SYS    | PUBLIC  |

#### 11.2.1.4 Object and Context Default Permissions

When a context is created or an object is bound to the OJDS, then the Read and Execute permissions are granted to the user or schema that creates the context.

### 11.2.2 Oracle Java Directory Service JNDI Name Space Provider

This section describes the following Oracle Java Directory Service concepts:

- Directory Context

- StateFactories

- ObjectFactories

- OJDS URL Support

- Client classpath

#### 11.2.2.1 Directory Context

The Oracle Java Directory Service (OJDS) must implement the interface as specified by the `javax.naming.directory.DirContext` context. The `javax.naming.directory.DirContext` context, the `oracle.aurora.jndi.ojds.OjdsServerContext` context, and the `oracle.aurora.jndi.ojds.OjdsClientContext` context provide the methods for examining and updating attributes associated with the objects, and enables searches of the directory for server-side and client-side executions respectively.

The following table describes the JNDI properties that you can use for creating a context or using a context:

| Package Name                       | Description                                                                                                                                                                                                                                 |
|:-----------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `java.naming.factory.initial`      | Specifies what class to use to create initial contexts for the application. The `oracle.aurora.jndi.ojds` package defines the `oracle.aurora.jndi.ojds.OjdsInitialContextFactory` for use with this property to create `InitialDirContext`. |
| `java.naming.security.principal`   | Specifies the user ID for creating a database connection. You must specify the value for this property.                                                                                                                                     |
| `java.naming.security.credentials` | Specifies the password for creating a database connection. You must specify the value for this property.                                                                                                                                    |
| `java.naming.provider.url`         | Specifies the connection URL for creating a database connection. This property is optional.                                                                                                                                                 |
| `java.naming.factory.url.pkgs`     | Is a colon separated list of URL handlers for specific JNDI implementations. The `oracle.aurora.jndi.ojds.OjdsURLContextFactory` class returns a context based on an OJDS URL.                                                              |

#### 11.2.2.2 StateFactories

A `StateFactory` transforms a Java object into an object that can be stored in the implementing JNDI provider. The OJDS converts all the objects to bind to a serialized object. OJDS follows the specifications of the `java.io.Serializable` interface and the Java Object Serialization Specification for this conversion. Once serialized, the object is stored in the OJDS persistent store. No external `StateFactories` are supported for OJDS.

#### 11.2.2.3 ObjectFactories

An `ObjectFactory` takes objects stored in the implementing JNDI provider and converts them to back into Java objects.The OJDS does not support external `ObjectFactories`. The serialized objects are created from their binary form that are retrieved from the OJDS persistent store. After an object is deserialized, OJDS handles the object in one of the following ways:

- If the object is a `Context`, then the `connection` and the `env` fields are set and a `DirContext` is returned.

- If the object is a `javax.naming.Reference`, then you can use the `DirectoryManager.getObjectInstance` method to create the object.

- If the object is neither a `Context` nor a `javax.naming.Reference`, then the object is returned as it is to the user.

The retrieved bytes specifying an object must conform to the `java.io.Serializable` interface standards. If the class implementing the object changes on the client, then the deserialization of the object can fail. So, you must be careful to maintain compatibility between the object bytes and the class or object stream deserializing the object bytes.

#### 11.2.2.4 OJDS URL Support

The OJDS supports a URL specified in the following format:

`ojds://jdbc_connection_url/path…/object`

In the preceding syntax:

- `jdbc_connection_url` is one of the supported JDBC connection URLs. You must specify the `jdbc_connection_url` in the URL to connect to the directory.

  **Note:**

  The OJDS provider supports both the thin and OCI URLs for a JDK-based external client. For example, you can use the following URLs for thin driver and OCI driver respectively:

      thin:localhost:5521:mysid
      oci:22.133.242:5521:mysid

  However, OJDS URL support in the server is only for thin connection type. You must set a value for `Context.SECURITY_PRINCIPAL` and `Context.SECURITY_CREDENTIALS` to complete the URL connection.

- `path` is a slash<sup>Foot 1</sup>-separated list similar to a Unix type file system. This represents nodes in the Directory tree.

- `object` is the actual terminal object name in the context. If the object is omitted, then the path terminates in a slash (/). In such a case, a `DirContext` is returned representing this path as the root.

##### Example

The following code snippet shows how to look up for the object `myobj` of type `MyObj` in the directory `/one/two` using the OCI driver connected as user `HR`:

    import javax.naming.*;
    .
    .
    .
    Hashtable env = new Hashtable();
    env.put(“java.naming.security.principal",“HR");
    @ env.put(“java.naming.security.credentials","<password>");
    MyObj obj = (MyObj)(new InitialDirContext(env)).lookup(ojds://oci:host1:5521:mysid/one/two/myobj");

#### 11.2.2.5 Client classpath

You must add the `$ORACLE_HOME/jdbc/lib/ojdbc6.jar` and `$ORACLE_HOME/javavm/lib/aurora.zip` jar files to the classpath for a JDK client to use the OJDS.

### 11.2.3 Namespace Browser

The namespace browser enables browsing permissions and properties of objects stored in the OJDS. The existing `ojvmjava` utility is enhanced to support the operations as described in the following table:

| Command Name | Description                                                                             |
|:-------------|:----------------------------------------------------------------------------------------|
| `ls`         | Lists the contents of a context similar to Unix `ls` command.                           |
| `rm`         | Removes the context or an object.                                                       |
| `mkdir`      | Creates a context in the OJDS.                                                          |
| `chown`      | Changes the owner of the given context, object, and so on.                              |
| `chmod`      | Changes rights on objects or contexts.                                                  |
| `cd`         | Changes the working context.                                                            |
| `pwd`        | Lists the current working context.                                                      |
| `ln`         | Refers to the same object by using different names, similar to a symbolic link in Unix. |
| `mv`         | Changes or rebinds old names of a context (or object), to a new name.                   |
| `bind`       | Binds an object reference or naming context into the JNDI namespace.                    |
| `bindds`     | Binds a Data Source object to a given context.                                          |
| `bindurl`    | Binds a URL object to the given context.                                                |

**Related Topics**

- [The ojvmjava Tool](ojvmjava-tool.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

The slash symbol (\\
