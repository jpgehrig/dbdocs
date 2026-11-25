This is partly described in the text. In addition, it illustrates:

- rules Sales(Prod1, 2002) = Sales(Prod1, 2000) + Sales(Prod1, 2001)

- rules Sales(Prod2, 2002) = Sales(Prod2, 2000) + Sales(Prod2, 2001)

Then the output of the MODEL clause:

- country values of A, A, A, A, B, B, B, B as original data product values of Prod1, Prod1, Prod1, Prod2, Prod1, Prod1, Prod2, Prod2, as original data

- year values of 2000, 2001, 2000, 2001, 2000, 2001, 2000, 2001 as original data

- sales values of 10, 15, 12, 16, 21, 23, 28, 29 as original data

- country values as rule results A, A, B, B

- product values as rule results Prod1, Prod2, Prod1, Prod2

- year values as rule results 2002, 2002, 2002, 2002

- sales values as rule results 25, 28, 44, 57
