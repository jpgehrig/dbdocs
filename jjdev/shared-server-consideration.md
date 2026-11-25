**Note:**

Oracle recommends dedicated servers for performance reasons. Additionally, dedicated servers support a class of applications that rely on threads and sockets that stay open across calls. For example, the JMX agent connectivity functionality.

For sessions that use shared servers, certain limitations exist across calls. The reason is that a session that uses a shared server is not guaranteed to connect to the same process on a subsequent database call, and hence the session-specific memory and objects that need to live across calls are saved in the SGA. This means that process-specific resources, such as threads, open files, and sockets, must be cleaned up at the end of each call, and therefore, will not be available for the next call.

This section covers the following topics:

- End-of-Call Migration

- Oracle-Specific Support for End-of-Call Optimization

- The EndOfCallRegistry.registerCallback() Method

- The EndOfCallRegistry.runCallbacks() Method

- The Callback Interface

- The Callback.act() method

- Operating System Resources Affected Across Calls

**Related Topics**

- [Managing Your Applications Using JMX](using-JMX.md)

### 2.13.1 End-of-Call Migration

In the shared server mode, Oracle Database preserves the state of your Java program between calls by migrating all objects that are reachable from `static` variables to session space at the end of the call. Session space exists within the session of the client to store `static` variables and objects that exist between calls. Oracle JVM automatically performs this migration operation at the end of every call.

This migration operation is a memory and performance consideration. Hence, you should be aware of what you designate to exist between calls and keep the `static` variables and objects to a minimum. If you store objects in `static` variables needlessly, then you impose an unnecessary burden on the memory manager to perform the migration and consume per-session resources. By limiting your `static` variables to only what is necessary, you help the memory manager and improve the performance of your server.

To maximize the number of users who can run your Java program at the same time, it is important to minimize the footprint of a session. In particular, to achieve maximum scalability, an inactive session should take up as little memory space as possible. A simple technique to minimize footprint is to release large data structures at the end of every call. You can lazily re-create many data structures when you need them again in another call. For this reason, Oracle JVM has a mechanism for calling a specified Java method when a session is about to become inactive, such as at the end of a call.

This mechanism is the `EndOfCallRegistry` notification. It enables you to clear `static` variables at the end of the call and reinitialize the variables using a lazy initialization technique when the next call comes in. You should run this only if you are concerned about the amount of storage you require the memory manager to store in between calls. It becomes a concern only for complex stateful server applications that you implement in Java.

The decision of whether to null-out data structures at the end of the call and then re-create them for each new call is a typical time and space trade-off. There is some extra time spent in re-creating the structure, but you can save significant space by not holding on to the structure between calls. In addition, there is a time consideration, because objects, especially large objects, are more expensive to access after they have been migrated to session space. The penalty results from the differences in representation of session, as opposed to objects based on call-space.

Examples of data structures that are candidates for this type of optimization include:

- Buffers or caches.

- Static fields, such as arrays, which once initialized can remain unchanged during the course of the program.

- Any dynamically built data structure that can have a space-efficient representation between calls and a more speed-efficient representation for the duration of a call. This can be tricky and may complicate your code, making it hard to maintain. Therefore, you should consider doing this only after demonstrating that the space saved is worth the effort.

### 2.13.2 Oracle-Specific Support for End-of-Call Optimization

You can register the `static` variables that you want cleared at the end of the call when the buffer, field, or data structure is created. Within the `oracle.aurora.memoryManager.EndOfCallRegistry` class, the `registerCallback()` method takes an object that implements a `Callback` object. The `registerCallback()` method stores this object until the end of the call. At the end of the call, Oracle JVM calls the `act()` method within all registered `Callback` objects. The `act()` method within the `Callback` object is implemented to clear the user-defined buffer, field, or data structure. Once cleared, the `Callback` object is removed from the registry.

**Note:**

If the end of the call is also the end of the session, then callbacks are not started, because the session space will be cleared anyway.

A weak table holds the registry of end-of-call callbacks. If either the `Callback` object or value are not reachable from the Java program, then both the object and the value will be dropped from the table. The use of a weak table to hold callbacks also means that registering a callback will not prevent the garbage collector from reclaiming that object. Therefore, you must hold on to the callback yourself if you need it, and you cannot rely on the table holding it back.

The way you use `EndOfCallRegistry` depends on whether you are dealing with objects held in `static` fields or instance fields.

#### Static fields

Use `EndOfCallRegistry` to clear state associated with an entire class. In this case, the `Callback` object should be held in a `private` `static` field. Any code that requires access to the cached data that was dropped between calls must call a method that lazily creates, or re-creates, the cached data.

Consider the following example:

    import oracle.aurora.memoryManager.Callback;
    import oracle.aurora.memoryManager.EndOfCallRegistry;

    class Example
    {
      static Object cachedField = null;
      private static Callback thunk = null;

      static void clearCachedField()
      {
        // clear out both the cached field, and the thunk so they don't
        // take up session space between calls
        cachedField = null;
        thunk = null;
      }

      private static Object getCachedField()
      {
        if (cachedField == null)
        {
          // save thunk in static field so it doesn't get reclaimed
          // by garbage collector
          thunk = new Callback () {
            public void act(Object obj)
            {
              Example.clearCachedField();
            }
          };

          // register thunk to clear cachedField at end-of-call.
          EndOfCallRegistry.registerCallback(thunk);
          // finally, set cached field
          cachedField = createCachedField();
        }
        return cachedField;
      }

      private static Object createCachedField()
      {
        ...
      }
    }

The preceding example does the following:

1.  Creates a `Callback` object within a `static` field, `thunk`.

2.  Registers this `Callback` object for end-of-call migration.

3.  Implements the `Callback.act()` method to free up all `static` variables, including the `Callback` object itself.

4.  Provides a method, `createCachedField()`, for lazily re-creating the cache.

When you create the cache, the `Callback` object is automatically registered within the `getCachedField()` method. At end-of-call, Oracle JVM calls the registered `Callback.act()` method, which frees the static memory.

#### Instance fields

Use `EndOfCallRegistry` to clear state in data structures held in instance fields. For example, when a state is associated with each instance of a class, each instance has a field that holds the cached state for the instance and fills in the cached field as necessary. You can access the cached field with a method that ensures the state is cached.

Consider the following example:

    import oracle.aurora.memoryManager.Callback;
    import oracle.aurora.memoryManager.EndOfCallRegistry;

    class Example2 implements Callback
    {
      private Object cachedField = null;

      public voidact (Object obj)
      {
        // clear cached field
        cachedField = null;
        obj = null;
      }

      // our accessor method
      private static Object getCachedField()
      {
        if (cachedField == null)
        {
          // if cachedField is not filled in then you must
          // register self, and fill it in.
          EndOfCallRegistry.registerCallback(self);
          cachedField = createCachedField();
        }
        return cachedField;
      }

      private Object createCachedField()
      {
        ...
      }
    }

The preceding example does the following:

1.  Implements the instance as a `Callback` object.

2.  Implements the `Callback.act()` method to free up the instance fields.

3.  When you request a cache, the `Callback` object registers itself for the end-of-call migration.

4.  Provides a method, `createCachedField()`, for lazily re-creating the cache.

When you create the cache, the `Callback` object is automatically registered within the `getCachedField()` method. At end-of-call, Oracle JVM calls the registered `Callback.act()` method, which frees the cache.

This approach ensures that the lifetime of the `Callback` object is identical to the lifetime of the instance, because they are the same object.

### 2.13.3 The EndOfCallRegistry.registerCallback() Method

The `registerCallback()` method installs a `Callback` object within a registry. At the end of the call, Oracle JVM calls the `act()` method of all registered `Callback` objects.

You can register your `Callback` object by itself or with an `Object` instance. If you need additional information stored within an object to be passed into `act()`, then you can register this object with the `value` parameter, which is an instance of `Object`.

The following are the valid signatures of the `registerCallback()` method:

    public static void registerCallback(Callback thunk, Object value);

    public static void registerCallback(Callback thunk);

The following table lists the parameters of `registerCallback` and their description:

| Parameter | Description                                                                                                                                                                                                                                                                                                             |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `thunk`   | The `Callback` object to be called at the end-of-call migration.                                                                                                                                                                                                                                                        |
| `value`   | If you need additional information stored within an object to be passed into `act()`, then you can register this object with the `value` parameter. In some cases, the `value` parameter is necessary to hold the state that the callback needs. However, most users do not need to specify a value for this parameter. |

### 2.13.4 The EndOfCallRegistry.runCallbacks() Method

The signature of the `runCallbacks()` method is as follows:

    static void runCallbacks()

JVM calls this method at end-of-call and calls `act()` for every `Callback` object registered using `registerCallback()`. It is called at end-of-call, before object migration and before the last finalization step.

**Note:**

Do not call this method in your code.

### 2.13.5 The Callback Interface

The interface is declared as follows:

    Interface oracle.aurora.memoryManager.Callback

Any object you want to register using `EndOfCallRegistry.registerCallback()` must implement the `Callback` interface. This interface can be useful in your application, where you require notification at end-of-call.

### 2.13.6 The Callback.act() method

The signature of the `act()` method is as follows:

    public void act(Object value)

You can implement any activity that you require to occur at the end of the call. Usually, this method contains procedures for clearing any memory that would be saved to session space.

### 2.13.7 Operating System Resources Affected Across Calls

In the shared server mode, Oracle JVM closes any open operating system resources at the end of a database call.

The following table lists the operating system resources across calls and specifies the corresponding lifetime.

| Resource                                          | Lifetime                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Files                                             | The system closes all files left open when a database call ends.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Threads                                           | All threads are terminated when a call ends.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Sockets                                           | • Client sockets can exist across calls.<br>• Server sockets terminate when the call ends.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Objects that depend on operating system resources | Regardless of the usable lifetime of the object, the Java object can be valid for the duration of the session. This can occur, for example, if the Java object is stored in a `static` class variable, or a class variable references it directly or indirectly. If you attempt to use one of these Java objects after its usable lifetime is over, then Oracle Database will throw an exception. This is true for the following examples:<br>• If an attempt is made to read from a `java.io.FileInputStream` that was closed at the end of a previous call, then a `java.io.IOException` is raised.<br>• `java.lang.Thread.isAlive()` is `false` for any `Thread` object running in a previous call and still accessible in a subsequent call. |

You should close resources that are local to a single call when the call ends. However, for `static` objects that hold on to operating system resources, you must be aware of how these resources are affected after the call ends.

#### Files

In the shared server mode, Oracle JVM automatically closes open operating system constructs when the call ends. This can affect any operating system resources within your Java object. If you have a file opened within a `static` variable, then the file handle is closed at the end of the call for you. Therefore, if you hold on to the `File` object across calls, then the next usage of the file handle throws an exception.

In the following example, the `Concat` class enables multiple files to be written into a single file, `outFile`. On the first call, `outFile` is created. The first input file is opened, read, written to `outFile`, and the call ends. Because `outFile` is defined as a `static` variable, it is moved into session space between call invocations. However, the file handle is closed at the end of the call. The next time you call `addFile()`, you will get an exception.

Example 2-5 Compromising Your Operating System Resources

    public class Concat
    {
      static File outFile = new File("outme.txt");
      FileWriter out = new FileWriter(outFile);

      public static void addFile(String[] newFile)
      {
        File inFile = new File(newFile);
        FileReader in = new FileReader(inFile);
        int i;

        while ((i = in.read()) != -1)
          out.write(i);
        in.close();
      }
    }

There are workarounds. To ensure that your handles stay valid, close your files, buffers, and so on, at the end of every call, and reopen the resource at the beginning of the next call. Another option is to use the database rather than using operating system resources. For example, try to use database tables rather than a file. Alternatively, do not store operating system resources within `static` objects that are expected to live across calls. Instead, use operating system resources only within objects local to the call.

The following example shows how you can perform concatenation, without compromising your operating system resources. The `addFile()` method opens the `outme.txt` file within each call, ensuring that anything written into the file is appended to the end. At the end of each call, the file is closed. Two things occur:

- The `File` object no longer exists outside a call.

- The operating system resource, the `outme.txt` file, is reopened for each call. If you had made the `File` object a `static` variable, then the closing of `outme.txt` within each call would ensure that the operating system resource is not compromised.

Example 2-6 Correctly Managing Your Operating System Resources

    public class Concat
    {

      public static void addFile(String[] newFile)
      {
        /*open the output file each call; make sure the input*/
        /*file is written out to the end by making it "append=true"*/
        FileWriter out = new FileWriter("outme.txt", TRUE);
        File inFile = new File(newFile);
        FileReader in = new FileReader(inFile);
        int i;

        while ((i = in.read()) != -1)
          out.write(i);
        in.close();

        /*close the output file between calls*/
        out.close();
      }
    }

#### Sockets

Sockets are used in setting up a connection between a client and a server. For each database connection, sockets are used at either end of the connection. Your application does not set up the connection. The connection is set up by the underlying networking protocol, TTC or IIOP of Oracle Net.

**See Also:**

"[Configuring Oracle JVM](configuring-Oracle-JVM.md)" for information about how to configure your connection.

You may also want to set up another connection, for example, connecting to a specified URL from within one of the classes stored within the database. To do so, instantiate sockets for servicing the client and server sides of the connection using the following:

- The `java.net.Socket()` constructor creates a client socket.

- The `java.net.ServerSocket()` constructor creates a server socket.

A socket exists at each end of the connection. The server side of the connection that listens for incoming calls is serviced by a `ServerSocket` instance. The client side of the connection that sends requests is serviced through a `Socket` instance. You can use sockets as defined within JVM with the restriction that a `ServerSocket` instance within a shared server cannot exist across calls.

The following table lists the socket types and their description:

| Socket Type  | Description                                                                                                                                                                                                                                                                                                                                                           |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Socket       | Because the client side of the connection is outbound, the `Socket` instance can be serviced across calls within a shared server.                                                                                                                                                                                                                                     |
| ServerSocket | The server side of the connection is a listener. The `ServerSocket` instance is closed at the end of a call within a shared server. The shared servers move on to another client at the end of every call. You will receive an I/O exception stating that the socket was closed, if you try to use the `ServerSocket` instance outside of the call it was created in. |

#### Threads

In the shared server mode, when a call ends because of a return or uncaught exceptions, Oracle JVM throws `ThreadDeathException` in all daemon threads. `ThreadDeathException` essentially forces threads to stop running. Code that depends on threads living across calls does not behave as expected in the shared server mode. For example, the value of a `static` variable that tracks initialization of a thread may become incorrect in subsequent calls because all threads are stopped at the end of a database call.

As a specific example, the standard RMI Server functions in the shared server mode. However, it is useful only within the context of a single call. This is because the RMI Server forks daemon threads, which are in the shared server mode, are stopped at the end of call, that is, the daemon thread are stopped when all non-daemon threads return. If the RMI server session is reentered in a subsequent call, then these daemon threads are not restarted and the RMI server fails to function properly.
