Specifies supported language, territory, and character set.

This parameter specifies the language in which messages appear, the territory and its conventions for calculating week and day numbers, and the character set displayed. Oracle Universal Installer sets this value during installation based on the language setting of the operating system.

The default value for `NLS_LANG,` if not set, is `AMERICAN_AMERICA.US7ASCII.`

There are other globalization parameters that can be set along `NLS_LANG` to override some values implicitly determined by `NLS_LANG.` These parameters are:

    NLS_DATE_FORMAT
    NLS_TIMESTAMP_FORMAT
    NLS_TIMESTAMP_TZ_FORMAT
    NLS_DATE_LANGUAGE
    NLS_NUMERIC_CHARACTERS
    NLS_CURRENCY
    NLS_ISO_CURRENCY
    NLS_DUAL_CURRENCY
    NLS_SORT

The following parameters can also be set along `NLS_LANG` to determine globalization behavior that is independent from the value of `NLS_LANG:`

    NLS_CALENDAR
    NLS_COMP
    NLS_NCHAR_CONV_EXCP
    NLS_LENGTH_SEMANTICS

**Note:**

All globalization parameters set in the environment and Registry for a database client are ignored if `NLS_LANG` is not set.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about `NLS_LANG` and other globalization parameters

**Parent topic:** [About HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME](about-hkey-local-machine.md)
