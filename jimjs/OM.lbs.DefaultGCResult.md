------------------------------------------------------------------------

#### new DefaultGCResult()

DefaultGCResult represents the default geocoding result for a single address.

It is typically set by the GeoCoder class on the corresponding Address
instance. In the case of a successful geocoding, one or more matches may be
contained in the DefaultGCResult instance. Each match varies by how relaxed the
match mode is, and is stored in its own Match instance.
The DefaultGCResult contains these properties:

- id : the id (if any) specified in the input address.
- rawResponse : the raw (XML) response from the geocoding service.
- matches : an array containing one or more instances of Match class
