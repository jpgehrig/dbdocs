## Configuring Oracle Components to Run in Different Languages

You can specify the language and the territory, or locale, in which you want to use Oracle components.

The locale setting of a component determines the language of the user interface of the component and the globalization behavior, such as date and number formatting. Depending on the Oracle component, the locale of the component is either inherited from the operating system session that started the component, or is defined by the `NLS_LANG `environment variable.

The operating system locale usually influences Oracle components that are based on Java technology. The `NLS_LANG` environment variable usually influences Oracle components that use Oracle Client libraries such as OCI.

**Note:**

The user interface of an Oracle component is displayed in a selected language only if the appropriate translation is available and has been installed. Otherwise, the user interface is displayed in English.

- [Determining the Operating System Locale](determining-the-operating-system-locale.md)
  The locale setting of your operating system session determines the language of the user interface and the globalization behavior for components such as Oracle Universal Installer, Oracle Net Configuration Assistant, and Oracle Database Configuration Assistant.
- [Configuring Locale and Character Sets Using the NLS_LANG Environment Variable](configuring-locale-and-character-sets-using-nls-lang-environment-variable.md)
  The `NLS_LANG` environment variable determines the language of the user interface and the globalization behavior for components such as SQL\*Plus, exp, and imp.
- [NLS_LANG Settings in Console Mode and Batch Mode](nls-lang-settings-in-console-mode-and-batch-mode.md)
  Before you can use Oracle utilities such as SQL\*Plus, SQL Loader, Import, and Export from the Command Prompt window, set the character set field of the `NLS_LANG` parameter to a value different than the one set in Registry.

**Parent topic:** [Installing and Using Oracle Components in Different Languages](installing-and-using-oracle-components-in-different-languages.md)
