# Description of the illustration invoker_rights_solution.gif

The figure illustrates the invoker's rights solution. In the figure there are three schemas, `EAST`, `WEST`, and `HQ`. The `EAST` and `WEST` schema have their own `sales` table. The `analyze` procedure is in the `HQ` schema. The `EAST` and `WEST` schema access the `analyze` procedure from the `HQ` schema, which in turn accesses the `sales` tables of these schemas.
