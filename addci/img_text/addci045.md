Sequence of the three transformations (T1, T2 and T3) as in the figure representing unparallelized, unpiped table functions, but here each table function is represented by multiple slave processes executing in parallel, and there is no intervening staging between the transformations.

- OLTP database structure points to several T1s

- T1s are collected and point to several T2s

- T2s are collected and point to several T3s

- T3s are collected and point to the DSS database structure
