## 13.4 AUTONOMOUS_TRANSACTION Pragma

The `AUTONOMOUS_TRANSACTION` pragma marks a routine as autonomous; that is, independent of the main transaction.

In this context, a routine is one of these:

- Schema-level (not nested) anonymous PL/SQL block

- Standalone, package, or nested subprogram

- Method of an ADT

- Noncompound trigger

### Topics

- Syntax

- Examples

- Related Topics

### Syntax

### autonomous_trans_pragma ::=

![Description of autonomous_trans_pragma.eps follows](img/autonomous_trans_pragma.gif)
[Description of the illustration autonomous_trans_pragma.eps](img_text/autonomous_trans_pragma.md)

### Examples

- [Example 6-43](autonomous-transactions.md), "Declaring Autonomous Function in Package"

- [Example 6-44](autonomous-transactions.md), "Declaring Autonomous Standalone Procedure"

- [Example 6-45](autonomous-transactions.md), "Declaring Autonomous PL/SQL Block"

- [Example 6-46](autonomous-transactions.md), "Autonomous Trigger Logs INSERT Statements"

- [Example 6-47](autonomous-transactions.md), "Autonomous Trigger Uses Native Dynamic SQL for DDL"

- [Example 6-48](autonomous-transactions.md), "Invoking Autonomous Function"

### Related Topics

- [Pragmas](lexical-units.md)

- [Autonomous Transactions](autonomous-transactions.md)
