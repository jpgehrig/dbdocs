This illustration shows changes to the same row in database A and database B. The columns are the same in both databases: Name, RowTS, BankName, Balance, and TS1. In both databases, the following columns are invisible: RowTS and TS1.

In database A, the values of the row are:

- The row starts with the following values: Scott, @T10, Chase, 100, and @T10.

- The row is changed to have the following values: Scott, @T20, Chase, 110, and @T20. Text above the row reads: “Increase balance by 10”. An arrow shows this change being replicated to database B.

- After conflict resolution, the row has the following values: Scott, @T22, Chase, 130, and @T22. Text above the row reads: “Apply delta of 20”.

In database B, the values of the row are:

- The row starts with the following values: Scott, @T10, Chase, 100, and @T10.

- The row is changed to have the following values: Scott, @T22, Chase, 120, and @T22. Text above the row reads: “Increase balance by 20”. An arrow shows this change being replicated to database A.

- After conflict resolution, the row has the following values: Scott, @T22, Chase, 130, and @T22. Text above the row reads: “Apply delta of 10”.
