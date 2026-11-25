Here are the mappings between XML C APIs that were available in Oracle Database Oracle9i Release, and the current Unified XML C APIs that became available in subsequent Oracle Database.

**See Also:**

Format Models in [Oracle XML Developer's Kit Programmer's Guide](../adxdk/index.md)

### C Package Changes

Pre-existing C APIs were available through the `oraxml` package. It had the following characteristics:

- Specification is limited to a one-to-one mapping between the xml context (`xmlctx`) and an xml document. Only one document can be accessed by DOM at any one time, however the data of multiple documents can be concurrent.

- The APIs are not always consistent, and don't always follow the declarations of the `xmlctx`.

In contrast, the new unified C APIs solve these problems:

- Multiple independent documents share the `xmlctx`.

- All APIs conform to the declarations of the `xmlctx`.

- Each document can be accessed simultaneously by DOM until explicitly destroyed by an `XmlDestroy()` call.

### Initializing and Parsing Sequence Changes

The initialization and parsing of documents has changed in the Unified C API.

Example A-1 Initializing and Parsing Sequence for the Pre-Unified C API, One Document at a Time

The following pseudo-code demonstrates how to initialize and parse documents, one at a time, using the old C APIs. Contrast this with Example A-2.

    #include <oraxml.h>
    uword err;
    xmlctx *ctx = xmlinit(&err, options);
    for (;;)
    {
       err = xmlparse(ctx, URI, options);
       ...
       /* DOM operations */
       ...
       /* recycle memory from document */
       xmlclean(ctx);
    }
    xmlterm(ctx);

Example A-2 Initializing and Parsing Sequence for the Unified C API, One Document at a Time

The following pseudo-code demonstrates how to initialize and parse documents, one at a time, using the new C APIs. Contrast this with Example A-1.

    #include <xml.h>
    xmlerr err;
    xmldocnode *doc;
    xmlctx *xctx = XmlCreate(&err, options, NULL);
    for (;;)
    {
       doc = XmlLoadDom(xctx, &err, "URI", URI, NULL);
       ...
       /* DOM operations */
       ...
       XmlFreeDocument(xctx, doc);
    }
    XmlDestroy(xctx);

Example A-3 Initializing and Parsing Sequence for the Pre-Unified C API, Multiple Documents and Simultaneous DOM Access

The following pseudo-code demonstrates how to initialize and parse multiple documents with simultaneous DOM access using the old C APIs. Contrast this with Example A-4.

    xmlctx *ctx1 = xmlinitenc(&err, options);
    xmlctx *ctx2 = xmlinitenc(&err, options);
    err = xmlparse(ctx1, URI_1, options);
    err = xmlparse(ctx2, URI_2, options);
    ...
    /* DOM operations for both documents */
    ...
    xmlterm(ctx1);
    xmlterm(ctx2);

Example A-4 Initializing and Parsing Sequence for the Unified C API, Multiple Documents and Simultaneous DOM Access

The following pseudo-code example demonstrates how to initialize and parse multiple documents with simultaneous DOM access using the new C APIs. Contrast this with Example A-3.

    xmldocnode *doc1;
    xmldocnode *doc2;
    xmlctx *xctx = XmlCreate(&err, options, NULL);
    doc1 = XmlLoadDom(xctx, &err, "URI", URI_1, NULL);
    doc2 = XmlLoadDom(xctx, &err, "URI", URI_2, NULL);
    ...
    /* DOM operations for both documents*/
    ...
    XmlFreeDocument(xctx, doc1);
    XmlFreeDocument(xctx, doc2);
    ...
    XmlDestroy(xctx);

### Datatype Mapping between oraxml and xml Packages

Table A-1 outlines the changes made to datatypes for the new C API.

Table A-1 Datatypes Supported by oraxml Package versus xml Package

| oraxml Supported Datatype | xml Supported Datatype                                                     |
|:--------------------------|:---------------------------------------------------------------------------|
| `uword`                   | `xmlerr`                                                                   |
| `xmlacctype`              | `xmlurlacc`                                                                |
| `xmlattrnode`             | `xmlattrnode`                                                              |
| `xmlcdatanode`            | `xmlcdatanode`                                                             |
| `xmlcommentnode`          | `xmlcommentnode`                                                           |
| `xmlctx`                  | `xmlctx`                                                                   |
| `xmldocnode`              | `xmldocnode`                                                               |
| `xmldomimp`               | Obsolete.Use`xmlctx`.                                                      |
| `xmldtdnode`              | `xmldtdnode`                                                               |
| `xmlelemnode`             | `xmlelemnode`                                                              |
| `xmlentnode`              | `xmlentnode`                                                               |
| `xmlentrefnode`           | `xmlentrefnode`                                                            |
| `xmlflags`                | `ub4`                                                                      |
| `xmlfragnode`             | `xmlfragnode`                                                              |
| `xmlihdl`                 | `xmlurlhdl`                                                                |
| `xmlmemcb`                | Use individual function pointers.                                          |
| `xmlnode`                 | `xmlnode`                                                                  |
| `xmlnodes`                | `xmlnodelist, xmlnamedmap`                                                 |
| `xmlnotenode`             | `xmlnotenode`                                                              |
| `xmlntype`                | `xmlnodetype`                                                              |
| `xmlpflags`               | `ub4`                                                                      |
| `xmlpinode`               | `xmlpinode`                                                                |
| `xmlsaxcb`                | `xmlsaxcb`                                                                 |
| `xmlstream`               | `xmlistream, xmliostream`                                                  |
| `xmltextnode`             | `xmltextnode`                                                              |
| `xpctx`                   | `xpctx`                                                                    |
| `xpexpr`                  | `xpexpr`                                                                   |
| `xpnset`                  | Obsolete.Use`XmlXPathGetObjectNSetNum()`and` XmlXPathGetObjectNSetNode()`. |
| `xpnsetele`               | Obsolete.Use`XmlXPathGetObjectNSetNum()`and` XmlXPathGetObjectNSetNode()`. |
| `xpobj`                   | `xpobj`                                                                    |
| `xpobjtyp`                | `xmlxslobjtype`                                                            |
| `xslctx`                  | `xslctx`                                                                   |
| `xsloutputmethod`         | `xmlxsloutputmethod`                                                       |

### Method Mapping between oraxml and xml Packages

Table A-2 outlines the changes made to the methods of the new C API.

Table A-2 Methods of the oraxml Package versus the xml Package

| Package oraxml Method           | Package xml Method(s)                                                    |
|:--------------------------------|:-------------------------------------------------------------------------|
| `appendChild()`                 | `XmlDomAppendChild()`                                                    |
| `appendData()`                  | `XmlDomAppendData()`                                                     |
| `cloneNode()`                   | `XmlDomCloneNode()`                                                      |
| `createAttribute()`             | `XmlDomCreateAttr()`                                                     |
| `createAttributeNS()`           | `XmlDomCreateAttrNS()`                                                   |
| `createCDATASection()`          | `XmlDomCreateCDATA()`                                                    |
| `createComment()`               | `XmlDomCreateComment()`                                                  |
| `createDocument()`              | `XmlCreateDocument()`                                                    |
| `createDocumentFragment()`      | `XmlDomCreateFragment()`                                                 |
| `createDocumentNS()`            | `XmlCreateDocument()`                                                    |
| `createDocumentType()`          | `XmlCreateDTD()`                                                         |
| `createElement()`               | `XmlDomCreateElem()`                                                     |
| `createElementNS()`             | `XmlDomCreateElemNS()`                                                   |
| `createEntityReference()`       | `XmlDomCreateEntityRef()`                                                |
| `createProcessingInstruction()` | `XmlDomCreatePI()`                                                       |
| `createTextNode()`              | `XmlDomCreateText()`                                                     |
| `deleteData()`                  | `XmlDomDeleteData()`                                                     |
| `freeElements()`                | `XmlDomFreeNodeList()`                                                   |
| `getAttribute()`                | `XmlDomGetAttr()`                                                        |
| `getAttributeIndex()`           | `XmlDomGetAttrs(), XmlDomGetNodeMapItem()`                               |
| `getAttributeNode()`            | `XmlDomGetAttrNode()`                                                    |
| `getAttributes()`               | `XmlDomGetAttrs()`                                                       |
| `getAttrLocal()`                | `XmlDomGetAttrLocal(), XmlDomGetAttrLocalLen()`                          |
| `getAttrName()`                 | `XmlDomGetAttrName()`                                                    |
| `getAttrNamespace()`            | `XmlDomGetAttrURI(), XmlDomGetAttrURILen()`                              |
| `getAttrPrefix()`               | `XmlDomGetAttrPrefix()`                                                  |
| `getAttrQualifiedName()`        | `XmlDomGetAttrName()`                                                    |
| `getAttrSpecified()`            | `XmlDomGetAttrSpecified()`                                               |
| `getAttrValue()`                | `XmlDomGetAttrValue()`                                                   |
| `getCharData()`                 | `XmlDomGetCharData()`                                                    |
| `getChildNode()`                | `XmlDomGetChildNode()`                                                   |
| `getChildNodes()`               | `XmlDomGetChildNodes()`                                                  |
| `getContentModel()`             | `XmlDomGetContentModel()`                                                |
| `getDocType()`                  | `XmlDomGetDTD()`                                                         |
| `getDocTypeEntities()`          | `XmlDomGetDTDEntities()`                                                 |
| `getDocTypeName()`              | `XmlDomGetDTDName()`                                                     |
| `getDocTypeNotations()`         | `XmlDomGetDTDNotations()`                                                |
| `getDocument()`                 | Obsolete; document returned by `XmlLoadDom``xxx``()`calls                |
| `getDocumentElement()`          | `XmlDomGetDoctElem()`                                                    |
| `getElementByID()`              | `XmlDomGetElemByID()`                                                    |
| `getElementsByTagName()`        | `XmlDomGetElemsByTag()`                                                  |
| `getElementsByTagNameNS()`      | `XmlDomGetElemsByTag()`                                                  |
| `getEncoding()`                 | `XmlDomGetEncoding()`                                                    |
| `getEntityNotation()`           | `XmlDomGetEntityNotation()`                                              |
| `getEntityPubID()`              | `XmlDomGetEntityPubID()`                                                 |
| `getEntitySysID()`              | `XmlDomGetEntitySysID()`                                                 |
| `getFirstChild()`               | `XmlDomGetFirstChild()`                                                  |
| `getImplementation()`           | Obsolete; use` xmlctx `instead of `DOMImplementation`                    |
| `getLastChild()`                | `XmlDomGetLastChild()`                                                   |
| `getNamedItem()`                | `XmlDomGetNamedItem()`                                                   |
| `getNextSibling()`              | `XmlDomGetNextSibling()`                                                 |
| `getNodeLocal()`                | `XmlDomGetNodeLocal(), XmlDomGetNodeLocalLen()`                          |
| `getNodeMapLength()`            | `XmlDomGetNodeMapLength()`                                               |
| `getNodeName()`                 | `XmlDomGetNodeName(), XmlDomGetNodeNameLen()`                            |
| `getNodeNameSpace()`            | `XmlDomGetNodeURI(), XmlDomGetNodeURILen()`                              |
| `getNodePrefix()`               | `XmlDomGetNodePrefix()`                                                  |
| `getNodeQualifiedName()`        | `XmlDomGetNodedName(), XmlDomGetNodedNameLen()`                          |
| `getNodeType()`                 | `XmlDomGetNodeType()`                                                    |
| `getNodeValue()`                | `XmlDomGetNodeValue(), XmlDomGetNodeValueLen()`                          |
| `getNotationPubID()`            | `XmlDomGetNotationPubID()`                                               |
| `getNotationSysID()`            | `XmlDomGetNotationSysID()`                                               |
| `getOwnerDocument()`            | `XmlDomGetOwnerDocument()`                                               |
| `getParentNode()`               | `XmlDomGetParentNode()`                                                  |
| `getPIData()`                   | `XmlDomGetPIData()`                                                      |
| `getPITarget()`                 | `XmlDomGetPITarget()`                                                    |
| `getPreviousSibling()`          | `XmlDomGetPrevSibling()`                                                 |
| `getTagName()`                  | `XmlDomGetTagName()`                                                     |
| `hasAttributes()`               | `XmlDomHasAttrs()`                                                       |
| `hasChildNodes()`               | `XmlDomHasChildNodes()`                                                  |
| `hasFeature()`                  | `XmlHasFeature()`                                                        |
| `importNode()`                  | `XmlDomImportNode()`                                                     |
| `insertBefore()`                | `XmlDomInsertBefore()`                                                   |
| `insertData()`                  | `XmlDomInsertData()`                                                     |
| `isSingleChar()`                | `XmlIsSimple()`                                                          |
| `isStandalone()`                | `XmlDomGetDecl()`                                                        |
| `isUnicode()`                   | `XmlDomIsUnicode()`                                                      |
| `nodeValid()`                   | `XmlDomValidate()`                                                       |
| `normalize()`                   | `XmlDomNormalize()`                                                      |
| `numAttributes()`               | `XmlDomNumAttrs()`                                                       |
| `numChildNodes()`               | `XmlDomNumChildNodes()`                                                  |
| `prefixToURI()`                 | `XmlDomPrefixToURI()`                                                    |
| `printBuffer()`                 | `XmlSaveDomBuffer()`                                                     |
| `printBufferEnc()`              | `XmlSaveDomBuffer()`                                                     |
| `printCallback()`               | `XmlSaveDomStream()`                                                     |
| `printCallbackEnc()`            | `XmlSaveDomStream()`                                                     |
| `printSize()`                   | `XmlSaveDomSize()`                                                       |
| `printSizeEnc()`                | `XmlSaveDomSize()`                                                       |
| `printStream()`                 | `XmlSaveDomStdio()`                                                      |
| `printStreamEnc()`              | `XmlSaveDomStdio()`                                                      |
| `removeAttribute()`             | `XmlDomRemoveAttr()`                                                     |
| `removeAttributeNode()`         | `XmlDomRemoveAttrNode()`                                                 |
| `removeChild()`                 | `XmlDomRemoveChild()`                                                    |
| `removeNamedItem()`             | `XmlDomRemoveNamedItem()`                                                |
| `replaceChild()`                | `XmlDomReplaceChild()`                                                   |
| `replaceData()`                 | `XmlDomReplaceData()`                                                    |
| `saveString2()`                 | `XmlDomSaveString2()`                                                    |
| `saveString()`                  | `XmlDomSaveString()`                                                     |
| `setAttribute()`                | `XmlDomSetAttr()`                                                        |
| `setAttributeNode()`            | `XmlDomSetAttrNode()`                                                    |
| `setAttrValue()`                | `XmlDomSetAttrValue()`                                                   |
| `setCharData()`                 | `XmlDomSetCharData()`                                                    |
| `setNamedItem()`                | `XmlDomSetNamedItem()`                                                   |
| `setNodeValue()`                | `XmlDomSetNodeValue(), XmlDomSetNodeValueLen()`                          |
| `setPIData()`                   | `XmlDomSetPIData()`                                                      |
| `splitText()`                   | `XmlDomSplitText()`                                                      |
| `substringData()`               | `XmlDomSubstringData()`                                                  |
| `xmlaccess()`                   | `XmlAccess()`                                                            |
| `xmlinit()`                     | `XmlCreate()`                                                            |
| `xmlinitenc()`                  | `XmlCreate()`                                                            |
| `xmlparse()`                    | `XmlLoadDomURI()`                                                        |
| `xmlparsebuf()`                 | `XmlLoadDomBuffer()`                                                     |
| `xmlparsedtd()`                 | Obsolete; use `XML_LOAD_FLAG_DTD_ONLY `flag in `XmlLoad``XXX``()` calls. |
| `xmlparsefile()`                | `XmlLoadDomFile()`                                                       |
| `xmlparsestream()`              | `XmlLoadDomStream()`                                                     |
| `xmlterm()`                     | `XmlDestroy()`                                                           |
| `xpevalxpathexpr()`             | `XmlXPathEval()`                                                         |
| `xpfreexpathctx()`              | `XmlXPathDeleteCtx()`                                                    |
| `xpgetbooleanval()`             | `XmlXPathGetObjectBoolean()`                                             |
| `xpgetfirstnsetelem()`          | `XmlXPathGetObjectNSetNum()`                                             |
| `xpgetnextnsetelem()`           | `XmlXPathGetObjectNSetNum()`                                             |
| `xpgetnsetelemnode()`           | `XmlXPathGetObjectNSetNum()`                                             |
| `xpgetnsetval()`                | `XmlXPathGetObjectNSetNum()`                                             |
| `xpgetnumval()`                 | `XmlXPathGetObjectNumber()`                                              |
| `xpgetrtfragval()`              | `XmlXPathGetObjectFragment()`                                            |
| `xpgetstrval()`                 | `XmlXPathGetObjectString()`                                              |
| `xpgetxpobjtyp()`               | `XmlXPathGetObjectType()`                                                |
| `xpmakexpathctx()`              | `XmlXPathCreateCtx()`                                                    |
| `xpparsexpathexpr()`            | `XmlXPathParse()`                                                        |
| `xslgetbaseuri()`               | `XmlXslGetBaseURI()`                                                     |
| `xslgetoutputdomctx()`          | `XmlXslGetOutputDom()`                                                   |
| `xslgetoutputsax()`             | Unnecessary                                                              |
| `xslgetoutputstream()`          | Unnecessary                                                              |
| `xslgetresultdocfrag()`         | `XmlXslGetOutputFragment()`                                              |
| `xslgettextparam()`             | `XmlXslGetTextParam()`                                                   |
| `xslgetxslctx()`                | Unnecessary                                                              |
| `xslinit()`                     | `XmlXslCreateCtx()`                                                      |
| `xslprocess()`                  | `XmlXslProcess()`                                                        |
| `xslprocessex()`                | `XmlXslProcess()`                                                        |
| `xslprocessxml()`               | `XmlXslProcess()`                                                        |
| `xslprocessxmldocfrag()`        | `XmlXslProcess()`                                                        |
| `xslresetallparams()`           | `XmlXslResetAllParams()`                                                 |
| `xslsetoutputdomctx()`          | `XmlXslSetOutputDom()`                                                   |
| `xslsetoutputencoding()`        | `XmlXslSetOutputEncoding()`                                              |
| `xslsetoutputmethod()`          | `XmlXslSetOutputMethod()`                                                |
| `xslsetoutputsax()`             | `XmlXslSetOutputSax()`                                                   |
| `xslsetoutputsaxctx()`          | `XmlXslSetOutputSax()`                                                   |
| `xslsetoutputstream()`          | `XmlXslSetOutputStream()`                                                |
| `xslsettextparam()`             | `XmlXslSetTextParam()`                                                   |
| `xslterm()`                     | `XmlXslDeleteCtx()`                                                      |
