After loading the Java classes, publish your Java stored procedures in the Oracle data dictionary. To do this, you must write call specifications that map Java method names, parameter types, and return types to their SQL counterparts.

The methods in the `POManager` Java class are logically related. You can group their call specifications in a PL/SQL package. To do this, first, create the package specification, as follows:

    CREATE OR REPLACE PACKAGE po_mgr AS
    PROCEDURE add_customer (cust_no NUMBER, cust_name VARCHAR2,
    street VARCHAR2, city VARCHAR2, state CHAR, zip_code VARCHAR2,
    phone_no VARCHAR2);
    PROCEDURE add_stock_item (stock_no NUMBER, description VARCHAR2,
    price NUMBER);
    PROCEDURE enter_order (order_no NUMBER, cust_no NUMBER,
    order_date VARCHAR2, ship_date VARCHAR2, to_street VARCHAR2,
    to_city VARCHAR2, to_state CHAR, to_zip_code VARCHAR2);
    PROCEDURE add_line_item (line_no NUMBER, order_no NUMBER,
    stock_no NUMBER, quantity NUMBER, discount NUMBER);
    PROCEDURE total_orders;
    PROCEDURE check_stock_item (stock_no NUMBER);
    PROCEDURE change_quantity (new_qty NUMBER, order_no NUMBER,
    stock_no NUMBER);
    PROCEDURE delete_order (order_no NUMBER);
    END po_mgr;

Then, create the package body by writing call specifications for the Java methods, as follows:

    CREATE OR REPLACE PACKAGE BODY po_mgr AS
    PROCEDURE add_customer (cust_no NUMBER, cust_name VARCHAR2,
    street VARCHAR2, city VARCHAR2, state CHAR, zip_code VARCHAR2,
    phone_no VARCHAR2) AS LANGUAGE JAVA
    NAME 'POManager.addCustomer(int, java.lang.String,
    java.lang.String, java.lang.String, java.lang.String,
    java.lang.String, java.lang.String)';

    PROCEDURE add_stock_item (stock_no NUMBER, description VARCHAR2,
    price NUMBER) AS LANGUAGE JAVA
    NAME 'POManager.addStockItem(int, java.lang.String, float)';

    PROCEDURE enter_order (order_no NUMBER, cust_no NUMBER,
    order_date VARCHAR2, ship_date VARCHAR2, to_street VARCHAR2,
    to_city VARCHAR2, to_state CHAR, to_zip_code VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'POManager.enterOrder(int, int, java.lang.String,
    java.lang.String, java.lang.String, java.lang.String,
    java.lang.String, java.lang.String)';

    PROCEDURE add_line_item (line_no NUMBER, order_no NUMBER,
    stock_no NUMBER, quantity NUMBER, discount NUMBER)
    AS LANGUAGE JAVA
    NAME 'POManager.addLineItem(int, int, int, int, float)';

    PROCEDURE total_orders
    AS LANGUAGE JAVA
    NAME 'POManager.totalOrders()';

    PROCEDURE check_stock_item (stock_no NUMBER)
    AS LANGUAGE JAVA
    NAME 'POManager.checkStockItem(int)';

    PROCEDURE change_quantity (new_qty NUMBER, order_no NUMBER,
    stock_no NUMBER) AS LANGUAGE JAVA
    NAME 'POManager.changeQuantity(int, int, int)';

    PROCEDURE delete_order (order_no NUMBER)
    AS LANGUAGE JAVA
    NAME 'POManager.deleteOrder(int)';
    END po_mgr;
