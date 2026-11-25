Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](Localizer.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.i18n.servlet

## Class ServletHelper

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.ServletHelper

<!-- -->

-

  ------------------------------------------------------------------------



      public class ServletHelper
      extends Object

  The `ServletHelper` class is a delegate class that provides a bridge between Java servlets and globalization objects. All operations that involve Java servlets are performed using this class.
  In order to enable a J2EE based Web application to use the GDK framework, it is necessary to configure a GDK filter and a listener in the application deployment descriptor file *web.xml*. This allows the GDK framework to be hooked into the Web application. See the sample *web.xml* descriptor file below.

  First the GDK filter is configured in the deployment descriptor file, whose purpose is to instantiate the GDK wrappers for HTTP requests and responses. The *GDKFilter* filter specifies the *oracle.i18n.servlet.filter.ServletFilter* Javaclass for use as the GDK filter. Additionally, the GDK default listener is configured that instantiates the GDK `ApplicationContext` object, that controls application scope operations for the framework. In this case the Java class *oracle.i18n.servlet.listener.ContextListener* is configured as the listener.

  **web.xml that enables the GDK framework**
  ` `

       <?xml version = '1.0' encoding = 'windows-1252'?>
       <!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
                    "http://java.sun.com/dtd/web-app_2_3.dtd">
       <web-app>
         <description>web.xml file for enabling GDK in the application</description>

         <!-- Enable the application to use the GDK Application Framework.-->
         <filter>
           <filter-name>GDKFilter</filter-name>
           <filter-class>oracle.i18n.servlet.filter.ServletFilter</filter-class>
         </filter>
         <filter-mapping>
           <filter-name>GDKFilter</filter-name>
           <url-pattern>*.jsp</url-pattern>
         </filter-mapping>

         <listener>
           <listener-class>oracle.i18n.servlet.listener.ContextListener</listener-class>
         </listener>

       ....

         <session-config>
           <session-timeout>35</session-timeout>
         </session-config>

       ....

       </web-app>


  Once the GDK framework has been enabled for your application, you need to configure its behavior via the use of the *gdkapp.xml* framework configuration file. The complete steps on how to enable the GDK framework within your application and its configuration is documented in the *Oracle Database Globalization Support Guide*.

  The GDK application framework is driven by the application configuration file, which by default is *gdkapp.xml* and resides in the same directory as the *web.xml* file. See below for a sample listing of the *gdkapp.xml* file, which shows configuration of the most applicable elements for J2EE applications. The ` <application-locales>` section is used to declare all the locales that the application supports, so they don't have to be hard coded somewhere, plus can be accessed from the application in a generic manner via the GDK API. The `<locale-determine-rule>` section is used to define locale sources in priority order, as to the sources that supply locale preferences. See the [`LocaleSource`](localesource/LocaleSource.md) class for more information. Finally, the message resource bundles allow a GDK application access to localized static content that may be displayed in a web page. They are declared using the `<message-bundles>` section. In this case the message bundle named *Messages*, is declared as the default application resource bundle. The [`Localizer`](Localizer.md) class exposes methods to retrieve localized messages from the declared resource bundles.

  **The GDK configuration file – gdkapp.xml**

       <?xml version="1.0" encoding="UTF-8"?>
       <gdkapp xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                         xsi:noNamespaceSchemaLocation="gdkapp.xsd">

         <!-- All pages are generated using the UTF-8 encoding          -->
         <page-charset default="yes">UTF-8</page-charset>

         <!-- The application locale list for the Web application, i.e. -->
         <!-- all the locales that are supported by the application.    -->
         <application-locales>
           <locale>de-CH</locale>
           <locale default="yes">en-US</locale>
           <locale>zh-CN</locale>
         </application-locales>

         <locale-determine-rule>
           <locale-source>
             oracle.i18n.servlet.localesource.UserInput
           </locale-source>
           <locale-source>
             oracle.i18n.servlet.localesource.HttpAcceptLanguage
           </locale-source>
         </locale-determine-rule>

         <!-- Declare a default application resource bundle that        -->
         <!-- supplies all the messages to the application.             -->
         <message-bundles>
           <resource-bundle name="default">
             com.oracle.demo.Messages
           </resource-bundle>
         </message-bundles>
       </gdkapp>


  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    |------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`ApplicationContext`](ApplicationContext.md)                                               | `getApplicationContextInstance``(`[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Returns an `ApplicationContext` object associated with the Web application.                                                                                                                                                                                                    |
    | `static `[`LocaleSource`](localesource/LocaleSource.md)                                              | `getLocaleSourceInstance``(`[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Returns a `LocaleSource` object associated with the HTTP request object.                                                                                                                                                                                                             |
    | `static `[`Localizer`](Localizer.md)                                                                 | `getLocalizerInstance``(`[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Returns a `Localizer` object derived from the HTTP request object.                                                                                                                                                                                                                      |
    | `static void`                                                                                        | `refreshLocales``(`[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Refreshes the locale objects associated with the request.                                                                                                                                                                                                                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `rewriteURL``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseURL, `[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Rewrites a URL based on the rules specified in the GDK application configuration file.                                                                                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `rewriteURL``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseURL, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`HttpServletRequest`](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true)` request)`<br>Rewrites a URL based on the rules specified in the GDK application configuration file. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### getApplicationContextInstance

          public static ApplicationContext getApplicationContextInstance(HttpServletRequest request)

      Returns an `ApplicationContext` object associated with the Web application.
      Parameters:
      `request` - an HTTP request object

      Returns:
      an `ApplicationContext` object

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if `ApplicationContext` cannot be instantiated

    <!-- -->

    - #### getLocaleSourceInstance

          public static LocaleSource getLocaleSourceInstance(HttpServletRequest request)

      Returns a `LocaleSource` object associated with the HTTP request object. This associated locale source is determined by the ServletRequestWrapper as part of the GDK framework functionality.
      Parameters:
      `request` - an HTTP request object

      Returns:
      a `LocaleSource` object

    <!-- -->

    - #### getLocalizerInstance

          public static Localizer getLocalizerInstance(HttpServletRequest request)

      Returns a `Localizer` object derived from the HTTP request object. The Localizer's properties are based on the locale source object associated with the request.
      Parameters:
      `request` - an HTTP request object

      Returns:
      `Localizer` object

    <!-- -->

    - #### rewriteURL

          public static String rewriteURL(String baseURL,
                                          HttpServletRequest request)

      Rewrites a URL based on the rules specified in the GDK application configuration file. This method is used to determine the URL where a localized static content resource exists.
      Parameters:
      `baseURL` - a URL string

      `request` - an HTTP request object

      Returns:
      a URL referencing the localized content

      See Also:
      `ServletHelper.rewriteURL(String, String, HttpServletRequest)`

    <!-- -->

    - #### rewriteURL

          public static String rewriteURL(String baseURL,
                                          String name,
                                          HttpServletRequest request)

      Rewrites a URL based on the rules specified in the GDK application configuration file. This method is used to determine the URL where a localized static content resource exists. The name of the rewrite URL rule can be specified when you use nondefault, multiple rules.
      For example, if localized contents are supplied in `/images/es/welcome.jpg` for Spanish and `/images/ja/welcome.jpg` for Japanese locales, the `baseURL` would be `/images/welcome.jpg`, and the rule defined in the regular expression should be `"(.)/([^\/]+)$"` in order that the URL be replaced with the string `"$1/$A/$2"`.

      Parameters:
      `baseURL` - a URL string

      `name` - the name of the rewrite URL rule

      `request` - an HTTP request object

      Returns:
      a URL referencing the localized content

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if invalid regular expression is specified

    <!-- -->

    - #### refreshLocales

          public static void refreshLocales(HttpServletRequest request)

      Refreshes the locale objects associated with the request.
      By calling this method, you can explicitly refresh the locale objects associated with the request. With the servlet authentication, usually it performs the `FORWARD` operation to jump to the success page or the failure page based on the results of authentication. However, because the `FORWARD` operation does not involve the servlet filter, GDK cannot refresh the locale information after the authentication. Instead, the page after the success page will take the effect. This method resolves this issue and provides the flexibility of taking advantage of GDK locale determination feature.

      For struts framework, the session attribute `Action.LOCALE_KEY` is updated.

      Parameters:
      `request` - an HTTP request object

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](Localizer.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
