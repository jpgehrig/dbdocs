Use these SQL queries to track the progress of `utlrp.sql` script recompilation of invalid objects.

Oracle recommends that you run the `utlrp.sql` script after upgrade to recompile invalid objects. You can run SQL queries to monitor the script.

Example 10-1 Number of Invalid Objects Remaining

Enter this query to return the number of remaining invalid objects. This number decreases over time as the `utlrp.sql` script runs.

    SELECT COUNT(*) FROM obj$ WHERE status IN (4, 5, 6);

Example 10-2 Number of Objects Recompiled

Enter this query to return the number of objects that `utlrp.sql` has compiled. This number increases over time as the script runs.

    SELECT COUNT(*) FROM UTL_RECOMP_COMPILED;

Example 10-3 Number of Objects Recompiled with Errors

Enter this query to return the number of objects that `utlrp.sql` has compiled with errors.

    select COUNT(DISTINCT(obj#)) "OBJECTS WITH ERRORS" from utl_recomp_errors;

If the number is higher than expected, then examine the error messages reported with each object. If you see errors due to system misconfiguration or resource constraints, then fix the cause of these errors, and run `utlrp.sql` again.

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
