Package XSLT implements types and methods related to XSL processing.

The following table summarizes the methods available through the `XSLT` package for XML C APIs.

Table 15-1 Summary of XSLT Methods for XML C Implementation

| Function                  | Summary                                         |
|:--------------------------|:------------------------------------------------|
| XmlXslCreate()            | Create an XSL context.                          |
| XmlXslDestroy()           | Destroy an XSL context.                         |
| XmlXslGetBaseURI()        | Get the XSL processor base URI.                 |
| XmlXslGetOutput()         | Get the XSL result fragment.                    |
| XmlXslGetStylesheetDom()  | Get the XSL stylesheet document.                |
| XmlXslGetTextParam()      | Get the XSL text parameter value.               |
| XmlXslProcess()           | Perform XSL processing on an instance document. |
| XmlXslResetAllParams()    | Reset XSL processor parameters.                 |
| XmlXslSetOutputDom()      | Set the XSL context output DOM.                 |
| XmlXslSetOutputEncoding() | Set the XSL context output encoding.            |
| XmlXslSetOutputMethod()   | Set the XSL context output method.              |
| XmlXslSetOutputSax()      | Set the XSL context output SAX.                 |
| XmlXslSetOutputStream()   | Set the XSL context output stream.              |
| XmlXslSetTextParam()      | Set the XSL context output text parameter.      |

### XmlXslCreate()

Create an XSLT context

#### Syntax

    xslctx *XmlXslCreate(
       xmlctx *ctx,
       xmldocnode *xsl,
       oratext *baseuri,
       xmlerr *err);

| Parameter | In/Out   | Description                                    |
|:----------|:---------|:-----------------------------------------------|
| `ctx`     | `IN`     | XSL context object                             |
| `xsl`     | `IN`     | XSL stylesheet document object                 |
| `baseuri` | `IN`     | base URI for including and importing documents |
| `err`     | `IN/OUT` | returned error code                            |

#### Returns

`(xslctx *)` XSLT context

**See Also:**

XmlXslDestroy()

### XmlXslDestroy()

Destroy an XSL context

#### Syntax

    xmlerr XmlXslDestroy(
       xslctx *ctx);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `ctx`     | `IN`   | XSL context |

#### Returns

`(xmlerr)` error code

**See Also:**

XmlXslCreate()

### XmlXslGetBaseURI()

Get the XSL processor base URI

#### Syntax

    oratext *XmlXslGetBaseURI(
       xslctx *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | XSL context object |

#### Returns

`(oratext *)` base URI

### XmlXslGetOutput()

Get the XSL result fragment

#### Syntax

    xmlfragnode *XmlXslGetOutput(
       xslctx *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | XSL context object |

#### Returns

`(xmlfragnode *)` result fragment

### XmlXslGetStylesheetDom()

Get the XSL stylesheet document

#### Syntax

    xmldocnode *XmlXslGetStylesheetDom(
       xslctx *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | XSL context object |

#### Returns

`(xmldocnode *)` stylesheet document

### XmlXslGetTextParam()

Get the XSL text parameter value

#### Syntax

    oratext *XmlXslGetTextParam(
       xslctx *ctx,
       oratext *name);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `ctx`     | `IN`   | XML context object                    |
| `name`    | `IN`   | name of the top-level parameter value |

#### Returns

`(oratext *)` parameter value

**See Also:**

XmlXslSetTextParam()

### XmlXslProcess()

Do XSL processing on an instance document

#### Syntax

    xmlerr XmlXslProcess(
       xslctx *ctx,
       xmldocnode *xml,
       boolean normalize);

| Parameter   | In/Out | Description                                                  |
|:------------|:-------|:-------------------------------------------------------------|
| `ctx`       | `IN`   | XSL context object                                           |
| `xml`       | `IN`   | instance document to process                                 |
| `normalize` | `IN`   | if `TRUE`, force the XSL processor to normalize the document |

#### Returns

`(xmlerr)` error code

### XmlXslResetAllParams()

Reset all the top level parameters added

#### Syntax

    xmlerr XmlXslResetAllParams(
       xslctx *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | XSL context object |

#### Returns

`(xmlerr)` error code, XMLERR_SUCC \[0\] on success.

**See Also:**

XmlXslSetTextParam()

### XmlXslSetOutputDom()

Set the xslctx output DOM

### XmlXslSetOutputEncoding()

Set the xslctx output encoding

#### Syntax

    xmlerr XmlXslSetOutputEncoding(
       xslctx *ctx,
       oratext* encoding);

| Parameter  | In/Out | Description        |
|:-----------|:-------|:-------------------|
| `ctx`      | `IN`   | XML context object |
| `encoding` | `IN`   | output encoding    |

#### Returns

`(xmlerr)` error code, `XMLERR_SUCC [0]` on success.

### XmlXslSetOutputMethod()

Set the xslctx output method

#### Syntax

    xmlerr XmlXslSetOutputMethod(
       xslctx *ctx,
       xmlxslomethod method);

| Parameter  | In/Out | Description        |
|:-----------|:-------|:-------------------|
| `ctx`      | `IN`   | XML context object |
| `encoding` | `IN`   | XSL output method  |

#### Returns

`(xmlerr)` error code, `XMLERR_SUCC [0]` on success.

### XmlXslSetOutputSax()

Set the xslctx output SAX

#### Syntax

    xmlerr XmlXslSetOutputSax(
       xslctx *ctx,
       xmlsaxcb* saxcb,
       void *saxctx);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `ctx`     | `IN`   | XSL context object   |
| `saxcb`   | `IN`   | SAX callback object  |
| `saxctx`  | `IN`   | SAX callback context |

#### Returns

`(xmlerr)` error code, `XMLERR_SUCC [0]` on success.

### XmlXslSetOutputStream()

#### Syntax

    xmlerr XmlXslSetOutputStream(
       xslctx *ctx,
       xmlostream *stream);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `ctx`     | `IN`   | XSL context object   |
| `stream`  | `IN`   | output stream object |

#### Returns

`(xmlxsl)` error code, `XMLXSL_SUCC [0]` on success.

### XmlXslSetTextParam()

Set the `xslctx` output text parameter.

#### Syntax

    xmlerr XmlXslSetTextParam(
       xslctx *ctx,
       oratext *name,
       oratext *value);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `ctx`     | `IN`   | XSL context object           |
| `name`    | `IN`   | name of top level parameter  |
| `value`   | `IN`   | value of top level parameter |

#### Returns

`(xmlerr)` error code, `XMLERR_SUCC [0]` on success.

**See Also:**

XmlXslGetTextParam()
