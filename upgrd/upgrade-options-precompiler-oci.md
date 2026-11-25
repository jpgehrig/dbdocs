## About Upgrading Options for Oracle Precompiler and OCI Applications

Oracle provides several options for upgrading your precompiler and Oracle Call Interface (OCI) applications running on a new release of Oracle Database.

The upgrade options are listed in order of increasing difficulty and increasing potential benefits. That is, Option 1 is the least difficult option, but it offers the least potential benefits, while Option 3 is the most difficult option, but it offers the most potential benefits.

- Option 1: Leave the Application Unchanged
  Leave the application and its environment unchanged.
- Option 2: Precompile or Compile the Application Using the New Software
  Application code must be changed if any APIs are deprecated or changed.
- Option 3: Change the Application Code to Use New Oracle Database Features
  Make code changes to your applications to take advantage of new Oracle Database features.
- Changing Oracle Precompiler and OCI Application Development Environments
  When you have decided on the new features to use, change the code of your application to use these features.

**Parent topic:** [Upgrading Applications After Upgrading Oracle Database](upgrading-apps-after-oracle-db-upgrade.md)

### Option 1: Leave the Application Unchanged

Leave the application and its environment unchanged.

Do not relink, precompile, or compile the application, and do not change the application code. The application continues to work against the new Oracle Database release. This option requires that the Oracle home environment of the application is not upgraded. You can leave the application unchanged, and it continues to work with the new release Oracle Database server. The major advantage to this option is that it is simple and easy. In addition, this option requires the least amount of administration, because you are not required to upgrade any of your client computers. If you have a large number of client computers, then avoiding the administrative costs of upgrading all of them can become very important.

The major disadvantage to this option is that your application cannot use the features that are available in the new release of Oracle Database. In addition, your application cannot leverage all the possible performance benefits of the new Oracle Database release.

**Parent topic:** About Upgrading Options for Oracle Precompiler and OCI Applications

### Option 2: Precompile or Compile the Application Using the New Software

Application code must be changed if any APIs are deprecated or changed.

Precompile or compile, and then relink the application using the new release of Oracle Database. When upgrading to the new release of Oracle Database software, you must precompile or compile the application with the new software after making necessary code changes to account for APIs that are deprecated or changed.

This option requires that you install the new Oracle Database client software on each client computer. You are required to precompile or compile, and relink your application only one time, regardless of the number of clients you have.

By recompiling, you perform a syntax check of your application code. Some problems in the application code that were not detected by previous releases of the Oracle software can emerge when you precompile or compile with the new Oracle Database software. Precompiling and compiling with the new software helps you detect and correct problems in the application code that previously were unnoticed.

Also, recompiling affords maximum stability for your application, because you are sure that it works with the new Oracle Database release. Further, your environment is ready for new development using the latest tools and features available. In addition, you might benefit from performance improvements that are available with the new Oracle software only after you recompile and relink.

**Parent topic:** About Upgrading Options for Oracle Precompiler and OCI Applications

### Option 3: Change the Application Code to Use New Oracle Database Features

Make code changes to your applications to take advantage of new Oracle Database features.

Change the application code to use new features in the new Oracle Database release. Then, precompile or compile and then relink the code. This option is the most difficult, but it can provide the most potential benefits. You gain all of the advantages described in Option 2: Precompile or Compile the Application Using the New Software. In addition, you also benefit from changes to your application that can leverage performance and scalability benefits available with the new release of Oracle Database. You can also add new features to your application that are available only with the new release. Consult the Oracle documentation for your development environment so that you understand how to implement the features thaqt you want to use.

**See Also:**

[Oracle Database New Features](../newft/index.md) to become familiar with the features in this new Oracle Database release

**Parent topic:** About Upgrading Options for Oracle Precompiler and OCI Applications

### Changing Oracle Precompiler and OCI Application Development Environments

When you have decided on the new features to use, change the code of your application to use these features.

Follow the appropriate instructions in the following sections based on your development environment.

- Changing Precompiler Applications
  Complete these steps to change precompiler applications to use new Oracle Database release features.
- Changing OCI Applications
  To use new features in your new Oracle Database release, you must recompile your applications with the OCI calls for the new Oracle Database release.

**Parent topic:** About Upgrading Options for Oracle Precompiler and OCI Applications

#### Changing Precompiler Applications

Complete these steps to change precompiler applications to use new Oracle Database release features.

To use new features in a new Oracle Database release, you must add new code into your existing applications, and recompile the applications.

1.  Incorporate the code for new features into your existing applications.
2.  Precompile each application using the Oracle precompiler.
3.  Compile each application.
4.  Relink each application with the runtime library of the new Oracle Database release, `SQLLIB`, which is included with the precompiler.

**Parent topic:** Changing Oracle Precompiler and OCI Application Development Environments

#### Changing OCI Applications

To use new features in your new Oracle Database release, you must recompile your applications with the OCI calls for the new Oracle Database release.

1.  Incorporate OCI calls of the new Oracle Database release into the existing application
2.  Compile the application.
3.  Relink the application with the new Oracle Database release runtime library.

**Parent topic:** Changing Oracle Precompiler and OCI Application Development Environments
