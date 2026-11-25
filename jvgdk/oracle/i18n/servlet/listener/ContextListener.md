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
- Next Class

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

oracle.i18n.servlet.listener

## Class ContextListener

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.listener.ContextListener

<!-- -->

- All Implemented Interfaces:
  [EventListener](http://docs.oracle.com/javase/8/docs/api/java/util/EventListener.html?is-external=true), [ServletContextListener](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContextListener.html?is-external=true)

  ------------------------------------------------------------------------



      public class ContextListener
      extends Object
      implements ServletContextListener

  The `ContextListener` class is the default context listener class that instantiates an [`ApplicationContext`](../ApplicationContext.md) object.
  Register this class in `web.xml` so that it is called at startup of JSP/Java Servlet applications. For example:

       <listener>
         <listener-class>oracle.i18n.servlet.listener.ContextListener</listener-class>
       </listener>


  If the application incorporates a database user schema containing a locale preference, a custom `ContextListener` class may need to be used.

  The following example shows how to use the `contextInitialized` and `contextDestroyed` methods in the context listener. Note that the constructor throws exceptions. For example:

        public void contextInitialized(ServletContextEvent event)
        {
          ...
          try
          {
            ServletContext context = event.getServletContext();
            context.setAttribute(
              ApplicationContext.OBJECT_KEY,
              new ApplicationContext(
                context.getResourceAsStream(ApplicationContext.DEFAULT_GDKAPP),
                getClass().getClassLoader()));
          }
          catch (Exception e)
          {
            // handle exception
            ...
          }
          ...
        }
        ...
        public void contextDestroyed(ServletContextEvent event)
        {
          event.getServletContext().removeAttribute(ApplicationContext.OBJECT_KEY);
        }


  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

    <!-- -->

    - ### Methods inherited from interface javax.servlet.[ServletContextListener](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContextListener.html?is-external=true)

      [`contextDestroyed`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContextListener.html?is-external=true#contextDestroyed-javax.servlet.ServletContextEvent-)`, `[`contextInitialized`](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContextListener.html?is-external=true#contextInitialized-javax.servlet.ServletContextEvent-)

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
- Next Class

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
