This dfigure illustrates the relationship between an advanced style and a theme in thematic mapping, and how the style and the theme relate to the base table. It is briefly explained in text before the illustration.

On the left side of the illustration is "Step 1: create advanced style," along with the V.SALES advanced style definition that includes several \<RangedBucket\> elements, one for each range of values (low to high). In addition, each \<RangedBucket\> element has an associated color style, for which the name and a sample (a small rectangle in that color) are provided. An arrow extends from the V.SALES name to the place in the theme definition on the right where the style name is specified (using the style attribute).

On the right side of the illustration is "Step 2: create predefined theme," along with the SALES_BY_REGION theme definition.

At the bottom of the illustration is a database icon with the REGIONS table definition: regions(geom, sales, name). The SALES column is linked by arrows to range bucket values in the style and to the column attribute in the theme.
