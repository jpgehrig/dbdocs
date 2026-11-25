# Description of the illustration lnpls028.eps

This figure shows how control flows from a main transaction (MT) to an autonomous transaction (AT) and back again.

The autonomous transaction commits two transactions, AT1 and AT2, before control returns to the main transaction. When control enters the executable section of the autonomous transaction (BEGIN), the main transaction suspends. When control exits the autonomous transaction (END), the main transaction resumes. COMMIT and ROLLBACK statements in an autonomous transaction end the active transaction, but they do not end the autonomous transaction.
