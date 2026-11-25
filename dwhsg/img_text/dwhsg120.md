This illustrates the process flow in a SQL model. The SQL statement in question is:

The the flow is:

- The query results input to MODEL clause are vcr 2001 sales of 9 and dvd sales for 2001 of 0

- An array is defined of prod/year with 1999, 2000, and 2001 values of vcr 1, 5, 9; dvd 2, 6, 0; tv 3, 7, 1; pc 4, 8, 2

- rule 1 is applied so the values for 2000 change to vcr=2, dvd=4, tv=6, pc=8

- rule 2 is applied so the value for 2002vcr=11

- rule 3 is applied so the value for 2002 dvd=3

- MODEL clause results converted back to rows (vcr, 2001, 9), (dvd, 2001, 0), (vcr, 2002, 11), and (dvd, 2002, 3)

<!-- -->

- MODEL

- DIMENSION BY (prod, year)

- MEASURES (sales s)

- RULES UPSERT

- s\[ANY, 2000\] = s\[CV(prod), CV(year -1)\*2\], -- rule 1

- s\[vcr, 2000\] = s\[vcr, 2001 + s\[vcr, 2000\], -- rule 2

- s\[dvd, 2002\] = AVG(s)\[CV(prod), year \< 2001\]) -- rule 3
