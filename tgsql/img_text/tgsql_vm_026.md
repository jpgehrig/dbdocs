# Description of the illustration tgsql_vm_026.eps

This flowchart diagram shows the SQL Tuning Advisor APIs.

The following SQL Tuning Advisor API procedures are shown: `CREATE_TUNING_TASK`, `EXECUTE_TUNING_TASK`, and `REPORT_TUNING_TASK`.

Starting from the top of the diagram, STS leads to the `CREATE_TUNING_TASK` procedure, which leads to `EXECUTE_TUNING_TASK`. The `REPORT_TUNING_TASK` procedure is shown to only take place after execute and leads to four types of recommendations that user may choose to implement: store, SQL Profile, access, and rewrite.

End of image description.
