The security measures to be taken when using software programs that are built using XDK are explained in this chapter.

### 2.1 Implementing Security for Java

The process to implement security for Java programs.

#### 2.1.1 Securing XSLT Processing with Oracle XML Developer's Kit

Before using Oracle XML Developer’s Kit for XSLT processing you need to secure it by setting some configuration options.

You must enable secure processing for both the `XSLProcessor` API and the JAXP transformer API, as follows.

- Use this Java code to enable the secure processing mode for `XSLProcessor`:

      processor.setAttribute(XMLConstants.FEATURE_SECURE_PROCESSING, Boolean.TRUE); 

- Use this Java code to enable the secure processing mode for `SAXTransformerFactory` of the JAXP transformer API:

      factory.setFeature(XMLConstants.FEATURE_SECURE_PROCESSING, true); 

Together, those settings improve XML-parsing security in the following ways:

- The settings block access to external resources, by default.

  Developers can then use `org.xml.sax.EntityResolver` or `javax.xml.transform.URIResolver` to resolve `include` and `import` elements in an XSL stylesheet. They can use Java interface `URIResolver` to provide XPath or XSLT functions access to trusted external resources.

- The settings block the use of Java reflection to execute Java code.

  Developers can convert trusted Java classes to interface `javax.xml.xpath.XPathFunction` and use interface `javax.xml.xpath.XPathFunctionResolver` to resolve them.

- The settings limit recursive entity expansion.

  This helps avoid a common denial-of-service attack from excessive resource consumption.

  **Note:**

  Although this can limit recursive entity expansion, XDK cannot limit resource consumption during XML transformation. An XSL stylesheet can include an infinite loop or otherwise consume resources extravagantly. For this reason, XSL stylesheets must not be accepted from untrusted sources or external entities. Test all stylesheets used, to ensure that they do not consume excessive resources.

In addition, Oracle recommends that all code that performs XSLT processing of data or files obtained from users or from external, untrusted entities check that secure processing is enabled for both the XSLProcessor API and the JAXP transformer API. Not doing this opens a security vulnerability. After the XSL processor has been secured, accessing external resources and running Java extension functions is not allowed.

##### Arbitrary Security Exemptions

If you want to arbitrarily override security restrictions, you can use the following options:

- Perform any of the following modifications to allow access to some external sources:

  - Set `URIResolver` to either `SAXTransformerFactory` or `XSLProcessor`, using the method `setURIResolver()`.

  - Set `EntityResolver` to `XSLProcessor` using the method `setEntityResolver()`.

- Use the Java interface `oracle.xml.xslt.XSLSecurityManager` to register a whitelist of Java classes and methods with which you can use Java reflection extension functions.

- Register `XSLSecurityManager` using the `XSLProcessor` method `setAttribute()` to run an extension function that you know to be safe:

      processor.setAttribute(XSLProcessor.SECURITY_MANAGER, securityManager);

- Use a simple API on `XSLSecurityManager` to implement a whitelist of Java classes and methods:

      boolean checkExtensionFunction(String className, String fnName);

#### 2.1.2 Using the Oracle XML Parser Safely

Like many XML parsers, by default the XDK parser tries to resolve external references. An attacker can exploit this behavior to perform XML External Entity (XXE) and XML Entity Expansion (XEE) attacks. To avoid this vulnerability, disable the use of arbitrary references to external resources, and disable unconstrained entity expansion.

To implement a global security setting, which blocks all parsers that are created within the system from using external entities, set the Java system property `oracle.xdkjava.security.resolveEntityDefault` to `false`.

To block entity expansion for a particular parser, or to limit the number of levels of entity expansion, set the attribute `XMLParser.RESOLVE_ENTITY_DEFAULT`, or `XMLParser.ENTITY_EXPANSION_DEPTH` to the parser.

For example:

    DOMParser domParser = new DOMParser(); // Extend oracle.xml.parser.v2.XMLParser
    domParser.setAttribute(DOMParser.EXPAND_ENTITYREF, false); // Do not  expand entity references
    domParser.setAttribute(DOMParser.DTD_OBJECT, dtdObj);  // dtdObj is an instance of oracle.xml.parser.v2.DTD
    domParser.setAttribute(DOMParser.ENTITY_EXPANSION_DEPTH, 12); // Do not allow more than 11 levels of entity expansion

If you use JAXP to enable XML parsing, then set `FEATURE_SECURE_PROCESSING` to `true` for `DocumentBuilderFactory` or `SAXParserFactor`. This blocks the expansion of external entities, limits entity expansion to a depth of 11, and limits the entity expansion count to 64000.

    my_factory.setFeature(XMLConstants.FEATURE_SECURE_PROCESSING, true);

**See Also:**

[XML External Entity (XXE) Prevention Cheat Sheet](https://www.owasp.org/index.php/XML_External_Entity_(XXE)_Prevention_Cheat_Sheet)

Example 2-1 Improving Safety of Java Code that Uses an XML Parser

This Java snippet blocks resolution of external entities, limits the number of entity-expansion levels, and limits the number of entity expansions.

    try {
      DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
      dbf.setNamespaceAware(true);
      dbf.setXIncludeAware(false);
      dbf.setExpandEntityReferences(false);  // Disable expanding of entities
      try {
        dbf.setFeature(XMLConstants.FEATURE_SECURE_PROCESSING, true);
      } catch (Throwable e) {
          //handle old parser version
          ...
      }
      DocumentBuilder dp = dbf.newDocumentBuilder();
      // Make resolveEntity just throw an exception.
      //   (If you really need to support external references
      //    then resolve publicId only against trusted values.)
      dp.setEntityResolver(new EntityResolver() {
        public InputSource resolveEntity(String publicId, String systemId)
                             throws DOMException, IOException {
          throw new DOMException((short)0, "Security Violation");
        }
      });
    ...

### 2.2 Implementing Security for C

The process to implement security for C programs.

#### Block Insecure Accesses

Usually, there are two sets of XDK C APIs that take the risks of the XXE attack: one set uses the function `LpxInitEncoded()`and the other set uses the function `XmlCreate()`or `XmlCreateNew()`

For `LpxInitEncoded()`, feed the flags `LPX_FLAG_URL_DONT_OPEN ` and `LPX_FLAG_FILE_DONT_OPEN` into the parser API to block external resource accesses.

For example:

    LpxBufferParse ( ctx,
                     (oratext *) buf,
                     (size_t) lstlen ( buf ),
                     (oratext *) "UTF-8", (lx_langid) 0, (lxglo *) 0,
                     LPX_FLAG_URL_DONT_OPEN | LPX_FLAG_FILE_DONT_OPEN);

For `XmlCreate()`or `XmlCreateNew()`, set the parameter `no_ri_open` to `TRUE` when creating the context `xctx`. This setting will block insecure accesses for parser APIs which use `xctx`.

For example:

    xctx = XmlCreateNew(&xerr, (oratext *) "test",
                        (oratext **)NULL, 0, (oratext *)NULL,
                        "data_encoding", “AL32UTF8”,
                        "input_encoding", "AL32UTF8",
                        "no_ri_open",  "TRUE", /* disallow URI resolution */
                        "error_handler", test_errmsg,
                        NULL);

The parameter `no_ri_open` can also be set to `TRUE` in DOM APIs to block insecure accesses. Setting this flag in DOM APIs ensures that security is enforced even when this flag is not set in `XmlCreate()`.

For example:

    doc = XmlLoadDom(xctx, &xerr,
                     "file", filename,
                     "discard_whitespace", TRUE,
                     "validate", TRUE,
                     "no_ri_open", TRUE, /* disallow URI resolution */
                     NULL);

#### Allow Arbitrary Accesses

When users want to allow arbitrary references to external resources or make the accesses under their own control, they can implement the following steps:

1.  Set `no_ri_open` to `FALSE` in the locations shown in the previous examples.

2.  Develop customized open, read and close callback functions and initialize an `OraSteam` using these functions.

3.  Override access to `xctx` with `OraSteam`

For example:

    ostream = OraStreamInit(actx, (oratext *)"test", &oerr,
                            "open", http_open,
                            "read", http_read,
                            "close", http_close,
                            NULL);
    xerr = XmlAccess(xctx, XML_ACCESS_HTTP, ostream);

The code creates an instance of `ostream` by providing three callbacks. The created stream will override the access inside `xctx` using `XmlAccess`. `xctx` is used when calling APIs such as `XmlLoadDom`. Hence, the user has the option to create rules based on which they can access external resources.

### 2.3 Security for C++

By default, C++ APIs block accesses to external resources – thereby ensuring security. However, users can override this security restriction and allow arbitrary references to external resources based on their discretion.

The `xmlctx.hpp` header file uses the `CXmlCtx(bool no_ri_open)` API to initialize the `xctx` context and set the parameter `no_ri_open`. When the `no_ri_open` parameter is set to `true`, parser APIs that use `xctx` will not be able to access external resources. When the `no_ri_open` parameter is set to `false`, parser APIs that use `xctx` will be able to access external resources.

By default, parser APIs that use `xctx` cannot access external resources. To allow access, set the `no_ri_open` parameter to `false` as shown below:

    xctx = CXmlCtx(FALSE); /* allow URI resolution */

**Caution:**

Allowing access to external resources can cause XML External Entity (XXE) and XML Entity Expansion (XEE) attacks. The user should be cautions when overriding the security restriction and allowing access to external resources.
