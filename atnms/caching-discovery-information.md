Use the list of commands to manage caching of discovery data.

### Syntax

    orachk -discovery -discoverydir location
    exachk -discovery -discoverydir location

    orachk -checkdiscovery
    exachk -checkdiscovery

    orachk -usediscovery -discoverydir location
    exachk -usediscovery -discoverydir location

    orachk -refreshdiscovery
    exachk -refreshdiscovery

    orachk -rmdiscovery
    exachk -rmdiscovery

Table 2-5 Manage Caching of Discovery Data

| Command             | Description                                                                                                                                                 |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-discovery`        | Caches discovery data, which Oracle ORAchk and Oracle EXAchk can use for future runs.<br>`-discoverydir`: Specify the location to store the discovery data. |
| `-checkdiscovery`   | Verifies discovery data.                                                                                                                                    |
| `-usediscovery`     | Uses discovery data.<br>`-discoverydir`: Specify the location where you have cached the discovery data.                                                     |
| `-refreshdiscovery` | Refreshes discovery data.                                                                                                                                   |
| `-rmdiscovery`      | Removes cached discovery data.                                                                                                                              |

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)
