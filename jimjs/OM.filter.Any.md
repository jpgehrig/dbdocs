------------------------------------------------------------------------

#### new Any(filterArray)

This is a combo-filter that evaluates a feature to be true if any one of
the filters in the supplied list evaluates the feature to be true. i.e. it performs an OR

##### Parameters:

| Name          | Type  | Description                            |
|---------------|-------|----------------------------------------|
| `filterArray` | Array | An array of OM.filter.Filter instances |

##### Returns:

An instance of OM.filter.Any

Type
OM.filter.Any

### Extends

- [OM.filter.Filter](OM.filter.Filter.md)
