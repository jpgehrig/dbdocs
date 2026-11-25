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

- **[Prev Class](EventListenerIterator.md)**
- **Next Class**

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

**javax.jcr.observation**

## **Interface ObservationManager**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ObservationManager

  **The ObservationManager object.**
  **Acquired via [`Workspace.getObservationManager()`](../Workspace.md). Allows for the registration and deregistration of event listeners.**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                                                  |
    |-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                              | `addEventListener``(`[`EventListener`](EventListener.md)` listener, int eventTypes, java.lang.String absPath, boolean isDeep, java.lang.String[] uuid, java.lang.String[] nodeTypeName, boolean noLocal)`<br>Adds an event listener that listens for the specified `eventTypes` (a combination of one or more event types encoded as a bit mask value). |
    | [`EventListenerIterator`](EventListenerIterator.md) | `getRegisteredEventListeners``()`<br>Returns all event listeners that have been registered through this session.                                                                                                                                                                                                                                        |
    | `void`                                              | `removeEventListener``(`[`EventListener`](EventListener.md)` listener)`<br>Deregisters an event listener.                                                                                                                                                                                                                                               |

<!-- -->

- - ### Method Detail

    - #### addEventListener

          void addEventListener(EventListener listener,
                                int eventTypes,
                                java.lang.String absPath,
                                boolean isDeep,
                                java.lang.String[] uuid,
                                java.lang.String[] nodeTypeName,
                                boolean noLocal)
                         throws RepositoryException

      Adds an event listener that listens for the specified `eventTypes` (a combination of one or more event types encoded as a bit mask value).
      The set of events can be filtered by specifying restrictions based on characteristics of the node associated with the event. In the case of event types `NODE_ADDED` and `NODE_REMOVED`, the node associated with an event is the node at (or formerly at) the path returned by `Event.getPath`. In the case of event types `PROPERTY_ADDED`, `PROPERTY_REMOVED` and `PROPERTY_CHANGED`, the node associated with an event is the parent node of the property at (or formerly at) the path returned by `Event.getPath`:

      - `absPath`, `isDeep`: Only events whose associated node is at `absPath` (or within its subtree, if `isDeep` is `true`) will be received. It is permissible to register a listener for a path where no node currently exists.
      - `uuid`: Only events whose associated node has one of the UUIDs in this list will be received. If his parameter is `null` then no UUID-related restriction is placed on events received.
      - `nodeTypeName`: Only events whose associated node has one of the node types (or a subtype of one of the node types) in this list will be received. If his parameter is `null` then no node type-related restriction is placed on events received.

      The restrictions are "ANDed" together. In other words, for a particular node to be "listened to" it must meet all the restrictions.
      Additionally, if `noLocal` is `true`, then events generated by the session through which the listener was registered are ignored. Otherwise, they are not ignored.

      The filters of an already-registered `EventListener` can be changed at runtime by re-registering the same `EventListener` object (i.e. the same actual Java object) with a new set of filter arguments. The implementation must ensure that no events are lost during the changeover.

      Parameters:
      `listener` - an [`EventListener`](EventListener.md) object.

      `eventTypes` - A combination of one or more event type constants encoded as a bitmask.

      `absPath` - an absolute path.

      `isDeep` - a `boolean`.

      `uuid` - array of UUIDs.

      `nodeTypeName` - array of node type names.

      `noLocal` - a `boolean`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - If an error occurs.

    <!-- -->

    - #### removeEventListener

          void removeEventListener(EventListener listener)
                            throws RepositoryException

      Deregisters an event listener.
      A listener may be deregistered while it is being executed. The deregistration method will block until the listener has completed executing. An exception to this rule is a listener which deregisters itself from within the `onEvent` method. In this case, the deregistration method returns immediately, but deregistration will effectively be delayed until the listener completes.

      Parameters:
      `listener` - The listener to deregister.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - If an error occurs.

    <!-- -->

    - #### getRegisteredEventListeners

          EventListenerIterator getRegisteredEventListeners()
                                                     throws RepositoryException

      Returns all event listeners that have been registered through this session. If no listeners have been registered, an empty iterator is returned.
      Returns:
      an `EventListenerIterator`.

      Throws:
      [`RepositoryException`](../RepositoryException.md)

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

- **[Prev Class](EventListenerIterator.md)**
- **Next Class**

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

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
