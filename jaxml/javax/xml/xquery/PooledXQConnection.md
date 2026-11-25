Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ConnectionPoolXQDataSource.md)**
- **[Next Class](XQCancelledException.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.xquery**

## **Interface PooledXQConnection**

-

  ------------------------------------------------------------------------

  **
  **

      public interface PooledXQConnection

  **An object that provides hooks for connection pool management. A `PooledXQConnection` object represents a physical connection to a data source. The connection can be recycled rather than being closed when an application is finished with it, thus reducing the number of connections that need to be made.**
  **An application programmer does not use the `PooledXQConnection` interface directly; rather, it is used by a middle tier infrastructure that manages the pooling of connections.**

  **When an application calls the method `XQDataSource.getConnection`, it gets back an `XQConnection` object. If connection pooling is being done, that `XQConnection` object is actually a handle to a `PooledXQConnection` object, which is a physical connection.**

  **The connection pool manager, typically the application server, maintains a pool of `PooledXQConnection` objects. If there is a `PooledXQConnection` object available in the pool, the connection pool manager returns an `XQConnection` object that is a handle to that physical connection. If no `PooledXQConnection` object is available, the connection pool manager calls the `ConnectionPoolXQDataSource` method `getPooledConnection` to create a new physical connection and returns a handle to it.**

  **When an application closes a connection, it calls the `XQConnection` method `close`. When connection pooling is being done, the connection pool manager is notified because it has registered itself as an `XQConnectionEventListener` object using the `PooledXQConnection` method `addConnectionEventListener`. The connection pool manager deactivates the handle to the `PooledXQConnection` object and returns the `PooledXQConnection` object to the pool of connections so that it can be used again. Thus, when an application closes its connection, the underlying physical connection is recycled rather than being closed.**

  **The physical connection is not closed until the connection pool manager calls the `PooledXQConnection` method `close`. This method is generally called to have an orderly shutdown of the server or if a fatal error has made the physical connection unusable.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                                    |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                            | `addConnectionEventListener``(`[`XQConnectionEventListener`](XQConnectionEventListener.md)` listener)`<br>Registers the given event listener so that it will be notified when an event occurs on this `PooledXQConnection` object.                        |
    | `void`                            | `close``()`<br>Closes the physical connection that this `PooledXQConnection` object represents.                                                                                                                                                           |
    | [`XQConnection`](XQConnection.md) | `getConnection``()`<br>Creates and returns an `XQConnection` object that is a handle for the physical connection that this `PooledXQConnection` object represents.                                                                                        |
    | `void`                            | `removeConnectionEventListener``(`[`XQConnectionEventListener`](XQConnectionEventListener.md)` listener)`<br>Removes the given event listener from the list of components that will be notified when an event occurs on this `PooledXQConnection` object. |

<!-- -->

- - ### Method Detail

    - #### getConnection

          XQConnection getConnection()
                              throws XQException

      Creates and returns an `XQConnection` object that is a handle for the physical connection that this `PooledXQConnection` object represents. The connection pool manager calls this method when an application has called the `XQDataSource` method `getConnection` and there are no `PooledXQConnection` objects available.
      Returns:
      an `XQConnection` object that is a handle to this `PooledXQConnection` object

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### close

          void close()
              throws XQException

      Closes the physical connection that this `PooledXQConnection` object represents. An application never calls this method directly; it is called by the connection pool manager.
      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### addConnectionEventListener

          void addConnectionEventListener(XQConnectionEventListener listener)

      Registers the given event listener so that it will be notified when an event occurs on this `PooledXQConnection` object.
      Parameters:
      `listener` - a component, usually the connection pool manager, that has implemented the `XQConnectionEventListener` interface and wants to be notified when the connection is closed or has an error

      See Also:
      `removeConnectionEventListener(javax.xml.xquery.XQConnectionEventListener)`

    <!-- -->

    - #### removeConnectionEventListener

          void removeConnectionEventListener(XQConnectionEventListener listener)

      Removes the given event listener from the list of components that will be notified when an event occurs on this `PooledXQConnection` object.
      Parameters:
      `listener` - a component, usually the connection pool manager, that has implemented the `XQConnectionEventListener` interface and been registered with this `PooledXQConnection` object as a listener

      See Also:
      `addConnectionEventListener(javax.xml.xquery.XQConnectionEventListener)`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ConnectionPoolXQDataSource.md)**
- **[Next Class](XQCancelledException.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
