## Setting External Jobs Ownership for HP-UX Installations

On HP-UX platforms only, set external jobs ownership to a low-privilege user.

Complete the following procedure to set external jobs ownership to the low-privilege user `extjob`:

1.  Log in as `root`.
2.  Go to the Oracle Database Oracle home directory:
        # cd $ORACLE_HOME/rdbms/admin/
3.  Open `externaljob.ora` with a text editor, and find the parameters run_userand run_group.
    Modify `externaljob.ora` only as `root`.
4.  Set run_user to the external jobs user (`extjob`), and set run_group to a low-privileged group, such as `other`, for example:
        run_user=extproc
        run_group=other
5.  Save the file.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
