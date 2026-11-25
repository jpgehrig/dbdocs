# Description of the illustration bradv007.eps

This illustration depicts block media recovery. Block 13 is shown on a line with its associated archived logs. The line represents the redo stream. At the beginning of the line, Block 13 is restored in data file 4; the associated archived log is Log 100. At the next stage, Log 120 is missing redo for block 13. At the next stage, Log 140, block 13 is newed. Finally, Log 160 has the last change for block 13. The recovery is explained in the following text.
