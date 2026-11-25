This illustration shows the UML class diagram that models the implementation of the Power Demand Sample Data Cartridge. This diagram is identical to the preceding UML model, except in that it excludes cameras, satellite images, sensors, and cell temperature readings.

- Power Cartridge User

  - Relationship: 1 to many "retrieves" and "stores" association with Hourly Demand Status

- Regional Grid

  - Attribute: "Grid No"

  - Relationships: 1 to many "association with Hourly Demand Status, and an is an aggregation of Locator

- Hourly Demand Status

  - Attributes: "Date", "Time", "TotalGridDemand", "MaxCellDemand", "MinCellDemand"

  - Methods: "calcTotalGridDemand()", "getMaxCellDemand()", "getMinCellDemand()", "isEqualToSpecificCell()", "isEqualToAnyCell()"

  - Relationships: many to 1 "association with Regional Grid, many to 1 "retrieves" and "stores" association with Power Cartridge User, and 1 to 100 aggregation of Cell Demand Reading

- Locator

  - Attributes: "NW", "NE", "SW", "SE"

  - Relationships: 1 to 1 aggregation component of Cell, and an aggregation component of Regional Grid

- Cell Demand Reading

  - Attributes: "CellNo", "Demand"

  - Relationships: 1 to 1 aggregation "reads demand for" of Cell, and 100 to 1 aggregation component of Hourly Demand Status

- Cell

  - Attribute: "CellNo"

  - Relationships: 1 to 1 aggregation of Meter, 1 to 1 aggregation of Locator, 1 to 2 aggregation of Grid Coordinate, and 1 to 1 aggregation component of Cell Demand Reading

- Meter

  - Relationship: 1 to 1 aggregation component of Cell

- Grid Coordinate

  - Attributes: "x" and "y"

  - Relationship: 2 to 1 aggregation component of Cell
