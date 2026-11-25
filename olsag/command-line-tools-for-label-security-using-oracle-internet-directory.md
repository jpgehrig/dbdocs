Oracle Label Security provides command-line tools for using Oracle Internet Directory.

- About the Command-line Oracle Label Security Tools
  When you use Oracle Label Security with Oracle Internet Directory, you can create and alter label security attributes stored in the directory.
- Oracle Label Security Commands in Categories
  Oracle Label Security commands can be categorized according to policies, levels, groups, and so on.
- olsadmintool Command Reference
  The `olsadmintool` commands performs tasks such as adding enterprise users to administrative groups for an Oracle Label Security policy.
- Relating Parameters to Commands for olsadmintool
  You must follow a set of guidelines for using the `olsadmintool` parameters.
- Examples of Using the olsadmintool Utility
  You use the `olsadmintool` commands to set up Oracle Label Security in an Oracle Internet Directory environment.
- olsoidsync Command Reference
  The `olsoidsync` command pulls policy information from Oracle Internet Directory and populates the information in the database (bootstrapping).

**Parent topic:** [Appendixes](part4.md)

### C.1 About the Command-line Oracle Label Security Tools

When you use Oracle Label Security with Oracle Internet Directory, you can create and alter label security attributes stored in the directory.

The commands perform updates, inserts and deletes of entries in the directory and are implemented through a script named `olsadmintool`, which you call from `$ORACLE_HOME/bin/olsadmintool`. In addition to the `olsadmintool`, you can perform bootstrap operations by using the `olsoidsync` command.

**Note:**

You can also use the graphical user interface provided by Oracle Enterprise Manager to manage Oracle Label Security. Detailed documentation can be found in Oracle Enterprise Manager help.

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

### C.2 Oracle Label Security Commands in Categories

Oracle Label Security commands can be categorized according to policies, levels, groups, and so on.

Table C-1 lists all the commands, in categories, with links to their explanations.

Some of these commands replace PL/SQL procedures that are used for the indicated purposes when Oracle Label Security is used without Oracle Internet Directory. Sites already using Oracle Label Security that add Oracle Internet Directory must replace the use of those PL/SQL procedures by switching to use these new commands instead.

Table C-1 Oracle Label Security Commands in Categories

| Command Category         | Command                        | Replaces PL/SQL Statement                              |
|:-------------------------|:-------------------------------|:-------------------------------------------------------|
| Policies                 | olsadmintool createpolicy      | `SA_SYSDBA.CREATE_POLICY`                              |
| Policies                 | olsadmintool alterpolicy       | `SA_SYSDBA.ALTER_POLICY`                               |
| Policies                 | olsadmintool droppolicy        | `SA_SYSDBA.DROP_POLICY`                                |
| Policies                 | olsadmintool addpolcreator     | None; new                                              |
| Policies                 | olsadmintool droppolcreator    | None; new                                              |
| Levels in a Policy       | olsadmintool createlevel       | `SA_COMPONENTS.CREATE_LEVEL`                           |
| Levels in a Policy       | olsadmintool alterlevel        | `SA_COMPONENTS.ALTER_LEVEL`                            |
| Levels in a Policy       | olsadmintool droplevel         | `SA_COMPONENTS`.`DROP_LEVEL`                           |
| Groups in a Policy       | olsadmintool creategroup       | `SA_COMPONENTS.CREATE_GROUP`                           |
| Groups in a Policy       | olsadmintool altergroup        | `SA_COMPONENTS.ALTER_GROUP`                            |
| Groups in a Policy       | olsadmintool altercompartent   | `SA_COMPONENTS.ALTER_GROUP_PARENT`                     |
| Groups in a Policy       | olsadmintool dropgroup         | `SA_COMPONENTS.DROP_GROUP`                             |
| Compartments in a Policy | olsadmintool createcompartment | `SA_COMPONENTS.CREATE_COMPARTMENT`                     |
| Compartments in a Policy | olsadmintool altercompartent   | `SA_COMPONENTS.ALTER_COMPARTMENT`                      |
| Compartments in a Policy | olsadmintool dropcompartment   | `SA_COMPONENTS.DROP_COMPARTMENT`                       |
| Data Labels              | olsadmintool createlabel       | `SA_LABEL_ADMIN.CREATE_LABEL`                          |
| Data Labels              | olsadmintool alterlabel        | `SA_LABEL_ADMIN.ALTER_LABEL`                           |
| Data Labels              | olsadmintool droplabel         | `SA_LABEL_ADMIN.DROP_LABEL`                            |
| Users                    | olsadmintool adduser           | None; new                                              |
| Users                    | olsadmintool dropuser          | `SA_USER_ADMIN.DROP_USER_ACCESS`                       |
| Profiles                 | olsadmintool createprofile     | Replaces the use of several methods. <sup>Foot 1</sup> |
| Profiles                 | olsadmintool listprofile       | None; new                                              |
| Profiles                 | olsamindtool describeprofile   | None; new                                              |
| Profiles                 | olsadmintool dropprofile       | None; new                                              |
| Policy Administrators    | olsadmintool addadmin          | None; new                                              |
| Policy Administrators    | olsadmintool dropadmin         | None; new                                              |
| Auditing                 | olsadmintool audit             | `SA_AUDIT_ADMIN.AUDIT`                                 |
| Auditing                 | olsadmintool noaudit           | `SA_AUDIT_ADMIN.NOAUDIT`                               |
| Help                     | olsadmintool --help            | None; new                                              |

<sup>Footnote 1</sup>

Replaces several methods in `SA_USER_ADMIN`: `SET_LEVELS`, `SET_USER_PRIVILEGES`, and `SET_DEFAULT_LABEL`

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

### C.3 olsadmintool Command Reference

The `olsadmintool` commands performs tasks such as adding enterprise users to administrative groups for an Oracle Label Security policy.

You must run `olsadmintool` from the command line.

- About the olsadmintool Commands
  You run the `olsadmintool` commands from a command prompt and can use special characters to perform specific operations.
- olsadmintool addadmin
  The `olsadmintool addadmin` command adds an enterprise user to the administrative group for a policy.
- olsadmintool addpolcreator
  The `olsadmintool addpolcreator` command enables the specified user to create policies.
- olsadmintool adduser
  The `olsadmintool adduser` command adds an enterprise user to a profile within a policy.
- olsadmintool altercompartent
  The `olsadmintool altercompartment` command changes the long name of a compartment.
- olsadmintool altergroup
  The `olsadmintool altergroup` command changes the long name for a group component or parent group.
- olsadmintool altergroupparent
  The `olsadmintool altergroupparent` command changes or removes the parent group of a group.
- olsadmintool alterlabel
  The `olsadmintool alterlabel` command changes the character string defining the label associated with a label tag.
- olsadmintool alterlevel
  The `olsadmintool alterlevel` command changes the long name of a level.
- olsadmintool alterpolicy
  The `olsadmintool alterpolicy` command alters the options of a policy.
- olsadmintool audit
  The `olsadmintool olsadmintool audit` command sets the audit options for a policy.
- olsadmintool createcompartment
  The `olsadmintool createcompartment` command creates a new compartment component.
- olsadmintool creategroup
  The `olsadmintool creategroup` command creates a new group component.
- olsadmintool createlabel
  The `olsadmintool createlabel` command creates a valid data label.
- olsadmintool createlevel
  The `olsadmintool createlevel` command creates a new level component.
- olsadmintool createprofile
  The `olsadmintool createprofile` command creates a new profile.
- olsadmintool createpolicy
  The `olsadmintool createpolicy` command creates a policy.
- olsamindtool describeprofile
  The `olsadmintool describeprofile` command enables you to see the contents of a policy profile.
- olsadmintool dropadmin
  The `olsadmintool dropadmin` command removes an enterprise user from the administrative group of a policy.
- olsadmintool dropcompartment
  The `olsadmintool dropcompartment` command removes a compartment component.
- olsadmintool dropgroup
  The `olsadmintool dropgroup` command removes a group component.
- olsadmintool droplabel
  The `olsadmintool droplabel` command drops a label from the policy.
- olsadmintool droplevel
  The `olsadmintool droplevel` command removes a level component from a specified policy.
- olsadmintool droppolicy
  The `olsadmintool droppolicy` command drops a policy.
- olsadmintool dropprofile
  The `olsadmintool dropprofile` command removes the specified profile.
- olsadmintool droppolcreator
  The `olsadmintool droppolcreator` command cancels the ability of the specified user to create policies.
- olsadmintool dropuser
  The `olsadmintool dropuser` command drops a user from the specified profile in the specified policy.
- olsadmintool --help
  The `olsadmintool` `command_name` `-- help` command displays help information about the specified command.
- olsadmintool listprofile
  The `olsadmintool listprofile` command to see a list of all profiles in a given policy.
- olsadmintool noaudit
  The `olsadmintool noaudit` command cancels the audit options for a policy.

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

#### C.3.1 About the olsadmintool Commands

You run the `olsadmintool` commands from a command prompt and can use special characters to perform specific operations.

In the `olsadmintool` commands, some parameters are optional, which is indicated by enclosing such a parameter within brackets. The two most common examples are `[ -b ``admin context` `]` and `[-p` `port``]`, indicating that it is optional to specify either the administrative context for the command or the port through which to connect to Oracle Internet Directory. (Default port is 389.)

The use of two dashes (`--`, no space) is required for all parameters other than `b`, `h`, `p`, `D`, and `w`, which are preceded by a single dash. The double dash indicates the need to specify the full or long version of the name or parameter being used. If any such name or parameter contains spaces, it must be enclosed by double quotation marks, for example, "this is an extremely long name or parameter."

**Parent topic:** olsadmintool Command Reference

#### C.3.2 olsadmintool addadmin

The `olsadmintool addadmin` command adds an enterprise user to the administrative group for a policy.

This enables the user to create, modify, or delete the specified policy's metadata. You must provide the policy name and the new administrator's DN. This group should contain only enterprise users.

##### Syntax

    olsadmintool addadmin --polname policy_name --admindn admin_DN
    [ -b admin_context] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool addadmin --polname defense --admindn "cn=scott,c=us"
    -h sales_west -D cn=lbacsys
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.3 olsadmintool addpolcreator

The `olsadmintool addpolcreator` command enables the specified user to create policies.

You must provide the DN for the user.

##### Syntax

    olsadmintool addpolcreator --userdn user_DN
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Examples

    olsadmintool addpolcreator --userdn "cn=scott" -h sales_west -D cn=lbacsys
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.4 olsadmintool adduser

The `olsadmintool adduser` command adds an enterprise user to a profile within a policy.

You must provide the profile and policy names and the user DN.<sup>Foot 2</sup> Enterprise users are normal Oracle Internet Directory users with the additional capability of connecting to the database. Users added to a profile must be enterprise users.

##### Syntax

    olsadmintool adduser --polname policy_name --profname profile_name --userdn
    enterprise_user_DN[ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool adduser --polname tradesecret --profname topsales --userdn "cn=perot"
    -b "cn=EDS" -h ford -p 1890 -D cn=lbacsys
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.5 olsadmintool altercompartent

The `olsadmintool altercompartment` command changes the long name of a compartment.

You must provide the name of the policy, the short name of the compartment, and the new long name of the compartment.

##### Syntax

    olsadmintool altercompartment --polname policy_name --shortname
    short_compartment_name --longname new_long_compartment_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool altercompartment --polname defense --shortname A --longname "Allied
    Forces" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.6 olsadmintool altergroup

The `olsadmintool altergroup` command changes the long name for a group component or parent group.

You must provide the name of the policy, the short name of the group, and the long name of the group.

##### Syntax

    olsadmintool altergroup --polname policy_name --shortname short_group_name
    --longname "new_long_group_name"
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool altergroup --polname defense --shortname US --longname "United States
    of America"  -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.7 olsadmintool altergroupparent

The `olsadmintool altergroupparent` command changes or removes the parent group of a group.

You must provide the name of the policy, the short name of the group, and either the short name of the parent group or the `clearparent` flag, but not both.

##### Syntax

    olsadmintool altergroupparent --polname policy_name --shortname
    short_group_name [--parentname new_parent_group_name ] [--clearparent]
    --longname "new_long_group_name" [--parentname new_short_group_name ]
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Examples

    olsadmintool altergroupparent --polname defense --shortname US --parentname
    "Earth" -h sales_west -p 5678 -D cn=defense_admin
    Enter bind password: bind_password

    olsadmintool altergroupparent --polname defense --shortname US --clearparent
    -h sales_west -p 5678 -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.8 olsadmintool alterlabel

The `olsadmintool alterlabel` command changes the character string defining the label associated with a label tag.

You must provide the policy name, the numeric tag of the label, and the new character string representing the label.

##### Syntax

    olsadmintool alterlabel --polname policy_name --tag tag_number
    --value new_label_value [ -b admin_context ] -h OID_host [-p port]
    -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool alterlabel --polname defense --tag 100 --value "TS:A:US" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.9 olsadmintool alterlevel

The `olsadmintool alterlevel` command changes the long name of a level.

You must provide the name of the policy, the short name of the level, and the new long name of the level.

##### Syntax

    olsadmintool alterlevel --polname policy_name --shortname short_level_name
    --longname "new_long_level_name"
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool alterlevel --polname defense --shortname TS
    --longname "VERY TOP SECRET" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.10 olsadmintool alterpolicy

The `olsadmintool alterpolicy` command alters the options of a policy.

You must provide the name of the policy and the new options.

##### Syntax

    olsadmintool alterpolicy --name policy_name --options new_options
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

In this specification:

- `new_options` can be any combination of the following entries: `INVERSE_GROUP`, `HIDE`, `LABEL_DEFAULT`, `LABEL_UPDATE`, `CHECK_CONTROL`, `READ_CONTROL`,`WRITE_CONTROL`,`INSERT_CONTROL`, `DELETE_CONTROL`, `UPDATE_CONTROL`, `ALL_CONTROL`, `NO_CONTROL`

##### Example

    olsadmintool alterpolicy --name defense --options "READ_CONTROL,INSERT_CONTROL"
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.11 olsadmintool audit

The `olsadmintool olsadmintool audit` command sets the audit options for a policy.

You must provide the policy name, the options to be audited, the type of audit, and the type of success to be audited.

##### Syntax

    olsadmintool audit --polname policy_name --options audit_option_name
    --type audit_option_type --success audit_success_type
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

In this specification:

- `audit_option `can be any combination of the following entries: `APPLY`, `REMOVE`, `SET`, `PRIVILEGE`

- `type` can be `session` or `access`

- `success` can be `successful`, `not successful`, or `both`

##### Example

    olsadmintool audit --polname defense --options "APPLY,PRIVILEGE" --type session
    --success success -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.12 olsadmintool createcompartment

The `olsadmintool createcompartment` command creates a new compartment component.

You must provide the name of the policy, the tag numeric value of the compartment, the short name of the compartment, and the long name of the compartment.

##### Syntax

    olsadmintool createcompartment --polname policy_name --tag tag_number
    --shortname short_compartment_name --longname <"long_compartment_name">
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool createcompartment --polname defense --tag 100 --shortname A
    --longname Alpha -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.13 olsadmintool creategroup

The `olsadmintool creategroup` command creates a new group component.

You must provide the name of the policy, the tag numeric value of the group, the short name of the group, the long name of the group, and the parent group name (optional).

##### Syntax

    olsadmintool creategroup --polname policy_name --tag tag_number
    --shortname short_group_name --longname <"long_group_name">
    [--parentname parent_group_name]
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool creategroup --polname defense --tag 55 --shortname US
    --longname "United States" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.14 olsadmintool createlabel

The `olsadmintool createlabel` command creates a valid data label.

You must provide the policy name, the numeric tag of the label to be created, and the character string representation of the label.

##### Syntax

    olsadmintool createlabel --polname policy_name --tag tag_number
    --value label_value
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool createlabel --polname defense --tag 100 --value "TS:A,B:US,CA"
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.15 olsadmintool createlevel

The `olsadmintool createlevel` command creates a new level component.

You must provide the name of the policy, the tag numeric value, the short name of the level, and the long name of the level.

##### Syntax

    olsadmintool createlevel --polname policy_name --tag tag_number
    --shortname short_level_name --longname <"long_level_name">
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool createlevel --polname defense --tag 100 --shortname TS
    --longname "TOP SECRET" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.16 olsadmintool createprofile

The `olsadmintool createprofile` command creates a new profile.

You must provide the policy name, the profile name, and either privileges, labels, or both privileges and labels. (A user profile can have either null label information or null privilege information, but not both null at the same time.) For labels, specify the maximum label users in this profile can use to read data, the maximum label users in this profile can use to write data, the minimum label users in this profile can use to write data, the default label for reading, the default row label for writing. For privileges, enclose in quotation markets list of privileges, separated by commas, for members of this profile.

##### Syntax

    olsadmintool createprofile --polname policy_name --profname profile_name
    --maxreadlabel max_read_label --maxwritelabel max_write_label
    --minwritelabel min_read_label --defreadlabel default_read_label
    --defrowlabel default_row_label --privileges privileges_separated_by_comma
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool createprofile --polname topsecret --profname topsales
    --maxreadlabel "TS:A,B:US,CA" --maxwritelabel "TS:A,B:US,CA"
    --minwritelabel "C" --defreadlabel "TS:A,B:US,CA"
    --defrowlabel "C:A,B:US,CA"
    --privileges "READ,COMPACCESS,WRITEACROSS"
    -b EDS -h ford -p 1890 -D cn=lbacsys
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.17 olsadmintool createpolicy

The `olsadmintool createpolicy` command creates a policy.

You must provide the name of the policy, the name of its label column, and the options.

##### Syntax

    olsadmintool createpolicy --name policy_name --colname column_name
    --options options_separated_by_commas
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

In this specification:

- `new_options `can be any combination of the following entries: `INVERSE_GROUP`, `HIDE`, `LABEL_DEFAULT`, `LABEL_UPDATE`, `CHECK_CONTROL`, `READ_CONTROL`, `WRITE_CONTROL`,`INSERT_CONTROL`, `DELETE_CONTROL`, `UPDATE_CONTROL`, `ALL_CONTROL`, `NO_CONTROL`

##### Example

    olsadmintool createpolicy --name defense --colname defense_col
    --options "READ_CONTROL,UPDATE_CONTROL" -h sales_west -p 389 -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.18 olsamindtool describeprofile

The `olsadmintool describeprofile` command enables you to see the contents of a policy profile.

You must provide the policy name and the name of the profile.

##### Syntax

    olsadmintool describeprofile --polname policy_name --profname profile_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool describeprofile --polname defense --profname contractors
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.19 olsadmintool dropadmin

The `olsadmintool dropadmin` command removes an enterprise user from the administrative group of a policy.

This means that the user is no longer able to create, modify, or delete the specified policy's metadata. You must provide the policy name and the DN of the administrator to be removed from the administrative group.

##### Syntax

    olsadmintool dropadmin --polname policy_name --admindn admin_DN
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool dropadmin --polname defense --admindn "cn=scott,c=us"
    -h sales_west -D cn=lbacsys
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.20 olsadmintool dropcompartment

The `olsadmintool dropcompartment` command removes a compartment component.

You must provide the name of the policy and the short name of the compartment.

##### Syntax

    olsadmintool dropcompartment --polname policy_name
    --shortname short_compartment_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool dropcompartment --polname defense --shortname A
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.21 olsadmintool dropgroup

The `olsadmintool dropgroup` command removes a group component.

You must provide the policy name and the short group name.

##### Syntax

    olsadmintool dropgroup --polname policy_name --shortname short_group_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool dropgroup --polname defense --shortname US
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.22 olsadmintool droplabel

The `olsadmintool droplabel` command drops a label from the policy.

You must provide the policy name and the string representation of the label.

##### Syntax

    olsadmintool droplabel --polname policy_name --value label_value
    -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool droplabel --polname defense --value "TS:A:US"
    h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.23 olsadmintool droplevel

The `olsadmintool droplevel` command removes a level component from a specified policy.

You must provide the name of the policy and the short name of the level.

##### Syntax

    olsadmintool droplevel --polname policy_name --shortname short_level_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool droplevel --polname defense --shortname TS
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.24 olsadmintool droppolicy

The `olsadmintool droppolicy` command drops a policy.

You must provide the name of the policy to be dropped. For directory-enabled installations of Oracle Label Security, refer to [Subscription of Policies in Directory-Enabled Label Security](oracle-label-security-using-oracle-internet-directory.md).

##### Syntax

    olsadmintool droppolicy --name policy_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool droppolicy --name defense -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.25 olsadmintool dropprofile

The `olsadmintool dropprofile` command removes the specified profile.

You must provide the policy name and the name of the profile to be dropped.

**Note:**

Dropping a profile removes the authorization on that policy for all the users in the dropped profile. The users will be unable to see data protected by that policy.

##### Syntax

    olsadmintool dropprofile --polname policy_name --profname profile_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool dropprofile --name defense --profname employees
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.26 olsadmintool droppolcreator

The `olsadmintool droppolcreator` command cancels the ability of the specified user to create policies.

You must provide the user's DN.

##### Syntax

    olsadmintool droppolcreator --userdn user_DN
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool droppolcreator --userdn "cn-scott,c=us"
    -b UA -h sales_west -p 1890 -D bind_DN
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.27 olsadmintool dropuser

The `olsadmintool dropuser` command drops a user from the specified profile in the specified policy.

You must provide the policy name, the name of the profile, and the DN of the user.

##### Syntax

    olsadmintool dropuser --polname policy_name --profname profile_name
    --userdn enterprise_user_DN
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool dropuser --polname defense --profname contractors
    --userdn "cn=hanssen,c=us" -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.28 olsadmintool --help

The `olsadmintool` `command_name` `-- help` command displays help information about the specified command.

##### Syntax

`olsadmintool` `command_name` `--help`

**Parent topic:** olsadmintool Command Reference

#### C.3.29 olsadmintool listprofile

The `olsadmintool listprofile` command to see a list of all profiles in a given policy.

You must provide the policy name.

##### Syntax

    olsadmintool listprofile --polname policy_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

##### Example

    olsadmintool listprofile --polname defense -b CIA
    -h sales_west -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

#### C.3.30 olsadmintool noaudit

The `olsadmintool noaudit` command cancels the audit options for a policy.

You must provide the policy name and the options that are no longer to be audited.

##### Syntax

    olsadmintool noaudit --polname policy_name --options audit_option_name
    [ -b admin_context ] -h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

In this specification:

- `audit_option_name `can be any combination of the following entries: `APPLY`, `REMOVE`, `SET`, `PRIVILEGE`

##### Example

    olsadmintool noaudit --polname defense --options "APPLY,PRIVILEGES" -h sales_west
    -D cn=defense_admin
    Enter bind password: bind_password

**Parent topic:** olsadmintool Command Reference

### C.4 Relating Parameters to Commands for olsadmintool

You must follow a set of guidelines for using the `olsadmintool` parameters.

- About Relating Parameters to Commands for olsadmintool
  All `olsadmintool` commands must specify connection parameters.
- Summaries of olsadmintool Parameters
  The `olsadmintool` has parameters that to accommodate different categories of need, such as policies, administration, and auditing.

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

#### C.4.1 About Relating Parameters to Commands for olsadmintool

All `olsadmintool` commands must specify connection parameters.

These parameters include the OID host, the bind DN, the bind password, and optionally, the port through which the connection to Oracle Internet Directory is to be made. The default port is 389.

All `olsadmintool` commands may specify, as needed, the subscriber/administrative-context using the` -b` flag.

The fact that specifying a parameter is optional, such as a port or an administrative context, is shown by enclosing the parameter within brackets. The two most common examples are `[ -b admin` `context``]` and `[-p` `port``]`.

Because every command must specify a host, bind DN, and password, and may, if needed, also specify an administrative context, Table C-2 uses the abbreviation CON to represent all of these connection parameters as a group:

    [ -b admin_context ] h OID_host [-p port] -D bind_DN
    Enter bind password: bind_password

**Parent topic:** Relating Parameters to Commands for olsadmintool

#### C.4.2 Summaries of olsadmintool Parameters

The `olsadmintool` has parameters that to accommodate different categories of need, such as policies, administration, and auditing.

Table C-2 summarizes the commands in several categories.

- Policies: creating, altering, or dropping policies or their components, that is, levels, groups, and compartments

- Data labels: creating, altering, or dropping them

- Administrators and policy creators: adding or dropping them

- Users: adding or dropping users from a profile

- Auditing options: setting the options for what to audit for a policy

- Profiles: creating, listing, describing, or dropping them

- Default read or row labels: setting them

In Table C-2 and Table C-3, the column headings show only the parameters, not the keywords that must precede them. For example, Table C-2 shows `policyname` and `column-name` as parameters for the `createpolicy` command, without showing the keywords that must precede them (`--name` and `--colname`).

Table C-2 explains the individual parameters that are used as column headings in the summaries of Table C-2 and Table C-3.

In all these tables:

- OptionsP means policy enforcement options, that is, any combination of the following entries, separated by a comma:

  - `INVERSE_GROUP`

  - `HIDE`

  - `LABEL_DEFAULT`

  - `LABEL_UPDATE`

  - `CHECK_CONTROL`

  - `READ_CONTROL`

  - `WRITE_CONTROL`

  - `INSERT_CONTROL`

  - `DELETE_CONTROL`

  - `UPDATE_CONTROL`

  - `ALL_CONTROL`

  - `NO_CONTROL`

- OptionsA means audit options, that is, any comma-separated combination of the following entries: ` SET`, ` APPLY`, ` REMOVE`, or `PRIVILEGE`.

Table C-2 Summary: olsadmintool Command Parameters

| Command Category         | Commands & Parameters                   | \-          | \-           | \-         | \-        | \-       | \-             |
|:-------------------------|:----------------------------------------|:------------|:-------------|:-----------|:----------|:---------|:---------------|
| Policies                 | Command                                 | policy name | column- name | optionsP   | CON       | \-       | \-             |
| a policy                 | `olsadmintool` `createpolicy`           | Required    | Required     | Required   | Required  | \-       | \-             |
| a policy                 | `olsadmintool` `alterpolicy`            | Required    | Omitted      | Required   | Required  | \-       | \-             |
| a policy                 | `olsadmintool` `droppolicy`             | Required    | Omitted      | Omitted    | Required  | \-       | \-             |
| Within a Policy, Create: | Command                                 | policy name | tag          | short name | long name | CON      |  parent name   |
| a level                  | olsadmintool `createlevel`              | Required    | Required     | Required   | Required  | Required | Omitted        |
| a group                  | olsadmintool `creategroup`              | Required    | Required     | Required   | Required  | Required | \[ Required \] |
| a compartment            | `olsadmintool` `createcompartment`      | Required    | Required     | Required   | Required  | Required | Omitted        |
| Within a Policy, Alter:  | Command                                 | \-          | \-           | \-         | \-        | \-       | \-             |
| a level                  | `olsadmintool` `alterlevel`             | Required    | Omitted      | Unused     | Unused    | Unused   | Omitted        |
| a group or group parent  | `olsadmintool` `altergroup`             | Required    | Omitted      | Required   | Required  | Required | Omitted        |
| a group or group parent  | `olsadmintool` `altergroupparent`       | Required    | Omitted      | Required   | Omitted   | Required | \[Required\]   |
| a group or group parent  | Command                                 | policy name | tag          | short name | long name | CON      |  parent name   |
| a compartment            | `olsadmintool` `altercompartment`       | Required    | Omitted      | Required   | Required  | Required | Omitted        |
| Within a Policy, Drop:   | Command                                 |             | \-           | \-         | \-        | \-       | \-             |
| level                    | `olsadmintool` `droplevel`              | Required    | Omitted      | Required   | Omitted   | Required | Omitted        |
| group                    | `olsadmintool` `dropgroup`              | Required    | Omitted      | Required   | Omitted   | Required | Omitted        |
| compartment              | `olsadmintool` `dropcompartment`        | Required    | Omitted      | Required   | Omitted   | Required | Omitted        |
| Data Labels              | Command                                 | policy name | tag          | value      | CON       | \-       | \-             |
| Create label             | `olsadmintool` `createlabel`            | Required    | Required     | Required   | Required  | \-       | \-             |
| Alter data label         | `olsadmintool` `alterlabel`             | Required    | Required     | Required   | Required  | \-       | \-             |
| Drop data label          | `olsadmintool` `droplabel`              | Required    | Omitted      | Required   | Required  | \-       | \-             |
| Policy Administrators    | Command                                 | policy name | userDN       | CON        | \-        | \-       | \-             |
| Add an Admin             | `olsadmintool` `addadmin`               | Required    | Required     | Required   | \-        | \-       | \-             |
| Drop an Admin            | `olsadmintool` `dropadmin`              | Required    | Required     | Required   | \-        | \-       | \-             |
| Policy Creation          | `olsadmintool` `addpolcreator`          | Omitted     | Required     | Required   | \-        | \-       | \-             |
| Policy Creation          | `olsadmintool droppolcreator`           | Omitted     | Required     | Required   | \-        | \-       | \-             |
| Users                    | Command                                 | policy name | profile name | userDN     | CON       | \-       | \-             |
| add a user               | `olsadmintool` `adduser`                | Required    | Required     | Required   | Required  | \-       | \-             |
| drop a user              | `olsadmintool dropuser`                 | Required    | Required     | Required   | Required  | \-       | \-             |
| Auditing                 | `olsadmintool` `audit`                  | Required    | optionsA     | type       | success   | CON      | \-             |
| auditing                 | `olsadmintool` `noaudit`                | Required    | Required     | Required   | Required  | Required | \-             |
| Help on olsadmintool     | `olsadmintool` `command_name` `-- help` | Omitted     | Omitted      | Omitted    | Omitted   | Omitted  | \-             |

Table C-3 Summary of Profile and Default Command Parameters

| Profile Action                    | Profile Command                     | Policy Name | Profile Name | Max Read Label | Max Write Label | Min Write Label | Def Read Label | Def Row Label | Priv's   | CON      |
|:----------------------------------|:------------------------------------|:------------|:-------------|:---------------|:----------------|:----------------|:---------------|:--------------|:---------|:---------|
| Create a Profile<sup>Foot 3</sup> | `olsadmin``tool` `create``profile`  | Required    | Required     | Required       | Required        | Required        | Required       | Required      | Required | Required |
| List Profiles                     | `olsadmintool`<br>`list` `profile`  | Required    | Omitted      | Omitted        | Omitted         | Omitted         | Omitted        | Omitted       | Omitted  | Required |
| Describe a Profile                | `olsadmintool` `describe` `profile` | Required    | Required     | Omitted        | Omitted         | Omitted         | Omitted        | Omitted       | Omitted  | Required |
| Drop a Profile                    | `olsadmintool` `drop` `profile`     | Required    | Required     | Omitted        | Omitted         | Omitted         | Omitted        | Omitted       | Omitted  | Required |

<sup>Footnote 3</sup>

In `createprofile`, specifying both privileges and labels is not required: a profile can specify labels, privileges, or both.

**Parent topic:** Relating Parameters to Commands for olsadmintool

### C.5 Examples of Using the olsadmintool Utility

You use the `olsadmintool` commands to set up Oracle Label Security in an Oracle Internet Directory environment.

Each command appears in this listing on multiple lines for readability, but in reality, would be given out as a single long string on the command line. The summarized results of carrying out all these commands appear in Results of These Examples, which follows the last example.

- Example: Making Other Users Policy Creators
  The `olsadmintool addpolcreator` command can enable other users to be policy creators.
- Example: Creating Policies with Valid Options
  The `olsadmintool createpolicy` command can create policies.
- Example: Creating Policy Administrators
  The `olsadmintool addadmin` command can create policy administrators.
- Example: Creating Levels
  The `olsadmintool createlevel` command can create individual levels.
- Example: Creating Compartments
  The `olsadmintool createcompartment` command can create a compartment.
- Example: Creating Groups
  The `olsadmintool creategroup` can create a group.
- Example: Creating Labels
  The `olsadmintool createlabel` can create a label.
- Example: Creating a Profile
  The `olsadmintool createprofile` command can create a profile.
- Example: Adding a User to a Profile
  The `olsadmintool adduser` command can add a user to a profile.
- Example: Adding Another User to a Profile
  You can use the `olsadmintool adduser` command to add another user to a profile.
- Example: Setting Audit Options
  The `olsadmintool audit` command can set audit options in a non-unified auditing environment.
- Results of These Examples
  As a result of running the sets of `olsadmintool` commands, the sample Oracle Label Security site has a specific structure.

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

#### C.5.1 Example: Making Other Users Policy Creators

The `olsadmintool addpolcreator` command can enable other users to be policy creators.

    ORACLE_HOME/bin/olsadmintool addpolcreator --userdn "cn=psmith,c=us"
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=lbacsys,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.2 Example: Creating Policies with Valid Options

The `olsadmintool createpolicy` command can create policies.

    ORACLE_HOME/bin/olsadmintool createpolicy --name Policy1 --colname pol1
    --options READ_CONTROL,WRITE_CONTROL -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 -D "cn=psmith,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool createpolicy --name Policy2 --colname pol2
    --options READ_CONTROL -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 -D "cn=lbacsys,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.3 Example: Creating Policy Administrators

The `olsadmintool addadmin` command can create policy administrators.

    ORACLE_HOME/bin/olsadmintool addadmin --polname Policy1
    --admindn "cn=shwong,c=us" -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389
    -D "cn=psmith,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool addadmin --polname Policy2
    --admindn "cn=shwong,c=us" -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389
    -D "cn=lbacsys,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.4 Example: Creating Levels

The `olsadmintool createlevel` command can create individual levels.

    ORACLE_HOME/bin/olsadmintool createlevel --polname Policy1 --tag 100
    --shortname TS --longname "TOP SECRET" -b "ou=Americas,o=Oracle, c=US"
    -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool createlevel --polname Policy1 --tag 99
    --shortname S --longname SECRET -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool createlevel --polname Policy1 --tag 98
    --shortname U --longname UNCLASSIFIED -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.5 Example: Creating Compartments

The `olsadmintool createcompartment` command can create a compartment.

    ORACLE_HOME/bin/olsadmintool createcompartment --polname Policy1 --tag 100
    --shortname A --longname ALPHA -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool createcompartment --polname Policy1 --tag 99
    --shortname B --longname BETA -b "ou=Americas,o=Oracle,c=US"
    -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.6 Example: Creating Groups

The `olsadmintool creategroup` can create a group.

    ORACLE_HOME/bin/olsadmintool creategroup --polname Policy1 --tag 100
    --shortname G1 --longname GROUP1
    -b "ou=Americas,o=Oracle,c=US"  -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool creategroup --polname Policy1 --tag 99
    --shortname G2 --longname GROUP2
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool creategroup --polname Policy1 --tag 98
    --shortname G3 --longname GROUP3
    -b "ou=Americas,o=Oracle,c=US"  -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.7 Example: Creating Labels

The `olsadmintool createlabel` can create a label.

    ORACLE_HOME/bin/olsadmintool createlabel --polname Policy1
    --tag 100 --value TS:A:G1
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

    ORACLE_HOME/bin/olsadmintool createlabel --polname Policy1 --tag 101
    --value TS:A,B:G2
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.8 Example: Creating a Profile

The `olsadmintool createprofile` command can create a profile.

    ORACLE_HOME/bin/olsadmintool createprofile --polname Policy1 --profname Profile1
    --maxreadlabel TS:A:G1 --maxwritelabel TS:A:G1 --minwritelabel U::
    --defreadlabel U:A:G1 --defrowlabel U:A:G1 --privileges WRITEUP,READ
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.9 Example: Adding a User to a Profile

The `olsadmintool adduser` command can add a user to a profile.

    ORACLE_HOME/bin/olsadmintool adduser --polname Policy1 --profname Profile1
    --userdn cn=nina,ou=Asia,o=microsoft,l=seattle,st=WA,c=US
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.10 Example: Adding Another User to a Profile

You can use the `olsadmintool adduser` command to add another user to a profile.

    ORACLE_HOME/bin/olsadmintool adduser --polname Policy1 --profname Profile1
    --userdn cn=daniel,ou=France,o=oracle,l=madison,st=WI,c=US
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.11 Example: Setting Audit Options

The `olsadmintool audit` command can set audit options in a non-unified auditing environment.

    ORACLE_HOME/bin/olsadmintool audit --polname Policy1 --option "SET,APPLY"
    --type SESSION --success BOTH
    -b "ou=Americas,o=Oracle,c=US" -h sales_west -p 389 -D "cn=shwong,c=us"
    Enter bind password: bind_password

**Parent topic:** Examples of Using the olsadmintool Utility

#### C.5.12 Results of These Examples

As a result of running the sets of `olsadmintool` commands, the sample Oracle Label Security site has a specific structure.

- Policy creators: User `psmith`

- Policies: `Policy1` and `Policy2`

- Policy Administrators: User `shwong`

- Levels, Compartments, and Groups: Refer to Table C-4.

Table C-4 Label Component Definitions from Using olsadmintool Commands

| Label Component | Tag | Short Name | Long Name    |
|:----------------|:----|:-----------|:-------------|
| Level           | 100 | TS         | TOP SECRET   |
| Level           | 99  | S          | SECRET       |
| Level           | 98  | U          | UNCLASSIFIED |
| Compartment     | 100 | A          | ALPHA        |
| Compartment     | 99  | B          | BETA         |
| Group           | 100 | G1         | GROUP1       |
| Group           | 99  | G2         | GROUP2       |
| Group           | 98  | G3         | GROUP3       |

- Data labels: Tag 100 for TS:A:G1 and tag 101 for TS:A,B:G2

- Users: Nina, from the Asia group of Microsoft, based in Seattle, Washington, managed under the Americas organization of the US Oracle organization, and Daniel, from the France group of Oracle in Madison, Wisconsin, managed under the same organization.

- Profiles: Refer to Table C-5.

Table C-5 Contents of Profile1 from Using olsadmintool Commands

| Profile Element | Contents       | Long-name Expansion or Meaning                                     |
|:----------------|:---------------|:-------------------------------------------------------------------|
| MaxReadLabel    | TS:A:G1        | TOP SECRET:ALPHA:GROUP1                                            |
| MaxWriteLabel   | TS:A:G1        | TOP SECRET:ALPHA:GROUP1                                            |
| MinWriteLabel   | U::            | UNCLASSIFIED (not restricted to any compartments or groups)        |
| DefReadLabel    | U:A:G1         | UNCLASSIFIED:ALPHA:GROUP1                                          |
| DefRowLabel     | U:A:G1         | UNCLASSIFIED:ALPHA:GROUP1                                          |
| Privileges      | WRITE_UP, READ | User can read any row and raise the level of rows the user writes. |

- Auditing options: `SET`, `APPLY`, `SESSION`, and `BOTH`

**Parent topic:** Examples of Using the olsadmintool Utility

### C.6 olsoidsync Command Reference

The `olsoidsync` command pulls policy information from Oracle Internet Directory and populates the information in the database (bootstrapping).

You must provide the database TNS name, the database user name, the database user's password, the administrative context (if any), the Oracle Internet Directory host name, the bind DN and bind password, and optionally the Oracle Internet Directory port number.

#### Syntax

    olsoidsync --dbconnectstring "database_connect_string_in_host:port:sid_format"
    --dbuser database_user [-c] [-r]
    [-b admin_context] -h OID_host [-p port] -D bind_DN

    Enter Database password: database_user_password
    Enter bind password: bind_password

In this specification:

- `-c` drops all the existing policies in the database and refreshes it with policy information from Oracle Internet Directory. Optional.
- `-r` drops all the policy metadata (without dropping the policies themselves) and refreshes the policies with new metadata from Oracle Internet Directory. Optional.

Without these two switches, the command will only create new policies from Oracle Internet Directory, and will halt on any errors encountered during the refresh.

#### Example

    olsoidsync --dbconnectstring sales_srvr:1521:ora101 --dbuser lbacsys -c
    -b "ou=Americas,o=ExampleCorp,c=US" -h sales_srvr -D cn=policycreator
    Enter Database password: database_user_password
    Enter bind password: bind_password

**Related Topics**

- [Bootstrapping Databases](oracle-label-security-using-oracle-internet-directory.md)

**Parent topic:** Command-line Tools for Label Security Using Oracle Internet Directory

------------------------------------------------------------------------



Footnote Legend

Footnote 2:

Command FootnoteEvery command must include the directory host name, the bind DN, and the bind password. Any command may, as needed, also supply the subscriber administrative context (optional), the directory port number (also optional), or both. See also Table C-2 for additional details on these parameters.
