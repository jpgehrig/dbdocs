The image shows an application container with a map object, a metadata-linked table named oe.cmtb, an application root, a query, and three application PDBs named `AMER`, `EURO`, and `ASIA`. The map object, metadata-linked table, and query are all in the application root.

The map object is a single-column partitioned table with a single `Country` column. The `AMER` partition has the following values in the `COUNTRY` column: `US`, `MEXICO`, and `CANADA`. The `EURO` partition has the following values in the `COUNTRY` column: `UK`, `FRANCE`, and `GERMANY`. The `ASIA` partition has the following values in the `COUNTRY` column: `INDIA`, `CHINA`, and `JAPAN`.

The metadata-linked table `oe.cmtb` has two columns: `COUNTRY` and `VALUE`. The following three values are shown in the `COUNTRY` column in order: `MEXICO`, `GERMANY`, and `JAPAN`. The following three values are shown in the `VALUE` column in order: `EX35`, `NR104`, and `PD98`. Dots are shown going down in the table to indicate that the table contains more rows.

The query is the following:

    SELECT value FROM oe.cmtb WHERE country='GERMANY';

An arrow goes from the query to the `EURO` application PDB. The line has the following label: Executed in the `EURO` application PDB.

End of image description.
