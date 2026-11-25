Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Package](../text/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.i18n.util

Provides general utilities for globalization support.

See: Description

- **Class Summary**

  | Class                                               | Description                                                                                                                                                                      |
  |-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [DualInputStreamBuilder](DualInputStreamBuilder.md) | The `DualInputStreamBuilder` class generates two `InputStream` wrapper objects for one `InputStream` source.                                                                     |
  | [LocaleMapper](LocaleMapper.md)                     | The `LocaleMapper` class maps between Oracle locale elements and equivalent locale elements in other vendors and standards.                                                      |
  | [OraDisplayLocaleInfo](OraDisplayLocaleInfo.md)     | The `OraDisplayLocaleInfo` class is a utility class that provides predefined translations for locale related attributes.                                                         |
  | [OraLocaleInfo](OraLocaleInfo.md)                   | The `OraLocaleInfo` is a utility class that provides locale related information regarding locale attributes like language, territory, character set, timezone, collators, etc... |
  | [OraResourceBundle](OraResourceBundle.md)           | The `OraResourceBundle` class is the factory class that constructs a `java.util.ResourceBundle` instance.                                                                        |
  | [OraSQLUtil](OraSQLUtil.md)                         | The `OraSQLUtil` class is an Oracle SQL utility class.                                                                                                                           |

## Package oracle.i18n.util Description

Provides general utilities for globalization support.

The following is a list of terminology that defines special meanings used in this package:

- `getAvailableXXX` - the methods that return all elements available in the GDK. For example, available Oracle languages and available linguistic sorting orders.
- `getCommonXXX` - the methods that return common elements independent of locale. For example, common locales and common time zones.
- `getLocalXXX` - the methods that return common elements for the specified locale. For example, local languages for the specified territory and local time zones for the specified territory.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Package](../text/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
