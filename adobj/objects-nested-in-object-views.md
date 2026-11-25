An object type can have other object types nested in it as attributes.

If the object type on which an object view is based has an attribute that itself is an object type, then you must provide column objects for this attribute as part of the process of creating the object view. If column objects of the attribute type already exist in a relational table, you can simply select them; otherwise, you must synthesize the object instances from underlying relational data just as you synthesize the principal object instances of the view. You synthesize, or create, these objects by calling the respective constructor methods of the object type to create the object instances, and you can populate their attributes with data from relational columns specified in the constructor.

For example, consider the department table `dept` in Example 6-2. You might want to create an object view where the addresses are objects inside the department objects. That would allow you to define reusable methods for address objects, and use them for all kinds of addresses.

First, create the types for the address and department objects, then create the view containing the department number, name and address. The `address` objects are constructed from columns of the relational table.

Example 6-2 Creating a View with Nested Object Types

    CREATE TABLE dept (
        deptno       NUMBER PRIMARY KEY,
        deptname     VARCHAR2(20),
        deptstreet   VARCHAR2(20),
        deptcity     VARCHAR2(10),
        deptstate    CHAR(2),
        deptzip      VARCHAR2(10));

    CREATE TYPE address_t AS OBJECT (
       street   VARCHAR2(20),
        city    VARCHAR2(10),
        state   CHAR(2),
        zip     VARCHAR2(10));
    /
    CREATE TYPE dept_t AS OBJECT (
       deptno     NUMBER,
       deptname   VARCHAR2(20),
       address    address_t );
    /

    CREATE VIEW dept_view OF dept_t WITH OBJECT IDENTIFIER (deptno) AS
        SELECT d.deptno, d.deptname,
          address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip) AS
          deptaddr
          FROM dept d;

    insert into dept values(1,'Sales','500 Oracle pkwy','Redwood S','CA','94065');
    insert into dept values(2,'ST','400 Oracle Pkwy','Redwood S','CA','94065');
    insert into dept values(3,'Apps','300 Oracle pkwy','Redwood S','CA','94065');

    select * from dept_view;

        DEPTNO DEPTNAME
    ---------- --------------------
    ADDRESS(STREET, CITY, STATE, ZIP)
    ----------------------------------------------------------------------------------
             1 Sales
    ADDRESS_T('500 Oracle pkwy', 'Redwood S', 'CA', '94065')

             2 ST
    ADDRESS_T('400 Oracle Pkwy', 'Redwood S', 'CA', '94065')

             3 Apps
    ADDRESS_T('300 Oracle pkwy', 'Redwood S', 'CA', '94065')
