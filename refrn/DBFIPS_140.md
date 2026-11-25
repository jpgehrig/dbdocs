## 1.101 DBFIPS_140

`DBFIPS_140` enables Transparent Data Encryption (TDE) and `DBMS_CRYPTO` PL/SQL package program units to run in a mode compliant to the Federal Information Processing Standard (subsequently known as "FIPS mode").

| Property            | Description                            |
|:--------------------|:---------------------------------------|
| Parameter type      | Boolean                                |
| Default value       | `false`                                |
| Modifiable          | No                                     |
| Modifiable in a PDB | No                                     |
| Range of values     | `true | false`                         |
| Basic               | No                                     |
| Oracle RAC          | All instances must use the same value. |

Set this parameter to `true` to use TDE and `DBMS_CRYPTO` in FIPS mode. This means that only FIPS-compliant algorithms may be used. By default, this parameter is set to `false`. When this parameter is set to `false`, all algorithms (FIPS-compliant or not) may be used.

**See Also:**

- [Oracle Database Security Guide](../dbseg/oracle-database-fips-140-settings.md) for information about configuring Oracle Database FIPS 140 settings

- [Oracle Database Security Guide](../dbseg/oracle-database-fips-140-settings.md) for a table that describes the effect of setting the value of `DBFIPS_140` to `true` or `false` on different platforms
