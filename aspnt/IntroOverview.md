Oracle Providers for ASP.NET is a collection of ASP.NET providers that follow the ASP.NET provider model and uses Oracle Database as the data source.

Microsoft ASP.NET includes a number of services and providers that store application state in databases and other storage media. Developers can store application state, such as shopping cart or user information, in a persistent data source. By storing the application state in a database, applications ensure high availability and reliable access to the data from any Web server in the server farm. Users can retrieve their ASP.NET state data no matter which Web farm computer they access because it is located centrally on the database. If the particular Web farm computer a user is accessing fails, the information is not lost because the ASP.NET data is persisted in the database. ASP.NET developers can now be more productive as they build their Web applications through these ASP.NET services, which are classes that are part of the .NET Framework.

These ASP.NET services are data-source independent, but they can be configured to use a particular ASP.NET provider, which is implemented specifically to store and retrieve data from a specific data source. Oracle Providers for ASP.NET, like all ASP.NET providers, follow the ASP.NET provider model to provide all the functionality that the ASP.NET services need. By simply configuring the Oracle Providers for ASP.NET as default providers in a configuration file, ASP.NET applications can store various types of application states in an Oracle database. The application states that can be stored are commonly used among Web applications. ASP.NET developers can use these providers, as opposed to creating their own from scratch.

Oracle Providers for ASP.NET are available for both 32-bit and 64-bit (x64) platforms.

**See Also:**

[System Requirements](IntroSystemRequirements.md) for more details.

Oracle offers the following providers:

- Membership Provider

- Role Provider

- Site Map Provider

- Session State Provider

- Profile Provider

- Web Event Provider

- Web Parts Personalization Provider

- Cache Dependency Provider

Descriptions of each provider that Oracle offers are as follows:

- Oracle Membership Provider for ASP.NET

  The Oracle membership provider enables ASP.NET applications to store the registered user information of a Web site in an Oracle database through the ASP.NET membership service. It provides methods for creating users, deleting users, verifying login credentials, changing passwords, and other tasks associated with managing application users.

- Oracle Role Provider for ASP.NET

  The Oracle role provider enables ASP.NET applications to store and manage Web site-specific role information in an Oracle database through the ASP.NET role service. The Oracle role provider exposes methods for creating roles, deleting roles, adding users to roles, and other tasks associated with managing roles defined in an ASP.NET application.

- Oracle Site Map Provider for ASP.NET

  The Oracle site map provider enables ASP.NET applications to store site map information in an Oracle database. The Oracle site map provider reads site map data from the Oracle database to build an upside-down tree of `SiteMapNode` objects, as well as to supply methods for retrieving nodes from the site map.

- Oracle Session State Provider for ASP.NET

  The Oracle session state provider enables ASP.NET applications to store ASP.NET session information in an Oracle database through the ASP.NET session state service. This provider manages per-user session state, such as a shopping cart for an e-commerce application.

- Oracle Profile Provider for ASP.NET

  The Oracle profile provider enables ASP.NET applications to store an individual Web site user's profile information in the Oracle database. The profile provider can write and read Web site user profile properties that are persisted in the database.

- Oracle Web Event Provider for ASP.NET

  The Oracle Web event provider enables ASP.NET applications to store events raised by the ASP.NET health monitoring system in the Oracle database. The provider provides buffering and flushing capabilities to minimize database round-trips.

- Oracle Web Parts Personalization Provider for ASP.NET

  The Oracle Web parts personalization provider enables ASP.NET applications to store personalization data in an Oracle database through the ASP.NET Web parts personalization service.

  It connects to an integrated set of controls for creating Web sites that enable end users to modify the content, appearance, and behavior of Web pages directly from a browser.

- Oracle Cache Dependency Provider for ASP.NET

  Oracle cache dependency provider provides automatic invalidation of data that is cached by ASP.NET applications in the `System.Web.Caching.Cache` object, based on changes made in the Oracle database. This provider can provide performance improvements to ASP.NET applications because ASP.NET applications can use the cached database data and fetch data from the database only when it is needed.

**See Also:**

[Oracle Data Provider for .NET Developer's Guide](../odpnt/featChange.md) for more information on database change notification

The Microsoft Developer Network for more information about:

- ASP.NET membership and membership providers [`http://msdn.microsoft.com/en-us/library/tw292whz.aspx`](http://msdn.microsoft.com/en-us/library/tw292whz.aspx)

- ASP.NET role management and role providers [`http://msdn.microsoft.com/en-us/library/9ab2fxh0.aspx`](http://msdn.microsoft.com/en-us/library/9ab2fxh0.aspx)

- ASP.NET site navigation and site map provider [`http://msdn.microsoft.com/en-us/library/ms227558.aspx`](http://msdn.microsoft.com/en-us/library/ms227558.aspx)

- ASP.NET session state and session state providers [`http://msdn.microsoft.com/en-us/library/ms178581.aspx`](http://msdn.microsoft.com/en-us/library/ms178581.aspx)

-  ASP.NET profile properties and profile providers [`http://msdn.microsoft.com/en-us/library/2y3fs9xs.aspx`](http://msdn.microsoft.com/en-us/library/2y3fs9xs.aspx)

- ASP.NET health monitoring and web event provider [`http://msdn.microsoft.com/en-us/library/ms178701%28VS.80%29.aspx`](http://msdn.microsoft.com/en-us/library/ms178701%28VS.80%29.aspx)

- ASP.NET Web Parts [`http://msdn.microsoft.com/en-us/library/e0s9t4ck.aspx`](http://msdn.microsoft.com/en-us/library/e0s9t4ck.aspx)

- ASP.NET Web Parts Personalization [`http://msdn.microsoft.com/en-us/library/ms178182.aspx`](http://msdn.microsoft.com/en-us/library/ms178182.aspx)

- ASP.NET `CacheDependency` class [`http://msdn.microsoft.com/en-us/library/system.web.caching.cachedependency.aspx`](http://msdn.microsoft.com/en-us/library/system.web.caching.cachedependency.aspx)

-
