#

The syntax that is in the image is in Backus–Naur form for the et_datatype_spec clause. The syntax is as follows:

et_datatype_spec ::=
{
\[UNSIGNED\] INTEGER \[EXTERNAL\] \[(len)\] \[delim_spec\]                          
\|{ DECIMAL \| ZONED } \[EXTERNAL\] \[(len)\] \[delim_spec\] (precision \[ , scale\])
\|ORACLE_DATE                                                    
\|ORACLE_NUMBER \[COUNTED\]                                      
\|FLOAT \[EXTERNAL\] \[(len)\] \[delim_spec\]
\|DOUBLE
\|BINARY_FLOAT \[EXTERNAL\] \[(len)\] \[delim_spec\]
\|BINARY_DOUBLE                          
\|RAW \[(len)\]                                                
\|CHAR \[(len)\] \[delim_spec\] \[trim_spec\] \[date_format_spec\]      
\|{ VARCHAR \| VARRAW \| VARCHARC \| VARRAWC } (\[length_of_length ,\] max_len)
}
