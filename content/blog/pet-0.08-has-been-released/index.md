---
fragment: content
date: 2016-01-15
title: pet 0.08 has been released
---


<a href="http://pet.gforge.inria.fr/">pet 0.08</a> was released containing
various changes:

 * **Initialize compiler builtins**

   Michael Kruse contributed a patch to initialize builtins.
   Without this initialization, builtins are treated as implicitly
   defined functions and are therefore assumed to have return type
   ```int```, resulting in compiler warnings or even errors when
   those builtins are used.

 * **Rename ```pet_scop``` accessors**

   The original names where too focused on how the accessors were
   implemented.

 * **Support variable renaming**

   This allows the input to have several locally declared variables
   with the same name.

 * **Support inlining of outermost call expressions**

 * **Add preliminary Python bindings**

   The python bindings are needed for some of the examples in the
   <a href="https://lirias.kuleuven.be/handle/123456789/523109">
   Presburger Formulas and Polyhedral Compilation</a> tutorial.
