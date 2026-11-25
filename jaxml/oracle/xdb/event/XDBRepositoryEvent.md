Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBRenderStream.md)**
- **[Next Class](XDBRepositoryEventListener.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xdb.event**

## **Class XDBRepositoryEvent**

- **java.lang.Object**

- - **[oracle.xdb.event.XDBEvent](XDBEvent.md)**

  - - **oracle.xdb.event.XDBRepositoryEvent**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBRepositoryEvent
      extends XDBEvent

  **This class stores information about the repository event that is fired. An object of this type is constructed and passed to event handlers. Handlers can use this to obtain information about the triggering event and the resources involved.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from class oracle.xdb.event.[XDBEvent](XDBEvent.md)**

      **[`POST_CHECKIN_EVENT`](XDBEvent.md)`, `[`POST_CHECKOUT_EVENT`](XDBEvent.md)`, `[`POST_CREATE_EVENT`](XDBEvent.md)`, `[`POST_DELETE_EVENT`](XDBEvent.md)`, `[`POST_INCONUPDATE_EVENT`](XDBEvent.md)`, `[`POST_LINKIN_EVENT`](XDBEvent.md)`, `[`POST_LINKTO_EVENT`](XDBEvent.md)`, `[`POST_LOCK_EVENT`](XDBEvent.md)`, `[`POST_OPEN_EVENT`](XDBEvent.md)`, `[`POST_UNCHECKOUT_EVENT`](XDBEvent.md)`, `[`POST_UNLINKFROM_EVENT`](XDBEvent.md)`, `[`POST_UNLINKIN_EVENT`](XDBEvent.md)`, `[`POST_UNLOCK_EVENT`](XDBEvent.md)`, `[`POST_UPDATE_EVENT`](XDBEvent.md)`, `[`POST_VERSIONCONTROL_EVENT`](XDBEvent.md)`, `[`PRE_CHECKIN_EVENT`](XDBEvent.md)`, `[`PRE_CHECKOUT_EVENT`](XDBEvent.md)`, `[`PRE_CREATE_EVENT`](XDBEvent.md)`, `[`PRE_DELETE_EVENT`](XDBEvent.md)`, `[`PRE_INCONUPDATE_EVENT`](XDBEvent.md)`, `[`PRE_LINKIN_EVENT`](XDBEvent.md)`, `[`PRE_LINKTO_EVENT`](XDBEvent.md)`, `[`PRE_LOCK_EVENT`](XDBEvent.md)`, `[`PRE_OPEN_EVENT`](XDBEvent.md)`, `[`PRE_UNCHECKOUT_EVENT`](XDBEvent.md)`, `[`PRE_UNLINKFROM_EVENT`](XDBEvent.md)`, `[`PRE_UNLINKIN_EVENT`](XDBEvent.md)`, `[`PRE_UNLOCK_EVENT`](XDBEvent.md)`, `[`PRE_UPDATE_EVENT`](XDBEvent.md)`, `[`PRE_VERSIONCONTROL_EVENT`](XDBEvent.md)`, `[`RENDER_EVENT`](XDBEvent.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                |
    |--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLType`](../XMLType.md)                 | `getApplicationData``()`<br>Returns the \<applicationData\> element extracted from the resource configuration that defines the invoking handler.                      |
    | [`XDBHandlerList`](XDBHandlerList.md)      | `getHandlerList``()`<br>Returns an `XDBHandlerList` object that contains the list of handlers that will be executed after the current handler.                        |
    | `java.lang.String`                         | `getInterface``()`<br>Returns the top-level interface used to initiate the operation that triggered the event.                                                        |
    | [`XDBLink`](XDBLink.md)                    | `getLink``()`<br>Returns an `XDBLink` object for the target resource.                                                                                                 |
    | `oracle.xdb.spi.XDBResource`               | `getOldResource``()`<br>Returns the original `XDBResource` object before the operation was executed.                                                                  |
    | [`XDBOutputStream`](../XDBOutputStream.md) | `getOutputStream``()`<br>Returns the output stream where the handler can write the rendered data.                                                                     |
    | `java.lang.String`                         | `getParameter``(java.lang.String key)`<br>Returns the value of a request or session-specific parameter.                                                               |
    | `oracle.xdb.spi.XDBResource`               | `getParent``()`<br>Returns the `XDBResource` object corresponding to a parent folder of the target resource.                                                          |
    | [`XDBPath`](XDBPath.md)                    | `getPath``()`<br>Returns the `XDBPath` object that represents the path of the resource for which the event was fired .                                                |
    | `oracle.xdb.spi.XDBResource`               | `getResource``()`<br>Returns an `XDBResource` object that provides methods to access and modify the contents and metadata of the target resource.                     |
    | `javax.servlet.http.HttpServletRequest`    | `getServletRequest``()`<br>Returns the servlet request object that corresponds to the HTTP request if the current interface is HTTP; otherwise, an error is returned. |
    | `void`                                     | `setRenderPath``(java.lang.String path)`<br>Specifies the path of the resource that contains the rendered contents.                                                   |
    | `void`                                     | `setRenderStream``(java.io.InputStream istr)`<br>Sets the stream where the rendered contents can be read.                                                             |

    - ### Methods inherited from class oracle.xdb.event.[XDBEvent](XDBEvent.md)

      [`getCurrentUser`](XDBEvent.md)`, `[`getEvent`](XDBEvent.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getInterface

          public java.lang.String getInterface()

      Returns the top-level interface used to initiate the operation that triggered the event.
      Returns:
      "HTTP", "FTP" or "SQL".

    <!-- -->

    - #### getServletRequest

          public javax.servlet.http.HttpServletRequest getServletRequest()

      Returns the servlet request object that corresponds to the HTTP request if the current interface is HTTP; otherwise, an error is returned. This method is not available from PL/SQL Events API because there is currently no PL/SQL servlet model supported by Oracle XML Database.
      Returns:
      The servlet request object

    <!-- -->

    - #### getApplicationData

          public XMLType getApplicationData()

      Returns the \<applicationData\> element extracted from the resource configuration that defines the invoking handler.
      Returns:
      The \<applicationData\> element

    <!-- -->

    - #### getPath

          public XDBPath getPath()

      Returns the `XDBPath` object that represents the path of the resource for which the event was fired . Using this object, you can obtain the path segments.
      Returns:
      path of the resource for which the event was fired

    <!-- -->

    - #### getResource

          public oracle.xdb.spi.XDBResource getResource()

      Returns an `XDBResource` object that provides methods to access and modify the contents and metadata of the target resource. This object reflects any changes made by previous handlers to the resource. Note that the modifier methods will work only in pre-create and pre-update event handlers. For a link\* or unlink\* event, this method returns the resource to which the link points. For a create event, this method returns the resource that is being created.
      Returns:
      The target resource.

    <!-- -->

    - #### getParent

          public oracle.xdb.spi.XDBResource getParent()

      Returns the `XDBResource` object corresponding to a parent folder of the target resource. Note that this could be any folder that contains a link to the target resource. This is a read-only object. This means that none of the modifier methods will work on this object. For a link\* or unlink\* event, this method returns the link's parent folder.
      Returns:
      Parent of the target resource

    <!-- -->

    - #### getHandlerList

          public XDBHandlerList getHandlerList()

      Returns an `XDBHandlerList` object that contains the list of handlers that will be executed after the current handler. The current handler can then filter out some of the subsequent handlers if necessary, subject to security checks. An insufficient privilege exception is thrown if the executing user does not have the required access privilege to any resource configuration associated with a handler in the list.
      Returns:
      list of handlers yet to be executed

    <!-- -->

    - #### getLink

          public XDBLink getLink()

      Returns an `XDBLink` object for the target resource. For a link or unlink event, this will be the link involved in the operation. For other events, an error is returned. Using this object the handler can access link properties such as ParentName, ParentOID, ChildOID and LinkName.
      Returns:
      The link object

    <!-- -->

    - #### getParameter

          public java.lang.String getParameter(java.lang.String key)

      Returns the value of a request or session-specific parameter. Currently, the only parameters supported are 'Accept', 'Accept-Language', 'Accept-Charset' and 'Accept-Encoding'. The definition of these parameters can be found in RFC 2616 (HTTP/1.1). They will be mapped to equivalent SQL session parameters (if any).
      Returns:
      The value of the parameter

    <!-- -->

    - #### getOldResource

          public oracle.xdb.spi.XDBResource getOldResource()

      Returns the original `XDBResource` object before the operation was executed. This method applies only to Update event. For other events, an error is returned. This is a read-only object. This means that none of the modifier methods will work on this object.
      Returns:
      The old `XDBResource`

    <!-- -->

    - #### getOutputStream

          public XDBOutputStream getOutputStream()

      Returns the output stream where the handler can write the rendered data. This is only valid for the Render event.
      Returns:
      An output stream for the handler

    <!-- -->

    - #### setRenderStream

          public void setRenderStream(java.io.InputStream istr)
                               throws java.sql.SQLException

      Sets the stream where the rendered contents can be read. This should not be called after the stream returned by `getOutputStream()` is written or after `setRenderPath()` is called; doing so will result in an error. This is only valid for the Render event.
      Parameters:
      `istr` - - The input stream

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setRenderPath

          public void setRenderPath(java.lang.String path)

      Specifies the path of the resource that contains the rendered contents. This should not be called after the stream returned by `getOutputStream()` is written or after `setRenderStream()` is called; doing so will result in an error. This is only valid for the Render event.
      Parameters:
      `path` - - The path of the resource to read data

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBRenderStream.md)**
- **[Next Class](XDBRepositoryEventListener.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
