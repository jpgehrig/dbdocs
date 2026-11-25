To check if your operating system has the required Oracle Solaris 11 packages for installation, run the following commands:

1.  To determine if the required packages are installed on Oracle Solaris 11:
    `# /usr/bin/pkg verify [-Hqv] ``[pkg_pattern ...]`
    - The `-H` option omits the headers from the verification output.

    - The `-q` option prints nothing but return failure if any fatal errors are found.

    - The `-v` option includes informational messages regarding packages.

    If a package that is required for your system architecture is not installed, then download and install it from My Oracle Support:

    [https://support.oracle.com](https://support.oracle.com/)

**Note:**

There may be more recent versions of packages listed installed on the system. If a listed patch is not installed, then determine if a more recent version is installed before installing the version listed. Refer to your operating system documentation for information about installing packages.

**Related Topics**

- [The Adding and Updating Oracle Solaris Software Packages guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/sscli&id=AUOSS)
- [Oracle Solaris 11 Product Documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/sscli&id=otn_solaris11_doc)
- [My Oracle Support note 1021281.1](https://support.oracle.com/rs?type=doc&id=1021281.1)

**Parent topic:** [Checking the Software Requirements for Oracle Solaris](checking-the-software-requirements-for-oracle-solaris.md)
