# Description of the illustration cncpt025.eps

The image cncpt025.gif shows the SQL statement for the banking transaction example. The statement is divided into four blocks:

- Decrement Savings Account

- Increment Checking Account

- Record in Transaction Journal

- End Transaction

The SQL statement for the Decrement Savings Account is as follows:

    UPDATE savings_accounts
    SET balance = balance - 500
    WHERE account = 3209;

The SQL statement for the Increment Checking Account is as follows:

    UPDATE checking_accounts
    SET balance = balance + 500
    WHERE account =3208;

The SQL statement for Record in Transaction Journal is as follows:

    INSERT INTO journal VALUES
    (journal_seq.NEXTVAL, '1B'
    3209, 3208, 500),

The SQL statement for End Transaction is as follows:

    COMMIT WORK;
