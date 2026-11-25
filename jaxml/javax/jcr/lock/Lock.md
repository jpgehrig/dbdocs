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

- **Prev Class**
- **[Next Class](LockException.md)**

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

**javax.jcr.lock**

## **Interface Lock**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Lock

  **Represents a lock placed on an item.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                           |
    |----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`   | `getLockOwner``()`<br>Returns the user ID of the user who owns this lock.                                                                        |
    | `java.lang.String`   | `getLockToken``()`<br>May return the lock token for this lock.                                                                                   |
    | [`Node`](../Node.md) | `getNode``()`<br>Returns the lock holding node.                                                                                                  |
    | `boolean`            | `isDeep``()`<br>Returns `true` if this is a deep lock; `false` otherwise.                                                                        |
    | `boolean`            | `isLive``()`<br>Returns true if this `Lock` object represents a lock that is currently in effect.                                                |
    | `boolean`            | `isSessionScoped``()`<br>Returns `true` if this is a session-scoped lock.                                                                        |
    | `void`               | `refresh``()`<br>If this lock's time-to-live is governed by a timer, this method resets that timer so that the lock does not timeout and expire. |

<!-- -->

- - ### Method Detail

    - #### getLockOwner

          java.lang.String getLockOwner()

      Returns the user ID of the user who owns this lock. This is the value of the `jcr:lockOwner` property of the lock-holding node. It is also the value returned by `Session.getUserID` at the time that the lock was placed. The lock owner's identity is only provided for informational purposes. It does not govern who can perform an unlock or make changes to the locked nodes; that depends entirely upon who the token holder is.
      Returns:
      a user ID.

    <!-- -->

    - #### isDeep

          boolean isDeep()

      Returns `true` if this is a deep lock; `false` otherwise.
      Returns:
      a boolean

    <!-- -->

    - #### getNode

          Node getNode()

      Returns the lock holding node. Note that `N.getLock().getNode()` (where `N` is a locked node) will only return `N` if `N` is the lock holder. If `N` is in the subtree of the lock holder, `H`, then this call will return `H`.
      Returns:
      an `Node`.

    <!-- -->

    - #### getLockToken

          java.lang.String getLockToken()

      May return the lock token for this lock.
      If this `Session` holds the lock token for this lock, then this method will return that lock token. If this `Session` does not hold the applicable lock token then this method will return null.

      Returns:
      a `String`.

    <!-- -->

    - #### isLive

          boolean isLive()
                  throws RepositoryException

      Returns true if this `Lock` object represents a lock that is currently in effect. If this lock has been unlocked either explicitly or due to an implementation-specific limitation (like a timeout) then it returns `false`. Note that this method is intended for those cases where one is holding a `Lock` Java object and wants to find out whether the lock (the JCR-level entity that is attached to the lockable node) that this object originally represented still exists. For example, a timeout or explicit `unlock` will remove a lock from a node but the `Lock` Java object corresponding to that lock may still exist, and in that case its `isLive` method will return `false`.
      Returns:
      a `boolean`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### isSessionScoped

          boolean isSessionScoped()

      Returns `true` if this is a session-scoped lock. Returns `false` if this is an open-scoped lock.
      Returns:
      a `boolean`.

    <!-- -->

    - #### refresh

          void refresh()
                throws LockException,
                       RepositoryException

      If this lock's time-to-live is governed by a timer, this method resets that timer so that the lock does not timeout and expire. If this lock's time-to-live is not governed by a timer, then this method has no effect.
      A LockException is thrown if this `Session` does not hold the correct lock token for this lock.

      Throws:
      [`LockException`](LockException.md) - if this `Session` does not hold the correct lock token for this lock.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

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

- **Prev Class**
- **[Next Class](LockException.md)**

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
