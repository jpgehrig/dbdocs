## Configuring Oracle Components to Run in Different Languages

You can specify the language and the territory, or locale, in which you want to use the Oracle components.

The locale setting of a component determines the language of the user interface of the component and the globalization behavior, such as date and number formatting. Depending on the Oracle component, the locale of the component is either inherited from the operating system session that started the component, or is defined by the `NLS_LANG `environment variable.

The operating system locale usually influences Oracle components that are based on Java technology. The `NLS_LANG` environment variable usually influences Oracle components that use Oracle Client libraries such as OCI.

**Note:**

The user interface of an Oracle component is displayed in a selected language only if the appropriate translation is available and has been installed. Otherwise, the user interface is displayed in English.

**Parent topic:** [Installing and Using Oracle Components in Different Languages](installing-and-using-oracle-components-in-different-languages.md)
