# Description of the illustration adfns056.eps

A main transaction scope (MT Scope) begins the main transaction, MTx. MTx invokes the first autonomous transaction scope (AT Scope1). MTx suspends. AT Scope 1 begins the transaction Tx1.1.

1.  AT Scope 1 commits or rolls back Tx1.1, then ends MTx resumes.

2.  MTx invokes AT Scope 2. MT suspends, passing control to AT Scope 2, which initially is performing queries.

3.  AT Scope 2 then begins Tx2.1 by, say, doing an update. AT Scope 2 commits or rolls back Tx2.1.

4.  Later, AT Scope 2 begins a second transaction, Tx2.2, then commits or rolls it back.

5.  AT Scope 2 performs a few queries, then ends, passing control back to MTx.

6.  MTx invokes AT Scope 3. MTx suspends, AT Scope 3 begins.

7.  AT Scope 3 begins Tx3.1, which in turn, invokes AT Scope 4. Tx3.1 suspends, AT Scope 4 begins.

8.  AT Scope 4 begins Tx4.1, commits or rolls it back, then ends. AT Scope 3 resumes.

9.  AT Scope 3 commits or rolls back Tx3.1, then ends. MTx resumes.

10. MT Scope commits or rolls back MTx, then ends.
