You can move Oracle Cluster Registry (OCR) and voting files from Network File System (NFS) to Oracle Automatic Storage Management (Oracle ASM) disk groups.

1.  As the `grid` user, create the Oracle ASM disk group using ASMCA.
        $ ./asmca

    Follow the steps in the ASMCA wizard to create the Oracle ASM disk group, for example, `DATA`.
2.  Move the voting files to the Oracle ASM disk group you created:
        $ crsctl replace votedisk +DATA

    The output of this command is as follows:

        CRS-4256: Updating the profile
        Successful addition of voting disk 24c6d682874a4f1ebf54f5ab0098b9e4.
        Successful deletion of voting disk 1b5044fa39684f86bfbe681f388e55fb.
        Successfully replaced voting disk group with +DATA_DG_OCR_VDSK.
        CRS-4256: Updating the profile
        CRS-4266: Voting file(s) successfully replaced
3.  Check the status of Oracle Cluster Registry (OCR):
        $ ./ocrcheck

    The output of the command is as follows:

        Status of Oracle Cluster Registry is as follows :
                 Version                  :          4
                 Total space (kbytes)     :     409568
                 Used space (kbytes)      :       1380
                 Available space (kbytes) :     408188
                 ID                       :  288871063
                 Device/File Name         : /oradbocfs/storage/12101/ocr
                 Device/File integrity check succeeded
                 Cluster registry integrity check succeeded
4.  As the `root` user, move the OCR files to the Oracle ASM disk group you created:
        # ./ocrconfig -add +DATA
5.  Delete the Oracle Clusterware files from the NFS location:
        # ./ocrconfig -delete ocr_file_ path_previously_on_nfs

**Parent topic:** [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
