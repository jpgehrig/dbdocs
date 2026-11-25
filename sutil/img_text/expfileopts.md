#

    expfileopts ::=

    [
    DIRECTORY = directory_object
    |DUMPFILE = [directory_object:]file_name
     [, [directory_object:]file_name] ...
    |FILESIZE = number_of_bytes
    | { LOGFILE = [directory_object:]file_name | NOLOGFILE = {YES | NO} }
    |PARFILE =  [directory_path] file_name]
    |REUSE_DUMPFILES = {YES | NO}
    ]
