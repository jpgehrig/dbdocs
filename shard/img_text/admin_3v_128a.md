# Description of the illustration admin_3v_128a.png

This illustration shows four shards (numbered 1 through 4 from left to right) surrounded by a dooted line with a callout reading “Tablespace Set tbs1”. Each of the shards contains a range of chunks, each of which contains a tablespace, which in turn contains a partition, for example:

Shard 1 contains the range of chunks 1 through 120, each of which contain tablespace tbs_1–1 through tbs_1–120 respectively, tbs_1–1 contains partition P_1, and tablespace tbs_1–120 contains partition P_120.

Shards 2, 3, and 4 each contain a range of 120 chunks, each containing a tablespace and partition with the numbering scheme: chunk n (tbs_1–n (P_n)).
