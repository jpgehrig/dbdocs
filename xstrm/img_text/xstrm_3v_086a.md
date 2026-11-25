This illustration shows changes to the same row in database A and database B. The columns are the same in both databases: Name, RowTS, Office, TS1, Title, Salary, and TS2. In both databases, the following columns are invisible: TS1 and TS2.

In database A, the values of the row are:

- The row starts with the following values: Scott, @T10, 1080, @T10, MTS1, 100, @T10.

- The row is changed to have the following values: Scott, @T22, 1103, @T10, MTS1, 100, @T10. Text above the row reads: “Update column group (Office)”. An arrow shows this change being replicated to database B.

- After conflict resolution, the row has the following values: Scott, @T22, 1103, @T22, MTS2, 100, @T20.

In database B, the values of the row are:

- The row starts with the following values: Scott, @T10, 1080, @T10, MTS1, 100, @T10.

- The row is changed to have the following values: Scott, @T20, 1080, @T10, MTS2, 100, @T20. Text above the row reads: “Update column group (Title, Salary)”. An arrow shows this change being replicated to database A.

- After conflict resolution, the row has the following values: Scott, @T22, 1103, @T22, MTS2, 100, @T20.
