## Installing Translation Resources

Learn how to install the appropriate language translation resources.

To view the user interface of Oracle components in different languages, you must install the appropriate language translations along with the component.

**Note:**

Part of Oracle Database Vault user interface text is stored in database tables in the DVSYS schema. By default, only the English language is loaded into these tables. You can use Oracle Database Vault Configuration Assistant to add more languages to Oracle Database Vault.

To install translation resources:

1.  Start Oracle Universal Installer.

2.  In the Configure Security Updates screen enter the relevant information and click Next.

3.  In the Select Installation Option screen, select the installation option and click Next.

4.  In the System Class screen, select the type of system class for installing the database, and click Next.

5.  In the Grid Installation Options screen, select the type of database installation you want to perform, and click Next.

6.  In the Select Product Languages screen, select the language in which you want to run the product from the Available Languages field.

    **Note:**

    The Available Languages field lists all languages supported by Oracle globalization libraries. The set of languages for which a translation is actually available is usually smaller and depends on a particular component. The scope of translation for a given component may differ between languages. For example, some translations may include all user interface text, while others may include only error messages and no help files.

7.  Use the \> arrow to move the selected language to the Selected Languages field, and then click Next.

    **Note:**

    Oracle Universal Installer ignores languages in the Selected Languages field for which no translation is available.

**Parent topic:** [Installing and Using Oracle Components in Different Languages](installing-and-using-oracle-components-in-different-languages.md)
