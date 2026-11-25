Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](ServerSession.md)
- [Next Class](Session.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

javax.jms

## Interface ServerSessionPool

-

  ------------------------------------------------------------------------



      public interface ServerSessionPool

  A `ServerSessionPool` object is an object implemented by an application server to provide a pool of `ServerSession` objects for processing the messages of a `ConnectionConsumer` (optional).
  Its only method is `getServerSession`. The JMS API does not architect how the pool is implemented. It could be a static pool of `ServerSession` objects, or it could use a sophisticated algorithm to dynamically create `ServerSession` objects as needed.

  If the `ServerSessionPool` is out of `ServerSession` objects, the `getServerSession` call may block. If a `ConnectionConsumer` is blocked, it cannot deliver new messages until a `ServerSession` is eventually returned.

  See Also:
  [`ServerSession`](ServerSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                           |
    |-------------------------------------|------------------------------------------------------------------|
    | [`ServerSession`](ServerSession.md) | `getServerSession``()`<br>Return a server session from the pool. |

<!-- -->

- - ### Method Detail

    - #### getServerSession

          ServerSession getServerSession()
                                  throws JMSException

      Return a server session from the pool.
      Returns:
      a server session from the pool

      Throws:
      [`JMSException`](JMSException.md) - if an application server fails to return a `ServerSession` out of its server session pool.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](ServerSession.md)
- [Next Class](Session.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
