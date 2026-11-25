The following table summarizes the methods available through the `Range` interface for XML C APIs.

Table 6-1 Summary of Range Methods for XML C Implementation

| Function                           | Summary                                                     |
|:-----------------------------------|:------------------------------------------------------------|
| XmlDomCreateRange()                | Create `Range` object.                                      |
| XmlDomRangeClone()                 | Clone a range.                                              |
| XmlDomRangeCloneContents()         | Clone contents selected by a range.                         |
| XmlDomRangeCollapse()              | Collapse range to either start point or end point.          |
| XmlDomRangeCompareBoundaryPoints() | Compare boundary points of two ranges.                      |
| XmlDomRangeDeleteContents()        | Delete content selected by a range.                         |
| XmlDomRangeDetach()                | Detach a range.                                             |
| XmlDomRangeExtractContents()       | Extract contents selected by a range.                       |
| XmlDomRangeGetCollapsed()          | Return whether the range is collapsed.                      |
| XmlDomRangeGetCommonAncestor()     | Return deepest common ancestor node of two boundary points. |
| XmlDomRangeGetDetached()           | Return whether the range is detached.                       |
| XmlDomRangeGetEndContainer()       | Return range end container node.                            |
| XmlDomRangeGetEndOffset()          | Return range end offset.                                    |
| XmlDomRangeGetStartContainer()     | Return range start container node.                          |
| XmlDomRangeGetStartOffset()        | Return range start offset.                                  |
| XmlDomRangeIsConsistent()          | Return whether the range is consistent.                     |
| XmlDomRangeSelectNode()            | Select a node as a range.                                   |
| XmlDomRangeSelectNodeContents()    | Define range to select node contents.                       |
| XmlDomRangeSetEnd()                | Set the end point.                                          |
| XmlDomRangeSetEndBefore()          | Set the end point before a node.                            |
| XmlDomRangeSetStart()              | Set the start point.                                        |
| XmlDomRangeSetStartAfter()         | Set the start point after a node.                           |
| XmlDomRangeSetStartBefore()        | Set the start point before a node.                          |

### XmlDomCreateRange()

The only one method of `DocumentRange` interface, used to create a `Range` object.

#### Syntax

    xmlrange* XmlDomCreateRange(
       xmlctx *xctx,
       xmlrange *range,
       xmldocnode *doc);

| Parameter | In/Out | Description                                      |
|:----------|:-------|:-------------------------------------------------|
| `xctx`    | `IN`   | XML context                                      |
| `range`   | `IN`   | existing NodeIterator, or `NULL` to allocate new |
| `doc`     | `IN`   | document to which the new `Range` is attached    |

#### Returns

`(xmlrange *)` original or new `Range` object.

### XmlDomRangeClone()

Clone a `Range`. Clones the range without affecting the content selected by the original range. Returns `NULL` if an error.

#### Syntax

    xmlrange* XmlDomRangeClone(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlrange *)` new range that clones the old one

### XmlDomRangeCloneContents()

Clone contents selected by a range. Clones but does not delete contents selected by a range. Performs the range consistency check and sets `retval` to an error code if an error.

#### Syntax

    xmlnode* XmlDomRangeCloneContents(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlnode *)` cloned contents

### XmlDomRangeCollapse()

Collapses the range to either start point or end point. The point where it is collapsed to is assumed to be a valid point in the document which this range is attached to.

#### Syntax

    xmlerr XmlDomRangeCollapse(
       xmlctx *xctx,
       xmlrange *range,
       boolean tostart);

| Parameter | In/Out | Description                                                         |
|:----------|:-------|:--------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                         |
| `range`   | `IN`   | range object                                                        |
| `tostart` | `IN`   | indicates whether to collapse to start (`TRUE`) or to end (`FALSE`) |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeCompareBoundaryPoints()

Compares two boundary points of two different ranges. Returns `-1,0,1` depending on whether the corresponding boundary point of the range (range) is before, equal, or after the corresponding boundary point of the second range (`srange`). It returns `~(int)0` if two ranges are attached to two different documents or if one of them is detached.

#### Syntax

    sb4 XmlDomRangeCompareBoundaryPoints(
       xmlctx *xctx,
       xmlrange *range,
       xmlcmphow how,
       xmlrange *srange,
       xmlerr *xerr);

| Parameter | In/Out | Description                        |
|:----------|:-------|:-----------------------------------|
| `xctx`    | `IN`   | XML context                        |
| `range`   | `IN`   | range object                       |
| `how`     | `IN`   | `xmlcmphow` value; how to compare  |
| `srange`  | `IN`   | range object with which to compare |
| `xerr`    | `OUT`  | numeric return code                |

#### Returns

`(sb4)` `strcmp`-like comparison result

### XmlDomRangeDeleteContents()

Deletes content selected by a range. Performs the range consistency check and sets `retval` to an error code if an error.

#### Syntax

    xmlerr XmlDomRangeDeleteContents(
       xmlctx *xctx,
       xmlrange *range);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeDetach()

Detaches the range from the document and places it (range) in invalid state.

#### Syntax

    xmlerr XmlDomRangeDetach(
       xmlctx *xctx,
       xmlrange *range);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeExtractContents()

Extract contents selected by a range. Clones and deletes contents selected by a range. Performs the range consistency check and sets `retval` to an error code if an error.

#### Syntax

    xmlnode* XmlDomRangeExtractContents(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlnode *)` extracted

### XmlDomRangeGetCollapsed()

Returns `TRUE` if the range is collapsed and is not detached, otherwise returns `FALSE`.

#### Syntax

    boolean XmlDomRangeGetCollapsed(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(boolean)` `TRUE` if the range is collapsed, `FALSE` otherwise

### XmlDomRangeGetCommonAncestor()

Returns deepest common ancestor node of two boundary points of the range if the range is not detached, otherwise returns `NULL`. It is assumed that the range is in a consistent state.

#### Syntax

    xmlnode* XmlDomRangeGetCommonAncestor(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlnode *)` deepest common ancestor node \[or `NULL`\]

### XmlDomRangeGetDetached()

Return whether the range is detached. Returns `TRUE` if the range is detached and is not `NULL`. Otherwise returns `FALSE`.

#### Syntax

    ub1 XmlDomRangeGetDetached(
       xmlctx *xctx,
       xmlrange *range);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |

#### Returns

`(ub1)` `TRUE` if the range is detached, `FALSE` otherwise

### XmlDomRangeGetEndContainer()

Returns range end container node if the range is not detached, otherwise returns `NULL`.

#### Syntax

    xmlnode* XmlDomRangeGetEndContainer(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlnode *)` range end container node \[or `NULL`\]

### XmlDomRangeGetEndOffset()

Returns range end offset if the range is not detached, otherwise returns `~(ub4)0` \[the maximum `ub4` value\].

#### Syntax

    ub4 XmlDomRangeGetEndOffset(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(ub4)` range end offset \[or `ub4` maximum\]

### XmlDomRangeGetStartContainer()

Returns range start container node if the range is valid and is not detached, otherwise returns `NULL`.

#### Syntax

    xmlnode* XmlDomRangeGetStartContainer(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(xmlnode *)` range start container node

### XmlDomRangeGetStartOffset()

Returns range start offset if the range is not detached, otherwise returns `~(ub4)0` \[the maximum `ub4` value\].

#### Syntax

    ub4 XmlDomRangeGetStartOffset(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(ub4)` range start offset \[or `ub4` maximum\]

### XmlDomRangeIsConsistent()

Return whether the range is consistent. Returns `TRUE` if the range is consistent: both points are under the same root and the start point is before or equal to the end point. Otherwise returns `FALSE`.

#### Syntax

    boolean XmlDomRangeIsConsistent(
       xmlctx *xctx,
       xmlrange *range,
       xmlerr *xerr);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `range`   | `IN`   | range object        |
| `xerr`    | `OUT`  | numeric return code |

#### Returns

`(ub1)` `TRUE` if the range is consistent, `FALSE` otherwise

### XmlDomRangeSelectNode()

Sets the range end point and start point so that the parent node of this node becomes the container node, and the offset is the offset of this node among the children of its parent. The range becomes collapsed. It is assumed that the node is a valid node of its document. If the range is detached, it is ignored, and the range becomes attached.

#### Syntax

    xmlerr XmlDomRangeSelectNode(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |
| `node`    | `IN`   | XML node     |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSelectNodeContents()

Sets the range start point to the start of the node contents and the end point to the end of the node contents. It is assumed that the node is a valid document node. If the range is detached, it is ignored, and the range becomes attached.

#### Syntax

    xmlerr XmlDomRangeSelectNodeContents(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |
| `node`    | `IN`   | XML node     |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSetEnd()

Sets the range end point. If it has a root container other than the current one for the range, the range is collapsed to the new position. If the end is set to be at a position before the start, the range is collapsed to that position. Returns `xmlerr` value. according to the description where this type is defined. It is assumed that the start point of the range is a valid start point.

#### Syntax

    xmlerr XmlDomRangeSetEnd(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node,
       ub4 offset);

| Parameter | In/Out | Description   |
|:----------|:-------|:--------------|
| `xctx`    | `IN`   | XML context   |
| `range`   | `IN`   | range object  |
| `node`    | `IN`   | XML node      |
| `offset`  | `IN`   | ending offset |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSetEndBefore()

Sets the range end point before a node. If it has a root container other than the current one for the range, the range is collapsed to the new position. If the before node sets the end to be at a position before the start, the range is collapsed to new position. Returns xmlerr value according to the description where this type is defined. It is assumed that the start point of the range is a valid start point.

#### Syntax

    xmlerr XmlDomRangeSetEndBefore(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |
| `node`    | `IN`   | XML node     |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSetStart()

Sets the range start point. If it has a root container other than the current one for the range, the range is collapsed to the new position. If the start is set to be at a position after the end, the range is collapsed to that position. Returns xmlerr value according to the description where this type is defined. It is assumed that the end point of the range is a valid end point.

#### Syntax

    xmlerr XmlDomRangeSetStart(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node,
       ub4 offset);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `xctx`    | `IN`   | XML context     |
| `range`   | `IN`   | range object    |
| `node`    | `IN`   | XML node        |
| `offset`  | `IN`   | starting offset |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSetStartAfter()

Sets the range start point after a node. If it has a root container other than the current one, the range is collapsed to the new position. If the previous node sets the start after the end, the range is collapsed to a new position. It is assumed that the end point of the range is a valid end point.

#### Syntax

    xmlerr XmlDomRangeSetStartAfter(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |
| `node`    | `IN`   | XML node     |

#### Returns

`(xmlerr)` numeric return code

### XmlDomRangeSetStartBefore()

Sets the range start point before a node. If it has a root container other than the current one, the range is collapsed to the new position with offset `0`. If the previous node sets the start after the end, the range is collapsed to a new position. It is assumed that the end point of the range is a valid end point.

#### Syntax

    xmlerr XmlDomRangeSetStartBefore(
       xmlctx *xctx,
       xmlrange *range,
       xmlnode *node);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `xctx`    | `IN`   | XML context  |
| `range`   | `IN`   | range object |
| `node`    | `IN`   | XML node     |

#### Returns

`(xmlerr)` numeric return code
