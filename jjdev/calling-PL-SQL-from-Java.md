Java Database Connectivity (JDBC) enable you to call PL/SQL stored functions and procedures. For example, you want to call the following stored function, which returns the balance of a specified bank account:

    FUNCTION balance (acct_id NUMBER) RETURN NUMBER IS
    acct_bal NUMBER;
    BEGIN
    SELECT bal INTO acct_bal FROM accts
    WHERE acct_no = acct_id;
    RETURN acct_bal;
    END;

In a JDBC program, a call to the `balance` function can be written as follows:

    ...
    CallableStatement cstmt = conn.prepareCall("{? = CALL balance(?)}");
    cstmt.registerOutParameter(1, Types.FLOAT);
    cstmt.setInt(2, acctNo);
    cstmt.executeUpdate();
    float acctBal = cstmt.getFloat(1);
    ...
