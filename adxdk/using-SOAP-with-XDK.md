An explanation is given of how to use Simple Object Access Protocol (SOAP) with the Oracle XML Developer's Kit (XDK) for C.

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/native-XML-DB-web-services.md)

### 9.1 Introduction to SOAP for C

SOAP is an Extensible Markup Language (XML) protocol for exchanging structured and typed information between peers using HTTP and HTTPS in a distributed environment. Only HTTP 1.0 is supported in XDK for Oracle Database 10g Release 2.

SOAP has three parts:

- The SOAP envelope which defines how to present what is in the message, who must process the message, and whether that processing is optional or mandatory.

- A set of serialization and deserialization rules for converting application data types to and from XML.

- A SOAP remote procedure call (RPC) that defines calls and responses.

  **Note:**

  RPC and serialization/deserialization are not supported in this release.

SOAP is operating system and language-independent because it is XML-based. This chapter presents the C implementation of the functions that read and write the SOAP message.

SOAP Version 1.2 is the definition of an XML-based message which is specified as an XML Infoset (an abstract data set, it could be XML 1.0) that gives a description of the message contents. Version 1.1 is also supported.

#### 9.1.1 SOAP Messaging Overview

SOAP is a lightweight protocol for sending and receiving requests and responses across the Internet. Because it is based on XML and transport protocols such as HTTP, it is not blocked by most firewalls. SOAP is independent of operating system, implementation language, and object model.

The power of SOAP is its ability to act as the glue between heterogeneous software components. For example, Visual Basic clients can invoke Common Object Request Broker Architecture (CORBA) services running on UNIX computers; Macintosh clients can invoke Perl objects running on Linux.

SOAP messages have these parts:

- An **envelope** that contains the message, defines how to process the message and who processes it, and whether processing is optional or mandatory. The `Envelope` element is required.

- A set of **encoding rules** that describe the data types for the application. These rules define a serialization mechanism that converts the application data types to and from XML.

- A **remote procedure call (RPC)** request and response convention. This required element is called a body element. The `Body` element contains a first subelement whose name is the name of a method. This method request element contains elements for each input and output parameter. The element names are the parameter names. RPC is not currently supported in this release.

SOAP is independent of any transport protocol. Nevertheless, SOAP used over HTTP for remote service invocation has emerged as a standard for delivering programmatic content over the Internet.

Besides being independent of transfer protocol, SOAP is also independent of operating system. In other words, SOAP enables programs to communicate even when they are written in different languages and run on different operating systems.

##### 9.1.1.1 SOAP Message Format

Types of SOAP messages are described.

- Requests for a service, including input parameters

- Responses from the requested service, including return value and output parameters

- Optional fault elements containing error codes and information

In a SOAP message, the **payload** contains the XML-encoded data. The payload contains no processing information. In contrast, the message header may contain processing information.

###### 9.1.1.1.1 SOAP Requests

SOAP requests are described.

In SOAP requests, the XML payload contains several elements that include:

- Root element

- Method element

- Header elements (optional)

Example 9-1 shows the format of a sample SOAP message request. A `GetLastTradePrice` SOAP request is sent to a `StockQuote` service. The request accepts a string parameter representing the company stock symbol and returns a float representing the stock price in the SOAP response.

Example 9-1 SOAP Request Message

    POST /StockQuote HTTP/1.0
    Host: www.stockquoteserver.com
    Content-Type: application/soap+xml; charset="utf-8"
    Content-Length: nnnn
    SOAPAction: "Some-URI"

    <SOAP-ENV:Envelope  xmlns:SOAP-ENV="http://www.w3.org/2003/05/soap-envelope"
                SOAP-ENV:encodingStyle="http://www.w3.org/2003/05/soap-encoding/">
      <SOAP-ENV:Body>
        <m:GetLastTradePrice xmlns:m="Some-URI">
          <symbol>ORCL</symbol>
        <m:GetLastTradePrice>
      </SOAP-ENV:Body>
    </SOAP-ENV:Envelope>

In Example 9-1, the XML document is the SOAP message. The `<SOAP-ENV:Envelope>` element is the top-level element of the XML document. The payload is represented by the method element `<m:GetLastTradePrice>`. XML namespaces distinguish SOAP identifiers from application-specific identifiers.

The first line of the header specifies that the request uses HTTP as the transport protocol:

    POST /StockQuote HTTP/1.1

Because SOAP is independent of transport protocol, the rules governing XML payload format are independent of the use of HTTP for transport of the payload. This HTTP request points to the URI `/StockQuote`. Because the SOAP specification is silent on the issue of component activation, the code behind this URI determines how to activate the component and invoke the `GetLastTradePrice` method.

###### 9.1.1.1.2 Example of a SOAP Response

An example of a SOAP response is presented.

Example 9-2 shows the format of the response to the request in Example 9-1. Element `<Price>` contains the stock price for `ORCL` requested by the first message.

The messages shown in Example 9-1 and Example 9-2 show two-way SOAP messaging, that is, a SOAP request that is answered by a SOAP response. A one-way SOAP message does not require a SOAP message in response.

Example 9-2 SOAP Response Message

    HTTP/1.0 200 OK
    Content-Type: application/soap+xml; charset="utf-8"
    Content-Length: nnnn

    <SOAP-ENV:Envelope  xmlns:SOAP-ENV="http://www.w3.org/2003/05/soap-envelope"
     SOAP-ENV:encodingStyle="http://www.w3.org/2003/05/soap-encoding/">
      <SOAP-ENV:Body>
        <m:GetLastTradePriceResponse xmlns:m="Some-URI">
          <Price>13.5</Price>
        </m:GetLastTradePriceResponse>
      </SOAP-ENV:Body>
    </SOAP-ENV:Envelope>

#### 9.1.2 Using SOAP Clients

SOAP clients are user-written applications that generate XML documents. The documents make a request for a SOAP service and handle a SOAP response. The SOAP implementation in XDK handles requests from any client that sends a valid SOAP request.

The SOAP client application programming interface (API) has these features:

- Supports a synchronous invocation model for requests and responses

- Facilitates the writing of client applications to make SOAP requests

- Encapsulates the creation of the SOAP request and the details of sending the request over the underlying transport protocol

- Supports a pluggable transport, allowing the client to easily change the transport (available transports include HTTP and HTTPS, but only HTTP 1.0 is supported in this release)

A SOAP client must perform these steps to make a request and receive a response:

1.  Gather all parameters that are needed to invoke a service.
2.  Create a SOAP service request message, which is an XML message that is built according to the SOAP protocol. It contains all the values of all input parameters encoded in XML. This process is called **serialization**.
3.  Submit the request to a SOAP server using a transport protocol that is supported by the SOAP server.
4.  Receive a SOAP response message.
5.  Determine the success or failure of the request by handling the SOAP Fault element.
6.  Convert the returned parameter from XML to native data type. This process is called **deserialization**.
7.  Use the result as needed.

#### 9.1.3 Using SOAP Servers

The steps performed by a SOAP server when executing a SOAP service request are described.

1.  The SOAP server receives the service request.

2.  The server parses the XML request and then decides whether to execute or reject the message.

3.  If the message is executed, then the server determines whether the requested service exists.

4.  The server converts all input parameters from XML into data types that the service understands.

5.  The server invokes the service.

6.  The server converts the return parameter to XML and generates a SOAP response message.

7.  The server sends the response message back to the caller.

### 9.2 SOAP C Functions

The SOAP C implementation uses the `xml.h` header. A context of type `xmlctx` must be created before a SOAP context can be created.

HTTP aspects of SOAP are hidden from the user. SOAP endpoints are specified as a couple (binding, endpoint) where binding is of type `xmlsoapbind` and the endpoint is a (`void *`) depending on the binding. Currently, only one binding is supported, `XMLSOAP_BIND_HTTP`. For HTTP binding, the endpoint is an (`OraText *`) URL.

The SOAP layer creates and transports SOAP messages between endpoints, and decomposes received SOAP messages.

The C functions are declared in `xmlsoap.h`. Here is the beginning of that header file:

**See Also:**

[Oracle Database XML C API Reference](../caxml/package-SOAP-API.md) for the C SOAP APIs

Example 9-3 SOAP C Functions Defined in xmlsoap.h

       FILE NAME
            xmlsoap.h - XML SOAP APIs

       FILE DESCRIPTION
            XML SOAP Public APIs

       PUBLIC FUNCTIONS
            XmlSoapCreateCtx         - Create and return a SOAP context
            XmlSoapDestroyCtx        - Destroy a SOAP context

            XmlSoapCreateConnection  - Create a SOAP connection object
            XmlSoapDestroyConnection - Destroy a SOAP connection object

            XmlSoapCall              - Send a SOAP message & wait for reply

            XmlSoapCreateMsg         - Create and return an empty SOAP message
            XmlSoapDestroyMsg        - Destroy a SOAP message created
                                          w/XmlSoapCreateMsg

            XmlSoapGetEnvelope       - Return a SOAP message's envelope
            XmlSoapGetHeader         - Return a SOAP message's envelope header
            XmlSoapGetBody           - Return a SOAP message's envelope body

            XmlSoapAddHeaderElement  - Adds an element to a SOAP header
            XmlSoapGetHeaderElement  - Gets an element from a SOAP header

            XmlSoapAddBodyElement    - Adds an element to a SOAP message body
            XmlSoapGetBodyElement    - Gets an element from a SOAP message body

            XmlSoapSetMustUnderstand - Set mustUnderstand attr for SOAP hdr elem
            XmlSoapGetMustUnderstand - Get mustUnderstand attr from SOAP hdr elem

            XmlSoapSetRole           - Set role for SOAP header element
            XmlSoapGetRole           - Get role from SOAP header element

            XmlSoapSetRelay          - Set relay Header element property
            XmlSoapGetRelay          - Get relay Header element property

            XmlSoapSetFault          - Set Fault in SOAP message
            XmlSoapHasFault          - Does SOAP message have a Fault?
            XmlSoapGetFault          - Return Fault code, reason, and details

            XmlSoapAddFaultReason    - Add additional Reason to Fault
            XmlSoapAddFaultSubDetail - Add additional child to Fault Detail
            XmlSoapGetReasonNum      - Get number of Reasons in Fault element
            XmlSoapGetReasonLang     - Get a lang of a reasons with a
                                           particular iindex.

            XmlSoapError             - Get error message(s)

    */

    #ifndef XMLSOAP_ORACLE
    # define XMLSOAP_ORACLE

    # ifndef XML_ORACLE
    #  include <xml.h>
    # endif

    /*---------------------------------------------------------------------------
                    Package SOAP - Simple Object Access Protocol APIs

         W3C: "SOAP is a lightweight protocol for exchange of information
         in a decentralized, distributed environment.  It is an XML based
         protocol that consists of three parts: an envelope that defines a
         framework for describing what is in a message and how to process
         it, a set of encoding rules for expressing instances of
         application-defined datatypes, and a convention for representing
         remote procedure calls and responses."
         Atachments are allowed only in Soap 1.1
         In Soap 1.2 body may not have other elements if Fault is present.

         Structure of a SOAP message:

         [SOAP message (XML document)
            [SOAP envelope
                 [SOAP header?
                     element*
                 ]
                 [SOAP body
                     (element* | Fault)?
                 ]
            ]
         ]
    ---------------------------------------------------------------------------*/
    ...

### 9.3 SOAP Example 1: Sending an XML Document

An XML document is presented that shows a request to a travel company for a reservation on a plane flight from New York to Los Angeles for John Smith. A simple example creates the XML document, sends it, receives and decomposes a reply. There is some minimal error checking.

The `DEBUG` option is shown for correcting anomalies. The program may not work on all operating systems. To send this XML document, the first client C program follows these steps:

1.  After declaring variables in `main()`, an XML context, `xctx`, is created using `XmlCreate()` and the context is then used to create a SOAP context, `ctx`, using `XmlSoapCreateCtx()`.

2.  To construct the message, `XmlSoapCreateMsg()` is called and returns an empty SOAP message.

3.  The header is constructed using `XmlSoapAddHeaderElement()`, `XmlSoapSetRole()`, `XmlSoapSetMustUnderstand()`, and `XmlDomAddTextElem()` to fill in the envelope with text.

4.  The body elements are created by `XmlSoapAddBodyElement()`, `XmlDomCreateElemNS()`, and a series of invocations of `XmlDomAddTextElem()`. Then `XmlDomAppendChild()` completes the section of the body specifying the New York to Los Angeles flight.

5.  The return flight is built in an analogous way. The lodging is added with another `XmlSoapAddBodyElement()` invocation.

6.  The connection must be created next with `XmlSoapCreateConnection()`, specifying HTTP binding (the only binding available now) and an endpoint URL.

7.  The function `XmlSoapCall()` sends the message over the defined connection with the SOAP server, and then waits for the reply.

8.  The message reply is returned in the form of another SOAP message. This is done with `XmlSaveDom()` and `XmlSoapHasFault()` used with `XmlSoapGetFault()` to check for a fault and analyze the fault. The fault is parsed into its parts, which is output in this example.

9.  If there was no fault returned, this is followed by `XmlSoapGetBody()` to return the envelope body. `XmlSaveDom()` completes the analysis of the returned message.

10. To clean up, use `XmlSoapDestroyMsg()` on the message and on the reply, `XmlDestroyCtx()` to destroy the SOAP context, and `XmlDestroy()` to destroy the XML context.

Example 9-4 Example 1 SOAP Message

    <?xml version='1.0' ?>
    <env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope">
     <env:Header>
      <m:reservation xmlns:m="http://travelcompany.example.org/reservation"
              env:role="http://www.w3.org/2003/05/soap-envelope/role/next"
               env:mustUnderstand="true">
       <m:reference>uuid:093a2da1-q345-739r-ba5d-pqff98fe8j7d</m:reference>
       <m:dateAndTime>2001-11-29T13:20:00.000-05:00</m:dateAndTime>
      </m:reservation>
      <n:passenger xmlns:n="http://mycompany.example.com/employees"
              env:role="http://www.w3.org/2003/05/soap-envelope/role/next"
               env:mustUnderstand="true">
       <n:name>John Smith</n:name>
      </n:passenger>
     </env:Header>
     <env:Body>
      <p:itinerary
        xmlns:p="http://travelcompany.example.org/reservation/travel">
       <p:departure>
         <p:departing>New York</p:departing>
         <p:arriving>Los Angeles</p:arriving>
         <p:departureDate>2001-12-14</p:departureDate>
         <p:departureTime>late afternoon</p:departureTime>
         <p:seatPreference>aisle</p:seatPreference>
       </p:departure>
       <p:return>
         <p:departing>Los Angeles</p:departing>
         <p:arriving>New York</p:arriving>
         <p:departureDate>2001-12-20</p:departureDate>
         <p:departureTime>mid-morning</p:departureTime>
         <p:seatPreference/>
       </p:return>
      </p:itinerary>
      <q:lodging
       xmlns:q="http://travelcompany.example.org/reservation/hotels">
       <q:preference>none</q:preference>
      </q:lodging>
     </env:Body>
    </env:Envelope>

Example 9-5 Example 1 SOAP C Client

    #ifndef S_ORACLE
    # include <s.h>
    #endif

    #ifndef XML_ORACLE
    # include <xml.h>
    #endif

    #ifndef XMLSOAP_ORACLE
    # include <xmlsoap.h>
    #endif


    #define MY_URL "http://my_url.com"

    /* static function declaration */
    static xmlerr add_ns_decl(xmlsoapctx  *ctx, xmlctx *xctx, xmlelemnode *elem,
                            oratext *pfx, oratext *uri);


    sb4 main( sword argc, char *argv[])
    {
        xmlctx      *xctx;
        xmlerr       xerr;
        xmlsoapctx  *ctx;
        oratext     *url;
        xmlsoapcon  *con;

        xmldocnode  *msg1, *reply, *msg2, *msg3;
        xmlelemnode *res, *pas, *pref, *itin, *departure, *ret, *lodging;
        xmlelemnode *departing, *arriving, *trans, *text, *charge, *card, *name;
        xmlelemnode *body, *header;
        boolean      has_fault;
        oratext     *code, *reason, *lang, *node, *role;
        xmlelemnode *detail;
        oratext *comp_uri   = "http://travelcompany.example.org/";
        oratext *mres_uri   = "http://travelcompany.example.org/reservation";
        oratext *trav_uri   = "http://travelcompany.example.org/reservation/travel";
        oratext *hotel_uri  = "http://travelcompany.example.org/reservation/hotels";
        oratext *npas_uri   = "http://mycompany.example.com/employees";

        oratext *tparty_uri = "http://thirdparty.example.org/transaction";
        oratext *estyle_uri = "http://example.com/encoding";
        oratext *soap_style_uri = "http://www.w3.org/2003/05/soap-encoding";
        oratext *estyle     = "env:encodingStyle";
        oratext *finance_uri = "http://mycompany.example.com/financial";


        if (!(xctx = XmlCreate(&xerr, (oratext *)"SOAP_test",NULL)))
        {
            printf("Failed to create XML context, error %u\n", (unsigned) xerr);
            return EX_FAIL;
        }
        /* Create SOAP context */
        if (!(ctx = XmlSoapCreateCtx(xctx, &xerr, (oratext *) "example", NULL)))
           {
             printf("Failed to create SOAP context, error %u\n", (unsigned) xerr);
             return EX_FAIL;
           }


        /* EXAMPLE 1 */
        /* construct message */
        if (!(msg1 = XmlSoapCreateMsg(ctx, &xerr)))
        {
          printf("Failed to create SOAP message, error %u\n", (unsigned) xerr);
          return xerr;
        }
        res = XmlSoapAddHeaderElement(ctx, msg1, "m:reservation", mres_uri, &xerr);
        xerr = XmlSoapSetRole(ctx, res, XMLSOAP_ROLE_NEXT);
        xerr = XmlSoapSetMustUnderstand(ctx, res, TRUE);
        (void) XmlDomAddTextElem(xctx, res, mres_uri, "m:reference",
                     "uuid:093a2da1-q345-739r-ba5d-pqff98fe8j7d");
        (void) XmlDomAddTextElem(xctx, res, mres_uri, "m:dateAndTime",
                                   "2001-11-29T13:20:00.000-05:00");
        pas = XmlSoapAddHeaderElement(ctx, msg1, "n:passenger", npas_uri, &xerr);
        xerr = XmlSoapSetRole(ctx, pas, XMLSOAP_ROLE_NEXT);
        xerr = XmlSoapSetMustUnderstand(ctx, pas, TRUE);
        (void) XmlDomAddTextElem(xctx, pas, npas_uri, "n:name",
                                  "John Smith");
        /* Fill body */
        /* Itinerary */
        itin = XmlSoapAddBodyElement(ctx, msg1, "p:itinerary", trav_uri, &xerr);
        /* Departure */
        departure = XmlDomCreateElemNS(xctx, msg1,  trav_uri, "p:departure");
        (void) XmlDomAddTextElem(xctx, departure, trav_uri,
                                  "p:departing","New York");
        (void) XmlDomAddTextElem(xctx, departure, trav_uri,
                                  "p:arriving", "Los Angeles");
        (void) XmlDomAddTextElem(xctx, departure, trav_uri,
                                  "p:departureDate", "2001-12-14");
        (void) XmlDomAddTextElem(xctx, departure, trav_uri,
                                  "p:departureTime", "late afternoon");
        (void) XmlDomAddTextElem(xctx, departure, trav_uri,
                                  "p:seatPreference", "aisle");
        XmlDomAppendChild(xctx, itin, departure);

        /* Return */
        ret = XmlDomCreateElemNS(xctx, msg1,  trav_uri, "p:return");
        (void) XmlDomAddTextElem(xctx, ret, trav_uri,
                                  "p:departing", "Los Angeles");
        (void) XmlDomAddTextElem(xctx, ret, trav_uri,
                                  "p:arriving", "New York");
        (void) XmlDomAddTextElem(xctx, ret, trav_uri,
                                  "p:departureDate", "2001-12-20");
        (void) XmlDomAddTextElem(xctx, ret, trav_uri,
                                  "p:departureTime", "mid-morning");
        pref = XmlDomCreateElemNS(xctx, msg1, trav_uri, "p:seatPreference");
        (void) XmlDomAppendChild(xctx, ret, pref);
        XmlDomAppendChild(xctx, itin, ret);

        /* Lodging */
        lodging = XmlSoapAddBodyElement(ctx, msg1, "q:lodging", hotel_uri, &xerr);
        (void) XmlDomAddTextElem(xctx, lodging, hotel_uri,
                                  "q:preference", "none");

    #ifdef DEBUG
        /* dump the message in debug mode */
        printf("Message:\n");
        XmlSaveDom(xctx, &xerr, msg1, "stdio", stdout, "indent_step", 1, NULL);
    #endif

    /* END OF EXAMPLE 1 */

        /* create connection */
        url = MY_URL;
        if (!(con = XmlSoapCreateConnection(ctx, &xerr, XMLSOAP_BIND_HTTP,
              url, NULL, 0, NULL, 0,
              "XTest: baz", NULL)))
          {
            printf("Failed to create SOAP connection, error %u\n", (unsigned) xerr);
            return xerr;
        }

        reply = XmlSoapCall(ctx, con, msg1, &xerr);
        XmlSoapDestroyConnection(ctx, con);

        if (!reply)
        {
          printf("Call failed, no message returned.\n");
          return xerr;
        }

    #ifdef DEBUG
        printf("Reply:\n");
        XmlSaveDom(xctx, &xerr, reply, "stdio", stdout, NULL);
    #endif

         printf("\n==== Header:\n ");
        header = XmlSoapGetHeader(ctx, reply, &xerr);
        if (!header)
        {
            printf("NULL\n");
        }
        else
            XmlSaveDom(xctx, &xerr, header, "stdio", stdout, NULL);


       /* check for fault */
        has_fault = XmlSoapHasFault(ctx, reply, &xerr);
        if(has_fault)
        {
            lang = NULL;
            xerr = XmlSoapGetFault(ctx, reply, &code, &reason, &lang,
                                   &node, &role, &detail);
            if (xerr)
            {
                printf("error getting Fault %d\n", xerr);
                return EX_FAIL;
            }
             if(code)
                printf("   Code -- %s\n", code);
            else
                printf("   NO Code\n");
            if(reason)
                printf("   Reason -- %s\n", reason);
            else
                printf("   NO Reason\n");
            if(lang)
                printf("   Lang -- %s\n", lang);
            else
                printf("   NO Lang\n");
            if(node)
                printf("   Node -- %s\n", node);
            else
                printf("   NO Node\n");
            if(role)
                printf("   Role -- %s\n", role);
            else
                printf("   NO Role\n");
            if(detail)
            {
                printf("   Detail\n");
                XmlSaveDom(xctx, &xerr, detail, "stdio", stdout, NULL);
                printf("\n");
            }
            else
                printf("   NO Detail\n");

        }
        else
        {
            body = XmlSoapGetBody(ctx, reply, &xerr);
            printf("==== Body:\n ");
            if (!body)
            {
                printf("NULL\n");
                return EX_FAIL;
            }
            XmlSaveDom(xctx, &xerr, body, "stdio", stdout, NULL);
        }
        (void) XmlSoapDestroyMsg(ctx, reply);
        (void) XmlSoapDestroyMsg(ctx, msg1);
        (void) XmlSoapDestroyCtx(ctx);
        XmlDestroy(xctx);
    }

### 9.4 SOAP Example 2: A Response Asking for Clarification

A travel company wants to know which New York airport a traveller, John Smith, will depart from: JFK, EWR, or LGA. It sends a response message that asks for such clarification.

To send this XML document as a SOAP message, substitute this code block for the lines beginning with `/* EXAMPLE 1 */` and ending with `/* END OF EXAMPLE 1 */` in Example 9-5

Example 9-6 Example 2 SOAP Message

    <?xml version='1.0' ?>
    <env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope">
     <env:Header>
      <m:reservation xmlns:m="http://travelcompany.example.org/reservation"
          env:role="http://www.w3.org/2003/05/soap-envelope/role/next"
               env:mustUnderstand="true">
       <m:reference>uuid:093a2da1-q345-739r-ba5d-pqff98fe8j7d</m:reference>
       <m:dateAndTime>2001-11-29T13:35:00.000-05:00</m:dateAndTime>
      </m:reservation>
      <n:passenger xmlns:n="http://mycompany.example.com/employees"
          env:role="http://www.w3.org/2003/05/soap-envelope/role/next"
               env:mustUnderstand="true">
       <n:name>John Smith</n:name>
      </n:passenger>
     </env:Header>
     <env:Body>
      <p:itineraryClarification
        xmlns:p="http://travelcompany.example.org/reservation/travel">
       <p:departure>
         <p:departing>
           <p:airportChoices>
              JFK LGA EWR
           </p:airportChoices>
         </p:departing>
       </p:departure>
       <p:return>
         <p:arriving>
           <p:airportChoices>
             JFK LGA EWR
           </p:airportChoices>
         </p:arriving>
       </p:return>
      </p:itineraryClarification>
     </env:Body>
    </env:Envelope>

Example 9-7 Example 2 SOAP C Client

    #define XMLSOAP_MAX_NAME        1024

    /* we need this function for examples 2 and 3 */
    static xmlerr add_ns_decl(xmlsoapctx  *ctx, xmlctx *xctx, xmlelemnode *elem,
                              oratext *pfx, oratext *uri)
    {
        oratext     *aq, aqbuf[XMLSOAP_MAX_NAME];
        xmldocnode  *doc;
        oratext     *xmlns = "xmlns:";

        /* if no room for "xmlns:usersprefix\0" then fail now */
        if ((strlen((char *)pfx) + strlen((char *)xmlns)) >
            sizeof(aqbuf))
            return EX_FAIL;
        (void) strcpy((char *)aqbuf, (char *)xmlns);
        strcat((char *)aqbuf, (char *)pfx);
        doc = XmlDomGetOwnerDocument(xctx, elem);
        aq = XmlDomSaveString(xctx, doc, aqbuf);
        XmlDomSetAttrNS(xctx, elem, uri, aq, uri);
        return XMLERR_OK;
    }

        /* EXAMPLE 2 */
        /* construct message */
        if (!(msg2 = XmlSoapCreateMsg(ctx, &xerr)))
        {
             printf("Failed to create SOAP message, error %u\n", (unsigned) xerr);
             return xerr;
        }
        res = XmlSoapAddHeaderElement(ctx, msg2, "m:reservation", mres_uri, &xerr);
        xerr = XmlSoapSetRole(ctx, res, XMLSOAP_ROLE_NEXT);
        xerr = XmlSoapSetMustUnderstand(ctx, res, TRUE);
        (void) XmlDomAddTextElem(xctx, res, mres_uri, "m:reference",
                     "uuid:093a2da1-q345-739r-ba5d-pqff98fe8j7d");
        (void) XmlDomAddTextElem(xctx, res, mres_uri, "m:dateAndTime",
                                   "2001-11-29T13:35:00.000-05:00");
        pas = XmlSoapAddHeaderElement(ctx, msg2, "n:passenger", npas_uri, &xerr);
        xerr = XmlSoapSetRole(ctx, pas, XMLSOAP_ROLE_NEXT);
        xerr = XmlSoapSetMustUnderstand(ctx, pas, TRUE);
        (void) XmlDomAddTextElem(xctx, pas, npas_uri, "n:name",
                                  "John Smith");
        /* Fill body */
        /* Itinerary */
        itin = XmlSoapAddBodyElement(ctx, msg2, "p:itineraryClarification",
                                     trav_uri, &xerr);
        /* Departure */
        departure = XmlDomCreateElemNS(xctx, msg2,  trav_uri, "p:departure");
        departing = XmlDomCreateElem(xctx, msg2,  "p:departing");
        (void) XmlDomAddTextElem(xctx, departing, trav_uri,
                                  "p:airportChoices", "JFK LGA EWR");
        (void) XmlDomAppendChild(xctx, departure, departing);
        XmlDomAppendChild(xctx, itin, departure);

        /* Return */
        ret = XmlDomCreateElemNS(xctx, msg2,  trav_uri, "p:return");
        arriving = XmlDomCreateElemNS(xctx, msg2,  trav_uri, "p:arriving");
        (void) XmlDomAddTextElem(xctx, arriving, trav_uri,
                                  "p:airportChoices", "JFK LGA EWR");
        XmlDomAppendChild(xctx, ret, arriving);
        XmlDomAppendChild(xctx, itin, ret);

    #ifdef DEBUG
        XmlSaveDom(xctx, &xerr, msg2, "stdio", stdout, "indent_step", 1, NULL);
    #endif

### 9.5 SOAP Example 3: Using POST

An example sends credit card information for John Smith as an XML document using method `POST`. `XmlSoapCall()` writes the HTTP header that precedes the XML message in the example.

The C Client includes this code block which is substituted like the second example in Example 9-5:

Example 9-8 Example 3 SOAP Message

    POST /Reservations HTTP/1.0
    Host: travelcompany.example.org
    Content-Type: application/soap+xml; charset="utf-8"
    Content-Length: nnnn

    <?xml version='1.0' ?>
    <env:Envelope xmlns:env="http://www.w3.org/2003/05/soap-envelope" >
     <env:Header>
       <t:transaction
               xmlns:t="http://thirdparty.example.org/transaction"
               env:encodingStyle="http://example.com/encoding"
               env:mustUnderstand="true" >5</t:transaction>
     </env:Header>
     <env:Body>
      <m:chargeReservation
          env:encodingStyle="http://www.w3.org/2003/05/soap-encoding"
             xmlns:m="http://travelcompany.example.org/">
       <m:reservation xmlns:m="http://travelcompany.example.org/reservation">
        <m:code>FT35ZBQ</m:code>
       </m:reservation>
       <o:creditCard xmlns:o="http://mycompany.example.com/financial">
        <n:name xmlns:n="http://mycompany.example.com/employees">
               John Smith
        </n:name>
        <o:number>123456789099999</o:number>
        <o:expiration>2005-02</o:expiration>
       </o:creditCard>
      </m:chargeReservation>
     </env:Body>
    </env:Envelope>

Example 9-9 Example 3 SOAP C Client

    #define XMLSOAP_MAX_NAME        1024

    /* we need this function for examples 2 and 3 */
    static xmlerr add_ns_decl(xmlsoapctx  *ctx, xmlctx *xctx, xmlelemnode *elem,
                              oratext *pfx, oratext *uri)
    {
        oratext     *aq, aqbuf[XMLSOAP_MAX_NAME];
        xmldocnode  *doc;
        oratext     *xmlns = "xmlns:";

        /* if no room for "xmlns:usersprefix\0" then fail now */
        if ((strlen((char *)pfx) + strlen((char *)xmlns)) >
            sizeof(aqbuf))
            return EX_FAIL;
        (void) strcpy((char *)aqbuf, (char *)xmlns);
        strcat((char *)aqbuf, (char *)pfx);
        doc = XmlDomGetOwnerDocument(xctx, elem);
        aq = XmlDomSaveString(xctx, doc, aqbuf);
        XmlDomSetAttrNS(xctx, elem, uri, aq, uri);
        return XMLERR_OK;
    }

        /* EXAMPLE 3 */
        if (!(msg3 = XmlSoapCreateMsg(ctx, &xerr)))
        {
            printf("Failed to create SOAP message, error %u\n", (unsigned) xerr);
            return xerr;
        }
        trans = XmlSoapAddHeaderElement(ctx,msg3, "t:transaction", tparty_uri, &xerr);
        xerr = XmlSoapSetMustUnderstand(ctx, trans, TRUE);
        XmlDomSetAttr(xctx, trans, estyle, estyle_uri);
        text = XmlDomCreateText(xctx, msg3, "5");
        XmlDomAppendChild(xctx, trans, text);

        /* Fill body */
        /* Charge Reservation */
        charge = XmlSoapAddBodyElement(ctx,msg3,"m:chargeReservation",comp_uri,&xerr);
        XmlDomSetAttr(xctx, charge, estyle, soap_style_uri);
        res = XmlDomCreateElemNS(xctx, msg3, mres_uri,  "m:reservation");
        if (add_ns_decl(ctx, xctx, res, "m", mres_uri))
            return EX_FAIL;
        (void) XmlDomAddTextElem(xctx, res, mres_uri,
                                  "m:code", "FT35ZBQ");
        (void) XmlDomAppendChild(xctx, charge, res);

        /* create card elem with  namespace */
        card = XmlDomCreateElemNS(xctx, msg3, finance_uri, "o:creditCard");
        if (add_ns_decl(ctx, xctx, card, "o", finance_uri))
            return EX_FAIL;
        name =  XmlDomAddTextElem(xctx, card, npas_uri,
                                  "n:name", "John Smith");
        /* add namespace */
        if (add_ns_decl(ctx, xctx, name, "n", npas_uri))
            return EX_FAIL;
        (void)  XmlDomAddTextElem(xctx, card, finance_uri,
                                  "o:number", "123456789099999");
        (void) XmlDomAddTextElem(xctx, card, finance_uri,
                                  "o:expiration", "2005-02");
        (void) XmlDomAppendChild(xctx, charge, card);

    #ifdef DEBUG
        XmlSaveDom(xctx, &xerr, msg3, "stdio", stdout, "indent_step", 1, NULL);
    #endif
