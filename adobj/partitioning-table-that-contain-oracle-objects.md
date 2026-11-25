Partitioning addresses the key problem of supporting very large tables and indexes by allowing you to decompose them into smaller and more manageable pieces called partitions.

Oracle extends partitioning capabilities by letting you partition tables that contain objects, `REF`s, varrays, and nested tables. Varrays stored in `LOB`s are equipartitioned in a way similar to `LOB`s. Nested table storage tables will be equipartitioned with the base table. .

**See Also:**

For further information on equipartitioning

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-storage-with-applications.md)

- [Oracle Database VLDB and Partitioning Guide](../vldbg/partition-create-tables-indexes.md)

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-object-relational-storage.md)

Example 5-42 partitions the purchase order table along zip codes (`ToZip`), which is an attribute of the `ShipToAddr` embedded column object. The `LineItemList_nt` nested table illustrates storage for the partitioned nested table.

Example 5-42 Partitioning a Nested Table That Contains Objects

    CREATE TYPE StockItem_objtyp AS OBJECT (
          StockNo NUMBER,
          Price NUMBER,
          TaxRate NUMBER);
    /

    CREATE TYPE LineItem_objtyp AS OBJECT (
          LineItemNo NUMBER,
          Stock_ref REF StockItem_objtyp,
          Quantity NUMBER,
          Discount NUMBER);
    /

    CREATE TYPE Address_objtyp AS OBJECT (
          Street VARCHAR2(200),
          City VARCHAR2(200),
          State CHAR(2),
          Zip VARCHAR2(20))
    /

    CREATE TYPE LineItemList_nt as table of LineItem_objtyp;
    /

    CREATE TYPE PurchaseOrder_ntyp AS OBJECT (
          PONo                NUMBER,
          OrderDate           DATE,
          ShipDate            DATE,
          OrderForm           BLOB,
          LineItemList        LineItemList_nt,
          ShipToAddr          Address_objtyp,

       MAP MEMBER FUNCTION
          ret_value RETURN NUMBER,
       MEMBER FUNCTION
          total_value RETURN NUMBER);
    /

    CREATE TABLE PurchaseOrders_ntab of PurchaseOrder_ntyp
    LOB (OrderForm) store as (nocache logging)
    NESTED TABLE LineItemList STORE AS LineItemList_ntab
    PARTITION BY RANGE (ShipToAddr.zip)
       (PARTITION PurOrderZone1_part VALUES LESS THAN ('59999')
           LOB (OrderForm) store as (
           storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100))
           NESTED TABLE LineItemList store as LineitemZone1_part(
           storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100)),
       PARTITION PurOrderZone2_part  VALUES LESS THAN ('79999')
           LOB (OrderForm) store as (
           storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100))
          NESTED TABLE LineItemList store as LineitemZone2_part(
           storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100)),
       PARTITION PurOrderZone3_part  VALUES LESS THAN ('99999')
           LOB (OrderForm) store as (
           storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100))
           NESTED TABLE LineItemList store as LineitemZone3_part(
       storage (INITIAL 10 MINEXTENTS 10 MAXEXTENTS 100)) )
    /
