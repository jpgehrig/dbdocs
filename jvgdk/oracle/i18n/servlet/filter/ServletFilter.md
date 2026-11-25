Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev Class
- [Next Class](ServletRequestWrapper.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.i18n.servlet.filter

## Class ServletFilter

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.filter.ServletFilter

<!-- -->

- All Implemented Interfaces:
  [Filter](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true)

  ------------------------------------------------------------------------



      public class ServletFilter
      extends Object
      implements Filter

  The `ServletFilter` class instantiates the wrappers of HTTP request and response objects for the GDK, and passes them to the application.
  The application requires registering this class in `web.xml` to incorporate the GDK framework as follows:

       ...
       <filter>
         <filter-name>gdkfilter</filter-name>
         <filter-class>oracle.i18n.servlet.filter.ServletFilter</filter-class>
       </filter>
       ...
       <filter-mapping>
         <filter-name>gdkfilter</filter-name>
         <url-pattern>*.jsp</url-pattern>
       </filter-mapping>
       ...


  Also, the [`ContextListener`](../listener/ContextListener.md) class needs to be registered in `web.xml` to complete the GDK installation.

  Basically, user applications do not need to explicitly call any method in this class.

  Since:
  10.1.0.2

  See Also:
  [`ContextListener`](../listener/ContextListener.md)

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

    <!-- -->

    - ### Methods inherited from interface javax.servlet.[Filter](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true)

      [`destroy`](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true#destroy--)`, `[`doFilter`](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true#doFilter-javax.servlet.ServletRequest-javax.servlet.ServletResponse-javax.servlet.FilterChain-)`, `[`init`](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true#init-javax.servlet.FilterConfig-)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev Class
- [Next Class](ServletRequestWrapper.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
