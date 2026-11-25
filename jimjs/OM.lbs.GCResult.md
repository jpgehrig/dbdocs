------------------------------------------------------------------------

#### new GCResult()

GCResult represents the geocoding result for a single address.

It is typically set by the GeoCoder class on the corresponding Address
instance. In the case of a successful geocoding, one or more matches may be
contained in the GCResult instance. Each match varies by how relaxed the
match mode is, and is stored in its own Match instance.
The GCResult contains these properties:

- id : the id (if any) specified in the input address.
- rawResponse : the raw (XML) response from the geocoding service.
- matches : an array containing one or more instances of Match class

### Members

------------------------------------------------------------------------

#### MATCH_CODE1

Exact match: the city name, postal code, street base name, street type
(and suffix or prefix or both, if applicable), and house or building
number match the data used for geocoding.

------------------------------------------------------------------------

#### MATCH_CODE2

The city name, postal code, street base name, and house or building
number match the data used for geocoding, but the street type, suffix, or
prefix does not match.

------------------------------------------------------------------------

#### MATCH_CODE3

The city name, postal code, and street base name match the data used for
geocoding, but the house or building number does not match.

------------------------------------------------------------------------

#### MATCH_CODE4

The city name and postal code match the data used for geocoding, but the
street address does not match.

------------------------------------------------------------------------

#### MATCH_CODE10

The city name matches the data used for geocoding, but the postal code
does not match.

------------------------------------------------------------------------

#### MATCH_CODE11

The postal code matches the data used for geocoding, but the city name
does not match.
