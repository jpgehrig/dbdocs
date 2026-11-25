Learn how to manipulate ACLs using ORADIM.

To use ORADIM to manipulate ACL, enter:

    oradim    -ACL -setperm|-addperm|-removeperm  dbfiles|diag|registry  -USER username  -OBJTYPE file|dir|registry  -OBJPATH object-path  -RECURSE true|false [-HOST hostname]

For this command, note the following:

- `-ACL ` indicates that you are manipulating ACL on an object. This is a mandatory parameter.

- `-setperm | -addperm | -removeperm dbfiles | diag | registry-` indicates that you are setting, adding, or removing ACLs on the specified object.  `dbfiles` is for database files, `diag ` is for database, `oracle-base & logs` and `registry` is for registry key. Set one of these based on the object on which the ACL is set. This is a mandatory parameter.

- `-USER ``username` indicates the user for whom the ACLs are granted. This must not be essentially the service user of the current oracle home. This is a mandatory parameter.

- `-OBJTYPE file|dir|registry` Set the object type to `file/dir/registry` based on the object on which the ACLs are set. This is a mandatory parameter.

- `-RECURSE true / false` indicates whether the ACL is applicable to all objects within the specified object. This is a mandatory parameter.

- `-HOST hostname` This can be used to remotely set ACLs on the specified host. This is limited to the scope of what windows supports remotely. Another way of doing this is to use the windows allowed conventions without using the `-HOST` option.  For example , `\\<hostame>\c$\oracle\rdbms\admin\abc.txt`. This is optional.

To set ACL on a file named abc.txt, for example, enter:

`c:\> oradim -acl -setperm dbfiles -user winusr -objtype file -objpath c:\a.txt -recurse true`

To add ACL on a registry key, for example, enter:

`c:\>oradim -acl -addperm registry -USER wingen  -OBJTYPE registry -OBJPATH MACHINE\SOFTWARE\ORACLE\KEY_OraDB12Home1 -RECURSE true`

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
