Patch for better fpu emulation

in /sys/src/9/mt7688;
rename fpimips.c to fpimips.c.old.
copy in the fpimips.c from this repository.

in the hostowners home directory;
make a directory and copy tos.h into it.

the included rc script shows how I run this on my system.
the idea is to bind BEFORE this tos.h into /sys/include.
you do this in the namespace in which you will compile the mt7688 kernel.
the kernel will be comiled using this modified top of stack.

Why?
The code for the floating point emulation needs some scratch space 
available to both the kernel and user space.  The easiest way to 
do that is from the Top Of Stack, which is set up by tos.h

tos.h is used by a lot of other random programs in 9front, 
so the this is expirimental.  however, this is pretty much a 
copy of how things were done in Legacy Plan 9.
