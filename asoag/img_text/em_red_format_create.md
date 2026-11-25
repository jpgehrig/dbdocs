# Description of the illustration em_red_format_create.png

Image em_red_format_create.png shows the Create dialog box with the following components, top to bottom, left to right:

- From top to bottom, the following: Format Name field, Description field, Sensitive Column Type menu, Redaction Function menu, a label describing the type of currently selected redaction function

- The Function Attributes region, which has the following, from top to bottom, based on a selection of the REGEX redaction function:

  - Pattern (Specifies the regular expression pattern to be searched. Example: '\d\d\d\d\d\d678' for number like '012345678')

  - Replace String (Example: Use 'XXXXXX\3' (replace string) to redact '012345678' (actual value) which matches '(\d\d\d) (\d\d\d) (\d\d\d)' (regexp pattern) to 'XXXXXX678' (redacted value). Note that the '\3' in the replace string preserves the actual data in the third set of parentheses in the pattern.)

  - Position (Specifies the starting position of the string search. The default is 1, meaning it begins the search from the first character of column data.)

  - Occurrence (Specifies how to perform the search and replace operation. Zero means it replaces all occurrences. Positive integer 'n' would replace nth occurrence of the string.)

  - Match Parameter menu (Specifies the matching parameters for the REGEX redaction function.)

- At the lower right corner, from left to right, the buttons OK and Cancel
