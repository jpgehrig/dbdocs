# Description of the illustration arpls006.eps

This illustration describes execution flow in UTL_HTTP that has two phases: (1) beginning with "begin_request" and ending with "end_request", (2) beginning with "get_response" and ending with "end_response".

The key to the symbols used is:

- ... -\> (an arrow) denotes "continue to next step", for example, "begin_request" -\> "get_response"

- ... material enclosed in double quotation marks denotes an action, for example "PARSE"

- ... material enclosed in single qutotation marks denotes a choice point, for example, 'perform pre-response set operations': Yes/No

- ... material unenclosed denotes a choice of direction, for example, Yes

---------------------------------------------------------------------------------------------

PHASE \#1.

- "begin_request" -\> 'perform pre-response set operations': Yes/No

  - 'perform set operations': Yes -\> "set_cookie_support" (optional with option to repeat multiple times) -\> "set_persistent_conn_support" (optional with option to repeat multiple times)-\> "set_body_charset" (optional with option to repeat multiple times) -\> "set_follow_redirect" (optional with option to repeat multiple times) -\>"set_authentication" (optional with option to repeat multiple times) -\> "set_header" (optional with option to repeat multiple times) -\> 'perform pre-response write operations':Yes/No

  - 'perform set operations': No -\> 'perform write operations':Yes/No

- 'perform pre-response write operations':Yes -\> "write_raw" (optional with option to repeat multiple times) -\> "write_line" (optional with option to repeat multiple times) -\> "write_text" (optional with option to repeat multiple times) -\> "end_request"

- 'perform pre-response write operations': No -\> "end_request"

PHASE \#2.

- "get_response" -\> 'perform get operations': Yes/No

  - 'perform get operations': Yes -\> "set_body_charset" (optional with option to repeat multiple times) -\> "get_authentication" (optional with option to repeat multiple times) -\> "get_header_count" (optional with option to repeat multiple times) -\>"get_header_by_name" (optional with option to repeat multiple times) -\> 'peform read operations':Yes/No

  - 'perform get operations': No -\> 'peform read operations':Yes/No

- 'peform read operations':Yes -\> "read_raw" (optional with option to repeat multiple times) -\>"read_line" (optional with option to repeat multiple times) -\> "read_text" (optional with option to repeat multiple times) -\> end_response

- 'peform read operations':No -\> end_response
