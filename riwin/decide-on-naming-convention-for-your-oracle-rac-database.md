## Decide on a Naming Convention to Use for Your Oracle RAC Database

The global database name for an Oracle RAC database must meet the naming requirements. The global database name consists of the database name and the domain name.

1.  Choose a name for your database that has the following characteristics:
    1.  Up to 30 characters in length
    2.  Begins with an alphabetic character
2.  Determine the domain name portion of the global database name, that satisfies these requirements:
    1.  Is up to 128 characters in length
    2.  Contains only alphabetic and numeric characters, and the period (.) character
3.  Determine the `ORACLE_SID` values for each instance.
    The maximum number of characters you can use for the SID prefix is 8 characters. Oracle Database Configuration Assistant uses the SID prefix to generate a unique value for the variable `ORACLE_SID` for each instance. The SID prefix must begin with an alphabetic character.

**Parent topic:** [Tasks to Complete Before Using DBCA to Create an Oracle RAC Database](tasks-to-complete-before-using-dbca-to-create-a-rac-database.md)
