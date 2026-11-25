## 188 DBMS_UNDO_ADV

The Undo Advisor assists in correctly sizing the undo tablespace and sets the low threshold value of the Undo Retention Period for any Oracle Flashback requirements. The Undo Advisor can also be used to estimate the undo tablespace required for migration from manual to automatic undo management before actually creating the new undo tablespace.

The `DBMS_UNDO_ADVISOR` package provides subprograms to manage the execution of the Undo Advisor feature.

The Undo Advisor relies for its analysis on data collected in the Automatic Workload Repository (AWR). Thus, it is important that the AWR have adequate workload statistics available so that the Undo Advisor can make accurate recommendations. For newly created databases, adequate statistics may not be available immediately. In such cases, continue to use the default auto-extending undo tablespace until at least one workload cycle completes.

This chapter contains the following topic:

- [Summary of DBMS_UNDO_ADV Subprograms](summary-dbms_undo_adv-subprograms.md)
