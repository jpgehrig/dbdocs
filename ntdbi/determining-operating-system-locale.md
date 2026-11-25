## Determining the Operating System Locale

The locale setting of your operating system session determines the language of the user interface and the globalization behavior for components such as Oracle Universal Installer, Oracle Net Configuration Assistant, and Oracle Database Configuration Assistant.

It also determines the globalization behavior of Oracle Database sessions created by a user application through Oracle JDBC driver, unless overridden by the application.

Open the Control Panel from the Start menu to modify the operating system locale settings. In the classic view of the Control Panel on Windows, click Regional and Language Options. In the default view of the Control Panel on Windows, click Change keyboards or other input methods.

To set locale for the current operating system user on Windows, select the desired locale from the Current format pop-up list on the Formats tab.

Some of the locales may be unavailable until you install required operating system support files.

Some Oracle components, such as SQL\*Plus, require that the Windows System Locale is also set to the language in which the components are to be run. System Locale is called Language for non-Unicode programs on Windows. On Windows, click the Change system locale button on the Administrative tab, accept the use of administrative privileges, if User Account Control is active, and select the locale from the pop-up list in the opened dialog box.

**Note:**

The operating system must be restarted after the System Locale is changed. See the operating system documentation for further information about Windows locale settings.

**Parent topic:** [Installing and Using Oracle Components in Different Languages](installing-and-using-oracle-components-in-different-languages.md)
