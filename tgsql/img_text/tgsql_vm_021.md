# Description of the illustration tgsql_vm_021.eps

This graphic shows a Production Database that contains the EXPORT_SYSTEM_STATS view. The view points to a staging table, which then points to a .dmp file. The arrow pointing to the file is labeled "Data Pump Export." The .dmp file points to another .dmp file. The arrow is labeled "Transport ftp, nfs." The .dmp file points to a staging table, which points to the IMPORT_SYSTEM_STATS view. The arrow is labeled "Data Pump Import." The table is in a Test Database.
