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

- [Prev Class](XStreamIn.md)
- [Next Class](XStreamOut.md)

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

## Interface XStreamLCRCallbackHandler

-

  ------------------------------------------------------------------------



      public interface XStreamLCRCallbackHandler

  The XStreamLCRCallbackHandler interface enables clients to receive LCRs and chunk data from an XStream outbound server or send LCRs and chunk data to an XStream inbound server using a callback mechanism. This interface is the callback interface for LCR handling in Oracle XStream.
  A Client Application needs to implement this interface for using XStream Inbound and/or Outbound, and process/create the LCR according to their requirements through callback mechanism.
  - The processLCR() interface is the callback method used for XStreamOut to deliver LCRs to a client application.
  - The processChunk() interface is the callback method used for XStreamOut to deliver chunk data to a client application.
  - The createLCR() interface is the callback method used for XStreamIn to retrieve LCRs from a client application.
  - The createChunk() interface is the callback method used for XStreamIn to retrieve chunk data from a client application.

  See Also:
  [`XStreamIn`](XStreamIn.md), [`XStreamOut`](XStreamOut.md), [`LCR`](LCR.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ChunkColumnValue`](ChunkColumnValue.md) | `createChunk``()`<br>The callback method for constructing chunk data that is sent to an XStream inbound server.                                                                                                           |
    | [`LCR`](LCR.md)                           | `createLCR``()`<br>The callback method for creating an LCR and sending it to an XStream inbound server.                                                                                                                   |
    | `void`                                    | `processChunk``(`[`ChunkColumnValue`](ChunkColumnValue.md)` chunk)`<br>The callback method for processing chunk data received from an XStream outbound server for an LCR received through the processLCR callback method. |
    | `void`                                    | `processLCR``(`[`LCR`](LCR.md)` lcr)`<br>The callback method for processing an LCR recevied from an XStream outbound server.                                                                                              |

<!-- -->

- - ### Method Detail

    - #### processLCR

          void processLCR(LCR lcr)
                   throws StreamsException

      The callback method for processing an LCR recevied from an XStream outbound server.
      You must implement the LCR handling logic in this method. If XStream Out is not used, you can provide an empty implementation of this method.

      To process an LCR with LOB columns, you must also use the processchunk API to retrieve the streaming chunk data.
      The following is an example of implementing this API:
      Note that the example is not a complete implementation and only illustrates how to process an LCR using the XStream APIs.

            public void processLCR(LCR lcr)
              throws StreamsException
            {
              // access LCR header info
              String cmdtype   = lcr.getCommandType();
              String srcDB     = lcr.getSourceDatabaseName();
              String objOwner  = lcr.getObjectOwner();
              String objName   = lcr.getObjectName();
              String txnId     = lcr.getTransactionId();
              DATE   srcTime   = lcr.getSourceTime();
              byte[] pos       = lcr.getPosition());
              ...

              // access scalar columns
              if (lcr instanceof RowLCR)
              {
                if ((lcr.getCommandType()).compareTo(RowLCR.INSERT) == 0)
                {
                  // access scalar columns in new column list
                  ColumnValue[] collist = ((RowLCR)lcr).getNewValues();
                  for (int i = 0; i < collist.length; i++)
                  {
                    String colName = collist[i].getColumnName();
                    Datum colData = collist[i].getColumnData();
                    if (colData instanceof NUMBER)
                    {
                      System.out.println(((NUMBER)coldata).intValue());
                    }
                    else if(colData instanceof CHAR)
                    {
                      System.out.println(((CHAR)colData).stringValue());
                      System.out.println(((CHAR)colData).oracleId());
                    }
                    ...
                  }

                  if (((RowLCR)lcr).hasChunkData())
                  {
                    // prepare to retrieve all LOB columns through
                    // processChunk() callback method.
                  }
                }
                ...
              }
              else
              {
                // handle DDL LCR.
              }
            }


      Parameters:
      `lcr` - the LCR received from an XStream outbound server.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when processing an LCR.

    <!-- -->

    - #### processChunk

          void processChunk(ChunkColumnValue chunk)
                     throws StreamsException

      The callback method for processing chunk data received from an XStream outbound server for an LCR received through the processLCR callback method.
      You must implement the chunk handling logic in this method. If XStream Out is not used, you can provide an empty implementation of this method.

      The following is an example of implementing this API:
      Note that the example is not a complete implementation and only illustrates how to process chunk data using the XStream APIs.

            public void processChunk(ChunkColumnValue chunk)
              throws StreamsException
            {
              // process the chunk data
              Datum coldata = chunk.getColumnData();
              String colname = chunk.getColumnName();
              ...

              if (chunk.isLastChunk())
                // do something for the column
              if (chunk.isEndOfRow())
                // do something for the entire row change, cleanup
            }


      Parameters:
      `chunk` - the chunk received from an XStream outbound server.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when processing chunk data.

    <!-- -->

    - #### createLCR

          LCR createLCR()
                 throws StreamsException

      The callback method for creating an LCR and sending it to an XStream inbound server.
      You must implement the LCR construction logic in this method. If XStreamIn is not used, you can provide an empty implementation of this method.

      This method is invoked by XStreamIn inside a sendLCRCallback call to retrieve LCRs. You can return a null LCR to stop the sendLCRCallback execution.

      To construct LCR with LOB columns, you can use the createChunk() callback method to send the streaming chunk data.

      You must construct the partial LCR with all scalar columns and set the ChunkDataFlag to true using setChunkDataFlag() method. When XStream gets the partially constructed LCR with this chunkDataFlag set to true, the createChunk callback method is invoked to get the chunk data.

      The following is an example of implementing this API:
      Note that the example is not a complete implementation and only illustrates how to construct an LCR using the XStream APIs.

            public LCR createLCR()
              throws StreamsException
            {
              // first construct the lcr with scalar columns
              DefaultRowLCR alcr = new DefaultRowLCR();

              alcr.setSourceDatabaseName("MY.TEST.DB");
              alcr.setSourceTime(getCurrentDate());
              alcr.setPosition(NUMBER.toBytes(1));
              alcr.setCommandType("INSERT");
              alcr.setObjectOwner("SCOTT");
              alcr.setObjectName("TEST_TABLE");
              alcr.setTransactionId("1.0.0");

              ColumnValue[] newValues = new DefaultColumnValue[4];
              try
              {
                CharacterSet mycharset =
                  CharacterSet.make(CharacterSet.AL16UTF16_CHARSET);
                newValues[0] = new DefaultColumnValue("ID",new NUMBER(1));
                newValues[1] = new DefaultColumnValue("CHAR_COLUMN",
                                                    new CHAR("chartest",mycharset));
                DefaultChunkColumnValue chunk1 =
                  new DefaultChunkColumnValue("LOB1_COLUMN",
                                              null, ChunkColumnValue.CLOB);
                chunk1.setEmptyChunk(true);
                newValues[2] = chunk1;
                DefaultChunkColumnValue chunk2 =
                  new DefaultChunkColumnValue("LOB2_COLUMN",
                                              null, ChunkColumnValue.BLOB);
                chunk2.setEmptyChunk(true);
                newValues[3]  = chunk2;
              }
              catch(Exception e)
              {
                System.out.println("fail to construct a lcr: "+e.getMessage());
                e.printStackTrace();
                throw new StreamsException("fail to create an LCR");
              }
              alcr.setNewValues(newValues);
              alcr.setChunkDataFlag(true);

              // return this lcr to an XStream inbound Server
              return alcr;
            }


      Returns:
      the LCR sent to an XStream inbound server.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when creating an LCR.

    <!-- -->

    - #### createChunk

          ChunkColumnValue createChunk()
                                throws StreamsException

      The callback method for constructing chunk data that is sent to an XStream inbound server.
      You must implement the Chunk construction logic in this method. If XStream Inbound is not used, you can provide an empty implementation of this method.

      The following is an example of implementing this API:
      Note that the example is not a complete implementation and only illustrates how to construct chunk data using the XStream APIs.

            public ChunkColumnValue createChunk()
              throws StreamsException
            {
              // construct the chunk data
              ChunkColumnValue chunk = new DefaultChunkColumnValue(...);
              ...

              if (last chunk in the column)
                chunk.setLastChunk(true)
              if (last chunk for the entire row)
                chunk.setEndOfRow(true);
              return chunk;
            }


      Returns:
      the Chunk sent to an XStream inbound server.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when creating chunk data.

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

- [Prev Class](XStreamIn.md)
- [Next Class](XStreamOut.md)

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
