`OracleXml` is the namespace for all XML C++ interfaces implemented by Oracle. It includes class `XmlException`, the root for all exceptions in XML, and the following namespaces:

- Ctx - namespace for TCtx related declarations, described in [Package Ctx APIs for C++](package-Ctx-API.md)

- Dom - namespace for DOM related declarations, described in [Package Dom APIs for C++](package-DOM-API.md)

- IO - namespace for input and output source declarations, described in [Package IO APIs for C++](package-IO-API.md)

- Parser - namespace for parser and schema validator declarations, described in [Package Parser APIs for C++](package-Parser-API.md)

- SOAP - namespace for the Simple Object Access Protocol declarations, described in [Package SOAP APIs for C++](package-SOAP-API.md)

- Tools - namespace for Tools::Factory related declarations, described in [Package Tools APIs for C++](package-Tools-API.md)

- XPath - namespace for XPath related declarations, described in [Package XPath APIs for C++](package-XPath-API.md)

- XPointer - namespace for XPointer related declarations, described in [Package XPointer APIs for C++](package-XPointer-API.md)

- Xsl - namespace for XSLT related declarations, described in [Package Xsl APIs for C++](package-Xsl-API.md)

**Note:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/adx_cp_unified.md)

### XmlException Interface

`XMLException` is the root interface for all XML exceptions. Table 1-1 summarizes the methods available through the `OracleXml `Package.

Table 1-1 Summary of OracleXml Package Interfaces

| Function     | Summary                                              |
|:-------------|:-----------------------------------------------------|
| getCode()    | Get Oracle XML error code embedded in the exception. |
| getMesLang() | Get current language (encoding) of error messages.   |
| getMessage() | Get Oracle XML error message.                        |

#### getCode()

This is a virtual member function that defines a prototype for implementation defined functions returning Oracle XML error codes (like error codes defined in xml.h) of the exceptional situations during execution

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (0 on success)

#### getMesLang()

This is a virtual member function that defines a prototype for user defined functions returning current language (encoding) of error messages for the exceptional situations during execution

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext *)` Current language (encoding) of error messages

#### getMessage()

This is a virtual member function that defines a prototype for implementation defined functions returning Oracle XML error messages of the exceptional situations during execution.

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message
