------------------------------------------------------------------------

#### new Filter()

The base class for all feature filters.

Each filter evaluates a single feature; if the feature's attribute(s) or
geometry passes the filter, the evaluate function returns true.

Multiple filters can be chained together using one of the combination filters
such as the AndFilter (conjunction) or AnyFilter (disjunction).

##### Returns:

An instance of OM.filter.Filter

Type
OM.filter.Filter
