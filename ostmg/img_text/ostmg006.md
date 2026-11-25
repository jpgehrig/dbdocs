This image shows the hierarchical structure of the folders inside /sys/asm. It shows a folder tree with /sys/asm at the top.

Underneath /sys/asm are two folders that represent the two disk groups, DATA and RECOVERY. Under each of the disk group folders are two folders representing two different databases, HR and MFG. Under each MFG folder are some file type folders, and under the file type folders, finally, come the files.

It is implied that the structure under the MFG database folders is duplicated under the HR database folders. The file type folders in the DATA disk group are DATAFILE, TEMPFILE, CONTROLFILE, and ONLINELOG. The file type folders in the RECOVERY disk group are CONTROLFILE, ONLINELOG, and ARCHIVELOG. Notice that the CONTROLFILE and ONLINELOG files are mirrored by the database in both disk groups.
