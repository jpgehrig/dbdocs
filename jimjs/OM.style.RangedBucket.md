------------------------------------------------------------------------

#### new RangedBucket(config)

This class defines a Ranged bucket. A ranged bucket typically has two values
representing the two ends (low, high) of a continuous numeric range.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                             |
|----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A config object with the following attributes:<br>• low {float} The low value for this range<br>• high {float} The high value for this range<br>• includeHighValue {boolean} Whether the high value should be inclusive. By default<br>the high value of a bucket is not inclusive.<br> |

##### Returns:

An instance of OM.style.RangedBucket

Type
OM.style.RangedBucket

### Extends

- [OM.style.Bucket](OM.style.Bucket.md)

### Methods

------------------------------------------------------------------------

#### clone()

Returns a clone of this bucket.

Inherited From:
- [OM.style.Bucket#clone](OM.style.Bucket.md)
