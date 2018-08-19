---
fragment: content
title: pet 0.10 has been released
---


<a href="http://pet.gforge.inria.fr/">pet 0.10</a> was released containing
a couple of changes:

 * **Detect and report unbalanced pairs of scop/endscop pragmas**

   For example, in the following code fragment,
   the ```#pragma scop``` appears inside the ```for```-loop,
   while the ```#pragma endscop``` appears outside of the loop.
   Previous versions would silently ignore such regions.
   Now, a warning is produced.

   ~~~
   void foo(int a[10])
   {
           for (int i = 0; i < 10; ++i)
   #pragma scop
                   a[i] = i;
   #pragma endscop
   }
   ~~~

 * **Take into account assumptions during extraction**

   Consider the program fragment below.

   ~~~
   int f(int k)
   {
           int a;
   #pragma scop
           __builtin_assume(k >= 0);
           a = k % 16;
   #pragma endscop
           return a;
   }
   ~~~

   Without the ```__builtin_assume```, pet would have to assume
   that ```k``` may be either positive or negative, resulting
   in a piecewise expression for ```a```.
   The extra assumption allows the expression to be simplified.
   Before, pet would only perform such simplifications at the very end,
   now they are also performed during the extraction process,
   potentially speeding up this extraction process in the presence
   of multiple modulo or integer division expressions.
