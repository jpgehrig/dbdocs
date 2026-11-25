Learn how to calculate Association Rules using Apriori algorithm.

- About Apriori

- Association Rules and Frequent Itemsets

- Data Preparation for Apriori

- Calculating Association Rules

- Evaluating Association Rules

**Related Topics**

- [Association](association.md)

### 10.1 About Apriori

Learn about Apriori.

An association mining problem can be decomposed into the following subproblems:

- Find all combinations of items in a set of transactions that occur with a specified minimum frequency. These combinations are called **frequent itemsets**.

- Calculate rules that express the probable co-occurrence of items within frequent itemsets.

Apriori calculates the probability of an item being present in a frequent itemset, given that another item or items is present.

Association rule mining is not recommended for finding associations involving rare events in problem domains with a large number of items. Apriori discovers patterns with frequencies above the minimum support threshold. Therefore, to find associations involving rare events, the algorithm must run with very low minimum support values. However, doing so potentially explodes the number of enumerated itemsets, especially in cases with a large number of items. This increases the execution time significantly. Classification or Anomaly Detection is more suitable for discovering rare events when the data has a high number of attributes.

The build process for Apriori supports parallel execution.

**Related Topics**

- Example: Calculating Rules from Frequent Itemsets
- [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md)

### 10.2 Association Rules and Frequent Itemsets

The Apriori algorithm calculates rules that express probabilistic relationships between items in frequent itemsets. For example, a rule derived from frequent itemsets containing A, B, and C might state that if A and B are included in a transaction, then C is likely to also be included.

An association rule states that an item or group of items implies the presence of another item with some probability. Unlike decision tree rules, which predict a target, association rules simply express correlation.

#### 10.2.1 Antecedent and Consequent

The IF component of an association rule is known as the **antecedent**. The THEN component is known as the **consequent**. The antecedent and the consequent are disjoint; they have no items in common.

Oracle Data Mining supports association rules that have one or more items in the antecedent and a single item in the consequent.

#### 10.2.2 Confidence

Rules have an associated confidence, which is the conditional probability that the consequent occurs given the occurrence of the antecedent. You can specify the minimum confidence for rules.

### 10.3 Data Preparation for Apriori

Association models are designed to use transactional data. In transactional data, there is a one-to-many relationship between the case identifier and the values for each case. Each case ID/value pair is specified in a separate record (row).

#### 10.3.1 Native Transactional Data and Star Schemas

Learn about storage format of transactional data.

Transactional data may be stored in native transactional format, with a non-unique case ID column and a values column, or it may be stored in some other configuration, such as a star schema. If the data is not stored in native transactional format, it must be transformed to a nested column for processing by the Apriori algorithm.

**Related Topics**

- [Transactional Data](association.md)
- [Oracle Data Mining User’s Guide](../dmprg/using-nested-dita.md)

#### 10.3.2 Items and Collections

In transactional data, a collection of items is associated with each case. The collection theoretically includes all possible members of the collection. For example, all products can theoretically be purchased in a single market-basket transaction. However, in actuality, only a tiny subset of all possible items are present in a given transaction; the items in the market-basket represent only a small fraction of the items available for sale in the store.

#### 10.3.3 Sparse Data

Learn about missing items through sparsity.

Missing items in a collection indicate **sparsity**. Missing items may be present with a null value, or they may simply be missing.

Nulls in transactional data are assumed to represent values that are known but not present in the transaction. For example, three items out of hundreds of possible items might be purchased in a single transaction. The items that were not purchased are known but not present in the transaction.

Oracle Data Mining assumes sparsity in transactional data. The Apriori algorithm is optimized for processing sparse data.

**Note:**

Apriori is not affected by Automatic Data Preparation.

**Related Topics**

- [Oracle Data Mining User’s Guide](../dmprg/handling-missing-values.md)

#### 10.3.4 Improved Sampling

Association Rules (AR) can use a good sample size with performance guarantee, based on the work of Riondato and Upfal.

The AR algorithm computes the sample size by the following inputs:

- d-index of the dataset

- Absolute error ε

- Confidence level γ

**d****-index** is defined as the maximum integer d such that the dataset contains at least d transactions of length d at the minimum. It is the upper bound of Vapnik-Chervonenkis (VC) dimension. The AR algorithm computes d-index of the dataset by scanning the length of all transactions in the dataset.

Users specify absolute error ε and confidence level γ parameters. A large d-index, small AR support, small ε or large γ can cause a large sample size. The sample size theoretically guarantees that the absolute error of both the support and confidence of the approximated AR (from sampling) is less than ε compared to the exact AR with probability (or confidence level) at least γ. In this document this sample size is called AR-specific sample size.

##### 10.3.4.1 Sampling Implementation

The sample size is only computed when users turn on the sampling (`ODMS_SAMPLING` is set as `ODMS_SAMPLING_ENABLE`) and do not specify the sample size (`ODMS_SAMPLE_SIZE` is unspecified).

##### Usage Notes

1.  If `ODMS_SAMPLING` is unspecified or set as `ODMS_SAMPLING_DISABLE`, the sampling is not performed for AR and the exact AR is obtained.

2.  If `ODMS_SAMPLING` is set as `ODMS_SAMPLING_ENABLE` and if `ODMS_SAMPLE_SIZE` is specified as positive integer number then the user-specified sample size (`ODMS_SAMPLE_SIZE`) is utilized. The sampling is performed in the general data preparation stage before the AR algorithm. The AR-specific sample size is not computed. The approximated AR is obtained.

3.  If `ODMS_SAMPLING` is set as `ODMS_SAMPLING_ENABLE` and `ODMS_SAMPLE_SIZE` is not specified, the AR-specified sample size is computed and then sampling is performed in the AR algorithm. The approximated AR is obtained.
    **Note:**

    If the computed AR-specific sample size is larger than or equal to the total transaction size in the dataset, the sampling is not performed and the exact AR is obtained.

If users do not have a good idea on the choice of sample size for AR, it is suggested to leave `ODMS_SAMPLE_SIZE` unspecified, only specify proper values for sampling parameters and let AR algorithm compute the suitable AR-specific sample size.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 10.4 Calculating Association Rules

The first step in association analysis is the enumeration of **itemsets**. An itemset is any combination of two or more items in a transaction.

#### 10.4.1 Itemsets

Learn about itemsets.

The maximum number of items in an itemset is user-specified. If the maximum is two, then all the item pairs are counted. If the maximum is greater than two, then all the item pairs, all the item triples, and all the item combinations up to the specified maximum are counted.

The following table shows the itemsets derived from the transactions shown in the following example, assuming that maximum number of items in an itemset is set to 3.

Table 10-1 Itemsets

| Transaction | Itemsets                                                            |
|:------------|:--------------------------------------------------------------------|
| 11          | (B,D) (B,E) (D,E) (B,D,E)                                           |
| 12          | (A,B) (A,C) (A,E) (B,C) (B,E) (C,E) (A,B,C) (A,B,E) (A,C,E) (B,C,E) |
| 13          | (B,C) (B,D) (B,E) (C,D) (C,E) (D,E) (B,C,D) (B,C,E) (B,D,E) (C,D,E) |

Example 10-1 Sample Transactional Data

    TRANS_ID   ITEM_ID
    ---------  -------------------
    11         B
    11         D
    11         E
    12         A
    12         B
    12         C
    12         E
    13         B
    13         C
    13         D
    13         E

#### 10.4.2 Frequent Itemsets

Learn about Frequent Itemsets and Support.

Association rules are calculated from itemsets. If rules are generated from all possible itemsets, there can be a very high number of rules and the rules may not be very meaningful. Also, the model can take a long time to build. Typically it is desirable to only generate rules from itemsets that are well-represented in the data. **Frequent itemsets** are those that occur with a minimum frequency specified by the user.

The minimum frequent itemset **Support** is a user-specified percentage that limits the number of itemsets used for association rules. An itemset must appear in at least this percentage of all the transactions if it is to be used as a basis for rules.

The following table shows the itemsets from Table 10-1 that are frequent itemsets with support \> 66%.

Table 10-2 Frequent Itemsets

| Frequent Itemset | Transactions | Support |
|:-----------------|:-------------|:--------|
| (B,C)            | 2 of 3       | 67%     |
| (B,D)            | 2 of 3       | 67%     |
| (B,E)            | 3 of 3       | 100%    |
| (C,E)            | 2 of 3       | 67%     |
| (D,E)            | 2 of 3       | 67%     |
| (B,C,E)          | 2 of 3       | 67%     |
| (B,D,E)          | 2 of 3       | 67%     |

**Related Topics**

- Apriori

#### 10.4.3 Example: Calculating Rules from Frequent Itemsets

Example to calculating rules from Frequent itemsets.

The following tables show the itemsets and frequent itemsets that were calculated in "Association". The frequent itemsets are the itemsets that occur with a minimum support of 67%; at least 2 of the 3 transactions must include the itemset.

Table 10-3 Itemsets

| Transaction | Itemsets                                                            |
|:------------|:--------------------------------------------------------------------|
| 11          | (B,D) (B,E) (D,E) (B,D,E)                                           |
| 12          | (A,B) (A,C) (A,E) (B,C) (B,E) (C,E) (A,B,C) (A,B,E) (A,C,E) (B,C,E) |
| 13          | (B,C) (B,D) (B,E) (C,D) (C,E) (D,E) (B,C,D) (B,C,E) (B,D,E) (C,D,E) |

Table 10-4 Frequent Itemsets with Minimum Support 67%

| Itemset | Transactions   | Support |
|:--------|:---------------|:--------|
| (B,C)   | 12 and 13      | 67%     |
| (B,D)   | 11 and 13      | 67%     |
| (B,E)   | 11, 12, and 13 | 100%    |
| (C,E)   | 12 and 13      | 67%     |
| (D,E)   | 11 and 13      | 67%     |
| (B,C,E) | 12 and 13      | 67%     |
| (B,D,E) | 11 and 13      | 67%     |

A rule expresses a conditional probability. Confidence in a rule is calculated by dividing the probability of the items occurring together by the probability of the occurrence of the antecedent.

For example, if B (antecedent) is present, what is the chance that C (consequent) is also present? What is the confidence for the rule "IF B, THEN C"?

As shown in Table 10-3:

- All 3 transactions include B (3/3 or 100%)

- Only 2 transactions include both B and C (2/3 or 67%)

- Therefore, the confidence of the rule "IF B, THEN C" is 67/100 or 67%.

The following table the rules that can be derived from the frequent itemsets in Table 10-4.

Table 10-5 Frequent Itemsets and Rules

| Frequent Itemset | Rules                                                                   | prob(antecedent and consequent) / prob(antecedent) | Confidence                |
|:-----------------|:------------------------------------------------------------------------|:---------------------------------------------------|:--------------------------|
| (B,C)            | • (If B then C)<br>• (If C then B)                                      | • 67/100<br>• 67/67                                | • 67%<br>• 100%           |
| (B,D)            | • (If B then D)<br>• (If D then B)                                      | • 67/100<br>• 67/67                                | • 67%<br>• 100%           |
| (B,E)            | • (If B then E)<br>• (If E then B)                                      | • 100/100<br>• 100/100                             | • 100%<br>• 100%          |
| (C,E)            | • (If C then E)<br>• (If E then C)                                      | • 67/67<br>• 67/100                                | • 100%<br>• 67%           |
| (D,E)            | • (If D then E)<br>• I(f E then D)                                      | • 67/67<br>• 67/100                                | • 100%<br>• 67%           |
| (B,C,E)          | • (If B and C then E)<br>• (If B and E then C)<br>• (If C and E then B) | • 67/67<br>• 67/100<br>• 67/67                     | • 100%<br>• 67%<br>• 100% |
| (B,D,E)          | • (If B and D then E)<br>• (If B and E then D)<br>• (If D and E then B) | • 67/67<br>• 67/100<br>• 67/67                     | • 100%<br>• 67%<br>• 100% |

If the minimum confidence is 70%, ten rules are generated for these frequent itemsets. If the minimum confidence is 60%, sixteen rules are generated.

**Tip:**

Increase the minimum confidence if you want to decrease the build time for the model and generate fewer rules.

**Related Topics**

- [Association](association.md)

#### 10.4.4 Aggregates

Aggregates refer to the quantities associated with each item that the user opts for Association Rules Model to aggregate.

There can be more than one aggregate. For example, the user can specify the model to aggregate both profit and quantity.

#### 10.4.5 Example: Calculating Aggregates

The following example shows the concept of Aggregates.

##### Calculating Aggregates for Grocery Store Data

Assume a grocery store has the following data:

Table 10-6 Grocery Store Data

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

#### 10.4.6 Including and Excluding Rules

Explains including rules and excluding rules used in Association.

Including rules enables a user to provide a list of items such that at least one item from the list must appear in the rules that are returned. Excluding rules enables a user to provide a list of items such that no item from the list can appear in the rules that are returned.

**Note:**

Since each association rule includes both antecedent and consequent, a set of including or excluding rules can be specified for antecedent while another set of including or excluding rules can be specified for consequent. Including or excluding rules can also be defined for the association rule.

**Related Topics**

- [Oracle Data Mining User’s Guide](../dmprg/model-detail-views.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

#### 10.4.7 Performance Impact for Aggregates

Aggregate function requires more memory usage and longer execution time.

For each item, the user may supply several columns to aggregate. It requires more memory to buffer the extra data and more time to compute the aggregate values.

### 10.5 Evaluating Association Rules

Minimum support and confidence are used to influence the build of an association model. Support and confidence are also the primary metrics for evaluating the quality of the rules generated by the model. Additionally, Oracle Data Mining supports lift for association rules. These statistical measures can be used to rank the rules and hence the usefulness of the predictions.

#### 10.5.1 Support

The support of a rule indicates how frequently the items in the rule occur together. For example, cereal and milk might appear together in 40% of the transactions. If so, the following rules each have a support of 40%:

    cereal implies milk
    milk implies cereal

Support is the ratio of transactions that include all the items in the antecedent and consequent to the number of total transactions.

Support can be expressed in probability notation as follows:

    support(A implies B) = P(A, B)

#### 10.5.2 Minimum Support Count

Minimum support Count defines minimum threshold in transactions that each rule must satisfy.

When the number of transactions is unknown, the support percentage threshold parameter can be tricky to set appropriately. For this reason, support can also be expressed as a count of transactions, with the greater of the two thresholds being used to filter out infrequent itemsets. The default is `1` indicating that this criterion is not applied.

**Related Topics**

- [Association Rules](association.md)
- [Oracle Data Mining User’s Guide](../dmprg/model-detail-views.md)
- Frequent Itemsets

#### 10.5.3 Confidence

The confidence of a rule indicates the probability of both the antecedent and the consequent appearing in the same transaction.

Confidence is the conditional probability of the consequent given the antecedent. For example, cereal appears in 50 transactions; 40 of the 50 might also include milk. The rule confidence is:

    cereal implies milk with 80% confidence

Confidence is the ratio of the rule support to the number of transactions that include the antecedent.

Confidence can be expressed in probability notation as follows.

    confidence (A implies B) = P (B/A), which is equal to P(A, B) / P(A)

**Related Topics**

- Confidence
- Frequent Itemsets

#### 10.5.4 Reverse Confidence

The Reverse Confidence of a rule is defined as the number of transactions in which the rule occurs divided by the number of transactions in which the consequent occurs.

Reverse Confidence eliminates rules that occur because the consequent is frequent. The default is `0`.

**Related Topics**

- Confidence
- Example: Calculating Rules from Frequent Itemsets
- [Oracle Data Mining User’s Guide](../dmprg/model-detail-views.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

#### 10.5.5 Lift

Both support and confidence must be used to determine if a rule is valid. However, there are times when both of these measures may be high, and yet still produce a rule that is not useful. For example:

    Convenience store customers who buy orange juice also buy milk with
    a 75% confidence.
    The combination of milk and orange juice has a support of 30%.

This at first sounds like an excellent rule, and in most cases, it would be. It has high confidence and high support. However, what if convenience store customers in general buy milk 90% of the time? In that case, orange juice customers are actually less likely to buy milk than customers in general.

A third measure is needed to evaluate the quality of the rule. Lift indicates the strength of a rule over the random co-occurrence of the antecedent and the consequent, given their individual support. It provides information about the improvement, the increase in probability of the consequent given the antecedent. Lift is defined as follows.

    (Rule Support) /(Support(Antecedent) * Support(Consequent))

This can also be defined as the confidence of the combination of items divided by the support of the consequent. So in our milk example, assuming that 40% of the customers buy orange juice, the improvement would be:

    30% / (40% * 90%)

which is 0.83 – an improvement of less than 1.

Any rule with an improvement of less than 1 does not indicate a real cross-selling opportunity, no matter how high its support and confidence, because it actually offers less ability to predict a purchase than does random chance.

**Tip:**

Decrease the maximum rule length if you want to decrease the build time for the model and generate simpler rules.

**Tip:**

Increase the minimum support if you want to decrease the build time for the model and generate fewer rules.
