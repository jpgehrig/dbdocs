The `OracleCacheDependency` object enables ASP.NET applications to invalidate cached items based on changes made in an Oracle database.

### Class Inheritance

`System.Object`

`  System.Web.Caching.CacheDependency`

`    Oracle.Web.Caching.OracleCacheDependency`

### Declaration

    // C#
    public sealed class OracleCacheDependency : CacheDependency

### Thread Safety

All public static methods are thread-safe, although instance members are not guaranteed to be thread-safe.

### Remarks

This class invalidates data that is cached by ASP.NET applications, based on changes in the Oracle database.

This feature uses the Oracle Database Change Notification feature.

The user must have the `CHANGE` `NOTIFICATION` privilege, which can be granted with the following SQL statement:

    GRANT change notification TO username;

### Requirements

Namespace: `Oracle.Web.Caching`

Assembly: `Oracle.Web.dll`

Oracle Providers for ASP.NET Version: Oracle Providers for ASP.NET 2.0 and Oracle Providers for ASP.NET 4

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleCacheDependency Members](OracleCacheDependencyMembers.md)

- [OracleCacheDependency Constructors](CacheDependencyConstructors.md)

- [OracleCacheDependency Properties](CacheDependencyProperties.md)

- [OracleCacheDependency Methods](CacheDependencyMethods.md)
