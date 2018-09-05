---
fragment: content
date: 2016-01-16
title: PPCG 0.05 has been released
---


<a href="http://ppcg.gforge.inria.fr/">PPCG 0.05</a>
was released containing various changes:

 * **Fix live-out computation**

   Due to a bug, the live-out computation would consider all elements
   written by a write to have been killed as soon as one of those elements
   had effectively been killed.  This could in rare cases result
   in some statement instances mistakenly getting removed during
   dead code elimination.

 * **Optionally compute schedule for C target**

   The original support for the C target only added the basic
   infrastructure and did not even allow the input code to be
   rescheduled.  Now, this backend will also (optionally)
   reschedule the code, but support for this target is still
   fairly basic.

 * **Create single kernel for non-permutable subtree**

   If some parts of the code that is mapped to the device
   do not have any parallelism, then a kernel would be launched
   for each instance of that part of the code, even if that would
   result in loop on the host that only launches such kernels.
   Now, a single kernel is invoked for the entire non-parallel part.
