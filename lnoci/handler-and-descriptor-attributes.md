Describes the attributes for OCI handles and descriptors.

The attributes for OCI handles and descriptors can be read with `OCIAttrGet()` and modified with `OCIAttrSet()`.

### 34.2.1 Conventions

For each handle type, the attributes that can be read or changed are listed.

Each attribute listing includes the following information:

Mode
The following modes are valid:

`READ` - The attribute can be read using `OCIAttrGet()`.

`WRITE` - The attribute can be modified using `OCIAttrSet()`.

`READ/WRITE` - The attribute can be read using `OCIAttrGet()`, and it can be modified using `OCIAttrSet()`.

Description
This is a description of the purpose of the attribute.

Attribute Data Type
This is the data type of the attribute. If necessary, a distinction is made between the data type for `READ` and `WRITE` modes.

### 34.2.2 Server Handle Attributes

Lists the server handle attributes.

The following server handle attributes are available:

- OCI_ATTR_XSTREAM_ACK_INTERVAL

- OCI_ATTR_XSTREAM_IDLE_TIMEOUT

#### 34.2.2.1 OCI_ATTR_XSTREAM_ACK_INTERVAL

Describes the OCI_ATTR_XSTREAM_ACK_INTERVAL server handle attribute.

Mode
`READ/WRITE`

Description
For XStream Out, the ACK interval is the minimum interval in seconds that the outbound server receives the processed low position from the client application. After each ACK interval, the outbound server ends any in-progress `OCIXStreamOutLCRReceive()` or `OCIXStreamOutLCRCallbackReceive()` call so that the processed low position cached at the client application can be sent to the outbound server.

For XStream In, the ACK interval is the minimum interval in seconds that the inbound server sends the processed low position to the client application. After each ACK interval, any in-progress `OCIXStreamInLCRSend()` or `OCIXStreamInLCRCallbackSend()` call is terminated for the inbound server to send a new processed low position to the client application.

The default value for `OCI_ATTR_XSTREAM_ACK_INTERVAL` is 30 seconds. This attribute is checked only during the `OCIXStreamOutAttach()` or `OCIXStreamInAttach()` calls. Thus, it must be set before invoking these APIs; otherwise, the default value is used.

Attribute Data Type
`ub4 *`/`ub4`

#### 34.2.2.2 OCI_ATTR_XSTREAM_IDLE_TIMEOUT

Describes the OCI_ATTR_XSTREAM_IDLE_TIMEOUT server handle attribute.

Mode
`READ/WRITE`

Description
The idle timeout is the number of seconds of idle the outbound server waits for an LCR before terminating the `OCIXStreamOutLCRReceive()` or `OCIXStreamOutLCRCallbackReceive()` call.

The default for `OCI_ATTR_XSTREAM_IDLE_TIMEOUT` is one second. This attribute is checked only during the `OCIXStreamOutAttach()` or `OCIXStreamInAttach()` call. Thus, it must be set before invoking these APIs; otherwise, the default value is used.

Attribute Data Type
`ub4 *`/`ub4`
