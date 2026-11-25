This figure shows two tables, labeled "Employee_tab of type OBJ_T2" and "Addr_tab of type OBJ_T1" (also labeled "XMLType table" and "This XML fragment is stored out-of-line").

Above the tables is represented a series of objects (with ellipsis: "..."), of which one is shown: \<element name="Addr" xdb:SQLInline="false"\>. There is a dashed arrow from this object to the Employee_tab table.

The Employee_tab table has three columns: "Name", "Age," and "Addr REF XMLType". The Addr_tab table has three columns: "Street", "City", and an unnamed column.

There is an arrow from an "Addr REF XMLType" entry in the Employee_tab table to a single row in the Addr_tab table. The arrow is labeled "REF points to another XMLType instance".
