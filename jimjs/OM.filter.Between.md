------------------------------------------------------------------------

#### new Between(filterAttribute, low, high)

This is a filter class that evaluates a feature to check if the specified attribute
value falls within a numeric range. A value passes this filter if
it is greater than or equal to the low value and smaller than or equal to the high value.
i.e. the value of expr1 BETWEEN expr 2 and expr3 is the value of
the boolean expression: expr2 \<= expr1 AND expr1 \<= expr3

##### Parameters:

| Name              | Type   | Description                                       |
|-------------------|--------|---------------------------------------------------|
| `filterAttribute` | String | The name of the feature attribute to be evaluated |
| `low`             | float  | minimum value (inclusive)                         |
| `high`            | float  | maximum value (inclusive)                         |

##### Returns:

An instance of OM.filter.Between

Type
OM.filter.Between

### Extends

- [OM.filter.Filter](OM.filter.Filter.md)
