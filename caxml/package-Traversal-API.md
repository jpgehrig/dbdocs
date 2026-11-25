Package Traversal contains APIs that implement the rules and behavior of traversal. For convenience, we grouped the APIs under four general interfaces types:

- DocumentTraversal Interface

- NodeFilter Interface

- NodeIterator Interface

- TreeWalker Interface

### DocumentTraversal Interface for Traversal XML C APIs

The following table summarizes the methods available through the `DocumentTraversal` interface of `Traversal` for XML C APIs.

Table 10-1 Summary of DocumentTraversal Traversal Methods for XML C Implementation

| Function                 | Summary                      |
|:-------------------------|:-----------------------------|
| XmlDomCreateNodeIter()   | Create node iterator object. |
| XmlDomCreateTreeWalker() | Create a tree walker object. |

#### XmlDomCreateNodeIter()

One of two methods of `DocumentTraversal` interface, used to create a `NodeIterator` object. This method is identical to XmlDomCreateTreeWalker() except for the type of object returned.

The `whatToShow` argument is a mask of flag bits, one for each node type. The value `XMLDOM_SHOW_ALL` passes all node types through, otherwise only the types whose bits are set will be passed.

`Entity` reference expansion is controlled by the `entrefExpansion` flag. If `TRUE`, entity references are replaced with their final content; if `FALSE`, entity references are left as nodes.

##### Syntax

    xmliter* XmlDomCreateNodeIter(
       xmlctx *xctx,
       xmliter *iter,
       xmlnode *root,
       xmlshowbits whatToShow,
       XMLDOM_ACCEPT_NODE_F(
          (*nodeFilter),
          xctx,
          node),
       boolean entrefExpand);

| Parameter    | In/Out | Description                                    |
|:-------------|:-------|:-----------------------------------------------|
| `xctx`       | `IN`   | XML context                                    |
| `iter`       | `IN`   | existing NodeIterator to set, `NULL` to create |
| `xerr`       | `IN`   | root node for NodeIterator                     |
| `whatToShow` | `IN`   | mask of `XMLDOM_SHOW_``XXX` flag bits          |
| `nodeFilter` | `IN`   | node filter to be used, `NULL` if none         |
| `xerr`       | `IN`   | whether to expand entity reference nodes       |

##### Returns

`(xmliter *)` original or new `NodeIterator` object

**See Also:**

XmlDomCreateTreeWalker()

#### XmlDomCreateTreeWalker()

One of two methods of DocumentTraversal interface, used to create a `TreeWalker` object. This method is identical to XmlDomCreateNodeIter() except for the type of object returned.

The `whatToShow` argument is a mask of flag bits, one for each node type. The value `XMLDOM_SHOW_ALL` passes all node types through, otherwise only the types whose bits are set will be passed.

`Entity` reference expansion is controlled by the `entrefExpansion` flag. If `TRUE`, entity references are replaced with their final content; if `FALSE`, entity references are left as nodes.

##### Syntax

    xmlwalk* XmlDomCreateTreeWalker(
       xmlctx *xctx,
       xmlwalk* walker,
       xmlnode *root,
       xmlshowbits whatToShow,
       XMLDOM_ACCEPT_NODE_F(
          (*nodeFilter),
          xctx,
          node),
       boolean entrefExpansion);

| Parameter    | In/Out | Description                                    |
|:-------------|:-------|:-----------------------------------------------|
| `xctx`       | `IN`   | XML context                                    |
| `walker`     | `IN`   | existing `TreeWalker` to set, `NULL` to create |
| `xerr`       | `IN`   | root node for `TreeWalker`                     |
| `whatToShow` | `IN`   | mask of `XMLDOM_SHOW_``XXX` flag bits          |
| `nodeFilter` | `IN`   | node filter to be used, `NULL` if none         |
| `xerr`       | `IN`   | whether to expand entity reference nodes       |

##### Returns

`(xmlwalk *)` new `TreeWalker` object

**See Also:**

XmlDomCreateNodeIter()

### NodeFilter Interface for Traversal XML C APIs

The following table summarizes the methods available through the `NodeFilter` interface of `Traversal` for XML C APIs.

Table 10-2 Summary of NodeFilter Traversal Methods for XML C Implementation

| Function               | Summary                                                   |
|:-----------------------|:----------------------------------------------------------|
| XMLDOM_ACCEPT_NODE_F() | Determines the filtering action based on node adn filter. |

#### XMLDOM_ACCEPT_NODE_F()

Sole method of `NodeFilter` interface. Given a node and a filter, determines the filtering action to perform.

This function pointer is passed to the node iterator/tree walker methods, as needed.

Values for xmlerr are:

- `XMLERR_OK` Accept the node. Navigation methods defined for `NodeIterator` or `TreeWalker` will return this node.

- `XMLERR_FILTER_REJECT` Reject the node. Navigation methods defined for `NodeIterator` or `TreeWalker` will not return this node. For `TreeWalker`, the children of this node will also be rejected. `NodeIterator`s treat this as a synonym for `XMLDOM_FILTER_SKIP`

- `XMLERR_FILTER_SKIP` Skip this single node. Navigation methods defined for `NodeIterator` or `TreeWalker` will not return this node. For both `NodeIterator` and `TreeWalker`, the children of this node will still be considered.

##### Syntax

    #define XMLDOM_ACCEPT_NODE_F(func, xctx, node)
    xmlerr func(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `node`    | `IN`   | node to test |

##### Returns

`(xmlerr)` filtering result

### NodeIterator Interface for Traversal XML C APIs

The following table summarizes the methods available through the `NodeIterator` interface of `Traversal` for XML C APIs.

Table 10-3 Summary of NodeIterator Traversal Methods for XML C Implementation

| Function             | Summary                                 |
|:---------------------|:----------------------------------------|
| XmlDomIterDetach()   | Detach a node iterator (deactivate it). |
| XmlDomIterNextNode() | Returns next node for iterator.         |
| XmlDomIterPrevNode() | Returns previous node for iterator.     |

#### XmlDomIterDetach()

Detaches the `NodeIterator` from the set which it iterated over, releasing any resources and placing the iterator in the `INVALID` state. After detach has been invoked, calls to `XmlDomIterNextNode` or `XmlDomIterPrevNode` will raise the exception `XMLERR_ITER_DETACHED`.

##### Syntax

    xmlerr XmlDomIterDetach(
       xmlctx *xctx,
       xmliter *iter);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `xctx`    | `IN`   | XML context          |
| `iter`    | `IN`   | node iterator object |

**See Also:**

XmlDomIterNextNode(), XmlDomIterPrevNode()

#### XmlDomIterNextNode()

Returns the next node in the set and advances the position of the iterator in the set. After a node iterator is created, the first call to `XmlDomIterNextNode` returns the first node in the set. It assumed that the reference node (current iterator position) is never deleted. Otherwise, changes in the underlying DOM tree do not invalidate the iterator.

##### Syntax

    xmlnode* XmlDomIterNextNode(
       xmlctx *xctx,
       xmliter *iter,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `iter`    | `IN`   | node iterator object      |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` next node in set being iterated over \[or `NULL`\]

**See Also:**

XmlDomIterPrevNode(), XmlDomIterDetach()

#### XmlDomIterPrevNode()

Returns the previous node in the set and moves the position of the iterator backward in the set.

##### Syntax

    xmlnode* XmlDomIterPrevNode(
       xmlctx *xctx,
       xmliter *iter,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `iter`    | `IN`   | node iterator object      |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` previous node in set being iterated over \[or `NULL`\]

**See Also:**

XmlDomIterNextNode(), XmlDomIterDetach()

### TreeWalker Interface for Traversal XML C APIs

Table 10-4 summarizes the methods available through the `TreeWalker` interface of `Traversal` for XML C APIs.

Table 10-4 Summary of TreeWalker Traversal Methods for XML C Implementation

| Function                     | Summary                                     |
|:-----------------------------|:--------------------------------------------|
| XmlDomWalkerFirstChild()     | Return first visible child of current node. |
| XmlDomWalkerGetCurrentNode() | Return current node.                        |
| XmlDomWalkerGetRoot()        | Return root node.                           |
| XmlDomWalkerLastChild()      | Return last visible child of current node.  |
| XmlDomWalkerNextNode()       | Return next visible node.                   |
| XmlDomWalkerNextSibling()    | Return next sibling node.                   |
| XmlDomWalkerParentNode()     | Return parent node.                         |
| XmlDomWalkerPrevNode()       | Return previous node.                       |
| XmlDomWalkerPrevSibling()    | Return previous sibling node.               |
| XmlDomWalkerSetCurrentNode() | Set current node.                           |
| XmlDomWalkerSetRoot()        | Set the root node.                          |

#### XmlDomWalkerFirstChild()

Moves the `TreeWalker` to the first visible child of the current node, and returns the new node. If the current node has no visible children, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerFirstChild(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` first visible child \[or `NULL`\]

**See Also:**

XmlDomWalkerLastChild()

#### XmlDomWalkerGetCurrentNode()

Return (get) current node, or `NULL` on error.

##### Syntax

    xmlnode* XmlDomWalkerGetCurrentNode(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` current node

#### XmlDomWalkerGetRoot()

Return (get) root node, or `NULL` on error. Since the current node can be removed from under the root node together with a subtree where it belongs to, the current root node in a walker might have no relation to the current node any more. The `TreeWalker` iterations are based on the current node. However, the root node defines the space of an iteration. This function checks if the root node is still in the root node (ancestor) relation to the current node. If so, it returns this root node. Otherwise, it finds the root of the tree where the current node belongs to, and sets and returns this root as the root node of the walker. It returns `NULL` if the walker is a `NULL` pointer.

##### Syntax

    xmlnode* XmlDomWalkerGetRoot(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | TreeWalker object         |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` root node

#### XmlDomWalkerLastChild()

Moves the `TreeWalker` to the last visible child of the current node, and returns the new node. If the current node has no visible children, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerLastChild(
       xmlctx *xctx,
       xmlwalk *walker,
        xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | TreeWalker object         |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` last visible children \[or `NULL`\]

#### XmlDomWalkerNextNode()

Moves the `TreeWalker` to the next visible node in document order relative to the current node, and returns the new node. If the current node has no next node, or if the search for the next node attempts to step upward from the `TreeWalker`'s root node, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerNextNode(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | TreeWalker object         |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` next node \[or `NULL`\]

**See Also:**

XmlDomWalkerPrevNode(), XmlDomWalkerNextSibling(), XmlDomWalkerPrevSibling()

#### XmlDomWalkerNextSibling()

Moves the `TreeWalker` to the next sibling of the current node, and returns the new node. If the current node has no visible next sibling, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerNextSibling(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` next sibling \[or `NULL`\]

**See Also:**

XmlDomWalkerNextNode(), XmlDomWalkerPrevNode(), XmlDomWalkerPrevSibling()

#### XmlDomWalkerParentNode()

Moves to and returns the closest visible ancestor node of the current node. If the search for the parent node attempts to step upward from the `TreeWalker`'s root node, or if it fails to find a visible ancestor node, this method retains the current position and returns null.

##### Syntax

    xmlnode* XmlDomWalkerParentNode(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | TreeWalker object         |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` parent node \[or `NULL`\]

#### XmlDomWalkerPrevNode()

Moves the `TreeWalker` to the previous visible node in document order relative to the current node, and returns the new node. If the current node has no previous node, or if the search for the previous node attempts to step upward from the `TreeWalker`'s root node, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerPrevNode(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` previous node \[or `NULL`\]

**See Also:**

XmlDomWalkerNextNode(), XmlDomWalkerNextSibling(), XmlDomWalkerPrevSibling()

#### XmlDomWalkerPrevSibling()

Moves the `TreeWalker` to the previous sibling of the current node, and returns the new node. If the current node has no visible previous sibling, returns `NULL`, and retains the current node.

##### Syntax

    xmlnode* XmlDomWalkerPrevSibling(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` previous sibling \[or `NULL`\]

**See Also:**

XmlDomWalkerNextNode(), XmlDomWalkerPrevNode(), XmlDomWalkerNextSibling()

#### XmlDomWalkerSetCurrentNode()

Sets and returns new current node. It also checks if the root node is an ancestor of the new current node. If not it does not set the current node, returns `NULL`, and sets retval to `XMLDOM_WALKER_BAD_NEW_CUR`. Returns `NULL` if an error.

##### Syntax

    xmlnode* XmlDomWalkerSetCurrentNode(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlnode *node,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `node`    | `IN`   | new current node          |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` new current node

#### XmlDomWalkerSetRoot()

Set the root node. Returns new root node if it is an ancestor of the current node. If not it signals an error and checks if the current root node is an ancestor of the current node. If yes it returns it. Otherwise it sets the root node to and returns the root of the tree where the current node belongs to. It returns `NULL` if the walker or the root node parameter is a `NULL` pointer.

##### Syntax

    xmlnode* XmlDomWalkerSetRoot(
       xmlctx *xctx,
       xmlwalk *walker,
       xmlnode *node,
       xmlerr *xerr);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `walker`  | `IN`   | `TreeWalker` object       |
| `node`    | `IN`   | new root node             |
| `xerr`    | `OUT`  | numeric return error code |

##### Returns

`(xmlnode *)` new root node
