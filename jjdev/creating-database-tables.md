After planning the database schema, create the database tables for the schema plan. Define the `Customers` table as follows:

    CREATE TABLE Customers (
    CustNo NUMBER(3) NOT NULL,
    CustName VARCHAR2(30) NOT NULL,
    Street VARCHAR2(20) NOT NULL,
    City VARCHAR2(20) NOT NULL,
    State CHAR(2) NOT NULL,
    Zip VARCHAR2(10) NOT NULL,
    Phone VARCHAR2(12),
    PRIMARY KEY (CustNo)
    );

The `Customers` table stores information about customers. Essential information is defined as `NOT NULL`. For example, every customer must have a shipping address. However, the `Customers` table does not manage the relationship between a customer and his or her purchase order. As a result, this relationship must be managed by the `Orders` table, which you can define as follows:

    CREATE TABLE Orders (
    PONo NUMBER(5),
    Custno NUMBER(3) REFERENCES Customers,
    OrderDate DATE,
    ShipDate DATE,
    ToStreet VARCHAR2(20),
    ToCity VARCHAR2(20),
    ToState CHAR(2),
    ToZip VARCHAR2(10),
    PRIMARY KEY (PONo)
    );

The line items have a relationship with purchase orders and stock items. The `LineItems` table manages these relationships using foreign keys. For example, the `StockNo` foreign key column in the `LineItems` table references the `StockNo` primary key column in the `StockItems` table, which you can define as follows:

    CREATE TABLE StockItems (
    StockNo NUMBER(4) PRIMARY KEY,
    Description VARCHAR2(20),
    Price NUMBER(6,2))
    );

The `Orders` table manages the relationship between a customer and purchase order using the `CustNo` foreign key column, which references the `CustNo` primary key column in the `Customers` table. However, the `Orders` table does not manage the relationship between a purchase order and its line items. As a result, this relationship must be managed by the `LineItems` table, which you can define as follows:

    CREATE TABLE LineItems (
    LineNo NUMBER(2),
    PONo NUMBER(5) REFERENCES Orders,
    StockNo NUMBER(4) REFERENCES StockItems,
    Quantity NUMBER(2),
    Discount NUMBER(4,2),
    PRIMARY KEY (LineNo, PONo)
    );
