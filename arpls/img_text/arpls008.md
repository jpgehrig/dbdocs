# Description of the illustration arpls008.eps

This illustration describes execution flow in DBMS_SQL that begins with "open_cursor" and ends with "close_cursor".

The key to the symbols used:

- ... -\> denotes "continue to next step", for example "open cursor" -\> "PARSE"

- ... material enclosed in double quotation marks denotes an action, for example "PARSE"

- ... material enclosed in single quotation marks denotes a choice point, for example 'Use bind variables': Yes/No

-------------------------------------------------------------------------------------------------------------

"open_cursor" -\> "PARSE" -\> Choice point: 'Use bind variables': Yes/No

- 'Use bind variables': Yes/No ...Yes -\> "bind variable" (option to repeat) -\> Choice point: 'query' -\>

- 'Use bind variables': Yes/No ...No -\> Choice point: 'query' -\>

Choice point: 'query': Yes/No

- Choice point: 'query': Yes/No ...Yes -\> "`DEFINE_COLUMN`" (option to repeat) -\> "EXECUTE" -\> "`FETCH_ROWS`" -\> "column_value, variable_value" (option to repeat) -\> option to loop back to "EXECUTE", option to loop back to "fetch_rows", option to loop back to "PARSE", option to loop back to 'Use bind variables', option to loop back to 'query' -\> "close_cursor"

- Choice point: query Yes/No ...No -\> "EXECUTE" -\> Choice point: pl/sql block(s): Yes/No

  - Choice point: pl/sql block(s): Yes/No ...Yes -\> Choice point: 'Use variable values': Yes/No

    - Choice point: 'Use variable values': Yes/No ... Yes -\> "variable_value" (option to repeat) -\> option to loop back to "PARSE", option to loop back to 'Use bind variables', option to loop back to 'query' -\> close_cursor

    - Choice point: 'Use variable values': Yes/No ... No -\> option to loop back to "PARSE", option to loop back to 'Use bind variables', option to loop back to 'query' -\> close_cursor

  - Choice point: pl/sql block(s): Yes/No ...No -\> option to loop back to "PARSE", option to loop back to 'Use bind variables', option to loop back to 'query' -\> close_cursor
