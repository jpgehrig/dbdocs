Oracle Database provides an annotated sample initialization parameter file with alternative values for initialization parameters.

These values and annotations are preceded by the comment signs (`#`), which prevent them from being processed. To activate a particular parameter, remove the preceding `#` sign. To clear a particular parameter, edit the initialization parameter file to add a comment sign. The sample file is called `initsmpl.ora` and is located in

    ORACLE_HOME\admin\sample\pfile.

If you installed a starter database, then the initialization parameter file used by the starter database is located in the same directory. You can use either `initsmpl.ora` or the starter database `init.ora` as a basis for creating a new Oracle Database initialization parameter file.

To use the sample file `initsmpl.ora` as part of the database creation:

1.  Rename the sample file `init.ora`.
2.  Edit this file to reflect the correct location of your database control files and the name of your database, as a minimum.

Here are two examples of activation and de-activation of alternative parameters. Several initialization parameters are specified with three different values to create a small, medium, or large System Global Area, respectively. The parameter that creates a small SGA is active in this first example:

      db_block_buffers = 200  # SMALL
    # db_block_buffers = 550  # MEDIUM
    # db_block_buffers = 3200 # LARGE

To create a medium-sized SGA, comment out the small parameter definition and activate the medium parameter definition. Edit the initialization parameter file as in this second example:

    # db_block_buffers = 200  # SMALL
      db_block_buffers = 550  # MEDIUM
    # db_block_buffers = 3200 # LARGE

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
