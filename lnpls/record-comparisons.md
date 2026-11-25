## 5.14 Record Comparisons

Records cannot be tested natively for nullity, equality, or inequality.

These `BOOLEAN` expressions are illegal:

- `My_Record IS NULL`

- `My_Record_1 = My_Record_2`

- `My_Record_1 > My_Record_2`

You must write your own functions to implement such tests. For information about writing functions, see [PL/SQL Subprograms](plsql-subprograms.md).
