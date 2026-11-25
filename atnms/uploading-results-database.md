Use the list of commands in this section to upload results to the database.

### Syntax

    [-setdbupload all|list of variable names]
    [-unsetdbupload all|list of variable names]
    [-checkdbupload]
    [-getdbupload]
    [-checkfaileduploads]
    [-uploadfailed all|list of failed collections]

### Parameters

Table A-4 Uploading Results to Database

| Option                                           | Description                                                                                                                                                                                                          |
|:-------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-setdbupload all|``variable_names`              | Sets the values in the wallet to upload health check run results to the database.<br>`all`: Sets all the variables in the wallet.<br>variable_names: Specify a comma-delimited list of variables to set.             |
| `-unsetdbupload all|``variable_names`            | Unsets the values in the wallet to upload health check run results to the database.<br>`all`: Unsets all the variables in the wallet.<br>variable_names: Specify a comma-delimited list of variables to unset.       |
| `-checkdbupload`                                 | Checks if the variables are set correctly for uploading the health check run results to the database.                                                                                                                |
| `-getdbupload`                                   | Prints the variables with their values from wallet for uploading the health check run result to the database.                                                                                                        |
| `-checkfaileduploads`                            | Reports any failed collection uploads.                                                                                                                                                                               |
| `-uploadfailed all|``list of failed collections` | Reattempts to upload one or more failed collection uploads.<br>`all`: Reattempts to upload all the filed collection uploads.<br>list of failed collections: Specify a comma-delimited list of collections to upload. |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
