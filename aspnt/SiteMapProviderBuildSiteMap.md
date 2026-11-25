This method builds a `SiteMap` tree of the `SiteMapNode` objects by loading site map data from the Oracle database.

### Declaration

    // C#
    Public override SiteMapNode BuildSiteMap();

### Return Value

The root `SiteMapNode` of the site map navigation structure.

### Exceptions

`InvalidOperationException` - The `OracleSiteMapProvider` instance is not initialized.

`ProviderException` - One of the following conditions exists:

- Root node is not found.

- Multiple root nodes are found.

- Parent node is not found for any node.

`ConfigurationErrorsException` - One of the following conditions exists:

- The roles of the `SiteMapNode` contain characters that are not valid.

- A URL is parsed for a `SiteMapNode` that is not unique.

- A `SiteMapNode` object was encountered with a duplicate value for `Key`.

- An error occurred while parsing the URL of a `SiteMapNode`.

### Remarks

This method fetches site map data from the database and builds a tree of site map nodes in memory. The `OracleSiteMapProvider` object could choose to subscribe to database change notifications to get notified about the changes in the site map data in the database. This method is thread-safe.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSiteMapProvider Class](OracleSiteMapProviderClass.md)

- [OracleSiteMapProvider Members](OracleSiteMapProviderMembers.md)

- [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featChange.md) for more information about continuous query notification support
