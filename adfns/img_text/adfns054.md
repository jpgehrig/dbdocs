# Description of the illustration adfns054.eps

This illustration shows Transaction A and Transaction B. Transaction A has a read operation followed by an insert operation. Transaction B has a read operation followed by a delete operation. The read issued by Transaction A does not prevent Transaction B from deleting the parent row, and Transaction B's query for child rows does not prevent Transaction A from inserting child rows.
