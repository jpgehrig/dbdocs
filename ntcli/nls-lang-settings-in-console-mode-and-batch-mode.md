## NLS_LANG Settings in Console Mode and Batch Mode

Before you can use Oracle utilities such as SQL\*Plus, SQL Loader, Import, and Export from the Command Prompt window, set the character set field of the `NLS_LANG` parameter to a value different than the one set in Registry.

This is required because programs running in console mode use, with a few exceptions, a different code page (character set) from programs running in GUI mode. The default Oracle home `NLS_LANG` parameter in the Registry is always set to the appropriate GUI code page. If you do not set the `NLS_LANG` parameter for the console mode session correctly, incorrect character conversion can corrupt error messages and data.

For Japanese, Korean, Simplified Chinese, Traditional Chinese, Thai, and Vietnamese, the console (OEM) code page is identical to the GUI (ANSI) code page. In this case, you are not required to set the `NLS_LANG` parameter. For other languages, set the correct character set value of `NLS_LANG` by issuing a `SET NLS_LANG `command in the same Command Prompt window in which you want to start the affected utility.

Similarly, in batch mode, set the correct character set value of `NLS_LANG` by inserting a `SET NLS_LANG` command at the start of the batch procedure, according to the character set of the files to be processed in the procedure.

To find the current console code page, issue the `CHCP` command in the Command Prompt window. Use the reported code page number to look up the corresponding Oracle character set name in the following table.

The following table lists the Oracle character sets that correspond to the console mode code pages.

Table D-1 Oracle Character Sets for Console Mode (OEM) Code Pages

| OEM Code Page                     | Oracle Character Set for Console Mode |
|:----------------------------------|:--------------------------------------|
| 437 (US)                          | US8PC437                              |
| 737 (Greek)                       | EL8PC737                              |
| 775 (Baltic)                      | BLT8PC775                             |
| 850 (Multilingual Latin I)        | WE8PC850                              |
| 852 (Latin II)                    | EE8PC852                              |
| 855 (Cyrillic)                    | RU8PC855                              |
| 857 (Turkish)                     | TR8PC857                              |
| 858 (Multilingual Latin I + Euro) | WE8PC858                              |
| 866 (Russian)                     | RU8PC866                              |
| 874 (Thai)                        | TH8TISASCII                           |
| 932 (Japanese Shift-JIS)          | JA16SJISTILDE                         |
| 936 (Simplified Chinese GBK)      | ZHS16GBK                              |
| 949 (Korean)                      | KO16MSWIN949                          |
| 950 (Traditional Chinese Big5)    | ZHT16MSWIN950                         |
| 1258 (Vietnam)                    | VN8MSWIN1258                          |

**Parent topic:** [Configuring Oracle Components to Run in Different Languages](configuring-oracle-components-to-run-in-different-languages.md)
