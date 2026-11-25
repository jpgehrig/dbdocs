You can manually implement an Information Lifecycle Management (ILM) system using partitioning.

Example 5-12 illustrates how to manually create storage tiers and partition a table across those storage tiers and then setup a virtual private database (VPD) policy on that database to restrict access to the online archive tier data.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about the `CREATE` `TABLE` SQL statement

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RLS.md) for information about the `DBMS_RLS` package

Example 5-12 Manually implementing an ILM system

    REM Setup the tablespaces for the data

    REM These tablespaces would be placed on a High Performance Tier
    CREATE SMALLFILE TABLESPACE q1_orders DATAFILE 'q1_orders'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE q2_orders DATAFILE 'q2_orders'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE q3_orders DATAFILE 'q3_orders'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE q4_orders DATAFILE 'q4_orders'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM These tablespaces would be placed on a Low Cost Tier
    CREATE SMALLFILE TABLESPACE "2006_ORDERS" DATAFILE '2006_orders'
      SIZE 5M AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE "2005_ORDERS"  DATAFILE '2005_orders'
      SIZE 5M AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM These tablespaces would be placed on the Online Archive Tier
    CREATE SMALLFILE TABLESPACE "2004_ORDERS" DATAFILE '2004_orders'
      SIZE 5M AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE old_orders DATAFILE 'old_orders'
      SIZE 15M AUTOEXTEND ON NEXT 10M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM Now create the Partitioned Table
    CREATE TABLE allorders (
        prod_id       NUMBER       NOT NULL,
        cust_id       NUMBER       NOT NULL,
        time_id       DATE         NOT NULL,
        channel_id    NUMBER       NOT NULL,
        promo_id      NUMBER       NOT NULL,
        quantity_sold NUMBER(10,2) NOT NULL,
        amount_sold   NUMBER(10,2) NOT NULL)
     --
     -- table wide physical specs
     --
      PCTFREE 5 NOLOGGING
     --
     -- partitions
     --
     PARTITION BY RANGE (time_id)
      ( partition allorders_pre_2004 VALUES LESS THAN
         (TO_DATE('2004-01-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE old_orders,
        partition allorders_2004 VALUES LESS THAN
         (TO_DATE('2005-01-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE "2004_ORDERS",
        partition allorders_2005 VALUES LESS THAN
         (TO_DATE('2006-01-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE "2005_ORDERS",
        partition allorders_2006 VALUES LESS THAN
         (TO_DATE('2007-01-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE "2006_ORDERS",
        partition allorders_q1_2007 VALUES LESS THAN
         (TO_DATE('2007-04-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE q1_orders,
        partition allorders_q2_2007 VALUES LESS THAN
         (TO_DATE('2007-07-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE q2_orders,
        partition allorders_q3_2007 VALUES LESS THAN
         (TO_DATE('2007-10-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE q3_orders,
        partition allorders_q4_2007 VALUES LESS THAN
         (TO_DATE('2008-01-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE q4_orders);

    ALTER TABLE allorders ENABLE ROW MOVEMENT;

    REM Here is another example using INTERVAL partitioning

    REM These tablespaces would be placed on a High Performance Tier
    CREATE SMALLFILE TABLESPACE cc_this_month DATAFILE 'cc_this_month'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    CREATE SMALLFILE TABLESPACE cc_prev_month DATAFILE 'cc_prev_month'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM These tablespaces would be placed on a Low Cost Tier
    CREATE SMALLFILE TABLESPACE cc_prev_12mth DATAFILE 'cc_prev_12'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM These tablespaces would be placed on the Online Archive Tier
    CREATE SMALLFILE TABLESPACE cc_old_tran DATAFILE 'cc_old_tran'
      SIZE 2M AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED LOGGING
      EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO ;

    REM Credit Card Transactions where new partitions
    REM are automatically placed on the high performance tier
    CREATE TABLE cc_tran (
        cc_no       VARCHAR2(16) NOT NULL,
        tran_dt     DATE         NOT NULL,
        entry_dt    DATE         NOT NULL,
        ref_no      NUMBER       NOT NULL,
        description VARCHAR2(30) NOT NULL,
        tran_amt    NUMBER(10,2) NOT NULL)
     --
     -- table wide physical specs
     --
     PCTFREE 5 NOLOGGING
     --
     -- partitions
     --
     PARTITION BY RANGE (tran_dt)
     INTERVAL (NUMTOYMINTERVAL(1,'month') ) STORE IN (cc_this_month )
      ( partition very_old_cc_trans VALUES LESS THAN
         (TO_DATE('1999-07-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE cc_old_tran ,
        partition old_cc_trans VALUES LESS THAN
         (TO_DATE('2006-07-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE cc_old_tran ,
        partition last_12_mths VALUES LESS THAN
         (TO_DATE('2007-06-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE cc_prev_12mth,
        partition recent_cc_trans VALUES LESS THAN
        (TO_DATE('2007-07-01 00:00:00'
                ,'SYYYY-MM-DD HH24:MI:SS'
                ,'NLS_CALENDAR=GREGORIAN'
                )) TABLESPACE cc_prev_month,
        partition new_cc_tran VALUES LESS THAN
         (TO_DATE('2007-08-01 00:00:00'
                 ,'SYYYY-MM-DD HH24:MI:SS'
                 ,'NLS_CALENDAR=GREGORIAN'
                 )) TABLESPACE cc_this_month);

    REM Create a Security Policy to allow user SH to see all credit card data,
    REM PM only sees this years data,
    REM and all other uses cannot see the credit card data

    CREATE OR REPLACE FUNCTION ilm_seehist
      (oowner IN VARCHAR2, ojname IN VARCHAR2)
       RETURN VARCHAR2 AS con VARCHAR2 (200);
    BEGIN
      IF SYS_CONTEXT('USERENV','CLIENT_INFO') = 'SH'
      THEN -- sees all data
        con:= '1=1';
      ELSIF SYS_CONTEXT('USERENV','CLIENT_INFO') = 'PM'
      THEN -- sees only data for 2007
        con := 'time_id > ''31-Dec-2006''';
      ELSE
        -- others nothing
        con:= '1=2';
      END IF;
      RETURN (con);
    END ilm_seehist;
    /
