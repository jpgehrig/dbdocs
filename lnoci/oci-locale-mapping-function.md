Lists and describes OCI locale-mapping functions.

Table 31-3 lists an OCI locale-mapping function that is described in this section.

The OCI locale-mapping function performs name mapping to and from Oracle Database, Internet Assigned Numbers Authority (IANA), and International Organization for Standardization (ISO) names for character set names, language names, and territory names.

Table 31-3 OCI Locale-Mapping Function

| Function        | Purpose                                                                                                                                                                                            |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OCINlsNameMap() | Map Oracle Database character set names, language names, and territory names to and from Internet Assigned Numbers Authority (IANA) and International Organization for Standardization (ISO) names |

### 31.3.1 OCINlsNameMap()

Maps Oracle Database character set names, language names, and territory names to and from Internet Assigned Numbers Authority (IANA) and International Organization for Standardization (ISO) names.

#### Purpose

Maps Oracle Database character set names, language names, and territory names to and from Internet Assigned Numbers Authority (IANA) and International Organization for Standardization (ISO) names.

#### Syntax

    sword OCINlsNameMap ( void             *hndl,
                          OraText          *buf,
                          size_t            buflen,
                          const OraText    *srcbuf,
                          uword             flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle. If the handle is invalid, then the function returns `OCI_INVALID_HANDLE`.

buf (OUT)
Points to the destination buffer. If the function returns `OCI_SUCCESS`, then the parameter contains a `NULL`-terminated string for the requested name.

buflen (IN)
The size of the destination buffer. The recommended size is `OCI_NLS_MAXBUFSZ` to guarantee storage of a globalization support name. If the size of the destination buffer is smaller than the length of the name, then the function returns `OCI_ERROR`.

srcbuf (IN)
Pointer to a `NULL`-terminated globalization support name. If it is not a valid name, then the function returns `OCI_ERROR`.

flag (IN)
It specifies the direction of the name mapping and can take the following values:

- `OCI_NLS_CS_IANA_TO_ORA`: Map character set name from IANA to Oracle Database
- `OCI_NLS_CS_ORA_TO_IANA`: Map character set name from Oracle Database to IANA
- `OCI_NLS_LANG_ISO_TO_ORA`: Map language name from ISO to Oracle Database
- `OCI_NLS_LANG_ORA_TO_ISO`: Map language name from Oracle Database to ISO
- `OCI_NLS_LOCALE_A2_ISO_TO_ORA`: Map locale name from A2 ISO to Oracle Database
- `OCI_NLS_LOCALE_ORA_TO_A2_ISO`: Map locale name from Oracle Database to A2 ISO
- `OCI_NLS_TERR_ISO_TO_ORA`: Map territory name from ISO to Oracle Database
- `OCI_NLS_TERR_ORA_TO_ISO`: Map territory name from Oracle Database to ISO
- `OCI_NLS_TERR_ISO3_TO_ORA`: Map territory name from 3-letter ISO abbreviation to Oracle Database
- `OCI_NLS_TERR_ORA_TO_ISO3`: Map territory name from Oracle Database to 3-letter ISO abbreviation

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.
