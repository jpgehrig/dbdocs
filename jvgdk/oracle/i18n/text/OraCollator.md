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

- [Prev Class](OraCollationKey.md)
- [Next Class](OraDateFormat.md)

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

oracle.i18n.text

## Class OraCollator

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraCollator

<!-- -->

- All Implemented Interfaces:
  [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), [Comparator](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true)

  ------------------------------------------------------------------------



      public class OraCollator
      extends Object
      implements Cloneable, Comparator

  The `OraCollator` class performs locale-sensitive string comparisons, including linguistic collation and binary sorting.
  Since:
  Oracle 10.1.0.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                  |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `CANONICAL_COMPOSITION`<br>The `OraCollator` class composition level value.                                                            |
    | `static int`      | `EQUAL`<br>The result of the comparison that the `OraCollator` object returns if the two strings are equal.                            |
    | `static int`      | `GREATER`<br>The result of the comparison that the `OraCollator` object returns if the first string is greater than the second string. |
    | `static int`      | `LESS`<br>The result of the comparison that the `OraCollator` object returns if the first string is less than the second string.       |
    | `static int`      | `NO_COMPOSITION`<br>The `OraCollator` class composition level value.                                                                   |
    | `static int`      | `PRIMARY`<br>The `OraCollator` class strength value.                                                                                   |
    | `static int`      | `SECONDARY`<br>The `OraCollator` class strength value.                                                                                 |
    | `static int`      | `TERTIARY`<br>The `OraCollator` class strength value.                                                                                  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier     | Constructor and Description                                         |
    |--------------|---------------------------------------------------------------------|
    | `protected ` | `OraCollator``()`<br>The constructor is here only for completeness. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                       |
    |---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `clone``()`<br>Makes an independent duplicate of the `OraCollator` object.                                                                                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                       | `compare``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` source, `[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` target)`<br>Compares two objects using the current collation rule.                                                                                                                                            |
    | `int`                                                                                       | `compare``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` target)`<br>Compares two strings using the current collation rule.                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `convertToBaseLetter``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source)`                                                                                                                                                                                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `convertToCaseFold``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source)`                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                   | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Returns `true` if this `OraCollator` object is equal to another.                                                                                                                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getCharSet``()`<br>Gets the `charSet` name of this `OraCollator` object.                                                                                                                                                                                                                                                                                                                                                    |
    | [`OraCollationKey`](OraCollationKey.md)                                                     | `getCollationKey``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source)`<br>Gets the `OraCollationKey` object for a given source string.                                                                                                                                                                                                                                    |
    | `int`                                                                                       | `getComposition``()`<br>Gets the composition level used for comparison.                                                                                                                                                                                                                                                                                                                                                      |
    | `static OraCollator`                                                                        | `getInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraCollator.getInstance(Locale)`                                                                                                                                                                                                                                                                                               |
    | `static OraCollator`                                                                        | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Constructs an Oracle collation object from the Java locale.                                                                                                                                                                                                                                         |
    | `static OraCollator`                                                                        | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sortRule, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charSet)`<br>Constructs an `OraCollator` instance from the specified `sortRule` value and locale. |
    | `static OraCollator`                                                                        | `getInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` oraLocale)`<br>Constructs an Oracle collation object from an `OraLocaleInfo` object.                                                                                                                                                                                                                                                                            |
    | `static OraCollator`                                                                        | `getInstance``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sortRule)`<br>Constructs an `OraCollator` instance from the specified `sortRule` value.                                                                                                                                                                                                                         |
    | `static OraCollator`                                                                        | `getInstance``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sortRule, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charSet)`<br>Constructs an `OraCollator` instance from the specified `sortRule` value.                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getName``()`<br>Gets the sorting rule name of this `OraCollator` object.                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                       | `getStrength``()`<br>Gets the strength used in comparisons.                                                                                                                                                                                                                                                                                                                                                                  |
    | `int`                                                                                       | `hashCode``()`<br>Creates a hash code for this `OraCollator` object based on sort rule, strength, and decomposition level.                                                                                                                                                                                                                                                                                                   |
    | `int[]`                                                                                     | `matchFirst``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>This method searches pattern string from the beginning of source string.                                                                                                                      |
    | `int[]`                                                                                     | `matchLast``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>This method searches pattern string from the end of source string.                                                                                                                             |
    | `void`                                                                                      | `setComposition``(int compositionMode)`<br>Sets the composition level used for comparison.                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                      | `setStrength``(int newStrength)`<br>Sets the strength used in comparisons.                                                                                                                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

    <!-- -->

    - ### Methods inherited from interface java.util.[Comparator](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true)

      [`comparing`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#comparing-java.util.function.Function-)`, `[`comparing`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#comparing-java.util.function.Function-java.util.Comparator-)`, `[`comparingDouble`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#comparingDouble-java.util.function.ToDoubleFunction-)`, `[`comparingInt`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#comparingInt-java.util.function.ToIntFunction-)`, `[`comparingLong`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#comparingLong-java.util.function.ToLongFunction-)`, `[`naturalOrder`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#naturalOrder--)`, `[`nullsFirst`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#nullsFirst-java.util.Comparator-)`, `[`nullsLast`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#nullsLast-java.util.Comparator-)`, `[`reversed`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#reversed--)`, `[`reverseOrder`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#reverseOrder--)`, `[`thenComparing`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparing-java.util.Comparator-)`, `[`thenComparing`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparing-java.util.function.Function-)`, `[`thenComparing`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparing-java.util.function.Function-java.util.Comparator-)`, `[`thenComparingDouble`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparingDouble-java.util.function.ToDoubleFunction-)`, `[`thenComparingInt`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparingInt-java.util.function.ToIntFunction-)`, `[`thenComparingLong`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#thenComparingLong-java.util.function.ToLongFunction-)

<!-- -->

- - ### Field Detail

    - #### PRIMARY

          public static final int PRIMARY

      The `OraCollator` class strength value. When set, only primary differences are considered significant during comparison. The assignment of strengths to language features is locale dependant. For example, different base letters ("a" vs. "b") are considered a primary difference. For monolingual and binary sort, a primary setting means accent insensitive.
      See Also:
      `OraCollator.setStrength(int)`, `OraCollator.getStrength()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECONDARY

          public static final int SECONDARY

      The `OraCollator` class strength value. When set, only secondary and higher-order differences are considered significant during comparison. The assignment of strengths to language features is locale dependant. For example, different accented forms of the same base letter ("a" vs. "â") are considered a secondary difference. For monolingual and binary sort, a secondary setting means case insensitive .
      See Also:
      `OraCollator.setStrength(int)`, `OraCollator.getStrength()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TERTIARY

          public static final int TERTIARY

      The `OraCollator` class strength value. When set, only tertiary and higher-order differences are considered significant during comparison. The assignment of strengths to language features is locale dependant. For example, case differences ("a" vs. "A") are considered a tertiary difference.
      See Also:
      `OraCollator.setStrength(int)`, `OraCollator.getStrength()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NO_COMPOSITION

          public static final int NO_COMPOSITION

      The `OraCollator` class composition level value. When the composition level set to `NO_COMPOSITION`, canonical equivalence is not considered.
      See Also:
      `OraCollator.setComposition(int)`, `OraCollator.getComposition()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CANONICAL_COMPOSITION

          public static final int CANONICAL_COMPOSITION

      The `OraCollator` class composition level value. When the composition level set to `CANONICAL_COMPOSITION`, canonical equivalence is considered as the same.
      See Also:
      `OraCollator.setComposition(int)`, `OraCollator.getComposition()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EQUAL

          public static final int EQUAL

      The result of the comparison that the `OraCollator` object returns if the two strings are equal.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LESS

          public static final int LESS

      The result of the comparison that the `OraCollator` object returns if the first string is less than the second string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GREATER

          public static final int GREATER

      The result of the comparison that the `OraCollator` object returns if the first string is greater than the second string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OraCollator

          protected OraCollator()

      The constructor is here only for completeness. The `getInstance` method should be used instead to create new `OraCollator` objects.

  <!-- -->

  - ### Method Detail

    - #### getInstance

          public static OraCollator getInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraCollator.getInstance(Locale)`
      Constructs an Oracle collation object from the default Java locale. Converts the default Java locale to the `OraLocaleInfo` object using the default sorting rule.
      Returns:
      `OraCollator` instance

    <!-- -->

    - #### getInstance

          public static OraCollator getInstance(Locale locale)

      Constructs an Oracle collation object from the Java locale. It converts the Java locale to Oracle locale and uses the result to get the `OraCollator` object.
      Parameters:
      `locale` - Java `Locale` object

      Returns:
      `OraCollator` instance

    <!-- -->

    - #### getInstance

          public static OraCollator getInstance(OraLocaleInfo oraLocale)

      Constructs an Oracle collation object from an `OraLocaleInfo` object. Retrieves the default collator associated with the `OraLocaleInfo` object.
      Parameters:
      `oraLocale` - `OraLocaleInfo` object

      Returns:
      `OraCollator` instance

    <!-- -->

    - #### getInstance

          public static OraCollator getInstance(String sortRule)

      Constructs an `OraCollator` instance from the specified `sortRule` value. The `sortRule` values are the same as NLSRTL's NLS_SORT names; for example, `xgerman`, `GENERIC_M`, `unicode_binary`, `binary`, etc. `ai` or `ci` can be attached to sort rules to specify the comparison level.
      Parameters:
      `sortRule` - Oracle sort rule name

      Returns:
      `OraCollator` instance

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid sort rule name is specified

    <!-- -->

    - #### getInstance

          public static OraCollator getInstance(String sortRule,
                                                String charSet)

      Constructs an `OraCollator` instance from the specified `sortRule` value. This method will take both Oracle sorting rule and "binary" as `sortRule` value. If using Oracle sorting rule, the `charSet` values will be ignored. If using binary sorting rule, the `charSet` value could be specified by a valid character set on the database server. `ai` or `ci` can be attached to "binary" for specifying the comparison level.
      Parameters:
      `sortRule` - Oracle sort rule name

      `charSet` - Oracle database character set, could be `null`. The default is UTF16

      Returns:
      `OraCollator` instance

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid sort rule name is specified

    <!-- -->

    - #### getInstance

          public static OraCollator getInstance(Locale locale,
                                                String sortRule,
                                                String charSet)

      Constructs an `OraCollator` instance from the specified `sortRule` value and locale. This method will take both Oracle sorting rule and "binary" as `sortRule` value. If using Oracle sorting rule, the `charSet` values will be ignored. If using binary sorting rule, the `charSet` value could be specified by a valid character set on the database server. `ai` or `ci` can be attached to "binary" for specifying the comparison level. It also records the locale information in the instance.
      Parameters:
      `locale` - Java `Locale` object

      `sortRule` - Oracle sort rule name

      `charSet` - Oracle database character set, could be `null`. The default is UTF16

      Returns:
      `OraCollator` instance

    <!-- -->

    - #### getName

          public String getName()

      Gets the sorting rule name of this `OraCollator` object.
      Returns:
      sorting rule name

    <!-- -->

    - #### getCharSet

          public String getCharSet()

      Gets the `charSet` name of this `OraCollator` object.
      Returns:
      database character set

    <!-- -->

    - #### setStrength

          public void setStrength(int newStrength)

      Sets the strength used in comparisons. Strength could have the values of `PRIMARY`, `SECONDARY`, or `TERTIARY`.
      Parameters:
      `newStrength` - the new strength to be set, options are `PRIMARY`, `SECONDARY` or `TERTIARY`

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid strength is specified

      See Also:
      `OraCollator.PRIMARY`, `OraCollator.SECONDARY`, `OraCollator.TERTIARY`

    <!-- -->

    - #### getStrength

          public int getStrength()

      Gets the strength used in comparisons. Strength could have the values of `PRIMARY`, `SECONDARY`, or `TERTIARY`.
      Returns:
      the current strength

      See Also:
      `OraCollator.PRIMARY`, `OraCollator.SECONDARY`, `OraCollator.TERTIARY`

    <!-- -->

    - #### setComposition

          public void setComposition(int compositionMode)

      Sets the composition level used for comparison. Composition level could be either `CANONICAL_COMPOSITION` or `NO_COMPOSITION`.
      Parameters:
      `compositionMode` - the composition level to be set, options are either `CANONICAL_COMPOSITION` or `NO_COMPOSITION`

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if an invalid composition mode is specified

      See Also:
      `OraCollator.NO_COMPOSITION`, `OraCollator.CANONICAL_COMPOSITION`

    <!-- -->

    - #### getComposition

          public int getComposition()

      Gets the composition level used for comparison. Composition level could be either `CANONICAL_COMPOSITION` or `NO_COMPOSITION`.
      Returns:
      the current composition level

      See Also:
      `OraCollator.NO_COMPOSITION`, `OraCollator.CANONICAL_COMPOSITION`

    <!-- -->

    - #### clone

          public Object clone()

      Makes an independent duplicate of the `OraCollator` object.
      Overrides:
      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      `OraCollator` object

    <!-- -->

    - #### hashCode

          public int hashCode()

      Creates a hash code for this `OraCollator` object based on sort rule, strength, and decomposition level.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a hash code

    <!-- -->

    - #### equals

          public boolean equals(Object obj)

      Returns `true` if this `OraCollator` object is equal to another.
      Specified by:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#equals-java.lang.Object-) in interface [`Comparator`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true)

      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `obj` - a target object with which to be compared

      Returns:
      `true` if equal or `false` if not

    <!-- -->

    - #### compare

          public int compare(Object source,
                             Object target)

      Compares two objects using the current collation rule. The comparison result depends on the sorting rule and the setting of comparison level.
      This implementation merely returns `compare((String)o1, (String)o2)`.

      Specified by:
      [`compare`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true#compare-T-T-) in interface [`Comparator`](http://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html?is-external=true)

      Parameters:
      `source` - first `Object` to be compared

      `target` - second `Object` to be compared

      Returns:
      `OraCollator.GREATER`, `OraCollator.EQUAL`, or `OraCollator.LESS`

    <!-- -->

    - #### compare

          public int compare(String source,
                             String target)

      Compares two strings using the current collation rule. The comparison result depends on the sorting rule and the setting of comparison level.
      Parameters:
      `source` - first `String` to be compared

      `target` - second `String` to be compared

      Returns:
      `OraCollator.GREATER`, `OraCollator.EQUAL`, or `OraCollator.LESS`

    <!-- -->

    - #### getCollationKey

          public OraCollationKey getCollationKey(String source)

      Gets the `OraCollationKey` object for a given source string.
      Parameters:
      `source` - source string to get Oracle collation key

      Returns:
      `OraCollationKey` object

    <!-- -->

    - #### convertToBaseLetter

          public String convertToBaseLetter(String source)

    <!-- -->

    - #### convertToCaseFold

          public String convertToCaseFold(String source)

    <!-- -->

    - #### matchFirst

          public int[] matchFirst(String source,
                                  String pattern)

      This method searches pattern string from the beginning of source string.
      Parameters:
      `source` - source string as the target. pattern as pattern string.

      Returns:
      If match found, return the first index(position) of source string to int\[0\] and the index of the last character matched plus one to int\[1\]. The returning index range is from 0 to n for the source string length of n. Return -1 to int\[0\] and int\[1\] if no match.

    <!-- -->

    - #### matchLast

          public int[] matchLast(String source,
                                 String pattern)

      This method searches pattern string from the end of source string.
      Parameters:
      `source` - source string as the target. pattern as pattern string.

      Returns:
      If match found, return the index(position) of source string to int\[0\] and the index of the last character matched plus one to int\[1\]. The returning index range is from 0 to n for the source string length of n. Return -1 to int\[0\] and int\[1\] if no match.

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

- [Prev Class](OraCollationKey.md)
- [Next Class](OraDateFormat.md)

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
