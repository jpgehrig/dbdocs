------------------------------------------------------------------------

#### new All(filterArray)

This is a combination filter that combines (ANDs) a list of Filter instances.
A feature passes this filter only if it passes all the filters in the list.

##### Parameters:

| Name          | Type  | Description                            |
|---------------|-------|----------------------------------------|
| `filterArray` | Array | An array of OM.filter.Filter instances |

##### Returns:

An instance of OM.filter.All

Type
OM.filter.All

### Extends

- [OM.filter.Filter](OM.filter.Filter.md)
