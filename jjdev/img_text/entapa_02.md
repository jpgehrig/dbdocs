# Description of the illustration entapa_02.gif

The figure illustrates the different actions performed by the garbage collector. New objects, when created, are placed in the new call space. Objects that survive iterations of garbage collection are moved from the new call space to the old call space. Objects that need to exist beyond a call are moved to the session space at the end of the call.
