Run these commands on the source and destination databases to find character sets that are compatible.

    SQL> show parameter CHARACTER

    NAME                    TYPE        VALUE
    ---------               ---------   ----------
    nls_numeric_characters  string

    SQL> select * from database_properties where PROPERTY_NAME in ('NLS_CHARACTERSET','NLS_NCHAR_CHARACTERSET');

    PROPERTY_NAME            PROPERTY_VALUE DESCRIPTION
    -----------------------  ------------   ------------------
    NLS_NCHAR_CHARACTERSET   AL16UTF16      NCHAR Character set
    NLS_CHARACTERSET         WE8MSWIN1252   Character set

    SQL> select * from nls_database_parameters where parameter like '%SET%';

    PROPERTY_NAME              VALUE
    ------------------------   ---------
    NLS_NCHAR_CHARACTERSET     AL16UTF16
    NLS_CHARACTERSET           WE8MSWIN1252

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
