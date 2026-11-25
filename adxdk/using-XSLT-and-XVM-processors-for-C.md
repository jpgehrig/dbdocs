An explanation is given of how to use the Extensible Stylesheet Language Transformation (XSLT) and XSLT Virtual Machine (XVM) processors for C.

**Note:**

Use the unified C application programming interface (API) for Oracle XML Developer's Kit (XDK) and Oracle XML DB applications. Older, nonunified C functions are deprecated and supported only for backward compatibility. They will be removed in a future release.

The unified C API is described in [Using the XML Parser for C](using-XML-parser-for-C.md).

### 4.1 XSLT XVM Processor

The Oracle XVM package includes the XSLT compiler and the XVM. This package implements the XSLT language as specified in the World Wide Web Consortium (W3C) Recommendation of 16 November 1999.

Implementing the XSLT compiler and the XVM enables compilation of XSLT (Version 1.0) into bytecode format, which is executed by the virtual machine. XVM is the software implementation of a CPU designed to run compiled XSLT code. The virtual machine assumes a compiler compiling XSLT stylesheets to a sequence of bytecodes or machine instructions for the XSLT CPU. The bytecode program is a platform-independent sequence of 2-byte units. It can be stored, cached, and run on different XVMs. The XVM uses the bytecode programs to transform XML instance documents. This approach clearly separates compile-time from runtime computations and specifies a uniform way of exchanging data between instructions.

The benefits of this approach are:

- An XSLT stylesheet can be compiled, saved in a file, and reused often, even on different platforms.

- The XVM is significantly faster and uses less memory than other XSLT processors.

- The bytecodes are language independent. There is no difference between code generated from a C or C++ XSLT compiler.

#### 4.1.1 XVM Usage Example

A typical scenario of using the package APIs is described.

1.  Create and use an XML meta-context object.

        xctx = XmlCreate(&err,...);

2.  Create and use an XSLT compiler object.

        comp = XmlXvmCreateComp(xctx);

3.  Compile an XSLT stylesheet or XPath expression and store or cache the resulting bytecode.

        code = XmlXvmCompileFile(comp, xslFile, baseuri, flags, &err);

    or

        code = XmlXvmCompileDom (comp, xslDomdoc, flags, &err);

    or

        code = XmlXvmCompileXPath (comp, xpathexp,  namespaces, &err);

4.  Create and use an XVM object. The explicit stack size setting is needed when XVM terminates with a `Stack Overflow` message or when smaller memory footprints are required. See `XmlXvmCreate()`.

        vm = XmlXvmCreate(xctx, "StringStack", 32, "NodeStack", 24, NULL);

5.  Set the output (optional). Default is a stream.

        err = XmlXvmSetOutputDom (vm, NULL);

    or

        err = XmlXvmSetOutputStream(vm, &xvm_stream);

    or

        err = XmlXvmSetOutputSax(vm, &xvm_callback, NULL);

6.  Set a stylesheet bytecode to the XVM object. Can be repeated with other bytecode.

        len = XmlXvmGetBytecodeLength(code, &err);
        err = XmlXvmSetBytecodeBuffer(vm, code, len);

    or

        err = XmlXvmSetBytecodeFile (vm, xslBytecodeFile);

7.  Transform an instance XML document or evaluate a compiled XPath expression. Can be repeated with the same or other XML documents.

        err = XmlXvmTransformFile(vm, xmlFile, baseuri);

    or

        err = XmlXvmTransformDom (vm, xmlDomdoc);

    or

        obj  = (xvmobj*)XmlXvmEvaluateXPath (vm, code, 1, 1, node);

8.  Get the output tree fragment (if DOM output is set at Step 5).

        node = XmlXvmGetOutputDom (vm);

9.  Delete the objects.

        XmlXvmDestroy(vm);
        XmlXvmDestroyComp(comp);
        XmlDestroy(xctx);

#### 4.1.2 Using the XVM Processor Command-Line Utility

The XVM processor is accessed from the command-line using command `xvm`.

    xvm

Usage:

    xvm options xslfile xmlfile

    xvm options xpath xmlfile

Options:

    -c        Compile xslfile. The bytecode is in "xmlfile.xvm".
    -ct       Compile xslfile and transform xmlfile.
    -t        Transform xmlfile using bytecode from xslfile.
    -xc       Compile xpath. The bytecode is in "code.xvm".
    -xct      Compile and evaluate xpath with xmlfile.
    -xt       Evaluate XPath bytecode from xpath with xmlfile.

Examples:

    xvm -ct  db.xsl db.xml
    xvm -t   db.xvm db.xml
    xvm -xct "doc/employee[15]/family" db.xml

#### 4.1.3 Accessing the XVM Processor for C

Oracle XVM Processor for C is part of the standard installation of Oracle Database.

**See Also:**

- [Oracle Database XML C API Reference](../caxml/package-XSLTVM-API.md), XSLTVM APIs for C

- [XDK on OTN](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=otn_db_xdk_overview)

### 4.2 XSLT Processor for XDK for C

The Oracle XSL/XPath package implements the XSLT language as specified in the W3C Recommendation of 16 November 1999. The package includes the XSLT 1.0 processor and XPath 1.0 Processor. The Oracle implementation of the XSLT processor follows the common design approach of melding compiler and processor into one object.

**See Also:**

- [XSL Transformations (XSLT)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xslt)

- [XML Path Language (XPath)](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xpath)

#### 4.2.1 XSLT Processor Usage Example

A typical scenario of using the package APIs is presented.

1.  Create and use an XML meta-context object.

        xctx = XmlCreate(&err,...);

2.  Parse the XSLT stylesheet.

        xslDomdoc = XmlLoadDom(xctx, &err, "file", xslFile, "base_uri", baseuri, NULL);

3.  Create an XSLT processor for the stylesheet

        xslproc = XmlXslCreate (xctx, xslDomdoc, baseuri, &err);

4.  Parse the instance XML document.

        xmlDomdoc = XmlLoadDom(xctx, &err, "file", xmlFile,  "base_uri", baseuri, NULL);

5.  Set the output (optional). Default is Document Object Model (DOM).

        err = XmlXslSetOutputStream(xslproc, &stream);

6.  Transform the XML document. This step can be repeated with the same or other XML documents.

        err = XmlXslProcess (xslproc, xmlDomdoc, FALSE);

7.  Get the output (if DOM).

        node = XmlXslGetOutput(xslproc);

8.  Delete objects.

        XmlXslDestroy(xslproc);
        XmlDestroy(xctx);

#### 4.2.2 XPath Processor Usage Example

A typical scenario of using the package APIs is described.

Follow these steps:

1.  Create and use an XML meta-context object.

        xctx = XmlCreate(&err,...);

2.  Parse the XML document or get the current node from already existing DOM.

        node = XmlLoadDom(xctx, &err, "file", xmlFile,  "base_uri", baseuri, NULL);

3.  Create an XPath processor.

        xptproc = XmlXPathCreateCtx(xctx, NULL, node, 0, NULL);

4.  Parse the XPath expression.

        exp = XmlXPathParse (xptproc, xpathexpr, &err);

5.  Evaluate the XPath expression.

        obj = XmlXPathEval(xptproc, exp, &err);

6.  Delete the objects.

        XmlXPathDestroyCtx (xptproc);
        XmlDestroy(xctx);

#### 4.2.3 Using the C XSLT Processor Command-Line Utility

You can call the C Oracle XSLT processor as an executable by invoking `bin/xsl`.

    xsl [switches] stylesheet instance
    or
    xsl -f [switches] [document filespec]

If no stylesheet is provided, no output is generated. If there is a stylesheet, but no output file, output goes to `stdout`.

Table 4-1 lists the command line options.

Table 4-1 XSLT Processor for C: Command Line Options

| Option          | Description                                                                                                       |
|:----------------|:------------------------------------------------------------------------------------------------------------------|
| `-B BaseUri`    | Set the Base URI for XSLT processor: `BaseUri` of `http://pqr/xsl.txt` resolves `pqr.txt` to `http://pqr/pqr.txt` |
| `-e encoding`   | Specify default input file encoding (`-ee` to force).                                                             |
| `-E encoding`   | Specify DOM or Simple API for XML (SAX) encoding.                                                                 |
| `-f`            | File—interpret as filespec, not Universal Resource Identifier (URI).                                              |
| `-G xptrexprs`  | Evaluates XPointer schema examples given in a file.                                                               |
| `-h`            | Help—show this usage. (Use `-hh` for more options.)                                                               |
| `-hh`           | Show complete options list.                                                                                       |
| `-i n`          | Number of times to iterate the XSLT processing.                                                                   |
| `-l language`   | Language for error reporting.                                                                                     |
| `-o XSLoutfile` | Specifies output file of XSLT processor.                                                                          |
| `-v`            | Version—display parser version then exit.                                                                         |
| `-V var value`  | Test top-level variables in C XSLT.                                                                               |
| `-w`            | White Space—preserve all white space.                                                                             |
| `-W`            | Warning—stop parsing after a warning.                                                                             |

#### 4.2.4 Accessing Oracle XSLT processor for C

Oracle XSLT processor for C is part of the standard installation of Oracle Database.

**See Also:**

- [Oracle Database XML C API Reference](../caxml/package-XSLT-API.md), XSLT APIs for C

- [Oracle Database XML C API Reference](../caxml/package-XPath-API.md), XPath APIs for C

- [XDK on OTN](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=otn_db_xdk_overview)

### 4.3 Using the Demo Files Included with the Software

Directory `$ORACLE_HOME/xdk/demo/c/parser/` contains several XML applications that show how to use the XSLT for C.

Table 4-2 XSLT for C Demo Files

| Sample File Name   | Description                                                                                                                                              |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XSLSample.c`      | Source for `XSLSample` program.                                                                                                                          |
| `XSLSample.std`    | Expected output from `XSLSample`.                                                                                                                        |
| `class.xml`        | XML file that can be used with `XSLSample`.                                                                                                              |
| `iden.xsl`         | Stylesheet that can be used with `XSLSample`.                                                                                                            |
| `cleo.xml`         | XML version of Shakespeare's play.                                                                                                                       |
| `XVMSample.c`      | Sample usage of XVM and compiler. It takes two file names as input—XML file and XSLT stylesheet file.                                                    |
| `XVMXPathSample.c` | Sample usage of XVM and compiler. It takes XML file name and `XPath` expression as input. Generates the result of the evaluated `XPath` expression.      |
| `XSLXPathSample.c` | Sample usage of `XSL/XPath` processor. It takes XML file name and `XPath` expression as input. Generates the result of the evaluated `XPath` expression. |

#### 4.3.1 Building the C Demo Programs for XSLT

Change directories to the demo directory and read the `README` file. That file explains how to build the sample programs according to your operating system.

Here is the usage of XSLT processor sample `XSLSample`, which takes two files as input, the XML file and the XSLT stylesheet:

    XSLSample xmlfile xslss
