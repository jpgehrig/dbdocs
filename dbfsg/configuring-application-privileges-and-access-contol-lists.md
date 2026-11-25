## 4  Configuring Application Privileges and Access Control Lists

This chapter describes how to configure application privileges and access control lists (ACLs) in Oracle Database Real Application Security. It includes information on how to create, set, and modify ACLs, and describes how ACL security interacts with other Oracle Database security mechanisms.

This chapter contains the following sections:

- About Application Privileges

- About Configuring Security Classes

- About Configuring Access Control Lists

- Data Security

- ACL Binding

### 4.1 About Application Privileges

The database has predefined system privileges, such as `CREATE TABLE`, and object privileges, such as `UPDATE`. A large number of custom privileges that must be defined for enterprise applications are often called application-defined privileges. Real Application Security introduces the definition of these privileges, termed application privileges, in the database. For application developers, these custom application privileges are used for access control on application-level operations. These application-level operations allow fine-grained access on data at a granular level of columns, rows, or cells.

When an application privilege is explicitly bound to a resource, for example, rows and columns of a table, an application privilege can be used to protect an application-level operation on a database object. Alternatively, it may be used in the same manner as a system privilege when binding to a resource is not required.

**See Also:**

About Checking ACLs for a Privilege

This section contains the following topic: Aggregate Privilege.

#### 4.1.1 Aggregate Privilege

A Real Application Security aggregate privilege implies a set of other application privileges. The implied application privileges of an aggregate privilege can be any application privilege defined by the current security class or an inherited application privilege (see "About Configuring Security Classes" for more information). When an aggregate privilege is granted or denied, its implied application privileges are implicitly granted or denied.

When an aggregate privilege `AG` implies the application privileges `p1` and `p2`, granting the application privilege, `AG`, implies that both `p1` and `p2` are granted. However, granting both the `p1` and `p2` does not imply that `AG` is granted.

Aggregate privileges are useful for the following purposes:

- Enabling grouping and granting a set of application privileges as a single grant, simplifying application privilege administration. A group name or an alias for a set of application privileges, where the group name itself is not an application privilege, makes checking for the set simpler as it checks for each application privilege in the group.

- Providing an efficient way to check a set of application privileges based on a single application privilege check.

Example 4-1 adds an aggregate privilege called `UPDATE_INFO` to the `HRPRIVS` security class. The aggregate privilege contains the implied privileges `UPDATE`, `DELETE`, and `INSERT`.

When the group name itself is a first class privilege, there may be several possible semantics for the aggregate privilege based on its relationship to its members. When defining a semantic to represent an aggregate privilege, you must consider various relations between the aggregate privilege and its members, such as imply and include. For example, consider the imply relation in Java Security; selecting this semantic when granting an aggregate privilege implies granting all its member application privileges individually, but not the aggregate privilege. Therefore, granting all the member application privileges of an aggregate does not imply granting the aggregate privilege.

Example 4-2 adds a list of implied application privileges for the aggregate privilege `UPDATE_INFO`.

An aggregate privilege is not an application role. An application role itself is not an application privilege that protects a resource. Application roles are used to activate and deactivate application privileges available to an application user to enforce role-based access control constraints.

Also, an aggregate privilege is not a security class. A security class is not an application privilege that can be granted to a user. A security class lists a set of application privileges including aggregate privileges that may be either granted or denied in an ACL. Within a security class, many aggregate privileges may be defined based on the application privileges available in the security class.

An aggregate privilege can have other aggregate privileges as its members. Note that the member privileges of an aggregate privilege must be defined in the same security class (or in an ancestor security class) as the aggregate privilege. An aggregate privilege definition cannot create a cycle.

Example 4-1 Adding an Aggregate Privilege to a Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_PRIVILEGES(sec_class=>'HRPRIVS',
                                       priv=>'UPDATE_INFO',
                                       implied_priv_list=>XS$NAME_LIST('"UPDATE"',
                                               '"DELETE"', '"INSERT"'));
    END;

Example 4-2 Adding Implied Privileges to an Aggregate Privilege

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_IMPLIED_PRIVILEGES(sec_class =>'HRPRIVS',(priv=>'UPDATE_INFO',
    implied_priv_list=>XS$NAME_LIST('"UPDATE"', '"DELETE"', '"INSERT"'));
    END;

This section contains: ALL Privilege.

##### 4.1.1.1 ALL Privilege

The `ALL` privilege is a predefined aggregate privilege. Every security class has the `ALL` privilege, and it contains all the application privileges of that security class. `ALL` is not explicitly defined in every security class, but it is internally understood by the system based on the security class associated with the ACL. The cardinality of an `ALL` for a security class changes whenever an application privilege is added or removed from the security class.

Use of the `ALL` construct enables Real Application Security to express access control policy such as "grant all the application privileges to the application user `u1` defined for an application except the specific privilege `p1`". Example 4-3 shows an ACL in the security class, `AppSecurityClass`, which has all the application privileges for the application. The ordered evaluation of ACEs ensures that the `ALL` except `p1` is granted to the application user `u1`.

Example 4-3 Using ALL Grant

    select NAME, SECURITY_CLASS, PARENT_ACL from DBA_XS_ACLS;

    NAME         SECURITY_CLASS     PARENT_ACL
    ----------   ----------------   ---------------
    sampleACL    AppSecurityClass


    select ACL, ACE_ORDER, GRANT_TYPE, PRINCIPAL, PRIVILEGE from DBA_XS_ACES;

    ACL         ACE_ORDER   GRANT_TYPE   PRINCIPAL      PRIVILEGE
    ---------   ---------   ----------   ------------   ----------
    sampleACL   1           DENY         U1             p1
    sampleACL   2           GRANT        U1             ALL

### 4.2 About Configuring Security Classes

This section contains the following topics:

- About Security Classes

- Security Class Inheritance

- Security Class as Privilege Scope

- DML Security Class

- About Validating Security Classes

- Manipulating Security Classes

#### 4.2.1 About Security Classes

A security class is a scope for a set of application privileges. The same application privilege can be defined in multiple security classes. A security class restricts the set of application privileges that may be granted or denied within an ACL. A security class is both a place to define a collection of relevant application privileges and a way to associate an ACL with one security class.

Real Application Security supports a set of predefined application privileges and security classes and also allows applications to define their own custom application privileges using security classes. Each class of object being protected is associated with a security class that indicates the set of operations that may be performed on its objects. There are predefined security classes that define built-in application privileges.

Security classes simplify the task of managing a large number of application privileges. Each ACL is associated with one security class. This security class defines the scope of application privileges that may be granted within the ACL.

Each object type can support a large number of application privileges, and many different object types may share a common set of operations. To simplify these types of specifications, security classes support inheritance.

#### 4.2.2 Security Class Inheritance

A security class can inherit application privileges from parent security classes. A child security class implicitly contains all the application privileges defined in the parent security classes. The application privileges available in a security class are the combination of the application privileges defined in the security class and the application privileges inherited from parent security classes.

A security class can specify a list of parent security classes. The application privileges available in these parent classes become available in the child class. When the same application privilege name is defined in a child and its parent security class, the application privilege in the child replaces or overrides the application privilege in the parent.

Example 4-4 shows security class inheritance by creating a security class called `HRPRIVS`. The `HRPRIVS` security class defines two application privileges, `VIEW_SENSITIVE_INFO` and `UPDATE_INFO`. `UPDATE_INFO`, which is an aggregate privilege that implies three other privileges: `UPDATE`, `DELETE`, and `INSERT`. The security class `HRPRIVS` inherits application privileges from `DML` security class as specified by the `parent_list` parameter.

Example 4-4 Showing Security Class Inheritance

     DECLARE
      pr_list  XS$PRIVILEGE_LIST;
    BEGIN
      pr_list :=XS$PRIVILEGE_LIST(
         XS$PRIVILEGE(name=>'VIEW_SENSITIVE_INFO'),
         XS$PRIVILEGE(name=>'UPDATE_INFO',
                      implied_priv_list=>XS$NAME_LIST
                        ('"UPDATE"', '"DELETE"', '"INSERT"')));

      sys.xs_security_class.create_security_class(
         name=>'HRPRIVS',
         parent_list=>XS$NAME_LIST('DML'),
         priv_list=>pr_list);
    END;
    /

#### 4.2.3 Security Class as Privilege Scope

An ACL has a single security class as its **scope**. An ACL grants application privileges to principals to control access to protected data or functionality; it can grant only the application privileges that are defined in its security class. The `security_class` parameter is used to specify the security class in an ACL. When checking an application privilege against an ACL, the security class of the application privilege is resolved based on the security class of the ACL, as the ACL always has an associated security class. If no security class is specified, then the DML Security Class is used as the default security class. Different ACLs can have as their scope the same security class.

#### 4.2.4 DML Security Class

The `DML` security class is predefined or created during installation. The `DML` security class contains common application privileges for object manipulation: `SELECT`, `INSERT`, `UPDATE`, and `DELETE`. If an ACL does not specify its security class, `DML` is the default security class for the ACL.

Real Application Security DML application privileges are the same as database object privileges and inherently enforced by database object-level operations. However, Real Application Security DML application privileges are effective only when Real Application Security Data Security is enabled for database tables.

#### 4.2.5 About Validating Security Classes

Oracle recommends that you always validate the Real Application Security objects after administrative configuration changes. The `XS_DIAG` package provides a set of validation APIs to help ensure that these changes do not damage the complicated relationships among your Real Application Security objects.

See "[VALIDATE_SECURITY_CLASS Function](XS_DIAG-package.md)" for more information about validating a security class.

#### 4.2.6 Manipulating Security Classes

To manipulate security classes, use the procedures in PL/SQL package `XS_SECURITY_CLASS`; it includes procedures to create, manage, and delete security classes and their application privileges. This package also includes procedures for managing security class inheritance; see "[XS_SECURITY_CLASS Package](XS_SECURITY_CLASS-package.md)".

Example 4-5 invokes `ADD_PARENTS` to add the parent security class `GENPRIVS` to the `HRPRIVS` security class.

Example 4-6 invokes `REMOVE_PARENTS` to remove the parent security class `GENPRIVS` from the `HRPRIVS` security class.

Example 4-7 invokes `ADD_PRIVILEGES` to add an aggregate privilege called `UPDATE_INFO` to the `HRPRIVS` security class. The aggregate privilege contains the implied privileges `UPDATE`, `DELETE`, and `INSERT`. Note that `ADD_PRIVILEGES` may be used to add several application privileges to a security class. See "Aggregate Privilege" for more information.

Example 4-8 invokes `REMOVE_PRIVILEGES` to remove the `UPDATE_INFO` application privilege from the `HRPRIVS` security class.

Example 4-9 invokes `REMOVE_PRIVILEGES` to remove all application privileges from the `HRPRIVS` security class.

Example 4-10 invokes `ADD_IMPLIED_PRIVILEGES` to add a list of implied application privileges for the aggregate privilege `UPDATE_INFO`.

Example 4-11 invokes `REMOVE_IMPLIED_PRIVILEGES` to remove the implicit privilege `DELETE` from the aggregate privilege `UPDATE_INFO`.

Example 4-12 invokes `REMOVE_IMPLIED_PRIVILEGES` to remove all implicit application privileges from the aggregate privilege `UPDATE_INFO`.

The procedure sets a description string for the specified security class. Example 4-13 invokes `SET_DESCRIPTION` to set a description string for the `HRPRIVS` security class.

Example 4-14 invokes `DELETE_SECURITY_CLASS` to delete the `HRACL` ACL using the default delete option `DEFAULT_OPTION`. Note that this option is defined in "[XS_ADMIN_UTIL Package](XS_ADMIN_UTIL-package.md)".

Example 4-5 Adding Parent Security Classes for a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_PARENTS('HRPRIVS','GENPRIVS');
    END;

Example 4-6 Removing One or More Parent Classes for a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PARENTS('HRPRIVS','GENPRIVS');
    END;

Example 4-7 Adding One or More Application Privileges to a Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_PRIVILEGES(sec_class=>'HRPRIVS',
                                       priv=>'UPDATE_INFO',
                                       implied_priv_list=>XS$NAME_LIST('"UPDATE"',
                                                        '"DELETE"', '"INSERT"'));
    END;

Example 4-8 Removing One or More Application Privileges from a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PRIVILEGES('HRPRIVS','UPDATE_INFO');
    END;

Example 4-9 Removing all Application Privileges for a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PRIVILEGES('HRPRIVS');
    END;

Example 4-10 Adding One or More Implied Application Privileges to an Aggregate Privilege

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_IMPLIED_PRIVILEGES(priv=>'UPDATE_INFO',
                                               implied_priv_list=>XS$NAME_LIST('"UPDATE"', '"DELETE"', '"INSERT"'));
    END;

Example 4-11 Removing a Specified Implied Application Privileges from an Aggregate Privilege

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES('UPDATE_INFO','"DELETE"');
    END;

Example 4-12 Removing all Implied Application Privileges from an Aggregate Privilege

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES('UPDATE_INFO');
    END;

Example 4-13 Setting a Description String for a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.SET_DESCRIPTION(
        'HRPRIVS','Contains privileges required to manage HR data');
    END;

Example 4-14 Deleting a Specified Security Class

    BEGIN
      SYS.XS_SECURITY_CLASS.DELETE_SECURITY_CLASS('HRPRIVS',XS_ADMIN_UTIL.DEFAULT_OPTION);
    END;

### 4.3 About Configuring Access Control Lists

This section contains the following topics:

- About ACLs and ACEs

- Creating ACLs and ACEs

- About Validating Access Control Lists

- Updating Access Control Lists

- About Checking ACLs for a Privilege

- About Using Multilevel Authentication

- Principal Types

- Access Resolution Results

- ACE Evaluation Order

- ACL Inheritance

- About ACL Catalog Views

- About Security Class Catalog Views

#### 4.3.1 About ACLs and ACEs

Real Application Security encompasses access control lists (ACLs) and supports grants, denials, and various conflict resolution methods. ACLs are extended to support application-defined privileges, enabling applications to control privileges that are meaningful to it. Authorization queries are of the form: "Is the application user authorized for privilege `p` in ACL `a`?" Application-defined privileges are implemented through APIs supported both in the middle tier and in the database. These APIs enable the application to protect sensitive operations, such as approval of purchase orders.

Before performing a sensitive operation, the application must determine the required application privileges. For example, if the application requires the `approvePO` application privilege, it must locate the ACL associated with the desired purchase order, `a1`, and issue a query to determine if the Real Application Security session is authorized for application privilege `approvePO` in `a1`. Note that the application must be trusted to properly carry out authorization. Data security improves this by providing a declarative method of associating ACLs with rows in a table; a data security policy allows an administrator or developer to identify a set of rows in a table using an SQL predicate and associates the set with the ACL that is used to control access to its member rows.

The data security system provides a SQL operator that returns the ACLs associated with a row. This SQL operator performs an authorization check using the ACL references associated with the row. By default, a query returns all rows the user is allowed to view; these ACL references may be used in the middle tier to determine appropriate access for a particular row, as arguments in a `WHERE` clause that limits the result set. Thus, the result set may be further restricted to display only those rows for some specific operations, such as `approvePO`, based on the user's authorization.

The Real Application Security system provides native enforcement for SQL operations in the database, limiting the scope for damage due to security errors in the application. Thus, a SQL injection attack in one part of the application will not provide access to tables outside of that component.

An ACL protects a resource by specifying application privileges of the principals on the resource. An ACL is a list of access control entries (ACEs) where each ACE maintains the mapping from a principal to a granted or denied application privileges for the resource. A principal may be a database user or Real Application Security application user or application role.

##### Access Control Entry or ACE

An access control entry, or ACE, represents an application privilege grant, and an ACL represents a set of application privilege grants that are bound to a resource. Here, the resource can be a database table, a column in a table, or a set of rows in a table selected using a SQL predicate. Hence when a resource is accessed, only the ACLs associated with the resource are checked for the access right.

An ACE either grants or denies access to some application function or other database data for a particular principal. The ACE does not, itself, specify which data to protect; that is done outside the ACE and the ACL, by associating the ACL with target data.

`XS$ACE_TYPE` type is provided to construct each ACE entry for the ACL. An `XS$ACE_LIST` object consists of a list of privileges and the principal to whom the privileges are granted or denied. ACEs related information can be accessed through `DBA_XS_ACES` view.

#### 4.3.2 Creating ACLs and ACEs

Example 4-15 creates an ACL called `HRACL`. This ACL includes ACEs contained in `ace_list`. The application privileges used in `ace_list` are available in the `HRPRIVS` security class. The `st_date` and `en_date` parameters specify the active start and end times for this ACL; note that only the `SELECT` and `VIEW_SENSITIVE_INFO` application privileges are temporary.

Example 4-15 Creating an Access Control List

    DECLARE
      st_date TIMESTAMP WITH TIME ZONE;
      en_date TIMESTAMP WITH TIME ZONE;
      ace_list XS$ACE_LIST;
    BEGIN
      st_date := SYSTIMESTAMP;
      en_date := TO_TIMESTAMP_TZ('2019-06-18 11:00:00 -5:00',
                              'YYYY-MM-DD HH:MI:SS  TZH:TZM');
      ace_list := XS$ACE_LIST(
          XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"','VIEW_SENSITIVE_INFO'),
                      granted=>true,
                      principal_name=>'HRREP',
                      start_date=>st_date,
                      end_date=>en_date),
          XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('UPDATE_INFO'),
                      granted=>true,
                      principal_name=>'HRMGR'),
          XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"'),
                      granted=>true,
                      principal_name=>'DB_HR', principal_type=>XS_ACL.PTYPE_DB));

      sys.xs_acl.create_acl(name=>'HRACL',
                        ace_list=>ace_list,
                        sec_class=>'HRPRIVS',
                        description=>'HR Representative Access');
    END;
    /

Each ACE includes a principal that is the target of the grant and a list of application privileges. The grant is subject to the following attributes described in these topics:

- Deny

- Invert

- ACE Start-Date and End-Date

##### 4.3.2.1 Deny

When a grant is negated, the application privileges are denied. Example 4-16 sets the value of the attribute `granted` to `FALSE` to deny application privileges to the principal. The default value is `TRUE`.

Real Application Security ACL supports only the ordered evaluation of ACEs. The first ACE that grants or denies the requested application privilege contributes toward the final grant or deny. See section "[DBA_XS_ACES](real-application-security-data-dictionary-views.md)".

Example 4-16 Denying a Privilege

    XS$ACE_LIST(
                XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('UPDATE_INFO'),
                granted=>FALSE,
                principal_name=>'HRREP'
                );

##### 4.3.2.2 Invert

When the specified application privileges are given to all principals except one, that principal is inverted; the `inverted` attribute is set to `TRUE`. The default value of the attribute `inverted` is `FALSE`. In Example 4-17, a grant made to the inverted role `HRGUEST` provides the application privileges to any user that does not have the role enabled.

Example 4-17 Inverting an Application Privilege

    XS$ACE_LIST(
                XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('UPDATE_INFO'),
                inverted=>TRUE,
                principal_name=>'HRGUEST'
                );

##### 4.3.2.3 ACE Start-Date and End-Date

Each ACE can have a time constraint based on a start-date and an end-date, specifying the time when the ACE is in effect.

In Example 4-18, the optional attributes `start_date` and `end_date` (of datatype `TIMESTAMP WITH TIME ZONE`) define the time period over which an ACE is valid. The `end_date` value must be greater than the `start_date` value.

Example 4-18 Setting ACE Start-Date and End-Date

    XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"','VIEW_SENSITIVE_INFO'),
                granted=>true,
                principal_name=>'HRREP',
                start_date=>st_date,
                end_date=>en_date))

#### 4.3.3 About Validating Access Control Lists

Oracle recommends that you always validate the Real Application Security objects after administrative configuration changes. The `XS_DIAG` package provides a set of validation APIs to help ensure that these changes do not damage the complicated relationships among your Real Application Security objects.

See "[VALIDATE_ACL Function](XS_DIAG-package.md)" for more information about validating an ACL.

#### 4.3.4 Updating Access Control Lists

To manipulate ACLs, use the procedures in PL/SQL package `XS_ACL`; it contains procedures that create and manage ACLs. See "[XS_ACL Package](XS_ACL-package.md)".

Example 4-19 invokes `APPEND_ACES` to add an ACE, `ace_entry`, to the `HRACL` ACL. The ACE grants the `SELECT` privilege to the `DB_HR` database user.

Example 4-20 invokes `REMOVE_ACES` to remove all ACEs from the ACL called `HRACL`.

The procedure sets or modifies the security class for an ACL. Example 4-21 invokes `SET_SECURITY_CLASS` procedure to associate the `HRPRIVS` security class with ACL `HRACL`.

Example 4-22 invokes `SET_PARENT_ACL` to set the `AllDepACL` ACL as the parent ACL for the `HRACL` ACL. The inheritance type is set to `EXTEND`.

Example 4-23 invokes `REMOVE_ACL_PARAMETERS` to remove all ACL parameters for `ACL1`.

Example 4-24 invokes `REMOVE_ACL_PARAMETERS` to remove the `REGION` parameter for `ACL1`.

Example 4-25 invokes `SET_DESCRIPTION` to set a description for ACL `HRACL`.

Example 4-26 invokes `DELETE_ACL` to delete ACL `HRACL` using the default delete option.

Example 4-19 Appending an ACE to an Access Control List

    DECLARE
      ace_entry XS$ACE_TYPE;
    BEGIN
      ace_entry := XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"'),
                               granted=>true,
                               principal_name=>'DB_HR',
                               principal_type=>XS_ACL.PTYPE_DB);
      SYS.XS_ACL.APPEND_ACES('HRACL',ace_entry);
    END;

Example 4-20 Removing all ACEs from an ACL

    BEGIN
      SYS.XS_ACL.REMOVE_ACES('HRACL');
    END;

Example 4-21 Modifying the Security Class for an ACL

    BEGIN
      SYS.XS_ACL.SET_SECURITY_CLASS('HRACL','HRPRIVS');
    END;

Example 4-22 Setting or Modifying the Parent ACL

    BEGIN
      SYS.XS_ACL.SET_PARENT_ACL('HRACL','AllDepACL',XS_ACL.EXTENDED);
    END;

Example 4-23 Removing all ACL Parameters for an ACL

    BEGIN
      SYS.XS_ACL.REMOVE_ACL_PARAMETERS('ACL1');
    END;

Example 4-24 Removing the Specified ACL Parameter for an ACL

    BEGIN
      SYS.XS_ACL.REMOVE_ACL_PARAMETERS('ACL1','REGION');
    END;

Example 4-25 Setting a Description String for an ACL

    BEGIN
      SYS.XS_ACL.SET_DESCRIPTION('HRACL',
                             'Grants privileges to HR representatives and managers.');
    END;

Example 4-26 Deleting an ACL

    BEGIN
      SYS.XS_ACL.DELETE_ACL('HRACL');
    END;

#### 4.3.5 About Checking ACLs for a Privilege

There are two forms of enforcement; the system enforces DML privileges on data security protected objects, and the SQL operator added by the user enforces all other application privileges.

To check an ACL for an application privilege, call the SQL operator `ORA_CHECK_ACL`:

    ORA_CHECK_ACL (acls, privilege [,privilege] ... )

The `ORA_CHECK_ACL` SQL operator evaluates the list of application privileges with respect to an ordered list of ACLs. The evaluation process proceeds until any one of the following three events occurs:

- A grant is encountered for every application privilege specified before any potential denials of the same application privilege. The outcome is that the application privileges are granted.

- One of the application privileges specified is denied before any potential grants. The outcome is that at least one of the application privileges is denied.

- The list of ACEs is fully traversed. The outcome is that not all of the application privileges are granted.

To evaluate the application privilege, Oracle checks the ACEs (which are kept in order), and the evaluation stops when it finds an ACE that grants or denies the requested application privileges.

To find the ACLs associated with rows of a table or view, call the SQL operator `ORA_GET_ACLIDS`: `ORA_GET_ACLIDS(table, ...)`. For example, to enforce an application privilege, `priv`, on a table, `tab`, the user query adds the following check:

    ORA_CHECK_ACL(ORA_GET_ACLIDS(tab), priv)

This function answers the question whether application privileges were granted, denied, or neither. A corresponding Java API is also available.

#### 4.3.6 About Using Multilevel Authentication

Multilevel authentication enables the user to specify, through system-constraining ACLs, application privileges based on levels of authentication. A system-constraining ACL specifies a minimum application-wide set of application privileges on objects, based on dynamic roles that reflect an application user's level of authentication. When attempting to access an object, an application user may be either strongly or weakly authenticated, either inside or outside the firewall, with the following four possible levels of authentication:

- Strongly authenticated, inside firewall

- Strongly authenticated, outside firewall

- Weakly authenticated, inside firewall

- Weakly authenticated, outside firewall

A system-constraining ACL can specify application privileges that apply to application users at each level of authentication in an application. Based on application requirements, the administrator may grant additional application privileges to specific users based on any necessary criteria; such additional application privileges are independent of any system-constraining ACL. Example 4-28 and Example 4-29 implement a system-constraining ACL.

#### 4.3.7 Principal Types

In addition to Real Application Security principals, application users and application roles, Real Application Security supports grants based on database users and roles. When the system evaluates an ACL in a context of a Real Application Security session, it ignores grants that are based on a database schema, but honors grants that are based on database role because they are part of Real Application Security user's role list. Within an ACL, multiple ACEs can grant privileges to a principal.

#### 4.3.8 Access Resolution Results

Requests for access can have two possible results: `true` or `false`.

- A result of `true` means that the requested application privilege is granted

- A result of `false` means that the requested application privilege is either not granted or denied.

#### 4.3.9 ACE Evaluation Order

ACEs are evaluated in the order they appear in the ACL. The outcome of evaluating a particular ACE may be one of the following:

- The application privilege is granted.

- The application privilege is denied.

- The application privilege is neither granted nor denied.

Note that if an ACE grants an application privilege that a previous ACE denies, the result is a deny because the ACEs are evaluated in order.

#### 4.3.10 ACL Inheritance

ACLs can explicitly inherit from a single parent ACL, enabling the application to share policies across multiple objects. When the request for an application privilege involves two ACLs, the final result of the access-resolution algorithm may be based on semantics of individual access-resolution results of the ACLs. Real Application Security supports two types of inheritance semantics: extending ACL inheritance (`OR` with ordered evaluation), and constraining ACL inheritance (`AND`).

This section contains:

- Extending ACL Inheritance

- Constraining ACL Inheritance

##### 4.3.10.1 Extending ACL Inheritance

Extending ACL inheritance (`OR` with ordered evaluation) dictates that the ACEs are evaluated from the bottom of the inheritance tree to its top, from child to parent. In extending ACL inheritance, an application privilege is granted if either child or parent ACL grants the privilege, and denied if either the child or parent ACL denies the privilege. In fact, the first ACL that explicitly grants or denies the requested application privilege determines the final result. After the first grant or deny, further evaluations of the remaining ACLs are not attempted. Note that this evaluation rule is the same as the ordered evaluation of ACEs within an ACL.

The following example sets the `AllDepACL` ACL as the parent ACL for the `HRACL` ACL. The inheritance type is set to `EXTENDED`.

Example 4-27 Extending ACL Inheritance

    BEGIN
      SYS.XS_ACL.SET_PARENT_ACL('HRACL','AllDepACL',XS_ACL.EXTENDED);
    END;

##### 4.3.10.2 Constraining ACL Inheritance

Constraining ACL inheritance (`AND`) requires that both the child and the parent ACL grant the application privilege so that the ACL check evaluates to `true`.

Application-wide security policies can be enforced if all the ACLs for an application are constrained by the same parent ACL. For example, imagine a sample policy where users who are authenticated as being inside the corporate firewall can have application privileges in addition to the `SELECT` privilege. Example 4-28 shows the constraining ACL for this policy (inheritance type is set to `CONSTRAINED`), where all application users with `XSPUBLIC` application role are granted the `SELECT` privilege. Note that only the application users who are inside the corporate firewall have the dynamic application role `FIREWALL` enabled. Therefore, application users inside the firewall are granted all the application privileges in `HRPRIVS` security class. As this ACL constrains all the ACLs, such as `guestACL`, Example 4-29 shows that the application privilege grants of these ACLs are constrained by `FIREWALL_ACL`.

Example 4-28 Constraining ACL Inheritance: Firewall-Specific Authentication Privilege

    DECLARE
      ace_list XS$ACE_LIST;
    BEGIN
      ace_list := XS$ACE_LIST(
                     XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"'),
                                 granted=>true,
                                 principal_name=>'XSPUBLIC'),
                     XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('ALL'),
                                 granted=>true,
                                 principal_name=>'FIREWALL'));
      sys.xs_acl.create_acl(name=>'FIREWALL_ACL',
                        ace_list=>ace_list,
                        sec_class=>'HRPRIVS',
                        description=>'Only select privilege if not inside firewall');
    END;
    /

    BEGIN
    SYS.XS_ACL.SET_PARENT_ACL('GuestACL', 'FIREWALL_ACL',XS_ACL.CONSTRAINED);
    END;

Example 4-29 Using a Constraining Application Privilege

    SQL> select ACE_ORDER, GRANT_TYPE, PRINCIPAL, PRIVILEGE
         from DBA_XS_ACES
         where ACL='FIREWALL_ACL';

    ACE_ORDER    GRANT_TYPE    PRINCIPAL    PRIVILEGE
    ----------   ----------    ---------    ----------
    1            GRANT         XSPUBLIC     SELECT
    2            GRANT         FIREWALL     ALL

#### 4.3.11 About ACL Catalog Views

ACLs have the following catalog views:

- `DBA_XS_ACLS` catalog view, described in section "[DBA_XS_ACLS](real-application-security-data-dictionary-views.md)"

- `DBA_XS_ACES` catalog view, described in section "[DBA_XS_ACES](real-application-security-data-dictionary-views.md)"

#### 4.3.12 About Security Class Catalog Views

Security classes have the following catalog views:

- `DBA_XS_SECURITY_CLASSES`, described in section "[DBA_XS_SECURITY_CLASSES](real-application-security-data-dictionary-views.md)"

- `DBA_XS_SECURITY_CLASS_DEP`, described in "[DBA_XS_SECURITY_CLASS_DEP](real-application-security-data-dictionary-views.md)"

- `DBA_XS_PRIVILEGES`, described in "[DBA_XS_PRIVILEGES](real-application-security-data-dictionary-views.md)"

### 4.4 Data Security

Data security associates ACLs with a logical group of rows, known as a data realm.

This enables applications to define and enforce application-specific privileges at the database layer, through policies that define data realms and their access. These data realms include both a SQL predicate that identifies a set of rows and an ACL that protects the identified rows. The ACL evaluation is based on the application user, not the schema owner.

This section includes the following topics:

- Data Realms

- Parameterized ACL

#### 4.4.1 Data Realms

Real Application Security's Data Security policy data realms associate ACLs with rows in a table. A data realm has two parts:

1.  A rule expressed as a SQL predicate, which selects a set of rows.

2.  A set of ACLs, which specify access policies on the rows.

Data Security manages DML Real Application Security application privileges granted by the associated ACLs. The `DataSecurity` module does not inherently enforce other (non-DML) Real Application Security application privileges. Such application privilege may be enforced programmatically as part of a DML operation, when invoking the `CHECK_PRIVILEGE` operator inside either the SQL operator or data realm predicate.

#### 4.4.2 Parameterized ACL

Because each data realm defines a rule that uses a set of parameters, different values for these parameters select different rows. These sets of rows may require different ACLs. Therefore, association between an ACL and a set of rows depends on the data realm rule and its parameter names and values.

### 4.5 ACL Binding

In the database, a privilege may be bound to a resource in the following manner:

- It can be explicitly bound as part of a privilege grant. For example, database object privileges are bound to a resource as part of a privilege grant, such as `GRANT ``user_N` `update ON ``table_M`.

- It may also be globally bound as part of the privilege definition, such as a system privileges `ALTER SYSTEM` or `CREATE ANY TABLE`, which do not require the resource name as part of their grant statement.

Similarly, a Real Application Security application privilege can be one of these types:

- Explicitly bound through an ACL and data realms as part of Data Security policies; see [Configuring Data Security](configuring-data-security.md)

- Globally bound to a resource as part of its definition
