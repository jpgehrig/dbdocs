Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](StreamsException.md)
- [Next Class](XStreamLCRCallbackHandler.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.streams

## Class XStreamIn

- java.lang.Object

- - oracle.streams.XStreamIn

<!-- -->

-

  ------------------------------------------------------------------------



      public class XStreamIn
      extends java.lang.Object

  The XStreamIn class provides APIs for using Oracle XStream In. This is the main Java API for Oracle XStream Inbound. It has the following main API methods as shown in the list.
  - Attach(): Attach to an XStream inbound server.
  - Detach(): Detach from an XStream inbound server.
  - SendLCRCallback(): Send a stream of logical change records (LCRs) to the XStream inbound server in callback mode. Specify an XStreamLCRCallbackHandler that constructs the LCRs that are sent to the XStream inbound server.
  - SendLCR(): Send one LCR to the XStream inbound server in non-callback mode.
  - SendChunk(): Send chunk data for LCRs that contain LOB, LONG, or XMLTYPE columns. Invoke this API only after invoking the sendLCR() API if the LCR contains chunk data.

  Here is an example of using the callback API:
         Connection conn;
         XStreamIn xsIn;
         ...

         // assume myLCRHandler implements XStreamLCRCallbackHandler
         XStreamLCRCallbackHandler hdlr = new MyLCRHandler();

         try
         {
           DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
           conn = DriverManager.getConnection("jdbc:oracle:oci:@hostname:port:sid",
                            "strmadm", "strmadm");
           xsIn = XStreamIn.attach(conn, new String("APPLY1"), new String("CAP1"),
                                   XStreamIn.DEFAULT_MODE);
           while(true)
           {
             xsIn.sendLCRCallback(hdlr, XStreamIn.DEFAULT_MODE);
             // maintain processed low watermark
             maintainWatermark();
             ...
             if (user_terminate_condition)
             {
               break;
             }
           }
           xsIn.detach(XStreamIn.DEFAULT_MODE);
         }
         catch(StreamsException e)
         {
            System.out.println("Streams exception: " + e.getMessage());
         }
         catch(Exception e)
         {
         }


  Please see createLCR() and createChunk() in XStreamLCRCallbackHandler for examples of implementing the callback methods.
  Here is an example of using the non-callback API:

         Connection conn;
         XStreamIn xsIn;
         ...

         try
         {
           DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
           conn = DriverManager.getConnection("jdbc:oracle:oci:@hostname:port:sid",
                            "strmadm", "strmadm");
           xsIn = XStreamIn.attach(conn, new String("APPLY1"), new String("CAP1"),
                                   XStreamIn.DEFAULT_MODE);
           lwm = xsIn.getProcessedLowWatermark(XStreamIn.DEFAULT_MODE);
           while(true)
           {
             RowLCR rowlcr = new DefaultRowLCR(...);

             if (rowlcr has chunk data)
               rowlcr.setChunkDataFlag(true);

             int status = xsIn.sendLCR(rowlcr, XStreamIn.DEFAULT_MODE);

             if (status == EXECUTING)
             {
               for (each chunk in each lob/long/xmltype column)
               {
                 ChunkColumnValue chunk = new DefaultChunkColumnValue(...);
                 if (chunk is the last one in the column)
                   chunk.setLastChunk(true);
                 if (chunk is the last one for entire row)
                   chunk.setEndOfRow(true);
                 xsIn.sendChunk(chunk, XStreamIn.DEFAULT_MODE);
               }
             }
             else // status == FINISHED
             {
               // maintain watermark
               lwm =  xsIn.getProcessedLowWatermark(XStreamIn.DEFAULT_MODE);
               maintainWatermark();
             }

             if (user_terminate_condition)
             {
               break;
             }
           }
           xsIn.detach(XStreamIn.DEFAULT_MODE);
         }
         catch(StreamsException e)
         {
            System.out.println("Streams exception: " + e.getMessage());
         }
         catch(Exception e)
         {
         }


<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                    |
    |-------------------|----------------------------------------------------------------------------------------------------------|
    | `static int`      | `DEFAULT_BATCH_INTERVAL`<br>XStreamIn default batch interval value for batch processing                  |
    | `static int`      | `DEFAULT_MODE`<br>XStreamIn default mode                                                                 |
    | `static int`      | `EXECUTING`<br>XStreamIn batch processing status EXECUTING, which indicates the the batch is in progress |
    | `static int`      | `FINISHED`<br>XStreamIn batch processing status FINISHED, which is the default status                    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                  |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static XStreamIn` | `attach``(oracle.jdbc.OracleConnection oconn, java.lang.String serverName, java.lang.String sourceName, int mode)`<br>Attaches to an inbound server.                    |
    | `static XStreamIn` | `attach``(oracle.jdbc.OracleConnection oconn, java.lang.String serverName, java.lang.String sourceName, int batchInterval, int mode)`<br>Attaches to an inbound server. |
    | `byte[]`           | `detach``(int mode)`<br>Detaches from an inbound server.                                                                                                                |
    | `void`             | `flush``(int mode)`<br>Flushes the network.                                                                                                                             |
    | `byte[]`           | `getLastPosition``()`<br>Gets last position.                                                                                                                            |
    | `byte[]`           | `getOldestPosition``()`<br>Gets the oldest position.                                                                                                                    |
    | `byte[]`           | `getProcessedLowWatermark``()`<br>Gets the processed low watermark.                                                                                                     |
    | `void`             | `sendChunk``(`[`ChunkColumnValue`](ChunkColumnValue.md)` chunk, int mode)`<br>Sends chunk data in non-callback mode.                                                    |
    | `int`              | `sendLCR``(`[`LCR`](LCR.md)` lcr, int mode)`<br>Sends one LCR in non-callback mode.                                                                                     |
    | `void`             | `sendLCRCallback``(`[`XStreamLCRCallbackHandler`](XStreamLCRCallbackHandler.md)` handler, int mode)`<br>Sends a stream of LCRs in callback mode.                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_MODE

          public static final int DEFAULT_MODE

      XStreamIn default mode
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEFAULT_BATCH_INTERVAL

          public static final int DEFAULT_BATCH_INTERVAL

      XStreamIn default batch interval value for batch processing
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FINISHED

          public static final int FINISHED

      XStreamIn batch processing status FINISHED, which is the default status
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EXECUTING

          public static final int EXECUTING

      XStreamIn batch processing status EXECUTING, which indicates the the batch is in progress
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### attach

          public static XStreamIn attach(oracle.jdbc.OracleConnection oconn,
                                         java.lang.String serverName,
                                         java.lang.String sourceName,
                                         int mode)
                                  throws StreamsException

      Attaches to an inbound server.
      This API attaches the client to the specified XStream inbound server. This is also the factory method that returns an XStreamIn instance once it is attached to a valid XStream inbound server.
      After successfully attached to an XStream inbound server, call getLastPosition() to decide where to start sending LCRs in the LCR stream.
      Parameters:
      `oconn` - Oracle database connection.
      Note that the connection must be made using Oracle OCI (thick) driver.

      `serverName` - Name of the XStream inbound server.

      `sourceName` - Name of the data source.

      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Returns:
      an XStreamIn instance object

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during attach.

    <!-- -->

    - #### attach

          public static XStreamIn attach(oracle.jdbc.OracleConnection oconn,
                                         java.lang.String serverName,
                                         java.lang.String sourceName,
                                         int batchInterval,
                                         int mode)
                                  throws StreamsException

      Attaches to an inbound server.
      This API is the same as the other attach API except that it includes the batchInterval parameter.
      Parameters:
      `oconn` - Oracle database connection.
      Note that the connection must be made using Oracle OCI (thick) driver.

      `serverName` - Name of the XStream inbound server.

      `sourceName` - Name of the data source

      `batchInterval` - XStreamIn batch processing interval.

      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Returns:
      an XStreamIn instance object

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during attach.

    <!-- -->

    - #### detach

          public byte[] detach(int mode)
                        throws StreamsException

      Detaches from an inbound server.
      This API detaches the client from the XStream inbound server.
      Parameters:
      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Returns:
      the inbound server's processed low watermark.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during detach.

    <!-- -->

    - #### sendLCRCallback

          public void sendLCRCallback(XStreamLCRCallbackHandler handler,
                                      int mode)
                               throws StreamsException

      Sends a stream of LCRs in callback mode.
      This API starts sending an LCR stream to the specified XStream inbound server using callback mode. You must supply an LCR callback handler that uses the createLCR() and createChunk() callback methods. See XStreamLCRCallbackHandler for details about the LCR callback handler.
      To reduce network roundtrip overhead, this method also starts a batch process that sends LCRs to the inbound server. The batch process is stopped after 30 seconds or when a NULL LCR is returned in the createLCR() callback method.
      Parameters:
      `handler` - The XStreamLCRCallbackHandler for constructing LCRs.

      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during the batch.

    <!-- -->

    - #### sendLCR

          public int sendLCR(LCR lcr,
                             int mode)
                      throws StreamsException

      Sends one LCR in non-callback mode.
      This method sends one LCR to the connected inbound server. To avoid a network round trip for each SendLCR call, XStreamIn starts a batch process internally to fill the network buffer with LCRs. This batch process is stopped after 30 seconds has elapsed.
      This method returns a batch status value of either EXECUTING or FINISHED. Note that when a RowLCR has chunkDataFlag set, the return status is always EXECUTING.
      Parameters:
      `lcr` - A constructed LCR.

      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Returns:
      The XStreamIn batch processing status.

      Throws:
      [`StreamsException`](StreamsException.md) - if the LCR is NULL or invalid, or error occurs while sending the LCR.

    <!-- -->

    - #### sendChunk

          public void sendChunk(ChunkColumnValue chunk,
                                int mode)
                         throws StreamsException

      Sends chunk data in non-callback mode.
      This API sends streaming LOB, LONG, and XMLTYPE chunk data.
      Call this API after calling sendLCR() to send chunk data for an LCR. Ensure that all of the chunks for one LOB column are sent before sending the chunks for another LOB column. The LOB columns can be sent in any order.
      Use setLastChunk() in chunkColumnValue to indicate whether the current chunk is the last chunk for a column. Use setEndOfRow() in chunkColumnValue to indicate whether the current chunk is the last chunk for an entire row change.
      Parameters:
      `chunk` - A ChunkColumnValue object that contains the chunk data for the LOB, LONG, or XMLTYPE column in a RowLCR

      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs while sending chunk data.

    <!-- -->

    - #### getProcessedLowWatermark

          public byte[] getProcessedLowWatermark()

      Gets the processed low watermark.
      Use this method to get the inbound server's processed low watermark. After attaching to an XStream inbound server, the client caches a local copy of the inbound server's processed low watermark. Each of the following calls refreshes the local copy with the inbound server's processed low watermark and returns the FINISHED batch status from sendLCR:
              attach
              sendLCR
              sendLCRCallback
              flush


      This method can be called while the client is attached to an XStream inbound server.
      Returns:
      The inbound server's processed low watermark.

    <!-- -->

    - #### getOldestPosition

          public byte[] getOldestPosition()

      Gets the oldest position.
      Use this method to get the inbound server's oldest position. After attaching to an XStream inbound server, the client caches a local copy of the inbound server's oldest position. Each of the following calls refreshes the local copy with the inbound server's oldest position and returns the FINISHED batch status from sendLCR:
              attach
              sendLCR
              flush


      This method can be called while the client is attached to an XStream inbound server.
      Returns:
      The inbound server's processed low watermark.

    <!-- -->

    - #### getLastPosition

          public byte[] getLastPosition()

      Gets last position.
      This method gets the inbound server's last position after an attach call. After attaching to an XStream inbound server, this method retrieves the inbound server's last position and sends it to the client. The client can use this last position to decide where to stream LCRs. Ensure that this method is called after successfully attaching to an XStream inbound server.
      Returns:
      The inbound server's processed low watermark.

    <!-- -->

    - #### flush

          public void flush(int mode)
                     throws StreamsException

      Flushes the network.
      This method flushes the network while attaching to an XStream inbound server. Ensure that this method is called only when there are no LCRs to send to the inbound server and the client needs to determine the progress of the inbound server.
      It terminates any in-progress batch processing and should not called in callback mode.
      This method contacts the inbound server to get the inbound server's processed low watermark. The getProcessedLowWatermark() method can retrieve the processed low watermark.
      Parameters:
      `mode` - The mode of XStream inbound server (for future extension). Use XStreamIn.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs while flushing network.

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](StreamsException.md)
- [Next Class](XStreamLCRCallbackHandler.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2001, 2019, Oracle and/or its affiliates. All Rights Reserved.
