## H  Stopword Transformations in Oracle Text

This appendix describes the stopword rewrites or transformations for each operator. In all tables, the Stopword Expression column describes the query expression or component of a query expression, while the right-hand column describes the way Oracle Text rewrites the query.

This appendix contains the following topics:

- Understanding Stopword Transformations

- About Stopwords in Phrase Queries

- Word Transformations

- AND Transformations

- OR Transformations

- ACCUMulate Transformations

- MINUS Transformations

- MNOT Transformations

- NOT Transformations

- EQUIValence Transformations

- NEAR Transformations

- Weight Transformations

- Threshold Transformations

- WITHIN Transformations

### H.1 Understanding Stopword Transformations

When you use a stopword or stopword-only phrase as an operand for a query operator, Oracle Text rewrites the expression to eliminate the stopword or stopword-only phrase and then executes the query.

The token stopword stands for a single stopword or a stopword-only phrase.

The token non_stopword stands for either a single non-stopword, a phrase of all non-stopwords, or a phrase of non-stopwords and stopwords.

The token no_lex stands for a single character or a string of characters that is neither a stopword nor a word that is indexed. For example, the + character by itself is an example of a no_lex token.

When the Stopword Expression column completely describes the query expression, a rewritten expression of no_token means that no hits are returned when you enter such a query.

When the Stopword Expression column describes a component of a query expression with more than one operator, a rewritten expression of no_token means that a no_token value is passed to the next step of the rewrite.

Transformations that contain a no_token as an operand in the Stopword Expression column describe intermediate transformations in which the no_token is a result of a previous transformation. These intermediate transformations apply when the original query expression has at least one stopword and more than one operator.

For example, consider the following compound query expression:

    '(this NOT dog) AND cat'

Assuming that this is the only stopword in this expression, Oracle Text applies the following transformations in the following order:

stopword NOT non-stopword =\> no_token

no_token AND non_stopword =\> non_stopword

The resulting expression is:

    'cat'

### H.2 About Stopwords in Phrase Queries

If used in a phrase query, a stopword will match any single word, whether that word is a stopword or not. For example, if "in" and "to" are stopwords, but "throughout" is not, then the query "hiking in California" will match any of these phrases:

- hiking in California

- hiking to California

- hiking throughout California

### H.3 Word Transformations

| Stopword Expression | Rewritten Expression |
|:--------------------|:---------------------|
| stopword            | no_token             |
| no_lex              | no_token             |

The first transformation means that a stopword or stopword-only phrase by itself in a query expression results in no hits.

The second transformation says that a term that is not lexed, such as the + character, results in no hits.

### H.4 AND Transformations

| Stopword Expression        | Rewritten Expression |
|:---------------------------|:---------------------|
| non_stopword AND stopword  | non_stopword         |
| non_stopword AND no_token  | non_stopword         |
| stopword AND non_stopword  | non_stopword         |
| no_token AND non_stopword  | non_stopword         |
| stopword AND stopword      | no_token             |
| no_token AND stopword      | no_token             |
| stopword AND no_token      | no_token             |
| no_token AND no_token      | no_token             |

### H.5 OR Transformations

| Stopword Expression       | Rewritten Expression |
|:--------------------------|:---------------------|
| non_stopword OR stopword  | non_stopword         |
| non_stopword OR no_token  | non_stopword         |
| stopword OR non_stopword  | non_stopword         |
| no_token OR non_stopword  | non_stopword         |
| stopword OR stopword      | no_token             |
| no_token OR stopword      | no_token             |
| stopword OR no_token      | no_token             |
| no_token OR no_token      | no_token             |

### H.6 ACCUMulate Transformations

| Stopword Expression          | Rewritten Expression |
|:-----------------------------|:---------------------|
| non_stopword ACCUM stopword  | non_stopword         |
| non_stopword ACCUM no_token  | non_stopword         |
| stopword ACCUM non_stopword  | non_stopword         |
| no_token ACCUM non_stopword  | non_stopword         |
| stopword ACCUM stopword      | no_token             |
| no_token ACCUM stopword      | no_token             |
| stopword ACCUM no_token      | no_token             |
| no_token ACCUM no_token      | no_token             |

### H.7 MINUS Transformations

| Stopword Expression          | Rewritten Expression |
|:-----------------------------|:---------------------|
| non_stopword MINUS stopword  | non_stopword         |
| non_stopword MINUS no_token  | non_stopword         |
| stopword MINUS non_stopword  | no_token             |
| no_token MINUS non_stopword  | no_token             |
| stopword MINUS stopword      | no_token             |
| no_token MINUS stopword      | no_token             |
| stopword MINUS no_token      | no_token             |
| no_token MINUS no_token      | no_token             |

### H.8 MNOT Transformations

| Stopword Expression        | Rewritten Expression |
|:---------------------------|:---------------------|
| non_stopword MNOT stopword | non_stopword         |
| non_stopword MNOT no_token | non_stopword         |
| stopword MNOT non_stopword | no_token             |
| no_token MNOT non_stopword | no_token             |
| stopword MNOT stopword     | no_token             |
| no_token MNOT stopword     | no_token             |
| stopword MNOT no_token     | no_token             |
| no_token MNOT no_token     | no_token             |

### H.9 NOT Transformations

| Stopword Expression        | Rewritten Expression |
|:---------------------------|:---------------------|
| non_stopword NOT stopword  | non_stopword         |
| non_stopword NOT no_token  | non_stopword         |
| stopword NOT non_stopword  | no_token             |
| no_token NOT non_stopword  | no_token             |
| stopword NOT stopword      | no_token             |
| no_token NOT stopword      | no_token             |
| stopword NOT no_token      | no_token             |
| no_token NOT no_token      | no_token             |

### H.10 EQUIValence Transformations

| Stopword Expression          | Rewritten Expression |
|:-----------------------------|:---------------------|
| non_stopword EQUIV stopword  | non_stopword         |
| non_stopword EQUIV no_token  | non_stopword         |
| stopword EQUIV non_stopword  | non_stopword         |
| no_token EQUIV non_stopword  | non_stopword         |
| stopword EQUIV stopword      | no_token             |
| no_token EQUIV stopword      | no_token             |
| stopword EQUIV no_token      | no_token             |
| no_token EQUIV no_token      | no_token             |

**Note:**

When you use query explain plan, not all of the equivalence transformations are represented in the `EXPLAIN` table.

### H.11 NEAR Transformations

| Stopword Expression         | Rewritten Expression |
|:----------------------------|:---------------------|
| non_stopword NEAR stopword  | non_stopword         |
| non_stopword NEAR no_token  | non_stopword         |
| stopword NEAR non_stopword  | non_stopword         |
| no_token NEAR non_stopword  | non_stopword         |
| stopword NEAR stopword      | no_token             |
| no_token NEAR stopword      | no_token             |
| stopword NEAR no_token      | no_token             |
| no_token NEAR no_token      | no_token             |

### H.12 Weight Transformations

| Stopword Expression | Rewritten Expression |
|:--------------------|:---------------------|
| stopword \* n       | no_token             |
| no_token \* n       | no_token             |

### H.13 Threshold Transformations

| Stopword Expression | Rewritten Expression |
|:--------------------|:---------------------|
| stopword \> n       | no_token             |
| no_token \> n       | no_token             |

### H.14 WITHIN Transformations

| Stopword Expression     | Rewritten Expression |
|:------------------------|:---------------------|
| stopword WITHIN section | no_token             |
| no_token WITHIN section | no_token             |
