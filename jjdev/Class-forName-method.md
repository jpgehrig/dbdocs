The JLS provides the following description of `Class.forName()`:

Given the fully qualified name of a class, this method attempts to locate, load, and link the class. If it succeeds, then a reference to the `Class` object for the class is returned. If it fails, then an instance of `ClassNotFoundException` is thrown.

Class lookup is always on behalf of a referencing class and is done through an instance of `ClassLoader`. The difference between the Java Development Kit (JDK) implementation and Oracle JVM implementation is the method in which the class is found:

- The JDK uses one instance of `ClassLoader` that searches the set of directory tree roots specified by the `CLASSPATH` environment variable.

- Oracle JVM defines several resolvers that specify how to locate classes. Every class has a resolver associated with it, and each class can, potentially, have a different resolver. When you run a method that calls `Class.forName()`, the resolver of the currently running class, which is `this`, is used to locate the class.

You can receive unexpected results if you try to locate a class with an incorrect resolver. For example, if a class `X` in schema `X` requests a class `Y` in schema `Y` to look up class `Z`, you will experience an error if you expected the resolver of class `X` to be used. Because class `Y` is performing the lookup, the resolver associated with class `Y` is used to locate class `Z`. In summary, if the class exists in another schema and you specified different resolvers for different classes, as would happen by default if they are in different schemas, you may not find the class.

You can solve this resolver problem as follows:

- Avoid any class name lookup by passing the `Class` object itself.

- Supply the `ClassLoader` instance in the `Class.forName()` method.

- Supply the class and the schema it resides in to the `classForNameAndSchema()` method.

- Supply the schema and class name to `ClassForName.lookupClass()`.

- Serialize your objects with the schema name and the class name.

**Note:**

Another unexpected behavior can occur if system classes invoke `Class.forName()`. The desired class is found only if it resides in `SYS` or in `PUBLIC`. If your class does not exist in either `SYS` or `PUBLIC`, then you can declare a `PUBLIC` synonym for the class.

This section covers the following topics:

- Supply ClassLoader in Class.forName()

- Supply Class and Schema Names to classForNameAndSchema()

- Supply Class and Schema Names to lookupClass()

- Supply Class and Schema Names when Serializing

- Class.forName Example

**Related Topics**

- [Overview of Resolving Class Dependencies](preparing-Java-class-methods.md)

### 2.8.1 Supply ClassLoader in Class.forName()

Oracle Database uses resolvers for locating classes within schemas. Every class has a specified resolver associated with it, and each class can have a different resolver associated with it. As a result, the locating of classes is dependent on the definition of the associated resolver. The `ClassLoader` instance knows which resolver to use, based on the class that is specified. When you supply a `ClassLoader` instance to `Class.forName()`, your class is looked up in the schemas defined in the resolver of the class. The syntax of this variant of `Class.forName()` is as follows:

    Class.forName (String name, boolean initialize, ClassLoader loader);

The following examples show how to supply the class loader of either the current class instance or the calling class instance.

Example 2-1 Retrieve Resolver from Current Class

You can retrieve the class loader of any instance by using the `Class.getClassLoader()` method. The following example retrieves the class loader of the class represented by instance `x`:

    Class c1 = Class.forName (x.whatClass(), true, x.getClass().getClassLoader());

Example 2-2 Retrieve Resolver from Calling Class

You can retrieve the class of the instance that called the running method by using the `oracle.aurora.vm.OracleRuntime.getCallerClass()` method. After you retrieve the class, call the `Class.getClassLoader()` method on the returned class. The following example retrieves the class of the instance that called the `workForCaller()` method. Then, its class loader is retrieved and supplied to the `Class.forName()` method. As a result, the resolver used for looking up the class is the resolver of the calling class.

    void workForCaller()
    {
      ClassLoader c1=oracle.aurora.vm.OracleRuntime.getCallerClass().getClassLoader();
      ...
      Class c=Class.forName(name, true, c1);
      ...
    }

### 2.8.2 Supply Class and Schema Names to classForNameAndSchema()

You can resolve the problem of where to find the class by supplying the resolver, which can identify the schemas to be searched. Alternatively, you can supply the schema in which the class is loaded. If you know in which schema the class is loaded, then you can use the `classForNameAndSchema()` method, which is in the `DbmsJava` class provided by Oracle Database. This method takes both the name of the class and the schema in which the class resides and locates the class within the designated schema.

Example 2-3 Providing Schema and Class Names

The following example shows how you can save the schema and class names using the `save()` method. Both names are retrieved, and the class is located using the `DbmsJava.classForNameAndSchema()` method.

    import oracle.aurora.rdbms.ClassHandle;
    import oracle.aurora.rdbms.Schema;
    import oracle.aurora.rdbms.DbmsJava;

    void save (Class c1)
    {
      ClassHandle handle = ClassHandle.lookup(c1);
      Schema schema = handle.schema();
      writeName (schema.getName());
      writeName (c1.getName());
    }

    Class restore()
    {
      String schemaName = readName();
      String className = readName();
      return DbmsJava.classForNameAndSchema (schemaName, className);
    }

### 2.8.3 Supply Class and Schema Names to lookupClass()

You can supply a `String` value containing both the schema and class names to the `oracle.aurora.util.ClassForName.lookupClass()` method. When called, this method locates the class in the specified schema. The string must be in the following format:

    "<schema>:<class>"

For example, to locate `com.package.myclass` in the `HR` schema, use the following:

    oracle.aurora.util.ClassForName.lookupClass("HR:com.package.myclass");

**Note:**

Use uppercase characters for the schema name. In this case, the schema name is case-sensitive.

### 2.8.4 Supply Class and Schema Names when Serializing

When you deserialize a class, part of the operation is to lookup a class based on a name. To ensure that the lookup is successful, the serialized object must contain both the class and schema names.

Oracle Database provides the following classes for serializing and deserializing objects:

- `oracle.aurora.rdbms.DbmsObjectOutputStream`

  This class extends `java.io.ObjectOutputStream` and adds schema names in the appropriate places.

- `oracle.aurora.rdbms.DbmsObjectInputStream`

  This class extends `java.io.ObjectInputStream` and reads streams written by `DbmsObjectOutputStream`. You can use this class in any environment. If used within Oracle Database, then the schema names are read out and used when performing the class lookup. If used on a client, then the schema names are ignored.

### 2.8.5 Class.forName Example

The following example shows several methods for looking up a class:

    import oracle.aurora.vm.OracleRuntime;
    import oracle.aurora.rdbms.Schema;
    import oracle.aurora.rdbms.DbmsJava;

    public class ForName
    {
      private Class from;

      /* Supply an explicit class to the constructor */
      public ForName(Class from)
      {
        this.from = from;
      }

      /* Use the class of the code containing the "new ForName()" */
      public ForName()
      {
        from = OracleRuntime.getCallerClass();
      }

      /* lookup relative to Class supplied to constructor */
      public Class lookupWithClassLoader(String name) throws ClassNotFoundException
      {
        /* A ClassLoader uses the resolver associated with the class*/
        return Class.forName(name, true, from.getClassLoader());
      }

      /* In case the schema containing the class is known */
      static Class lookupWithSchema(String name, String schema)
      {
        Schema s = Schema.lookup(schema);
        return DbmsJava.classForNameAndSchema(name, s);
      }
    }

The preceding example uses the following methods for locating a class:

- To use the resolver of the class of an instance, call `lookupWithClassLoader()`. This method supplies a class loader to the `Class.forName()` method in the `from` variable. The class loader specified in the `from` variable defaults to this class.

- To use the resolver from a specific class, call `ForName()` with the designated class name, followed by `lookupWithClassLoader()`. The `ForName()` method sets the `from` variable to the specified class. The `lookupWithClassLoader()` method uses the class loader from the specified class.

- To use the resolver from the calling class, first call the `ForName()` method without any parameters. It sets the `from` variable to the calling class. Then, call the `lookupWithClassLoader()` method to locate the class using the resolver of the calling class.

- To lookup a class in a specified schema, call the `lookupWithSchema()` method. This provides the class and schema name to the `classForNameAndSchema()` method.
