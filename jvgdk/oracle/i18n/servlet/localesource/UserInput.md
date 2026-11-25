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

- [Prev Class](LocaleSource.WritingDirection.md)
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

oracle.i18n.servlet.localesource

## Class UserInput

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.i18n.servlet.localesource.LocaleSource](LocaleSource.md)

  - - oracle.i18n.servlet.localesource.UserInput

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class UserInput
      extends LocaleSource

  The `UserInput` class calls the `request.getParameter(LocaleSource.Parameter)` method to retrieve the user input. The user input locales are cached for subsequent use in the session. Note that the multipart request object is not supported.
  In typical web applications, user input comes from web clients that submit a form containing a locale and its attributes. The `UserInput` class is used when the application allows users to specify their language preference. By default, the parameters defined in the `LocaleSource.Parameter` class are recognized as the user input locale. Default Caching : This locale source is not cached in the session by default

  The `UserInput` locale source is declared in the *gdkapp.xml* configuration file via the `locale-determine-rule` hierarchy:

        <locale-determine-rule>
            <locale-source>
                oracle.i18n.servlet.localesource.UserInput
            </locale-source>
        </locale-determine-rule>



  The UserInput locale source rule can then be invoked from an HTML page, if a `locale` parameter with a value is posted. In the sample code below, selecting a locale and then submitting a button will result in an HTTP Post that the GDK intercepts and results in the change of the user interface language for the response.
        <html>
          ....

          <form>
            <select name="locale" size="1">
              <option value="de_CH">Switzerland [de_CH]</option>
              <option value="en_US">United States [en_US]</option>
            </select>
            <input  type="submit" value="Submit" />
          </form>

          ....
       </html>



  Since:
  10.1.0.2

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`LocaleSource.Alignment`](LocaleSource.Alignment.md)`, `[`LocaleSource.Parameter`](LocaleSource.Parameter.md)`, `[`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`equals`](LocaleSource.md)`, `[`getAttribute`](LocaleSource.md)`, `[`getCharacterSet`](LocaleSource.md)`, `[`getCollator`](LocaleSource.md)`, `[`getCurrencyFormat`](LocaleSource.md)`, `[`getDateFormat`](LocaleSource.md)`, `[`getDateTimeFormat`](LocaleSource.md)`, `[`getISOCurrency`](LocaleSource.md)`, `[`getLocale`](LocaleSource.md)`, `[`getLocaleSourceClass`](LocaleSource.md)`, `[`getNumberFormat`](LocaleSource.md)`, `[`getTimeFormat`](LocaleSource.md)`, `[`getTimeZone`](LocaleSource.md)`, `[`getWritingDirection`](LocaleSource.md)`, `[`hashCode`](LocaleSource.md)`, `[`isCached`](LocaleSource.md)`, `[`isReadOnly`](LocaleSource.md)`, `[`load`](LocaleSource.md)`, `[`setAttribute`](LocaleSource.md)`, `[`setCharacterSet`](LocaleSource.md)`, `[`setCollator`](LocaleSource.md)`, `[`setCurrencyFormat`](LocaleSource.md)`, `[`setDateFormat`](LocaleSource.md)`, `[`setDateTimeFormat`](LocaleSource.md)`, `[`setISOCurrency`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocaleSourceClass`](LocaleSource.md)`, `[`setNumberFormat`](LocaleSource.md)`, `[`setTimeFormat`](LocaleSource.md)`, `[`setTimeZone`](LocaleSource.md)`, `[`setWritingDirection`](LocaleSource.md)`, `[`store`](LocaleSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

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

- [Prev Class](LocaleSource.WritingDirection.md)
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
