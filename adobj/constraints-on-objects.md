Oracle does not support constraints and defaults in type specifications. However, you can specify the constraints and defaults when creating the tables:

Example 9-15 Specifying Constraints on an Object Type When Creating a Table

    CREATE TYPE customer_typ AS OBJECT(
       cust_id INTEGER);
    /
    CREATE TYPE department_typ AS OBJECT(
       deptno INTEGER);
    /
    CREATE TABLE customer_tab OF customer_typ (
       cust_id default 1 NOT NULL);

    CREATE TABLE department_tab OF department_typ (
       deptno PRIMARY KEY);

    CREATE TABLE customer_tab1 (
       cust customer_typ DEFAULT customer_typ(1)
       CHECK (cust.cust_id IS NOT NULL),
       some_other_column VARCHAR2(32));
