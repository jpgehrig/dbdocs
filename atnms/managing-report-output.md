Use the list of commands in this section to manage the report output.

### Syntax

    [-syslog] [-tag tagname]
    [-o]
    [-nopass]
    [-noscore]
    [-diff old_report new_report [-outfile output_HTML]]
    [-merge [-force] collections]

### Parameters

Table A-3 Managing Output

| Option                                                           | Description                                                                                                                                                                                                                                                            |
|:-----------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-syslog`                                                        | Writes JSON results to syslog.                                                                                                                                                                                                                                         |
| `-tag ``tagname`                                                 | Appends the `tagname` specified to the output report name.<br>The `tagname` must contain only alphanumeric characters.                                                                                                                                                 |
| `-o`                                                             | Argument to an option.<br>If `-o` is followed by `v`, (or `verbose`, and neither option is case-sensitive), then the command prints passed checks on the screen.<br>If the `-o` option is not specified, then the command prints only the failed checks on the screen. |
| `-nopass`                                                        | Does not show passed checks in the generated output.                                                                                                                                                                                                                   |
| `-noscore`                                                       | Does not print health score in the HTML report.                                                                                                                                                                                                                        |
| `-diff ``old_report`` ``new_report`` [-outfile ``output_HTML``]` | Reports the difference between the two HTML reports.<br>Specify a directory name or a ZIP file or an HTML report file as `old_report` and `new_report`.                                                                                                                |
| `-merge [-force] ``collections`                                  | Merges a comma-delimited list of collections and prepares a single report.                                                                                                                                                                                             |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
