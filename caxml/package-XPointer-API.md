Package `XPointer` methods implement XML pointers for XML C APIs. They are grouped into three interface types:

- XPointer Interface

- XPtrLoc Interface

- XPtrLocSet Interface

### XPointer Interface for XPointer XML C APIs

The following table summarizes the methods available through the `XPointer` interface of `XPointer` for XML C APIs.

Table 14-1 Summary of XPointer XPointer Methods for XML C Implementation

| Function          | Summary                    |
|:------------------|:---------------------------|
| XmlXPointerEval() | Evaluates XPointer string. |

#### XmlXPointerEval()

Parses and evaluates xpointer string and calculates locations in the document.

##### Syntax

    xmlxptrlocset* XmlXPointerEval(
       xmldocnode* doc,
       oratext* xptrstr);

| Parameter | In/Out | Description                                 |
|:----------|:-------|:--------------------------------------------|
| `doc`     | `IN`   | document node of the corresponding DOM tree |
| `xptrstr` | `IN`   | xpointer string                             |

##### Returns

`(xmlxptrlocset *)` calculated location set

### XPtrLoc Interface for XPointer XML C APIs

The following table summarizes the methods available through the `XPtrLoc` interface of `XPointer` for XML C API.

Table 14-2 Summary of XPtrLoc XPointer Methods for XML C Implementation

| Function             | Summary                           |
|:---------------------|:----------------------------------|
| XmlXPtrLocGetNode()  | Returns Xml node from `XPtrLoc`.  |
| XmlXPtrLocGetPoint() | Returns Xml point from `XPtrLoc`. |
| XmlXPtrLocGetRange() | Returns Xml range from `XPtrLoc`. |
| XmlXPtrLocGetType()  | Returns type of `XPtrLoc`.        |
| XmlXPtrLocToString() | Returns string for a location.    |

#### XmlXPtrLocGetNode()

Returns node from location

##### Syntax

    xmlnode* XmlXPtrLocGetNode(
       xmlxptrloc* loc);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `loc`     | `IN`   | location    |

##### Returns

`(xmlnode *)` `Node` from location

#### XmlXPtrLocGetPoint()

Returns point from location

##### Syntax

    xmlpoint* XmlXPtrLocGetPoint(
       xmlxptrloc* loc);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `loc`     | `IN`   | location    |

##### Returns

`(xmlpoint *)` Point from location

#### XmlXPtrLocGetRange()

Returns range from location.

##### Syntax

    xmlrange* XmlXPtrLocGetRange(
       xmlxptrloc* loc);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `loc`     | `IN`   | location    |

##### Returns

`(xmlrange *)` Range from location

#### XmlXPtrLocGetType()

Returns type of location

##### Syntax

    xmlxptrloctype XmlXPtrLocGetType(
       xmlxptrloc* loc);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `loc`     | `IN`   | location    |

##### Returns

`(xmlxptrloctype)` Type of location

#### XmlXPtrLocToString()

Returns string for a location:

\- node name: name of the container node

\- names of container nodes: "not a location" otherwise

##### Syntax

    oratext* XmlXPtrLocToString(
       xmlxptrloc* loc);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `loc`     | `IN`   | location    |

##### Returns

`(oratext *)` string

### XPtrLocSet Interface for XPointer XML C APIs

The following table summarizes the methods available through the `XPtrLocSet` interface of `XPointer` for XML C APIs.

Table 14-3 Summary of XPtrLocSet XPointer Methods for XML C Implementation

| Function                 | Summary                                              |
|:-------------------------|:-----------------------------------------------------|
| XmlXPtrLocSetFree()      | Free a location set                                  |
| XmlXPtrLocSetGetItem()   | Returns location with `idx` position in `XPtrLocSet` |
| XmlXPtrLocSetGetLength() | Returns length of `XPtrLocSet`.                      |

#### XmlXPtrLocSetFree()

It is user's responsibility to call this function on every location set returned by `XPointer` or `XPtrLocSet` interfaces

##### Syntax

    void XmlXPtrLocSetFree(
       xmlxptrlocset* locset);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `locset`  | `IN`   | location set |

#### XmlXPtrLocSetGetItem()

Returns location with idx position in the location set. First position is `1`.

##### Syntax

    xmlxptrloc* XmlXPtrLocSetGetItem(
       xmlxptrlocset* locset,
       ub4 idx);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `locset`  | `IN`   | location set   |
| `idx`     | `IN`   | location index |

##### Returns

`(xmlxptrloc *)` location with the position `idx`

#### XmlXPtrLocSetGetLength()

Returns the number of locations in the location set

##### Syntax

    ub4 XmlXPtrLocSetGetLength(
       xmlxptrlocset* locset);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `locset`  | `IN`   | location set |

##### Returns

`(ub4)` number of nodes in `locset`
