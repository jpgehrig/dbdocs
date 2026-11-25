The screenshot shows the Show SQL page for a selected recommendation. The heading of the page is Show SQL. On the top, on the right-hand side of the page, is a Done button. The SQL statement displayed is:

    Rem SQL Access Advisor: Version 12.1.0.0.2 – Production
    Rem
    Rem Username:  DBA1
    Rem Task: SQLACCESS8895797
    Rem Execution date:
    Rem

    ALTER MATERIALIZED VIEW LOG FORCE ON
    "SH"."SALES"
    ADD ROWID, SEQUENCE("PROD_ID", "QUANTITY_SOLD","AMOUNT_SOLD)
    INCLUDING NEW VALUES;

    CREATE MATERIALIZED VIEW "DBA1"."MV$$_01680000"
    REFRESH FAST WITH ROWID
    ENABLE QUERY REWRITE
    AS SELECT SH.PRODUCTS.PROD_NAME C1, SH.SALES.AMOUNT_SOLD C2,
    SUM("SH"."SALES"."QUANTITY_SOLD")
    M1, COUNT("SH"."SALES"."QUANTITY_SOLD" M2, COUNT(*) M3 FROM SH.SALES,
    SH.PRODUCTS WHERE SH.SALES.PROD_ID = SH.PRODUCTS.PROD_ID AND
    (SH.SALES.AMOUNT_SOLD > 20000) AND
    (SH.PRODUCTS.PROD_NAME = 'Linen Big Shirt')
    GROUP BY SH.PRODUCTS.PROD_NAME, SH.SALES.AMOUNT_SOLD;

    BEGIN
    dbms_stats.gather_table_stats('"DBA1"', '"MV$$_01680000"', NULL, dbms_stats.auto_sample_size
    END;
    /

    CREATE BITMAP INDEX "SH"."SALES_IDX$$_01680000"
    ON "SH"."SALES"
    ("QUANTITY_SOLD")
    COMPUTE STATISTICS
    LOCAL;

End of description.
