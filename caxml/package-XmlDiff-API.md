The methods of the package `XmlDiff` allow you to compare and modify XML documents. The XmlDiff() and XmlPatch() methods are generally equivalent to UNIX commands `diff` and `patch`, and in addition are optimized for, and aware of, XML.

The following table summarizes the methods available through the `XmlDiff` package for XML C APIs.

Table 12-1 Summary of XmlDiff Methods for XML C Implementation

| Function   | Summary                                                     |
|:-----------|:------------------------------------------------------------|
| XmlDiff()  | Determines the changes between two XML documents.           |
| XmlHash()  | Computes a hash value for an XML document or a node in DOM. |
| XmlPatch() | Applies changes on input XML document.                      |

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/determining-XML-differences-using-C.md)

### XmlDiff()

Determines the changes between two XML documents.

XmlDiff() captures the `diff` between two documents in an XML format that conforms to the `Xdiff` XML schema; you can customize this output.

These input documents can be specified either as DOM Trees, files, URI, `orastream`, and so on. DOM trees for both the inputs will be created if they are not supplied as DOM trees. The DOM for the diff document is created, and the doc node is returned.

If the caller supplies inputs as DOMs, the memory for the DOMs will not be freed.

Data (DOM) encoding of both documents must be the same as the data encoding in `xctx`. The diff DOM will be created in the data encoding specified in `xctx`.

There are four algorithms that can be run in XmlDiff(): global, local, global with hashing, and local with hashing. The `diff` may be different in the four cases.

The global algorithm will generate minimal `diff` using insert, append, delete and update operations. It needs more memory and time than the local algorithm. The local algorithm may not generate minimal diff, but is faster and uses less space than the global algorithm.

Hashing can be used with both global and local algorithms. If hashing is used with the global algorithm, it will speed up diff computation significantly, but may reduce the quality of diff. With local algorithm, it improves the quality of the `diff`.

You must specify a depth at which to use hashing. In hashing, the hash value for every element node is associated with a digest for the entire subtree rooted at that node. The tree is not investigated beyond the specified hash level depth while computing the `diff`.

The output of the global algorithm with or without hashing meets 'operations-in-docorder' requirement (the nodes must appear in same order as a preorder traversal of the document tree), but the output of the local algorithm does not.

The namespace prefixes XmlDiff() will use in the `xdiff` document may be same as those in either the first or second `doc`, depending on which prefix was seen first while processing. The NS URI will be bound to the prefix in the output appropriately. If this NS does not have a prefix in both `doc`s, a new prefix will be generated and bound to the NS in `xdiff` `doc.`

#### Syntax

    xmldocnode *XmlDiff(
       xmlctx *xctx,
       xmlerr *err,
       ub4  flags,
       xmldfsrct firstSourceType,
       void *firstSource,
       void *firstSourceExtra,
       xmldfsrct secondSourceType,
       void *secondSource,
       void *secondSourceExtra,
       uword hashLevel,
       oraprop *properties);

| Parameter           | In/Out | Description                                                                                                                                                                                                                                                                                                                                |
|:--------------------|:-------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `xctx`              | `IN`   | XML context                                                                                                                                                                                                                                                                                                                                |
| `xmlerr`            | `OUT`  | numeric error code, `XMLERR_OK` on success                                                                                                                                                                                                                                                                                                 |
| `flags`             | `IN`   | The following options are available:<br>• `XMLDF_FL_DEFAULTS(=0)` chooses defaults<br>• `XMLDF_FL_ALGORITHM_GLOBAL` is the global algorithm<br>• `XMLDF_FL_ALGORITHM_LOCAL` is the local algorithm<br>• `XMLDF_FL_DISABLE_UPDATE` indicates a disable update operation, with the global algorithm<br>By default, global algorithm is used. |
| `firstSourceType`   | `IN`   | Type of source for first document; if zero, `firstSource` is assumed to be a DOM doc node.                                                                                                                                                                                                                                                 |
| `firstSource`       | `IN`   | Pointer to the source for the first document                                                                                                                                                                                                                                                                                               |
| `firstSourceExtra`  | `IN`   | An additional pointer to the source for the first document; used for buffer length pointer                                                                                                                                                                                                                                                 |
| `secondSourceType`  | `IN`   | Type of source for second document; if zero, `secondSource` is assumed to be a DOM doc node.                                                                                                                                                                                                                                               |
| `secondSource`      | `IN`   | Pointer to the source for the second document                                                                                                                                                                                                                                                                                              |
| `secondSourceExtra` | `IN`   | An additional pointer to the source for the second document; used for buffer length pointer                                                                                                                                                                                                                                                |
| `hashLevel`         | `IN`   | The depth (counting from `1` for the root) at which to use hashing for sub trees; `<=1` means not to use hashing                                                                                                                                                                                                                           |
| `properties`        | `IN`   | Used for Output Builder                                                                                                                                                                                                                                                                                                                    |

#### Returns

`(xmldocnode)` Doc node for the diff document, or `NULL` on error

### XmlHash()

Computes a hash value for an XML document or a node in DOM.

If the hash values for two XML subtrees are equal, the corresponding subtrees are equal to a very high probability. Computes the hash value using the Message Digest algorithm 5 (MD5), a widely-used cryptographic hash function with a 128-bit hash value, so there is a very small probability that two different inputs might map to same MD5 digest.

The source can be specified as a file, a URL, and so on. It can also be a Document node in DOM, or any other DOM node, and must be specified using the `inputSource` parameter. If `inputSource` is a non-Document DOM node, `inputSourceExtra` must point to the Document node for the DOM.

#### Syntax

    xmlerr XmlHash(
       xmlctx *xctx,
       xmlhasht *digest,
       ub4 flags,
       xmldfsrct iputSourceType,
       void *inputSource,
       void *inputSourceExtra,
       oraprop *properties);

| Parameter          | In/Out | Description                                                                                                                             |
|:-------------------|:-------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `xctx`             | `IN`   | XML context                                                                                                                             |
| `digest`           | `OUT`  | The hash value for the XML sub-tree                                                                                                     |
| `flags`            | `IN`   | Not used                                                                                                                                |
| `inputSourceType`  | `IN`   | Type of source for the input document; if zero, `inputSource` is assumed to be a DOM doc node                                           |
| `inputSource`      | `IN`   | Pointer to the source for the input document                                                                                            |
| `inputSourceExtra` | `IN`   | An additional pointer to the source for the input document; if used for a node pointer in a DOM, `inputSource` must be a document node. |
| `properties`       | `IN`   | Not used                                                                                                                                |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK` on success

### XmlPatch()

XmlPatch() applies `Xdiff` schema-conforming changes to an input document. The input document and the `diff` document can be specified either as a DOM tree, file, URI, or buffer.

DOMs are built for both the input and `diff` document if they are not supplied as DOMs.

Data(DOM) encoding of both input and diff documents must be the same as the data encoding in `xctx`. The patched DOM will be in the data encoding specified in `xctx`.

Only the simple XPath is supported in the snapshot model. The `XPath` should identify a node with a posistion predicate in abbreviated syntax, such as `/a[1]/b[2]`. The `XPath`s generated by XmlDiff() meet this requirement. Also, 'operations-in-docorder' condition must be `TRUE`; the nodes must appear in same order as a preorder traversal of the document tree. Global (with or without hashing) meets this requirement. Local does not.

The programming interface should specify the output model used in the diff doc. The `oracle-xmldif` should be the first child of the top level `xdiff` element. It should also use flags to specify if operations are in document order (`TRUE` or `FALSE`), and wether the output model is a snapshot or current.

#### Syntax

    xmldocnode *XmlPatch(
       xmlctx *xctx,
       xmlerr *err,
       ub4  flags,
       xmldfsrct inputSourceType,
       void *inputSource,
       void *inputSourceExtra,
       xmldfsrct diffSourceType,
       void *diffSource,
       void *diffSourceExtra,
       oraprop *properties);

| Parameter          | In/Out | Description                                                                                    |
|:-------------------|:-------|:-----------------------------------------------------------------------------------------------|
| `xctx`             | `IN`   | XML context                                                                                    |
| `xmlerr`           | `OUT`  | numeric error code, `XMLERR_OK` on success                                                     |
| `flags`            | `IN`   | The following option is available:<br>• `XMLDF_FL_DEFAULTS(=0)` chooses defaults               |
| `inputSourceType`  | `IN`   | Type of source for the input document; if zero, `inputSource` is assumed to be a DOM doc node. |
| `inputSource`      | `IN`   | Pointer to the source for the input document                                                   |
| `inputSourceExtra` | `IN`   | An additional pointer to the source for the input document; used for buffer length pointer     |
| `diffSourceType`   | `IN`   | Type of source for `diff` document; if zero, `secondSource` is assumed to be a DOM doc node.   |
| `diffsSource`      | `IN`   | Pointer to the source for the `diff` document                                                  |
| `diffSourceExtra`  | `IN`   | An additional pointer to the source for the `diff` document; used for buffer length pointer    |
| `properties`       | `IN`   | Not used                                                                                       |

#### Returns

`(xmldocnode)` Doc node for the pathed DOM, or `NULL` on error
