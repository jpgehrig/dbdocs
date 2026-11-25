You must create Oracle schema objects to use net directory naming features with Active Directory.

Schema objects are sets of rules for Oracle Net Services and Oracle Database entries and their attributes stored in Active Directory. The following restrictions apply to creating Oracle schema objects to use with Active Directory:

- Only one Oracle schema object can be created for each forest.

- The Windows server domain controller must be the operations master that allows schema updates. See your operating system documentation for instructions.

To create an Oracle schema object:

1.  Log in as a member of Schema Administrator group or as a member who has rights to update the schema into schema master domain. The logged in client computer must be a part of the schema master domain. Schema master domain administrators are schema administrators by default.

2.  Use Oracle Net Configuration Assistant to create the Oracle schema object. You can create your schema object during or after database installation.

If the Active Directory display is not configured to accept all 24 default languages, then Oracle schema object creation can fail while Oracle Net Configuration Assistant is configuring Active Directory as the directory server. Before running Oracle Net Configuration Assistant to complete directory access configuration, verify that the display specifiers for all 24 languages are populated by entering the following at the command prompt:

    ldifde -p OneLevel -d cn=DisplaySpecifiers,cn=Configuration,domain context -f
    temp file

For this command, note the following:

- `domain` `context` is the domain context for this Active Directory server.

  For example, `dc=example`,`dc=com`.

- `temp` `file` is a file where you want to put the output.

If the command reports that fewer than 24 entries were found, then you can still use Oracle Net Configuration Assistant. However, the report indicates that the Oracle schema object creation failed, rather than simply reporting that display specifiers for some languages were not created.

When the Oracle Net Configuration Assistant report shows failure due to less than 24 entries found, create display specifiers manually.

### Creating Display Specifiers Manually

When Oracle Net Configuration Assistant creates the Oracle schema object in Active Directory, the display specifiers for Oracle entries are not created. This means you cannot view Oracle database entries in Active Directory interfaces.

You can manually add these entries into Active Directory after the Oracle schema object has been created by doing the following, using the same Windows user identification you used when creating the Oracle schema object with Net Configuration Assistant:

1.  Open a command shell.
2.  Change directory to `ORACLE_HOME``\ldap\schema\ad`.
3.  Copy `adDisplaySpecifiers_us.sbs` to `adDisplaySpecifiers_us.ldif`.
4.  Copy `adDisplaySpecifiers_other.sbs` to `adDisplaySpecifiers_other.ldif`.
5.  Edit each of these `.ldif` files, replacing all occurrences of `%s_AdDomainDN%` with the domain DN for the specific Active Directory into which you want to load the display specifiers (for example, `dc=example,dc=com`).
6.  Run the following commands:
        ldapmodify -h ad hostname -Z -f adDisplaySpecifiers_us.ldif
        ldapmodify -h ad hostname -Z -f adDisplaySpecifiers_other.ldif

    where `ad hostname` is the host name of the Active Directory domain controller to which you want to load the display specifiers.

**Related Topics**

- [About Automatic Discovery of Directory Servers](about-automatic-discovery-of-directory-servers.md)

**Parent topic:** [Overview of Requirements for Using Oracle Database with Active Directory](overview-of-requirements-for-using-oracle-database-with-active-directory.md)
