## TO_NCHAR (number)

### Syntax

### to_nchar_number::=

![Description of to_nchar_number.eps follows](img/to_nchar_number.gif)
[Description of the illustration to_nchar_number.eps](img_text/to_nchar_number.md)

### Purpose

`TO_NCHAR` (number) converts `n` to a string in the national character set. The value `n` can be of type `NUMBER`, `BINARY_FLOAT`, or `BINARY_DOUBLE`. The function returns a value of the same type as the argument. The optional `fmt` and `'nlsparam'` corresponding to `n` can be of `DATE`, `TIMESTAMP`, `TIMESTAMP` `WITH` `TIME` `ZONE`, `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`, `INTERVAL` `MONTH` `TO` `YEAR`, or `INTERVAL` `DAY` `TO` `SECOND` data type.

**See Also:**

- "[Security Considerations for Data Conversion](Data-Type-Comparison-Rules.md)"

- Appendix C in [Oracle Database Globalization Support Guide](../nlspg/appendix-C-collation-derivation-and-determination-rules-for-SQL-operations.md) for the collation derivation rules, which define the collation assigned to the character return value of this function

### Examples

The following example converts the `customer_id` values from the sample table `oe.orders` to the national character set:

    SELECT TO_NCHAR(customer_id) "NCHAR_Customer_ID"  FROM orders
       WHERE order_status > 9
       ORDER BY "NCHAR_Customer_ID";

    NCHAR_Customer_ID
    ----------------------------------------
    102
    103
    148
    148
    149
