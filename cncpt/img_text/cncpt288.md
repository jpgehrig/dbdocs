# Description of the illustration cncpt288.eps

This figure shows how control flows from a main routine (MT) to an autonomous routine (AT) and back again.

The autonomous routine commits two transactions, AT1 and AT2, before control returns to the main routine. When control enters the executable section of the autonomous routine (BEGIN), the main routine suspends. When control exits the autonomous routine (END), the main routine resumes. COMMIT and ROLLBACK statements in an autonomous routine end the active transaction, but they do not end the autonomous routine.
