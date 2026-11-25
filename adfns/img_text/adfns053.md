# Description of the illustration adfns053.eps

This illustration shows a time line for two transactions, Transaction A (arbitrary) and Transaction B (serializable).

Transaction A issues an update that is too recent for Transaction B to see. Transaction B changes the other row in the same block, and sees its own changes. Transaction A creates a possible "phantom row." Uncommitted changes are invisible to Transaction B, so Transaction A commits, making changes visible to transactions that begin later.

Transaction B makes changes after Transaction A commits. Transaction B can see its own changes, but not the committed changes of Transaction A, so the attempt to update the row fails, after which Transaction B rolls back and retries.
