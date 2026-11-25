Flow chart of the cartridge development process. Defining custom index types is recommended for complex access methods. Where multi-domain queries are involved, implementing a custom optimization is also recommended.

"Inventory Domain" leads to "Define Key Objects".

"Define Key Objects" has two exit paths, Option 1 and Option 2.

Option 1: To "Package Existing 3GL code in a DLL" and then "Test" and "Installation Script(s) and User's Guide"

Option 2: To "Write SQL and PL/SQL for Object's Type Specification", and then to "Inventory Access Methods" and the decision point "Simple", which has two exit paths, Option 2.1 and Option 2.2.

Option 2.1: If "Simple", then "Build Regular Indexes" and continue as with Option 1.

Option 2.2: If not "Simple", then "Define Index Types" and the decision point "Multi-domain Queries", which has two exit paths, Option 2.2.1 and Option 2.2.2.

Option 2.2.1: If "Multi-domain Queries", then "Implement Extensible Optimizer", then "Test" and "Installation Script(s) and User's Guide".

Option 2.2.2: If not "Multi-domain Queries", then go to decision point "Cost of I/O Only Significant Factor", which has two exit paths, Option 2.2.2.1 and Option 2.2.1 (if not "Cost of I/O Only Significant Factor")

Option 2.2.2.1: If "Cost of I/O Only Significant Factor", then "Use Existing Optimizer", then "Test" and "Installation Script(s) and User's Guide"
