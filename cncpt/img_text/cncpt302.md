# Description of the illustration cncpt302.eps

This graphic shows two table partitions: SYS_P33 and SYS_P34. The partitions contain the following rows:

     Table Partition SYS_P33
      PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
           40     100530 30-NOV-98          9         33             1       44.99
          118        133 06-JUN-01          2        999             1       17.12
           36       4523 27-JAN-99          3        999             1       53.89
           30        170 23-FEB-01          2        999             1         8.8
           35       2606 17-FEB-00          3        999             1       54.94

    Table Partition SYS_P34
    PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          116      11393 05-JUN-99          2        999             1       12.18
          133       9450 01-DEC-00          2        999             1       31.28
          125       9417 04-FEB-98          3        999             1       16.86
           24      11899 26-JUN-99          4        999             1       43.04
           45       9491 28-AUG-98          4        350             1       47.45

Above the table partitions are two index partitions that point down to the table partitions. Index partition SYS_P38 indexes rows in table partition SYS_P33, whereas index partition SYS_P39 indexes rows in table partition SYS_P34. The two index partitions are inside a box labeled hash_sales_idx.
