## 13.60 SERIALLY_REUSABLE Pragma

The `SERIALLY_REUSABLE` pragma specifies that the package state is needed for only one call to the server (for example, an OCI call to the database or a stored procedure invocation through a database link).

After this call, the storage for the package variables can be reused, reducing the memory overhead for long-running sessions.

This pragma is appropriate for packages that declare large temporary work areas that are used once in the same session.

The `SERIALLY_REUSABLE` pragma can appear in the `declare_section` of the specification of a bodiless package, or in both the specification and body of a package, but not in only the body of a package.

### Topics

- Syntax

- Examples

- Related Topics

### Syntax

### serially_reusable_pragma ::=

![Description of serially_reusable_pragma.eps follows](img/serially_reusable_pragma.gif)
[Description of the illustration serially_reusable_pragma.eps](img_text/serially_reusable_pragma.md)

### Examples

- [Example 10-4](serially_reusable-packages.md), "Creating SERIALLY_REUSABLE Packages"

- [Example 10-5](serially_reusable-packages.md), "Effect of SERIALLY_REUSABLE Pragma"

- [Example 10-6](serially_reusable-packages.md), "Cursor in SERIALLY_REUSABLE Package Open at Call Boundary"

### Related Topics

- "[SERIALLY_REUSABLE Packages](serially_reusable-packages.md)"

- "[Pragmas](lexical-units.md)"
