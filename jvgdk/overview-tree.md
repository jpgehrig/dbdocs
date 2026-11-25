Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Hierarchy For All Packages

Package Hierarchies:

- [oracle.i18n.lcsd](oracle/i18n/lcsd/package-tree.md),
- [oracle.i18n.net](oracle/i18n/net/package-tree.md),
- [oracle.i18n.servlet](oracle/i18n/servlet/package-tree.md),
- [oracle.i18n.servlet.filter](oracle/i18n/servlet/filter/package-tree.md),
- [oracle.i18n.servlet.listener](oracle/i18n/servlet/listener/package-tree.md),
- [oracle.i18n.servlet.localesource](oracle/i18n/servlet/localesource/package-tree.md),
- [oracle.i18n.text](oracle/i18n/text/package-tree.md),
- [oracle.i18n.util](oracle/i18n/util/package-tree.md)

## Class Hierarchy

- java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - oracle.i18n.servlet.[ApplicationContext](oracle/i18n/servlet/ApplicationContext.md)
  - oracle.i18n.net.[CharEntityReference](oracle/i18n/net/CharEntityReference.md)
  - oracle.i18n.net.[CharEntityReference.Form](oracle/i18n/net/CharEntityReference.Form.md)
  - oracle.i18n.servlet.listener.[ContextListener](oracle/i18n/servlet/listener/ContextListener.md) (implements javax.servlet.[ServletContextListener](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletContextListener.html?is-external=true))
  - oracle.i18n.util.[DualInputStreamBuilder](oracle/i18n/util/DualInputStreamBuilder.md)
  - java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true) (implements java.lang.[Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.i18n.text.[OraDateFormat](oracle/i18n/text/OraDateFormat.md)
      - oracle.i18n.text.[OraSimpleDateFormat](oracle/i18n/text/OraSimpleDateFormat.md)
    - oracle.i18n.text.[OraNumberFormat](oracle/i18n/text/OraNumberFormat.md)
      - oracle.i18n.text.[OraDecimalFormat](oracle/i18n/text/OraDecimalFormat.md)
  - java.io.[InputStream](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) (implements java.io.[Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true))
    - java.io.[FilterInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/FilterInputStream.html?is-external=true)
      - java.io.[BufferedInputStream](http://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html?is-external=true)
        - oracle.i18n.text.[UTF8ValidationFilter](oracle/i18n/text/UTF8ValidationFilter.md)
      - oracle.i18n.lcsd.[LCSDetectionInputStream](oracle/i18n/lcsd/LCSDetectionInputStream.md)
        - oracle.i18n.lcsd.[LCSDetectionHTMLInputStream](oracle/i18n/lcsd/LCSDetectionHTMLInputStream.md)
  - oracle.i18n.lcsd.[LCSDetector](oracle/i18n/lcsd/LCSDetector.md)
  - oracle.i18n.lcsd.[LCSDResultSet](oracle/i18n/lcsd/LCSDResultSet.md)
  - oracle.i18n.util.[LocaleMapper](oracle/i18n/util/LocaleMapper.md)
  - oracle.i18n.servlet.localesource.[LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) (implements java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.i18n.servlet.localesource.[ApplicationDefault](oracle/i18n/servlet/localesource/ApplicationDefault.md)
    - oracle.i18n.servlet.localesource.[DBLocaleSource](oracle/i18n/servlet/localesource/DBLocaleSource.md)
    - oracle.i18n.servlet.localesource.[HttpAcceptLanguage](oracle/i18n/servlet/localesource/HttpAcceptLanguage.md)
    - oracle.i18n.servlet.localesource.[UserInput](oracle/i18n/servlet/localesource/UserInput.md)
  - oracle.i18n.servlet.localesource.[LocaleSource.Alignment](oracle/i18n/servlet/localesource/LocaleSource.Alignment.md) (implements java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - oracle.i18n.servlet.localesource.[LocaleSource.Parameter](oracle/i18n/servlet/localesource/LocaleSource.Parameter.md)
  - oracle.i18n.servlet.localesource.[LocaleSource.WritingDirection](oracle/i18n/servlet/localesource/LocaleSource.WritingDirection.md) (implements java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - oracle.i18n.servlet.[Localizer](oracle/i18n/servlet/Localizer.md)
  - oracle.i18n.net.[MimeUtility](oracle/i18n/net/MimeUtility.md)
  - oracle.i18n.text.[OraCollationKey](oracle/i18n/text/OraCollationKey.md) (implements java.lang.[Comparable](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true))
  - oracle.i18n.text.[OraCollator](oracle/i18n/text/OraCollator.md) (implements java.lang.[Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), java.util.[Comparator](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true))
  - oracle.i18n.text.[OraDateFormatSymbols](oracle/i18n/text/OraDateFormatSymbols.md) (implements java.lang.[Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - oracle.i18n.text.[OraDecimalFormatSymbols](oracle/i18n/text/OraDecimalFormatSymbols.md) (implements java.lang.[Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - oracle.i18n.util.[OraDisplayLocaleInfo](oracle/i18n/util/OraDisplayLocaleInfo.md)
  - oracle.i18n.util.[OraLocaleInfo](oracle/i18n/util/OraLocaleInfo.md)
  - oracle.i18n.text.[OraNormalizer](oracle/i18n/text/OraNormalizer.md)
  - oracle.i18n.util.[OraResourceBundle](oracle/i18n/util/OraResourceBundle.md)
  - oracle.i18n.util.[OraSQLUtil](oracle/i18n/util/OraSQLUtil.md)
  - oracle.i18n.text.[OraUnicodeProperty](oracle/i18n/text/OraUnicodeProperty.md) (implements java.io.[Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
  - java.io.[Reader](http://docs.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true) (implements java.io.[Closeable](http://docs.oracle.com/javase/8/docs/api/java/io/Closeable.html?is-external=true), java.lang.[Readable](http://docs.oracle.com/javase/8/docs/api/java/lang/Readable.html?is-external=true))
    - java.io.[FilterReader](http://docs.oracle.com/javase/8/docs/api/java/io/FilterReader.html?is-external=true)
      - oracle.i18n.text.[CharacterValidationReader](oracle/i18n/text/CharacterValidationReader.md)
    - oracle.i18n.lcsd.[LCSDetectionReader](oracle/i18n/lcsd/LCSDetectionReader.md)
      - oracle.i18n.lcsd.[LCSDetectionHTMLReader](oracle/i18n/lcsd/LCSDetectionHTMLReader.md)
  - oracle.i18n.servlet.filter.[ServletFilter](oracle/i18n/servlet/filter/ServletFilter.md) (implements javax.servlet.[Filter](http://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html?is-external=true))
  - oracle.i18n.servlet.[ServletHelper](oracle/i18n/servlet/ServletHelper.md)
  - javax.servlet.[ServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequestWrapper.html?is-external=true) (implements javax.servlet.[ServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletRequest.html?is-external=true))
    - javax.servlet.http.[HttpServletRequestWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequestWrapper.html?is-external=true) (implements javax.servlet.http.[HttpServletRequest](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletRequest.html?is-external=true))
      - oracle.i18n.servlet.filter.[ServletRequestWrapper](oracle/i18n/servlet/filter/ServletRequestWrapper.md)
  - javax.servlet.[ServletResponseWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletResponseWrapper.html?is-external=true) (implements javax.servlet.[ServletResponse](http://docs.oracle.com/javaee/7/api/javax/servlet/ServletResponse.html?is-external=true))
    - javax.servlet.http.[HttpServletResponseWrapper](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletResponseWrapper.html?is-external=true) (implements javax.servlet.http.[HttpServletResponse](http://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServletResponse.html?is-external=true))
      - oracle.i18n.servlet.filter.[ServletResponseWrapper](oracle/i18n/servlet/filter/ServletResponseWrapper.md)
  - oracle.i18n.net.[URLDecoder](oracle/i18n/net/URLDecoder.md)
  - oracle.i18n.net.[URLEncoder](oracle/i18n/net/URLEncoder.md)
  - oracle.i18n.text.[UTF8ValidationFilter.ValidationBehavior](oracle/i18n/text/UTF8ValidationFilter.ValidationBehavior.md)

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
