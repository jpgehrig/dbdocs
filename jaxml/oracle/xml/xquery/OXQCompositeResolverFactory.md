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

- **[Prev Class](OXQCloseable.md)**
- **[Next Class](OXQConnection.md)**

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

**oracle.xml.xquery**

## **Interface OXQCompositeResolverFactory**

- **All Superinterfaces:**
  **[OXQEntityResolverFactory](OXQEntityResolverFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQCompositeResolverFactory
      extends OXQEntityResolverFactory

  **The factory interface for creating composite entity resolvers.**
  **A composite resolver delegates the entity lookup process to other entity resolvers in the order of their registration. It returns the first non-null result that it receives.**

  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                            |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addResolver``(`[`OXQEntityResolver`](OXQEntityResolver.md)` resolver)`<br>Adds a delegate entity resolver.       |
    | [`OXQEntityResolver`](OXQEntityResolver.md)`[]` | `getResolvers``()`<br>Returns the delegate entity resolvers currently registered with this factory.               |
    | `boolean`                                       | `removeResolver``(`[`OXQEntityResolver`](OXQEntityResolver.md)` resolver)`<br>Removes a delegate entity resolver. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQEntityResolverFactory](OXQEntityResolverFactory.md)

      [`createResolver`](OXQEntityResolverFactory.md)

<!-- -->

- - ### Method Detail

    - #### addResolver

          void addResolver(OXQEntityResolver resolver)

      Adds a delegate entity resolver.
      Parameters:
      `resolver` - the delegate entity resolver. Cannot be `null`

      Throws:
      `java.lang.NullPointerException` - if argument is `null`

    <!-- -->

    - #### removeResolver

          boolean removeResolver(OXQEntityResolver resolver)

      Removes a delegate entity resolver.
      Parameters:
      `resolver` - the entity resolver that must be removed. Cannot be `null`

      Returns:
      `true` if entity resolver was removed, or `false` if the entity resolver didn't exist in the list

      Throws:
      `java.lang.NullPointerException` - if argument is `null`

    <!-- -->

    - #### getResolvers

          OXQEntityResolver[] getResolvers()

      Returns the delegate entity resolvers currently registered with this factory.
      Returns:
      an array containing all delegate entity resolvers, never `null`

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

- **[Prev Class](OXQCloseable.md)**
- **[Next Class](OXQConnection.md)**

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
