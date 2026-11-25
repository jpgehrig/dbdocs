XPath methods process XPath related types and interfaces.

The following table summarizes the methods available through the `XPath` package for XML C APIs.

Table 13-1 Summary of XPath Methods for XML C Implementation

| Function                    | Summary                                           |
|:----------------------------|:--------------------------------------------------|
| XmlXPathCreateCtx()         | Create an XPath context.                          |
| XmlXPathDestroyCtx()        | Destroy an XPath context.                         |
| XmlXPathEval()              | Evaluate XPath expression.                        |
| XmlXPathGetObjectBoolean()  | Get boolean value of XPath object.                |
| XmlXPathGetObjectFragment() | Get fragment value of XPath object.               |
| XmlXPathGetObjectNSetNode() | Get node from nodeset type XPath object.          |
| XmlXPathGetObjectNSetNum()  | Get number of nodes in nodeset type XPath object. |
| XmlXPathGetObjectNumber()   | Get number from XPath object.                     |
| XmlXPathGetObjectString()   | Get string from XPath object.                     |
| XmlXPathGetObjectType()     | Get XPath object type.                            |
| XmlXPathParse()             | Parse XPath expression.                           |

### XmlXPathCreateCtx()

Create an `XPath` context

#### Syntax

    xpctx* XmlXPathCreateCtx(
       xmlctx *xsl,
       oratext *baseuri,
       xmlnode *ctxnode,
       ub4 ctxpos,
       ub4 ctxsize);

| Parameter | In/Out | Description                       |
|:----------|:-------|:----------------------------------|
| `xsl`     | `IN`   | XSL stylesheet as `xmldoc` object |
| `baseuri` | `IN`   | base URI used by document, if any |
| `ctxnode` | `IN`   | current context position          |
| `ctxpos`  | `IN`   | current context size              |
| `ctxsize` | `IN`   | current context node              |

#### Returns

`(xpctx *)` XPath context or `NULL` on error

### XmlXPathDestroyCtx()

Destroy an XPath context.

#### Syntax

    void XmlXPathDestroyCtx(
       xpctx *xslxpctx);

| Parameter  | In/Out | Description          |
|:-----------|:-------|:---------------------|
| `xslxpctx` | `IN`   | XPath context object |

### XmlXPathEval()

Evaluate `XPath` expression.

#### Syntax

    xpobj *XmlXPathEval(
       xpctx *xctx,
       xpexpr *exprtree,
       xmlerr *err);

| Parameter  | In/Out | Description                    |
|:-----------|:-------|:-------------------------------|
| `xctx`     | `IN`   | `XPath` context                |
| `exprtree` | `IN`   | parsed `XPath` expression tree |
| `err`      | `OUT`  | error code                     |

#### Returns

`(xpobj *)` result XPath object or `NULL` on error

### XmlXPathGetObjectBoolean()

Get boolean value of `XPath` object

#### Syntax

    boolean XmlXPathGetObjectBoolean(
       xpobj *obj);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `obj`     | `IN`   | XPath object |

#### Returns

`(boolean)` truth value

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNum(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectFragment()

Get boolean value of `XPath` object

#### Syntax

    xmlnode* XmlXPathGetObjectFragment(
       xpobj *obj);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `obj`     | `IN`   | `XPath` object |

#### Returns

`(boolean)` truth value

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNum(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectNSetNode()

Get node from nodeset-type XPath object

#### Syntax

    xmlnode *XmlXPathGetObjectNSetNode(
       xpobj *obj,
       ub4 i);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `obj`     | `IN`   | `XPath` object        |
| `i`       | `IN`   | node index in nodeset |

#### Returns

`(xmlnode *)` The object type or values.

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNum(), XmlXPathGetObjectString(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectNSetNum()

Get number of nodes in nodeset-type `XPath` object

#### Syntax

    ub4 XmlXPathGetObjectNSetNum(
       xpobj *obj);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `obj`     | `IN`   | `XPath` object |

#### Returns

`(ub4)` number of nodes in nodeset

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectString(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectNumber()

Get number from XPath object

#### Syntax

    double XmlXPathGetObjectNumber(
       xpobj *obj);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `obj`     | `IN`   | `XPath` object |

#### Returns

`(double)` number

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNum(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectString(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectString()

Get string from `XPath` object

#### Syntax

    oratext *XmlXPathGetObjectString(
       xpobj *obj);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `obj`     | `IN`   | XPath object |

#### Returns

`(oratext *)` string

**See Also:**

XmlXPathGetObjectType(), XmlXPathGetObjectNSetNum(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathGetObjectType()

Get `XPath` object type

#### Syntax

    xmlxslobjtype XmlXPathGetObjectType(
       xpobj *obj);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `obj`     | `IN`   | XPath object |

#### Returns

`(xmlxslobjtype)` type-code for object

**See Also:**

XmlXPathGetObjectNSetNum(), XmlXPathGetObjectNSetNode(), XmlXPathGetObjectString(), XmlXPathGetObjectNumber(), XmlXPathGetObjectBoolean()

### XmlXPathParse()

Parse `XPath` expression.

#### Syntax

    xpexpr* XmlXPathParse(
       xpctx *xctx,
       oratext *expr,
       xmlerr * err);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `xctx`    | `IN`   | XPath context object |
| `expr`    | `IN`   | XPath expression     |
| `err`     | `OUT`  | error code           |

#### Returns

`(xpexpr *)` `XPath` expression parse tree or `NULL` on error
