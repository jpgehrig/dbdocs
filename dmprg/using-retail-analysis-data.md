Retail analysis often makes use of Association Rules and Association models.

The Association Rules are enhanced to calculate aggregates along with rules or itemsets.

**Related Topics**

- [Oracle Data Mining Concepts](../dmcon/apriori.md)

### 3.5.1 Example: Calculating Aggregates

The following example shows the concept of Aggregates.

#### Calculating Aggregates for Grocery Store Data

Assume a grocery store has the following data:

Table 3-2 Grocery Store Data

| Customer   | Item A               | Item B                | Item C                | Item D               |
|:-----------|:---------------------|:----------------------|:----------------------|:---------------------|
| Customer 1 | Buys (Profit \$5.00) | Buys (Profit \$3.20)  | Buys (Profit \$12.00) | NA                   |
| Customer 2 | Buys (Profit \$4.00) | NA                    | Buys (Profit \$4.20)  | NA                   |
| Customer 3 | Buys (Profit \$3.00) | Buys (Profit \$10.00) | Buys (Profit \$14.00) | Buys (Profit \$8.00) |
| Customer 4 | Buys (Profit \$2.00) | NA                    | NA                    | Buys (Profit \$1.00) |

The basket of each customer can be viewed as a transaction. The manager of the store is interested in not only the existence of certain association rules, but also in the aggregated profit if such rules exist.

In this example, one of the association rules can be (A, B)=\>C for customer 1 and customer 3. Together with this rule, the store manager may want to know the following:

- The total profit of item A appearing in this rule

- The total profit of item B appearing in this rule

- The total profit for consequent C appearing in this rule

- The total profit of all items appearing in the rule

For this rule, the profit for item A is \$5.00 + \$3.00 = \$8.00, for item B the profit is \$3.20 + \$10.00 = \$13.20, for consequent C, the profit is \$12.00 + \$14.00 = \$26.00, for the antecedent itemset (A, B) is \$8.00 + \$13.20 = \$21.20. For the whole rule, the profit is \$21.20 + \$26.00 = \$47.40.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)
