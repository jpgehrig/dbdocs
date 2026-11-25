# Description of the illustration olsag004.png

This illustration depicts how Oracle Label Security operates when a user issues a SQL request. First, Oracle12c checks the DAC privileges to make sure the user has the SELECT privilege on the table. It then checks to see if a VPD policy has been attached to the table. If so, the VPD SQL modification (WHERE clause) is added to the original SQL statement, and the set of rows to which the user has access is determined. Then Oracle Label Security checks the labels on each row in this set, to determine the subset of rows to which the user has access.
