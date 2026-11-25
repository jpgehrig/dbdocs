# Description of the illustration adfns039.eps

    DEPNO   DNAME       LOC
    -----   ---------   --------
    20      RESEARCH    DALLAS
    30      SALES       NEW YORK
    40      MARKETING   BOSTON
    -       UNIQUE      -

UNIQUE is a constraint that means no row can duplicate a value in the constraint's column.)

    DEPNO   DNAME   LOC        COMMENTS
    -----   -----   --------   --------
    50      SALES   NEW YORK   1
    60      N/A     BOSTON     2

1.  This row violates the UNIQUE key constraint, because SALES is already present in another row; therefore, it is not allowed in the table.

2.  This row is allowed because a NULL value is entered for the DNAME column; however, if a NOT NULL constraint is defined on the DNAME column, this row is not allowed.
