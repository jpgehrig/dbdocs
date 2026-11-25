LOB storage considerations for JSON data are described, including considerations when you use a client to retrieve JSON data as a LOB instance.

### General Considerations

If you use LOB storage for JSON data, Oracle recommends that you use `BLOB`, not `CLOB` storage.

This is particularly relevant if the database character set is the Oracle-recommended value of AL32UTF8. In AL32UTF8 databases `CLOB` instances are stored using the UCS2 character set, which means that each character requires two bytes. This doubles the storage needed for a document if most of its content consists of characters that are represented using a single byte in character set AL32UTF8.

Even in cases where the database character set is not AL32UTF8, choosing `BLOB` over `CLOB` storage has the advantage that it avoids the need for character-set conversion when storing the JSON document  (see [Character Sets and Character Encoding for JSON Data](json-character-sets-and-encoding.md)).

When using large objects (LOBs), Oracle recommends that you do the following:

- Use the clause `LOB (``COLUMN_NAME``) STORE AS (CACHE)` in your `CREATE TABLE` statement, to ensure that read operations on the JSON documents are optimized using the database buffer cache.

- Use SecureFiles LOBs.

SQL/JSON functions and conditions work with JSON data without any special considerations, whether the data is stored as `BLOB` or `CLOB`. From an application-development perspective, the API calls for working with `BLOB` content are nearly identical to those for working with `CLOB` content.

A downside of choosing `BLOB` storage over `CLOB` (for JSON or any other kind of data) is that it is sometimes more difficult to work with `BLOB` content using command-line tools such as SQL\*Plus. For instance:

- When selecting data from a `BLOB` column, if you want to view it as printable text then you must use SQL function `to_clob`.

- When performing insert or update operations on a `BLOB` column, you must explicitly convert character strings to `BLOB` format using SQL function `rawtohex`.<sup>Foot 1</sup>

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/TO_CLOB-bfile-blob.md) for information about SQL function `to_clob`

- [Oracle Database SQL Language Reference](../sqlrf/RAWTOHEX.md) for information about SQL function `rawtohex`

### Considerations When Using a Client To Retrieve JSON Data As a LOB Instance

If you use a client, such as Oracle Call Interface (OCI) or Java Database Connectivity (JDBC), to retrieve JSON data from the database then the following considerations apply.

There are three main ways for a client to retrieve a LOB that contains JSON data from the database:

- Use the LOB locator interface, with a LOB locator returned by a SQL/JSON operation<sup>Foot 2</sup>

- Use the LOB data interface

- Read the LOB content directly

In general, Oracle recommends that you use the LOB data interface or you read the content directly.

If you use the LOB locator interface:

- Be aware that the LOB is temporary and read-only.

- Be sure to read the content of the current LOB completely before fetching the next row. The next row fetch can render this content unreadable.

  Save this current-LOB content, in memory or to disk, if your client continues to need it after the next row fetch.

- Free the fetched LOB locator after each row is read. Otherwise, performance can be reduced, and memory can leak.

Consider also these optimizations if you use the LOB locator interface:

- Set the LOB prefetch size to a large value, such as 256 KB, to minimize the number of round trips needed for fetching.

- Set the batch fetch size to a large value, such as 1000 rows.

Example 7-1 and Example 7-2 show how to use the LOB locator interface with JDBC.

Example 7-3 and Example 7-4 show how to use the LOB locator interface with ODP.NET.

Each of these examples fetches a LOB row at a time. To ensure that the current LOB content remains readable after the next row fetch, it also reads the full content.

If you use the LOB data interface:

- In OCI, use data types `SQLT_BIN` and `SQLT_CHR`, for `BLOB` and `CLOB` data, respectively.

- In JDBC, use data types `LONGVARBINARY` and `LONGVARCHAR`, for `BLOB` and `CLOB` data, respectively.

Example 7-5 and Example 7-6 show how to use the LOB data interface with JDBC.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/data-interface-for-persistent-LOBs.md)

Example 7-7 and Example 7-8 show how to read the full LOB content directly with JDBC.

Example 7-9 and Example 7-10 show how to read the full LOB content directly with ODP.NET.

Example 7-1 JDBC Client: Using the LOB Locator Interface To Retrieve JSON BLOB Data

    static void test_JSON_SERIALIZE_BLOB() throws Exception {
      try(
          OracleConnection conn = getConnection();
          OracleStatement stmt = (OracleStatement)conn.createStatement();
          ) {
        stmt.setFetchSize(1000); // Set batch fetch size to 1000 rows.

        // Set LOB prefetch size to be 256 KB.
        ((OraclePreparedStatement)stmt).setLobPrefetchSize(256000);

        // Query the JSON data in column jblob of table myTab1,
        // serializing the returned JSON data as a textual BLOB instance.
        String query =
          "SELECT json_serialize(jblob RETURNING BLOB) FROM myTab1";
        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          Blob blob = rs.getBlob(1);

          // Do something with the BLOB instance for the row...

          // Read full content, to be able to access past current row.
          String val =
            new String(blob.getBytes(1,
                                     (int)blob.length()),
                                     StandardCharsets.UTF_8);

          // Free the LOB at the end of each iteration.
          blob.free();
        }
        rs.close();
        stmt.close();
      }
    }

Example 7-2 JDBC Client: Using the LOB Locator Interface To Retrieve JSON CLOB Data

    static void test_JSON_SERIALIZE_CLOB() throws Exception {
      try(
          OracleConnection conn = getConnection();
          OracleStatement stmt = (OracleStatement)conn.createStatement();
          ){
        stmt.setFetchSize(1000); // Set batch fetch size to 1000 rows.

        // Set LOB prefetch size to be 256 KB.
        ((OraclePreparedStatement)stmt).setLobPrefetchSize(256000);

        // Query the JSON data in column jclob of table myTab2,
        // serializing the returned JSON data as a textual CLOB instance.
        String query =
          "SELECT json_serialize(jclob RETURNING CLOB) FROM myTab2";

        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          Clob clob = rs.getClob(1);

          // Do something with the CLOB instance for the row...

          // Read full content, to be able to access past current row.
          String val = clob.getSubString(1, (int)clob.length());

          // Free the LOB at the end of each iteration.
          blob.free();
        }
        rs.close();
        stmt.close();
      }
    }

Example 7-3 ODP.NET Client: Using the LOB Locator Interface To Retrieve JSON BLOB Data

    static void test_JSON_SERIALIZE_BLOB()
    {
      try
      {
        using (OracleConnection conn =
          new OracleConnection(
            "user id=<schema>;password=<password>;data source=oracle"))
        {
          conn.Open();
          OracleCommand cmd = conn.CreateCommand();

          // Set LOB prefetch size to be 256 KB.
          cmd.InitialLOBFetchSize = 256000;

          // Query the JSON datatype data in column jblob of table myTab1,
          // serializing the returned JSON data as a textual BLOB instance.
          cmd.CommandText =
            "SELECT json_serialize(jblob RETURNING BLOB) FROM myTab1";

          OracleDataReader rs = cmd.ExecuteReader();

          // Iterate over the returned rows.
          while (rs.Read())
          {
            OracleBlob blob = rs.GetOracleBlob(0);

            // Do something with the BLOB instance for the row...

            // Read full content, to be able to access past current row.
            String val = Encoding.UTF8.GetString(blob.Value);

            blob.Close();
            blob.Dispose();
          }
          rs.Close();
        }
      }
      catch (Exception e)
      {
        throw e;
      }
    }

Example 7-4 ODP.NET Client: Using the LOB Locator Interface To Retrieve JSON CLOB Data

    static void test_JSON_SERIALIZE_CLOB()
    {
      try
      {
        using (OracleConnection conn =
          new OracleConnection(
            "user id=<schema>;password=<password>;data source=oracle"))
        {
          conn.Open();
          OracleCommand cmd = conn.CreateCommand();

          // Set LOB prefetch size to be 256 KB.
          cmd.InitialLOBFetchSize = 256000;

          // Query the JSON datatype data in column jclob of table myTab2,
          // serializing the returned JSON data as a textual CLOB instance.
          cmd.CommandText =
            "SELECT json_serialize(jclob RETURNING CLOB) FROM myTab2";

          OracleDataReader rs = cmd.ExecuteReader();

          // Iterate over the returned rows.
          while (rs.Read())
          {
            OracleClob clob = rs.GetOracleClob(0);

            // Do something with the CLOB instance for the row...

            // Read full content, to be able to access past current row.
            String val = clob.Value;

            clob.Close();
            clob.Dispose();
          }
          rs.Close();
        }
      }
      catch (Exception e)
      {
        throw e;
      }
    }

Example 7-5 JDBC Client: Using the LOB Data Interface To Retrieve JSON BLOB Data

    static void test_JSON_SERIALIZE_LONGVARBINARY() throws Exception {
      try(
          OracleConnection conn = getConnection();
          OracleStatement  stmt = (OracleStatement)conn.createStatement();
          ){

        // Query the JSON data in column jblob of table myTab1,
        // serializing the returned JSON data as a textual BLOB instance.
        String query =
          "SELECT json_serialize(jblob RETURNING BLOB) FROM myTab1";
        stmt.defineColumnType(1, OracleTypes.LONGVARBINARY, 1);
        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          BufferedReader br =
            new BufferedReader(
                  new InputStreamReader(rs.getBinaryStream( 1 )));
          int size = 0;
          int data = 0;
          data = br.read();
          while( -1 != data ){
              System.out.print( (char)(data) );
            data = br.read();
            size++;
          }
          br.close();
        }
        rs.close();
        stmt.close();
      }
    }

Example 7-6 JDBC Client: Using the LOB Data Interface To Retrieve JSON CLOB Data

    static void test_JSON_SERIALIZE_LONGVARCHAR() throws Exception {
      try(
          OracleConnection conn = getConnection();
          OracleStatement  stmt = (OracleStatement)conn.createStatement();
          ){

        // Query the JSON data in column jclob of table myTab2,
        // serializing the returned JSON data as a textual CLOB instance.
        String query =
          "SELECT json_serialize(jclob RETURNING CLOB) FROM myTab2";
        stmt.defineColumnType(1, OracleTypes.LONGVARCHAR, 1);
        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          Reader reader = rs.getCharacterStream(1);
          int size = 0;
          int data = 0;
          data = reader.read();
          while( -1 != data ){
            System.out.print( (char)(data) );
            data = reader.read();
            size++;
          }
          reader.close();
        }
        rs.close();
        stmt.close();
      }
    }

Example 7-7 JDBC Client: Reading Full BLOB Content Directly with getBytes

    static void test_JSON_SERIALIZE_BLOB_2() throws Exception {
      try(
          OracleConnection con = getConnection();
          OracleStatement stmt = (OracleStatement)con.createStatement();
          ){
        stmt.setFetchSize(1000); // Set batch fetch size to 1000 rows.

        // set LOB prefetch size to be 256 KB.
        ((OracleStatement)stmt).setLobPrefetchSize(256000);

        // Query the JSON data in column jblob of table myTab1,
        // serializing the returned JSON data as a textual BLOB instance.
        String query =
          "SELECT json_serialize(jblob RETURNING BLOB) FROM myTab1";
        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          String val = new String(rs.getBytes(1), StandardCharsets.UTF_8);
        }
        rs.close();
        stmt.close();
        }
      }

Example 7-8 JDBC Client:Reading Full CLOB Content Directly with getString

    static void test_JSON_SERIALIZE_CLOB_2() throws Exception {
      try(
          OracleConnection conn = getConnection();
          OracleStatement  stmt = (OracleStatement)conn.createStatement();
          ){
        stmt.setFetchSize(1000); // Set batch fetch size to 1000 rows.

        // Set LOB prefetch size to be 256 KB.
        ((OracleStatement)stmt).setLobPrefetchSize(256000);

        // Query the JSON data in column jclob of table myTab2,
        // serializing the returned JSON data as a textual CLOB instance.
        String query =
          "SELECT json_serialize(jclob RETURNING CLOB) FROM myTab2";
        ResultSet rs = stmt.executeQuery(query);

        while(rs.next()) { // Iterate over the returned rows.
          String val = rs.getString(1);
        }
        rs.close();
        stmt.close();
        }
      }

Example 7-9 ODP.NET Client: Reading Full BLOB Content Directly with getBytes

    static void test_JSON_SERIALIZE_BLOB_2()
    {
      try
      {
        using (OracleConnection conn = new OracleConnection("user id=scott;password=tiger;data source=oracle"))
        {
          conn.Open();
          OracleCommand cmd = conn.CreateCommand();

          // Set LOB prefetch size to be 256 KB.
          cmd.InitialLOBFetchSize = 256000;

          // Query the JSON datatype data in column blob of table myTab1,
          // serializing the returned JSON data as a textual BLOB instance.

          cmd.CommandText =
            "SELECT json_serialize(blob RETURNING BLOB) FROM myTab1";
          OracleDataReader rs = cmd.ExecuteReader();

          // Iterate over the returned rows.
          while (rs.Read())
          {
            long len = rs.GetBytes(0, 0, null, 0, 0); /* Get LOB length */
            byte[] obuf = new byte[len];
            rs.GetBytes(0, 0, obuf, 0, (int)len);
            String val = Encoding.UTF8.GetString(obuf);
          }
          rs.Close();
        }
      }
      catch (Exception e)
      {
        throw e;
      }
    }

Example 7-10 ODP.NET Client: Reading Full CLOB Content Directly with getString

    static void test_JSON_SERIALIZE_CLOB_2()
    {
      try
      {
        using (OracleConnection conn =
          new OracleConnection(
            "user id=<schema>;password=<password>;data source=oracle"))
        {
          conn.Open();
          OracleCommand cmd = conn.CreateCommand();

          // Set LOB prefetch size to be 256 KB.
          cmd.InitialLOBFetchSize = 256000;

          // Query the JSON datatype data in column clob of table myTab2,
          // serializing the returned JSON data as a textual CLOB instance.

          cmd.CommandText = "SELECT json_serialize(clob RETURNING CLOB) FROM myTab2";

          OracleDataReader rs = cmd.ExecuteReader();

          // Iterate over the returned rows.
          while (rs.Read())
          {
            String val = rs.GetString(0);
          }
          rs.Close();
        }
      }
      catch (Exception e)
      {
        throw e;
      }
    }

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1: The return value of SQL function `rawtohex` is limited to 32767 bytes. The value is truncated to remove any converted data beyond this length.
Footnote 2: The SQL/JSON functions that can return a LOB locator are these, when used with `RETURNING CLOB` or `RETURNING BLOB`: `json_serialize`, `json_value`, `json_query`, `json_table`, `json_array`,` json_object`, `json_arrayagg`, and` json_objectagg`.
