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

- [Prev Class](XStreamLCRCallbackHandler.md)
- [Next Class](XStreamUtility.md)

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

## Class XStreamOut

- java.lang.Object

- - oracle.streams.XStreamOut

<!-- -->

-

  ------------------------------------------------------------------------



      public class XStreamOut
      extends java.lang.Object

  The XStreamOut class provides APIs for using Oracle XStream Out. This is the main Java API for Oracle XStream Out. It contains several main API methods as shown in the list.
  - Attach(): Attach to an XStream outbound server.
  - Detach(): Detach from an XStream outbound server.
  - ReceiveLCR(): Receive one LCR from the XStream outbound server in non-callback mode.
  - ReceiveChunk(): Retrieve chunk data in non-callback mode. Invoke this API after ReceiveLCR() if the LCR contains LOB, LONG, or XMLTYPE data.
  - ReceiveLCRCallback(): Receive a stream of LCRs from the XStream outbound server in callback mode. You can specify an XStreamLCRCallbackHandler to process the LCRs received from the XStream outbound server.

  Here is an example of using the callback API:

         Connection conn;
         XStreamOut xsOut;
         ...

         // assume myLCRHandler implements XStreamLCRCallbackHandler and
         XStreamLCRCallbackHandler hdlr = new MyLCRHandler();

         try
         {
           DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
           conn = DriverManager.getConnection("jdbc:oracle:oci:@hostname:port:sid",
                                              "strmadm", "strmadm");
           xsOut = XStreamOut.attach(conn, new String("APPLY1"),
                                     lastPosition,
                                     XStreamOut.ATTACH_APP_CONTAINER_MODE +
                                     XStreamOut.ATTACH_EXTENDED_ID_MODE);
           while(true)
           {
             xsOut.receiveLCRCallback(hdlr, XStreamOut.DEFAULT_MODE);
             maintainWatermark();
             ...
             if (user_terminate_condition)
             {
               break;
             }
           }
           xsOut.detach(XStreamOut.DEFAULT_MODE);
           }
         }
         catch(StreamsException e)
         {
            System.out.println("Streams exception: " + e.getMessage());
         }
         catch(Exception e)
         {
         }


  Please see processLCR() and processChunk() in XStreamLCRCallbackHandler for examples of implementing the callback methods.

  Here is an example of using the non-callback API:

         Connection conn;
         XStreamOut xsOut;
         ...

         try
         {
           DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
           conn = DriverManager.getConnection("jdbc:oracle:oci:@hostname:port:sid",
                                              "strmadm", "strmadm");
           xsOut = XStreamOut.attach(conn, new String("APPLY1"),
                                     lastPosition,
                                     XStreamOut.ATTACH_APP_CONTAINER_MODE +
                                     XStreamOut.ATTACH_EXTENDED_ID_MODE);
           while(true)
           {
             LCR alcr = xsOut.receiveLCR(XStreamOut.DEFAULT_MODE);
             if (xsOut.getBatchStatus == EXECUTING) // system is active
             {
               maintainWatermark();
               // ... process LCR header
               if (alcr instanceof RowLCR)
               {
                 // ... process scalar columns
                 // process chunk data using receiveChunk() API
                 if (((RowLCR)alcr).hasChunkData())
                 {
                   do
                   {
                     ChunkColumnValue chunk = xsOut.receiveChunk(DEFAULT_MODE);
                     // process the Chunk
                   } while (!chunk.isEndOfRow())
                 }
               }
             }
             else // system is idle
             {
               maintainWatermark();
               if (user_terminate_condition)
               {
                 break;
               }
             }
           }
           xsOut.detach(XStreamOut.DEFAULT_MODE);
           }
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

    | Modifier and Type | Field and Description                                                                                                     |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ATTACH_APP_CONTAINER_MODE`<br>This attach mode captures application container statements.                                |
    | `static int`      | `ATTACH_EXTENDED_ID_MODE`<br>This attach mode returns transaction ID using extended format, "pdb_id.nn.nn.nn".            |
    | `static int`      | `DEFAULT_BATCH_INTERVAL`<br>XStreamOut default acknowledge interval value for batch processing                            |
    | `static int`      | `DEFAULT_IDLE_TIMEOUT`<br>XStreamOut default timeout value for idle processing                                            |
    | `static int`      | `DEFAULT_MODE`<br>XStreamOut default mode                                                                                 |
    | `static int`      | `EXECUTING`<br>XStreamOut batch processing status EXECUTING, which indicates the the batch is in progress                 |
    | `static int`      | `FINISHED`<br>XStreamOut batch processing status FINISHED, which is the default status                                    |
    | `static int`      | `NEW_COLUMN_ONLY_MODE`<br>This column list mode allows users to receive LCRs with only new columns in the new value list. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                         |
    |-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static XStreamOut`                       | `attach``(oracle.jdbc.OracleConnection oconn, java.lang.String serverName, byte[] lastPosition, int mode)`<br>Attaches to outbound server.                                     |
    | `static XStreamOut`                       | `attach``(oracle.jdbc.OracleConnection oconn, java.lang.String serverName, byte[] lastPosition, int batchInterval, int idleTimeout, int mode)`<br>Attaches to outbound server. |
    | `void`                                    | `detach``(int mode)`<br>Detaches from outbound server.                                                                                                                         |
    | `int`                                     | `getBatchStatus``()`<br>Gets batch status.                                                                                                                                     |
    | `byte[]`                                  | `getFetchLowWatermark``()`<br>Gets fetch low watermark.                                                                                                                        |
    | [`ChunkColumnValue`](ChunkColumnValue.md) | `receiveChunk``(int mode)`<br>Receives chunk data in non-callback mode.                                                                                                        |
    | [`LCR`](LCR.md)                           | `receiveLCR``(int mode)`<br>Receives one LCR in non-callback mode.                                                                                                             |
    | `void`                                    | `receiveLCRCallback``(`[`XStreamLCRCallbackHandler`](XStreamLCRCallbackHandler.md)` handler, int mode)`<br>Receives a stream of LCRs in callback mode.                         |
    | `void`                                    | `setProcessedLowWatermark``(byte[] processedLowWatermark, byte[] oldestPosition, int mode)`<br>Sets processed low watermark.                                                   |
    | `void`                                    | `setProcessedLowWatermark``(byte[] processedLowWatermark, int mode)`<br>Sets processed low watermark.                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_MODE

          public static final int DEFAULT_MODE

      XStreamOut default mode
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NEW_COLUMN_ONLY_MODE

          public static final int NEW_COLUMN_ONLY_MODE

      This column list mode allows users to receive LCRs with only new columns in the new value list.
      By default XStreamOut returns the union of new columns and old columns that are not present in the new column list. This mode is valid for receiveLCR and receiveLCRCallback APIs.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEFAULT_BATCH_INTERVAL

          public static final int DEFAULT_BATCH_INTERVAL

      XStreamOut default acknowledge interval value for batch processing
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEFAULT_IDLE_TIMEOUT

          public static final int DEFAULT_IDLE_TIMEOUT

      XStreamOut default timeout value for idle processing
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FINISHED

          public static final int FINISHED

      XStreamOut batch processing status FINISHED, which is the default status
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EXECUTING

          public static final int EXECUTING

      XStreamOut batch processing status EXECUTING, which indicates the the batch is in progress
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTACH_APP_CONTAINER_MODE

          public static final int ATTACH_APP_CONTAINER_MODE

      This attach mode captures application container statements.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTACH_EXTENDED_ID_MODE

          public static final int ATTACH_EXTENDED_ID_MODE

      This attach mode returns transaction ID using extended format, "pdb_id.nn.nn.nn".
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### attach

          public static XStreamOut attach(oracle.jdbc.OracleConnection oconn,
                                          java.lang.String serverName,
                                          byte[] lastPosition,
                                          int mode)
                                   throws StreamsException

      Attaches to outbound server.
      This API attaches the client to the specified XStream outbound server. This API is also the factory method that returns an XStreamOut instance once it is attached to a valid XStream outbound server.
      Parameters:
      `oconn` - Oracle database connection.
      Note that the connection must be made using Oracle OCI (thick) driver.

      `serverName` - Name of the XStream outbound server.

      `lastPosition` - Position that establishes the starting point of the stream. An exception is thrown if the specified position is non-NULL and less than the outbound server's processed low watermark. Otherwise, LCRs with positions greater than the specified position are sent to the client.

      `mode` - The mode of XStream outbound server (for future extension). Valid modes are
      XStreamOut.ATTACH_APP_CONTAINER_MODE and
      XStreamOut.ATTACH_EXTENDED_ID_MODE. These modes can be added
      together.

      Returns:
      an XStreamOut instance.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during attach.

    <!-- -->

    - #### attach

          public static XStreamOut attach(oracle.jdbc.OracleConnection oconn,
                                          java.lang.String serverName,
                                          byte[] lastPosition,
                                          int batchInterval,
                                          int idleTimeout,
                                          int mode)
                                   throws StreamsException

      Attaches to outbound server.
      This API is the same as the other attach API except that is includes the batchInterval and idleTimeout parameters.
      Parameters:
      `oconn` - Oracle database connection.
      Note that the connection must be made using Oracle OCI (thick) driver.

      `serverName` - name of the XStream outbound server.

      `lastPosition` - Position that establishes the starting point of the stream. An exception is thrown if the specified position is non-NULL and less than the outbound server's processed low watermark. Otherwise, LCRs with positions greater than the specified position are sent to the client.

      `batchInterval` - XStreamOut batch processing interval.

      `idleTimeout` - XStreamOut idle timeout value.

      `mode` - The mode of XStream outbound server (for future extension). Use XStreamOut.DEFAULT_MODE for now.

      Returns:
      an XStreamOut instance.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during attach.

    <!-- -->

    - #### detach

          public void detach(int mode)
                      throws StreamsException

      Detaches from outbound server.
      This API detaches the client from the XStream outbound server.
      Parameters:
      `mode` - The mode of XStream outbound server (for future extension). Use XStreamOut.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during detach.

    <!-- -->

    - #### receiveLCRCallback

          public void receiveLCRCallback(XStreamLCRCallbackHandler handler,
                                         int mode)
                                  throws StreamsException

      Receives a stream of LCRs in callback mode.

      This API starts LCR streaming from the specified XStream outbound server. You must specify an LCR callback handler that processes each LCR. See more details about LCR callback handlers in XStreamLCRCallbackHandler. For each LCR received, the callback method processLCR() in the given XStreamLCRCallbackHandler is invoked. If chunk data exists in the LCRs, the callback method processChunk() in the given XStreamLCRCallbackHandler is invoked.

      To reduce network roundtrip overhead, for each ReceiveLCRCallback call, XStream also starts a batch process to fill the network buffer with LCRs. The batch process is stopped at a transaction boundary after 30 seconds or after one second if the system is idle. ReceiveLCRCallback does not return until one batch process ends.

      To receive LCRs with only new columns in the new value list, COLUMN_NEW_ONLY_MODE can be set in the mode flag,
             int mode = XStreamOut.DEFAULT_MODE | XStreamOut.COLUMN_NEW_ONLY_MODE;


      By default XStreamOut returns the union of new columns and old columns that are not present in the new column list.
      Parameters:
      `handler` - The XStreamLCRCallbackHandler for handling the LCRs.

      `mode` - A bit flag indicates the mode of XStream outbound server. There are two supported modes currently, DEFAULT_MODE and COLUMN_NEW_ONLY_MODE

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs during the entire batch.

      See Also:
      [`XStreamLCRCallbackHandler`](XStreamLCRCallbackHandler.md)

    <!-- -->

    - #### receiveLCR

          public LCR receiveLCR(int mode)
                         throws StreamsException

      Receives one LCR in non-callback mode.

      This method receives one LCR in the stream from the connected outbound server. To avoid network roundtrip for every ReceiveLCR call, XStream still uses batch processing to fill up the network buffer with LCRs. The batch is stopped at a transaction boundary after 30 seconds or after one second if the system is idle.

      You should use getBatchStatus API after receiveLCR call to check the status of batch processing.
      To receive LCRs with only new columns in the new value list, COLUMN_NEW_ONLY_MODE can be set in the mode flag,
             int mode = XStreamOut.DEFAULT_MODE | XStreamOut.COLUMN_NEW_ONLY_MODE;


      By default XStreamOut returns the union of new columns and old columns that are not present in the new column list.
      Parameters:
      `mode` - A bit flag indicates the mode of XStream outbound server . There are two supported modes currently, DEFAULT_MODE and COLUMN_NEW_ONLY_MODE

      Returns:
      An LCR object.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs while receiving an LCR

    <!-- -->

    - #### receiveChunk

          public ChunkColumnValue receiveChunk(int mode)
                                        throws StreamsException

      Receives chunk data in non-callback mode.
      This API retrieves streaming LOB, LONG, or XMLTYPE chunk data. Call this method after the receiveLCR() call when the received LCR contains chunk data. All the chunks from one LOB column are returned entirely before switching to the next LOB column.
      There is no fixed ordering when LOB columns are returned. You must check the column name to determine the column to which the chunk belongs. Use the the isLastChunk() method in ChunkColumnValue to determine when the last chunk of a LOB column is returned.
      Use the isEndOfRow() method in ChunkColumnValue to determine if the last chunk of entire row change has been returned.
      Parameters:
      `mode` - The mode of XStream outbound server (for future extension). Use XStreamOut.DEFAULT_MODE for now.

      Returns:
      A ChunkColumnValue object contains the chunked column data.

      Throws:
      [`StreamsException`](StreamsException.md) - If error occurs while receiving chunk data or constructing a ChunkColumnValue object.

    <!-- -->

    - #### getBatchStatus

          public int getBatchStatus()

      Gets batch status.
      This method is used to get the status of XStreamOut batch processing in non-callback mode. The return value can be either EXECUTING or FINISHED. See receiveLCR and receiveLCRCallback for more information about batch process in XStreamOut.
      When the status is EXECUTING, the current connection associated with XStreamOut is in use for batch receiving the LCRs from outbound server. Therefore, this connection cannot be used for other JDBC calls. When the status is FINISHED, the connection is available for use.
      The batch status is updated whenever the receiveLCR() method is invoked.
      Returns:
      The XStreamOut batch processing status

    <!-- -->

    - #### getFetchLowWatermark

          public byte[] getFetchLowWatermark()

      Gets fetch low watermark.
      This API gets the outbound server's FetchLowWatermark. The FetchLowWatermark denotes that the outbound server has processed all LCRs with positions lower than or equal to this value. This method can be used to increase the position maintained on the client when the system is idle. When the system is actively streaming LCRs, you can maintain the low watermark using received LCRs.
      Returns:
      The outbound server's FetchLowWatermark

    <!-- -->

    - #### setProcessedLowWatermark

          public void setProcessedLowWatermark(byte[] processedLowWatermark,
                                               int mode)
                                        throws StreamsException

      Sets processed low watermark.
      The ProcessedLowWatermark denotes that all LCRs at or below this watermark have been processed by the client. This ProcessedLowWatermark is sent to the outbound server periodically so that archived redo logs containing already processed transactions can be purged. You can call this method anytime between attach and detach calls.
      Parameters:
      `processedLowWatermark` - The client's processed low watermark.

      `mode` - The mode of XStream outbound server (for future extension). Use XStreamOut.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs while setting the low watermark.

    <!-- -->

    - #### setProcessedLowWatermark

          public void setProcessedLowWatermark(byte[] processedLowWatermark,
                                               byte[] oldestPosition,
                                               int mode)
                                        throws StreamsException

      Sets processed low watermark.
      The ProcessedLowWatermark denotes that all LCRs at or below this watermark have been processed by the client. This ProcessedLowWatermark is sent to the outbound server periodically so that archived redo logs containing already processed transactions can be purged. You can call this method anytime between attach and detach calls.
      Parameters:
      `processedLowWatermark` - The client's processed low watermark.

      `oldestPosition` - The client's oldest position.

      `mode` - The mode of XStream outbound server (for future extension). Use XStreamOut.DEFAULT_MODE for now.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs while setting the low watermark.

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

- [Prev Class](XStreamLCRCallbackHandler.md)
- [Next Class](XStreamUtility.md)

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
