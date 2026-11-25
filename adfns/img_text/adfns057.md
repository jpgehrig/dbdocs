# Description of the illustration adfns057.eps

1.  MT Scope begins the main transaction, MTx inserts the buy order into a table.

2.  MTx invokes the autonomous transaction scope (AT Scope). When AT Scope begins, MT Scope suspends.

3.  ATx updates the audit table with customer information.

4.  MTx seeks to validate the order, finds that the selected item is unavailable, and therefore rolls back the main transaction.
