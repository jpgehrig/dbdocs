Oracle provides advanced functionality for Oracle Label Security, such as the ability to analyze relationships between labels.

- Analyzing the Relationships Between Labels
  You can analyze the relationships between labels.
- Queries for Audited Oracle Label Security Session Labels
  You can use the unified audit trail to capture information from various audit sources, including Oracle Label Security.
- Oracle Call Interface for Setting Session Labels
  You can use an Oracle Call Interface (OCI) to set session labels.

**Parent topic:** [Appendixes](part4.md)

### B.1 Analyzing the Relationships Between Labels

You can analyze the relationships between labels.

- About Dominant and Dominated Labels
  The relationship between two labels can be described in terms of dominance.
- Non-Comparable Labels
  It is important to understand how labels can be compared with regard to dominance.
- Using Dominance Functions
  Oracle Label Security provides functions to control dominance.

**Parent topic:** Advanced Topics in Oracle Label Security

#### B.1.1 About Dominant and Dominated Labels

The relationship between two labels can be described in terms of dominance.

A user's ability to access an object depends on whether the user's label dominates the label of the object. If a user's label does not dominate the object's label, then the user is not allowed to access the object.

Label dominance is analyzed in terms of all its components: levels, compartments, and groups.

Table B-1 Dominance in the Comparison of Labels

| Factor      | Criteria for Dominance                                                                                         |
|:------------|:---------------------------------------------------------------------------------------------------------------|
| Level       | For `label1` to dominate `label2`, the level of `label1` must be greater than or equal to that of `label2`.    |
| Compartment | For `label1` to dominate `label2`, the compartments of `label1` must contain all the compartments of `label2`. |
| Group       | For `label1` to dominate `label2`, `label1` must contain at least one of the groups of `label2`.               |

One label dominates another label if all of its components dominate the components of the other label. For example, the label `HIGHLY_SENSITIVE`:`FINANCE`,`OPERATIONS` dominates the label `HIGHLY_SENSITIVE:FINANCE`. Similarly, the label `HIGHLY_SENSITIVE::WR_AP` dominates the label `HIGHLY_SENSITIVE::WR_AP, WR_AR`.

**Related Topics**

- [Dominance Rules for Labels with Inverse Groups](releasability-using-inverse-groups.md)

**Parent topic:** Analyzing the Relationships Between Labels

#### B.1.2 Non-Comparable Labels

It is important to understand how labels can be compared with regard to dominance.

The relationship between two labels cannot always be defined by dominance. Two labels are non-comparable if neither label dominates the other.

If any compartments differ between the two labels (as with `HS:A` and `HS:B`), then they are non-comparable. Similarly, the labels `HS:A` and `S:B` are non-comparable.

You can find existing labels by querying the DBA_SA_LABELS data dictionary view.

**Parent topic:** Analyzing the Relationships Between Labels

#### B.1.3 Using Dominance Functions

Oracle Label Security provides functions to control dominance.

- About the Dominance Functions
  You can use dominance functions to specify ranges in queries.
- OLS_DOMINATES Standalone Function
  The `OLS_DOMINATES` (`OLS_DOM`) function returns `1` (`TRUE`) if `label1` dominates `label2`, or `0` (`FALSE`) if it does not.
- OLS_LABEL_DOMINATES Standalone Function
  The standalone `OLS_LABEL_DOMINATES` function checks the dominance of session labels.
- OLS_STRICTLY_DOMINATES Standalone Function
  The `OLS_STRICTLY_DOMINATES` (`OLS_S_DOM`) function returns `1` (`TRUE`) if `label1` dominates `label2` and is not equal to it.
- OLS_DOMINATED_BY Standalone Function
  The `OLS_DOMINATED_BY` (`OLS_DOM_BY`) function returns `1` (`TRUE`) if `label1` is dominated by `label2`.
- OLS_STRICTLY_DOMINATED_BY Standalone Function
  The `OLS_STRICTLY_DOMINATED_BY` (`OLS_S_DOM_BY`) function returns `1` (`TRUE`) if `label1` is dominated by `label2` and is not equal to it.
- SA_UTL.DOMINATES
  The `SA_UTL.DOMINATES` function returns `TRUE` if `label1` dominates `label2` or if the session label for the given OLS policy dominates `label`.
- SA_UTL.STRICTLY_DOMINATES
  The `SA_UTL.STRICTLY_DOMINATES` function returns `TRUE` if `label1` dominates `label2` and is not equal to it.
- SA_UTL.DOMINATED_BY
  The `SA_UTL.DOMINATED_BY` function returns `TRUE` if `label1` is dominated by `label2`.
- SA_UTL.STRICTLY_DOMINATED_BY
  The `SA_UTL.STRICTLY_DOMINATED_BY` function returns `TRUE` if `label1` is dominated by `label2` and is not equal to it.

**Related Topics**

- [Ordering Labeled Data Rows](working-with-labeled-data.md)

**Parent topic:** Analyzing the Relationships Between Labels

##### B.1.3.1 About the Dominance Functions

You can use dominance functions to specify ranges in queries.

The following functions enable you to indicate dominance relationships between specified labels.

Table B-2 Functions to Determine Dominance

| Function                    | Description                                                                                                    |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------|
| `OLS_DOMINATES`             | The value of `label1` dominates, or is equal to, that of `label2`.                                             |
| `OLS_LABEL_DOMINATES`       | The value of the session label for the corresponding `policy_name` dominates, or is equal to, that of `label`. |
| `OLS_STRICTLY_DOMINATES`    | The value of `label1` dominates that of `label2`, and is not equal to it.                                      |
| `OLS_DOMINATED_BY`          | The value of `label1` is dominated by that of `label2`.                                                        |
| `OLS_STRICTLY_DOMINATED_BY` | The value of `label1` is dominated by that of `label2`, and is not equal to it.                                |

Note that there are two types of dominance function. While the `SA_UTL` dominance functions return `BOOLEAN` values, the standalone dominance functions return integers.

**Parent topic:** Using Dominance Functions

##### B.1.3.2 OLS_DOMINATES Standalone Function

The `OLS_DOMINATES` (`OLS_DOM`) function returns `1` (`TRUE`) if `label1` dominates `label2`, or `0` (`FALSE`) if it does not.

##### Syntax

    OLS_DOMINATES (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN INTEGER;

##### Parameters

Table B-3 OLS_DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SELECT OLS_DOMINATES ('1111', '1112') FROM DUAL;

    OLS_DOMINATES('1111','1112')
    ----------------------------
                               0

**Note:**

The old OLS functions, `DOMINATES` and `DOM`, have been deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_LABEL_DOMINATES` and `OLS_DOM` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Using Dominance Functions

##### B.1.3.3 OLS_LABEL_DOMINATES Standalone Function

The standalone `OLS_LABEL_DOMINATES` function checks the dominance of session labels.

It returns `1` (`TRUE`) if the session label of the specified `policy_name` value dominates or is equal to the label that is specified by the `label` parameter. Otherwise, this function returns `0` (`FALSE`). This function is publicly available.

**Note:**

This feature is available starting with Oracle Database 12c release 1 (12.1.0.2).

In addition to Oracle Label Security policies, you can use this function with both Oracle Data Redaction and Oracle Database Vault policies.

##### Syntax

    OLS_LABEL_DOMINATES (
      policy_name    IN VARCHAR2,
      label          IN VARCHAR2)
    RETURN INTEGER;

##### Parameters

Table B-4 OLS_LABEL_DOMINATES Parameters

| Parameter     | Description                                                                                                                                                                                                          |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | The name of the Oracle Label Security policy whose session label must be checked for dominance. To find existing label values for policies, query the `POLICY_NAME` and `LABEL` columns of the `ALL_SA_LABELS` view. |
| `label`       | The base label against whom the dominance has to be checked                                                                                                                                                          |

##### Examples

The following example checks if the session label for the `hr_ols_pol` policy dominates or is equal to the `hs` label.

    SELECT OLS_LABEL_DOMINATES ('hr_ols_pol', 'hs') FROM DUAL;

    OLS_LABEL_DOMINATES('HR_OLS_POL','HS')
    --------------------------------------
                                         0

This example shows how you can use the `OLS_LABEL_DOMINATES` function in an Oracle Data Redaction policy:

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema   => 'oe',
       object_name     => 'customers',
       column_name     => 'customer_id',
       policy_name     => 'redact_cust_user_ids',
       function_type   => DBMS_REDACT.FULL,
       expression      => 'OLS_LABEL_DOMINATES(''hr_ols_pol'', ''hs'') = 0');
    END;
    /

The following example shows how you can use the `OLS_LABEL_DOMINATES` function in an Oracle Database Vault rule definition:

    EXEC DBMS_MACADM.CREATE_RULE('Check OLS Factor', 'OLS_LABEL_DOMINATES(''hr_ols_pol'', ''hs'') = 1');

**See Also:**

- [Oracle Database Advanced Security Guide](../asoag/introduction-to-oracle-data-redaction.md) for more information about Data Redaction

- [Oracle Database Vault Administrator’s Guide](../dvadm/configuring-realms.md) for more information about Database Vault realms

**Parent topic:** Using Dominance Functions

##### B.1.3.4 OLS_STRICTLY_DOMINATES Standalone Function

The `OLS_STRICTLY_DOMINATES` (`OLS_S_DOM`) function returns `1` (`TRUE`) if `label1` dominates `label2` and is not equal to it.

##### Syntax

    OLS_STRICTLY_DOMINATES (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN INTEGER;

##### Parameters

Table B-5 OLS_STRICTLY_DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Examples

The following example compares existing label tags `1111` and `1112`.

    SELECT OLS_STRICTLY_DOMINATES ('1111', '1112') FROM DUAL;

    OLS_STRICTLY_DOMINATES('1111','1112')
    -------------------------------------
                                        0

**Note:**

The old OLS functions, `STRICTLY_DOMINATES` and `S_DOM` have been deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_STRICTLY_DOMINATES` and `OLS_S_DOM` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Using Dominance Functions

##### B.1.3.5 OLS_DOMINATED_BY Standalone Function

The `OLS_DOMINATED_BY` (`OLS_DOM_BY`) function returns `1` (`TRUE`) if `label1` is dominated by `label2`.

##### Syntax

    OLS_DOMINATED_BY (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN INTEGER;

##### Parameters

Table B-6 OLS_STRICTLY_DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SELECT OLS_DOMINATED_BY ('1111', '1112') FROM DUAL;

    OLS_DOMINATED_BY('1111','1112')
    -------------------------------
                                  1

**Note:**

The old OLS functions, `DOMINATED_BY` and `DOM_BY` have been deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_DOMINATED_BY` and `OLS_DOM_BY` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Using Dominance Functions

##### B.1.3.6 OLS_STRICTLY_DOMINATED_BY Standalone Function

The `OLS_STRICTLY_DOMINATED_BY` (`OLS_S_DOM_BY`) function returns `1` (`TRUE`) if `label1` is dominated by `label2` and is not equal to it.

##### Syntax

    OLS_STRICTLY_DOMINATED_BY (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN INTEGER;

##### Parameters

Table B-7 OLS_DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SELECT OLS_STRICTLY_DOMINATES ('1111', '1112') FROM DUAL;

    OLS_STRICTLY_DOMINATES('1111','1112')
    -------------------------------------
                                        0

**Note:**

The old OLS functions, `STRICTLY_DOMINATED_BY` and `S_DOM_BY` have been deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_STRICTLY_DOMINATED_BY` and `OLS_S_DOM_BY` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Using Dominance Functions

##### B.1.3.7 SA_UTL.DOMINATES

The `SA_UTL.DOMINATES` function returns `TRUE` if `label1` dominates `label2` or if the session label for the given OLS policy dominates `label`.

##### Syntax

    SA_UTL.DOMINATES (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN BOOLEAN;

##### Syntax

    SA_UTL.DOMINATES (
      ols_policy_name  IN VARCHAR2,
      label            IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameters

Table B-8 SA_UTL.DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_UTL.DOMINATES(1111, 1112)
      THEN DBMS_OUTPUT.PUT_LINE('Label 1111 dominates label 1112.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('Label 1112 dominates label 1111.');
     END IF;
    END;
    /

    Label 1112 dominates label 1111.

**Note:**

The second `SA_UTL.DOMINATES` function, which takes the Oracle Label Security policy name and label as inputs, has been deprecated in Oracle Database 12c release 1 (12.1).

You can still use this function, but not with Oracle Data Redaction and Oracle Database Vault conditions. Oracle recommends that you use the `OLS_LABEL_DOMINATES` function instead.

The first `SA_UTL.DOMINATES` function, which uses the `NUMBER` datatype, is not deprecated.

**Parent topic:** Using Dominance Functions

##### B.1.3.8 SA_UTL.STRICTLY_DOMINATES

The `SA_UTL.STRICTLY_DOMINATES` function returns `TRUE` if `label1` dominates `label2` and is not equal to it.

##### Syntax

    SA_UTL.STRICTLY_DOMINATES (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN BOOLEAN;

##### Parameters

Table B-9 SA_UTL.STRICTLY_DOMINATES Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_UTL.STRICTLY_DOMINATES(1111, 1112)
      THEN DBMS_OUTPUT.PUT_LINE('Label 1111 strictly dominates label 1112.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('Label 1112 strictly dominates label 1111.');
     END IF;
    END;
    /

    Label 1112 strictly dominates label 1111.

**Parent topic:** Using Dominance Functions

##### B.1.3.9 SA_UTL.DOMINATED_BY

The `SA_UTL.DOMINATED_BY` function returns `TRUE` if `label1` is dominated by `label2`.

##### Syntax

    SA_UTL.DOMINATED_BY (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN BOOLEAN;

##### Parameters

Table B-10 SA_UTL.DOMINATED_BY Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_UTL.DOMINATED_BY(1111, 1112)
      THEN DBMS_OUTPUT.PUT_LINE('Label 1111 is dominated by label 1112.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('Label 1112 is dominated by label 1111.');
     END IF;
    END;
    /

    Label 1111 is dominated by label 1112.

**Parent topic:** Using Dominance Functions

##### B.1.3.10 SA_UTL.STRICTLY_DOMINATED_BY

The `SA_UTL.STRICTLY_DOMINATED_BY` function returns `TRUE` if `label1` is dominated by `label2` and is not equal to it.

##### Syntax

    SA_UTL.STRICTLY_DOMINATED_BY (
      label1          IN NUMBER,
      label2          IN NUMBER)
    RETURN BOOLEAN;

##### Parameters

Table B-11 SA_UTL.STRICTLY_DOMINATED_BY Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing label tags `1111` and `1112`.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_UTL.STRICTLY_DOMINATED_BY(1111, 1112)
      THEN DBMS_OUTPUT.PUT_LINE('Label 1111 is strictly dominated by label 1112.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('Label 1112 is strictly dominated by label 1111.');
     END IF;
    END;
    /

    Label 1111 is strictly dominated by label 1112.

**Related Topics**

- [Determination of the Upper and Lower Bounds of Labels](working-with-labeled-data.md)

**Parent topic:** Using Dominance Functions

### B.2 Queries for Audited Oracle Label Security Session Labels

You can use the unified audit trail to capture information from various audit sources, including Oracle Label Security.

- About Queries for Auditing Oracle Label Security Session Labels
  You must configure Oracle Label Security auditing by creating unified audit policies.
- ORA_GET_AUDITED_LABEL Function
  The `ORA_GET_AUDITED_LABEL` function returns the audited session label for the specified OLS policy and `APPLICATION_CONTEXTS` column value.

**Parent topic:** Advanced Topics in Oracle Label Security

#### B.2.1 About Queries for Auditing Oracle Label Security Session Labels

You must configure Oracle Label Security auditing by creating unified audit policies.

OLS auditing enables you to audit additional events such as enabling and disabling of OLS policies.

The session labels that the audit trail captures are stored in the `APPLICATION_CONTEXTS` column of the `UNIFIED_AUDIT_TRAIL` view. You can use the `LBACSYS.ORA_GET_AUDITED_LABEL` function to retrieve session labels that are stored in the `APPLICATION_CONTEXTS` column. This function accepts the `UNIFIED_AUDIT_TRAIL.APPLICATION_CONTEXTS` column value, and the Oracle Label Security policy name as arguments, and then returns the session label that is stored in the column for the specified policy.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) for detailed information about configuring and using OLS auditing in a unified audit trail

**Parent topic:** Queries for Audited Oracle Label Security Session Labels

#### B.2.2 ORA_GET_AUDITED_LABEL Function

The `ORA_GET_AUDITED_LABEL` function returns the audited session label for the specified OLS policy and `APPLICATION_CONTEXTS` column value.

The `AUDIT_VIEWER` role has `EXECUTE` privilege on the `ORA_GET_AUDITED_LABEL` function.

##### Syntax

    ORA_GET_AUDITED_LABEL (
      appctx_col_value   IN VARCHAR2,
      ols_policy_name    IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table B-12 ORA_GET_AUDITED_LABEL Parameters

| Parameter          | Description                                                    |
|:-------------------|:---------------------------------------------------------------|
| `appctx_col_value` | Value in the `UNIFIED_AUDIT_TRAIL.APPLICATION_CONTEXTS` column |
| `policy_name`      | The label security policy name                                 |

##### Example

The following example returns the audited session label for the `hr_ols_pol` policy.

    SELECT ORA_GET_AUDITED_LABEL ('cust_ctx', 'hr_ols_pol') FROM DUAL;

    ORA_GET_AUDITED_LABEL('X','HR_OLS_POL')
    ---------------------------------------
                                         HS

**Parent topic:** Queries for Audited Oracle Label Security Session Labels

### B.3 Oracle Call Interface for Setting Session Labels

You can use an Oracle Call Interface (OCI) to set session labels.

- About Using the Oracle Call Interface to Set Session Labels
  When you connect using Oracle Call Interface (OCI), you can use the `SYS_CONTEXT` variables to initialize the session label and the row label.
- Using the Oracle Call Interface to Set Session Labels
  You can use the Oracle Call Interface to set the session labels.
- Example: Using Oracle Call Interface with the SYS_CONTEXT Function
  You can create an OCI call that uses an externalized `SYS_CONTEXT` function with Oracle Label Security.

**Parent topic:** Advanced Topics in Oracle Label Security

#### B.3.1 About Using the Oracle Call Interface to Set Session Labels

When you connect using Oracle Call Interface (OCI), you can use the `SYS_CONTEXT` variables to initialize the session label and the row label.

You can set the variables using the `OCIAttrSet` function to initialize externally initialized `SYS_CONTEXT` variables. These are available when Oracle Label Security is enabled.

Each policy has a `SYS_CONTEXT` named `SA$``policy_name``_X`. You can set these two variables, `INITIAL_LABEL` and `INITIAL_ROW_LABEL`.

When the new values are set to valid labels within the user's authorizations, they will be used instead of the default values stored for the user. This is the same mechanism used for remote connections.

**Related Topics**

- [Using Oracle Label Security with a Distributed Database](using-oracle-label-security-with-a-distributed-database.md)

**Parent topic:** Oracle Call Interface for Setting Session Labels

#### B.3.2 Using the Oracle Call Interface to Set Session Labels

You can use the Oracle Call Interface to set the session labels.

1.  Call `OCIAttrSet` with `OCI_ATTR_APPCTX_SIZE` to initialize the context array size with the desired number of context attributes:
        OCIAttrSet(session, OCI_HTYPE_SESSION,
                         (dvoid *)&size, (ub4)0, OCI_ATTR_APPCTX_SIZE, error_handle);


    This defines additional attributes for `OCIAttrSet`.

    Note that the size is `ub4` type.
2.  Call `OCIAttrGet` with `OCI_ATTR_APPCTX_LIST` to get a handle on the application context list descriptor for the session:
        OCIAttrGet(session, OCI_HTYPE_SESSION,
                       (dvoid *)&ctxl_desc, (ub4)0, OCI_ATTR_APPCTX_LIST, error_handle);

    Note that `ctxl_desc` is (`OCIParam *`) type.
3.  Call `OCIParamGet` with the application context list descriptor to obtain an individual descriptor for the i-th application context:
        OCIParamGet(ctxl_desc, OCI_DTYPE_PARAM, error_handle,(dvoid **)&ctx_desc, i);

    Note that `ctx_desc` is (`OCIParam *`) type.
4.  Call `OCIAttrSet` with each of the three new attributes, `OCI_ATTR_APPCTX_NAME`, `OCI_ATTR_APPCTX_ATTR`, and `OCI_ATTR_APPCTX_VALUE`, to set the proper values in the application context:
        OCIAttrSet(ctx_desc, OCI_DTYPE_PARAM,
                         (dvoid *)ctx_name, sizeof(ctx_name), OCI_ATTR_APPCTX_NAME,
                         error_handle);

        OCIAttrSet(ctx_desc, OCI_DTYPE_PARAM,
                         (dvoid *)attr_name, sizeof(attr_name), OCI_ATTR_APPCTX_ATTR,
                         error_handle);

        OCIAttrSet(ctx_desc, OCI_DTYPE_PARAM,
                         (dvoid *)value, sizeof(value), OCI_ATTR_APPCTX_VALUE,
                         error_handle);

    Note that only character type is supported, because application context operations are based on the `VARCHAR2` type.

**Parent topic:** Oracle Call Interface for Setting Session Labels

#### B.3.3 Example: Using Oracle Call Interface with the SYS_CONTEXT Function

You can create an OCI call that uses an externalized `SYS_CONTEXT` function with Oracle Label Security.

Example B-1 shows how to accomplish this.

Example B-1 Using OCI to Externalize SYS_CONTEXT with OLS

    #ifdef RCSID
    static char *RCSid =
       "$Header: ext_mls.c 09-may-00.10:07:08 jdoe Exp $ ";
    #endif /* RCSID */

    /* Copyright (c) Oracle Corporation 1999, 2000. All Rights Reserved. */

    /*

       NAME
    ext_mls.c - externalized SYS_CONTEXT with Label Security

       DESCRIPTION
    Run olsdemo.sql script before executing this example.
    Usage: <executable obtained with .c file> <user_name> <password> <session-initial-label
    Example: avg_sal sa_demo sa_demo L3:M,E:D10

       PUBLIC FUNCTION(S)
    <list of external functions declared/defined - with one-line descriptions>

       PRIVATE FUNCTION(S)
    <list of static functions defined in .c file - with one-line descriptions>

       RETURNS
    The average salary in the EMP table of the SA_DEMO schema querying as the specified user with the specified session label.

       NOTES
    <other useful comments, qualifications, and so on>

       MODIFIED   (MM/DD/YY)
    jlev      09/18/03 - cleanup
    jdoe      05/09/00 - cleanup
       jdoe      10/13/99 - standalone OCI program to test MLS SYS_CONTEXT
       jdoe      10/13/99 - Creation

    */
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <oci.h>

    static OCIEnv *envhp;
    static OCIError *errhp;

    int main(/*_ int argc, char *argv[] _*/);

    /* get and print error */
    static void checkerr(/*_OCIError *errhp, sword status _*/);
    /* print error */
    static void printerr(char *call);
    static sword status;

    /* return the average of employees' salary */
    static CONST text *const selectstmt = (text *)
         "select avg(sal) from sa_demo.emp";

    int main(argc, argv)
    int argc;
    char *argv[];
    {
      OCISession *authp = (OCISession *) 0;
      OCIServer *srvhp;
      OCISvcCtx *svchp;
      OCIDefine *defnp = (OCIDefine *) 0;
      dvoid *parmdp;
      ub4 ctxsize;
      OCIParam *ctxldesc;
      OCIParam *ctxedesc;
      OCIStmt *stmtp = (OCIStmt *) 0;
      ub4 avg_sal = 0;
      sword status;

      if (OCIInitialize((ub4) OCI_DEFAULT, (dvoid *) 0,
                        (dvoid * (*)(dvoid *, size_t)) 0,
                        (dvoid * (*)(dvoid *, dvoid *, size_t)) 0,
                        (void (*)(dvoid *, dvoid *)) 0))
        printerr("OCIInitialize");

      if (OCIEnvInit((OCIEnv **) &envhp, OCI_DEFAULT, (size_t) 0, (dvoid **) 0))
        printerr("OCIEnvInit");

      if (OCIHandleAlloc((dvoid *) envhp, (dvoid **) &errhp, OCI_HTYPE_ERROR,
                         (size_t) 0, (dvoid **) 0))
        printerr("OCIHandleAlloc:OCI_HTYPE_ERROR");

      if (OCIHandleAlloc((dvoid *) envhp, (dvoid **) &srvhp, OCI_HTYPE_SERVER,
                         (size_t) 0, (dvoid **) 0))
        printerr("OCIHandleAlloc:OCI_HTYPE_SERVER");

      if (OCIHandleAlloc((dvoid *) envhp, (dvoid **) &svchp, OCI_HTYPE_SVCCTX,
                         (size_t) 0, (dvoid **) 0))
        printerr("OCIHandleAlloc:OCI_HTYPE_SVCCTX");

      if (OCIServerAttach(srvhp, errhp, (text *) "", strlen(""), 0))
        printerr("OCIServerAttach");

      /* set attribute server context in the service context */
      if (OCIAttrSet((dvoid *) svchp, OCI_HTYPE_SVCCTX, (dvoid *) srvhp,
                     (ub4) 0, OCI_ATTR_SERVER, (OCIError *) errhp))
        printerr("OCIAttrSet:OCI_HTYPE_SVCCTX");

      if (OCIHandleAlloc((dvoid *) envhp, (dvoid **) &authp,
                         (ub4) OCI_HTYPE_SESSION, (size_t) 0, (dvoid **) 0))
        printerr("OCIHandleAlloc:OCI_HTYPE_SESSION");

      /* set application context to 1 */
      ctxsize = 1;

      /* set up app ctx buffer */
      if (OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_SESSION, (dvoid *) &ctxsize,
                     (ub4) 0, (ub4) OCI_ATTR_APPCTX_SIZE, errhp))
        printerr("OCIAttrSet:OCI_ATTR_APPCTX_SIZE");

      /* retrieve the list descriptor */
      if (OCIAttrGet((dvoid *) authp, (ub4) OCI_HTYPE_SESSION,
                     (dvoid *) &ctxldesc, 0, OCI_ATTR_APPCTX_LIST, errhp))
        printerr("OCIAttrGet:OCI_ATTR_APPCTX_LIST");

      if (status = OCIParamGet(ctxldesc, OCI_DTYPE_PARAM, errhp,
                               (dvoid **) &ctxedesc, 1))
        {
          if (status == OCI_NO_DATA)
            {
              printf("No Data found!\n");
              exit(1);
            }
        }

      /* set context namespace to SA$<pol_name>_X */
      if (OCIAttrSet((dvoid *) ctxedesc, (ub4) OCI_DTYPE_PARAM,
                     (dvoid *) "SA$HUMAN_RESOURCES_X",
                     (ub4) strlen((char *) "SA$HUMAN_RESOURCES_X"),
                     (ub4) OCI_ATTR_APPCTX_NAME, errhp))
        printerr("OCIAttrSet:OCI_ATTR_APPCTX_NAME:SA$HUMAN_RESOURCES_X");

      /* set context attribute to INITIAL_LABEL */
      if (OCIAttrSet((dvoid *) ctxedesc, (ub4) OCI_DTYPE_PARAM,
                     (dvoid *) "INITIAL_LABEL",
                     (ub4) strlen((char *) "INITIAL_LABEL"),
                     (ub4) OCI_ATTR_APPCTX_ATTR, errhp))
        printerr("OCIAttrSet:OCI_DTYPE_PARAM:INITIAL_LABEL");

      /* set context value to argv[3] - initial label */
      if (OCIAttrSet((dvoid *) ctxedesc, (ub4) OCI_DTYPE_PARAM,
                     (dvoid *) argv[3],
                     (ub4) strlen((char *) argv[3]),
                     (ub4) OCI_ATTR_APPCTX_VALUE, errhp))
        printerr("OCIAttrSet:argv[3]");

      /* username first command line argument */
      if (OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_SESSION, (dvoid *) argv[1],
                     (ub4) strlen((char *) argv[1]), (ub4) OCI_ATTR_USERNAME,
                     errhp))
        printerr("OCIAttrSet:username");

      /* password second command line argument */
      if (OCIAttrSet((dvoid *) authp, (ub4) OCI_HTYPE_SESSION, (dvoid *) argv[2],
                     (ub4) strlen((char *) argv[2]), (ub4) OCI_ATTR_PASSWORD,
                     errhp))
        printerr("OCIAttrSet:password");

      if (OCISessionBegin(svchp, errhp, authp, OCI_CRED_RDBMS, (ub4) OCI_DEFAULT))
        printerr("OCISessionBegin");

      if (OCIAttrSet((dvoid *) svchp, (ub4) OCI_HTYPE_SVCCTX, (dvoid *) authp,
                     (ub4) 0, (ub4) OCI_ATTR_SESSION, errhp))
        printerr("OCIAttrSet:OCI_ATTR_SESSION");

      if (OCIHandleAlloc((dvoid *) envhp, (dvoid **) &stmtp, OCI_HTYPE_STMT,
                         0, 0))
        printerr("OCIHandleAlloc:OCI_HTYPE_STMT");

      if (OCIStmtPrepare(stmtp, errhp, (CONST OraText *) selectstmt,
                         (ub4) strlen((const char *) selectstmt),
                         (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT))
        printerr("OCIStmtPrepare");

      if (OCIDefineByPos(stmtp, &defnp, errhp, (ub4) 1, (dvoid *) &avg_sal,
                         (sb4) sizeof(avg_sal), SQLT_INT, 0, 0, 0, OCI_DEFAULT))
        printerr("OCIDefineByPos");

      if (status = OCIStmtExecute(svchp, stmtp, errhp, 1, 0, NULL, NULL,
                                  OCI_DEFAULT))
        {
          if (status == OCI_NO_DATA)
            {
              printf("No Data found!\n");
              exit(1);
            }
        }

      if (OCISessionEnd(svchp, errhp, authp, OCI_DEFAULT))
        printerr("OCISessionEnd");

      printf("average salary is: %d\n", avg_sal);
    }

    void checkerr(errhp, status)
         OCIError *errhp;
         sword status;
    {
      text errbuf[512];
      sb4 errcode = 0;

      switch (status)
        {
        case OCI_ERROR:
          (void) OCIErrorGet((dvoid *) errhp, 1, NULL, &errcode, errbuf,
                             (ub4) sizeof(errbuf), OCI_HTYPE_ERROR);
          printf("Error - %.*s\n", 512, errbuf);
          break;
        default:
          break;
        }
    }

    void printerr(call)
         char *call;
    {
      printf("Error: %s\n", call);
    }
    /* end of file ext_mls.c */

**Parent topic:** Oracle Call Interface for Setting Session Labels
