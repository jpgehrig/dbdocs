## F  The Oracle Text Scoring Algorithm

This appendix describes how Oracle Text calculates scoring for word queries, which is different from the way it calculates scores for `ABOUT` queries in English. Scoring is obtained using the `SCORE` operator.

This appendix contains these topics:

- Scoring Algorithm for Word Queries

- Word Scoring Example

- DML and Scoring Algorithm

**See Also:**

"[DEFINESCORE](oracle-text-CONTAINS-query-operators.md)" and "[DEFINEMERGE](oracle-text-CONTAINS-query-operators.md)" for information about user-defined scoring

### F.1 Scoring Algorithm for Word Queries

To calculate a relevance score for a returned document in a word query, Oracle Text uses an inverse frequency algorithm based on Salton's formula.

Inverse frequency scoring assumes that frequently occurring terms in a document set are noise terms, and so these terms are scored lower. For a document to score high, the query term must occur frequently in the document but infrequently in the document set as a whole.

The following table illustrates Oracle Text's inverse frequency scoring. The first column shows the number of documents in the document set, and the second column shows the number of terms in the document necessary to score 100.

This table assumes that only one document in the set contains the query term.

| Number of Documents in Document Set | Occurrences of Term in Document Needed to Score 100 |
|:------------------------------------|:----------------------------------------------------|
| 1                                   | 34                                                  |
| 5                                   | 20                                                  |
| 10                                  | 17                                                  |
| 50                                  | 13                                                  |
| 100                                 | 12                                                  |
| 500                                 | 10                                                  |
| 1,000                               | 9                                                   |
| 10,000                              | 7                                                   |
| 100,000                             | 6                                                   |
| 1,000,000                           | 5                                                   |

Note that the score varies, depending on the set size. For example, if only one document in the set contains the query term, and there are five documents in the set, then the term must occur 20 times in the document to score 100. If 1,000,000 documents are in the set, then the term can occur only 5 times in the document to score 100.

### F.2 Word Scoring Example

You have 5000 documents dealing with chemistry in which the term chemical occurs at least once in every document. The term chemical thus occurs frequently in the document set.

You have a document that contains 5 occurrences of chemical and 5 occurrences of the term hydrogen. No other document contains the term hydrogen. The term hydrogen thus occurs infrequently in the document set.

Because chemical occurs so frequently in the document set, its score for the document is lower with respect to hydrogen, which is infrequent is the document set as a whole. The score for hydrogen is therefore higher than that of chemical. This is so even though both terms occur 5 times in the document.

**Note:**

Even if the relatively infrequent term hydrogen occurred 4 times in the document, and chemical occurred 5 times in the document, the score for hydrogen might still be higher, because chemical occurs so frequently in the document set (at least 5000 times).

Inverse frequency scoring also means that adding documents that contain hydrogen lowers the score for that term in the document, and adding more documents that do not contain hydrogen raises the score.

### F.3 DML and Scoring Algorithm

Because the scoring algorithm is based on the number of documents in the document set, inserting, updating or deleting documents in the document set is likely to change the score for any given term before and after DML.

If DML is heavy, you must optimize the index. Perfect relevance ranking is obtained by running a query right after optimizing the index.

If DML is light, Oracle Database still gives fairly accurate relevance ranking.

In either case, you must synchronize the index with CTX_DDL.[SYNC_INDEX](CTX_DDL-package.md).

**See Also:**

"[SYNC_INDEX](CTX_DDL-package.md)"
