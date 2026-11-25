# Description of the illustration cncpt282.eps

This graphic shows the redo log buffer as a pile of slabs. Slabs 1-3, 6, and 8-9 are darkly shaded, which means "Change in Data File." Slabs 4-5, 7, 10-11 are not shaded, which means "Change Not in Data File." Slabs 12-14 are lightly shaded, which means "Free Buffer." An arrow marks the point right below slab 3 as "Checkpoint Position." An arrow marks the position right above the top free buffer as "End of Redo Thread."
