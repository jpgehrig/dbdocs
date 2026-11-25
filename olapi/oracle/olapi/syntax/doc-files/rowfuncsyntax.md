Skip navigation links

<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01</em></td>
</tr>
</tbody>
</table>

# Examples of TypedExpression Methods

This page has examples of the methods of the `TypedExpression` class In the examples, the `mp` object is the `MdmMetadataProvider` for the session.

------------------------------------------------------------------------

## Example for ascii

      TypedExpression char = (TypedExpression) SyntaxObject.fromSyntax("'Boston'", mp);
      TypedExpression asciiExpr = exp.ascii();
      System.out.println("The syntax of asciiExpr is " + asciiExpr.toSyntax());

The example produces the following output.

    The syntax of asciiExpr is ASCII('Boston')

The `asciiExpr` `TypedExpression` evaluates to `66`, which is the ASCII equivalent of the letter B.

------------------------------------------------------------------------

## Example for chr

      TypedExpression numExp = (TypedExpression) SyntaxObject.fromSyntax("67", mp);
      TypedExpression chrExp = numExp.chr();
      System.out.println("The syntax of chrExp is " + chrExp.toSyntax());

      // Example for chr(boolean usingNChar).
      boolean useNCharCS = true;
      TypedExpression chrNcharExp = numExp.chr(useNCharCS);
      System.out.println("The syntax of chrNcharExp is " + chrNcharExp.toSyntax());

The example produces the following output.

    The syntax of chrExp is CHR(67).
    The syntax of chrNcharExp is CHR(67 USING NCHAR_CS)

The `chrExp` `TypedExpression` evaluates to `C`.

The `chrNcharExp` `TypedExpression` evaluates to `C`.

------------------------------------------------------------------------

## Example for concat

       // Concatenate a TypedExpression and a String.
       TypedExpression char1 = (TypedExpression)
                                SyntaxObject.fromSyntax("'The time '", mp);
       TypedExpression concatExpS = char1.concat("has come.");
       System.out.println("The syntax of concatExpS is " + concatExpS.toSyntax());

       // Concatenate a TypedExpression and another TypedExpression.
       TypedExpression stringExp = (TypedExpression)
                                    SyntaxObject.fromSyntax("'is '", mp);
       TypedExpression curTime = (TypedExpression)
                                  SyntaxObject.fromSyntax("CURRENT_TIMESTAMP(2)", mp);
       TypedExpression char2 = stringExp.concat(curTime);
       TypedExpression concatExpT = char1.concat(char2);

       System.out.println("The syntax of concatExpT is " + concatExpT.toSyntax());

The example produces the following output.

    The syntax of concatExpS is 'The time ' || 'has come.'
    The syntax of concatExpT is 'The time ' || ('is ' || CURRENT_TIMESTAMP(2))

The `||` characters are the concatenation operator.

The `concatExpS` `TypedExpression` evaluates to `The time has come.`

The `concatExpT` `TypedExpression` evaluates to `The time is 19-OCT-06 11.19.29.63 AM -07:00`.

------------------------------------------------------------------------

## Example for initcap

      TypedExpression charExp = (TypedExpression)
                                 SyntaxObject.fromSyntax("'top tEN tunes'", mp);
      TypedExpression initcapExp = charExp.initcap();
      System.out.println("The syntax of initcapExp is " + initcapExp.toSyntax());

The example produces the following output.

    The syntax of initcapExpr is INITCAP('top tEN tunes')

The `initcapExpr` `TypedExpression` evaluates to `Top Ten Tunes`.

------------------------------------------------------------------------

## Examples for round

This first example rounds a number. It produces the `TypedExpression` objects `roundNumExpr` and `roundNegNumExpr`.

      NumberExpression n1 = (NumberExpression) SyntaxObject.fromSyntax("15.193", mp);
      NumberExpression rhs = (NumberExpression) SyntaxObject.fromSyntax("1", mp);
      TypedExpression roundNumExpr = n1.round(rhs);
      rhs = (NumberExpression) SyntaxObject.fromSyntax("-1", mp);
      TypedExpression roundNegNumExpr = n1.round(rhs);
      System.out.println("The syntax of roundNumExpr is " + roundNumExpr.toSyntax());
      System.out.println("The syntax of roundNegNumExpr is " +
                                                roundNegNumExpr.toSyntax());

The example produces the following output.

    The syntax of roundNumExpr is ROUND(15.193, 1)
    The syntax of roundNegNumExpr is ROUND(15.193, -1)

The `roundNumExpr` `TypedExpression` evaluates to `15.2`.
The `roundNegNumExpr` `TypedExpression` evaluates to `20`.

This second example rounds a date. It produces the `TypedExpression` object `roundedDateExpr`.

      DateExpression dateExpr = new DateExpression("2006-11-15", DataType.DATE);
      TypedExpression roundedDateExpr = dateExpr.round(fmt);
      System.out.println("The syntax of roundedDateExpr is " +
                          roundedDateExpr.toSyntax());

The example produces the following output.

    The syntax of roundedDateExpr is ROUND(DATE '2006-11-15', 'YEAR')

The `roundedDateExpr` `TypedExpression` evaluates to `01-JAN-07`.

------------------------------------------------------------------------

## Example for trunc

The following code produces the `TypedExpression` objects `truncNumExpr`, `truncNegNumExpr`, and `truncZeroNumExpr`.

      NumberExpression exp = (NumberExpression) SyntaxObject.fromSyntax("15.193", mp);
      NumberExpression fmt = (NumberExpression) SyntaxObject.fromSyntax("1", mp);
      TypedExpression truncNumExpr = exp.trunc(fmt);
      fmt = (NumberExpression) SyntaxObject.fromSyntax("-1", mp);
      TypedExpression truncNegNumExpr = exp.trunc(fmt);
      fmt = (NumberExpression) SyntaxObject.fromSyntax("0", mp);
      TypedExpression truncZeroNumExpr = exp.trunc(fmt);
      System.out.println("The syntax of truncNumExpr is " + truncNumExpr.toSyntax());
      System.out.println("The syntax of truncNegNumExpr is " +
                                                  truncNegNumExpr.toSyntax());
      System.out.println("The syntax of truncZeroNumExpr is " + truncZeroNumExpr.toSyntax());

The code produces the following output.

      The syntax of truncNumExpr is TRUNC(15.193, 1)
      The syntax of truncNegNumExpr is TRUNC(15.193, -1)
      The syntax of truncZeroNumExpr is TRUNC(15.193, 0)

The `truncNumExpr` `TypedExpression` evaluates to `15.2`.
The `truncNegNumExpr` `TypedExpression` evaluates to `20`.
The `truncZeroNumExpr` `TypedExpression` evaluates to `15`.

------------------------------------------------------------------------

## Example for widthBucket

      TypedExpression exp = (TypedExpression) SyntaxObject.fromSyntax("13", mp);
      TypedExpression minValue = (TypedExpression) SyntaxObject.fromSyntax("0", mp);
      TypedExpression maxValue = (TypedExpression) SyntaxObject.fromSyntax("20", mp);
      TypedExpression numBuckets = (TypedExpression) SyntaxObject.fromSyntax("4", mp);
      TypedExpression wbExpr = exp.widthBucket(minValue, maxValue, numBuckets);

      exp = (TypedExpression) SyntaxObject.fromSyntax("-5", mp);
      TypedExpression wbNegExpr = exp.widthBucket(minValue, maxValue, numBuckets);

      System.out.println("The syntax of wbExpr is " + wbExpr.toSyntax());
      System.out.println("The syntax of wbNegExpr is " + wbNegExpr.toSyntax());

The example produces the following output.

    The syntax of wbExpr is WIDTH_BUCKET(13, 0, 20, 4)
    The syntax of wbNegExpr is WIDTH_BUCKET(-5, 0, 20, 4)

The `wbExpr` `TypedExpression` evaluates to `3`. The evaluation creates four buckets from 0 to 20 and sorts the value 13 into bucket 3.

The `wbNegExpr` `TypedExpression` evaluates to `0`. The value -5 is below the beginning of the range.

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
