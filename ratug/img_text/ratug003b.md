#

This diagram illustrates the workflow for using SQL Performance Analyzer in a database upgrade from Oracle 9.2.0.8 or 10.1.0.5 to Oracle Database 11.2.0.3 or higher. In the top left corner is a database labeled "Oracle Database 9.2.0.8 or 10.1.0.5 - Production". An arrow labeled "1" points from this database to multiple documents labeled "SQL Trace (subset of sessions)". A second arrow labeled "2" points from this database to a single document labeled "Mapping Table". Two arrows labeled "3" point from both sets of documents to a second database in the lower left corner labeled "Oracle Database 12.2".

From the second database labeled "Oracle Database 12.2", a line labeled "4" connects to the text "Build STS". A second unlabeled line connects to the text "No Data Necessary". An arrow labeled "5" points to a third database in the lower right corner labeled "Oracle Database 11.2.0.3 or higher - Test". This arrow is further labeled with the text "SQL" and "Remote Test-execute (db link)".

From the third database labeled "Oracle Database 11.2.0.3 or higher - Test", another arrow labeled "5" points back to the second database labeled "Oracle Database 12.2". This arrow is further labeled with the text "Plan + Stats". A line labeled "6" connects to the text "Compare Perf, View Report" from the "Oracle Database 12.2" database.

End of description.
