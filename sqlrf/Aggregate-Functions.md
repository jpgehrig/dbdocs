## Aggregate Functions

Aggregate functions return a single result row based on groups of rows, rather than on single rows. Aggregate functions can appear in select lists and in `ORDER` `BY` and `HAVING` clauses. They are commonly used with the `GROUP` `BY` clause in a `SELECT` statement, where Oracle Database divides the rows of a queried table or view into groups. In a query containing a `GROUP` `BY` clause, the elements of the select list can be aggregate functions, `GROUP` `BY` expressions, constants, or expressions involving one of these. Oracle applies the aggregate functions to each group of rows and returns a single result row for each group.

If you omit the `GROUP` `BY` clause, then Oracle applies aggregate functions in the select list to all the rows in the queried table or view. You use aggregate functions in the `HAVING` clause to eliminate groups from the output based on the results of the aggregate functions, rather than on the values of the individual rows of the queried table or view.

**See Also:**

- [Using the GROUP BY Clause: Examples](SELECT.md) and the [HAVING Clause](SELECT.md) for more information on the `GROUP` `BY` clause and `HAVING` clauses in queries and subqueries

- Appendix C in [Oracle Database Globalization Support Guide](../nlspg/appendix-C-collation-derivation-and-determination-rules-for-SQL-operations.md) for the collation determination rules for expressions in the `ORDER` `BY` clause of an aggregate function

Many (but not all) aggregate functions that take a single argument accept these clauses:

- `DISTINCT` and `UNIQUE`, which are synonymous, cause an aggregate function to consider only distinct values of the argument expression. The syntax diagrams for aggregate functions in this chapter use the keyword `DISTINCT` for simplicity.

- `ALL` causes an aggregate function to consider all values, including all duplicates.

For example, the `DISTINCT` average of 1, 1, 1, and 3 is 2. The `ALL` average is 1.5. If you specify neither, then the default is `ALL`.

Some aggregate functions allow the `windowing_clause`, which is part of the syntax of analytic functions. Refer to [windowing_clause](Analytic-Functions.md) for information about this clause.

All aggregate functions except `COUNT`(\*), `GROUPING`, and `GROUPING_ID` ignore nulls. You can use the `NVL` function in the argument to an aggregate function to substitute a value for a null. `COUNT` and `REGR_COUNT` never return null, but return either a number or zero. For all the remaining aggregate functions, if the data set contains no rows, or contains only rows with nulls as arguments to the aggregate function, then the function returns null.

The aggregate functions `MIN`, `MAX`, `SUM`, `AVG`, `COUNT`, `VARIANCE`, and `STDDEV`, when followed by the `KEEP` keyword, can be used in conjunction with the `FIRST` or `LAST` function to operate on a set of values from a set of rows that rank as the `FIRST` or `LAST` with respect to a given sorting specification. Refer to [FIRST](FIRST.md) for more information.

You can nest aggregate functions. For example, the following example calculates the average of the maximum salaries of all the departments in the sample schema `hr`:

    SELECT AVG(MAX(salary))
      FROM employees
      GROUP BY department_id;

    AVG(MAX(SALARY))
    ----------------
          10926.3333

This calculation evaluates the inner aggregate (`MAX`(`salary`)) for each group defined by the `GROUP` `BY` clause (`department_id`), and aggregates the results again.

- [APPROX_COUNT](APPROX_COUNT.md)
- [APPROX_COUNT_DISTINCT](APPROX_COUNT_DISTINCT.md)
- [APPROX_COUNT_DISTINCT_AGG](APPROX_COUNT_DISTINCT_AGG.md)
- [APPROX_COUNT_DISTINCT_DETAIL](APPROX_COUNT_DISTINCT_DETAIL.md)
- [APPROX_MEDIAN](APPROX_MEDIAN.md)
- [APPROX_PERCENTILE](APPROX_PERCENTILE.md)
- [APPROX_PERCENTILE_AGG](APPROX_PERCENTILE_AGG.md)
- [APPROX_PERCENTILE_DETAIL](APPROX_PERCENTILE_DETAIL.md)
- [APPROX_RANK](APPROX_RANK.md)
- [APPROX_SUM](APPROX_SUM.md)
- [AVG](AVG.md)
- [COLLECT](COLLECT.md)
- [CORR](CORR.md)
- [CORR\_\*](CORR_A.md)
- [COUNT](COUNT.md)
- [COVAR_POP](COVAR_POP.md)
- [COVAR_SAMP](COVAR_SAMP.md)
- [CUME_DIST](CUME_DIST.md)
- [DENSE_RANK](DENSE_RANK.md)
- [FIRST](FIRST.md)
- [GROUP_ID](GROUP_ID.md)
- [GROUPING](GROUPING.md)
- [GROUPING_ID](GROUPING_ID.md)
- [JSON_ARRAYAGG](JSON_ARRAYAGG.md)
- [JSON_OBJECTAGG](JSON_OBJECTAGG.md)
- [LAST](LAST.md)
- [LISTAGG](LISTAGG.md)
- [MAX](MAX.md)
- [MEDIAN](MEDIAN.md)
- [MIN](MIN.md)
- [PERCENT_RANK](PERCENT_RANK.md)
- [PERCENTILE_CONT](PERCENTILE_CONT.md)
- [PERCENTILE_DISC](PERCENTILE_DISC.md)
- [RANK](RANK.md)
- [REGR\_ (Linear Regression) Functions](REGR_-Linear-Regression-Functions.md)
- [STATS_BINOMIAL_TEST](STATS_BINOMIAL_TEST.md)
- [STATS_CROSSTAB](STATS_CROSSTAB.md)
- [STATS_F_TEST](STATS_F_TEST.md)
- [STATS_KS_TEST](STATS_KS_TEST.md)
- [STATS_MODE](STATS_MODE.md)
- [STATS_MW_TEST](STATS_MW_TEST.md)
- [STATS_ONE_WAY_ANOVA](STATS_ONE_WAY_ANOVA.md)
- [STATS_T_TEST\_\*](STATS_T_TEST_.md)
- [STATS_WSR_TEST](STATS_WSR_TEST.md)
- [STDDEV](STDDEV.md)
- [STDDEV_POP](STDDEV_POP.md)
- [STDDEV_SAMP](STDDEV_SAMP.md)
- [SUM](SUM.md)
- [SYS_OP_ZONE_ID](SYS_OP_ZONE_ID.md)
- [SYS_XMLAGG](SYS_XMLAGG.md)
- [TO_APPROX_COUNT_DISTINCT](TO_APPROX_COUNT_DISTINCT.md)
- [TO_APPROX_PERCENTILE](TO_APPROX_PERCENTILE.md)
- [VAR_POP](VAR_POP.md)
- [VAR_SAMP](VAR_SAMP.md)
- [VARIANCE](VARIANCE.md)
- [XMLAGG](XMLAGG.md)
