This implementation follows REC-DOM-Level-1-19981001. Because the DOM standard is object-oriented, some changes were made for C language adaptation.

- Reused function names have to be expanded; `getValue` in the `Attr` interface has the unique name `XmlDomGetAttrValue` that matches the pattern established by DOM 2's `getNodeValue`.

- Functions were added to extend the DOM beyond the standard; one example is `XmlDomNumChildNodes`, which returns the number of children of a node.

Note that if the `data_encoding` parameter is set to UTF-16, the APIs process wide-`CHAR` arrays, not `oratext` byte arrays.

### Attr Interface for DOM XML C APIs

The following table summarizes the methods available through the `Attr` interface of DOM for XML C APIs.

Table 3-1 Summary of Attr DOM Methods for XML C Implementation

| Function                   | Summary                                                                  |
|:---------------------------|:-------------------------------------------------------------------------|
| XmlDomGetAttrLocal()       | Returns an attribute's namespace local name as `NULL`-terminated string. |
| XmlDomGetAttrLocalLen()    | Returns an attribute's namespace local name as length-encoded string.    |
| XmlDomGetAttrName()        | Return attribute's name as `NULL`-terminated string.                     |
| XmlDomGetAttrNameLen()     | Return attribute's name as length-encoded string.                        |
| XmlDomGetAttrPrefix()      | Returns an attribute's namespace prefix.                                 |
| XmlDomGetAttrSpecified()   | Return flag that indicates whether an attribute was explicitly created.  |
| XmlDomGetAttrURI()         | Returns an attribute's namespace URI as `NULL`-terminated string.        |
| XmlDomGetAttrURILen()      | Returns an attribute's namespace URI as length-encoded string.           |
| XmlDomGetAttrValue()       | Return attribute's value as `NULL`-terminated string.                    |
| XmlDomGetAttrValueLen()    | Return attribute's value as length-encoded string.                       |
| XmlDomGetAttrValueStream() | Get attribute value stream-style,i.e.chunked.                            |
| XmlDomGetOwnerElem()       | Return an attribute's "owning" element.                                  |
| XmlDomSetAttrValue()       | Set an attribute's value.                                                |
| XmlDomSetAttrValueStream() | Sets an attribute value stream style (chunked).                          |

#### XmlDomGetAttrLocal()

Returns an attribute's namespace local name (in the data encoding). If the attribute's name is not fully qualified (has no prefix), then the local name is the same as the name.

A length-encoded version is available as `XmlDomGetAttrURILen` which returns the local name as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetAttrLocal(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(oratext *)` attribute's local name \[data encoding\]

**See Also:**

XmlDomGetAttrLocalLen(), XmlDomGetAttrName(), XmlDomGetAttrURI(), XmlDomGetAttrPrefix()

#### XmlDomGetAttrLocalLen()

Returns an attribute's namespace local name (in the data encoding). If the attribute's name is not fully qualified (has no prefix), then the local name is the same as the name.

A `NULL`-terminated version is available as `XmlDomGetAttrLocal` which returns the local name as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the attribute's data will be stored internally as length-encoded. Using the length-based `Get``XXX` functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than `buflen`, then a truncated value will be copied into the buffer and len will return the actual length.

##### Syntax

    oratext* XmlDomGetAttrLocalLen(
       xmlctx *xctx,
       xmlattrnode *attr,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                         |
|:----------|:-------|:------------------------------------|
| `xctx`    | `IN`   | XML context                         |
| `attr`    | `IN`   | attribute node                      |
| `buf`     | `IN`   | input buffer; optional              |
| `buflen`  | `IN`   | input buffer length; optional       |
| `len`     | `OUT`  | length of local name, in characters |

##### Returns

`(oratext *)` `Attr`'s local name \[data encoding\]

**See Also:**

XmlDomGetAttrLocal(), XmlDomGetAttrName(), XmlDomGetAttrURI(), XmlDomGetAttrPrefix()

#### XmlDomGetAttrName()

Returns the fully-qualified name of an attribute (in the data encoding) as a `NULL`-terminated string, for example `bar\0` or `foo:bar\0`.

A length-encoded version is available as `XmlDomGetAttrNameLen` which returns the attribute name as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetAttrName(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(oratext *)` name of attribute \[data encoding\]

**See Also:**

XmlDomGetAttrNameLen(), XmlDomGetAttrURI(), XmlDomGetAttrPrefix(), XmlDomGetAttrLocal()

#### XmlDomGetAttrNameLen()

Returns the fully-qualified name of an attribute (in the data encoding) as a length-encoded string, for example `("bar", 3)` or `("foo:bar", 7)`.

A `NULL`-terminated version is available as `XmlDomGetAttrName` which returns the attribute name as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the attribute's data will be stored internally as length-encoded. Using the length-based `Get``XXX()` functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than `buflen`, then a truncated value will be copied into the buffer and `len` will return the actual length.

##### Syntax

    oratext* XmlDomGetAttrNameLen(
       xmlctx *xctx,
       xmlattrnode *attr,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                         |
|:----------|:-------|:------------------------------------|
| `xctx`    | `IN`   | XML context                         |
| `attr`    | `IN`   | attribute node                      |
| `buf`     | `IN`   | input buffer; optional              |
| `buflen`  | `IN`   | input buffer length; optional       |
| `len`     | `OUT`  | length of local name, in characters |

##### Returns

`(oratext *)` name of attribute \[data encoding\]

**See Also:**

XmlDomGetAttrName(), XmlDomGetAttrURI(), XmlDomGetAttrPrefix(), XmlDomGetAttrLocal()

#### XmlDomGetAttrPrefix()

Returns an attribute's namespace prefix (in the data encoding). If the attribute's name is not fully qualified (has no prefix), `NULL` is returned.

##### Syntax

    oratext* XmlDomGetAttrPrefix(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(oratext *)` attribute's namespace prefix \[data encoding\] or `NULL`

**See Also:**

XmlDomGetAttrName(), XmlDomGetAttrURI(), XmlDomGetAttrLocal()

#### XmlDomGetAttrSpecified()

Return the 'specified' flag for an attribute. If the attribute was explicitly given a value in the original document, this is `TRUE`; otherwise, it is `FALSE`. If the node is not an attribute, returns `FALSE`. If the user sets an attribute's value through DOM, its specified flag will be `TRUE`. To return an attribute to its default value (if it has one), the attribute should be deleted; it will then be re-created automatically with the default value (and specified will be `FALSE`).

##### Syntax

    boolean XmlDomGetAttrSpecified(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(boolean)` attribute's "specified" flag

**See Also:**

XmlDomSetAttrValue()

#### XmlDomGetAttrURI()

Returns an attribute's namespace URI (in the data encoding). If the attribute's name is not qualified (does not contain a namespace prefix), it will have the default namespace in effect when the node was created (which may be `NULL`).

A length-encoded version is available as `XmlDomGetAttrURILen` which returns the URI as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetAttrURI(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(oratext *)` attribute's namespace URI \[data encoding\] or `NULL`

**See Also:**

XmlDomGetAttrURILen(), XmlDomGetAttrPrefix(), XmlDomGetAttrLocal()

#### XmlDomGetAttrURILen()

Returns an attribute's namespace URI (in the data encoding) as length-encoded string. If the attribute's name is not qualified (does not contain a namespace prefix), it will have the default namespace in effect when the node was created (which may be `NULL`).

A `NULL`-terminated version is available as `XmlDomGetAttrURI` which returns the URI as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the attribute's data will be stored internally as length-encoded. Using the length-based Get functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than buflen, then a truncated value will be copied into the buffer and len will return the actual length.

##### Syntax

    oratext* XmlDomGetAttrURILen(
       xmlctx *xctx,
       xmlattrnode *attr,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `xctx`    | `IN`   | XML context                   |
| `attr`    | `IN`   | attribute node                |
| `buf`     | `IN`   | input buffer; optional        |
| `buflen`  | `IN`   | input buffer length; optional |
| `len`     | `OUT`  | length of URI, in characters  |

##### Returns

`(oratext *)` attribute's namespace URI \[data encoding\] or `NULL`

**See Also:**

XmlDomGetAttrURI(), XmlDomGetAttrPrefix(), XmlDomGetAttrLocal()

#### XmlDomGetAttrValue()

Returns the "value" (character data) of an attribute (in the data encoding) as `NULL`-terminated string. Character and general entities will have been replaced.

A length-encoded version is available as `XmlDomGetAttrValueLen` which returns the attribute value as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetAttrValue(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(oratext *)` attribute's value

**See Also:**

XmlDomGetAttrValueLen(), XmlDomSetAttrValue()

#### XmlDomGetAttrValueLen()

Returns the "value" (character data) of an attribute (in the data encoding) as length-encoded string. Character and general entities will have been replaced.

A `NULL`-terminated version is available as `XmlDomGetAttrValue` which returns the attribute value as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the attribute's data will be stored internally as length-encoded. Using the length-based `Get``XXX`() functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than buflen, then a truncated value will be copied into the buffer and len will return the actual length.

##### Syntax

    oratext* XmlDomGetAttrValueLen(
       xmlctx *xctx,
       xmlattrnode *attr,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                                |
|:----------|:-------|:-------------------------------------------|
| `xctx`    | `IN`   | XML context                                |
| `attr`    | `IN`   | attribute node                             |
| `buf`     | `IN`   | input buffer; optional                     |
| `buflen`  | `IN`   | input buffer length; optional              |
| `len`     | `OUT`  | length of attribute's value, in characters |

##### Returns

`(oratext *)` attribute's value

**See Also:**

XmlDomGetAttrValue(), XmlDomSetAttrValue()

#### XmlDomGetAttrValueStream()

Returns the large "value" (associated character data) for an attribute and sends it in pieces to the user's output stream. For very large values, it is not always possible to store them \[efficiently\] as a single contiguous chunk. This function is used to access chunked data of that type.

##### Syntax

    xmlerr XmlDomGetAttrValueStream(
       xmlctx *xctx,
       xmlnode *attr,
       xmlostream *ostream);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `xctx`    | `IN`   | XML context          |
| `attr`    | `IN`   | attribute node       |
| `ostream` | `IN`   | output stream object |

##### Returns

`(xmlerr)` numeric error code, `0` on success

#### XmlDomGetOwnerElem()

Returns the `Element` node associated with an attribute. Each attr either belongs to an element (one and only one), or is detached and not yet part of the DOM tree. In the former case, the element node is returned; if the attr is unassigned, `NULL` is returned.

##### Syntax

    xmlelemnode* XmlDomGetOwnerElem(
       xmlctx *xctx,
       xmlattrnode *attr);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |

##### Returns

`(xmlelemnode *)` attribute's element node \[or `NULL`\]

**See Also:**

XmlDomGetOwnerDocument()

#### XmlDomSetAttrValue()

Sets the given attribute's value to data. If the node is not an attribute, does nothing. Note that the new value must be in the data encoding! It is not verified, converted, or checked. The attribute's specified flag will be `TRUE` after setting a new value.

##### Syntax

    void XmlDomSetAttrValue(
       xmlctx *xctx,
       xmlattrnode *attr,
       oratext *value);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `xctx`    | `IN`   | XML context                           |
| `attr`    | `IN`   | attribute node                        |
| `value`   | `IN`   | new value of attribute; data encoding |

**See Also:**

XmlDomGetAttrValue()

#### XmlDomSetAttrValueStream()

Sets the large "value" (associated character data) for an attribute piecemeal from an input stream. For very large values, it is not always possible to store them efficiently as a single contiguous chunk. This function is used to access chunked data of that type.

##### Syntax

    xmlerr XmlDomSetAttrValueStream(
       xmlctx *xctx,
       xmlnode *attr,
       xmlistream *istream);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `attr`    | `IN`   | attribute node |
| `isream`  | `IN`   | input stream   |

##### Returns

`(xmlerr)` numeric error code, `0` on success

### CharacterData Interface for DOM XML C APIs

The following table summarizes the methods available through the `CharacterData` interface of DOM for XML C APIs.

Table 3-2 Summary of CharacterData DOM Methods for XML C Implementation

| Function                  | Summary                                    |
|:--------------------------|:-------------------------------------------|
| XmlDomAppendData()        | Append data to end of node's current data. |
| XmlDomDeleteData()        | Remove part of node's data.                |
| XmlDomGetCharData()       | Return data for node.                      |
| XmlDomGetCharDataLength() | Return length of data for node.            |
| XmlDomInsertData()        | Insert string into node's current data.    |
| XmlDomReplaceData()       | Replace part of node's data.               |
| XmlDomSetCharData()       | Set data for node.                         |
| XmlDomSubstringData()     | Return substring of node's data.           |

#### XmlDomAppendData()

Append a string to the end of a `CharacterData` node's data. If the node is not `Text`, `Comment` or `CDATA`, or if the string to append is `NULL`, does nothing. The appended data should be in the data encoding. It will not be verified, converted, or checked.

The new node data will be allocated and managed by DOM, but if the previous node value was allocated and manager by the user, they are responsible for freeing it, which is why it is returned.

##### Syntax

    void XmlDomAppendData(
       xmlctx *xctx,
       xmlnode *node,
       oratext *data,
       oratext **old);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `xctx`    | `IN`   | XML context                           |
| `node`    | `IN`   | `CharacterData` node                  |
| `data`    | `IN`   | data to append; data encoding         |
| `old`     | `OUT`  | previous data for node; data encoding |

**See Also:**

XmlDomGetCharData(), XmlDomInsertData(), XmlDomDeleteData(), XmlDomReplaceData(), XmlDomSplitText()

#### XmlDomDeleteData()

Remove a range of characters from a `CharacterData` node's data. If the node is not text, comment or `CDATA`, or if the offset is outside of the original data, does nothing. The `offset` is zero-based, so offset zero refers to the start of the data. Both `offset` and `count` are in characters, not bytes. If the sum of offset and count exceeds the data length then all characters from `offset` to the end of the data are deleted.

The new node data will be allocated and managed by DOM, but if the previous node value was allocated and managed by the user, they are responsible for freeing it, which is why it is returned.

##### Syntax

    void XmlDomDeleteData(
       xmlctx *xctx,
       xmlnode *node,
       ub4 offset,
       ub4 count,
       oratext **old);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `node`    | `IN`   | `CharacterData` node                     |
| `offset`  | `IN`   | character offset where to start removing |
| `count`   | `IN`   | number of characters to delete           |
| `old`     | `OUT`  | previous data for node; data encoding    |

**See Also:**

XmlDomGetCharData(), XmlDomAppendData(), XmlDomInsertData(), XmlDomReplaceData(), XmlDomSplitText()

#### XmlDomGetCharData()

Returns the data for a `CharacterData` node (type text, comment or `CDATA`) in the data encoding. For other node types, or if there is no data, returns `NULL`.

##### Syntax

    oratext* XmlDomGetCharData(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment` or `CDATA` |

##### Returns

`(oratext *)` character data of node \[data encoding\]

**See Also:**

XmlDomSetCharData(), XmlDomCreateText(), XmlDomCreateComment(), XmlDomCreateCDATA()

#### XmlDomGetCharDataLength()

Returns the length of the data for a `CharacterData` node, type `Text`, `Comment` or `CDATA`) in characters, not bytes. For other node types, returns 0.

##### Syntax

    ub4 XmlDomGetCharDataLength(
       xmlctx *xctx,
       xmlnode *cdata);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment` or `CDATA` |

##### Returns

`(ub4)` length in characters, not bytes, of node's data

**See Also:**

XmlDomGetCharData()

#### XmlDomInsertData()

Insert a string into a `CharacterData` node's data at the specified position. If the node is not `Text`, `Comment` or `CDATA`, or if the data to be inserted is `NULL`, or the offset is outside the original data, does nothing. The inserted data must be in the data encoding. It will not be verified, converted, or checked. The offset is specified as characters, not bytes. The offset is zero-based, so inserting at offset zero prepends the data.

The new node data will be allocated and managed by DOM, but if the previous node value was allocated and managed by the user, they are responsible for freeing it (which is why it's returned).

##### Syntax

    void XmlDomInsertData(
       xmlctx *xctx,
       xmlnode *node,
       ub4 offset,
       oratext *arg,
       oratext **old);

| Parameter | In/Out | Description                                         |
|:----------|:-------|:----------------------------------------------------|
| `xctx`    | `IN`   | XML context                                         |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment`, or `CDATA` |
| `offset`  | `IN`   | character offset where to start inserting           |
| `arg`     | `IN`   | data to insert                                      |
| `old`     | `OUT`  | previous data for node; data encoding               |

**See Also:**

XmlDomGetCharData(), XmlDomAppendData(), XmlDomDeleteData(), XmlDomReplaceData(), XmlDomSplitText()

#### XmlDomReplaceData()

Replaces a range of characters in a `CharacterData` node's data with a new string. If the node is not text, comment or `CDATA`, or if the offset is outside of the original data, or if the replacement string is `NULL`, does nothing. If the count is zero, acts just as `XmlDomInsertData`. The offset is zero-based, so offset zero refers to the start of the data. The replacement data must be in the data encoding. It will not be verified, converted, or checked. The offset and count are both in characters, not bytes. If the sum of offset and count exceeds length, then all characters to the end of the data are replaced.

The new node data will be allocated and managed by DOM, but if the previous node value was allocated and managed by the user, they are responsible for freeing it, which is why it is returned.

##### Syntax

    void XmlDomReplaceData(
       xmlctx *xctx,
       xmlnode *node,
       ub4 offset,
       ub4 count,
       oratext *arg,
       oratext **old);

| Parameter | In/Out | Description                                         |
|:----------|:-------|:----------------------------------------------------|
| `xctx`    | `IN`   | XML context                                         |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment`, or `CDATA` |
| `offset`  | `IN`   | character offset where to start replacing           |
| `count`   | `IN`   | number of characters to replace                     |
| `arg`     | `IN`   | replacement substring; data encoding                |
| `old`     | `OUT`  | previous data for node; data encoding               |

**See Also:**

XmlDomGetCharData(), XmlDomAppendData(), XmlDomInsertData(), XmlDomDeleteData(), XmlDomSplitText()

#### XmlDomSetCharData()

Sets data for a `CharacterData` node (type text, comment or `CDATA`), replacing the old data. For other node types, does nothing. The new data is not verified, converted, or checked; it should be in the data encoding.

##### Syntax

    void XmlDomSetCharData(
       xmlctx *xctx,
       xmlnode *node,
       oratext *data);

| Parameter | In/Out | Description                                         |
|:----------|:-------|:----------------------------------------------------|
| `xctx`    | `IN`   | XML context                                         |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment`, or `CDATA` |
| `data`    | `IN`   | new data for node                                   |

**See Also:**

XmlDomGetCharData()

#### XmlDomSubstringData()

Returns a range of character data from a `CharacterData` node, type `Text`, `Comment` or `CDATA`. For other node types, or if count is zero, returns `NULL`. Since the data is in the data encoding, offset and count are in characters, not bytes. The beginning of the string is offset `0`. If the sum of offset and count exceeds the length, then all characters to the end of the data are returned.

The substring is permanently allocated in the node's document's memory pool. To free the substring, use `XmlDomFreeString`.

##### Syntax

    oratext* XmlDomSubstringData(
       xmlctx *xctx,
       xmlnode *node,
       ub4 offset,
       ub4 count);

| Parameter | In/Out | Description                                             |
|:----------|:-------|:--------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                             |
| `node`    | `IN`   | `CharacterData` node; `Text`, `Comment`, or `CDATA`     |
| `offset`  | `IN`   | character offset where to start extraction of substring |
| `count`   | `IN`   | number of characters to extract                         |

##### Returns

`(oratext *)` specified substring.

**See Also:**

XmlDomAppendData(), XmlDomInsertData(), XmlDomDeleteData(), XmlDomReplaceData(), XmlDomSplitText(), XmlDomFreeString()

### Document Interface for DOM XML C APIs

The following table summarizes the methods available through the `Document` interface of DOM for XML C APIs.

Table 3-3 Summary of Document DOM Methods for XML C Implementation

| Function                   | Summary                                                         |
|:---------------------------|:----------------------------------------------------------------|
| XmlDomCreateAttr()         | Create attribute node.                                          |
| XmlDomCreateAttrNS()       | Create attribute node with namespace information.               |
| XmlDomCreateCDATA()        | Create `CDATA` node.                                            |
| XmlDomCreateComment()      | Create comment node.                                            |
| XmlDomCreateElem()         | Create an element node.                                         |
| XmlDomCreateElemNS()       | Create an element node with namespace information.              |
| XmlDomCreateEntityRef()    | Create entity reference node.                                   |
| XmlDomCreateFragment()     | Create a document fragment.                                     |
| XmlDomCreatePI()           | Create PI node.                                                 |
| XmlDomCreateText()         | Create text node.                                               |
| XmlDomFreeString()         | Frees a string allocate by `XmlDomSubstringData`, and others.   |
| XmlDomGetBaseURI()         | Returns the base URI for a document.                            |
| XmlDomGetDTD()             | Get DTD for document.                                           |
| XmlDomGetDecl()            | Returns a document's `XMLDecl` information.                     |
| XmlDomGetDocElem()         | Get top-level element for document.                             |
| XmlDomGetDocElemByID()     | Get document element given ID.                                  |
| XmlDomGetDocElemsByTag()   | Obtain document elements.                                       |
| XmlDomGetDocElemsByTagNS() | Obtain document elements (namespace aware version).             |
| XmlDomGetLastError()       | Return last error code for document.                            |
| XmlDomGetSchema()          | Returns URI of schema associated with document.                 |
| XmlDomImportNode()         | Import a node from another DOM.                                 |
| XmlDomIsSchemaBased()      | Indicate whether a schema is associated with a document.        |
| XmlDomSaveString()         | Saves a string permanently in a document's memory pool.         |
| XmlDomSaveString2()        | Saves a Unicode string permanently in a document's memory pool. |
| XmlDomSetDTD()             | Sets DTD for document.                                          |
| XmlDomSetDocOrder()        | Set document order for all nodes.                               |
| XmlDomSetLastError()       | Sets last error code for document.                              |
| XmlDomSync()               | Synchronizes the persistent version of a document with its DOM. |

#### XmlDomCreateAttr()

Creates an attribute node with the given name and value (in the data encoding). Note this function differs from the DOM specification, which does not allow the initial value of the attribute to be set (see `XmlDomSetAttrValue`). The name is required, but the value may be `NULL`; neither is verified, converted, or checked.

This is the non-namespace aware function (see `XmlDomCreateAttrNS`): the new attribute will have `NULL` namespace URI and prefix, and its local name will be the same as its name, even if the name specified is a qualified name.

If given an initial value, the attribute's specified flag will be `TRUE`.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild`, and so on.

See `XmlDomSetAttr` which creates and adds an attribute in a single operation.

The name and value are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlattrnode* XmlDomCreateAttr(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *name,
       oratext *value);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `doc`     | `IN`   | XML document node                             |
| `name`    | `IN`   | new node's name; data encoding; user control  |
| `value`   | `IN`   | new node's value; data encoding; user control |

##### Returns

`(xmlattrnode *)` new `Attr` node.

**See Also:**

XmlDomSetAttrValue(), XmlDomCreateAttrNS(), XmlDomSetAttr(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateAttrNS()

Creates an attribute node with the given namespace URI and qualified name; this is the namespace-aware version of `XmlDomCreateAttr`. Note this function differs from the DOM specification, which does not allow the initial value of the attribute to be set (see `XmlDomSetAttrValue`). The name is required, but the value may be `NULL`; neither is verified, converted, or checked.

If given an initial value, the attribute's specified flag will be `TRUE`.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild`, and so on. See `XmlDomSetAttr` which creates and adds an attribute in a single operation.

The URI, qualified name and value are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlattrnode* XmlDomCreateAttrNS(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *uri,
       oratext *qname,
       oratext *value);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `doc`     | `IN`   | XML document node                                  |
| `uri`     | `IN`   | node's namespace URI; data encoding; user control  |
| `qname`   | `IN`   | node's qualified name; data encoding; user control |
| `value`   | `IN`   | new node's value; data encoding; user control      |

##### Returns

`(xmlattrnode *)` new `Attr` node.

**See Also:**

XmlDomSetAttrValue(), XmlDomCreateAttr(), XmlDomSetAttr(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateCDATA()

Creates a `CDATASection` node with the given initial data (which should be in the data encoding). A `CDATASection` is considered verbatim and is never parsed; it will not be joined with adjacent `Text` nodes by the normalize operation. The initial data may be `NULL`; if provided, it is not verified, converted, or checked. The name of a `CDATA` node is always "`#cdata-section`".

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The `CDATA` is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlcdatanode* XmlDomCreateCDATA(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *data);

| Parameter | In/Out | Description                                     |
|:----------|:-------|:------------------------------------------------|
| `xctx`    | `IN`   | XML context                                     |
| `doc`     | `IN`   | XML document node                               |
| `data`    | `IN`   | new node's `CDATA`; data encoding; user control |

##### Returns

`(xmlcdatanode *)` new `CDATA` node.

**See Also:**

XmlDomCreateText(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateComment()

Creates a `Comment` node with the given initial data (which must be in the data encoding). The data may be `NULL`; if provided, it is not verified, converted, or checked. The name of a `Comment` node is always "`#comment`".

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The comment data is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlcommentnode* XmlDomCreateComment(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *data);

| Parameter | In/Out | Description                                     |
|:----------|:-------|:------------------------------------------------|
| `xctx`    | `IN`   | XML context                                     |
| `doc`     | `IN`   | XML document node                               |
| `data`    | `IN`   | new node's comment; data encoding; user control |

##### Returns

`(xmlcommentnode *)` new `Comment` node.

**See Also:**

XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateElem()

Creates an element node with the given tag name (which should be in the data encoding). Note that the tag name of an element is case sensitive. This is the non-namespace aware function: the new node will have `NULL` namespace URI and prefix, and its local name will be the same as its tag name, even if the tag name specified is a qualified name.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The `tagname` is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlelemnode* XmlDomCreateElem(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *tagname);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `doc`     | `IN`   | XML document node                            |
| `tagname` | `IN`   | new node's name; data encoding; user control |

##### Returns

`(xmlelemnode *)` new `Element` node.

**See Also:**

XmlDomCreateElemNS(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateElemNS()

Creates an element with the given namespace URI and qualified name. Note that element names are case sensitive, and the qualified name is required though the URI may be `NULL`. The qualified name will be split into prefix and local parts, retrievable with `XmlDomGetNodePrefix`, `XmlDomGetNodeLocal`, and so on; the tagName will be the full qualified name.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The URI and qualified name are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlelemnode* XmlDomCreateElemNS(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *uri,
       oratext *qname);

| Parameter | In/Out | Description                                            |
|:----------|:-------|:-------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                            |
| `doc`     | `IN`   | XML document node                                      |
| `uri`     | `IN`   | new node's namespace URI; data encoding, user control  |
| `qname`   | `IN`   | new node's qualified name; data encoding; user control |

##### Returns

`(xmlelemnode *)` new `Element` node.

**See Also:**

XmlDomCreateElem(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateEntityRef()

Creates an `EntityReference` node; the name (which should be in the data encoding) is the name of the entity to be referenced. The named entity does not have to exist. The name is not verified, converted, or checked.

`EntityReference` nodes are never generated by the parser; instead, entity references are expanded as encountered. On output, an entity reference node will turn into a "&name;" style reference.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild`, and so on.

The entity reference name is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlentrefnode* XmlDomCreateEntityRef(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *name);

| Parameter | In/Out | Description                                            |
|:----------|:-------|:-------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                            |
| `doc`     | `IN`   | XML document node                                      |
| `name`    | `IN`   | name of referenced entity; data encoding; user control |

##### Returns

`(xmlentrefnode *)` new `EntityReference` node.

#### XmlDomCreateFragment()

Creates an empty `DocumentFragment` node. A document fragment is treated specially when it is inserted into a DOM tree: the children of the fragment are inserted in order instead of the fragment node itself. After insertion, the fragment node will still exist, but have no children. See `XmlDomInsertBefore`, `XmlDomReplaceChild`, `XmlDomAppendChild`, and so on. The name of a fragment node is always "`#document-fragment`".

##### Syntax

    xmlfragnode* XmlDomCreateFragment(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(xmlfragnode *)` new empty `DocumentFragment` node

**See Also:**

XmlDomInsertBefore(), XmlDomReplaceChild(), XmlDomAppendChild()

#### XmlDomCreatePI()

Creates a `ProcessingInstruction` node with the given target and data (which should be in the data encoding). The data may be `NULL` initially, and may be changed later (with `XmlDomSetPIData`), but the target is required and cannot be changed. Note the target and data are not verified, converted, or checked. The name of a PI node is the same as the target.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The PI's target and data are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlpinode* XmlDomCreatePI(
       xmlctx *xctx
       xmldocnode *doc,
       oratext *target,
       oratext *data);

| Parameter | In/Out | Description                                    |
|:----------|:-------|:-----------------------------------------------|
| `xctx`    | `IN`   | XML context                                    |
| `doc`     | `IN`   | XML document node                              |
| `target`  | `IN`   | new node's target; data encoding; user control |
| `data`    | `IN`   | new node's data; data encoding; user control   |

##### Returns

`(xmlpinode *)` new PI node.

**See Also:**

XmlDomGetPITarget(), XmlDomGetPIData(), XmlDomSetPIData(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomCreateText()

Creates a `Text` node with the given initial data (which must be non-`NULL` and in the data encoding). The data may be `NULL`; if provided, it is not verified, converted, checked, or parsed (entities will not be expanded). The name of a fragment node is always "`#text`". New data for a `Text` node can be set; see the `CharacterData` interface for editing methods.

The new node is an orphan with no parent; it must be added to the DOM tree with `XmlDomAppendChild` and so on.

The text data is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmltextnode* XmlDomCreateText(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *data);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `doc`     | `IN`   | XML document node                            |
| `data`    | `IN`   | new node's text; data encoding; user control |

##### Returns

`(xmltextnode *)` new `Text` node.

**See Also:**

XmlDomCreateCDATA(), XmlDomSetNodeValue(), XmlDomGetNodeValue(), XmlDomSetCharData(), XmlDomGetCharData(), XmlDomGetCharDataLength(), XmlDomSubstringData(), XmlDomAppendData(), XmlDomInsertData(), XmlDomDeleteData(), XmlDomReplaceData(), XmlDomCleanNode(), XmlDomFreeNode()

#### XmlDomFreeString()

Frees the string allocated by `XmlDomSubstringData` or similar functions. Note that strings explicitly saved with `XmlDomSaveString` are not freeable individually.

##### Syntax

    void XmlDomFreeString(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *str);

| Parameter | In/Out | Description                       |
|:----------|:-------|:----------------------------------|
| `xctx`    | `IN`   | XML context                       |
| `doc`     | `IN`   | document where the string belongs |
| `str`     | `IN`   | string to free                    |

**See Also:**

XmlDomSaveString(), XmlDomSaveString2()

#### XmlDomGetBaseURI()

Returns the base URI for a document. Usually only documents that were loaded from a URI will automatically have a base URI; documents loaded from other sources (`stdin`, buffer, and so on) will not naturally have a base URI, but a base URI may have been set for them using `XmlDomSetBaseURI`, for the purposes of resolving relative URIs in inclusion.

##### Syntax

    oratext *XmlDomGetBaseURI(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(oratext *)` document's base URI \[or `NULL`\]

**See Also:**

XmlDomSetBaseURI()

#### XmlDomGetDTD()

Returns the DTD node associated with current document; if there is no DTD, returns `NULL`. The DTD cannot be edited, but its children may be retrieved with `XmlDomGetChildNodes` as for other node types.

##### Syntax

    xmldtdnode* XmlDomGetDTD(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(xmldtdnode *)` DTD node for document \[or `NULL`\]

**See Also:**

XmlDomSetDTD(), [XmlCreateDTD()](package-XML-API.md) and [XmlCreate()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md), XmlDomGetDTDName(), XmlDomGetDTDEntities(), and XmlDomGetDTDNotations()

#### XmlDomGetDecl()

Returns the information from a document's `XMLDecl`. If there is no `XMLDecl`, returns `XMLERR_NO_DECL`. Returned are the XML version# ("`1.0`" or "`2.0`"), the specified encoding, and the standalone value. If encoding is not specified, `NULL` will be set. The standalone flag is three-state: `< 0` if standalone was not specified, `0` if it was specified and `FALSE`, `> 0` if it was specified and `TRUE`.

##### Syntax

    xmlerr XmlDomGetDecl(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext **ver,
       oratext **enc,
       sb4 *std);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `xctx`    | `IN`   | XML context              |
| `doc`     | `IN`   | XML document node        |
| `ver`     | `OUT`  | XML version              |
| `enc`     | `OUT`  | encoding specification   |
| `std`     | `OUT`  | standalone specification |

##### Returns

`(xmlerr)` XML error code, perhaps version/encoding/standalone set

#### XmlDomGetDocElem()

Returns the root element (node) of the DOM tree, or `NULL` if there is none. Each document has only one uppermost `Element` node, called the root element. It is created after a document is parsed successfully, or manually by `XmlDomCreateElem` then `XmlDomAppendChild`, and so on.

##### Syntax

    xmlelemnode* XmlDomGetDocElem(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(xmlelemnode *)` root element \[or `NULL`\]

**See Also:**

XmlDomCreateElem()

#### XmlDomGetDocElemByID()

Returns the element node which has the given ID. If no such ID is defined, returns `NULL`. Note that attributes named "ID" are not automatically of type ID; ID attributes (which can have any name) must be declared as type ID in the DTD.

The given ID should be in the data encoding or it might not match.

##### Syntax

    xmlelemnode* XmlDomGetDocElemByID(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *id);

| Parameter | In/Out | Description                        |
|:----------|:-------|:-----------------------------------|
| `xctx`    | `IN`   | XML context                        |
| `doc`     | `IN`   | XML document node                  |
| `id`      | `IN`   | element's unique ID; data encoding |

##### Returns

`(xmlelemnode *)` matching element.

**See Also:**

XmlDomGetDocElemsByTag(), XmlDomGetDocElemsByTagNS()

#### XmlDomGetDocElemsByTag()

Returns a list of all elements in the document tree rooted at the root node with a given tag name, in document order (the order in which they would be encountered in a preorder traversal of the tree). If root is `NULL`, the entire document is searched.

The special name "`*`" matches all tag names; a `NULL` name matches nothing. Note that tag names are case sensitive, and should be in the data encoding or a mismatch might occur.

This function is not namespace aware; the full tag names are compared. If two qualified names with two different prefixes both of which map to the same URI are compared, the comparison will fail. See `XmlDomGetElemsByTagNS` for the namespace-aware version.

The list should be freed with `XmlDomFreeNodeList` when it is no longer needed.

The list is not live, it is a snapshot. That is, if a new node which matched the tag name were added to the DOM after the list was returned, the list would not automatically be updated to include the node.

##### Syntax

    xmlnodelist* XmlDomGetDocElemsByTag(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *name);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `doc`     | `IN`   | XML document node                            |
| `name`    | `IN`   | tagname to match; data encoding; `*` for all |

##### Returns

`(xmlnodelist *)` new `NodeList` containing all matched `Element`s.

**See Also:**

XmlDomGetDocElemByID(), XmlDomGetDocElemsByTagNS(), XmlDomFreeNodeList()

#### XmlDomGetDocElemsByTagNS()

Returns a list of all elements (in the document tree rooted at the given node) with a given namespace URI and local name, in the order in which they would be encountered in a preorder traversal of the tree. If root is `NULL`, the entire document is searched.

The URI and local name should be in the data encoding. The special local name "\*" matches all local names; a `NULL` local name matches nothing. Namespace URIs must always match, however, no wildcard is allowed. Note that comparisons are case sensitive. See `XmlDomGetDocElemsByTag` for the non-namespace aware version.

The list should be freed with `XmlDomFreeNodeList` when it is no longer needed.

The list is not live, it is a snapshot. That is, if a new node which matched the tag name were added to the DOM after the list was returned, the list would not automatically be updated to include the node.

##### Syntax

    xmlnodelist* XmlDomGetDocElemsByTagNS(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                                            |
|:----------|:-------|:-------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                            |
| `doc`     | `IN`   | XML document node                                      |
| `uri`     | `IN`   | namespace URI to match; data encoding; `*` matches all |
| `local`   | `IN`   | local name to match; data encoding; `*` matches all    |

##### Returns

`(xmlnodelist *)` new `NodeList` containing all matched `Element`s.

**See Also:**

XmlDomGetDocElemByID(), XmlDomGetDocElemsByTag(), XmlDomFreeNodeList()

#### XmlDomGetLastError()

Returns the error code of the last error which occurred in the given document.

##### Syntax

    xmlerr XmlDomGetLastError(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(xmlerr)` numeric error code, `0` if no error

#### XmlDomGetSchema()

Returns URI of schema associated with document, if there is one, else returns `NULL`. The `XmlLoadDom` functions take a schema location hint (URI); the schema is used for efficient layout of `XMLType` data. If a schema was provided at load time, this function returns `TRUE`.

##### Syntax

    oratext* XmlDomGetSchema(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(oratext *)` Schema URI or `NULL`

**See Also:**

XmlDomIsSchemaBased(), [XmlLoadDom()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md)

#### XmlDomImportNode()

Imports a node from one `Document` to another. The new node is an orphan and has no parent; it must be added to the DOM tree with `XmlDomAppendChild`, and so on. The original node is not modified in any way or removed from its document; instead, a new node is created with copies of all the original node's qualified name, prefix, namespace URI, and local name.

As with `XmlDomCloneNode,` the deep controls whether the children of the node are recursively imported. If `FALSE`, only the node itself is imported, and it will have no children. If `TRUE`, all descendents of the node will be imported as well, and an entire new subtree created.

`Document` and `DocumentType` nodes cannot be imported. Imported attributes will have their specified flags set to `TRUE`. Elements will have only their specified attributes imported; non-specified (default) attributes are omitted. New default attributes (for the destination document) are then added.

##### Syntax

    xmlnode* XmlDomImportNode(
       xmlctx *xctx,
       xmldocnode *doc,
       xmlctx *nctx,
       xmlnode *node,
       boolean deep);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `doc`     | `IN`   | XML document node                        |
| `nctx`    | `IN`   | XML context of imported node             |
| `node`    | `IN`   | node to import                           |
| `deep`    | `IN`   | `TRUE` to import the subtree recursively |

##### Returns

`(xmlnode *)` newly imported node (in this `Document`).

**See Also:**

XmlDomCloneNode()

#### XmlDomIsSchemaBased()

Returns flag specifying whether there is a schema associated with this document. The `XmlLoadDom` functions take a schema location hint (URI); the schema is used for efficient layout of `XMLType` data. If a schema was provided at load time, this function returns `TRUE`.

##### Syntax

    boolean XmlDomIsSchemaBased(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(boolean)` `TRUE` if there is a schema associated with the document

**See Also:**

XmlDomGetSchema(), [XmlLoadDom()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md)

#### XmlDomSaveString()

Copies the given string into the document's memory pool, so that it persists for the life of the document. The individual string will not be freeable, and the storage will be returned only when the entire document is freed. Works on single-byte or multibyte encodings; for Unicode strings, use `XmlDomSaveString2`.

##### Syntax

    oratext* XmlDomSaveString(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *str);

| Parameter | In/Out | Description                                               |
|:----------|:-------|:----------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                               |
| `doc`     | `IN`   | XML document node                                         |
| `str`     | `IN`   | string to save; data encoding; single- or multi-byte only |

##### Returns

`(oratext *)` saved copy of string

**See Also:**

XmlDomSaveString2(), [XmlFreeDocument()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md)

#### XmlDomSaveString2()

Copies the given string into the document's memory pool, so that it persists for the life of the document. The individual string will not be freeable, and the storage will be returned only when the entire document is free. Works on Unicode strings only; for single-byte or multibyte strings, use `XmlDomSaveString`.

##### Syntax

    ub2* XmlDomSaveString2(
       xmlctx *xctx,
       xmldocnode *doc,
       ub2 *ustr);

| Parameter | In/Out | Description                                 |
|:----------|:-------|:--------------------------------------------|
| `xctx`    | `IN`   | XML context                                 |
| `doc`     | `IN`   | XML document node                           |
| `ustr`    | `IN`   | string to save; data encoding; Unicode only |

##### Returns

`(ub2 *)` saved copy of string

**See Also:**

XmlDomSaveString(), [XmlFreeDocument()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md)

#### XmlDomSetBaseURI()

Only documents that were loaded from a URI will automatically have a base URI; documents loaded from other sources (stdin, buffer, and so on) will not naturally have a base URI, so this API is used to set a base URI, for the purposes of relative URI resolution in includes. The base URI should be in the data encoding, and a copy will be made.

##### Syntax

    xmlerr XmlDomSetBaseURI(
       xmlctx *xctx,
       xmldocnode *doc,
       oratext *uri);

| Parameter | In/Out | Description                    |
|:----------|:-------|:-------------------------------|
| `xctx`    | `IN`   | XML context                    |
| `doc`     | `IN`   | XML document node              |
| `uri`     | `IN`   | base URI to set; data encoding |

##### Returns

`(xmlerr)` XML error code

**See Also:**

XmlDomGetBaseURI()

#### XmlDomSetDTD()

Sets the DTD for document. Note this call may only be used for a blank document, before any parsing has taken place. A single DTD can be set for multiple documents, so when a document with a set DTD is freed, the set DTD is not also freed.

##### Syntax

    xmlerr XmlDomSetDTD(
       xmlctx *xctx,
       xmldocnode *doc,
       xmldtdnode *dtdnode);

| Parameter | In/Out | Description                |
|:----------|:-------|:---------------------------|
| `xctx`    | `IN`   | XML context                |
| `doc`     | `IN`   | XML document node          |
| `dtdnode` | `IN`   | `DocumentType` node to set |

##### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDEntities(), XmlDomGetDTDNotations()

#### XmlDomSetDocOrder()

Sets the document order for each node in the current document. Must be called once on the final document before XSLT processing can occur. Note this is called automatically by the XSLT processor, so ordinarily the user need not make this call.

##### Syntax

    ub4 XmlDomSetDocOrder(
       xmlctx *xctx,
       xmldocnode *doc,
       ub4 start_id);

| Parameter  | In/Out | Description       |
|:-----------|:-------|:------------------|
| `xctx`     | `IN`   | XML context       |
| `doc`      | `IN`   | XML document node |
| `start_id` | `IN`   | string ID number  |

##### Returns

`(ub4)` highest ordinal assigned

#### XmlDomSetLastError()

Sets the Last Error code for the given document. If `doc` is `NULL`, sets the error code for the XML context.

##### Syntax

    xmlerr XmlDomSetLastError(
       xmlctx *xctx,
       xmldocnode *doc,
       xmlerr errcode);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `xctx`    | `IN`   | XML context                           |
| `doc`     | `IN`   | XML document node                     |
| `errcode` | `IN`   | error code to set, `0` to clear error |

##### Returns

`(xmlerr)` original error code

#### XmlDomSync()

Causes a modified DOM to be written back out to its original source, synchronizing the persistent store and in-memory versions.

##### Syntax

    xmlerr XmlDomSync(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `doc`     | `IN`   | XML document node |

##### Returns

`(xmlerr)` numeric error code, `0` on success

### DocumentType Interface for DOM XML C APIs

The following table summarizes the methods available through the `DocumentType` interface of DOM for XML C APIs.

Table 3-4 Summary of DocumentType DOM Methods for XML C Implementation

| Function                     | Summary                    |
|:-----------------------------|:---------------------------|
| XmlDomGetDTDEntities()       | Get entities of DTD.       |
| XmlDomGetDTDInternalSubset() | Get DTD's internal subset. |
| XmlDomGetDTDName()           | Get name of DTD.           |
| XmlDomGetDTDNotations()      | Get notations of DTD.      |
| XmlDomGetDTDPubID()          | Get DTD's public ID.       |
| XmlDomGetDTDSysID()          | Get DTD's system ID.       |

#### XmlDomGetDTDEntities()

Returns a named node map of general entities defined by the DTD. If the node is not a DTD, or has no general entities, returns `NULL`.

##### Syntax

    xmlnamedmap* XmlDomGetDTDEntities(
       xmlctx *xctx,
       xmldtdnode *dtd);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `dtd`     | `IN`   | DTD node    |

##### Returns

`(xmlnamedmap *)` named node map containing entities declared in DTD

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDNotations(), XmlDomGetDTDSysID(), XmlDomGetDTDInternalSubset()

#### XmlDomGetDTDInternalSubset()

Returns the content model for an element. If there is no DTD, returns `NULL`.

##### Syntax

    xmlnode* XmlDomGetDTDInternalSubset(
       xmlctx *xctx,
       xmldtdnode *dtd,
       oratext *name);

| Parameter | In/Out | Description                      |
|:----------|:-------|:---------------------------------|
| `xctx`    | `IN`   | XML context                      |
| `dtd`     | `IN`   | DTD node                         |
| `name`    | `IN`   | name of `Element`; data encoding |

##### Returns

`(xmlnode *)` content model subtree

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDEntities(), XmlDomGetDTDNotations(), XmlDomGetDTDPubID()

#### XmlDomGetDTDName()

Returns a DTD's name (specified immediately after the `DOCTYPE` keyword), or `NULL` if the node is not type DTD.

##### Syntax

    oratext* XmlDomGetDTDName(
       xmlctx *xctx,
       xmldtdnode *dtd);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `dtd`     | `IN`   | DTD node    |

##### Returns

`(oratext *)` name of DTD

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDEntities(), XmlDomGetDTDNotations(), XmlDomGetDTDSysID(), XmlDomGetDTDInternalSubset()

#### XmlDomGetDTDNotations()

Returns named node map of notations declared by the DTD. If the node is not a DTD or has no `Notation`s, returns `NULL`.

##### Syntax

    xmlnamedmap* XmlDomGetDTDNotations(
       xmlctx *xctx,
       xmldtdnode *dtd);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `dtd`     | `IN`   | DTD node    |

##### Returns

`(xmlnamedmap *)` named node map containing notations declared in DTD

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDEntities(), XmlDomGetDTDSysID(), XmlDomGetDTDInternalSubset()

#### XmlDomGetDTDPubID()

Returns a DTD's public identifier.

##### Syntax

    oratext* XmlDomGetDTDPubID(
       xmlctx *xctx,
       xmldtdnode *dtd);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `dtd`     | `IN`   | DTD node    |

##### Returns

`(oratext *)` DTD's public identifier \[data encoding\]

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDEntities(), XmlDomGetDTDSysID(), XmlDomGetDTDInternalSubset()

#### XmlDomGetDTDSysID()

Returns a DTD's system identifier.

##### Syntax

    oratext* XmlDomGetDTDSysID(
       xmlctx *xctx,
       xmldtdnode *dtd);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `dtd`     | `IN`   | DTD node    |

##### Returns

`(oratext *)` DTD's system identifier \[data encoding\]

**See Also:**

XmlDomGetDTD(), XmlDomGetDTDName(), XmlDomGetDTDEntities(), XmlDomGetDTDPubID(), XmlDomGetDTDInternalSubset()

### Element Interface for DOM XML C APIs

The following table summarizes the methods available through the `Element` Interface of DOM for XML C APIs.

Table 3-5 Summary of Element DOM Methods for XML C Implementation

| Function                   | Summary                                                            |
|:---------------------------|:-------------------------------------------------------------------|
| XmlDomGetAttr()            | Return attribute's value given its name.                           |
| XmlDomGetAttrNS()          | Return attribute's value given its URI and local name.             |
| XmlDomGetAttrNode()        | Get attribute by name.                                             |
| XmlDomGetAttrNodeNS()      | Get attribute by name (namespace aware version).                   |
| XmlDomGetChildrenByTag()   | Get children of element with given tag name (non-namespace aware). |
| XmlDomGetChildrenByTagNS() | Get children of element with tag name (namespace aware version).   |
| XmlDomGetDocElemsByTag()   | Obtain doc elements.                                               |
| XmlDomGetDocElemsByTagNS() | Obtain doc elements (namespace aware version).                     |
| XmlDomGetTag()             | Return an element node's tag name.                                 |
| XmlDomHasAttr()            | Does named attribute exist?                                        |
| XmlDomHasAttrNS()          | Does named attribute exist (namespace aware version)?              |
| XmlDomRemoveAttr()         | Remove attribute with specified name.                              |
| XmlDomRemoveAttrNS()       | Remove attribute with specified URI and local name.                |
| XmlDomRemoveAttrNode()     | Remove attribute node.                                             |
| XmlDomSetAttr()            | Set new attribute for element.                                     |
| XmlDomSetAttrNS()          | Set new attribute for element (namespace aware version).           |
| XmlDomSetAttrNode()        | Set attribute node.                                                |
| XmlDomSetAttrNodeNS()      | Set attribute node (namespace aware version).                      |

#### XmlDomGetAttr()

Returns the value of an element's attribute (specified by name). Note that an attribute may have the empty string as its value, but cannot be `NULL`. If the element does not have an attribute with the given name, `NULL` is returned.

##### Syntax

    oratext* XmlDomGetAttr(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `elem`    | `IN`   | element node     |
| `name`    | `IN`   | attribute's name |

##### Returns

`(oratext *)` named attribute's value \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetAttrNS(), XmlDomGetAttrs(), XmlDomGetAttrNode()

#### XmlDomGetAttrNS()

Returns the value of an element's attribute (specified by URI and local name). Note that an attribute may have the empty string as its value, but cannot be `NULL`. If the element does not have an attribute with the given name, `NULL` is returned.

##### Syntax

    oratext* XmlDomGetAttrNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `elem`    | `IN`   | element node                             |
| `uri`     | `IN`   | attribute's namespace URI; data encoding |
| `local`   | `IN`   | attribute's local name; data encoding    |

##### Returns

`(oratext *)` named attribute's value \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetAttr(), XmlDomGetAttrs(), XmlDomGetAttrNode()

#### XmlDomGetAttrNode()

Returns an element's attribute specified by name. If the node is not an element or the named attribute does not exist, returns `NULL`.

##### Syntax

    xmlattrnode* XmlDomGetAttrNode(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description                     |
|:----------|:-------|:--------------------------------|
| `xctx`    | `IN`   | XML context                     |
| `elem`    | `IN`   | element node                    |
| `name`    | `IN`   | attribute's name; data encoding |

##### Returns

`(xmlattrnode *)` attribute with the specified name \[or `NULL`\]

**See Also:**

XmlDomGetAttrNodeNS(), XmlDomGetAttr()

#### XmlDomGetAttrNodeNS()

Returns an element's attribute specified by URI and localname. If the node is not an element or the named attribute does not exist, returns `NULL`.

##### Syntax

    xmlattrnode* XmlDomGetAttrNodeNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `elem`    | `IN`   | element node                             |
| `uri`     | `IN`   | attribute's namespace URI; data encoding |
| `local`   | `IN`   | attribute's local name; data encoding    |

##### Returns

`(xmlattrnode *)` attribute node with the given URI/local name \[or `NULL`\]

**See Also:**

XmlDomGetAttrNode(), XmlDomGetAttr()

#### XmlDomGetChildrenByTag()

Returns a list of children of an element with the given tag name, in the order in which they would be encountered in a preorder traversal of the tree. The tag name should be in the data encoding. The special name "`*`" matches all tag names; a `NULL` name matches nothing. Note that tag names are case sensitive. This function is not namespace aware; the full tag names are compared. If two prefixes which map to the same URI are compared, the comparison will fail. See `XmlDomGetChildrenByTagNS` for the namespace-aware version. The returned list can be freed with `XmlDomFreeNodeList`.

##### Syntax

    xmlnodelist* XmlDomGetChildrenByTag(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `elem`    | `IN`   | element node                                  |
| `name`    | `IN`   | tag name to match; data encoding; `*` for all |

##### Returns

`(xmlnodelist *)` node list of matching children

**See Also:**

XmlDomGetChildrenByTagNS(), XmlDomFreeNodeList()

#### XmlDomGetChildrenByTagNS()

Returns a list of children of an element with the given URI and local name, in the order in which they would be encountered in a preorder traversal of the tree. The URI and local name should be in the data encoding. The special name "`*`" matches all URIs or tag names; a `NULL` name matches nothing. Note that names are case sensitive. See `XmlDomGetChildrenByTag` for the non-namespace version. The returned list can be freed with `XmlDomFreeNodeList`.

##### Syntax

    xmlnodelist* XmlDomGetChildrenByTagNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                                            |
|:----------|:-------|:-------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                            |
| `elem`    | `IN`   | element node                                           |
| `uri`     | `IN`   | namespace URI to match; data encoding; `*` matches all |
| `local`   | `IN`   | local name to match; data encoding; \* matches all     |

##### Returns

`(xmlnodelist *)` node list of matching children

**See Also:**

XmlDomGetChildrenByTag(), XmlDomFreeNodeList()

#### XmlDomGetElemsByTag()

Returns a list of all elements (in the document tree rooted at the root node) with a given tag name, in the order in which they would be encountered in a preorder traversal of the tree. If root is `NULL`, the entire document is searched. The tag name should be in the data encoding. The special name "`*`" matches all tag names; a `NULL` name matches nothing. Note that tag names are case sensitive. This function is not namespace aware; the full tag names are compared. If two prefixes which map to the same URI are compared, the comparison will fail. See `XmlDomGetElemsByTagNS` for the namespace-aware version. The returned list can be freed with `XmlDomFreeNodeList`.

##### Syntax

    xmlnodelist* XmlDomGetElemsByTag(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `elem`    | `IN`   | element node                                  |
| `name`    | `IN`   | tag name to match; data encoding; `*` for all |

##### Returns

`(xmlnodelist *)` node list of matching elements

**See Also:**

XmlDomGetElemsByTagNS(), XmlDomFreeNodeList()

#### XmlDomGetElemsByTagNS()

Returns a list of all elements (in the document tree rooted at the root node) with a given URI and localname, in the order in which they would be encountered in a preorder traversal of the tree. If root is `NULL`, the entire document is searched. The tag name should be in the data encoding. The special name "`*`" matches all tag names; a `NULL` name matches nothing. Note that tag names are case sensitive. This function is not namespace aware; the full tag names are compared. If two prefixes which map to the same URI are compared, the comparison will fail. The returned list can be freed with `XmlDomFreeNodeList`.

##### Syntax

    xmlnodelist* XmlDomGetElemsByTagNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `elem`    | `IN`   | element node                                       |
| `uri`     | `IN`   | namespace URI to match; data encoding; `*` for all |
| `local`   | `IN`   | local name to match; data encoding; `*` for all    |

##### Returns

`(xmlnodelist *)` node list of matching elements

**See Also:**

XmlDomGetDocElemsByTag(), XmlDomFreeNodeList()

#### XmlDomGetTag()

Returns the `tagName` of a node, which is the same as its name. DOM 1.0 states "...even though there is a generic `nodeName` attribute on the `Node` interface, there is still a `tagName` attribute on the `Element` interface; these two attributes must contain the same value, but the Working Group considers it worthwhile to support both, given the different constituencies the DOM API must satisfy."

##### Syntax

    oratext* XmlDomGetTag(
       xmlctx *xctx,
       xmlelemnode *elem);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `elem`    | `IN`   | `Element` node |

##### Returns

`(oratext *)` element's name \[data encoding\]

**See Also:**

XmlDomGetNodeName()

#### XmlDomHasAttr()

Determines if an element has an attribute with the given name. Returns `TRUE` if so, `FALSE` if not.

##### Syntax

    boolean XmlDomHasAttr(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description                     |
|:----------|:-------|:--------------------------------|
| `xctx`    | `IN`   | XML context                     |
| `elem`    | `IN`   | `Element` node                  |
| `name`    | `IN`   | attribute's name; data encoding |

##### Returns

`(boolean)` `TRUE` if element has attribute with given name

**See Also:**

XmlDomHasAttrNS()

#### XmlDomHasAttrNS()

Determines if an element has an attribute with the given URI and localname. Returns `TRUE` if so, `FALSE` if not.

##### Syntax

    boolean XmlDomHasAttrNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `elem`    | `IN`   | `Element` node                           |
| `uri`     | `IN`   | attribute's namespace URI; data encoding |
| `local`   | `IN`   | attribute's local name; data encoding    |

##### Returns

`(boolean)` `TRUE` if element has attribute with given URI/localname

**See Also:**

XmlDomHasAttr()

#### XmlDomRemoveAttr()

Removes an attribute (specified by name). If the removed attribute has a default value it is immediately re-created with that default. Note that the attribute is removed from the element's list of attributes, but the attribute node itself is not destroyed.

##### Syntax

    void XmlDomRemoveAttr(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name);

| Parameter | In/Out | Description                     |
|:----------|:-------|:--------------------------------|
| `xctx`    | `IN`   | XML context                     |
| `elem`    | `IN`   | element node                    |
| `name`    | `IN`   | attribute's name; data encoding |

**See Also:**

XmlDomRemoveAttrNS(), XmlDomRemoveAttrNode()

#### XmlDomRemoveAttrNS()

Removes an attribute (specified by URI and local name). If the removed attribute has a default value it is immediately re-created with that default. Note that the attribute is removed from the element's list of attributes, but the attribute node itself is not destroyed.

##### Syntax

    void XmlDomRemoveAttrNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `xctx`    | `IN`   | XML context               |
| `elem`    | `IN`   | element node              |
| `uri`     | `IN`   | attribute's namespace URI |
| `local`   | `IN`   | attribute's local name    |

**See Also:**

XmlDomRemoveAttr(), XmlDomRemoveAttrNode()

#### XmlDomRemoveAttrNode()

Removes an attribute from an element. If the attribute has a default value, it is immediately re-created with that value (Specified set to `FALSE`). Returns the removed attribute on success, else `NULL`.

##### Syntax

    xmlattrnode* XmlDomRemoveAttrNode(
       xmlctx *xctx,
       xmlelemnode *elem,
       xmlattrnode *oldAttr);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `xctx`    | `IN`   | XML context              |
| `elem`    | `IN`   | element node             |
| `oldAtrr` | `IN`   | attribute node to remove |

##### Returns

`(xmlattrnode *)` replaced attribute node \[or `NULL`\]

**See Also:**

XmlDomRemoveAttr()

#### XmlDomSetAttr()

Creates a new attribute for an element with the given name and value (which should be in the data encoding). If the named attribute already exists, its value is simply replaced. The name and value are not verified, converted, or checked. The value is not parsed, so entity references will not be expanded. The attribute's specified flag will be set.

##### Syntax

    void XmlDomSetAttr(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *name,
       oratext *value);

| Parameter | In/Out | Description                      |
|:----------|:-------|:---------------------------------|
| `xctx`    | `IN`   | XML context                      |
| `elem`    | `IN`   | element node                     |
| `name`    | `IN`   | attribute's name; data encoding  |
| `value`   | `IN`   | attribute's value; data encoding |

**See Also:**

XmlDomSetAttrNS(), XmlDomCreateAttr(), XmlDomSetAttrValue(), XmlDomRemoveAttr()

#### XmlDomSetAttrNS()

Creates a new attribute for an element with the given URI, localname and value (which should be in the data encoding). If the named attribute already exists, its value is simply replaced. The name and value are not verified, converted, or checked.

The value is not parsed, so entity references will not be expanded.

The attribute's specified flag will be set.

##### Syntax

    void XmlDomSetAttrNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       oratext *uri,
       oratext *qname,
       oratext *value);

| Parameter | In/Out | Description                               |
|:----------|:-------|:------------------------------------------|
| `xctx`    | `IN`   | XML context                               |
| `elem`    | `IN`   | element node                              |
| `uri`     | `IN`   | attribute's namespace URI; data encoding  |
| `qname`   | `IN`   | attribute's qualified name; data encoding |
| `value`   | `IN`   | attribute's value; data encoding          |

**See Also:**

XmlDomSetAttr(), XmlDomCreateAttr(), XmlDomSetAttrValue(), XmlDomRemoveAttr()

#### XmlDomSetAttrNode()

Adds a new attribute to an element. If an attribute with the given name already exists, it is replaced and the old attribute returned through `oldNode`. If the attribute is new, it is added to the element's list and `oldNode` set to `NULL`.

##### Syntax

    xmlattrnode* XmlDomSetAttrNode(
       xmlctx *xctx,
       xmlelemnode *elem,
       xmlattrnode *newAttr);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `xctx`    | `IN`   | XML context           |
| `elem`    | `IN`   | element node          |
| `newAttr` | `IN`   | attribute node to add |

##### Returns

`(xmlattrnode *)` replaced attribute node (or `NULL`)

**See Also:**

XmlDomSetAttrNodeNS(), XmlDomCreateAttr(), XmlDomSetAttrValue()

#### XmlDomSetAttrNodeNS()

Adds a new attribute to an element. If an attribute with `newNode`'s URI and localname already exists, it is replaced and the old attribute returned through `oldNode`. If the attribute is new, it is added to the element's list and `oldNode` set to `NULL`.

##### Syntax

    xmlattrnode* XmlDomSetAttrNodeNS(
       xmlctx *xctx,
       xmlelemnode *elem,
       xmlattrnode *newAttr);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `xctx`    | `IN`   | XML context           |
| `elem`    | `IN`   | element node          |
| `newAttr` | `IN`   | attribute node to add |

##### Returns

`(xmlattrnode *)` replaced attribute node \[or `NULL`\]

**See Also:**

XmlDomSetAttrNode(), XmlDomCreateAttr(), XmlDomSetAttrValue()

### Entity Interface for DOM XML C APIs

The following table summarizes the methods available through the `Entity` interface of DOM for XML C APIs.

Table 3-6 Summary of Entity DOM Methods for XML C Implementation

| Function                  | Summary                 |
|:--------------------------|:------------------------|
| XmlDomGetEntityNotation() | Get entity's notation.  |
| XmlDomGetEntityPubID()    | Get entity's public ID. |
| XmlDomGetEntitySysID()    | Get entity's system ID. |
| XmlDomGetEntityType()     | Get entity's type.      |

#### XmlDomGetEntityNotation()

For unparsed entities, returns the name of its notation (in the data encoding). For parsed entities and other node types, returns `NULL`.

##### Syntax

    oratext* XmlDomGetEntityNotation(
       xmlctx *xctx,
       xmlentnode *ent);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `ent`     | `IN`   | entity node |

##### Returns

`(oratext *)` entity's notation \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetEntityPubID(), XmlDomGetEntitySysID()

#### XmlDomGetEntityPubID()

Returns an entity's public identifier (in the data encoding). If the node is not an entity, or has no defined public ID, returns `NULL`.

##### Syntax

    oratext* XmlDomGetEntityPubID(
       xmlctx *xctx,
       xmlentnode *ent);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `ent`     | `IN`   | entity node |

##### Returns

`(oratext *)` entity's public identifier \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetEntitySysID(), XmlDomGetEntityNotation()

#### XmlDomGetEntitySysID()

Returns an entity's system identifier (in the data encoding). If the node is not an entity, or has no defined system ID, returns `NULL`.

##### Syntax

    oratext* XmlDomGetEntitySysID(
       xmlctx *xctx,
       xmlentnode *ent);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `ent`     | `IN`   | entity node |

##### Returns

`(oratext *)` entity's system identifier \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetEntityPubID(), XmlDomGetEntityNotation()

#### XmlDomGetEntityType()

Returns a boolean for an entity describing whether it is general (`TRUE`) or parameter (`FALSE`).

##### Syntax

    boolean XmlDomGetEntityType(
       xmlctx *xctx,
       xmlentnode *ent);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `ent`     | `IN`   | entity node |

##### Returns

`(boolean)` `TRUE` for general entity, `FALSE` for parameter entity

**See Also:**

XmlDomGetEntityPubID(), XmlDomGetEntitySysID(), XmlDomGetEntityNotation()

### NamedNodeMap Interface for DOM XML C APIs

The following table summarizes the methods available through the `NamedNodeMap` interface of DOM for XML C APIs.

Table 3-7 Summary of NamedNodeMap DOM Methods for XML C Implementation

| Function                  | Summary                                                    |
|:--------------------------|:-----------------------------------------------------------|
| XmlDomGetNamedItem()      | Return named node from list.                               |
| XmlDomGetNamedItemNS()    | Return named node from list (namespace aware version).     |
| XmlDomGetNodeMapItem()    | Return n<sup>th</sup> node in list.                        |
| XmlDomGetNodeMapLength()  | Return length of named node map.                           |
| XmlDomRemoveNamedItem()   | Remove node from named node map.                           |
| XmlDomRemoveNamedItemNS() | Remove node from named node map (namespace aware version). |
| XmlDomSetNamedItem()      | Set node in named node list.                               |
| XmlDomSetNamedItemNS()    | Set node in named node list (namespace aware version).     |

#### XmlDomGetNamedItem()

Retrieves an item from a `NamedNodeMap`, specified by name (which should be in the data encoding). This is a non-namespace-aware function; it just matches (case sensitively) on the whole qualified name. Note this function differs from the DOM spec in that the index of the matching item is also returned.

##### Syntax

    xmlnode* XmlDomGetNamedItem(
       xmlctx *xctx,
       xmlnamedmap *map,
       oratext *name);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `xctx`    | `IN`   | XML context                  |
| `map`     | `IN`   | `NamedNodeMap`               |
| `name`    | `IN`   | name of the node to retrieve |

##### Returns

`(xmlnode *)` `Node` with the specified name \[or `NULL`\]

**See Also:**

XmlDomGetNamedItemNS(), XmlDomGetNodeMapItem(), XmlDomGetNodeMapLength()

#### XmlDomGetNamedItemNS()

Retrieves an item from a `NamedNodeMap`, specified by URI and localname (which should be in the data encoding). Note this function differs from the DOM spec in that the index of the matching item is also returned.

##### Syntax

    xmlnode* XmlDomGetNamedItemNS(
       xmlctx *xctx,
       xmlnamedmap *map,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                                          |
|:----------|:-------|:-----------------------------------------------------|
| `xctx`    | `IN`   | XML context                                          |
| `map`     | `IN`   | `NamedNodeMap`                                       |
| `uri`     | `IN`   | namespace URI of the node to retrieve; data encoding |
| `local`   | `IN`   | local name of the node to retrieve; data encoding    |

##### Returns

`(xmlnode *)` node with given local name and namespace URI \[or `NULL`\]

**See Also:**

XmlDomGetNamedItem(), XmlDomGetNodeMapItem(), XmlDomGetNodeMapLength()

#### XmlDomGetNodeMapItem()

Retrieves an item from a `NamedNodeMap`, specified by name (which should be in the data encoding). This is a non-namespace-aware function; it just matches (case sensitively) on the whole qualified name. Note this function differs from the DOM specification in that the index of the matching item is also returned. Named "item" in W3C specification.

##### Syntax

    xmlnode* XmlDomGetNodeMapItem(
       xmlctx *xctx,
       xmlnamedmap *map,
       ub4 index);

| Parameter | In/Out | Description                 |
|:----------|:-------|:----------------------------|
| `xctx`    | `IN`   | XML context                 |
| `map`     | `IN`   | `NamedNodeMap`              |
| `index`   | `IN`   | `0`-based index for the map |

##### Returns

`(xmlnode *)` node at the nth position in the map (or `NULL`)

**See Also:**

XmlDomGetNamedItem(), XmlDomSetNamedItem(), XmlDomRemoveNamedItem(), XmlDomGetNodeMapLength()

#### XmlDomGetNodeMapLength()

Returns the number of nodes in a `NamedNodeMap` (the length). Note that nodes are referred to by index, and the range of valid indexes is `0` through length-1.

##### Syntax

    ub4 XmlDomGetNodeMapLength(
       xmlctx *xctx,
       xmlnamedmap *map);

| Parameter | In/Out | Description    |
|:----------|:-------|:---------------|
| `xctx`    | `IN`   | XML context    |
| `map`     | `IN`   | `NamedNodeMap` |

##### Returns

`(ub4)` number of nodes in `NamedNodeMap`

**See Also:**

XmlDomGetNodeMapItem(), XmlDomGetNamedItem()

#### XmlDomRemoveNamedItem()

Removes a node from a `NamedNodeMap`, specified by name. This is a non-namespace-aware function; it just matches (case sensitively) on the whole qualified name. If the removed node is an attribute with default value (not specified), it is immediately replaced. The removed node is returned; if no removal took place, `NULL` is returned.

##### Syntax

    xmlnode* XmlDomRemoveNamedItem(
       xmlctx *xctx,
       xmlnamedmap *map,
       oratext *name);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `xctx`    | `IN`   | XML context            |
| `map`     | `IN`   | `NamedNodeMap`         |
| `name`    | `IN`   | name of node to remove |

##### Returns

`(xmlnode *)` node removed from this map

**See Also:**

XmlDomRemoveNamedItemNS(), XmlDomGetNamedItem(), XmlDomGetNamedItemNS(), XmlDomSetNamedItem(), XmlDomSetNamedItemNS()

#### XmlDomRemoveNamedItemNS()

Removes a node from a `NamedNodeMap`, specified by URI and localname. If the removed node is an attribute with default value (not specified), it is immediately replaced. The removed node is returned; if no removal took place, `NULL` is returned.

##### Syntax

    xmlnode* XmlDomRemoveNamedItemNS(
       xmlctx *xctx,
       xmlnamedmap *map,
       oratext *uri,
       oratext *local);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `map`     | `IN`   | `NamedNodeMap`                                     |
| `uri`     | `IN`   | namespace URI of the node to remove; data encoding |
| `local`   | `IN`   | local name of the node to remove; data encoding    |

##### Returns

`(xmlnode *)` node removed from this map

**See Also:**

XmlDomRemoveNamedItem(), XmlDomGetNamedItem(), XmlDomGetNamedItemNS(), XmlDomSetNamedItem(), XmlDomSetNamedItemNS()

#### XmlDomSetNamedItem()

Adds a new node to a `NamedNodeMap`. If a node already exists with the given name, replaces the old node and returns it. If no such named node exists, adds the new node to the map and sets old to `NULL`. This is a non-namespace-aware function; it just matches (case sensitively) on the whole qualified name. Since some node types have fixed names (`Text`, `Comment`, and so on), trying to set another of the same type will always cause replacement.

##### Syntax

    xmlnode* XmlDomSetNamedItem(
       xmlctx *xctx,
       xmlnamedmap *map,
       xmlnode *newNode);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `xctx`    | `IN`   | XML context              |
| `map`     | `IN`   | `NamedNodeMap`           |
| `newNode` | `IN`   | new node to store in map |

##### Returns

`(xmlnode *)` the replaced node (or `NULL`)

**See Also:**

XmlDomSetNamedItemNS(), XmlDomGetNamedItem(), XmlDomGetNamedItemNS(), XmlDomGetNodeMapItem(), XmlDomGetNodeMapLength()

#### XmlDomSetNamedItemNS()

Adds a new node to a `NamedNodeMap`. If a node already exists with the given URI and localname, replaces the old node and returns it. If no such named node exists, adds the new node to the map and sets old to `NULL`. Since some node types have fixed names (`Text`, `Comment`, and so on), trying to set another of the same type will always cause replacement.

##### Syntax

    xmlnode* XmlDomSetNamedItemNS(
       xmlctx *xctx,
       xmlnamedmap *map,
       xmlnode *newNode);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `xctx`    | `IN`   | XML context              |
| `map`     | `IN`   | `NamedNodeMap`           |
| `newNode` | `IN`   | new node to store in map |

##### Returns

`(xmlnode *)` replaced `Node` \[or `NULL`\]

**See Also:**

XmlDomSetNamedItem(), XmlDomGetNamedItem(), XmlDomGetNamedItemNS(), XmlDomGetNodeMapItem(), XmlDomGetNodeMapLength()

### Node Interface for DOM XML C APIs

The following table summarizes the methods available through the `Node` interface of DOM for XML C APIs.

Table 3-8 Summary of Node DOM Methods for XML C Implementation

| Function                             | Summary                                                                                                   |
|:-------------------------------------|:----------------------------------------------------------------------------------------------------------|
| XmlDomAppendChild()                  | Append new child to node's list of children.                                                              |
| XmlDomCleanNode()                    | Clean a node (free DOM allocations).                                                                      |
| XmlDomCloneNode()                    | Clone a node.                                                                                             |
| XmlDomFreeNode()                     | Free a node allocated with `XmlDomCreateXXX`.                                                             |
| XmlDomGetAttrs()                     | Return attributes of node.                                                                                |
| XmlDomGetChildNodes()                | Return children of node.                                                                                  |
| XmlDomGetDefaultNS()                 | Get default namespace for node.                                                                           |
| XmlDomGetFirstChild()                | Returns first child of node.                                                                              |
| XmlDomGetFirstPfnsPair()             | Get first prefix namespace pair.                                                                          |
| XmlDomGetLastChild()                 | Returns last child of node.                                                                               |
| XmlDomGetNextPfnsPair()              | Get subsequent prefix namespace pair.                                                                     |
| XmlDomGetNextSibling()               | Return next sibling of node.                                                                              |
| XmlDomGetNodeLocal()                 | Get local part of node's qualified name as `NULL`-terminated string.                                      |
| XmlDomGetNodeLocalLen()              | Get local part of node's qualified name as length-encoded string.                                         |
| XmlDomGetNodeName()                  | Get node's name as `NULL`-terminated string.                                                              |
| XmlDomGetNodeNameLen()               | Get node's name as length-encoded string.                                                                 |
| XmlDomGetNodePrefix()                | Return namespace prefix of node.                                                                          |
| XmlDomGetNodeType()                  | Get node's numeric type code.                                                                             |
| XmlDomGetNodeURI()                   | Return namespace URI of node as a `NULL`-terminated string.                                               |
| XmlDomGetNodeURILen()                | Return namespace URI of node as length-encoded string.                                                    |
| XmlDomGetNodeValue()                 | Get node's value as `NULL`-terminated string.                                                             |
| XmlDomGetNodeValueLen()              | Get node value as length-encoded string.                                                                  |
| XmlDomGetNodeValueStream()           | Returns the large data for a node and sends it in pieces to the user's output stream.                     |
| XmlDomGetOwnerDocument()             | Get the owner document of node.                                                                           |
| XmlDomGetParentNode()                | Get parent node.                                                                                          |
| XmlDomGetPrevSibling()               | Return previous sibling of node.                                                                          |
| XmlDomGetPullNodeAsBinaryStream()    | Returns the address of a binary stream using the pull paradigm.                                           |
| XmlDomGetPullNodeAsCharacterStream() | Returns the address of a character stream using the pull paradigm.                                        |
| XmlDomGetPushNodeAsBinaryStream()    | Returns the address of a binary stream, as an `OUT ostream` parameter, using the push paradigm.           |
| XmlDomGetPushNodeAsCharacterStream() | Returns the address of a character stream, as an `OUT ostream` parameter, using the push paradigm.        |
| XmlDomGetSourceEntity()              | Return the entity node if the input file is an external entity.                                           |
| XmlDomGetSourceLine()                | Return source line number of node.                                                                        |
| XmlDomGetSourceLocation()            | Return source location (path, URI, and so on) of node.                                                    |
| XmlDomHasAttr()                      | Does named attribute exist?                                                                               |
| XmlDomHasChildNodes()                | Test if node has children.                                                                                |
| XmlDomInsertBefore()                 | Insert new child in to node's list of children.                                                           |
| XmlDomNormalize()                    | Normalize a node by merging adjacent text nodes.                                                          |
| XmlDomNumAttrs()                     | Return number of attributes of element.                                                                   |
| XmlDomNumChildNodes()                | Return number of children of node.                                                                        |
| XmlDomPrefixToURI()                  | Get namespace URI for prefix.                                                                             |
| XmlDomRemoveChild()                  | Remove an existing child node.                                                                            |
| XmlDomRenameNode()                   | Updates the name of a node, for element and attribute nodes only.                                         |
| XmlDomRenameNodeNS()                 | Updates the name and URI of a node, for element and attribute nodes only.                                 |
| XmlDomReplaceChild()                 | Replace an existing child of a node.                                                                      |
| XmlDomSetDefaultNS()                 | Set default namespace for node.                                                                           |
| XmlDomSetNodePrefix()                | Set namespace prefix of node.                                                                             |
| XmlDomSetNodeValue()                 | Set node value.                                                                                           |
| XmlDomSetNodeValueLen()              | Set node value as length-encoded string.                                                                  |
| XmlDomSetNodeValueStream()           | Sets the large "value" (character data) for a node piecemeal from an input stream.                        |
| XmlDomSetPullNodeAsBinaryStream()    | Returns the address of a binary input stream, as an `OUT istream` parameter, using the pull paradigm.     |
| XmlDomSetPullNodeAsCharacterStream() | Returns the address of an input character stream, as an `OUT istream` parameter, using the pull paradigm. |
| XmlDomSetPushNodeAsBinaryStream()    | Returns the address of an input binary stream using the push paradigm.                                    |
| XmlDomSetPushNodeAsCharacterStream() | Returns the address of a character stream using the push paradigm.                                        |
| XmlDomValidate()                     | Validate a node against current DTD.                                                                      |

#### XmlDomAppendChild()

Appends the node to the end of the parent's list of children and returns the new node. If `newChild` is a `DocumentFragment`, all of its children are appended in original order; the `DocumentFragment` node itself is not.

##### Syntax

    xmlnode* XmlDomAppendChild(
       xmlctx *xctx,
       xmlnode *parent,
       xmlnode *newChild);

| Parameter  | In/Out | Description                  |
|:-----------|:-------|:-----------------------------|
| `xctx`     | `IN`   | XML context                  |
| `parent`   | `IN`   | parent to receive a new node |
| `newChild` | `IN`   | node to add                  |

##### Returns

`(xmlnode *)` node added

**See Also:**

XmlDomInsertBefore(), XmlDomReplaceChild()

#### XmlDomCleanNode()

Frees parts of the node which were allocated by DOM itself, but does not recurse to children or touch the node's attributes. After freeing part of the node (such as name), a DOM call to get that part (such as `XmlDomGetNodeName`) should return a `NULL` pointer. Used to manage the allocations of a node parts of which are controlled by DOM, and part by the user. Calling clean frees all allocations may by DOM and leaves the user's allocations alone. The user is responsible for freeing their own allocations.

##### Syntax

    void XmlDomCleanNode(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description   |
|:----------|:-------|:--------------|
| `xctx`    | `IN`   | XML context   |
| `node`    | `IN`   | node to clean |

**See Also:**

XmlDomFreeNode()

#### XmlDomCloneNode()

Creates and returns a duplicate of a node. The duplicate node has no parent. Cloning an element copies all attributes and their values, including those generated by the XML processor to represent defaulted attributes, but it does not copy any text it contains unless it is a deep clone, since the text is contained in a child text node. Cloning any other type of node simply returns a copy of the node. Note that a clone of an unspecified attribute node is specified. If deep is `TRUE`, all children of the node are recursively cloned, and the cloned node will have cloned children; a non-deep clone will have no children.

##### Syntax

    xmlnode* XmlDomCloneNode(
       xmlctx *xctx,
       xmlnode *node,
       boolean deep);

| Parameter | In/Out | Description                          |
|:----------|:-------|:-------------------------------------|
| `xctx`    | `IN`   | XML context                          |
| `node`    | `IN`   | XML node                             |
| `deep`    | `IN`   | `TRUE` to recursively clone children |

##### Returns

`(xmlnode *)` duplicate (cloned) node

**See Also:**

XmlDomImportNode()

#### XmlDomFreeNode()

Free a node allocated with `XmlDomCreate``XXX`. Frees all resources associated with a node, then frees the node itself. Certain parts of the node are under DOM control, and some parts may be under user control. DOM keeps flags tracking who owns what, and only frees its own allocations. The user is responsible for freeing their own parts of the node before calling XmlDomFreeNode.

##### Syntax

    void XmlDomFreeNode(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `node`    | `IN`   | XML node to free |

**See Also:**

XmlDomCleanNode()

#### XmlDomGetAttrs()

Returns a `NamedNodeMap` of attributes of an element node, or `NULL` if it has no attributes. For other node types, `NULL` is returned. Note that if an element once had attributes, but they have all been removed, an empty list will be returned. So, presence of the list does not mean the element has attributes. You must check the size of the list with `XmlDomNumAttrs` or use `XmlDomHasChildNodes` first.

##### Syntax

    xmlnamedmap* XmlDomGetAttrs(
       xmlctx *xctx,
       xmlelemnode *elem);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `elem`    | `IN`   | XML element node |

##### Returns

`(xmlnamedmap *)` `NamedNodeMap` of node's attributes

**See Also:**

XmlDomNumAttrs(), XmlDomHasChildNodes()

#### XmlDomGetChildNodes()

Returns a list of the node's children, or `NULL` if it has no children. Only `Element`, `Document`, DTD, and `DocumentFragment` nodes may have children; all other types will return `NULL`.

Note that an empty list may be returned if the node once had children, but all have been removed! That is, the list may exist but have no members. So, presence of the list alone does not mean the node has children. You must check the size of the list with `XmlDomNumChildNodes` or use `XmlDomHasChildNodes` first.

The xmlnodelist structure is opaque and can only be manipulated with functions in the `NodeList` interface.

The returned list is live; all changes in the original node are reflected immediately.

##### Syntax

    xmlnodelist* XmlDomGetChildNodes(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnodelist *)` live `NodeList` containing all children of node

#### XmlDomGetDefaultNS()

Gets the default namespace for a node.

##### Syntax

    oratext* XmlDomGetDefaultNS(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `xctx`    | `IN`   | XML context                   |
| `node`    | `IN`   | element or attribute DOM node |

##### Returns

`(oratext *)` default namespace for node \[data encoding; may be `NULL`\]

#### XmlDomGetFirstChild()

Returns the first child of a node, or `NULL` if the node has no children. Only `Element`, `Document`, DTD, and `DocumentFragment` nodes may have children; all other types will return `NULL`.

##### Syntax

    xmlnode* XmlDomGetFirstChild(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnode *)` first child of node

**See Also:**

XmlDomGetLastChild(), XmlDomHasChildNodes(), XmlDomGetChildNodes(), XmlDomNumChildNodes()

#### XmlDomGetFirstPfnsPair()

This function is to allow implementations an opportunity to speedup the iteration of all available prefix-URI bindings available on a given node. It returns a state structure and the prefix and URI of the first prefix-URI mapping. The state structure should be passed to `XmlDomGetNextPfnsPair` on the remaining pairs.

##### Syntax

    xmlpfnspair* XmlDomGetFirstPfnsPair(
       xmlctx *xctx,
       xmlnode *node,
       oratext **prefix,
       oratext **uri);

| Parameter | In/Out | Description                            |
|:----------|:-------|:---------------------------------------|
| `xctx`    | `IN`   | XML context                            |
| `node`    | `IN`   | XML node                               |
| `prefix`  | `OUT`  | prefix of first mapping; data encoding |
| `uri`     | `OUT`  | URI of first mapping; data encoding    |

##### Returns

`(xmlpfnspair *)` iterating object or `NULL` of no prefixes

#### XmlDomGetLastChild()

Returns the last child of a node, or `NULL` if the node has no children. Only `Element`, `Document`, DTD, and `DocumentFragment` nodes may have children; all other types will return `NULL`.

##### Syntax

    xmlnode* XmlDomGetLastChild(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnode *)` last child of node

**See Also:**

XmlDomGetFirstChild(), XmlDomHasChildNodes(), XmlDomGetChildNodes(), XmlDomNumChildNodes()

#### XmlDomGetNextPfnsPair()

This function is to allow implementations an opportunity to speedup the iteration of all available prefix-URI bindings available on a given node. Given an iterator structure from `XmlDomGetFirstPfnsPair`, returns the next prefix-URI mapping; repeat calls to `XmlDomGetNextPfnsPair` until `NULL` is returned.

##### Syntax

    xmlpfnspair* XmlDomGetNextPfnsPair(
       xmlctx *xctx
       xmlpfnspair *pfns,
       oratext **prefix,
       oratext **uri);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `xctx`    | `IN`   | XML context                           |
| `node`    | `IN`   | XML node                              |
| `prefix`  | `OUT`  | prefix of next mapping; data encoding |
| `uri`     | `OUT`  | URI of next mapping; data encoding    |

##### Returns

`(xmlpfnspair *)` iterating object, `NULL` when no more pairs

#### XmlDomGetNextSibling()

Returns the node following a node at the same level in the DOM tree. That is, for each child of a parent node, the next sibling of that child is the child which comes after it. If a node is the last child of its parent, or has no parent, `NULL` is returned.

##### Syntax

    xmlnode* XmlDomGetNextSibling(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnode *)` node immediately following node at same level

**See Also:**

XmlDomGetPrevSibling()

#### XmlDomGetNodeLocal()

Returns the namespace local name for a node as a `NULL`-terminated string. If the node's name is not fully qualified (has no prefix), then the local name is the same as the name.

A length-encoded version is available as `XmlDomGetNodeLocalLen` which returns the local name as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetNodeLocal(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` local name of node \[data encoding\]

**See Also:**

XmlDomGetNodeLocalLen(), XmlDomGetNodePrefix(), XmlDomGetNodeURI()

#### XmlDomGetNodeLocalLen()

Returns the namespace local name for a node as a length-encoded string. If the node's name is not fully qualified (has no prefix), then the local name is the same as the name.

A `NULL`-terminated version is available as `XmlDomGetNodeLocal` which returns the local name as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the node's data will be stored internally as length-encoded. Using the length-based Get functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than buflen, then a truncated value will be copied into the buffer and len will return the actual length.

##### Syntax

    oratext* XmlDomGetNodeLocalLen(
       xmlctx *xctx,
       xmlnode *node,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                         |
|:----------|:-------|:------------------------------------|
| `xctx`    | `IN`   | XML context                         |
| `node`    | `IN`   | XML node                            |
| `buf`     | `IN`   | input buffer; optional              |
| `buflen`  | `IN`   | input buffer length; optional       |
| `len`     | `OUT`  | length of local name, in characters |

##### Returns

`(oratext *)` local name of node \[data encoding\]

**See Also:**

XmlDomGetNodeLocal(), XmlDomGetNodePrefix(), XmlDomGetNodeURILen()

#### XmlDomGetNodeName()

Returns the (fully-qualified) name of a node (in the data encoding) as a `NULL`-terminated string, for example `bar\0` or `foo:bar\0`.

Note that some node types have fixed names: "`#text`", "`#cdata-section`", "#`comment`", "`#document`", "`#document-fragment`".

A node's name cannot be changed once it is created, so there is no matching `SetNodeName` function.

A length-based version is available as `XmlDomGetNodeNameLen` which returns the node name as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetNodeName(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` name of node \[data encoding\]

**See Also:**

XmlDomGetNodeNameLen()

#### XmlDomGetNodeNameLen()

Returns the (fully-qualified) name of a node (in the data encoding) as a length-encoded string, for example `"bar", 3` or `"foo:bar", 7`.

Note that some node types have fixed names: "`#text`", "`#cdata-section`", "`#comment`", "`#document`", "`#document-fragment`".

A node's name cannot be changed once it is created, so there is no matching SetNodeName function.

A `NULL`-terminated version is available as XmlDomGetNodeName which returns the node name as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the node's name will be stored internally as length-encoded. Using the length-encoded `Get``XXX` functions will avoid having to copy and `NULL`-terminate the name.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than buflen, then a truncated value will be copied into the buffer and `len` will return the actual length.

##### Syntax

    oratext* XmlDomGetNodeNameLen(
       xmlctx *xctx,
       xmlnode *node,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `xctx`    | `IN`   | XML context                   |
| `node`    | `IN`   | XML node                      |
| `buf`     | `IN`   | input buffer; optional        |
| `buflen`  | `IN`   | input buffer length; optional |
| `len`     | `OUT`  | length of name, in characters |

##### Returns

`(oratext *)` name of node, with length of name set in 'len'

**See Also:**

XmlDomGetNodeName()

#### XmlDomGetNodePrefix()

Returns the namespace prefix for a node (as a `NULL`-terminated string). If the node's name is not fully qualified (has no prefix), `NULL` is returned.

##### Syntax

    oratext* XmlDomGetNodePrefix(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` namespace prefix of node \[data encoding; may be `NULL`\]

#### XmlDomGetNodeType()

Returns the type code of a node. The type names and numeric values match the DOM specification:

- `ELEMENT_NODE=1`

- `ATTRIBUTE_NODE=2`

- `TEXT_NODE=3`

- `CDATA_SECTION_NODE=4`

- `ENTITY_REFERENCE_NODE=5`

- `ENTITY_NODE=6`

- `PROCESSING_INSTRUCTION_NODE=7`

- `COMMENT_NODE=8`

- `DOCUMENT_NODE=9`

- `DOCUMENT_TYPE_NODE=10`

- `DOCUMENT_FRAGMENT_NODE=11`

- `NOTATION_NODE=12`

Additional Oracle extension node types are as follows:

- `ELEMENT_DECL_NODE`

- `ATTR_DECL_NODE`

- `CP_ELEMENT_NODE`

- `CP_CHOICE_NODE`

- `CP_PCDATA_NODE`

- `CP_STAR_NODE`

- `CP_PLUS_NODE`

- `CP_OPT_NODE`

##### Syntax

    xmlnodetype XmlDomGetNodeType(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnodetype)` numeric type-code of the node

#### XmlDomGetNodeURI()

Returns the namespace URI for a node (in the data encoding) as a `NULL`-terminated string. If the node's name is not qualified (does not contain a namespace prefix), it will have the default namespace in effect when the node was created (which may be `NULL`).

A length-encoded version is available as `XmlDomGetNodeURILen` which returns the URI as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetNodeURI(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` namespace URI of node \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetNodeURILen(), XmlDomGetNodePrefix(), XmlDomGetNodeLocal()

#### XmlDomGetNodeURILen()

Returns the namespace URI for a node (in the data encoding) as length-encoded string. If the node's name is not qualified (does not contain a namespace prefix), it will have the default namespace in effect when the node was created (which may be `NULL`).

A `NULL`-terminated version is available as `XmlDomGetNodeURI` which returns the URI value as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the node's data will be stored internally as length-encoded. Using the length-based Get functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than buflen, then a truncated value will be copied into the buffer and `len` will return the actual length.

##### Syntax

    oratext* XmlDomGetNodeURILen(
       xmlctx *xctx,
       xmlnode *node,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `xctx`    | `IN`   | XML context                   |
| `node`    | `IN`   | XML node                      |
| `buf`     | `IN`   | input buffer; optional        |
| `buflen`  | `IN`   | input buffer length; optional |
| `len`     | `OUT`  | length of URI, in characters  |

##### Returns

`(oratext *)` namespace URI of node \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetNodeURI(), XmlDomGetNodePrefix(), XmlDomGetNodeLocal()

#### XmlDomGetNodeValue()

Returns the "value" (associated character data) for a node as a `NULL`-terminated string. Character and general entities will have been replaced. Only `Attr`, `CDATA`, `Comment`, `ProcessingInstruction` and `Text` nodes have values, all other node types have `NULL` value.

A length-encoded version is available as `XmlDomGetNodeValueLen` which returns the node value as a pointer and length, for use if the data is known to use `XMLType` backing store.

##### Syntax

    oratext* XmlDomGetNodeValue(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` value of node

**See Also:**

XmlDomSetNodeValue(), XmlDomGetNodeValueLen()

#### XmlDomGetNodeValueLen()

Returns the "value" (associated character data) for a node as a length-encoded string. Character and general entities will have been replaced. Only `Attr`, `CDATA`, `Comment`, PI and `Text` nodes have values, all other node types have `NULL` value.

A `NULL`-terminated version is available as `XmlDomGetNodeValue` which returns the node value as `NULL`-terminated string. If the backing store is known to be `XMLType`, then the node's data will be stored internally as length-encoded. Using the length-based Get functions will avoid having to copy and `NULL`-terminate the data.

If both the input buffer is non-`NULL` and the input buffer length is nonzero, then the value will be stored in the input buffer. Else, the implementation will return its own buffer.

If the actual length is greater than `buflen`, then a truncated value will be copied into the buffer and len will return the actual length.

##### Syntax

    oratext* XmlDomGetNodeValueLen(
       xmlctx *xctx,
       xmlnode *node,
       oratext *buf,
       ub4 buflen,
       ub4 *len);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `xctx`    | `IN`   | XML context                   |
| `node`    | `IN`   | XML node                      |
| `buf`     | `IN`   | input buffer; optional        |
| `buflen`  | `IN`   | input buffer length; optional |
| `len`     | `OUT`  | length of value, in bytes     |

##### Returns

`(oratext *)` value of node

**See Also:**

XmlDomSetNodeValueLen(), XmlDomGetNodeValue()

#### XmlDomGetNodeValueStream()

Returns the large data for a node and sends it in pieces to the user's output stream. For very large values, it is not always possible to store them \[efficiently\] as a single contiguous chunk. This function is used to access chunked data of that type. Only `XMLType` chunks its data (sometimes); XDK's data is always contiguous.

##### Syntax

    xmlerr XmlDomGetNodeValueStream(
       xmlctx *xctx,
       xmlnode *node,
       xmlostream *ostream);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `xctx`    | `IN`   | XML context          |
| `node`    | `IN`   | XML node             |
| `ostream` | `IN`   | output stream object |

##### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XmlDomSetNodeValueStream(), XmlDomGetNodeValue(), XmlDomGetNodeValueLen()

#### XmlDomGetOwnerDocument()

Returns the `Document` node associated with a node. Each node may belong to only one document, or may not be associated with any document at all (such as immediately after `XmlDomCreateElem`, and so on). The "owning" document \[node\] is returned, or `NULL` for an orphan node.

##### Syntax

    xmldocnode* XmlDomGetOwnerDocument(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmldocnode *)` document node is in

#### XmlDomGetParentNode()

Returns a node's parent node. All nodes types except `Attr`, `Document`, `DocumentFragment`, `Entity`, and `Notation` may have a parent (these five exceptions always have a `NULL` parent). If a node has just been created but not yet added to the DOM tree, or if it has been removed from the DOM tree, its parent is also `NULL`.

##### Syntax

    xmlnode* XmlDomGetParentNode(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnode *)` parent of node

#### XmlDomGetPrevSibling()

Returns the node preceding a node at the same level in the DOM tree. That is, for each child of a parent node, the previous sibling of that child is the child which came before it. If a node is the first child of its parent, or has no parent, `NULL` is returned.

##### Syntax

    xmlnode* XmlDomGetPrevSibling(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlnode *)` node immediately preceding node at same level

**See Also:**

XmlDomGetNextSibling()

#### XmlDomGetPullNodeAsBinaryStream()

Returns the address of a binary stream using the pull paradigm.

##### Syntax

    orastream *XmlDomGetPullNodeAsBinaryStream(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                                                             |
|:----------|:-------|:------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                             |
| `node`    | `IN`   | XML node; may be `RAW` or `BLOB`, otherwise the function returns `NULL` |

##### Returns

`(orastream *)` the readable binary stream; use `OraStreamRead()` on the output, not `OraStreamReadChar()`

#### XmlDomGetPullNodeAsCharacterStream()

Returns the address of a character stream using the pull paradigm.

##### Syntax

    orastream *XmlDomGetPullNodeAsCharacterStream(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `node`    | `IN`   | XML node; may be any type supported by XML DB |

##### Returns

`(orastream *)` the readable character stream; use `OraStreamReadChar()` on the output, not `OraStreamRead()`.

#### XmlDomGetPushNodeAsBinaryStream()

Returns the address of a binary stream, as an `OUT ostream` parameter, using the push paradigm.

##### Syntax

    xmlerr XmlDomGetPushNodeAsBinaryStream(
       xmlctx *xctx,
       xmlnode *node,
       orastream *ostream);

| Parameter | In/Out | Description                                                                                                      |
|:----------|:-------|:-----------------------------------------------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                                                                      |
| `node`    | `IN`   | XML node; may be `RAW` or `BLOB`, otherwise returns an error                                                     |
| `ostream` | `OUT`  | application implementation of `orastream`; use `OraStreamWrite()` to write the value, not `OraStreamWriteChar()` |

##### Returns

`(xmlerr *)` error code, `XMLERR_OK []` on success

#### XmlDomGetPushNodeAsCharacterStream()

Returns the address of a character stream, as an `OUT ostream` parameter, using the push paradigm.

##### Syntax

    xmlerr XmlDomGetPushNodeAsCharacterStream(
       xmlctx *xctx,
       xmlnode *node,
       orastream *ostream);

| Parameter | In/Out | Description                                                                                                      |
|:----------|:-------|:-----------------------------------------------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                                                                      |
| `node`    | `IN`   | XML node; any type supported by XML DB                                                                           |
| `ostream` | `IN`   | application implementation of `orastream`; use `OraStreamWriteChar()` to write the value, not `OraStreamWrite()` |

##### Returns

`(xmlerr *)` error code, `XMLERR_OK []` on success

#### XmlDomGetSourceEntity()

Returns the external entity node whose inclusion caused the creation of the given node.

##### Syntax

    xmlentnode* XmlDomGetSourceEntity(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(xmlentnode *)` entity node if the input is from an external entity

#### XmlDomGetSourceLine()

Returns the line# in the original source where the node started. The first line in every input is line \#1.

##### Syntax

    ub4 XmlDomGetSourceLine(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(ub4)` line number of node in original input source

#### XmlDomGetSourceLocation()

Return source location (path, URI, and so on) of node. Note this will be in the compiler encoding, not the data encoding!

##### Syntax

    oratext* XmlDomGetSourceLocation(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(oratext *)` full path of input source \[in compiler encoding\]

#### XmlDomHasAttrs()

Test if an element has attributes. Returns `TRUE` if any attributes of any sort are defined (namespace or regular).

##### Syntax

    boolean XmlDomHasAttrs(
       xmlctx *xctx,
       xmlelemnode *elem);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `elem`    | `IN`   | XML element node |

##### Returns

`(boolean)` `TRUE` if element has attributes

#### XmlDomHasChildNodes()

Test if a node has children. Only `Element`, `Document`, DTD, and `DocumentFragment` nodes may have children. Note that just because `XmlDomGetChildNodes` returns a list does not mean the node actually has children, since the list may be empty, so a non-`NULL` return from `XmlDomGetChildNodes` should not be used as a test.

##### Syntax

    boolean XmlDomHasChildNodes(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(boolean)` `TRUE` if the node has any children

#### XmlDomInsertBefore()

Inserts the node `newChild` before the existing child node `refChild` in the parent node. If `refChild` is `NULL`, appends to parent's children as for each `XmlDomAppendChild`; otherwise it must be a child of the given parent. If `newChild` is a `DocumentFragment`, all of its children are inserted (in the same order) before` refChild`; the `DocumentFragment` node itself is not. If `newChild` is already in the DOM tree, it is first removed from its current position.

##### Syntax

    xmlnode* XmlDomInsertBefore(
       xmlctx *xctx,
       xmlnode *parent,
       xmlnode *newChild,
       xmlnode *refChild);

| Parameter  | In/Out | Description                      |
|:-----------|:-------|:---------------------------------|
| `xctx`     | `IN`   | XML context                      |
| `parent`   | `IN`   | parent that receives a new child |
| `newChild` | `IN`   | node to insert                   |
| `refChild` | `IN`   | reference node                   |

##### Returns

`(xmlnode *)` node being inserted

**See Also:**

XmlDomAppendChild(), XmlDomReplaceChild(), XmlDomRemoveChild()

#### XmlDomNormalize()

Normalizes the subtree rooted at an element, merges adjacent `Text` nodes children of elements. Note that adjacent `Text` nodes will never be created during a normal parse, only after manipulation of the document with DOM calls.

##### Syntax

    void XmlDomNormalize(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

#### XmlDomNumAttrs()

Returns the number of attributes of an element. Note that just because a list is returned by `XmlDomGetAttrs` does not mean it contains any attributes; it may be an empty list with zero length.

##### Syntax

    ub4 XmlDomNumAttrs(
       xmlctx *xctx,
       xmlelemnode *elem);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `elem`    | `IN`   | XML element node |

##### Returns

`(ub4)` number of attributes of node

#### XmlDomNumChildNodes()

Returns the number of children of a node. Only `Element`, `Document`, DTD, and `DocumentFragment` nodes may have children, all other types return 0. Note that just because `XmlDomGetChildNodes` returns a list does not mean that it contains any children; it may be an empty list with zero length.

##### Syntax

    ub4 XmlDomNumChildNodes(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `node`    | `IN`   | XML node    |

##### Returns

`(ub4)` number of children of node

#### XmlDomPrefixToURI()

Given a namespace prefix and a node, returns the namespace URI mapped to that prefix. If the given node doesn't have a matching prefix, its parent is tried, then its parent, and so on, all the way to the root node. If the prefix is undefined, `NULL` is returned.

##### Syntax

    oratext* XmlDomPrefixToURI(
       xmlctx *xctx,
       xmlnode *node,
       oratext *prefix);

| Parameter | In/Out | Description   |
|:----------|:-------|:--------------|
| `xctx`    | `IN`   | XML context   |
| `node`    | `IN`   | XML node      |
| `prefix`  | `IN`   | prefix to map |

##### Returns

`(oratext *)` URI for prefix \[data encoding; `NULL` if no match\]

#### XmlDomRemoveChild()

Removes a node from its parent's list of children and returns it. The node is orphaned; its parent will be `NULL` after removal.

##### Syntax

    xmlnode* XmlDomRemoveChild(
       xmlctx *xctx,
       xmlnode *oldChild);

| Parameter  | In/Out | Description    |
|:-----------|:-------|:---------------|
| `xctx`     | `IN`   | XML context    |
| `oldChild` | `IN`   | node to remove |

##### Returns

`(xmlnode *)` node removed

**See Also:**

XmlDomAppendChild(), XmlDomInsertBefore(), XmlDomReplaceChild()

#### XmlDomRenameNode()

Updates the name of a node, for element and attribute nodes only.

If the prefix does not have a current mapping, the user should add the mapping by creating an `xmlns` attribute and associating it with this element node by calling XmlDomSetAttrNodeNS()XmlDomSetAttrNodeNS(). A namespace attribute node cannot be modified.

##### Syntax

    xmlnode* XmlDomRenameNode(
       xmlctx *xctx,
       xmlnode *node,
       oratext *tagname);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `xctx`    | `IN`   | XML context     |
| `node`    | `IN`   | XML node        |
| `tagname` | `IN`   | The new tagname |

##### Returns

`(xmlnode *)` the changed node

**See Also:**

XmlDomSetAttrNodeNS()

#### XmlDomRenameNodeNS()

Updates the name and URI of a node, for element and attribute nodes only.

If the prefix does not have a current mapping, the user should add the mapping by creating an `xmlns` attribute and associating it with this element node by calling XmlDomSetAttrNodeNS()XmlDomSetAttrNodeNS(). A namespace attribute node cannot be modified.

##### Syntax

    xmlnode* XmlDomRenameNodeNS(
       xmlctx *xctx,
       xmlnode *node,
       oratext *uri,
       oratext *tagname);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `node`    | `IN`   | XML node                                     |
| `uri`     | `IN`   | The new URI; if `NULL`, retains existing URI |
| `tagname` | `IN`   | The new tagname                              |

##### Returns

`(xmlnode *)` the changed node.

**See Also:**

XmlDomSetAttrNodeNS()

#### XmlDomReplaceChild()

Replaces the child node `oldChild` with the new node `newChild` in `oldChild`'s parent, and returns `oldChild` (which is now orphaned, with a `NULL` parent). If `newChild` is a `DocumentFragment`, all of its children are inserted in place of `oldChild`; the `DocumentFragment` node itself is not. If `newChild` is already in the DOM tree, it is first removed from its current position.

##### Syntax

    xmlnode* XmlDomReplaceChild(
       xmlctx *xctx,
       xmlnode *newChild,
       xmlnode *oldChild);

| Parameter  | In/Out | Description                  |
|:-----------|:-------|:-----------------------------|
| `xctx`     | `IN`   | XML context                  |
| `newChild` | `IN`   | new node that is substituted |
| `oldChild` | `IN`   | old node that is replaced    |

##### Returns

`(xmlnode *)` node replaced

**See Also:**

XmlDomAppendChild(), XmlDomInsertBefore(), XmlDomRemoveChild()

#### XmlDomSetDefaultNS()

Set the default namespace for a node

##### Syntax

    void XmlDomSetDefaultNS(
       xmlctx *xctx,
       xmlnode *node,
       oratext *defns);

| Parameter | In/Out | Description                        |
|:----------|:-------|:-----------------------------------|
| `xctx`    | `IN`   | XML context                        |
| `node`    | `IN`   | element or attribute DOM node      |
| `defns`   | `IN`   | new default namespace for the node |

#### XmlDomSetNodePrefix()

Sets the namespace prefix of node (as `NULL`-terminated string). Does not verify the prefix is defined. Just causes a new qualified name to be formed from the new prefix and the old local name; the new qualified name will be under DOM control and should not be managed by the user.

##### Syntax

    void XmlDomSetNodePrefix(
       xmlctx *xctx,
       xmlnode *node,
       oratext *prefix);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `xctx`    | `IN`   | XML context          |
| `node`    | `IN`   | XML node             |
| `prefix`  | `OUT`  | new namespace prefix |

#### XmlDomSetNodeValue()

Sets a node's value (character data) as a `NULL`-terminated string. Does not allow setting the value to `NULL`. Only `Attr`, `CDATA`, `Comment`, PI and `Text` nodes have values; trying to set the value of another type of node is a no-op. The new value must be in the data encoding. It is not verified, converted, or checked.

The value is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    xmlerr XmlDomSetNodeValue(
       xmlctx *xctx,
       xmlnode *node,
       oratext *value);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `node`    | `IN`   | XML node                                      |
| `value`   | `IN`   | node's new value; data encoding; user control |

##### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XmlDomGetNodeValue(), XmlDomSetNodeValueLen()

#### XmlDomSetNodeValueLen()

Sets the value (associated character data) for a node as a length-encoded string.

A `NULL`-terminated version is available as `XmlDomSetNodeValue` which takes the node value as a `NULL`-terminated string. If the backing store is known to be `XMLType`, then the node's data will be stored internally as length-encoded. Using the length-based Set functions will avoid having to copy and `NULL`-terminate the data.

##### Syntax

    xmlerr XmlDomSetNodeValueLen(
       xmlctx *xctx,
       xmlnode *node,
       oratext *value,
       ub4 len);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `xctx`    | `IN`   | XML context                                   |
| `node`    | `IN`   | XML node                                      |
| `value`   | `IN`   | node's new value; data encoding; user control |
| `len`     | `IN`   | length of value, in bytes                     |

##### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XmlDomSetNodeValueLen(), XmlDomSetNodeValue()

#### XmlDomSetNodeValueStream()

Sets the large "value" (character data) for a node piecemeal from an input stream. For very large values, it is not always possible to store them \[efficiently\] as a single contiguous chunk. This function is used to store chunked data of that type. Used only for `XMLType` data; XDK's data is always contiguous.

##### Syntax

    xmlerr XmlDomSetNodeValueStream(
       xmlctx *xctx,
       xmlnode *node,
       xmlistream *istream);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `xctx`    | `IN`   | XML context         |
| `node`    | `IN`   | XML node            |
| `istream` | `IN`   | input stream object |

##### Returns

`(xmlerr)` numeric error code, `0` on success

**See Also:**

XmlDomGetNodeValueStream(), XmlDomSetNodeValue()

#### XmlDomSetPullNodeAsBinaryStream()

Returns the address of a binary input stream, as an `OUT istream` parameter, using the pull paradigm.

##### Syntax

    xmlerr *XmlDomSetPullNodeAsBinaryStream(
       xmlctx *xctx,
       xmlnode *node
       orastream *istream);

| Parameter | In/Out | Description                                                                                                  |
|:----------|:-------|:-------------------------------------------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                                                                  |
| `node`    | `IN`   | XML node; may be `RAW` or `BLOB`, otherwise returns an error                                                 |
| `istream` | `OUT`  | input stream object; the method `OraStreamRead()` must be used to read this value, not `OraStreamReadChar()` |

##### Returns

`(xmlerr *)` error code, `XMLERR_OK []` on success

#### XmlDomSetPullNodeAsCharacterStream()

Returns the address of an input character stream, as an `OUT istream` parameter, using the pull paradigm.

##### Syntax

    xmlerr *XmlDomSetPullNodeAsCharacterStream(
       xmlctx *xctx,
       xmlnode *node
       orcharacterinputstream *istream);

| Parameter | In/Out | Description                                                                                                   |
|:----------|:-------|:--------------------------------------------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                                                                   |
| `node`    | `IN`   | XML node; may be any type supported by XML DB                                                                 |
| `istream` | `OUT`  | input stream object; the method `OraStreamReadChar()` must be used to read this value, not `OraStreamRead()`. |

##### Returns

`(xmlerr *)` error code, `XMLERR_OK []` on success

#### XmlDomSetPushNodeAsBinaryStream()

Returns the address of an input binary stream using the push paradigm.

##### Syntax

    orastream* XmlDomSetPushNodeAsBinaryStream(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                      |
|:----------|:-------|:---------------------------------|
| `xctx`    | `IN`   | XML context                      |
| `node`    | `IN`   | XML node; may be `RAW` or `BLOB` |

##### Returns

`(orastream *)` the binary stream; to read the output, use `OraStreamWrite()` instead of `OraStreamWriteChar()`

#### XmlDomSetPushNodeAsCharacterStream()

Returns the address of a character stream using the push paradigm.

##### Syntax

    orastream *XmlDomSetPushNodeAsCharacterStream(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description                            |
|:----------|:-------|:---------------------------------------|
| `xctx`    | `IN`   | XML context                            |
| `node`    | `IN`   | XML node; any type supported by XML DB |

##### Returns

`(orastream *)` the character stream; to read the output, use `OraStreamWriteChar()` instead of `OraStreamWrite()`

#### XmlDomValidate()

Given a root node, validates it against the current DTD.

##### Syntax

    xmlerr XmlDomValidate(
       xmlctx *xctx,
       xmlnode *node);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `node`    | `IN`   | node to validate |

##### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` means node is valid

### NodeList Interface for DOM XML C APIs

The following table summarizes the methods available through the `NodeList` interface of DOM for XML C APIs.

Table 3-9 Summary of NodeList DOM Methods for XML C Implementation

| Function                  | Summary                                                      |
|:--------------------------|:-------------------------------------------------------------|
| XmlDomFreeNodeList()      | Free a node list returned by XmlDomGetElemsByTag, and so on. |
| XmlDomGetNodeListItem()   | Return n<sup>th</sup> node in list.                          |
| XmlDomGetNodeListLength() | Return length of node list.                                  |

#### XmlDomFreeNodeList()

Free a node list returned by `XmlDomGetElemsByTag` or related functions, releasing all resources associated with it. If given a node list that is part of the DOM proper (such as the children of a node), does nothing.

##### Syntax

    void XmlDomFreeNodeList(
       xmlctx *xctx,
       xmlnodelist *list);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `xctx`    | `IN`   | XML context        |
| `list`    | `IN`   | `NodeList` to free |

**See Also:**

XmlDomGetElemsByTag(), XmlDomGetElemsByTagNS(), XmlDomGetChildrenByTag(), XmlDomGetChildrenByTagNS()

#### XmlDomGetNodeListItem()

Return nth node in a node list. The first item is index `0`.

##### Syntax

    xmlnode* XmlDomGetNodeListItem(
       xmlctx *xctx,
       xmlnodelist *list,
       ub4 index);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `list`    | `IN`   | `NodeList`        |
| `index`   | `IN`   | index into `list` |

##### Returns

`(xmlnode *)` node at the nth position in node list \[or `NULL`\]

**See Also:**

XmlDomGetNodeListLength(), XmlDomFreeNodeList()

#### XmlDomGetNodeListLength()

Returns the number of nodes in a node list (its length). Note that nodes are referred to by index, so the range of valid indexes is `0` through `length-1`.

##### Syntax

    ub4 XmlDomGetNodeListLength(
       xmlctx *xctx,
       xmlnodelist *list);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |
| `list`    | `IN`   | `NodeList`  |

##### Returns

`(ub4)` number of nodes in node list

**See Also:**

XmlDomGetNodeListItem(), XmlDomFreeNodeList()

### Notation Interface for DOM XML C APIs

The following table summarizes the methods available through the `Notation` interface of DOM for XML C APIs.

Table 3-10 Summary of NodeList DOM Methods for XML C Implementation

| Function                 | Summary                   |
|:-------------------------|:--------------------------|
| XmlDomGetNotationPubID() | Get notation's public ID  |
| XmlDomGetNotationSysID() | Get notation's system ID. |

#### XmlDomGetNotationPubID()

Return a notation's public identifier (in the data encoding).

##### Syntax

    oratext* XmlDomGetNotationPubID(
       xmlctx *xctx,
       xmlnotenode *note);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `xctx`    | `IN`   | XML context     |
| `note`    | `IN`   | `Notation` node |

##### Returns

`(oratext *)` notation's public identifier \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetNotationSysID()

#### XmlDomGetNotationSysID()

Return a notation's system identifier (in the data encoding).

##### Syntax

    oratext* XmlDomGetNotationSysID(
       xmlctx *xctx,
       xmlnotenode *note);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `xctx`    | `IN`   | XML context     |
| `note`    | `IN`   | `Notation` node |

##### Returns

`(oratext *)` notation's system identifier \[data encoding; may be `NULL`\]

**See Also:**

XmlDomGetNotationPubID()

### ProcessingInstruction Interface for DOM XML C APIs

The following table summarizes the methods available through the `ProcessingInstruction` interface of DOM for XML C APIs.

Table 3-11 Summary of ProcessingInstruction DOM Package Methods for XML C Implementation

| Function            | Summary                            |
|:--------------------|:-----------------------------------|
| XmlDomGetPIData()   | Get processing instruction's data. |
| XmlDomGetPITarget() | Get PI's target.                   |
| XmlDomSetPIData()   | Set processing instruction's data. |

#### XmlDomGetPIData()

Returns the content (data) of a processing instruction (in the data encoding). If the node is not a `ProcessingInstruction`, returns `NULL`. The content is the part from the first non-whitespace character after the target until the ending "`?>`".

##### Syntax

    oratext* XmlDomGetPIData(
       xmlctx *xctx,
       xmlpinode *pi);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `xctx`    | `IN`   | XML context                  |
| `pi`      | `IN`   | `ProcessingInstruction` node |

##### Returns

`(oratext *)` processing instruction's data \[data encoding\]

**See Also:**

XmlDomGetPITarget(), XmlDomSetPIData()

#### XmlDomGetPITarget()

Returns a processing instruction's target string. If the node is not a `ProcessingInstruction`, returns `NULL`. The target is the first token following the markup that begins the `ProcessingInstruction`. All `ProcessingInstruction`s must have a target, though the data part is optional.

##### Syntax

    oratext* XmlDomGetPITarget(
       xmlctx *xctx,
       xmlpinode *pi);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `xctx`    | `IN`   | XML context                  |
| `pi`      | `IN`   | `ProcessingInstruction` node |

##### Returns

`(oratext *)` processing instruction's target \[data encoding\]

**See Also:**

XmlDomGetPIData(), XmlDomSetPIData()

#### XmlDomSetPIData()

Sets a `ProcessingInstruction`'s content, which must be in the data encoding. It is not permitted to set the data to `NULL`. If the node is not a `ProcessingInstruction`, does nothing. The new data is not verified, converted, or checked.

##### Syntax

    void XmlDomSetPIData(
       xmlctx *xctx,
       xmlpinode *pi,
       oratext *data);

| Parameter | In/Out | Description                                       |
|:----------|:-------|:--------------------------------------------------|
| `xctx`    | `IN`   | XML context                                       |
| `pi`      | `IN`   | `ProcessingInstruction` node                      |
| `data`    | `IN`   | `ProcessingInstruction`'s new data; data encoding |

**See Also:**

XmlDomGetPITarget(), XmlDomGetPIData()

### Text Interface for DOM XML C APIs

The following table summarizes the methods available through the `Text` interface of DOM for XML C APIs.

Table 3-12 Summary of Text DOM Methods for XML C Implementation

| Function          | Summary                    |
|:------------------|:---------------------------|
| XmlDomSplitText() | Split text node in to two. |

#### XmlDomSplitText()

Splits a single text node into two text nodes; the original data is split between them. If the given node is not type text, or the offset is outside of the original data, does nothing and returns `NULL`. The offset is zero-based, and is in characters, not bytes. The original node is retained, its data is just truncated. A new text node is created which contains the remainder of the original data, and is inserted as the next sibling of the original. The new text node is returned.

##### Syntax

    xmltextnode* XmlDomSplitText(
       xmlctx *xctx,
       xmltextnode *textnode,
       ub4 offset);

| Parameter  | In/Out | Description                                      |
|:-----------|:-------|:-------------------------------------------------|
| `xctx`     | `IN`   | XML context                                      |
| `textnode` | `IN`   | `Text` node                                      |
| `offset`   | `IN`   | `0`-based character count at which to split text |

##### Returns

`(xmltextnode *)` new text node

**See Also:**

XmlDomGetCharData(), XmlDomAppendData(), XmlDomInsertData(), XmlDomDeleteData(), XmlDomReplaceData()
