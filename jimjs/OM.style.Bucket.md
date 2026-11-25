------------------------------------------------------------------------

#### new Bucket(config)

This abstract class defines a bucket in a BucketStyle. OM.style.CollectionBucket and
OM.style.RangedBucket extend it.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                            |
|----------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A configuration object with the following attributes:<br><br>• seq {int} The sequence number<br>• label {String} A label string for the bucket<br>• labelStyle {OM.style.Style} A style for the labels |

##### Returns:

An instance of OM.style.Bucket

Type
OM.style.Bucket

### Methods

------------------------------------------------------------------------

#### clone()

Returns a clone of this bucket.
