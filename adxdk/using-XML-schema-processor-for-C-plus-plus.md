An explanation is given of how to use the Extensible Markup Language (XML) schema processor for C++.

**Note:**

Use the unified C++ application programming interface (API) in `xml.hpp` for Oracle XML Developer's Kit (XDK) applications. The older, nonunified C++ API in `oraxml.hpp` is deprecated and supported only for backward compatibility. It will be removed in a future release.

### 30.1 Oracle XML Schema Processor for C++

The XML Schema processor for C++ is a companion component to the Extensible Markup Language (XML) parser for C++ that allows support to simple and complex data types into XML applications.

The XML Schema processor for C++ supports the World Wide Web Consortium (W3C) XML Schema Recommendation. This makes writing custom applications that process XML documents straightforward, and means that a standards-compliant XML Schema processor is part of XDK on each operating system where Oracle Database is ported.

#### 30.1.1 Oracle XML Schema for C++ Features

The features of the Oracle XML Schema processor for C++ are described.

These are the features:

- Supports simple and complex types

- Built upon the XML parser for C++

- Supports the W3C XML Schema Recommendation

The XML Schema processor for C++ class is `OracleXml::Parser::SchemaValidator`.

**See Also:**

[Oracle Database XML C++ API Reference](../cpxml/package-Parser-API.md) schema validator interface

##### 30.1.1.1 Online Documentation

Documentation for Oracle XML Schema processor for C++ is located in `/xdk/doc/cpp/schema` directory in your install area.

#### 30.1.2 Standards Conformance for Oracle XML Schema Processor for C++

The standards to which the XML Schema Processor for C++ conforms are listed.

- W3C recommendation for Extensible Markup Language (XML) 1.0

- W3C recommendation for Document Object Model Level 1.0

- W3C recommendation for Namespaces in XML 1.0

- W3C recommendation for XML Schema 1.0

### 30.2 XML Schema Processor API

Interface `SchemaValidator` is an abstract template class to handle XML schema-based validation of XML documents.

#### 30.2.1 Invoking XML Schema Processor for C++

The XML Schema processor for C++ can be called as an executable by invoking `bin/schema` in the install area. This takes the arguments:

- XML instance document

- Optionally, a default schema

- Optionally, the working directory

Table 30-1 lists the options (can be listed if the option is invalid or -h is the option):

Table 30-1 XML Schema Processor for C++ Command-Line Options

| Option          | Description                                     |
|:----------------|:------------------------------------------------|
| `-0`            | Always exit with code 0 (success).              |
| `-e` `encoding` | Specify default input file encoding.            |
| `-E` `encoding` | Specify output/data/presentation encoding.      |
| `-h`            | Help. Prints these choices.                     |
| `-i`            | Ignore provided schema.                         |
| `-o` `num`      | Validation option.                              |
| `-p`            | Print document instance to `stdout` on success. |
| `-u`            | Force the Unicode path.                         |
| `-v`            | Version—display version, then exit.             |

The XML Schema processor for C++ can also be invoked by writing code using the supplied APIs. The code must be compiled using the headers in the `include` subdirectory and linked against the libraries in the `lib` subdirectory. See M`akefile` or `Make.bat` in the `xdk/demo/cpp/schema` directory for details on how to build your program.

Error message files in different languages are provided in the `mesg` subdirectory.

### 30.3 Running the Provided XML Schema for C++ Sample Programs

Directory `$ORACLE_HOME/xdk/demo/cpp/schema` contains a sample application that shows how to use Oracle XML Schema processor for C++ with its API.

Table 30-2 lists the sample files provided.

Table 30-2 XML Schema Processor for C++ Samples Provided

| Sample File         | Description                                                                                              |
|:--------------------|:---------------------------------------------------------------------------------------------------------|
| `Makefile`          | Makefile to build the sample programs and run them, verifying correct output.                            |
| `xsdtest.cpp`       | Trivial program which invokes the XML Schema for C++ API                                                 |
| `car.{xsd,xml,std}` | Sample schema, instance document, expected output respectively, after running `xsdtest` on them.         |
| `aq.{xsd,xml,std}`  | Second sample schema, instance document, expected output, respectively, after running `xsdtest` on them. |
| `pub.{xsd,xml,std}` | Third sample schema, instance document, expected output respectively, after running `xsdtest` on them.   |

To build the sample programs, run `make`.

To build the programs and run them, comparing the actual output to expected output:

    make sure
