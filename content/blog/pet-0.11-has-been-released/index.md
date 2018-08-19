---
fragment: content
title: pet 0.11 has been released
---


<a href="http://pet.gforge.inria.fr/">pet 0.11</a> was released containing
a couple of changes:

 * **Return statements in summary functions**

    Return statements are now allowed at the end of a summary function.
    The accesses that appear in the argument of the return statement
    are treated like any other read.  Return statements in other positions
    are currently not allowed as that would require special treatment
    for turning perceived must-writes that may get short-cut by the return
    into may-writes.

    For example, the following input is now accepted.

   ~~~
   int select(int n, int a[n], int i)
   {
           return a[i];
   }

   void foo(int n, int a[n])
   {
   #pragma scop
           for (int i = 0; i + 1 < n; ++i) {
                   a[i] = select(n, a, i) + select(n, a, i + 1);
           }
   #pragma endscop
   }
   ~~~

 * **Return statements in inlined functions**

    Return statements are now allowed at the end of an inlined function.
    This enables support for calls to inlined functions in nested expressions.
    The return statement in the inlined function is simply replaced by
    a write to a freshly allocated variable.

    For example, the following input is now accepted.

   ~~~
   inline int select(int n, int a[n], int i)
   {
           return a[i];
   }

   void foo(int n, int a[n])
   {
   #pragma scop
           for (int i = 0; i + 1 < n; ++i) {
                   a[i] = select(n, a, i) + select(n, a, i + 1);
           }
   #pragma endscop
   }
   ~~~
