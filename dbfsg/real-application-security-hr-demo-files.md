## C Real Application Security HR Demo Files

This appendix contains both the source files and log files. A detailed description of the HR Demo can be found in [Real Application Security HR Demo](real-application-security-hr-demo.md).

This appendix describes the following topics:

- How to Run the Security HR Demo

- Scripts for the Security HR Demo

- Generated Log Files for Each Script

### C.1 How to Run the Security HR Demo

To run the Security HR demo, run the following scripts in the order shown:

1.  Run the setup script `hrdemo_setup.sql`, which creates the log file: `hrdemo_setup.log`.
2.  Run the demo script `hrdemo.sql` with direct logon, which creates the log file: `hrdemo.log`.
3.  Run the demo script to explicitly create and attach to the Real Application Security session `hrdemo_session.sql`, which creates the log file: `hrdemo_session.log`.
4.  Run the Java demo `hrdemo.java` file, which creates the log file: `hrdemo.log`.
5.  Run the clean up script `hrdemo_clean.sql`, which creates the log file: `hrdemo_clean.log`.

### C.2 Scripts for the Security HR Demo

Table C-1 lists the scripts and generated log files with links to the content of each file.

Table C-1 HR Demo Scripts and Log Files

| Scripts            | Log Files          |
|:-------------------|:-------------------|
| hrdemo_setup.sql   | hrdemo_setup.log   |
| hrdemo.sql         | hrdemo.log         |
| hrdemo_session.sql | hrdemo_session.log |
| hrdemo.java        | hrdemo.log         |
| hrdemo_clean.sql   | hrdemo_clean.log   |

This section includes the following script files:

#### C.2.1 hrdemo_setup.sql

The source file for the set up script `hrdemo_setup.sql`.

    SET ECHO OFF
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100
    SET ECHO ON

    define passwd=&1

    ----------------------------------------------------------------------
    --  Introduction
    ----------------------------------------------------------------------
    -- The HR Demo shows how to use basic Real Application Security features.
    -- The demo secures HR.EMPLOYEES table by creating a data security
    -- policy that grants the table access to:
    -- Data Security Policy
    --
    --(1) An employee can view his/her own record including SALARY column.
    --(2) An IT engineer can view all employee records in IT department,
    --    but cannot view employee's salaries.
    --(3) An HR representative can view and update all employee records.
    --
    --
    --Sample Users and Their Role Grants:
    -- 1) DAUSTIN, an application user in IT department. He has role employee
    --    and it_engineer. He can view employee records in IT department, but he
    --    cannot view the salary column except for his own.
    -- 2) SMAVRIS, an application user in HR department. She has role employee
    --    and hr_representative. She can view and update all the employee records.

    ----------------------------------------------------------------------
    -- 1. SETUP - User and Roles
    ----------------------------------------------------------------------

    connect sys/&passwd as sysdba
    -- Create an application role employee for common employees.
    exec sys.xs_principal.create_role(name => 'employee', enabled => true);

    -- Create an application role it_engineer for IT department.
    exec sys.xs_principal.create_role(name => 'it_engineer', enabled => true);

    -- Create an application role hr_representative for HR department.
    exec sys.xs_principal.create_role(name => 'hr_representative', enabled => true);

    -- create a database role for object privilege grants
    create role db_emp;

    -- Grant DB_EMP to the three application roles, so they have the required
    -- object privileges to access the table.
    grant db_emp to employee;
    grant db_emp to it_engineer;
    grant db_emp to hr_representative;

    -- Create two application users:
    -- DAUSTIN (in IT department), granted employee and it_engineer.
    exec  sys.xs_principal.create_user(name => 'daustin', schema => 'hr');
    exec  sys.xs_principal.set_password('daustin', 'welcome1');
    exec  sys.xs_principal.grant_roles('daustin', 'XSCONNECT');
    exec  sys.xs_principal.grant_roles('daustin', 'employee');
    exec  sys.xs_principal.grant_roles('daustin', 'it_engineer');

    -- SMAVRIS (in HR department), granted employee and hr_representative.
    exec  sys.xs_principal.create_user(name => 'smavris', schema => 'hr');
    exec  sys.xs_principal.set_password('smavris', 'welcome1');
    exec  sys.xs_principal.grant_roles('smavris', 'XSCONNECT');
    exec  sys.xs_principal.grant_roles('smavris', 'employee');
    exec  sys.xs_principal.grant_roles('smavris', 'hr_representative');

    -- Grant HR user policy adminisration privilege
    exec sys.xs_admin_util.grant_system_privilege('ADMIN_ANY_SEC_POLICY','HR');

    ----------------------------------------------------------------------
    -- 2. SETUP - Security class and ACL
    ----------------------------------------------------------------------

    -- Connect as HR
    connect hr/hr;

    -- Grant necessary object privileges to db_emp role
    -- This role will be used to grant the required object privileges to
    -- application users.

    grant select, insert, update, delete on hr.employees to db_emp;

    -- Create a security class hr_privileges and include privileges from the predefined DML security class.
    -- hr_privileges has a new privilege VIEW_SALARY, which is used to control the
    -- access to SALARY column.
    declare
    begin
      sys.xs_security_class.create_security_class(
        name        => 'hr_privileges',
        parent_list => xs$name_list('sys.dml'),
        priv_list   => xs$privilege_list(xs$privilege('view_salary')));
    end;
    /

    -- Create three ACLs to grant privileges for the policy defined later.
    declare
      aces xs$ace_list := xs$ace_list();
    begin
      aces.extend(1);

      -- EMP_ACL: This ACL grants employee the privileges to view an employee's
      --          own record including SALARY column.
      aces(1) := xs$ace_type(privilege_list => xs$name_list('select','view_salary'),
                             principal_name => 'employee');

      sys.xs_acl.create_acl(name      => 'emp_acl',
                        ace_list  => aces,
                        sec_class => 'hr_privileges');

      -- IT_ACL:  This ACL grants it_engineer the privilege to view the employee
      --          records in IT department, but it does not grant the VIEW_SALARY
      --          privilege that is required for access to SALARY column.
      aces(1) := xs$ace_type(privilege_list => xs$name_list('select'),
                             principal_name => 'it_engineer');

      sys.xs_acl.create_acl(name      => 'it_acl',
                        ace_list  => aces,
                        sec_class => 'hr_privileges');

      -- HR_ACL:  This ACL grants hr_representative the privileges to view and update all
      --          employees' records including SALARY column.
      aces(1):= xs$ace_type(privilege_list => xs$name_list('select', 'insert',
                                            'update', 'delete', 'view_salary'),
                            principal_name => 'hr_representative');

      sys.xs_acl.create_acl(name      => 'hr_acl',
                        ace_list  => aces,
                        sec_class => 'hr_privileges');
    end;
    /

    ----------------------------------------------------------------------
    -- 3. SETUP - Data security policy
    ----------------------------------------------------------------------
    -- Create data security policy for EMPLOYEE table. The policy defines three
    -- realm constraints and a column constraint that protects SALARY column.
    declare
      realms   xs$realm_constraint_list := xs$realm_constraint_list();
      cols     xs$column_constraint_list := xs$column_constraint_list();
    begin
      realms.extend(3);

      -- Realm #1: Only the employee's own record.
      --           employee can view the realm including SALARY column.
      realms(1) := xs$realm_constraint_type(
        realm    => 'email = xs_sys_context(''xs$session'',''username'')',
        acl_list => xs$name_list('emp_acl'));

      -- Realm #2: The records in the IT department.
      --           it_engineer can view the realm excluding SALARY column.
      realms(2) := xs$realm_constraint_type(
        realm    => 'department_id = 60',
        acl_list => xs$name_list('it_acl'));

      -- Realm #3: All the records.
      --           hr_representative can view and update the realm including SALARY column.
      realms(3) := xs$realm_constraint_type(
        realm    => '1 = 1',
        acl_list => xs$name_list('hr_acl'));

      -- Column constraint protects SALARY column by requiring VIEW_SALARY
      -- privilege.
      cols.extend(1);
      cols(1) := xs$column_constraint_type(
        column_list => xs$list('salary'),
        privilege   => 'view_salary');

      sys.xs_data_security.create_policy(
        name                   => 'employees_ds',
        realm_constraint_list  => realms,
        column_constraint_list => cols);
    end;
    /

    -- Apply the data security policy to the table.
    begin
      sys.xs_data_security.apply_object_policy(
        policy => 'employees_ds',
        schema => 'hr',
        object =>'employees');
    end;
    /

    ----------------------------------------------------------------------
    -- 4. SETUP - Validate the objects we have set up.
    ----------------------------------------------------------------------
    set serveroutput on;
    begin
      if (sys.xs_diag.validate_workspace()) then
        dbms_output.put_line('All configurations are correct.');
      else
        dbms_output.put_line('Some configurations are incorrect.');
      end if;
    end;
    /
    -- XS$VALIDATION_TABLE contains validation errors if any.
    -- Expect no rows selected.
    select * from xs$validation_table order by 1, 2, 3, 4;

    ----------------------------------------------------------------------
    -- 5. SETUP - Mid-Tier related configuration.
    ----------------------------------------------------------------------

    connect sys/&passwd as sysdba

    -- create a session administrator who has only
    -- RAS session administration privilege (no data privilege),
    -- and is responsible to manage RAS session for each application user.
    grant xs_session_admin, create session to hr_session identified by hr_session;
    grant create session to hr_common identified by hr_common;

    -- craete a dispatcher user for java demo, to set up session for application user
    exec sys.xs_principal.create_user(name=>'dispatcher', schema=>'HR');
    exec sys.xs_principal.set_password('dispatcher', 'welcome1');
    exec sys.xs_principal.grant_roles('dispatcher', 'XSCONNECT');
    exec sys.xs_principal.grant_roles('dispatcher', 'xsdispatcher');

    exit

#### C.2.2 hrdemo.sql

The source file for the `hrdemo.sql` script. This script runs the demo with direct logon.

    SET ECHO OFF
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100
    COLUMN EMAIL FORMAT A10
    COLUMN FIRST_NAME FORMAT A15
    COLUMN LAST_NAME FORMAT A15
    COLUMN DEPARTMENT_ID FORMAT 9999
    COLUMN MANAGER_ID FORMAT 9999
    COLUMN SALARY FORMAT 999999
    SET ECHO ON

    ----------------------------------------------------------------------
    --  HR Demo - PL/SQL with RAS direct logon user
    ----------------------------------------------------------------------
    -- This demo shows RAS runtime, using RAS direct logon user.
    -- Each user directly connects to database and accesses employee table.
    -- RAS policy is automatically enforced.
    ---------------------------------------------------------------------

    -- Connect as DAUSTIN, who has only employee and it_engineer role
    conn daustin/welcome1;

    SET SECUREDCOL ON UNAUTH *******

    -- DAUSTIN can view the records in IT department, but can only view his own
    -- SALARY column.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees order by email;


    SET SECUREDCOL OFF

    -- DAUSTIN cannot update the record.
    update employees set manager_id = 102 where email = 'DAUSTIN';

    -- Record is not changed.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where email = 'DAUSTIN';


    -- Connect as SMAVRIS, who has both employee and hr_representative role.
    conn smavris/welcome1;

    -- SMAVRIS can view all the records including SALARY column.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where department_id = 60 or department_id = 40
    order by department_id, email;

    -- EMPLOYEES table has 107 rows, we expect to see all of them.
    select count(*) from employees;

    -- SMAVRIS can update the record.
    update employees set manager_id = 102 where email = 'DAUSTIN';

    -- Record is changed.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where email = 'DAUSTIN';

    -- change the record back to the original.
    update employees set manager_id = 103 where email = 'DAUSTIN';

    exit

#### C.2.3 hrdemo_session.sql

The source file for the `hrdemo_session.sql` script. This script explicitly creates and attaches a Real Application Security session.

    SET ECHO OFF
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100
    COLUMN EMAIL FORMAT A10
    COLUMN FIRST_NAME FORMAT A15
    COLUMN LAST_NAME FORMAT A15
    COLUMN DEPARTMENT_ID FORMAT 9999
    COLUMN MANAGER_ID FORMAT 9999
    COLUMN SALARY FORMAT 999999
    SET ECHO ON

    ----------------------------------------------------------------------
    --  HR Demo - PL/SQL with Session API
    ----------------------------------------------------------------------
    -- This demo shows RAS runtime, using RAS user as application user.
    -- The user does not logon to database, but a RAS session is created
    -- and attached for each user before accessing employee table.
    ---------------------------------------------------------------------

    -- Connect as RAS session administrator.
    connect hr_session/hr_session;

    -- Variable used to remember the session ID.
    var gsessionid varchar2(32);

    -- Create an application session for SMARVIS and attach to it.
    declare
      sessionid raw(16);
    begin
      sys.dbms_xs_sessions.create_session('SMAVRIS', sessionid);
      :gsessionid := rawtohex(sessionid);
      sys.dbms_xs_sessions.attach_session(sessionid, null);
    end ;
    /

    -- Display the current user, it should be SMAVRIS now.
    select xs_sys_context('xs$session','username') from dual;

    -- Display the enabled application roles and database roles.
    select role_name from v$xs_session_roles union
    select role from session_roles order by 1;

    -- SMAVRIS can view all the records including SALARY column.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where department_id = 60 or department_id = 40
    order by department_id, email;

    -- EMPLOYEES table has 107 rows, we expect to see all of them.
    select count(*) from employees;

    -- Disable hr_representative role.
    exec dbms_xs_sessions.disable_role('hr_representative');

    -- SMAVRIS should only be able to see her own record.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where department_id = 60 or department_id = 40
    order by department_id, email;

    -- Enable hr_representative role.
    exec sys.dbms_xs_sessions.enable_role('hr_representative');

    -- SMAVRIS can view all the records again.
    select email, first_name, last_name, department_id, manager_id, salary
    from employees where department_id = 60 or department_id = 40
    order by department_id, email;

    -- EMPLOYEES table has 107 rows, we expect to see all of them.
    select count(*) from employees;

    -- Detach and destroy the application session.
    declare
      sessionid raw(16);
    begin
      sessionid := hextoraw(:gsessionid);
      sys.dbms_xs_sessions.detach_session;
      sys.dbms_xs_sessions.destroy_session(sessionid);
    end;
    /

    exit

#### C.2.4 hrdemo.java

The source file for the Java demo is `hrdemo.java`.

    import java.security.GeneralSecurityException;
    import java.security.InvalidAlgorithmParameterException;
    import java.security.InvalidKeyException;
    import java.security.NoSuchAlgorithmException;
    import java.security.spec.InvalidKeySpecException;

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    import java.util.ArrayList;
    import java.util.List;
    import oracle.jdbc.OracleDriver;
    import oracle.jdbc.OracleResultSet;
    import oracle.jdbc.OracleResultSet.AuthorizationIndicator;

    import oracle.security.xs.AccessDeniedException;
    import oracle.security.xs.InvalidXSNamespaceException;
    import oracle.security.xs.InvalidXSUserException;
    import oracle.security.xs.Role;
    import oracle.security.xs.Session;
    import oracle.security.xs.XSAccessController;
    import oracle.security.xs.XSException;
    import oracle.security.xs.XSSessionManager;

    /**
     * A simple java application implemented using RAS.
     * It shows:
     *  -  How to setup RAS session manager
     *  -  How to manage RAS sessions
     *  -  How to use Column authorization indicator
     *  -  How to check privileges using "checkAcl" function
    */
    public class hrdemo {

      // application connection, should be created with unprivileged user
      // in RAS case, the user only needs DB connection privilege
      private Connection appConnection = null;

      // RAS dispatcher's connection, should be create with a RAS dispatcher user
      private Connection mgrConnection = null;
      // RAS session manager, to manage session for application user
      // Must be instanciated with disptcher's connection
      private XSSessionManager manager = null;

      public static void main(String[] args)  {

        try {
          DriverManager.registerDriver(new OracleDriver());


          if (args.length != 1) {
            System.out.println("Usage hrdemo dbURL");
            System.exit(1);
          }
          hrdemo demo = new hrdemo();
          demo.setupConnection(args[0]);

          demo.queryAsUser("DAUSTIN");
          demo.queryAsUser("SMAVRIS");

          demo.cleanupConnection();

        } catch (Exception e) {
          // we don't handle exception for now
          e.printStackTrace();
        }
      }

      private void queryAsUser(String user) throws SQLException, XSException {

        System.out.println("\nQuery HR.EMPLOYEES table as user \"" + user + "\"");

          Session lws = manager.createSession(appConnection, user, null,null);
          manager.attachSession(appConnection, lws, null, null, null, null, null);

          queryEmployees(lws);

          manager.detachSession(lws);
          manager.destroySession(appConnection, lws);

      }

      public void setupConnection(String url) throws SQLException, XSException, GeneralSecurityException {
        // dispatcher's connection
        mgrConnection =
            DriverManager.getConnection(url, "dispatcher", "welcome1");

        // RAS session manager
        manager = XSSessionManager.getSessionManager(mgrConnection, 30, 2048000);

        // connection used for application query
        appConnection = DriverManager.getConnection(url, "hr_common", "hr_common");
      }

      public void cleanupConnection() throws SQLException {
        mgrConnection.close();
        appConnection.close();

      }

      public void queryEmployees(Session lws) throws SQLException, XSException  {
        // using DB connection that has been attached to a RAS session
        Connection conn = lws.getConnection();
        String query = " select email, first_name, last_name, department_id, salary, ora_get_aclids(emp) from hr.employees emp where department_id in (40, 60, 100) order by email";

        Statement stmt = null;
        ResultSet rs = null;

        System.out.printf("  EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY\n");

        try {

          stmt = conn.createStatement();
          rs = stmt.executeQuery(query);

          while (rs.next()) {

            String email = rs.getString("EMAIL");
            String first_name = rs.getString("FIRST_NAME");
            String last_name = rs.getString("LAST_NAME");
            String department_id = rs.getString("DEPARTMENT_ID");
            String salary;

            if (((OracleResultSet)rs).getAuthorizationIndicator("SALARY") == AuthorizationIndicator.NONE) {
              salary = rs.getString("SALARY");
            }
            else {
              salary = "*****";
            }

            byte[] aclRaw = rs.getBytes(6);
            String update, viewSalary;


        // call checkAcl to determine whether can update the database record
        if (XSAccessController.checkAcl(lws, aclRaw, "UPDATE")) {
              update = "true";
            }
            else {
              update = "false";
            }

            if (XSAccessController.checkAcl(lws, aclRaw, "VIEW_SALARY")) {
              viewSalary = "true";
            }
            else {
              viewSalary = "false";
            }

            System.out.printf("%9s|%12s|%12s|%6s|%8s|%8s|%8s\n", email,
                              first_name, last_name, department_id,
                              salary, update, viewSalary);
           }
        } finally {
          try { if (rs != null) rs.close(); } catch (Exception e) {};
          try { if (stmt != null) stmt.close(); } catch (Exception e) {};
        }
      }
    }

#### C.2.5 hrdemo_clean.sql

The source file for the cleanup script is `hrdemo_clean.sql`.

    SET ECHO OFF
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100
    SET ECHO ON

    define passwd=&1

    connect hr/hr;

    -- Remove policy from the table.
    begin
      sys.xs_data_security.remove_object_policy(policy=>'employees_ds',
                                            schema=>'hr', object=>'employees');
    end;
    /
    -- Delete security class and ACLs
    exec sys.xs_security_class.delete_security_class('hr_privileges', xs_admin_util.cascade_option);
    exec sys.xs_acl.delete_acl('emp_acl', xs_admin_util.cascade_option);
    exec sys.xs_acl.delete_acl('it_acl', xs_admin_util.cascade_option);
    exec sys.xs_acl.delete_acl('hr_acl', xs_admin_util.cascade_option);

    -- Delete data security policy
    exec sys.xs_data_security.delete_policy('employees_ds', xs_admin_util.cascade_option);

    connect sys/&passwd as sysdba
    -- Delete application users and roles
    exec sys.xs_principal.delete_principal('employee', xs_admin_util.cascade_option);
    exec sys.xs_principal.delete_principal('hr_representative', xs_admin_util.cascade_option);
    exec sys.xs_principal.delete_principal('it_engineer', xs_admin_util.cascade_option);
    exec sys.xs_principal.delete_principal('smavris', xs_admin_util.cascade_option);
    exec sys.xs_principal.delete_principal('daustin', xs_admin_util.cascade_option);


    -- Delete database role
    drop role db_emp;

    -- Delete session administrator
    drop user hr_session;
    -- Delete the common user used to connect to DB
    drop user hr_common;

    -- Delete dispatcher user used by mid-tier
    exec sys.xs_principal.delete_principal('dispatcher', xs_admin_util.cascade_option);

    exit

### C.3 Generated Log Files for Each Script

This section includes the following log files that are generated from running the scripts listed in Table C-1:

- hrdemo_setup.log

- hrdemo.log

- hrdemo_run_sess.log

- hrdemo.log

- hrdemo_clean.log

#### C.3.1 hrdemo_setup.log

The `hrdemo_setup.log` file.

    SQL> @hrdemo_setup
    SQL>
    SQL> define passwd=&1
    Enter value for 1: sample
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> --  Introduction
    SQL> ----------------------------------------------------------------------
    SQL> -- The HR Demo shows how to use basic Real Application Security features.
    SQL> -- The demo secures HR.EMPLOYEE table by creating a data security
    SQL> -- policy that grants the table access to.
    SQL> -- Data Security Policy
    SQL> --
    SQL> --(1) An employee can view his/her own record including SALARY column.
    SQL> --(2) An IT engineer can view all employee records in IT department,
    SQL> --    but cannot view employee's salaries.
    SQL> --(3) An HR representative can view and update all employee records.
    SQL> --
    SQL> --
    SQL> --Sample Users and Their Role Grants:
    SQL> --1) DAUSTIN, an application user in IT department. He has role employee
    SQL> --   and it_engineer. He can view employee records in IT department, but he
    SQL> --   cannot view the salary column except for his own.
    SQL> --2) SMAVRIS, an application user in HR department. She has role employee
    SQL> --   and hr_representative. She can view and update all the employee records
    SQL> --
    SQL> ----------------------------------------------------------------------
    SQL> -- 1. SETUP - User and Roles
    SQL> ----------------------------------------------------------------------
    SQL>
    SQL> connect sys/&passwd as sysdba
    Connected.
    SQL> -- Create an application role employee for common employees.
    SQL> exec xs_principal.create_role(name => 'employee', enabled => true);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Create an application role it_engineer for IT department.
    SQL> exec xs_principal.create_role(name => 'it_engineer', enabled => true);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Create an application role hr_representative for HR department.
    SQL> exec xs_principal.create_role(name => 'hr_representative', enabled => true);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- create a database role for object privilege grants
    SQL> create role db_emp;

    Role created.

    SQL>
    SQL> -- Grant DB_EMP to the three application roles, so they have the required
    SQL> -- object privileges to access the table.
    SQL> grant db_emp to employee;

    Grant succeeded.

    SQL> grant db_emp to it_engineer;

    Grant succeeded.

    SQL> grant db_emp to hr_representative;

    Grant succeeded.

    SQL>
    SQL> -- Create two application users:
    SQL> -- DAUSTIN (in IT department), granted employee and it_engineer.
    SQL> exec  xs_principal.create_user(name => 'daustin', schema => 'hr');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.set_password('daustin', 'welcome1');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('daustin', 'XSCONNECT');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('daustin', 'employee');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('daustin', 'it_engineer');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- SMAVRIS (in HR department), granted employee and hr_representative.
    SQL> exec  xs_principal.create_user(name => 'smavris', schema => 'hr');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.set_password('smavris', 'welcome1');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('smavris', 'XSCONNECT');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('smavris', 'employee');

    PL/SQL procedure successfully completed.

    SQL> exec  xs_principal.grant_roles('smavris', 'hr_representative');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Grant HR user policy adminisration privilege
    SQL> exec xs_admin_util.grant_system_privilege('ADMIN_ANY_SEC_POLICY','HR');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> -- 2. SETUP - Security class and ACL
    SQL> ----------------------------------------------------------------------
    SQL>
    SQL>
    SQL> -- Connect as HR
    SQL> connect hr/hr;
    Connected.
    SQL>
    SQL> -- Grant necessary object privileges to db_emp role
    SQL> -- This role will be used to grant the required object privileges to
    SQL> -- application users.
    SQL>
    SQL> grant select, insert, update, delete on hr.employees to db_emp;

    Grant succeeded.

    SQL>
    SQL>
    SQL> -- Create a security class hr_privileges and include privileges from the predefined DML security class.
    SQL> -- hr_privileges has a new privilege VIEW_SALARY, which is used to control the
    SQL> -- access to SALARY column.
    SQL> declare
      2  begin
      3    xs_security_class.create_security_class(
      4      name        => 'hr_privileges',
      5      parent_list => xs$name_list('sys.dml'),
      6      priv_list   => xs$privilege_list(xs$privilege('view_salary')));
      7  end;
      8  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL>
    SQL>
    SQL> -- Create three ACLs to grant privileges for the policy defined later.
    SQL> declare
      2    aces xs$ace_list := xs$ace_list();
      3  begin
      4    aces.extend(1);
      5
      6    -- EMP_ACL: This ACL grants employee the privileges to view an employee's
      7    --          own record including SALARY column.
      8    aces(1) := xs$ace_type(privilege_list => xs$name_list('select','view_salary'),
      9                           principal_name => 'employee');
     10
     11    xs_acl.create_acl(name      => 'emp_acl',
     12                      ace_list  => aces,
     13                      sec_class => 'hr_privileges');
     14
     15    -- IT_ACL:  This ACL grants it_engineer the privilege to view the employee
     16    --          records in IT department, but it does not grant the VIEW_SALARY
     17    --          privilege that is required for access to SALARY column.
     18    aces(1) := xs$ace_type(privilege_list => xs$name_list('select'),
     19                           principal_name => 'it_engineer');
     20
     21    xs_acl.create_acl(name      => 'it_acl',
     22                      ace_list  => aces,
     23                      sec_class => 'hr_privileges');
     24
     25    -- HR_ACL:  This ACL grants hr_representative the privileges to view and update all
     26    --          employees' records including SALARY column.
     27    aces(1):= xs$ace_type(privilege_list => xs$name_list('select', 'insert',
     28                                            'update', 'delete', 'view_salary'),
     29                          principal_name => 'hr_representative');
     30
     31    xs_acl.create_acl(name      => 'hr_acl',
     32                      ace_list  => aces,
     33                      sec_class => 'hr_privileges');
     34  end;
     35  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL>
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> -- 3. SETUP - Data security policy
    SQL> ----------------------------------------------------------------------
    SQL> -- Create data security policy for EMPLOYEE table. The policy defines three
    SQL> -- realm constraints and a column constraint that protects SALARY column.
    SQL> declare
      2    realms   xs$realm_constraint_list := xs$realm_constraint_list();
      3    cols     xs$column_constraint_list := xs$column_constraint_list();
      4  begin
      5    realms.extend(3);
      6
      7    -- Realm #1: Only the employee's own record.
      8    --           employee can view the realm including SALARY column.
      9    realms(1) := xs$realm_constraint_type(
     10      realm    => 'email = xs_sys_context(''xs$session'',''username'')',
     11      acl_list => xs$name_list('emp_acl'));
     12
     13    -- Realm #2: The records in the IT department.
     14    --           it_engineer can view the realm excluding SALARY column.
     15    realms(2) := xs$realm_constraint_type(
     16      realm    => 'department_id = 60',
     17      acl_list => xs$name_list('it_acl'));
     18
     19    -- Realm #3: All the records.
     20    --           hr_representative can view and update the realm including SALARY column.
     21    realms(3) := xs$realm_constraint_type(
     22      realm    => '1 = 1',
     23      acl_list => xs$name_list('hr_acl'));
     24
     25    -- Column constraint protects SALARY column by requiring VIEW_SALARY
     26    -- privilege.
     27    cols.extend(1);
     28    cols(1) := xs$column_constraint_type(
     29      column_list => xs$list('salary'),
     30      privilege   => 'view_salary');
     31
     32    xs_data_security.create_policy(
     33      name                   => 'employees_ds',
     34      realm_constraint_list  => realms,
     35      column_constraint_list => cols);
     36  end;
     37  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL>
    SQL>
    SQL> -- Apply the data security policy to the table.
    SQL> begin
      2    xs_data_security.apply_object_policy(
      3      policy => 'employees_ds',
      4      schema => 'hr',
      5      object =>'employees');
      6  end;
      7  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL>
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> -- 4. SETUP - Validate the objects we have set up.
    SQL> ----------------------------------------------------------------------
    SQL> set serveroutput on;
    SQL> begin
      2    if (xs_diag.validate_workspace()) then
      3      dbms_output.put_line('All configurations are correct.');
      4    else
      5      dbms_output.put_line('Some configurations are incorrect.');
      6    end if;
      7  end;
      8  /
    Some configurations are incorrect.

    PL/SQL procedure successfully completed.

    SQL> -- XS$VALIDATION_TABLE contains validation errors if any.
    SQL> -- Expect no rows selected.
    SQL> select * from xs$validation_table order by 1, 2, 3, 4;

          CODE
    ----------
    DESCRIPTION
    --------------------------------------------------------------------------------
    OBJECT
    --------------------------------------------------------------------------------
    NOTE
    --------------------------------------------------------------------------------
         -1020
    No ACE in the ACL
    [ACL "SYS"."NETWORK_ACL_30D45882EF095A86E053B0AAE80AF5F8"]

    1 row selected.

    SQL>
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> -- 5. SETUP - additional configuration for Java demo.
    SQL> ----------------------------------------------------------------------
    SQL>
    SQL> connect sys/&passwd as sysdba
    Connected.
    SQL>
    SQL> -- create a session administrator who has only
    SQL> -- RAS session administration privilege (no data privilege),
    SQL> -- and is responsible to manage RAS session for each application user.
    SQL> grant xs_session_admin, create session to hr_session identified by hr_session;

    Grant succeeded.

    SQL> grant create session to hr_common identified by hr_common;

    Grant succeeded.

    SQL>
    SQL> -- craete a dispatcher user for java demo, to set up session for application user
    SQL> exec xs_principal.create_user(name=>'dispatcher', schema=>'HR');

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.set_password('dispatcher', 'welcome1');

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.grant_roles('dispatcher', 'XSCONNECT');

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.grant_roles('dispatcher', 'xsdispatcher');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> exit

#### C.3.2 hrdemo.log

The `hrdemo.log` file.

    SQL> @hrdemo
    SQL>
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> --  HR Demo - PL/SQL with RAS direct logon user
    SQL> ----------------------------------------------------------------------
    SQL> -- This demo shows RAS runtime, using RAS direct logon user.
    SQL> -- Each user directly connects to database and accesses employee table.
    SQL> -- RAS policy is automaticlly enforced.
    SQL> ---------------------------------------------------------------------
    SQL>
    SQL> -- Connect as DAUSTIN, who has only employee and it_engineer role
    SQL> conn daustin/welcome1;
    Connected.
    SQL>
    SQL> SET SECUREDCOL ON UNAUTH *******
    SQL>
    SQL> -- DAUSTIN can view the records in IT department, but can only view his own
    SQL> -- SALARY column.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees order by email;

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    AHUNOLD    Alexander       Hunold                     60        102 *******
    BERNST     Bruce           Ernst                      60        103 *******
    DAUSTIN    David           Austin                     60        103    4800
    DLORENTZ   Diana           Lorentz                    60        103 *******
    VPATABAL   Valli           Pataballa                  60        103 *******

    5 rows selected.

    SQL>
    SQL>
    SQL> SET SECUREDCOL OFF
    SQL>
    SQL>
    SQL> -- DAUSTIN cannot update the record.
    SQL> update employees set manager_id = 102 where email = 'DAUSTIN';

    0 rows updated.

    SQL>
    SQL> -- Record is not changed.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where email = 'DAUSTIN';

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    DAUSTIN    David           Austin                     60        103    4800

    1 row selected.

    SQL>
    SQL>
    SQL>
    SQL> -- Connect as SMAVRIS, who has both employee and hr_representative role.
    SQL> conn smavris/welcome1;
    Connected.
    SQL>
    SQL> -- SMAVRIS can view all the records including SALARY column.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where department_id = 60 or department_id = 40
      3  order by department_id, email;

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    SMAVRIS    Susan           Mavris                     40        101    6500
    AHUNOLD    Alexander       Hunold                     60        102    9000
    BERNST     Bruce           Ernst                      60        103    6000
    DAUSTIN    David           Austin                     60        103    4800
    DLORENTZ   Diana           Lorentz                    60        103    4200
    VPATABAL   Valli           Pataballa                  60        103    4800

    6 rows selected.

    SQL>
    SQL> -- EMPLOYEES table has 107 rows, we expect to see all of them.
    SQL> select count(*) from employees;

      COUNT(*)
    ----------
           107

    1 row selected.

    SQL>
    SQL>
    SQL>
    SQL> -- SMAVRIS can update the record.
    SQL> update employees set manager_id = 102 where email = 'DAUSTIN';

    1 row updated.

    SQL>
    SQL> -- Record is changed.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where email = 'DAUSTIN';

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    DAUSTIN    David           Austin                     60        102    4800

    1 row selected.

    SQL>
    SQL> -- change the record back to the original.
    SQL> update employees set manager_id = 103 where email = 'DAUSTIN';

    1 row updated.

    SQL>
    SQL> exit

#### C.3.3 hrdemo_run_sess.log

The `hrdemo_run_sess.log` file.

    SQL> @hrdemo_session
    SQL>
    SQL>
    SQL> ----------------------------------------------------------------------
    SQL> --  HR Demo - PL/SQL with Session API
    SQL> ----------------------------------------------------------------------
    SQL> -- This demo shows RAS runtime, using RAS user as application user.
    SQL> -- The user does not logon to database, but a RAS session is created
    SQL> -- and attached for each user before accessing employee table.
    SQL> ---------------------------------------------------------------------
    SQL>
    SQL> -- Connect as RAS session administrator
    SQL> connect hr_session/hr_session;
    Connected.
    SQL>
    SQL> -- Variable used to remember the session ID;
    SQL> var gsessionid varchar2(32);
    SQL>
    SQL> -- Create an application session for SMARVIS and attach to it.
    SQL> declare
      2    sessionid raw(16);
      3  begin
      4    dbms_xs_sessions.create_session('SMAVRIS', sessionid);
      5    :gsessionid := rawtohex(sessionid);
      6    dbms_xs_sessions.attach_session(sessionid, null);
      7  end ;
      8  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Display the current user, it should be SMAVRIS now.
    SQL> select xs_sys_context('xs$session','username') from dual;

    XS_SYS_CONTEXT('XS$SESSION','USERNAME')
    --------------------------------------------------------------------------------
    SMAVRIS

    1 row selected.

    SQL>
    SQL> -- Display the enabled application roles and database roles.
    SQL> select role_name from v$xs_session_roles union
      2  select role from session_roles order by 1;

    ROLE_NAME
    --------------------------------------------------------------------------------
    DB_EMP
    EMPLOYEE
    HR_REPRESENTATIVE
    XSCONNECT
    XSPUBLIC
    XS_CONNECT

    6 rows selected.

    SQL>
    SQL> -- SMAVRIS can view all the records including SALARY column.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where department_id = 60 or department_id = 40
      3  order by department_id, email;

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    SMAVRIS    Susan           Mavris                     40        101    6500
    AHUNOLD    Alexander       Hunold                     60        102    9000
    BERNST     Bruce           Ernst                      60        103    6000
    DAUSTIN    David           Austin                     60        103    4800
    DLORENTZ   Diana           Lorentz                    60        103    4200
    VPATABAL   Valli           Pataballa                  60        103    4800

    6 rows selected.

    SQL>
    SQL> -- EMPLOYEES table has 107 rows, we expect to see all of them.
    SQL> select count(*) from employees;

      COUNT(*)
    ----------
           107

    1 row selected.

    SQL>
    SQL> -- Disable hr_representative role
    SQL> exec dbms_xs_sessions.disable_role('hr_representative');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- SMAVRIS should only be able to see her own record.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where department_id = 60 or department_id = 40
      3  order by department_id, email;

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    SMAVRIS    Susan           Mavris                     40        101    6500

    1 row selected.

    SQL>
    SQL>
    SQL> -- Enable HR_ROLE
    SQL> exec dbms_xs_sessions.enable_role('hr_representative');

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- SMAVRIS can view all the records again.
    SQL> select email, first_name, last_name, department_id, manager_id, salary
      2  from employees where department_id = 60 or department_id = 40
      3  order by department_id, email;

    EMAIL      FIRST_NAME      LAST_NAME       DEPARTMENT_ID MANAGER_ID  SALARY
    ---------- --------------- --------------- ------------- ---------- -------
    SMAVRIS    Susan           Mavris                     40        101    6500
    AHUNOLD    Alexander       Hunold                     60        102    9000
    BERNST     Bruce           Ernst                      60        103    6000
    DAUSTIN    David           Austin                     60        103    4800
    DLORENTZ   Diana           Lorentz                    60        103    4200
    VPATABAL   Valli           Pataballa                  60        103    4800

    6 rows selected.

    SQL>
    SQL> -- EMPLOYEES table has 107 rows, we expect to see all of them.
    SQL> select count(*) from employees;

      COUNT(*)
    ----------
           107

    1 row selected.

    SQL>
    SQL> -- Detach and destroy the application session.
    SQL> declare
      2    sessionid raw(16);
      3  begin
      4    sessionid := hextoraw(:gsessionid);
      5    dbms_xs_sessions.detach_session;
      6    dbms_xs_sessions.destroy_session(sessionid);
      7  end;
      8  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL> exit

#### C.3.4 hrdemo.log

The Java `hrdemo.log` file.

    Query HR.EMPLOYEES table as user "DAUSTIN"
      EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY
      AHUNOLD|   Alexander|      Hunold|    60|   *****|   false|   false
       BERNST|       Bruce|       Ernst|    60|   *****|   false|   false
      DAUSTIN|       David|      Austin|    60|    4800|   false|    true
     DLORENTZ|       Diana|     Lorentz|    60|   *****|   false|   false
     VPATABAL|       Valli|   Pataballa|    60|   *****|   false|   false

    Query HR.EMPLOYEES table as user "SMAVRIS"
      EMAIL  | FIRST_NAME | LAST_NAME  | DEPT | SALARY | UPDATE | VIEW_SALARY
      AHUNOLD|   Alexander|      Hunold|    60|    9000|    true|    true
       BERNST|       Bruce|       Ernst|    60|    6000|    true|    true
      DAUSTIN|       David|      Austin|    60|    4800|    true|    true
      DFAVIET|      Daniel|      Faviet|   100|    9000|    true|    true
     DLORENTZ|       Diana|     Lorentz|    60|    4200|    true|    true
     ISCIARRA|      Ismael|     Sciarra|   100|    7700|    true|    true
        JCHEN|        John|        Chen|   100|    8200|    true|    true
      JMURMAN| Jose Manuel|       Urman|   100|    7800|    true|    true
        LPOPP|        Luis|        Popp|   100|    6900|    true|    true
     NGREENBE|       Nancy|   Greenberg|   100|   12008|    true|    true
      SMAVRIS|       Susan|      Mavris|    40|    6500|    true|    true
     VPATABAL|       Valli|   Pataballa|    60|    4800|    true|    true

#### C.3.5 hrdemo_clean.log

The `hrdemo_clean.log` file.

    SQL> @hrdemo_clean
    SQL>
    SQL> define passwd=&1
    Enter value for 1: test
    SQL>
    SQL> connect hr/hr;
    Connected.
    SQL>
    SQL> -- Remove policy from the table.
    SQL> begin
      2    xs_data_security.remove_object_policy(policy=>'employees_ds',
      3                                          schema=>'hr', object=>'employees');
      4  end;
      5  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Delete security class and ACLs
    SQL> exec xs_security_class.delete_security_class('hr_privileges', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_acl.delete_acl('emp_acl', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_acl.delete_acl('it_acl', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_acl.delete_acl('hr_acl', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Delete data security policy
    SQL> exec xs_data_security.delete_policy('employees_ds', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> connect sys/&passwd as sysdba
    Connected.
    SQL> -- Delete application users and roles
    SQL> exec xs_principal.delete_principal('employee', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.delete_principal('hr_representative', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.delete_principal('it_engineer', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.delete_principal('smavris', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL> exec xs_principal.delete_principal('daustin', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> -- Delete database role
    SQL> drop role db_emp;

    Role dropped.

    SQL>
    SQL> -- Delete session administrator
    SQL> drop user hr_session;

    User dropped.

    SQL> -- Delete the common user used to connect to DB
    SQL> drop user hr_common;

    User dropped.

    SQL>
    SQL> -- Delete dispatcher
    SQL> exec xs_principal.delete_principal('dispatcher', xs_admin_util.cascade_option);

    PL/SQL procedure successfully completed.

    SQL>
    SQL> exit
