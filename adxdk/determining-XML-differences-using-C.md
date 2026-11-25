An explanation is given of how to determine the differences between two Extensible Markup Language (XML) inputs and apply the differences as a patch to one of the XML documents.

### 8.1 Overview of XMLDiff in C

You can use Oracle `XmlDiff` to determine the differences between two similar XML documents. It generates an `Xdiff` instance document that indicates the differences. The `Xdiff` document is an XML document that conforms to an XML schema, the `Xdiff` schema.

You can then use `XmlPatch`, which takes the `Xdiff` instance document and applies the changes to other documents. You can use this process to apply the same changes to a large number of XML documents.

`XmlDiff` supports only the Document Object Model (DOM) application programming interface (API) for input and output.

`XmlPatch` also supports the DOM for the input and patch documents.

You can use `XmlDiff` and `XmlPatch` through a C API or a command-line tool. They are exposed by two structured query language (SQL) functions.

An `XmlHash` C API is provided to compute the hash value of an XML tree or subtree. If hash values of two trees or subtrees are equal, the trees are identical to a very high probability.

#### 8.1.1 Process Flow for XMLDiff

The XMLDiff process flow is described.

1.  The two input documents are compared by `XmlDiff`.

2.  `XmlDiff` creates a `Xdiff` instance document.

3.  The application can pass the `Xdiff` instance document to `XmlPatch`, if this is required.

4.  `XmlPatch` can apply the differences captured from the comparison to other documents as specified by the application.

### 8.2 Using XmlDiff

`XmlDiff` compares the trees that represent two input documents, to determine their differences. Both input documents must use the same character-set encoding. The `Xdiff` (output) instance document has the same encoding as the data encoding (DOM encoding) of the input documents.

#### 8.2.1 User Options for Comparison Optimization

There are two optimization options for comparison: global and local optimization.

- Global Optimization—Default

  The whole document trees are compared.

- Local Optimization

  Comparison is at the sibling level. Local optimization compares siblings under the corresponding parents from two trees.

Global optimization can take more time and space for large documents but always produces the smallest set of differences (the optimal difference). Local optimization is much faster, but may not produce the optimal difference.

#### 8.2.2 User Option for Hashing

Hashing generally speeds up global optimization with a small possible loss in quality. Hashing improves the quality of the difference output, with local optimization. Using different hash levels may generate both local and global differences. You can specify the use of hashing for both local and global optimization.

To specify hashing, provide the `hashLevel` parameter. If `hashLevel` is greater than 1, then only the `DOMHash` values are used for comparing all subtrees at `depth >= hashLevel` of difference. If the hash values are equal, then the subtrees are presumed to be equal.

#### 8.2.3 How XmlDiff Looks at Input Documents

How `XmlDiff` handles input documents is described.

`XmlDiff` ignores differences in the order of attributes while doing the comparison.

`XmlDiff` ignores `DocType` declarations. Files are not validated against the document type definition (DTD).

`XmlDiff` ignores any differences in the namespace prefixes if the namespace prefixes refer to the same namespace Universal Resource Identifier (URI). Otherwise, if two nodes have the same local name and content but differ in namespace URI, these differences are indicated.

**Note:**

`XmlDiff` operates on its input documents in a nonschema-based way. It does not operate on elements or attributes in a type-aware manner.

#### 8.2.4 Using the XmlDiff Command-Line Utility

The command-line options for utility `XmlDiff` are described.

Table 8-1 XmlDiff Command-Line Options for the C Language

| Option             | Description                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `-e` encoding      | Specify default input-file encoding. If no encoding is specified in XML file, this encoding is assumed for input.                                |
| `-E` encoding      | Specify output/data encoding. DOMs and the `Xdiff` instance document are created in this encoding. Default is 8-bit encoding of Unicode (UTF-8). |
| `-h` `hash`L`evel` | Specify the hash level. `0` means none.<br>If greater than `1`, starting depth to use hashing for subtrees.                                      |
| `-g`               | Set global optimization (default).                                                                                                               |
| `-l`               | Set local optimization.                                                                                                                          |
| `-p`               | Show this usage help.                                                                                                                            |
| `-u`               | Disable update operation.                                                                                                                        |

#### 8.2.5 Sample Input Document

A sample input XML document is presented.

Example 8-1 is a sample XML document that you can use to explain updates resulting from using both `XmlDiff` and `XmlPatch`. It is followed by some hypothetical changes.

Assume that there is another file, `book2.xml`, that looks just like Example 8-1 except that it causes these actions:

- Deletes "The Eleventh Commandment", a `delete-node` operation.

- Changes the country code for the "C++ Primer" to US from USA, an `update-node` operation.

- Adds a description to "Emperor's New Mind", an `append-node` operation.

- Adds the edition to "Evening News", an `insert-node-before` operation.

- Updates the price of "Evening News", an `update-node` operation.

Example 8-1 book1.xml

    <?xml version="1.0"?>
    <booklist xmlns="http://booklist.oracle.com">
      <book>
        <title>Twelve Red Herrings</title>
        <author>Jeffrey Archer</author>
        <publisher>Harper Collins</publisher>
        <price>7.99</price>
      </book>
      <book>
        <title language="English">The Eleventh Commandment</title>
        <author>Jeffrey Archer</author>
        <publisher>McGraw Hill</publisher>
        <price>3.99</price>
      </book>
      <book>
        <title language="English" country="USA">C++ Primer</title>
        <author>Lippmann</author>
        <publisher>Harper Collins</publisher>
        <price>4.99</price>
      </book>
      <book>
        <title>Emperor's New Mind</title>
        <author>Roger Penrose</author>
        <publisher>Oxford Publishing Company</publisher>
        <price>15.9</price>
      </book>
      <book>
        <title>Evening News</title>
        <author>Arthur Hailey</author>
        <publisher>MacMillan Publishers</publisher>
        <price>9.99</price>
      </book>
    </booklist>

#### 8.2.6 Sample Xdiff Instance Document

A sample `Xdiff` instance document is presented.

This section shows the `Xdiff` instance document produced by the comparison of these two XML files described in the previous section. The sections that follow explain the XML processing instructions and the operations on this document.

You can invoke `XmlDiff`:

    > xmldiff book1.xml book2.xml

You can also examine the sample application for arguments and flags.

Example 8-2 Sample Xdiff Instance Document

    <?xml version="1.0" encoding="UTF-8"?>
    <xd:xdiff xsi:schemaLocation="http://xmlns.oracle.com/xdb/xdiff.xsd
    xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:oraxdfns_0="http://booklist.oracle.com">
        <?oracle-xmldiff operations-in-docorder="true" output-model="snapshot"
            diff-algorithm="global"?>
        <xd:delete-node xd:node-type="element" xd:xpath="/oraxdfns_0
                  :booklist[1]/oraxdfns_0:book[2]"/>
        <xd:update-node xd:node-type="attribute"
             xd:parent-xpath="/oraxdfns_0:booklist[1]/oraxdfns_0:book[3]/oraxdfns_0
                  :title[1]" xd:attr-local="country">
                    <xd:content>US</xd:content>
        </xd:update-node>
        <xd:append-node xd:node-type="element" xd:parent-xpath="/oraxdfns_0
                  :booklist[1]/oraxdfns_0:book[4]">
            <xd:content>
                <oraxdfns_0:description> This is a classic </oraxdfns_0:description>
            </xd:content>
        </xd:append-node>
        <xd:insert-node-before xd:node-type="element" xd:xpath="/oraxdfns_0
                  :booklist[1]/oraxdfns_0:book[5]/oraxdfns_0:author[1]">
            <xd:content>
                <oraxdfns_0:edition>Hardcover</oraxdfns_0:edition>
            </xd:content>
        </xd:insert-node-before>
        <xd:update-node xd:node-type="text" xd:xpath="/oraxdfns_0
               :booklist[1]/oraxdfns_0:book[5]/oraxdfns_0:price[1]/text()[1]">
            <xd:content>12.99</xd:content>
        </xd:update-node>
    </xd:xdiff>

#### 8.2.7 Output Model and XML Processing Instructions

The `Xdiff` instance document uses some XML processing instructions (shown in bold in the previous section) that are used to represent certain aspects of the differencing process.

See Xdiff Schema. These instructions and related options are:

- `operations-in-docorder`: Options are `true` or `false`:

  - `true`—The `Xdiff` instance document refers to the nodes from the first document in the same order as in the document.

  - `false`—The `Xdiff` instance document does not refer to the nodes from the first document in the same order as in the document.

  The output of global optimization meets the `operations-in-docorder` requirement, but local optimization does not.

- `output-model`: Options are:

  - `snapshot`—`Xmldiff` generates output in snapshot model and follows the UNIX diff model. Each operation uses `XPath` as if no operations have been applied to the input document. This is the default. `XmlPatch` can handle this model only if `operations-in-docorder` is set to `true` and the `XPath`s are simple. Simple `XPath`s require a child axis, no wild cards, and must use positional predicates, such as `/root[1]/child[2]/text()[2]`.

  - `current`—Each operation uses `XPath` as if all operations up to the previous one have been applied to the input document. Even though `XmlDiff` does not generate differences in the current model, `XmlPatch` can handle a hand-crafted `diff` document in the current model

- `diff-algorithm`: Options indicate which optimization generated the differences.

  - Global optimization

  - Local optimization

**Related Topics**

- User Options for Comparison Optimization

#### 8.2.8 Xdiff Operations

`XmlDiff` captures differences using operations indicated by the `Xdiff` instance document. The `XmlDiff` operations are described.

Table 8-2 Xdiff Operation Attributes

| Attribute                | Description                                                                                            |
|:-------------------------|:-------------------------------------------------------------------------------------------------------|
| `parent-path` or `xpath` | Specifies the `XPATH` location of the parent node of the operand node or the `XPATH` location of node. |
| `node-type`              | Specifies the type of the operand node.                                                                |
| `content`                | Child element that specifies the new subtree or value appended or inserted.                            |

The `Xdiff` operations, presented in the `Xdiff` instance document, are:

- `append-node`:

  The `append-node` element specifies that a node of the given type is added as the last child of the given parent.

- `insert-node-before`:

  The `insert-node-before` element specifies that a node of the given type is inserted before the given reference node.

- `delete-node`:

  The `delete-node` element specifies that the node be deleted along with all its children. You can use this element to delete elements, comments, and so on.

- `update-node`:

  `update-node` specifies that the value associated with the node with the given `XPath` expression is updated to the new value, which is specified. Content is the value for a text node. The value of an attribute is the value for an attribute node.

  - Update for Text Nodes:

    - Generation of update node operations can be turned off by the user.

    - The value of an attribute is the value for an attribute node.

    - `update-node` is generated for text nodes only by global optimization.

  - Update for Elements:

    - `XmlDiff` does not generate update operations for element nodes.

      You can either manually modify the `Xdiff` instance document to create an update operation that works with `XmlPatch`, or provide a totally hand-written `Xdiff` instance document. All children of the element operated on by the update are deleted. Any new subtree specified under the content node is imported.

#### 8.2.9 Format of Xdiff Instance Document

The output of `XmlDiff`, the `Xdiff` instance document, is an XML document that conforms to the `Xdiff` XML schema. The output document contains a sequence of operations describing the differences between the two input documents. If you apply the differences to the first document, you obtain the second document.

#### 8.2.10 Xdiff Schema

An `Xdiff` XML schema, to which an `Xdiff` instance document (output) adheres, is presented.

Example 8-3 Xdiff Schema: xdiff.xsd

    <schema targetNamespace="http://xmlns.oracle.com/xdb/xdiff.xsd"
        xmlns="http://www.w3.org/2001/XMLSchema"
        xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"
        version="1.0" elementFormDefault="qualified"
        attributeFormDefault="qualified">
        <annotation>
            <documentation xml:lang="en">
             Defines the structure of XML documents that capture the difference
             between two XML documents. Changes that are not supported by Oracle
             XmlDiff may not be expressible in this schema.

           'oracle-xmldiff' PI in Xdiff document:

           We use 'oracle-xmldiff' PI to describe certain aspects of the diff.
           The PI denotes values for 'operations-in-docorder' and 'output-model'.
           The output of XmlDiff has the PI always. If the user hand-codes a diff doc
           then it must also have the PI in it as the first child of top level xdiff
           element, to be able to call XmlPatch.

           operations-in-docorder:
           Can be either 'true' or 'false'.
           If true, the operations in the diff document refer to the
           elements of the input doc in the same order as document order. Output of
           global algorithm meets this requirement while local does not.

           output-model:
           output models for representing the diff. Can be either 'Snapshot' or
           'Current'.

           Snapshot model:
           Each operation uses Xpaths as if no operations
           have been applied to the input document. (like UNIX diff)
           This is the model used in the output of XmlDiff. XmlPatch works with
           this (and the current model too).
           For XmlPatch to handle this model, "operations-in-docorder" must be
           true and the Xpaths must be simple. (see XmlDif C API documentation).

           Current model:
           Each operation uses Xpaths as if all operations till the previous one
           have been applied to the input document. Works with XmlPatch even if
           the 'operations-in-docorder' criterion is not met and the xpaths are
           not simple.
           <!-- Example:
                <?oracle-xmldiff operations-in-docorder="true" output-model=
                "snapshot" diff-algorithm="global"?>
            -->
          </documentation>
        </annotation>
        <!-- Enumerate the supported node types -->
        <simpleType name="xdiff-nodetype">
            <restriction base="string">
                <enumeration value="element"/>
                <enumeration value="attribute"/>
                <enumeration value="text"/>
                <enumeration value="cdata"/>
                <enumeration value="entity-reference"/>
                <enumeration value="entity"/>
                <enumeration value="processing-instruction"/>
                <enumeration value="notation"/>
                <enumeration value="comment"/>
             </restriction>
        </simpleType>

        <element name="xdiff">
            <complexType>
                <choice minOccurs="0" maxOccurs="unbounded">
                    <element name="append-node">
                        <complexType>
                            <sequence>
                                <element name="content" type="anyType"/>
                            </sequence>
                            <attribute name="node-type" type="xd:xdiff-nodetype"/>
                            <attribute name="xpath" type="string"/>
                            <attribute name="parent-xpath" type="string"/>
                            <attribute name="attr-local" type="string"/>
                            <attribute name="attr-nsuri" type="string"/>
                        </complexType>
                    </element>

                    <element name="insert-node-before">
                        <complexType>
                            <sequence>
                                <element name="content" type="anyType"/>
                            </sequence>
                            <attribute name="xpath" type="string"/>
                            <attribute name="node-type" type="xd:xdiff-nodetype"/>

                        </complexType>
                    </element>

                    <element name="delete-node">
                        <complexType>
                            <attribute name="node-type" type="xd:xdiff-nodetype"/>
                            <attribute name="xpath" type="string"/>
                            <attribute name="parent-xpath" type="string"/>
                            <attribute name="attr-local" type="string"/>
                            <attribute name="attr-nsuri" type="string"/>
                        </complexType>
                    </element>
                     <element name="update-node">
                        <complexType>
                            <sequence>
                                <element name="content" type="anyType"/>
                            </sequence>
                            <attribute name="node-type" type="xd:xdiff-nodetype"/>
                            <attribute name="parent-xpath" type="string"/>
                            <attribute name="xpath" type="string"/>
                            <attribute name="attr-local" type="string"/>
                            <attribute name="attr-nsuri" type="string"/>
                        </complexType>
                    </element>
                    <element name="rename-node">
                        <complexType>
                            <sequence>
                                <element name="content" type="anyType"/>
                            </sequence>
                            <attribute name="xpath" type="string"/>
                            <attribute name="node-type" type="xd:xdiff-nodetype"/>
                        </complexType>
                    </element>
                </choice>
             <attribute name="xdiff-version" type="string"/>
            </complexType>
        </element>
    </schema>

#### 8.2.11 Using XMLDiff in an Application

In an application, `XmlDiff` takes the source types and locations of the input documents as arguments. The source type can be a URL, file, `orastream` and `stream` context pointers, buffer, and `buffer_length` pointers or the pointer to a DOM document element (`docelement`).

`XmlDiff` returns the document node for the DOM for the `Xdiff` instance document.

XmlDiff builds the DOM for the two documents, if they are not already provided as DOM, before performing a comparison.

**See Also:**

[Oracle Database XML C API Reference](../caxml/package-XmlDiff-API.md) for the C API for the flags that control the behavior of `XmlDiff`

Example 8-4 XMLDiff Application

    # include <xmldf.h>
    ...
    xmlctx     *xctx;
    xmldocnode *doc1, *doc2, *doc3;
    uword       hash_level;
    oratext    *s, *inp1 = "book1.xml", *inp2="book2.xml";
    xmlerr      err;
    ub4         flags;

    flags = 0; /* defaults : global algorithm */
    hash_level = 0; /* no hashing */
    /* create XML meta context */
    if (!(xctx = XmlCreate(&err, (oratext *) "XmlDiff", NULL)))
    {
       printf("Failed to create XML context, error %u\n",
    (unsigned) err);
    err_exit("Exiting");
    }
    /* Load the two input files */
    if (!(doc1 = XmlLoadDom(xctx, &err, "file", inp1, "discard_whitespace", TRUE,
     NULL)))
    {
       printf("Parsing first file failed, error %u\n", (unsigned)err);
       err_exit((oratext *)"Exiting.");
    }
    if (!(doc2 = XmlLoadDom(xctx, &err, "file", inp2, "discard_whitespace", TRUE,
        NULL)))
    {
       printf("Parsing second file failed, error %u\n", (unsigned)err);
       err_exit((oratext *)"Exiting.");
    }

    /* run XmlDiff on the DOM trees. */

    doc3 = XmlDiff(xctx, &err, flags, XMLDF_SRCT_DOM, doc1, NULL, XMLDF_SRCT_DOM,
                   doc2, NULL,hash_level, NULL);

    if(!doc3)
       printf("XmlDiff Failed, error %u\n", (unsigned)err);
    else
    {
    if(err != XMLERR_OK)
    printf("XmlDiff returned error %u\n", (unsigned)err);
    /* Now we have the DOM tree in doc3 which represent the Diff */
    ...
    }

    XmlFreeDocument(xctx, doc1);
    XmlFreeDocument(xctx, doc2);
    XmlFreeDocument(xctx, doc3);
    XmlDestroy(xctx);

#### 8.2.12 Customized Output

A customized output builder stores differences in any format suitable to the application. You can create your own customized output builder, rather than using the default `Xdiff` instance document, which is generated by `XmlDiff` and that conforms to the `Xdiff` schema.

To create a customized output builder, you must provide a callback that can be called after `XmlDiff` determines the differences. The differences are passed to the callback as an array of `xmdlfop`. The callback may be called multiple times as the differences are being generated.

Using a customized output builder may perform better than using the default, because it does not have to maintain the internal state necessary for `XPath` generation.

By default, `XmlDiff` captures the differences in XML conforming to the `Xdiff` schema. If necessary, plug in your own output builder. The differences are represented as an array `xmldfop`. You must write an output builder callback function. The function signature is:

    xmlerr(*xdfobcb)(void *uctx, xmldfop *escript, ub4 escript_siz);

`uctx` is the user specific context.

`escript` is the array of size `escript_siz`:

    diff[escript_siz]

`mctx` is the memory context.

Supply this memory context through properties to `XmlDiff()`. Use this memory context to allocate `escript`. You must later free `escript`.

Invoke the output builder callback after the differences have been found which happens even before the invocation of `XmlDiff()` returns. The output builder callback can be called multiple times.

Example 8-5 Customized XMLDiff Output

     /* Sample useage:  */
     ...
     #include <orastruc.h> / * for 'oraprop' * /
     ...
     static oraprop diff_props[] = {
        ORAPROP(XMLDF_PROPN_CUSTOM_OB, XMLDF_PROPI_CUSTOM_OB, POINTER),
        ORAPROP(XMLDF_PROPN_CUSTOM_OBMCX, XMLDF_PROPI_CUSTOM_OBMCX, POINTER),
        ORAPROP(XMLDF_PROPN_CUSTOM_OBUCX, XMLDF_PROPI_CUSTOM_OBUCX, POINTER),
            { NULL }
      };
      ...
      oramemctx *mymemctx;
      ...
      xmlerr myob(void *uctx,  xmldfop *escript, ub4 escript_siz)
      {
         /* process diff which is available in escript * /

         /* free escript - the caller has to do this * /
         OraMemFree(mymemctx, escript);
      }

      main()
      {
       ...
          myctxt  *myctx;

          diff_props[0].value_oraprop.p_oraprop_v = myob;
          diff_props[1].value_oraprop.p_oraprop_v = mymemctx;
          diff_props[2].value_oraprop.p_oraprop_v = myctx;
          XmlDiff(xctx, &err, 0, doc1, NULL, 0, doc2, NULL, 0, diff_props);
     ...


### 8.3 Using XmlPatch

`XmlPatch` takes an `Xdiff` instance document, generated by `XmlDiff` or created by another mechanism, and follows the instructions in the `Xdiff` instance document to modify other XML documents.

#### 8.3.1 Using the XmlPatch Command-Line Utility

Command-line options for utility `XmlPatch` are described.

Table 8-3 XmlPatch for C Command-Line Options

| Option        | Description                                                                                                       |
|:--------------|:------------------------------------------------------------------------------------------------------------------|
| `-e` encoding | Specify default input-file encoding. If no encoding is specified in XML file, this encoding is assumed for input. |
| `-E` encoding | Specify output/data encoding. DOMs and patched document are created in this encoding. Default is UTF-8.           |
| `-i`          | Interpret file names as URLs.                                                                                     |
| `-h`          | Show this usage help.                                                                                             |

#### 8.3.2 Using XmlPatch in an Application

`XmlPatch` takes the source types and locations of the input document and the `diff` document as arguments. The source type can be a URL, file, `orastream` and `stream` context pointers, buffer and `buffer_length` pointers, or the pointer to a DOM document element (`docelement`).

**See Also:**

[Oracle Database XML C API Reference](../caxml/package-XmlDiff-API.md) for the C API for the flags that control the behavior of `XmlPatch`

The modes that were set by the `Xdiff` schema affect how `XmlPatch` works.

If the `output-model` is `Snapshot`, `XmlPatch` only works if `operations-in-docorder` is `TRUE`.

If the `output-model` is `Current`, it is not necessary that `operations-in-docorder` be set to `TRUE`.

Example 8-6 Sample Application for XmlPatch

    ...
    #include <xmldf.h>
    ...
    xmlctx     *xctx;
    xmldocnode *doc1, *doc2;
    oratext    *s;
    oratext    *inp1 = "book1.xml"; /* input document */
    oratext    *inp2 = "diff.xml", /* diff document */
    xmlerr      err;

    /* create XML meta context */
    if (!(xctx = XmlCreate(&err, (oratext *) "XmlPatch", NULL)))
    {
       printf("Failed to create XML context, error %u\n",
    (unsigned) err);
    err_exit("Exiting");
    }
    /* Load the two input files */
    if (!(doc1 = XmlLoadDom(xctx, &err, "file", inp1, "discard_whitespace", TRUE,
        NULL)))
    {
       printf("Parsing first file failed, error %u\n", (unsigned)err);
       err_exit((oratext *)"Exiting.");
    }
    if (!(doc2 = XmlLoadDom(xctx, &err, "file", inp2, "discard_whitespace", TRUE,
        NULL)))
    {
       printf("Parsing second file failed, error %u\n", (unsigned)err);
       err_exit((oratext *)"Exiting.");
    }

    /* call XmlPatch */
    if(!XmlPatch(xctx, &err, 0, XMLDF_SRCT_DOM, doc1, NULL, XMLDF_SRCT_DOM,
               doc2, NULL, NULL));

       printf("XmlPatch Failed, error %u\n", (unsigned)err);
    else
    {
    if(err != XMLERR_OK)
    printf("XmlPatch returned error %u\n", (unsigned)err);
    /* Now we have the patched document in doc1 */
    ...
    }

    XmlFreeDocument(xctx, doc1);
    XmlFreeDocument(xctx, doc2);
    XmlDestroy(xctx);

### 8.4 Using XmlHash

`XmlHash` computes a hash value for an XML tree. If the hash values of two trees are equal, it is probable that they are the same XML. You can use `XmlHash` to do a quick comparison to see if an XML tree is already in the database.

You can run `XmlDiff` again, if necessary, on any matches, to be absolutely certain there is a match. You can compute the hash value of the new document and query the database for it.

Example 8-7 shows a sample program that uses `XmlHash`.

Example 8-7 XmlHash Program

    sword main(sword argc, char *argv[])
    {
       xmlctx     *xctx;
       xmldfsrct   srct;
       oratext    *data_encoding, *input_encoding, *s, *inp1;
       ub1         flags;
       xmlerr      err;
       ub4         num_args;
       xmlhasht    digest;
       flags = 0; /* defaults */
       srct = XMLDF_SRCT_FILE;
       inp1 = "somexml.xml";
       xctx = XmlCreate(&err, (oratext *) "XmlHash", NULL);

       if (!xctx)
       {
          /* handle error with creating xml context and exit */
          ...
       }

       /* run XmlHash */
       err = XmlHash(xctx, &digest, 0, srct, inp1, NULL, NULL);
       if(err)
          printf("XmlHash returned error:%d \n", err);
       else
          txdfha_pd(digest);

       XmlDestroy(xctx);

       return (sword )err;
    }

    /* print bytes in xml hash */
    static void txdfha_pd(xmlhasht digest)
    {
       ub4  i;

       for(i = 0; i < digest.l_xmlhasht; i++)
          printf("%x ", digest.d_xmlhasht[i]);

       printf("\n");
    }

#### 8.4.1 Invoking XmlDiff and XmlPatch

`XmlDiff` and `XmlPatch` can be called as command-line tools and from the C language. They are also available as SQL functions.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/XMLDIFF.md) `XMLDiff`

- [Oracle Database SQL Language Reference](../sqlrf/XMLPATCH.md), `XMLPatch`
