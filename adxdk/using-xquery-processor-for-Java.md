An explanation is given of how to use the Oracle XML Developer's Kit (XDK) XQuery processor for Java.

### 15.1 Introduction to the XQuery Processor for Java

XDK provides a standalone XQuery processor for use by Java applications. XQuery is the World Wide Web Consortium (W3C) standard query language for Extensible Markup Language (XML). Using XQuery to process XML within a Java application can improve developer productivity and application performance.

Applications written with XQuery often require less code, run faster, and use less memory than applications written fully in Java.

JSR 225: XQuery API for Java (XQJ) defines how queries can be executed from a Java application. To use XQJ, your application must run with Java version 1.6. In addition, these JAR files are required:

- `jlib/oxquery.jar`

- `jlib/xqjapi.jar`

- `jlib/orai18n-mapping.jar`

- `lib/xmlparserv2.jar`

- `xdk/jlib/apache-xmlbeans.jar`

The directory paths for these Java Archive (JAR) files are relative to the `ORACLE_HOME` directory of your Oracle Database installation.

Example 15-1 shows how to execute a simple "Hello World" query using XQuery API for Java (XQJ). Because the XQuery processor runs directly in the Java Virtual Machine (JVM), you need no database or server to run this example. The example prints the output `<hello-world>2</hello-world>`.

This chapter describes the features and extensions that are specific to the Oracle implementation of XQuery. General information about XQuery and XQJ is documented outside of this document.

**See Also:**

- [Oracle Database XML Java API Reference](../jaxml/index.md), `XQuery Packages`, for the related API documentation

- [JSR-000225 XQuery API for Java](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=jcp_org_jsr225)

- [XQuery 3.0: An XML Query Language](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquery_30)

**Note:**

Oracle also implements XQuery and XQJ as part of Oracle XML DB. See [Using XQuery API for Java to Access Oracle XML DB](using-xquery-API-for-Java-to-access-XML-DB.md) for details about Oracle XML DB.

Example 15-1 Simple Query Using XQJ

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;

    import oracle.xml.xquery.OXQDataSource;

    public class HelloWorld {

        public static void main(String[] args) throws XQException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();
            String query = "<hello-world>{1 + 1}</hello-world>";
            XQPreparedExpression expr = con.prepareExpression(query);
            XQSequence result = expr.executeQuery();

            // prints "<hello-world>2</hello-world>"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }

    }

### 15.2 XQJ Entity Resolution

XDK extends XQJ with an entity resolver framework for controlling how documents, schemas, modules, collations, and external functions are obtained during query processing. The examples in this section show how to use an entity resolver for several types of entities.

See the class `oracle.xml.xquery.OXQEntity` in [Oracle Database XML Java API Reference](../jaxml/index.md) for a complete list of the types of entities that the query processor can request.

#### 15.2.1 Resolution of Documents for fn:doc

The example in this section shows how you can use an entity resolver to determine which document is returned by XQuery function `fn:doc`.

Example 15-2 displays the contents of `books.xml`.

Example 15-3 displays the contents of `books.xq`.

Example 15-4 shows how to execute the query `books.xq` with a custom entity resolver.

The instance of `MyEntityResolver` is passed to the XQuery processor by setting it on the connection. The XQuery processor invokes the entity resolver during query processing to get the document to be returned by the `fn:doc` function.

Example 15-2 books.xml

    <books>
      <book>
        <title>A Game of Thrones</title>
        <author><first>George</first><last>Martin</last></author>
        <price>10.99</price>
      </book>
      <book>
        <title>The Pillars of the Earth</title>
        <author><first>Ken</first><last>Follett</last></author>
        <price>7.99</price>
      </book>
    </books>

Example 15-3 books.xq

    for $book in fn:doc('books.xml')/books/book
    where xs:decimal($book/price) gt 10.00
    return
      $book/title

Example 15-4 Executing a Query with a Custom Entity Resolver

    import java.io.File;
    import java.io.FileInputStream;
    import java.io.IOException;
    import java.net.URI;

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQEntity;
    import oracle.xml.xquery.OXQEntityKind;
    import oracle.xml.xquery.OXQEntityLocator;
    import oracle.xml.xquery.OXQEntityResolver;
    import oracle.xml.xquery.OXQEntityResolverRequestOptions;
    import oracle.xml.xquery.OXQView;

    public class ResolveDocument {

        private static class MyEntityResolver extends OXQEntityResolver {
            @Override
            public OXQEntity resolveEntity(OXQEntityKind kind, OXQEntityLocator locator,
                    OXQEntityResolverRequestOptions options) throws IOException {
                if (kind == OXQEntityKind.DOCUMENT) {
                    URI systemId = locator.getSystemIdAsURI();
                    if ("file".equals(systemId.getScheme())) {
                        File file = new File(systemId);
                        FileInputStream input = new FileInputStream(file);
                        OXQEntity result = new OXQEntity(input);
                        result.enlistCloseable(input);
                        return result;
                    }
                }
                return null;
            }
        }

        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            // OXQView is used to access Oracle extensions on XQJ objects.
            OXQConnection ocon = OXQView.getConnection(con);
            ocon.setEntityResolver(new MyEntityResolver());

            File query = new File("books.xq");

            // Relative URIs are resolved against the base URI before invoking the entity resolver.
            // The relative URI 'books.xml' used in the query will be resolved against this URI.
            XQStaticContext ctx = con.getStaticContext();
            ctx.setBaseURI(query.toURI().toString());

            FileInputStream queryInput = new FileInputStream(query);
            XQPreparedExpression expr = con.prepareExpression(queryInput, ctx);
            queryInput.close();
            XQSequence result = expr.executeQuery();

            // Prints "<title>A Game of Thrones</title>"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example generates this output:

    <title>A Game of Thrones</title>

#### 15.2.2 Resolution of External XQuery Functions

You can use an entity resolver to define the implementation of an XQuery external function.

For each external XQuery function that is declared in a query, the entity resolver is called with the entity kind `oracle.xml.xquery.OXQEntityKind.EXTERNAL_FUNCTION`. The `oracle.xml.xquery.OXQEntityLocator` instance that is passed in the call to the entity resolver provides the name of the XQuery function and its argument types. The entity resolver can then return any class that extends `oracle.xml.xquery.OXQFunctionEvaluator` and has a public constructor. The XQuery processor then instantiates the returned class. When the XQuery external function call is evaluated, method `evaluate()` is invoked.

Example 15-5 displays an XQuery query that is the content of file `trim.xq`.

External XQuery function `util:trim` removes white space from the beginning and end of a string value. This function is implemented in Java and called within the query.

Example 15-6 uses `trim.xq` and shows how to define the implementation of an external XQuery function. The entity resolver in this example returns a class that extends `OXQFunctionEvaluator`.

In some cases it is more convenient to return a Java static method instead of a class. When a static method is returned, the query processor automatically maps the method arguments and the return value to the XQuery data model, as defined by the XQJ specification.

Example 15-7 also runs `trim.xq`, but in this case the external function is bound to a Java static method.

Example 15-5 trim.xq

    declare namespace util = "http://example.com/util";

    declare function util:trim($arg as xs:string) as xs:string external;

    (: a string with surrounding white space :)
    declare variable $input := "   John Doe    ";

    <result>{util:trim($input)}</result>

Example 15-6 Defining the Implementation of an External XQuery Function

    import java.io.FileInputStream;
    import java.io.IOException;
    import java.util.Collections;

    import javax.xml.namespace.QName;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQEntity;
    import oracle.xml.xquery.OXQEntityKind;
    import oracle.xml.xquery.OXQEntityLocator;
    import oracle.xml.xquery.OXQEntityResolver;
    import oracle.xml.xquery.OXQEntityResolverRequestOptions;
    import oracle.xml.xquery.OXQFunctionContext;
    import oracle.xml.xquery.OXQFunctionEvaluator;
    import oracle.xml.xquery.OXQFunctionMetaData;
    import oracle.xml.xquery.OXQView;

    public class ResolveExternalFunction {

        public static class TrimFunction extends OXQFunctionEvaluator {
            @Override
            public XQSequence evaluate(OXQFunctionContext context, XQSequence[] params) throws XQException {
                XQConnection con = context.getConnection();
                XQSequence arg = params[0];
                String value = arg.getSequenceAsString(null);
                String trimmed = value.trim();
                return con.createSequence(Collections.singleton(trimmed).iterator());
            }
        }

        private static class MyEntityResolver extends OXQEntityResolver {
            @Override
            public OXQEntity resolveEntity(OXQEntityKind kind, OXQEntityLocator locator,
                    OXQEntityResolverRequestOptions options) throws XQException, IOException {
                if (kind == OXQEntityKind.EXTERNAL_FUNCTION) {
                    OXQFunctionMetaData metaData = (OXQFunctionMetaData)locator.getExtension();
                    QName name = metaData.getName();
                    int arity = metaData.getParameterTypes().length;
                    if ("http://example.com/util".equals(name.getNamespaceURI()) &&
                        "trim".equals(name.getLocalPart()) && arity == 1) {
                        return new OXQEntity(TrimFunction.class);
                    }
                }
                return null;
            }
        }

        public static void main(String[] args) throws IOException, XQException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();
            OXQConnection ocon = OXQView.getConnection(con);
            ocon.setEntityResolver(new MyEntityResolver());

            FileInputStream query = new FileInputStream("trim.xq");
            XQPreparedExpression expr = con.prepareExpression(query);
            query.close();

            XQSequence result = expr.executeQuery();

            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example prints this output:` <result>John Doe</result>`.

Example 15-7 Binding an External Function to a Java Static Method

    import java.io.FileInputStream;
    import java.io.IOException;
    import java.lang.reflect.Method;

    import javax.xml.namespace.QName;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQEntity;
    import oracle.xml.xquery.OXQEntityKind;
    import oracle.xml.xquery.OXQEntityLocator;
    import oracle.xml.xquery.OXQEntityResolver;
    import oracle.xml.xquery.OXQEntityResolverRequestOptions;
    import oracle.xml.xquery.OXQFunctionMetaData;
    import oracle.xml.xquery.OXQView;

    public class ResolveExternalFunction2 {

        public static String trim(String value) {
            return value.trim();
        }

        private static class MyEntityResolver extends OXQEntityResolver {
            @Override
            public OXQEntity resolveEntity(OXQEntityKind kind, OXQEntityLocator locator,
                    OXQEntityResolverRequestOptions options) throws XQException, IOException {
                if (kind == OXQEntityKind.EXTERNAL_FUNCTION) {
                    OXQFunctionMetaData metaData = (OXQFunctionMetaData)locator.getExtension();
                    QName name = metaData.getName();
                    int arity = metaData.getParameterTypes().length;
                    if ("http://example.com/util".equals(name.getNamespaceURI()) &&
                        "trim".equals(name.getLocalPart()) && arity == 1) {
                        Method staticMethod = null;
                        try {
                            staticMethod = ResolveExternalFunction2.class.getMethod("trim", String.class);
                        } catch (NoSuchMethodException e) {
                            throw new IllegalStateException(e);
                        }
                        return new OXQEntity(staticMethod);
                    }
                }
                return null;
            }
        }

        public static void main(String[] args) throws IOException, XQException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();
            OXQConnection ocon = OXQView.getConnection(con);
            ocon.setEntityResolver(new MyEntityResolver());

            FileInputStream query = new FileInputStream("trim.xq");
            XQPreparedExpression expr = con.prepareExpression(query);
            query.close();

            XQSequence result = expr.executeQuery();

            // Prints "<result>John Doe</result>"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example prints the same output as for Example 15-6:` <result>John Doe</result>`.

#### 15.2.3 Resolution of Imported XQuery Modules

The entity resolver can locate the XQuery modules imported by an XQuery library module.

An XQuery library module provides functions and variables that can be imported by other modules. For each imported module, the entity resolver is called with the entity kind `oracle.xml.xquery.OXQEntityKind.MODULE`. Using the `oracle.xml.xquery.OXQEntityLocator` instance, you can invoke the `getSystemId()` method to get the location of the module being imported. If no location is provided in the module import, you can invoke the method `getNamespace()` to get the target namespace of the module. The entity resolver can then return the corresponding library module.

The example in this section shows how you can use an entity resolver to control the resolution of XQuery library modules.

Example 15-8 displays the contents of `math.xq`.

Example 15-9 displays the contents of `main.xq`.

Example 15-10 shows how to execute a query that imports a library module.

The query `main.xq` imports the library module `math.xq`, and then invokes the function `math:circumference` to compute the circumference of a circle.

Example 15-8 math.xq

    module namespace math = "http://example.com/math";

    declare variable $math:pi as xs:decimal := 3.14159265;

    declare function math:circumference($diameter as xs:decimal) {
       $math:pi * $diameter
    };

Example 15-9 main.xq

    import module namespace math = "http://example.com/math" at "math.xq";

    math:circumference(6.54)

Example 15-10 Executing a Query that Imports a Library Module

    import java.io.File;
    import java.io.FileInputStream;
    import java.io.IOException;
    import java.net.URI;

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQEntity;
    import oracle.xml.xquery.OXQEntityKind;
    import oracle.xml.xquery.OXQEntityLocator;
    import oracle.xml.xquery.OXQEntityResolver;
    import oracle.xml.xquery.OXQEntityResolverRequestOptions;
    import oracle.xml.xquery.OXQView;

    public class ResolveLibraryModule {

        private static class MyEntityResolver extends OXQEntityResolver {
            @Override
            public OXQEntity resolveEntity(OXQEntityKind kind, OXQEntityLocator locator,
                    OXQEntityResolverRequestOptions options) throws IOException {
                if (kind == OXQEntityKind.MODULE) {
                    URI systemId = locator.getSystemIdAsURI();
                    if (systemId != null && "file".equals(systemId.getScheme())) {
                        File file = new File(systemId);
                        FileInputStream input = new FileInputStream(file);
                        OXQEntity result = new OXQEntity(input);
                        result.enlistCloseable(input);
                        return result;
                    }
                }
                return null;
            }
        }

        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            // OXQView is used to access Oracle extensions on XQJ objects.
            OXQConnection ocon = OXQView.getConnection(con);
            ocon.setEntityResolver(new MyEntityResolver());

            File query = new File("main.xq");

            // Relative URIs are resolved against the base URI before invoking the entity resolver.
            // The relative URI 'math.xq' used in the query will be resolved against this URI.
            XQStaticContext ctx = con.getStaticContext();
            ctx.setBaseURI(query.toURI().toString());

            FileInputStream queryInput = new FileInputStream(query);
            XQPreparedExpression expr = con.prepareExpression(queryInput, ctx);
            queryInput.close();

            XQSequence result = expr.executeQuery();

            // Prints the result: "20.546015931"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example generates this output:

    20.546015931

#### 15.2.4 Resolution of XML Schemas Imported by an XQuery Query

You can use an entity resolver to control which XML schema is imported by an XQuery query.

An XQuery schema import imports type definitions and declarations of elements and attributes from an XML schema. You can use imported declarations and definitions in a query to validate and test data instances.

Example 15-11 displays the contents of XML schema file `size.xsd`.

Example 15-12 displays the contents of XQuery file `size.xq`.

Example 15-13 shows how to execute a query that imports a schema.

`size.xq` uses the type `shirt-size` defined in `size.xsd` to test a list of values.

Example 15-11 size.xsd

    <xs:schema
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      targetNamespace="http://example.com/size">

      <xs:simpleType name="shirt-size">
        <xs:restriction base="xs:string">
          <xs:enumeration value="XS"/>
          <xs:enumeration value="S"/>
          <xs:enumeration value="M"/>
          <xs:enumeration value="L"/>
          <xs:enumeration value="XL"/>
        </xs:restriction>
      </xs:simpleType>

    </xs:schema>

Example 15-12 size.xq

    import schema namespace ns = "http://example.com/size" at "size.xsd";

    for $size in ("S", "big", "XL", 42)
    return
      if ($size castable as ns:shirt-size) then
        ns:shirt-size($size)
      else
        concat("INVALID:", $size)

Example 15-13 Executing an XQuery Query that Imports an XML Schema

    import java.io.File;
    import java.io.FileInputStream;
    import java.io.IOException;
    import java.net.URI;

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQEntity;
    import oracle.xml.xquery.OXQEntityKind;
    import oracle.xml.xquery.OXQEntityLocator;
    import oracle.xml.xquery.OXQEntityResolver;
    import oracle.xml.xquery.OXQEntityResolverRequestOptions;
    import oracle.xml.xquery.OXQView;

    public class ResolveSchema {

        private static class MyEntityResolver extends OXQEntityResolver {
            @Override
            public OXQEntity resolveEntity(OXQEntityKind kind, OXQEntityLocator locator,
                    OXQEntityResolverRequestOptions options) throws IOException {
                if (kind == OXQEntityKind.SCHEMA) {
                    URI systemId = locator.getSystemIdAsURI();
                    if (systemId != null && "file".equals(systemId.getScheme())) {
                        File file = new File(systemId);
                        FileInputStream input = new FileInputStream(file);
                        OXQEntity result = new OXQEntity(input);
                        result.enlistCloseable(input);
                        return result;
                    }
                }
                return null;
            }
        }

       public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            // OXQView is used to access Oracle extensions on XQJ objects.
            OXQConnection ocon = OXQView.getConnection(con);
            ocon.setEntityResolver(new MyEntityResolver());

            File query = new File("size.xq");

            // Relative URIs are resolved against the base URI before invoking the entity resolver.
            // The relative URI 'math.xq' used in the query will be resolved against this URI.
            XQStaticContext ctx = con.getStaticContext();
            ctx.setBaseURI(query.toURI().toString());

            FileInputStream queryInput = new FileInputStream(query);
            XQPreparedExpression expr = con.prepareExpression(queryInput, ctx);
            queryInput.close();

            XQSequence result = expr.executeQuery();

            // Prints "S INVALID:big XL INVALID:42"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example prints this output: `S INVALID:big XL INVALID:42`.

#### 15.2.5 Prefabricated Entity Resolvers for XQuery

XDK includes several implementations of `OXQEntityResolver` that you can use for common tasks such as file system and HTTP resolution. This can sometimes save you needing to implement your own entity resolver.

Example 15-14 shows how you can run the query in Example 15-3 using a prefabricated file resolver.

An instance of the factory `oracle.xml.xquery.OXQFileResolverFactory` is created from the connection. Then, this factory is used to create an entity resolver that resolves schemas, modules, and documents against the file system. By contrast with this example, Example 15-4 uses the custom entity resolver `MyEntityResolver` to resolve only documents against the file system.

XDK provides these entity resolver factories:

- `oracle.xml.xquery.OXQFileResolverFactory`: Creates an entity resolver that resolves 'file:' URIs for schema, module, and document locations.

- `oracle.xml.xquery.OXQHttpResolverFactory`: Creates an entity resolver that resolves 'http:' URIs for schema, module, and document locations.

- `oracle.xml.xquery.OXQCompositeResolverFactory`: Creates an entity resolver that delegates requests to other entity resolvers. For any kind of request, the resolver returns the first nonnull result it receives from one of the delegate resolvers.

- `oracle.xml.xquery.OXQJavaResolverFactory`: Creates an entity resolver that resolves external functions and modules to Java static methods or classes.

**See Also:**

[Oracle Database XML Java API Reference](../jaxml/index.md), package `oracle.xml.xquery`, for API information about these factory interfaces

Example 15-14 Executing a Query with a Prefabricated File Resolver

    import java.io.File;
    import java.io.FileInputStream;
    import java.io.IOException;

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQConnection;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQFileResolverFactory;
    import oracle.xml.xquery.OXQView;

    public class ResolverFactory {
        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            // OXQView is used to access Oracle extensions on XQJ objects.
            OXQConnection ocon = OXQView.getConnection(con);
            OXQFileResolverFactory factory = ocon.createEntityResolverFactory(OXQFileResolverFactory.class);
            ocon.setEntityResolver(factory.createResolver());

            File query = new File("books.xq");

            // Relative URIs are resolved against the base URI before invoking the entity resolver.
            // The relative URI 'books.xml' used in the query will be resolved against this URI.
            XQStaticContext ctx = con.getStaticContext();
            ctx.setBaseURI(query.toURI().toString());

            FileInputStream queryInput = new FileInputStream(query);
            XQPreparedExpression expr = con.prepareExpression(queryInput, ctx);
            queryInput.close();

            XQSequence result = expr.executeQuery();

            // Prints "<title>A Game of Thrones</title>"
            System.out.println(result.getSequenceAsString(null));

            result.close();
            expr.close();
            con.close();
        }
    }

The example prints this output: `<title>A Game of Thrones</title>`.

#### 15.2.6 Resolution of Other Types of Entity

You can use the XQJ entity resolver to obtain other entities, besides documents, schemas, modules, and external functions.

Table 15-1 describes these other entities.

Table 15-1 Descriptions of Various Types of Entity

| OXQEntityKind          | Description                                                                   |
|:-----------------------|:------------------------------------------------------------------------------|
| `TEXT`                 | Result of `fn:unparsed-text` and `fn:unparsed-text-lines`.                    |
| `ENVIRONMENT_VARIABLE` | Result of `fn:available-environment-variables` and `fn:environment-variable`. |
| `DOCUMENT_TYPE`        | Static type for function `fn:doc`.                                            |
| `COLLECTION`           | Documents returned by `fn:collection`.                                        |
| `URI_COLLECTION`       | URIs returned by `fn:uri-collection`.                                         |
| `XML_PARSER_FACTORY`   | StAX implementation used for parsing XML data.                                |
| `XML_ENTITY`           | Used when a StAX parser needs to resolve an external XML resource.            |
| `UPD_PUT`              | Controls the behavior of `fn:put`.                                            |
| `COLLATION`            | Controls the behavior of collation URIs.                                      |

For details on how these entity types are used, see class `oracle.xml.xquery.OXQEntity` in [Oracle Database XML Java API Reference](../jaxml/index.md).

### 15.3 XQuery Output Declarations

XQuery 3.0 defines output declarations, which you can use to set the values of serialization parameters from within a query.

An output declaration is an option declaration in namespace `http://www.w3.org/2010/xslt-xquery-serialization`. You use it in a query to declare and set serialization parameters on the static context.

By default, these static context serialization parameters are ignored, but they can be accessed using XQJ methods `OXQPreparedExpression#getExpressionStaticContext()` and `OXQStaticContext#getSerializationParameters()`.

Example 15-15 shows how to access the values of option declarations.

You can also use an option declaration when serializing the result of a query. Example 15-16 is similar to Example 15-15, but it uses the static context serialization parameters when serializing the result of the query.

**Note:**

The URI value of option `output:parameter-document` is resolved to a document using entity resolver `OXQEntityResolver` and entity kind `OXQEntityKind#DOCUMENT` — see Resolution of Other Types of Entity.

Example 15-15 Accessing the Values of Option Declarations

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQPreparedExpression;
    import oracle.xml.xquery.OXQSerializationParameters;
    import oracle.xml.xquery.OXQStaticContext;
    import oracle.xml.xquery.OXQView;

    public class OptionDeclarations1 {

        public static void main(String[] args) throws XQException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();
            String query =
                "declare option output:indent 'yes'; \n" +
                "declare option output:encoding 'UTF-16'; \n" +
                "<person><first>John</first><last>Doe</last></person>";

            XQPreparedExpression expr = con.prepareExpression(query);

            OXQPreparedExpression oexpr = OXQView.getPreparedExpression(expr);
            XQStaticContext ctx = oexpr.getExpressionStaticContext();
            OXQStaticContext octx = OXQView.getStaticContext(ctx);
            OXQSerializationParameters params = octx.getSerializationParameters();

            System.out.println("indent=" + params.isIndent());
            System.out.println("encoding=" + params.getEncoding());

            expr.close();
            con.close();
        }
    }

This produces the following output:

      indent=true
      encoding=UTF-16

Example 15-16 Using Option Declarations When Serializing a Query Result

    package oracle.xml.xquery.examples.published;

    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQResultSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQPreparedExpression;
    import oracle.xml.xquery.OXQSerializationParameters;
    import oracle.xml.xquery.OXQStaticContext;
    import oracle.xml.xquery.OXQView;

    public class OptionDeclarations2 {

        public static void main(String[] args) throws XQException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();
            String query =
                "declare option output:indent 'yes'; \n" +
                "declare option output:omit-xml-declaration 'no'; \n" +
                "<person><first>John</first><last>Doe</last></person>";

            XQPreparedExpression expr = con.prepareExpression(query);

            OXQPreparedExpression oexpr = OXQView.getPreparedExpression(expr);
            XQStaticContext ctx = oexpr.getExpressionStaticContext();
            OXQStaticContext octx = OXQView.getStaticContext(ctx);
            OXQSerializationParameters params = octx.getSerializationParameters();

            XQResultSequence result = expr.executeQuery();
            result.writeSequence(System.out, params.createProperties());
            result.close();

            expr.close();
            con.close();
        }
    }

This produces the following output:

    <?xml version="1.0" encoding="UTF-8"?>
    <person>
        <first>John</first>
        <last>Doe</last>
    </person>

### 15.4 Improving Application Performance and Scalability with XQuery

The XDK XQuery processor provides several features for improving the performance and scalability of your application.

#### 15.4.1 Streaming Query Evaluation

The XDK XQuery processor for Java supports streaming evaluation for many types of queries. Streaming evaluation requires a small amount of main memory, even when the input XML is very large.

To facilitate streaming evaluation, the following actions are recommended:

- Set the binding mode on the static context to deferred mode (see the method `javax.xml.xquery.XQStaticContext.setBindingMode(int)` in [Oracle Database XML Java API Reference](../jaxml/index.md)). If the binding mode is not deferred, the input XML is fully materialized when it is bound.

- Provide the input XML as an instance of `java.io.InputStream`, `java.io.Reader`, or `javax.xml.stream.XMLStreamReader`. Input XML is provided to the query processor by binding it to the expression, or by returning it from an entity resolver.

- Ensure that the `javax.xml.xquery.XQSequence` instance is consumed in a way that does not require materialization:

  - The string serialization methods `getSequenceAsString(...)` and `getItemAsString(...)` produce data as a string that is held in memory. Instead, use the `writeSequence(...)` or the `writeItem(...)` method to serialize the sequence.

  - The `getNode()` method builds a Document Object Model (DOM) node that is held in memory. Instead, consider using the `getSequenceAsStream()` or the `getItemAsStream()` method to get a Streaming API for XML (StAX) stream.

  - The `getItem()` method copies and materializes the current item in memory. Instead, use methods directly on the `java.xml.xquery.XQSequence` instance to access the current item (see the interface `javax.xml.xquery.XQItemAccessor` in [Oracle Database XML Java API Reference](../jaxml/index.md)).

The code shown in this section invokes a query using XQJ in a way that does not prevent streaming evaluation.

Example 15-17 displays the contents of `books2.xq`.

Example 15-18 sets up the query to enable streaming evaluation. The example writes this output to file `results.xml`: `<title>A Game of Thrones</title>`.

The binding mode is set to the value `BINDING_MODE_DEFERRED` to avoid materializing `books.xml` when it is bound to the prepared expression. Likewise, the result is written to an output stream, and it is not materialized.

To simplify the example, the input file `books.xml` is small. Even if this file contained millions of books, evaluating the query would require only a small maximum heap size because only one book element is held in memory at one time. In contrast with the query `books.xq`, shown in Example 15-3, the query `books2.xq` does not require you to define an entity resolver. Both examples (`books.xq` and `books2.xq`) are streamable.

Example 15-17 books2.xq

    declare variable $doc external;

    for $book in $doc/books/book
    where xs:decimal($book/price) gt 10.00
    return
      $book/title

Example 15-18 Facilitating Streaming Evaluation

    import java.io.FileInputStream;
    import java.io.FileOutputStream;
    import java.io.IOException;

    import javax.xml.namespace.QName;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQConstants;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQDataSource;

    public class Streaming {

        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            XQStaticContext ctx = con.getStaticContext();
            ctx.setBindingMode(XQConstants.BINDING_MODE_DEFERRED);
            con.setStaticContext(ctx);

            FileInputStream input = new FileInputStream("books.xml");
            FileInputStream query = new FileInputStream("books2.xq");
            FileOutputStream output = new FileOutputStream("result.xml");

            XQPreparedExpression expr = con.prepareExpression(query);
            query.close();
            expr.bindDocument(new QName("doc"), input, null, null);

            XQSequence result = expr.executeQuery();

            // Writes "<title>A Game of Thrones</title>" to file results.xml
            result.writeSequence(output, null);

            result.close();
            input.close();
            output.close();
            expr.close();
            con.close();
        }
    }

#### 15.4.2 External Storage

Depending on the query, the processor might have to store part of the input XML in main memory during query evaluation.

For example, this scenario can occur in cases such as these:

- A sequence is sorted.

- The value bound to a variable is used multiple times.

- A path expression uses a reverse-axis step.

To reduce memory usage in such cases, you can configure the XQuery processor to use external storage for materializing XML, rather than main memory. To enable the use of external storage, set the data source property `OXQConstants.USE_EXTERNAL_STORAGE` to `true`, and set an `oracle.xml.scalable.PageManager` instance on the dynamic context.

**Note:**

Using external storage can significantly reduce the amount of main memory that is consumed during query processing. However, it can also reduce performance.

Example 15-19 shows how to enable the XQuery processor to use disk-based storage rather than main memory when XML is materialized. The example writes this output to file `results.xml`: `<title>A Game of Thrones</title>`.

Example 15-19 Configuring the XQuery Processor to Use External Storage

    import java.io.File;
    import java.io.FileInputStream;
    import java.io.FileOutputStream;
    import java.io.IOException;

    import javax.xml.namespace.QName;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQConstants;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQSequence;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.scalable.FilePageManager;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQPreparedExpression;
    import oracle.xml.xquery.OXQView;

    public class ExternalStorage {

        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            ds.setProperty(OXQDataSource.USE_EXTERNAL_STORAGE, "true");

            XQConnection con = ds.getConnection();
            XQStaticContext ctx = con.getStaticContext();
            ctx.setBindingMode(XQConstants.BINDING_MODE_DEFERRED);
            con.setStaticContext(ctx);

            FileInputStream input = new FileInputStream("books.xml");
            FileInputStream query = new FileInputStream("books2.xq");
            FileOutputStream output = new FileOutputStream("results.xml");

            XQPreparedExpression expr = con.prepareExpression(query);
            query.close();
            expr.bindDocument(new QName("doc"), input, null, null);

            // Set a page manager that will be used by the XQuery processor if XML needs to be materialized
            OXQPreparedExpression oexpr = OXQView.getPreparedExpression(expr);
            File temporaryFile = File.createTempFile("books", ".pagefile");
            temporaryFile.deleteOnExit();
            oexpr.setPageManager(new FilePageManager(temporaryFile.getAbsolutePath()));

            XQSequence result = expr.executeQuery();

            // Writes to file results.xml: "<title>A Game of Thrones</title>"
            result.writeSequence(output, null);

            result.close();
            input.close();
            output.close();
            expr.close();
            con.close();
        }
    }

#### 15.4.3 Thread Safety for XQJ

The Oracle implementation of XQJ is not thread-safe. For example, an instance of `javax.xml.xquery.XQSequence` must be accessed by only one thread. However, a restricted form of thread safety is supported for managing instances of `javax.xml.xquery.XQConnection`.

- An instance of `XQConnection` serves as a factory for creating instances of `XQExpression`, `XQPreparedExpression`, `XQItem`, `XQSequence`, `XQItemType`, and `XQSequenceType`. One thread can manage the creation of these objects for use by other threads. For example, `XQPreparedExpression` instances created in one thread by the same connection can be used in other threads. Each `XQPreparedExpression` instance, however, must be executed by only one thread. Any user-defined implementations of `oracle.xml.xquery.OXQEntityResolver` that are specified must be thread-safe when expressions from the same connection are evaluated concurrently.

- Method `XQConnection.close()` closes all `XQExpression` and `XQPreparedExpression` instances that were obtained from the connection. Closing those instances closes all `XQResultSequence` and `XQResultItem` instances obtained from the expressions. Method `XQConnection.close()` can be called while expressions obtained from the connection are being processed in other threads. In that case, all registered resources held by the expressions (such as `java.io.InputStream` and `java.io.Reader`) are closed. This contract assumes that all registered resources support a thread-safe close method. For example, many JDK implementations of `java.io.Closeable` satisfy this requirement. But, many implementations of `javax.xml.stream.XMLStreamReader` do not provide a thread-safe close method. Implementations without this support can give unpredictable results if they are closed while a second thread is still reading (see interface `oracle.xml.xquery.OXQCloseable` in [Oracle Database XML Java API Reference](../jaxml/index.md)).

  **See Also:**

  [Oracle Database XML Java API Reference](../jaxml/index.md), method `oracle.xml.xquery.OXQConnection.copyExpression(XQPreparedExpression)`

### 15.5 Performing Updates

XDK extends XQJ with the ability to execute updating queries. XML documents can be read as an instance of `javax.xml.xquery.XQItem`, and then modified using XQuery Update Facility extensions.

This feature is disabled by default. You can enable it by setting the update mode on the dynamic context to `oracle.xml.xquery.OXQConstants.UPDATE_MODE_ENABLED`.

Documents to be updated must be bound in deferred mode (see method `javax.xml.xquery.XQStaticContext.setBindingMode(int)` in [Oracle Database XML Java API Reference](../jaxml/index.md)). If the binding mode is not set to deferred, the input bindings are copied before query execution. Thus, only the copy is updated.

The example in this section shows how you can modify an XML document using the XQuery Update Facility.

Example 15-20 displays the contents of `configuration.xml`.

Example 15-21 displays the contents of `update.xq`.

Example 15-22 displays the contents of `configuration.xml` after an update.

Example 15-23 shows how execute the query `update.xq`.

In the example, these actions occur:

1.  The XML file `configuration.xml` is read as an instance of `javax.xml.xquery.XQItem`.

2.  The item is bound to the prepared expression for the query `update.xq`.

3.  The query `update.xq` is executed.

4.  The modified document is written to the file `configuration.xml`.

**See Also:**

- [XQuery Update Facility 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xquery_update10)

- [Oracle Database XML Java API Reference](../jaxml/index.md), interface `oracle.xml.xquery.OXQDynamicContext`

Example 15-20 configuration.xml

    <configuration>
      <property>
        <name>hostname</name>
        <value>example.com</value>
      </property>
      <property>
        <name>timeout</name>
        <value>1000</value>
      </property>
    </configuration>

Example 15-21 update.xq

    declare variable $doc external;

    let $timeout := $doc/configuration/property[name eq "timeout"]
    return
      replace value of node $timeout/value
      with 2 * xs:integer($timeout/value)

Example 15-22 Updated File configuration.xml

    <configuration>
      <property>
        <name>hostname</name>
        <value>example.com</value>
      </property>
      <property>
        <name>timeout</name>
        <value>2000</value>
      </property>
    </configuration>

Example 15-23 Executing the Updating Query update.xq

    import java.io.FileInputStream;
    import java.io.IOException;
    import java.io.FileOutputStream;

    import javax.xml.namespace.QName;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQConstants;
    import javax.xml.xquery.XQException;
    import javax.xml.xquery.XQItem;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.xquery.XQStaticContext;

    import oracle.xml.xquery.OXQConstants;
    import oracle.xml.xquery.OXQDataSource;
    import oracle.xml.xquery.OXQView;

    public class UpdateDocument {
        public static void main(String[] args) throws XQException, IOException {
            OXQDataSource ds = new OXQDataSource();
            XQConnection con = ds.getConnection();

            XQStaticContext ctx = con.getStaticContext();
            // Set the binding mode to deferred so the document
            // item is not copied when it is bound.
            ctx.setBindingMode(XQConstants.BINDING_MODE_DEFERRED);
            con.setStaticContext(ctx);

            FileInputStream input = new FileInputStream("configuration.xml");
            XQItem doc = con.createItemFromDocument(input, null, null);
            input.close();

            System.out.println("Before update: \n" + doc.getItemAsString(null));

            FileInputStream query = new FileInputStream("update.xq");
            XQPreparedExpression expr = con.prepareExpression(query);
            query.close();
            expr.bindItem(new QName("doc"), doc);
            // Enable updates (disabled by default)
            OXQView.getDynamicContext(expr).setUpdateMode(OXQConstants.UPDATE_MODE_ENABLED);
            expr.executeQuery();

            System.out.println("After update: \n" + doc.getItemAsString(null));

            // Write the modified document back to the file
            FileOutputStream out = new FileOutputStream("configuration.xml");
            doc.writeItem(out, null);

            expr.close();
            con.close();
        }
    }

### 15.6 Oracle XQuery Functions and Operators

Oracle supports the standard XQuery functions and operators, as well as some Oracle-specific functions.

Oracle-specific XQuery functions use namespace `http://xmlns.oracle.com/xdk/xquery/function`. Namespace prefix `ora-fn` is predeclared, and the module is automatically imported.

**Related Topics**

- Standards and Specifications for the XQuery Processor for Java

#### 15.6.1 Oracle XQuery Functions for Duration, Date, and Time

You can manipulate durations, dates, and times in XQuery using Oracle XQuery functions.

The Oracle XQuery functions are in namespace `http://xmlns.oracle.com/xdk/xquery/function`. Namespace prefix`ora-fn` is predeclared, and the module is automatically imported.

##### 15.6.1.1 ora-fn:date-from-string-with-format

This Oracle XQuery function returns a new date value from a string according to a given pattern.

##### Signature

    ora-fn:date-from-string-with-format($format as xs:string?,
                                        $dateString as xs:string?,
                                        $locale as xs:string*)
                                       as xs:date?

    ora-fn:date-from-string-with-format($format as xs:string?,
                                        $dateString as xs:string?)
                                       as xs:date?

##### Parameters

`$format`: The pattern; see Format Argument

`$dateString`: An input string that represents a date

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Example

This example returns the specified date in the current time zone:

    ora-fn:date-from-string-with-format("yyyy-MM-dd G", "2013-06-22 AD")

##### 15.6.1.2 ora-fn:date-to-string-with-format

This Oracle XQuery function returns a date string with a given pattern.

##### Signature

    ora-fn:date-to-string-with-format($format as xs:string?,
                                      $date as xs:date?,
                                      *$locale as xs:string?)
                                     as xs:string?

    ora-fn:date-to-string-with-format($format as xs:string?,
                                      $date as xs:date?)
                                     as xs:string?

##### Parameters

`$format`: The pattern; see Format Argument

`$date`: The date

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Example

This example returns the string `2013-07-15`:

    ora-fn:date-to-string-with-format("yyyy-mm-dd", xs:date("2013-07-15"))

##### 15.6.1.3 ora-fn:dateTime-from-string-with-format

This Oracle XQuery function returns a new date-time value from an input string, according to a given pattern.

##### Signature

    ora-fn:dateTime-from-string-with-format($format as xs:string?,
                                            $dateTimeString as xs:string?,
                                            $locale as xs:string?)
                                           as xs:dateTime?

    ora-fn:dateTime-from-string-with-format($format as xs:string?,
                                            $dateTimeString as xs:string?)
                                           as xs:dateTime?

##### Parameters

`$format`: The pattern; see Format Argument

`$dateTimeString`: The date and time

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Examples

This example returns the specified date and 11:04:00AM in the current time zone:

    ora-fn:dateTime-from-string-with-format("yyyy-MM-dd 'at' hh:mm",
                                            "2013-06-22 at 11:04")

The next example returns the specified date and 12:00:00AM in the current time zone:

    ora-fn:dateTime-from-string-with-format("yyyy-MM-dd G",
                                            "2013-06-22 AD")

##### 15.6.1.4 ora-fn:dateTime-to-string-with-format

This Oracle XQuery function returns a date and time string with a given pattern.

##### Signature

    ora-fn:dateTime-to-string-with-format($format as xs:string?,
                                          $dateTime as xs:dateTime?,
                                          $locale as xs:string?)
                                         as xs:string?

    ora-fn:dateTime-to-string-with-format($format as xs:string?,
                                          $dateTime as xs:dateTime?)
                                         as xs:string?

##### Parameters

`$format`: The pattern; see Format Argument

`$dateTime`: The date and time

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Examples

This example returns the string `07 JAN 2013 10:09 PM AD`:

    ora-fn:dateTime-to-string-with-format("dd MMM yyyy hh:mm a G",
                                          xs:dateTime("2013-01-07T22:09:44"))

The next example returns the string "01-07-2013":

    ora-fn:dateTime-to-string-with-format("MM-dd-yyyy",
                                          xs:dateTime("2013-01-07T22:09:44"))

##### 15.6.1.5 ora-fn:time-from-string-with-format

This Oracle XQuery function returns a new time value from an input string, according to a given pattern.

##### Signature

    ora-fn:time-from-string-with-format($format as xs:string?,
                                        $timeString as xs:string?,
                                        $locale as xs:string?)
                                       as xs:time?

    ora-fn:time-from-string-with-format($format as xs:string?,
                                        $timeString as xs:string?)
                                       as xs:time?

##### Parameters

`$format`: The pattern; see Format Argument

`$timeString`: The time

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Example

This example returns 9:45:22 PM in the current time zone:

    ora-fn:time-from-string-with-format("HH.mm.ss", "21.45.22")

The next example returns 8:07:22 PM in the current time zone:

    fn-bea:time-from-string-with-format("hh:mm:ss a", "8:07:22 PM")

##### 15.6.1.6 ora-fn:time-to-string-with-format

This Oracle XQuery function returns a time string with a given pattern.

##### Signature

    ora-fn:time-to-string-with-format($format as xs:string?,
                                      $time as xs:time?,
                                      $locale as xs:string?)
                                     as xs:string?

    ora-fn:time-to-string-with-format($format as xs:string?, $time as xs:time?) as xs:string?

##### Parameters

`$format`: The pattern; see Format Argument

`$time`: The time

`$locale`: A one- to three-field value that represents the locale; see Locale Argument

##### Examples

This example returns the string "10:09 PM":

    ora-fn:time-to-string-with-format("hh:mm a", xs:time("22:09:44"))

The next example returns the string "22:09 PM":

    ora-fn:time-to-string-with-format("HH:mm a", xs:time("22:09:44"))

##### 15.6.1.7 Format Argument

The `$format` argument identifies the various fields that compose a date or time value.

##### 15.6.1.8 Locale Argument

The `$locale` represents a specific geographic, political, or cultural region.

It is defined by up to three fields:

1.  Language code: The ISO 639 alpha-2 or alpha-3 language code, or the registered language subtags of up to eight letters. For example, `en` for English and `ja` for Japanese.

2.  Country code: The ISO 3166 alpha-2 country code or the UN M.49 numeric-3 area code. For example, `US` for the United States and `029` for the Caribbean.

3.  Variant: Indicates a variation of the locale, such as a particular dialect. Order multiple values in order of importance and separate them with an underscore (\_). These values are case sensitive.

**See Also:**

- [Class Locale](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=javase7_util_locale) in Java Standard Edition 7 Reference

#### 15.6.2 Oracle XQuery Functions for Strings

You can manipulate strings in XQuery using Oracle XQuery functions.

The Oracle XQuery functions are in namespace `http://xmlns.oracle.com/xdk/xquery/function`. Namespace prefix`ora-fn` is predeclared, and the module is automatically imported.

##### 15.6.2.1 ora-fn:pad-left

Adds padding characters to the left of a string to create a fixed-length string. If the input string exceeds the specified size, then it is truncated to return a substring of the specified length. The default padding character is a space (ASCII 32).

##### Signature

    ora-fn:pad-left($str as xs:string?,
                    $size as xs:integer?,
                    $pad as xs:string?)
                   as xs:string?

    ora-fn:pad-left($str as xs:string?,
                    $size as xs:integer?)
                   as xs:string?

##### Parameters

`$str`: The input string

`$size`: The desired fixed length, which is obtained by adding padding characters to `$str`

`$pad`: The padding character

If either argument is an empty sequence, then the function returns an empty sequence.

##### Examples

This example prefixes `"01`" to the input string up to the maximum of six characters. The returned string is "`010abc`". The function returns one complete and one partial pad character.

    ora-fn:pad-left("abc", 6, "01")

The example returns only "`ab`" because the input string exceeds the specified fixed length:

    ora-fn:pad-left("abcd", 2, "01")

This example prefixes spaces to the string up to the specified maximum of six characters. The returned string has a prefix of two spaces: "` abcd`":

    ora-fn:pad-left("abcd", 6)

The next example returns only "`ab`" because the input string exceeds the specified fixed length:

    ora-fn:pad-left("abcd", 2)

##### 15.6.2.2 ora-fn:pad-right

Adds padding characters to the right of a string to create a fixed-length string. If the input string exceeds the specified size, then it is truncated to return a substring of the specified length. The default padding character is a space (ASCII 32).

##### Signature

    ora-fn:pad-right($str as xs:string?,
                     $size as xs:integer?,
                     $pad as xs:string?)
                    as xs:string?

    ora-fn:pad-right($str as xs:string?,
                     $size as xs:integer?)
                    as xs:string?

##### Parameters

`$str`: The input string

`$size`: The desired fixed length, which is obtained by adding padding characters to `$str`

`$pad`: The padding character

If either argument is an empty sequence, then the function returns an empty sequence.

##### Examples

This example appends "`01`" to the input string up to the maximum of six characters. The returned string is "`abc010`". The function returns one complete and one partial pad character.

    ora-fn:pad-right("abc", 6, "01")

This example returns only "`ab`" because the input string exceeds the specified fixed length:

    ora-fn:pad-right("abcd", 2, "01")

This example appends spaces to the string up to the specified maximum of six characters. The returned string has a suffix of two spaces: "`abcd `":

    ora-fn:pad-right("abcd", 6)

The next example returns only "`ab`" because the input string exceeds the specified fixed length:

    ora-fn:pad-right("abcd", 2)

##### 15.6.2.3 ora-fn:trim

Removes any leading or trailing white space from a string.

##### Signature

    ora-fn:trim($input as xs:string?) as xs:string?

##### Parameters

`$input`: The string to trim. If `$input` is an empty sequence, then the function returns an empty sequence. Other data types trigger an error.

##### Example

This example returns the string "`abc`":

    ora-fn:trim("  abc  ")

##### 15.6.2.4 ora-fn:trim-left

Removes any leading white space.

##### Signature

    ora-fn:trim-left($input as xs:string?) as xs:string?

##### Parameters

`$input`: The string to trim. If `$input` is an empty sequence, then the function returns an empty sequence. Other data types trigger an error.

##### Example

This example removes the leading spaces and returns the string "`abc    `":

    ora-fn:trim-left("    abc    ")

##### 15.6.2.5 ora-fn:trim-right

Removes any trailing white space.

##### Signature

    ora-fn:trim-right($input as xs:string?) as xs:string?

##### Parameters

`$input`: The string to trim. If `$input` is an empty sequence, then the function returns an empty sequence. Other data types trigger an error.

##### Example

This example removes the trailing spaces and returns the string "`    abc`":

    ora-fn:trim-left("    abc    ")

### 15.7 Standards and Specifications for the XQuery Processor for Java

The standards and specifications to which the XDK XQuery processor for Java conforms are listed.

- [XQuery 3.0: An XML Query Language](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquery_30)

  **Note:**

  All XQuery 1.0 level features are supported. XQuery 3.0 level features are supported except for the following: FLWOR window clause, FLWOR count clause, namespace constructors, decimal format declarations, `fn:format-number`, `fn:format-integer`, `fn:format-date`, `fn:format-time`, `fn:path`, and higher order XQuery functions.

- [XQuery Update Facility 1.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_tr_xquery_update10)

- [XQueryX 3.0](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xqueryx_30), the XML syntax for XQuery 3.0

- [JSR-000225 XQuery API for Java](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=jcp_org_jsr225)

**Note:**

The XDK XQuery processor for Java is not interoperable with other XQJ implementations, including the Oracle XQJ implementation for Oracle XML DB. (See JSR-225: XQuery API for Java for the meaning of interoperable.)

#### 15.7.1 Optional XQuery Features

The XQuery specification defines certain features as optional. Links are provided to the standards that specify those that are supported by XDK.

These are the optional features supported by XDK:

- [Schema Import](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xqueryschemaimport)

- [Validate Expressions](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xqueryschemavalid)

- [Static Typing](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquerystatictyping)

- [Static Typing for Update](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquerystaticupdate)

- [Modules](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquery_modules)

- [Serialization](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_xquery_serial8n)

#### 15.7.2 Implementation-Defined Items

The XQJ and XQuery specifications leave the definition of certain aspects up to the implementation. The implementation-defined items for XDK are described briefly.

Table 15-2 summarizes the XQJ implementation-defined items.

Table 15-2 XQJ Implementation-Defined Items

| Description                                                                                                          | Behavior                                                                                                             |
|:---------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| Class name of `XQDataSource` implementation                                                                          | `oracle.xml.xquery.OXQDataSource`.                                                                                   |
| Properties defined on `OXQDataSource`                                                                                | None. The username and password are silently ignored.                                                                |
| JDBC connection support                                                                                              | JDBC connections are not supported.                                                                                  |
| Commands                                                                                                             | Not supported.                                                                                                       |
| Cancelling of query execution with method `XQPreparedExpression.cancel()`                                            | Yes.                                                                                                                 |
| Serialization                                                                                                        | Yes.                                                                                                                 |
| Additional StAX or SAX events                                                                                        | None.                                                                                                                |
| User-defined schema types                                                                                            | Yes.                                                                                                                 |
| Node identity, document order, and full-node context preservation when a node is bound to an external variable       | Not preserved.                                                                                                       |
| Login timeout                                                                                                        | Not supported.                                                                                                       |
| Transactions                                                                                                         | Not supported. An exception is thrown if a transaction method is called.                                             |
| `XQItemAccessor.getNodeUri()` method behavior if the input node is not a document node                               | Exception.                                                                                                           |
| `XQItemType.getTypeName()` method for anonymous types                                                                | A unique name.                                                                                                       |
| `XQItemType.getSchemaURI()` method                                                                                   | The schema URI is returned when a type is created from XQJ. No otherwise.                                            |
| `XQDataFactory.createItemFromDocument()` and `bindDocument()` methods if the input is not a well-formed XML document | Exception.                                                                                                           |
| Additional error codes returned by class `XQQueryException`                                                          | The qualified names of Oracle-specific error codes are in the namespace `http://xmlns.oracle.com/xdk/xquery/errors`. |
| `ConnectionPoolXQDataSource`, `PooledXQConnection`, `XQConnectionEvent`, `XQConnectionEventListener` interfaces      | No.                                                                                                                  |
| `XQDataSource.getConnection(java.sql.Connection)`                                                                    | JDBC connections are not supported. An exception is thrown if this method is called.                                 |
| `XQDataSource.getConnection(java.lang.String, java.lang.String)`                                                     | Same as `getConnection()`. Parameters are ignored.                                                                   |

**Note:**

XDK support for the features in Table 15-2 differs from the Oracle XML DB support for them.

Table 15-3 summarizes the XQuery implementation-defined items.

Table 15-3 XQuery Implementation-Defined Items

| Item                                                                                                                                                                                                    | Behavior                                                                                                                                                                                                                                                                                                                                                                 |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The version of Unicode that is used to construct expressions                                                                                                                                            | Depends on the version of Java used. Different Java versions support different versions of Unicode.                                                                                                                                                                                                                                                                      |
| The statically-known collations                                                                                                                                                                         | Unicode codepoint collation and collations derived from classes `java.text.Collator` or `oracle.i18n.text.OraCollator`.                                                                                                                                                                                                                                                  |
| The implicit time zone.                                                                                                                                                                                 | Uses the default time zone, as determined by method `java.util.Calendar.getInstance()`.                                                                                                                                                                                                                                                                                  |
| The circumstances in which warnings are raised, and the ways in which warnings are handled                                                                                                              | None.                                                                                                                                                                                                                                                                                                                                                                    |
| The method by which errors are reported to the external processing environment                                                                                                                          | Exception `javax.xml.xquery.XQException`.                                                                                                                                                                                                                                                                                                                                |
| Whether the implementation is based on the rules of XML 1.0 and XML Names, or the rules of XML 1.1 and XML Names 1.1                                                                                    | 1.0.                                                                                                                                                                                                                                                                                                                                                                     |
| Any components of the static context or dynamic context that are overwritten or augmented by the implementation                                                                                         | See Table 15-5.                                                                                                                                                                                                                                                                                                                                                          |
| Which of the optional axes are supported by the implementation, if the Full-Axis Feature is not supported                                                                                               | Full support.                                                                                                                                                                                                                                                                                                                                                            |
| The default handling of empty sequences returned by an ordering key (sortspec) in an order by clause (empty least or empty greatest)                                                                    | `least`.                                                                                                                                                                                                                                                                                                                                                                 |
| The names and semantics of any extension expressions (pragmas) recognized by the implementation                                                                                                         | None.                                                                                                                                                                                                                                                                                                                                                                    |
| The names and semantics of any option declarations recognized by the implementation                                                                                                                     | None.                                                                                                                                                                                                                                                                                                                                                                    |
| Protocols (if any) by which parameters can be passed to an external function, and the result of the function can be returned to the invoking query                                                      | Defined by XQJ.                                                                                                                                                                                                                                                                                                                                                          |
| The process by which the specific modules to be imported by a module import are identified, if the Module feature is supported (includes processing of location hints, if any)                          | Entity resolvers. See XQJ Entity Resolution.                                                                                                                                                                                                                                                                                                                             |
| Any static typing extensions supported by the implementation, if the Static Typing feature is supported                                                                                                 | Strict mode (based on subtype) and optimistic mode (based on type intersection). Optimistic mode is the default.                                                                                                                                                                                                                                                         |
| The means by which serialization is invoked, if the Serialization feature is supported                                                                                                                  | Defined by XQJ.                                                                                                                                                                                                                                                                                                                                                          |
| The default values for the `byte-order-mark`, `encoding`, `media-type`, `normalization-form`, `omit-xml-declaration`, `standalone`, and `version` parameters, if the Serialization feature is supported | See the interface `oracle.xml.xquery.OXQSerializationParameters` in [Oracle Database XML Java API Reference](../jaxml/index.md).                                                                                                                                                                                                                                         |
| Limits on ranges of values for various data types.                                                                                                                                                      | Decimal and integer values have arbitrary precision.                                                                                                                                                                                                                                                                                                                     |
| The signatures of functions provided by the implementation or via an implementation-defined API (see the XQuery standard, section 2.1.1, Static Context).                                               | See Oracle XQuery Functions and Operators.                                                                                                                                                                                                                                                                                                                               |
| Any environment variables provided by the implementation.                                                                                                                                               | Entity resolvers. See XQJ Entity Resolution.                                                                                                                                                                                                                                                                                                                             |
| Any rules used for static typing (see the XQuery standard, section 2.2.3.1, Static Analysis Phase).                                                                                                     | Defaults to optimistic, pessimistic configurable.                                                                                                                                                                                                                                                                                                                        |
| Any serialization parameters provided by the implementation (see the XQuery standard, section 2.2.4 Serialization).                                                                                     | See `OXQSerializationParameters`. See [Oracle Database XML Java API Reference](../jaxml/index.md).                                                                                                                                                                                                                                                                       |
| The means by which the location hint for a serialization parameter document identifies the corresponding XDM instance (see the XQuery standard, section 2.2.4, Serialization).                          | Entity resolvers, `OXQEntityKind.DOCUMENT`. See XQJ Entity Resolution.                                                                                                                                                                                                                                                                                                   |
| What error, if any, is returned if an external function's implementation does not return the declared result type (see the XQuery standard, section 2.2.5, Consistency Constraints).                    |  `XPTY0004`.                                                                                                                                                                                                                                                                                                                                                             |
| Any annotations defined by the implementation, and their associated behavior (see the XQuery standard, section 4.15, Annotations).                                                                      | You can use `%ora-fn:context-item` to allow the context item of a function caller to be implicitly passed as the first argument to the function.<br>For example, this query evaluates to `e`, `f`, `g`:<br>` declare %ora-fn:context-item`<br>` function local:foo($arg as node()) {`<br>`     node-name($arg)`<br>`  };`<br>`(<e/>, <f/>)/local:foo(), local:foo(<g/>)` |
| Any function assertions defined by the implementation.                                                                                                                                                  | None.                                                                                                                                                                                                                                                                                                                                                                    |
| The effect of function assertions understood by the implementation on section 2.5.6.3. The judgment subtype-assertions (AnnotationsA, AnnotationsB) .                                                   | Not applicable.                                                                                                                                                                                                                                                                                                                                                          |
| Any implementation-defined variables defined by the implementation. (see the XQuery standard, section 3.1.2, Variable References).                                                                      | None.                                                                                                                                                                                                                                                                                                                                                                    |
| The ordering associated with `fn:unordered` in the implementation (see the XQuery standard, section 3.11, Ordered and Unordered Expressions).                                                           | It does not change the order of the input sequence.                                                                                                                                                                                                                                                                                                                      |
| Any additional information provided for `try`/`catch` by variable `err:additional` (see the XQuery standard, section 3.15, Try/Catch Expressions).                                                      | None.                                                                                                                                                                                                                                                                                                                                                                    |
| The default boundary-space policy (see the XQuery standard, section 4.3, Boundary-space Declaration).                                                                                                   | `strip`.                                                                                                                                                                                                                                                                                                                                                                 |
| The default collation (see the XQuery standard, section 4.4, Default Collation Declaration).                                                                                                            | Unicode.                                                                                                                                                                                                                                                                                                                                                                 |
| The default base URI (see the XQuery standard, section 4.5, Base URI Declaration).                                                                                                                      | None.                                                                                                                                                                                                                                                                                                                                                                    |

Table 15-4 summarizes the XQuery Update Facility implementation-defined items.

Table 15-4 XQuery Update Facility Implementation-Defined Items

| Item                                                                                                                                      | Behavior                                                                                                                                                                                                                                               |
|:------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The revalidation modes that are supported by this implementation.                                                                         | `skip`.                                                                                                                                                                                                                                                |
| The default revalidation mode for this implementation.                                                                                    | `skip`.                                                                                                                                                                                                                                                |
| The mechanism (if any) by which an external function can return an XDM instance, or a pending update list, or both to the invoking query. | Returning a pending update list from an external function is not supported.                                                                                                                                                                            |
| The semantics of `fn:put()`, including the kinds of nodes accepted as operands by this function.                                          | Any node type is accepted. Storage of the node is determined by the entity resolver. See class `oracle.xml.xquery.OXQEntity` in [Oracle Database XML Java API Reference](../jaxml/index.md), specifically the documentation for entity kind `UPD_PUT`. |

Table 15-5 summarizes the default initial values for the static context.

Table 15-5 Default Initial Values for the Static Context

| Context Component                        | Default Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Statically known namespaces              | `err`=`http://w3.org/2005/xqt-errors`<br>`fn`=`http://www.w3.org/2005/xpath-functions`<br>`local`=`http://www.w3.org/2005/xquery-local-functions`<br>`math`=`http://www.w3.org/2005/xpath-functions/math`<br>`ora-ext`=`http://xmlns.oracle.com/xdk/xquery/extension`<br>`ora-java`=`http://xmlns.oracle.com/xdk/xquery/java`<br>`ora-xml`=`http://xmlns.oracle.com/xdk/xquery/xml`<br>`ora-fn`=`http://xmlns.oracle.com/xdk/xquery/function`<br>`output`=`http://www.w3.org/2010/xslt-xquery-serialization`<br>`xml`=`http://www.w3.org/XML/1998/namespace`<br>`xs`=`http://www.w3.org/2001/XMLSchema`<br>`xsi`=`http://www.w3.org/2001/XMLSchema-instance`<br>Prefixes that begin with `ora-` are reserved for use by Oracle. Additional prefixes that begin with `ora-` may be added to the default statically known namespaces in a future release. |
| Default element/type namespace           | No namespace.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Default function namespace               | `fn`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| In-scope schema types                    | Built-in types in `xs`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| In-scope element declarations            | None.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| In-scope attribute declarations          | None.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| In-scope variables                       | None.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Context item static type                 | `item()`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Function signatures                      | Functions in namespace `fn`, and constructors for built-in atomic types.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Statically known collations              | Unicode codepoint collation and collations derived from class `java.text.Collator` or `oracle.i18n.text.OraCollator`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Default collation                        | Unicode codepoint collation:<br>`http://www.w3.org/2005/xpath-functions/collation/codepoint`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Construction mode                        | `preserve`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Ordering mode                            | `ordered`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Default order for empty sequences        | `least`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Boundary-space policy                    | `strip`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Copy-namespaces mode                     | `preserve`, `no-inherit`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Base URI                                 | As defined in the standard.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Statically known documents               | None.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Statically known collections             | None.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Statically known default collection type | `node()*`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Serialization parameters                 | Same as the defaults for `OXQSerializationParameters`. See [Oracle Database XML Java API Reference](../jaxml/index.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
