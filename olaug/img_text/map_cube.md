Units Cube Mapped in the Tabular View: This screen capture shows the mapping section for the `UNITS_CUBE` cube. At the top of the section are icons for the following tools:

- Graphical Mapping View

- Table Mapping View

- Auto Arrange Mappings

- Auto Map Star Schema

- Remove All Mappings

- Refresh Tables, Views, and Synonyms from Database

At the top right is the Group By list with the aggregate function `SUM` selected.

The `UNITS_CUBE` cube is mapped to columns in the Global `UNITS_FACT` table as follows.

- `UNITS_CUBE` has three measures with these mappings

- `UNITS` to `GLOBAL.UNITS_FACT.UNITS`

- `SALES` to `GLOBAL.UNITS_FACT.SALES`

- `COST` to `GLOBAL.UNITS_FACT.COST`

`UNITS_CUBE` has four dimensions, all of them mapped to the detail level of the source. In the schema tree the Aggregate From Level symbol Sigma Up Arrow appears after the name of the detail level of each dimension.

- `MONTH` level of `TIME` to `GLOBAL.UNITS_FACT.MONTH_ID`.

- `CHANNEL` level of `CHANNEL` to `GLOBAL.UNITS_FACT.CHANNEL_ID`.

- `SHIP_TO` level of `CUSTOMER` to `GLOBAL.UNITS_FACT.SHIP_TO_ID`.

- `ITEM` level of `PRODUCT` to `GLOBAL.UNITS_FACT.ITEM_ID`.

The join conditions for the dimensions are the following:

- `GLOBAL.TIME_DIM.MONTH_ID = GLOBAL.UNITS_FACT.MONTH_ID`

- `GLOBAL.CHANNEL_DIM.CHANNEL_ID = GLOBAL.UNITS_FACT.CHANNEL_ID`

- `GLOBAL.CUSTOMER_DIM.SHIP_TO_ID = GLOBAL.UNITS_FACT.SHIP_TO_ID`

- `GLOBAL.PRODUCT_DIM.ITEM_ID = GLOBAL.UNITS_FACT.ITEM_ID`

The Filter row is empty.

At the bottom of the mapping section are the following buttons:

- Help

- Show SQL

- Apply

- Revert
