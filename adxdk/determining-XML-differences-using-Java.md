An explanation is given of how to determine the differences between two Extensible Markup Language (XML) inputs, using the Java library included in the Oracle XML Developer's Kit (XDK).

### 20.1 Overview of XML Diffing Utilities for Java

The Java XML diffing library includes diffing, hashing, and equality-comparison methods for XML inputs in class `XmlUtils` of package `oracle.xml.diff`.

The `Options` class in the `oracle.xml.diff` package provides options that enable users to control how the input is processed by the methods in the `XmlUtils` class (see User Options for the Java XML Diffing Library). One of these supported options is white space normalization, which is enabled by default.

The algorithm used by the XML diffing methods is specifically designed for the use case of finding differences between two large XML documents (5 MB or more) within seconds, where the minimal diff is not required. The minimal diff is the smallest possible set of changes which, when applied to the first XML input, produces an output equivalent (identical) to the second XML input. Known minimal diff algorithms require prohibitively large amounts of memory and time for processing multimegabyte inputs. The algorithm used in the XML diff methods produces best quality (as close to minimal as possible) diffs in the absence of recurring identical subtrees in the XML inputs.

The Java XML diffing library provides several equivalent variants of each method to allow XML inputs in different forms, including Document Object Model (DOM) nodes, files, and input streams. Internally, the diffing, hashing, and equality comparisons operate on a DOM tree. Input that is not in the form of a DOM tree is internally converted to a DOM tree. To reduce computational overhead, Oracle recommends passing in DOM directly whenever possible.

The Java XML diffing library includes methods to return the diff output as a DOM document, or as a list of objects, each representing a diff operation. With the second option, you can avoid the overhead of XML document generation. With the first option, the resulting document conforms to the XML schema described in Diff Output Schema. The first option is useful, for example, if the diff output must be stored as a log for future reference.

The hash methods provided by the Java XML diffing library compute the hash value of XML input. If the hash values of the two XML inputs are equal, they are identical with a very high probability.

The equal methods provided in the Java XML diffing library compare two inputs for equality.

To use the Java XML diffing library, your application must run with Java version 1.6 or later, with any DOM implementation.

**Note:**

The application programming interface (API) components described in this chapter are contained within the Java package `oracle.xml.diff`. For brevity, fully qualified names are used only when necessary to avoid confusion.

See [Oracle Database XML Java API Reference](../jaxml/index.md) for more information about the `oracle.xml.diff` package.

### 20.2 User Options for the Java XML Diffing Library

The Java XML diffing library supports two options, which you can set using methods in the `Options` class of the `oracle.xml.diff` package. The `Options` object is passed in directly to the diff, hash, and equal methods on each invocation.

- Text Node Normalization (enabled by default)

  Text nodes are normalized in the DOM trees on which the diff, hash, and equal methods operate. Text node normalization involves coalescing adjacent text nodes, followed by stripping leading and trailing white space from the coalesced nodes. Single text nodes have their leading and trailing white space stripped. White-space-only text nodes are eliminated.

  Normalization is performed within the library with minimal additional space, and without modifying the provided XML inputs.

  To perform your own normalization on the DOM inputs before passing them to the library, you must invoke the method `normalizeTextNodes(false)` on the `Options` object to turn off the default normalization.

  Oracle does not recommend invoking the diff methods without performing some type of normalization, either the default or your own. The diff quality suffers in the presence of identical white space text nodes, which commonly occur in XML documents.

- Ignoring Namespace Prefix Differences (enabled by default)

  XML namespace prefix differences are ignored by the diff, hash, and equal methods. For example, two DOM nodes are considered equal if they are identical except for having different prefixes (even if the two different prefixes map to Universal Resource Identifier (URI) of the same namespace. To configure the library to treat different namespace prefixes as truly different, even if they map to the same URI, you can invoke the method `ignorePrefixDifferences(false)` on the `Options` object to turn off the default namespace prefix behavior.

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md) for details about the methods in the `Options` class

### 20.3 Using Java XML Diffing Methods to Find Differences

The Java XML dffing library provides various `diff` and `diffToDoc` methods in the `XmlUtils` class of the `oracle.xml.diff` package. You can use these methods to compare two XML inputs to determine if there are any differences between them.

The `diffToDoc` methods return the output as a DOM document that conforms to the schema described in Diff Output Schema. The Java XML diffing library includes several equivalent variants of these methods, which accept inputs in different forms (DOM nodes, files, and others).

The Java XML diffing library includes an equivalent set of `diff` methods that enable you to work on the diff output that is returned as a list of diff operation objects.

Because the DOM document that represents the diff does not need to be constructed, using the `diff` methods is more efficient than using the `difftoDoc` methods. You should consider using these methods whenever you do not need a representation of the diff in XML form. To use the `diff `methods, you must create an implementation of the `DiffOpReceiver` interface, and then pass it as a parameter to the `diff` methods. The `DiffOpReceiver.receiveDiff` method receives the diff as a list of `DiffOp` objects.

The diff result, whether it is returned as a DOM document or as a list of `DiffOps` objects, can be understood as a series of diff operations. The possible diff operations are:

- append-node

- insert-node-before

- delete-node

Applying the sequence of diff operations on the first DOM tree produces a tree that is equivalent to the second DOM tree. For example, using these two XML inputs:

First input: `<b/>`

Second input: `<c/>`

The diff result from comparing the first and second input is a list, with these two diff operations:

    delete-node /a[1]/b[1]
    append-node <c/> to /a[1]

Deleting the node represented by the XPath expression `/a/b` in the first input, and then appending `<c/>` to the node represented by the XPath expression `/a` in the first input produces the result `<c/>`, which is equivalent to the second input.

When the diff operations are output to a DOM document by the `domToDoc(…)` method, they rely on XPath expressions to indicate the node locations. These XPath locations refer to node positions in the original first input. They do not reflect the applied diff operations.

**Note:**

The Java XML diffing library does not support append-node, insert-node-before, and delete-node operations for attribute nodes. Thus, when any attributes of a node are changed, the change is shown as a delete of the whole node, followed by the insert or the append of the new node with the changed attributes.

For example, for these two inputs:

First input: `<b/>`

Second input: `<b/`

The diff consists of these two diff operations:

    insert <b/> before /a[1]
    delete /a[1]

**Note:**

This section uses XML document output to describe each diff operation. Although they are not described here, diff operation results that are returned programmatically are equivalent.

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md) for more information about the `DiffOpReceiver` interface, and for details about the methods in the `XmlUtils` class

#### 20.3.1 About the append-node Operation

The append-node operation specifies that a given node is to be appended as the last child of a particular first input node.

Example 20-1 shows an append-node operation that adds the highlighted node `<enumeration value="FL"/>` to a document.

Invoking a `diffToDoc(…)` method, using the original document (without the highlighted change) and the changed document as input produces this output:

    <xd:append-node
     xd:parent-xpath="/schema[1]/simpleType[1]/restriction[1]"
     xd:node-type="element">
             <xd:content>
                 <enumeration value="FL"/>
             </xd:content>
    </xd:append-node>

The append-node operation is represented by the `<append-node>` element in the preceding output. This element specifies that a node of the given type is added as the last child of the given first input parent node. The `parent-xpath` attribute specifies the parent node. The `node-type` attribute specifies the type of the node to be appended. The `<content>` child element specifies the node to be appended.

Alternatively, when the `diff(…)` methods are used, the append-node operation is accessible in the `DiffOpReceiver.receiverDiff(…)` method as a `DiffOp` object. In this case, the operation returns the actual references to the nodes in the two DOM trees involved in the diff operation. The reference to the parent node in the first input is returned by invoking the `getParent()` method of `DiffOp`. The reference to the node to be appended from the second input is returned by invoking the `getNew()` method of `DiffOp`.

Example 20-1 Appending a Node

    <schema>
    …
         <simpleType name="USState">
              <restriction base="string">
                   <enumeration value="NY"/>
                   <enumeration value="TX"/>
                   <enumeration value="CA"/>
                   <enumeration value="FL"/>
              </restriction>
         </simpleType>
    …
    </schema>

#### 20.3.2 About the insert-node-before Operation

The insert-node-before operation specifies that a given node is to be inserted before a particular node in the first input.

Example 20-2 shows an insert-node-before operation that inserts the highlighted node `<!-- A type representing US States -->` before the node `<simpleType name="USState">` in a document.

Invoking a `diffToDoc(…)` method, using the original document (without the highlighted change) and the changed document as input produces this output:

    <xd:insert-node-before xd:node-type="comment"
     xd:xpath="/schema[1]/simpleType[1]">
               <xd:content>
                       <!-- A type representing US States -->
               </xd:content>
    </xd:insert-node-before>

The insert-node-before operation is represented by the `<insert-node-before>` element in the preceding output. This element specifies that a node of the given type is inserted before the given first input node. The `xpath` attribute specifies the location of the first input node. The `node-type` attribute specifies the type of the node to be inserted. The `<content>` child element specifies the node to be inserted.

Alternatively, when the `diff(…)` methods are used, the insert-node-before operation is accessible in the `DiffOpReceiver.receiverDiff(…)` method as a `DiffOp` object. In this case, the operation returns the actual references to the nodes in the two DOM trees involved in the diff operation. The reference to the node before which to insert a node in the first input is returned by invoking the `getSibling()` method of `DiffOp`. The reference to the node to be inserted from the second input is returned by invoking the `getNew()` method of `DiffOp`.

Example 20-2 Inserting a Node

    <schema>
    …
        <!-- A type representing US States -->
        <simpleType name="USState">
                <restriction base="string">
                    <enumeration value="NY"/>
                    <enumeration value="TX"/>
                    <enumeration value="CA"/>
                </restriction>
        </simpleType>
    …
    </schema>

#### 20.3.3 About the delete-node Operation

The delete-node operation specifies that a particular node (and its subtree) in the first input is to be deleted.

Example 20-3 shows a delete-node operation that deletes the highlighted node `<element name="LineItems" maxOccurs="unbounded">` from a document.

Invoking a diffToDoc(…) method, using the original document (without the highlighted change) and the changed document as input produces this output:

    <xd:delete-node xd:node-type="element" xd:xpath=
     "/schema[1]/element[1]/complexType[1]/sequence[1]/element[1]/element[1]"/>

The delete-node operation is represented by the `<delete-node>` element in the preceding output. This element specifies that a node of the given type is deleted. The `xpath` attribute specifies the location of the first input node. The `node-type` attribute specifies the type of the node to be deleted.

Alternatively, when the `diff(…)` methods are used, the delete-node operation is accessible in the `DiffOpReceiver.receiverDiff(…)` method as a `DiffOp` object. In this case, the operation returns the actual reference to the node in the first input DOM tree. The reference to the node to be deleted from the first input is returned by invoking `getCurrent()` method of `DiffOp`.

Example 20-3 Deleting a Node

    <schema>
    …
         <element name="PurchaseOrder">
            <complexType>
               <sequence>
                  <element name="PO-Number" type="string">
                     <element name="LineItems" maxOccurs="unbounded">
    …
    </schema>

### 20.4 Invoking diff and difftoDoc Methods in a Java Application

Examples here show how to compare two inputs by invoking `diff` and `diffToDoc` methods from a Java application.

Example 20-4 shows how to use the `diffToDoc` method to compare the input files `doc` and `doc1`.

Continuing with this example, the two input files `f1.xml` and `f2.xml` contain the same data as in Example 20-1.

This sample code displays the contents of `f1.xml`:

    <schema>
         <simpleType name="USState">
              <restriction base="string">
                   <enumeration value="NY"/>
                   <enumeration value="TX"/>
                   <enumeration value="CA"/>
              </restriction>
         </simpleType>
    </schema>

And this sample code displays the contents of `f2.xml`:

    <schema>
         <simpleType name="USState">
              <restriction base="string">
                   <enumeration value="NY"/>
                   <enumeration value="TX"/>
                   <enumeration value="CA"/>
                   <enumeration value="FL"/>
              </restriction>
         </simpleType>
    </schema>

Assume that `textDiff.java` and the input files are in the current directory. Then enter these commands to compile and run the example:

    javac -classpath "xml.jar" textDiff.java
    java –classpath “xml.jar:." textDiff f1.xml f2.xml

Serializing the resulting `diffAsDom` document produces this output:

    <xd:xdiff xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.oracle.com/xdb/xdiff.xsd http://xmlns.oracle.com/xdb/xdiff.xsd">
        <?oracle-xmldiff operations-in-docorder="true"
         output-model="snapshot" diff-algorithm="greedy-heuristic"?>
        <xd:append-node xd:node-type="element"
         xd:parent-xpath="/schema[1]/simpleType[1]/restriction[1]">
            <xd:content>
                <enumeration value="FL"/>
            </xd:content>
        </xd:append-node>
    </xd:xdiff>

Example 20-5 shows how to use an implementation of the `DiffOpReceiver` interface to process the diff returned from the comparison between two XML inputs as a list of `DiffOp` objects.

Enter these commands to compile and run the example:

    javac -classpath "xml.jar" progDiff.java
    java –classpath “xml.jar:." progDiff f1.xml f2.xml

The example generates this output:

    APPENDING NODE:
    <enumeration value="FL"/>
    TO THE PARENT NODE:
    <restriction base="string">
        <enumeration value="NY"/>
        <enumeration value="TX"/>
        <enumeration value="CA"/>
    </restriction>

Example 20-4 Getting a diff as a Document from a Java Application

    import oracle.xml.diff.XmlUtils;
    import oracle.xml.diff.Options;

    import java.io.File;

    import org.w3c.dom.Node;
    import org.w3c.dom.Document;

    import javax.xml.parsers.DocumentBuilderFactory;
    import javax.xml.parsers.DocumentBuilder;

    public class textDiff
    {
        public static void main(String[] args) throws Exception
        {
            XmlUtils xmlUtils = new XmlUtils();

            //Parse the two input files
            DocumentBuilderFactory dbFactory =
                      DocumentBuilderFactory.newInstance();
            dbFactory.setNamespaceAware(true);
            DocumentBuilder docBuilder =
                      dbFactory.newDocumentBuilder();
            Node doc = docBuilder.parse(new File(args[0]));
            Node doc1 = docBuilder.parse(new File(args[1]));

            //Run the diff
            try
            {
                Document diffAsDom = xmlUtils.diffToDoc(doc,
                                      doc1, new Options());
            }
            catch (Exception e)
            {
                e.printStackTrace();
            }
        }
    }

Example 20-5 Getting a diff Using DiffOpReceiver from a Java Application

    import oracle.xml.diff.DiffOp;
    import oracle.xml.diff.DiffOpReceiver;

    import java.util.List;
    import java.util.Properties;

    import java.io.File;

    import org.w3c.dom.Node;

    import javax.xml.parsers.DocumentBuilderFactory;
    import javax.xml.parsers.DocumentBuilder;

    public class progDiff
    {
      public static void main(String[] args) throws Exception
      {
         XmlUtils xmlUtils = new XmlUtils();

         //Parse the two input files
         DocumentBuilderFactory dbFac =
                            DocumentBuilderFactory.newInstance();
         dbFac.setNamespaceAware(true);
         DocumentBuilder docBuilder = dbFac.newDocumentBuilder();
         Node doc = docBuilder.parse(new File(args[0]));
         Node doc1 = docBuilder.parse(new File(args[1]));

         Options opt = new Options();

         //Instantiate the DiffOpReceiver. This is the object that
         //will receive DiffOps, ie diff operations that the XmlDiff
         //outputs. Each object represents either deletion or insert
         //or append of a node. In this DiffOpReceiverImpl
         //implementation (see below) of the DiffOpReceiver
         //interface, we simply print out each diff operation.
         DiffOpReceiver diffOpRec =
                     new progDiff().new DiffOpReceiverImpl();
         xmlUtils.diff(doc, doc1, diffOpRec, opt);
      }

      class DiffOpReceiverImpl implements DiffOpReceiver
      {
          public void receiveDiff(List<DiffOp> diffOps)
          {
             try
             {
                 for (int i = 0; i < diffOps.size(); i++)
                 {
                     DiffOp diffOperation= diffOps.get(i);

                     //Delete operation, print out the deleted
                     // node from the first tree
                     if (diffOperation.getOpName() ==
                         DiffOp.Name.DELETE)
                        System.out.println ("DELETING NODE:\n" +
        XmlUtils.nodeToString(diffOperation.getCurrent(), false));

                     //Insert operation. Print out the node
                     //from the second tree to be inserted,
                     //and the node from the first tree
                     //before  which the insertion will happen
                     else if (diffOperation.getOpName() ==
                              DiffOp.Name.INSERT_BEFORE_NODE)
                        System.out.println ("INSERTING NODE:\n" +
           XmlUtils.nodeToString(diffOperation.getNew(), false) +
                                               "BEFORE NODE:\n" +
        XmlUtils.nodeToString(diffOperation.getSibling(), false));




                     //Append as the last node of the parent.
                     //Print out the node from the second tree
                     //that will be appended, and the parent
                     //node from the first tree to which the
                     //former node will be appended as the
                     //last child.
                     else if (diffOperation.getOpName() ==
                        DiffOp.Name.INSERT_BY_APPENDING)
                        System.out.println ("APPENDING NODE:\n" +
           XmlUtils.nodeToString(diffOperation.getNew(), false) +
                                        "TO THE PARENT NODE:\n" +
           XmlUtils.nodeToString(diffOperation.getParent(), false));
               }
           }
           catch (Exception e)
           {
               System.err.println ("Error while printing out the
                                diff result:" + e.getMessage());
           }
        }
      }
    }

### 20.5 Using Java XML hash and equal Methods to Identify and Compare Inputs

The Java XML diffing library provides `hash` methods to compute a hash value that uniquely identifies the input, with a high probability. Because there is a very low probability of a hash collision, there can be no guarantee that two inputs are identical when their hash values match.

To check that two inputs are truly identical with absolute certainty, use the `equal` methods. The `equal` methods process both inputs simultaneously, while checking them for absolute equality.

The Java XML diffing library provides several equivalent variants of the `hash` and `equal` methods that accept inputs in different forms (DOM nodes, files, and more).

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md) for details about the `hash` and `equal` methods in the `XmlUtils` class

### 20.6 Diff Output Schema

The output schema `xdiff.xsd`, to which the Java XML diffing library conforms, is presented.

Example 20-6 Diff Output Schema: xdiff.xsd

    <schema targetNamespace="http://xmlns.oracle.com/xdb/xdiff.xsd"
        xmlns="http://www.w3.org/2001/XMLSchema"
        xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"
        version="1.0" elementFormDefault="qualified"
        attributeFormDefault="qualified">
        <annotation>
            <documentation xml:lang="en">
             Defines the structure of XML documents that capture the difference
             between two XML inputs. Changes that are not supported by Oracle
             XmlDiff may not be expressible in this schema.

            'oracle-xmldiff' PI:

            We use 'oracle-xmldiff' PI to describe certain aspects of the diff.
            This should be the first element of top level xdiff element.

            version-number: version number of the XML diff schema

            output-model: output model for representing the diff. Currently, only
            the "snapshot" model is supported.

            Snapshot model:
            Each operation uses XPaths as if no operations
            have been applied to the input document.
            Default and works for both Xmldiff and XmlPatch.

            <!-- Example:
                <?oracle-xmldiff version-number = "1.0" output-model = "snapshot"?>
            -->
            </documentation>
         </annotation>
        <!-- Enumerate the supported node types -->
        <simpleType name="xdiff-nodetype">
            <restriction base="string">
                <enumeration value="element"/>
                <enumeration value="text"/>
                <enumeration value="cdata"/>
                <enumeration value="processing-instruction"/>
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
                            <attribute name="parent-xpath" type="string"/>
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
                        </complexType>
                    </element>

                 </choice>
            </complexType>
        </element>
    </schema>
