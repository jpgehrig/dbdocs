Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventTarget.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.w3c.dom.events**

## **Interface MutationEvent**

- **All Superinterfaces:**
  **[Event](Event.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface MutationEvent
      extends Event

  **The `MutationEvent` interface provides specific contextual information associated with Mutation events.**
  **See also the [Document Object Model (DOM) Level 2 Events Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                               |
    |-------------------|-----------------------------------------------------|
    | `static short`    | `ADDITION`<br>The `Attr` was just added.            |
    | `static short`    | `MODIFICATION`<br>The `Attr` was modified in place. |
    | `static short`    | `REMOVAL`<br>The `Attr` was just removed.           |

    -

      ### **Fields inherited from interface org.w3c.dom.events.[Event](Event.md)**

      **[`AT_TARGET`](Event.md)`, `[`BUBBLING_PHASE`](Event.md)`, `[`CAPTURING_PHASE`](Event.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                                                                                                                                                                                                                    |
    |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`              | `getAttrChange``()`<br>`attrChange` indicates the type of change which triggered the DOMAttrModified event.                                                                                                                                                                                                                                                                               |
    | `java.lang.String`   | `getAttrName``()`<br>`attrName` indicates the name of the changed `Attr` node in a DOMAttrModified event.                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`   | `getNewValue``()`<br>`newValue` indicates the new value of the `Attr` node in DOMAttrModified events, and of the `CharacterData` node in DOMCharDataModified events.                                                                                                                                                                                                                      |
    | `java.lang.String`   | `getPrevValue``()`<br>`prevValue` indicates the previous value of the `Attr` node in DOMAttrModified events, and of the `CharacterData` node in DOMCharDataModified events.                                                                                                                                                                                                               |
    | [`Node`](../Node.md) | `getRelatedNode``()`<br>`relatedNode` is used to identify a secondary node related to a mutation event.                                                                                                                                                                                                                                                                                   |
    | `void`               | `initMutationEvent``(java.lang.String typeArg, boolean canBubbleArg, boolean cancelableArg, `[`Node`](../Node.md)` relatedNodeArg, java.lang.String prevValueArg, java.lang.String newValueArg, java.lang.String attrNameArg, short attrChangeArg)`<br>The `initMutationEvent` method is used to initialize the value of a `MutationEvent` created through the `DocumentEvent` interface. |

    - ### Methods inherited from interface org.w3c.dom.events.[Event](Event.md)

      [`getBubbles`](Event.md)`, `[`getCancelable`](Event.md)`, `[`getCurrentTarget`](Event.md)`, `[`getEventPhase`](Event.md)`, `[`getTarget`](Event.md)`, `[`getTimeStamp`](Event.md)`, `[`getType`](Event.md)`, `[`initEvent`](Event.md)`, `[`preventDefault`](Event.md)`, `[`stopPropagation`](Event.md)

<!-- -->

- - ### Field Detail

    - #### MODIFICATION

          static final short MODIFICATION

      The `Attr` was modified in place.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ADDITION

          static final short ADDITION

      The `Attr` was just added.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REMOVAL

          static final short REMOVAL

      The `Attr` was just removed.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getRelatedNode

          Node getRelatedNode()

      `relatedNode` is used to identify a secondary node related to a mutation event. For example, if a mutation event is dispatched to a node indicating that its parent has changed, the `relatedNode` is the changed parent. If an event is instead dispatched to a subtree indicating a node was changed within it, the `relatedNode` is the changed node. In the case of the DOMAttrModified event it indicates the `Attr` node which was modified, added, or removed.

    <!-- -->

    - #### getPrevValue

          java.lang.String getPrevValue()

      `prevValue` indicates the previous value of the `Attr` node in DOMAttrModified events, and of the `CharacterData` node in DOMCharDataModified events.

    <!-- -->

    - #### getNewValue

          java.lang.String getNewValue()

      `newValue` indicates the new value of the `Attr` node in DOMAttrModified events, and of the `CharacterData` node in DOMCharDataModified events.

    <!-- -->

    - #### getAttrName

          java.lang.String getAttrName()

      `attrName` indicates the name of the changed `Attr` node in a DOMAttrModified event.

    <!-- -->

    - #### getAttrChange

          short getAttrChange()

      `attrChange` indicates the type of change which triggered the DOMAttrModified event. The values can be `MODIFICATION` , `ADDITION`, or `REMOVAL`.

    <!-- -->

    - #### initMutationEvent

          void initMutationEvent(java.lang.String typeArg,
                                 boolean canBubbleArg,
                                 boolean cancelableArg,
                                 Node relatedNodeArg,
                                 java.lang.String prevValueArg,
                                 java.lang.String newValueArg,
                                 java.lang.String attrNameArg,
                                 short attrChangeArg)

      The `initMutationEvent` method is used to initialize the value of a `MutationEvent` created through the `DocumentEvent` interface. This method may only be called before the `MutationEvent` has been dispatched via the `dispatchEvent` method, though it may be called multiple times during that phase if necessary. If called multiple times, the final invocation takes precedence.
      Parameters:
      `typeArg` - Specifies the event type.

      `canBubbleArg` - Specifies whether or not the event can bubble.

      `cancelableArg` - Specifies whether or not the event's default action can be prevented.

      `relatedNodeArg` - Specifies the `Event`'s related Node.

      `prevValueArg` - Specifies the `Event`'s `prevValue` attribute. This value may be null.

      `newValueArg` - Specifies the `Event`'s `newValue` attribute. This value may be null.

      `attrNameArg` - Specifies the `Event`'s `attrName` attribute. This value may be null.

      `attrChangeArg` - Specifies the `Event`'s `attrChange` attribute

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventTarget.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
