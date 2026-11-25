## Reasons for Using Silent Mode or Response File Mode

Review this section for use cases for running the installer in silent mode or response file mode.

Table B-1 Reasons for Using Silent Mode or Response File Mode

| Mode          | Uses                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Silent        | Use silent mode to:<br>• Complete an unattended installation, which you schedule using operating system utilities such as at.<br>• Complete several similar installations on multiple systems without user interaction.<br>• Install the software on a system that does not have X Window System software installed on it.<br>The installer displays progress information on the terminal that you used to start it, but it does not display any of the installer screens. |
| Response file | Use response file mode to complete similar Oracle software installations on more than one system, providing default answers to some, but not all of the installer prompts.<br>If you do not specify information required for a particular installer screen in the response file, then the installer displays that screen. It suppresses screens for which you have provided all of the required information.                                                               |

**Parent topic:** [How Response Files Work](how-response-files-work.md)
