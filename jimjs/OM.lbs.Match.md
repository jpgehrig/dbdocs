------------------------------------------------------------------------

#### new Match()

Match is a class representing a single match determined by the geocoder
for an input address. Note that each input address can have potentially
one or more matches.

Each Match object may contain these properties:

- id : the id if specified in the input address.
- sequence : the sequence within all the matches for a given input address; starts at 0.
- longitude : the longtitude of the address
- latitude : the latitude of the address
- matchCode : the match code
- errorMessage : the error message containing detailed match information
- matchVector : the new match vector information
- outputAddress : the validated/cleaned-up address
