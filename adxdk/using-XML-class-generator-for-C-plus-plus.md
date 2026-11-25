Topics here explain how to use the Extensible Markup Language (XML) class generator for C++.

### 32.1 Accessing the XML C++ Class Generator

The XML C++ class generator is provided with Oracle Database.

### 32.2 Using the XML C++ Class Generator

The XML C++ class generator creates source files from an XML document type definition (DTD) or XML schema. It generates a class for each defined element. The classes are then used in a C++ program to construct XML documents that conform to the DTD or XML schema.

This is useful when an application wants to send an XML message to another application based on an agreed-upon DTD or XML Schema, or as the back end of a Web form to construct an XML document. Using these classes, C++ applications can construct, validate, and print XML documents that comply with the input.

The class generator works with the Oracle XML parser for C++, which parses the input and passes the parsed document to the class generator.

#### 32.2.1 External DTD Parsing

The XML C++ class generator can also parse an external DTD directly without requiring a complete (dummy) document by using the Oracle XML parser for C++ routine `xmlparsedtd()`. The provided command-line program `xmlcg` has a `-d` option that is used to parse external DTDs.

### 32.3 Using the XML C++ Class Generator Command-Line Utility

The standalone class generator can be called as an executable by invoking `bin/xmlcg`.

You can invoke the C++ class generator from the command line:

    xmlcg [options] input_file

Table 32-1 C++ Class Generator Options

| Option           | Description                                                                             |
|:-----------------|:----------------------------------------------------------------------------------------|
| `-d` `name`      | Input is an external DTD or a DTD file. Generates `name``.cpp` and `name``.h.`          |
| `-o` `directory` | Output directory for generated files (the default is the current directory).            |
| `-e` `encoding`  | Default input file encoding.                                                            |
| `-h`             | Show this usage help.                                                                   |
| `-v`             | Show the class generator version validator options.                                     |
| `-s ``name`      | Input is an XML Schema file with the given name. Generates `name``.cpp` and `name``.h`. |

`input_file` is the name of the parsed XML document with `<!DOCTYPE>` definitions, or parsed DTD, or an XML Schema document. The XML document must have an associated DTD.

The DTD input to the XML C++ class generator is an XML document containing a DTD, or it is an external DTD. The document body itself is ignored — only the DTD is relevant, though the document must conform to the DTD.

If invalid options were used, or no input was provided, a usage message is output.

Two source files are output, a `name``.h` header file and a C++ file, `name``.cpp`. These are named after the DTD file.

The output files are typically used to generate XML documents.

Constructors are provided for each class (element) that allow an object to be created in these ways:

- Initially empty, then adding the children or data after the initial creation

- Created with the initial full set of children or initial data

A method is provided for `#PCDATA` (and Mixed) elements to set the data and, when appropriate, set an element's attributes.

#### 32.3.1 Input to the XML C++ Class Generator

The input is an XML document containing a DTD. The document body itself is ignored; only the DTD is relevant, though the dummy document must conform to the DTD. The underlying XML parser accepts only file names for the document and associated external entities.

### 32.4 Using the XML C++ Class Generator Examples

The demo XML C++ class generator files are described.

Table 32-2 XML C++ Class Generator Files

| File Name                                   | Description                                                                                       |
|:--------------------------------------------|:--------------------------------------------------------------------------------------------------|
| `CG.cpp`                                    | Sample program                                                                                    |
| `CG.xml`                                    | XML file contains DTD and dummy document                                                          |
| `CG.dtd`                                    | DTD file referenced by `CG.xml`                                                                   |
| `Make.bat` on Windows<br>`Makefile` on UNIX | Batch file (on Windows) or Make file (on UNIX) to generate classes and build the sample programs. |
| `README`                                    | A readme file with these instructions                                                             |

The `make.bat` batch file (on Windows) or `Makefile` (on UNIX) does the following:

- Generate classes based on `CG.xml` into `Sample.h` and `Sample.cpp`

- Compile the program `CG.cpp` (using `Sample.h`), and link this with the Sample object into an executable named `CG.exe` in the...`\bin` (or ...`/bin`) directory.

#### 32.4.1 XML C++ Class Generator Example 1: XML — Input File to Class Generator, CG.xml

XML file `CG.xml` is presented. It is input to XML C++ class generator. It references the DTD file, `CG.dtd`.

    <?xml version="1.0"?>
    <!DOCTYPE Sample SYSTEM "CG.dtd">
      <Sample>
        <B>Be!</B>
        <D attr="value"></D>
        <E>
          <F>Formula1</F>
          <F>Formula2</F>
        </E>
      </Sample>

#### 32.4.2 XML C++ Class Generator Example 2: DTD — Input File to Class Generator, CG.dtd

DTD file `CG.dtd` is presented. It is referenced by XML file `CG.xml`, which is input to XML C++ class generator.

    <!ELEMENT Sample (A | (B, (C | (D, E))) | F)>
    <!ELEMENT A (#PCDATA)>
    <!ELEMENT B (#PCDATA | F)*>
    <!ELEMENT C (#PCDATA)>
    <!ELEMENT D (#PCDATA)>
    <!ATTLIST D attr CDATA #REQUIRED>
    <!ELEMENT E (F, F)>
    <!ELEMENT F (#PCDATA)>

#### 32.4.3 XML C++ Class Generator Example 3: CG Sample Program

Sample program CG, `CG.cpp`, is presented.

It does the following:

1.  Initializes the XML parser.

2.  Loads the DTD (by parsing the DTD-containing file—the dummy document part is ignored).

3.  Creates some objects using the generated classes.

4.  Invokes the validation function which verifies that the constructed classes match the DTD.

5.  Writes the constructed document to `Sample.xml`.

<!-- -->

    //////////////////////////////////////////////////////////////////////////////
    // NAME        CG.cpp
    // DESCRIPTION Demonstration program for C++ class generator usage
    //////////////////////////////////////////////////////////////////////////////

    #ifndef ORAXMLDOM_ORACLE
    # include <oraxmldom.h>
    #endif

    #include <fstream.h>

    #include "Sample.h"

    #define DTD_DOCUMENT "CG.xml"
    #define OUT_DOCUMENT Sample.xml"

    int main()
    {
        XMLParser parser;
        Document *doc;
        Sample   *samp;
        B        *b;
        D        *d;
        E        *e;
        F        *f1, *f2;
        fstream  *out;
        ub4       flags = XML_FLAG_VALIDATE;
        uword     ecode;

        // Initialize XML parser
        cout << "Initializing XML parser...\n";
        if (ecode = parser.xmlinit())
        {
            cout << "Failed to initialize parser, code " << ecode << "\n";
            return 1;
        }

        // Parse the document containing a DTD; parsing just a DTD is not
        // possible yet, so the file must contain a valid document (which
        // is parsed but we're ignoring).
        cout << "Loading DTD from " << DTD_DOCUMENT << "...\n";
        if (ecode = parser.xmlparse((oratext *) DTD_DOCUMENT, (oratext *)0, flags))
        {
            cout << "Failed to parse DTD document " << DTD_DOCUMENT <<
            ", code " << ecode << "\n";
            return 2;
        }

        // Fetch dummy document
        cout << "Fetching dummy document...\n";
        doc = parser.getDocument();

        // Create the constituent parts of a Sample
        cout << "Creating components...\n";
        b = new B(doc, (String) "Be there or be square");
        d = new D(doc, (String) "Dit dah");
        d->setattr((String) "attribute value");
        f1 = new F(doc, (String) "Formula1");
        f2 = new F(doc, (String) "Formula2");
        e = new E(doc, f1, f2);

        // Create the Sample
        cout << "Creating top-level element...\n";
        samp = new Sample(doc, b, d, e);

        // Validate the construct
        cout << "Validating...\n";
        if (ecode = parser.validate(samp))
        {
         cout << "Validation failed, code " << ecode << "\n";
         return 3;
        }

        // Write out doc
        cout << "Writing document to " << OUT_DOCUMENT << "\n";
        if (!(out = new fstream(OUT_DOCUMENT, ios::out)))
        {
          cout << "Failed to open output stream\n";
          return 4;
        }
        samp->print(out, 0);
        out->close();

        // Everything's OK
        cout << "Success.\n";

        // Shut down
        parser.xmlterm();
        return 0;
    }

    // end of CG.cpp
