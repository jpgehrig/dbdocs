On HP-UX platforms only, complete the following procedure to set external jobs ownership to the low-privilege user `extjob`:

1.  Log on as `root`.
2.  Change directory to the Oracle Database Oracle home:
        # cd $ORACLE_HOME/rdbms/admin/
3.  Open `externaljob.ora` with a text editor, and find the parameters `run_user` and `run_group`.
4.  Set `run_user` to the external jobs user (`extjob`), and set `run_group` to a low-privileged group, such as `other`. For example:
        run_user=extproc
        run_group=other
5.  Save the file.
    **Note:**

    Modify `externaljob.ora` only as `root`.

**Parent topic:** [Required Postinstallation Tasks](required-postinstallation-tasks.md)
