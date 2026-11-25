Handling of `root` passwords depends on whether you have installed the Expect utility.

Expect automates interactive applications such as Telnet, FTP, passwd, fsck, rlogin, tip, and so on.

### To handle root passwords:

1.  If you have installed the Expect utility, then specify the `root` password when you run the health checks for the first time.
    The Expect utility stores the password and uses the stored password for subsequent sessions.

    The Expect utility prompts you to check if the `root` password is same for all the remote components such as databases, switches, and so on.
2.  Specify the password only once if you have configured the same `root` password for all the components.
    If `root` password is not same for all the components, then the Expect utility prompts you to validate `root` password every time you run the health checks.

    If you enter the password incorrectly or the password is changed between the time it is entered and used, then Oracle ORAchk and Oracle EXAchk:

    - Notify you

    - Skip relevant checks
3.  Run the health checks after resolving the issues.
    If Oracle ORAchk and Oracle EXAchk skip any of the health checks, then the tools log details about the skipped checks in the report output.

**Related Topics**

- [Expect - Expect - Home Page](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/atnms&id=expect_utility_download)

**Parent topic:** [Configuring Oracle ORAchk and Oracle EXAchk](config-orachk-and-exachk.md)
