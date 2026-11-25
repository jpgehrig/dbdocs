Customers have frequently asked questions about Oracle Label Security.

- Who Uses Oracle Label Security?
  Sensitivity labels can categorize data in virtually every industry.
- How Can Oracle Label Security Address My Security Needs?
  Oracle Label Security can label data and restrict access with a high degree of granularity.
- Should I Use Oracle Label Security to Protect All My Tables?
  No, you should not use Oracle Label Security to protect all of your tables.
- What Is the Difference Between Oracle Virtual Private Database and Oracle Label Security?
  Oracle Virtual Private Database (VPD) is provided at no additional cost with the Enterprise Edition of Oracle Database.
- Can I Combine Oracle Virtual Private Database and Oracle Label Security?
  Yes. You can use a `WHERE` clause or a VPD policy.
- Can I Use Oracle Label Security with Oracle E-Business Suite?
  Oracle Applications use Oracle Virtual Private Database (VPD) to provide new functionality and security protections.
- Can I Use Oracle Label Security with Oracle Database Vault?
  Oracle Database Vault and Oracle Label Security can be used together within the same database.
- Does Oracle Label Security Provide Column-Level Access Control?
  No, Oracle Label Security is not column aware.
- Can I Base Secure Application Roles on Oracle Label Security?
  Yes, you can base secure application roles on Oracle Label Security.
- What Are Trusted Stored Program Units?
  Trusted stored program units are stored procedures, functions, and packages that execute with the system and object privileges (DAC) of the definer.
- Does VPD or OLS Add an Additional Column to the Protected Table?
  When you apply an Oracle Label Security (OLS) policy to a table, the policy adds an additional column to the table.
- Why Should the Additional OLS Row Label Column Be Hidden?
  Most applications are designed with access control mechanisms in mind, so Oracle Label Security must do this transparently.

**Parent topic:** [Appendixes](part4.md)

### H.1 Who Uses Oracle Label Security?

Sensitivity labels can categorize data in virtually every industry.

These industries include health care, law enforcement, energy, retail, national security, and defense industries.

The following list gives some examples of sensitivity labels:

- Internal

- ConfidentialPhysician OnlyHighly SensitiveWidget CorporationConfidential: Chicago OperationSensitive: Finance : EuropeTop SecretUnclassified

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.2 How Can Oracle Label Security Address My Security Needs?

Oracle Label Security can label data and restrict access with a high degree of granularity.

This is especially useful when multiple organizations or companies share a single application. Sensitivity labels can be used to restrict application users to an organization or to a subset of data within an organization.

Data privacy is important to consumers and regulatory measures continue to be announced. Oracle Label Security can be used to implement privacy policies on data, restricting access to only those who have a need-to-know.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.3 Should I Use Oracle Label Security to Protect All My Tables?

No, you should not use Oracle Label Security to protect all of your tables.

The traditional Oracle discretionary access control (DAC) object privileges such as `SELECT`, `INSERT`, `UPDATE`, and `DELETE` combined with database roles and stored procedures are sufficient in most cases. You can find a user’s privileges by querying the DBA_SYS_PRIVS data dictionary view.

In addition, there are many other ways that you can protect access to your database tables, such using Oracle Virtual Private Database (VPD), Oracle Database Vault, Oracle Data Redaction, Transparent Data Encryption (TDE), or Transparent Sensitive Data Protection (TSDP).

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.4 What Is the Difference Between Oracle Virtual Private Database and Oracle Label Security?

Oracle Virtual Private Database (VPD) is provided at no additional cost with the Enterprise Edition of Oracle Database.

Oracle Label Security is an add-on security option for the Oracle Database Enterprise Edition.

Oracle VPD is a term used for several powerful security features like, fine grained access control (FGAC), application context and global application context. VPD policies are written using `PL/SQL`, and can be assigned to an individual table or view. An information request, that accesses a table or view protected by VPD, is modified according to the policy assigned to the table or view.

VPD policies can be as simple as enforcing access during business hours. VPD policies can restrict access by comparing the value of an attribute in an individual row with an application context value. Global application context allows an application context to be accessed across multiple database sessions, reducing or eliminating the need to create a separate application context for each user session.

Oracle Label Security is an out-of-the-box solution for row level security. No coding or software development is required, allowing the administrator to focus completely on the policy. Oracle Label Security provides an interface for creating policies, specifying enforcement options, defining data sensitivity labels, establishing user label authorizations, and protecting individual tables or schemes.

Data sensitivity labels provide a powerful and flexible method of restricting access to data. For example, data belonging to different organizations or companies can be separated using data sensitivity labels and selectively shared between companies by changing the data sensitivity label.

Depending on the complexity of the security policy, Oracle Virtual Private Database may be the preferred method for implementing your security policy. Oracle Label Security is best suited for situations where access control decisions need to be based on the sensitivity of the information.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.5 Can I Combine Oracle Virtual Private Database and Oracle Label Security?

Yes. You can use a `WHERE` clause or a VPD policy.

- A `WHERE` clause can be appended to an OLS policy, which provides one more level of granularity. An example would be that users, regardless of their label authorizations, are only allowed to connect from a specific IP address or subnet, and during business hours only.

- A VPD policy, whether column sensitive or not, can evaluate user labels and determine access to columns and rows without the need to apply data labels.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.6 Can I Use Oracle Label Security with Oracle E-Business Suite?

Oracle Applications use Oracle Virtual Private Database (VPD) to provide new functionality and security protections.

In addition, you can use other Oracle security products with Oracle E-Business Suite, such as Oracle Database Vault. Contact Oracle Support for more information.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.7 Can I Use Oracle Label Security with Oracle Database Vault?

Oracle Database Vault and Oracle Label Security can be used together within the same database.

An Oracle Database Vault realm can protect a table that is also protected by an Oracle Label Security policy. The realm can protect the entire table and the Oracle Label Security can provide row level security for users that need to access the table data.

In addition, Oracle Label Security can be used together with Database Vault features. You can assign Oracle Label Security labels to Database Vault Factors. These labels are then merged with the user clearance labels, following the algorithms documented in [Merging Labels with the MERGE_LABEL Function](working-with-labeled-data.md), before access control decisions are being made by comparing the merged user labels with the row labels.

The following example on the Oracle Technology Network Web site discusses using Oracle Label security along with Oracle Database Vault features:

[`http://www.oracle.com/technetwork/database/security/label-security-factors-093209.html`](http://www.oracle.com/technetwork/database/security/label-security-factors-093209.html)

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.8 Does Oracle Label Security Provide Column-Level Access Control?

No, Oracle Label Security is not column aware.

This behavior is available with Virtual Private Database (VPD). A VPD policy can be written so that it only becomes active when a certain column is part of a SQL statement against a protected table. If the column sensitivity switch is on, then VPD either returns only those rows for which the sensitive column values are accessible to the user, or it returns all rows with all cells in the sensitive column being empty, except those values that the user is allowed to see.

The following link on the Oracle Technology Network Web site contains an example:

[`http://www.oracle.com/technetwork/database/security/index-088277.html`](http://www.oracle.com/technetwork/database/security/index-088277.html)

A column-sensitive VPD policy can determine access to a specific column by evaluating OLS user labels, which this example demonstrates:

[`http://www.oracle.com/technetwork/database/security/ols-cs1-099558.html`](http://www.oracle.com/technetwork/database/security/ols-cs1-099558.html)

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.9 Can I Base Secure Application Roles on Oracle Label Security?

Yes, you can base secure application roles on Oracle Label Security.

The procedure that determines if the `SET ROLE` command is executed can evaluate OLS user labels. In this case, the OLS policy does not need to be applied to a table, since row labels are not part of this solution.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.10 What Are Trusted Stored Program Units?

Trusted stored program units are stored procedures, functions, and packages that execute with the system and object privileges (DAC) of the definer.

If the invoker is a user with Oracle Label Security user clearances (labels), the procedure executes with a combination of the definer's DAC privileges and the invoker's security clearances.

Trusted stored procedures are procedures that are either granted the Oracle Label Security privilege `FULL` or `READ`. When a trusted stored program unit is run, the policy privileges in force are a combination of the invoking user's privileges and the program unit's privileges.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.11 Does VPD or OLS Add an Additional Column to the Protected Table?

When you apply an Oracle Label Security (OLS) policy to a table, the policy adds an additional column to the table.

The name of this column needs to be specified when the policy is initially created.

An existing column can be used to store the OLS row labels. This column must have the `NUMBER(10)` data type.

Oracle Virtual Private Database (VPD) does not add an additional column to the protected table.

**Parent topic:** Frequently Asked Questions about Oracle Label Security

### H.12 Why Should the Additional OLS Row Label Column Be Hidden?

Most applications are designed with access control mechanisms in mind, so Oracle Label Security must do this transparently.

When an application queries a table with a `SELECT FROM` `tablename` statement, it returns all columns, including the unhidden label column. Existing applications may not be designed to display an additional column, and malfunction. However, if the label column is hidden, then it is displayed only when its name is included in the SQL statement. A `SELECT FROM` `tablename` would return all columns as expected by the application, excluding the hidden OLS column.

**Parent topic:** Frequently Asked Questions about Oracle Label Security
