The screenshot shows the Top SQL with Top Events section of the report results.

The table contains the following columns: SQL ID, Planhash, Sampled \# of Executions, % Activity, Event, % Event, Top Row Source, % RwSrc, SQL Text. Values in the SQL ID column are links. The rows of the table have the following values:

- Row 1: 31h2wmu3q47u6, 4090065844, 277, 26.22, CPU + Wait for CPU, 26.13, TABLE ACCESS - FULL, 19.94, SELECT /\*+ ORDERED USE_NL(c)

- Row 2: 3djkjtba139ct, 1426549735, 148, 13.76, db file sequential read, 12.00, \*\* Row Source Not Available \*\*, 12.00, INSERT INTO EMPLOYEES VALUES

- Row 3: null, null, null, null, flashback buf free by RVWR, 1.39, \*\* Row Source Not Available \*\*,1.39, null

- Row 4: 7u628xsamhqka, 781635435, 127, 11.82, db file sequential read, 9.70, DELETE, 9.70, DELETE FROM EPLOYEES WHERE EM...

- Row 5: null, null, null, null, flashback buf free by RVWR, 1.75, DELETE, 1.75, null

End of description.
