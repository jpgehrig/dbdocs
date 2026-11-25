Sequence of three transformations (T1, T2, and T3), implemented by table functions. Each transformation is performed by a single table function. Output from all but the final one is materialized and staged before being passed to the next transformation.

- OLTP database structure points to T1

- T1 points to Stage 1

- Stage 1 points to T2

- T2 points to Stage 2

- Stage 2 points to T3

- T3 points to DSS database structure
