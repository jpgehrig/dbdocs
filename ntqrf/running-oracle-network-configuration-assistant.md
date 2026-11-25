Oracle Net Configuration Assistant is a graphical, wizard-based tool used to configure and manage Oracle Network configurations.

To start Oracle Net Configuration Assistant:

1.  Click Start, then click All Programs.
2.  Click Oracle - HOMENAME, Configuration and Migration Tools, then Net Configuration Assistant.
3.  Select the Directory Usage Configuration option, then click Next.
4.  Select Directory Type Microsoft Active Directory, then click Next.
    **Note:**

    The Microsoft Active Directory configuration option is only available in the Windows version of Oracle Net Configuration Assistant.
5.  Select the option to configure the directory server for Oracle usage and to create or upgrade the Oracle Schema and Context, then click Next.
6.  Enter the Active Directory host name, then click Next.
7.  Select the option to upgrade the Oracle Schema, then click Next.
    The next page must denote successful Directory configuration.

        Directory usage configuration complete!
        The distinguished name of your default Oracle Context is:
        cn=OracleContext,DC=home,DC=com
8.  Click Next, then click Finish.
9.  The earlier message may only denote partial success:
        The Assistant is unable to create or upgrade the Oracle Schema
        for the following reason: ConfigException: Oracle Schema creation
        was successful, but Active Directory Display Specifier creation
        failed.oracle.net.config.ConfigException; TNS-04420: Problem
        running LDAPMODIFY

    Click OK, then click Finish.
10. If you receive the preceding error, disregard the message and rerun Oracle Net Configuration Assistant using the originally supplied values.
    The wizard must complete denoting successful Directory configuration:

        Directory usage configuration complete!
        The distinguished name of your default Oracle Context is:
        cn=OracleContext,DC=home,DC=com

    Click Next, then click Finish.

**Parent topic:** [Creating an OracleContext](creating-an-oraclecontext.md)
