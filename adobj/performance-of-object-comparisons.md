You can compare objects by invoking either a map or order method.

A map method converts objects into scalar values while preserving the ordering of the objects. Using a map method is preferable because it allows the system to efficiently order objects.

**Note:**

For any one object type, you can implement either a map or an order method, but not both. Neither are required.

The way objects are mapped has significant performance implications when sorting the objects using `ORDER` `BY` or `GROUP` `BY` processes. An object may need to be compared to other objects many times, and it is much more efficient if the objects can be mapped to scalar values first (the map method). If the comparison semantics are extremely complex, or if the objects cannot be mapped to scalar values for comparison, you can define an order method that, given two objects, returns the ordering determined by the object implementor. Order methods are not as efficient as map methods, so performance may suffer if you use order methods.

Consider an object type `address` consisting of four character attributes: `street`, `city`, `state`, and `zipcode`. Here, the most efficient comparison method is a map method because each object can be converted easily into scalar values. For example, you might define a map method that orders all of the objects by state.

On the other hand, suppose you want to compare binary objects, such as images. In this case, the comparison semantics may be too complex to use a map method; if so, you can use an order method to perform comparisons. For example, you could create an order method that compares images according to brightness or the number of pixels in each image.

If an object type does not have either a map or order method, only equality comparisons are allowed on objects of that type. In this case, Oracle performs the comparison by doing a field-by-field comparison of the corresponding object attributes, in the order they are defined. If the comparison fails at any point, a `FALSE` value is returned. If the comparison matches at every point, a `TRUE` value is returned. However, if an object has a LOB or `ANYDATA` attributes, then Oracle does not compare the object on a field-by-field basis. Such objects must have a map or order method to perform comparisons.
