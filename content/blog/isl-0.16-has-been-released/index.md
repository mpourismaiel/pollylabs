---
fragment: content
title: isl 0.16 has been released
---


<a href="http://isl.gforge.inria.fr/">isl 0.16</a> was released containing various improvements:

 * **Add 32 bit integer optimization for IMath**

   Until isl 0.15 the IMath backend, which serves as MIT licensed alternative
   to the default libgmp backend, was not very well optimized and its result
   could result in isl being 2-4x slower. Michael Kruse contributed a new
   small-integer-optimization to isl which improved the performance of the
   IMath backend to be now around 30% faster than libgmp.

 * **Improved AST generation quality**

   Various smaller changes result in generally improved AST generation quality.

 * **Add ```isl_union_flow_get_full_may_dependence``` and
   ```isl_union_flow_get_full_must_dependence```**

   These functions include the accessed data elements that are
   responsible for the dependence in their results.

 * **Improvements to Python bindings**

   The isl provided python bindings have been extended to support the full set
   of polyhedral compilation examples that is discussed in our new
   <a href="https://lirias.kuleuven.be/handle/123456789/523109">Presburger Formulas and Polyhedral Compilation</a> tutorial.

 * **Improved printing of isl sets and maps**

   Until isl 0.15 the constraints in an isl set and map have been printed
   in the (rather random) order they have been added to the data structure.
   isl now makes an effort to print constraints in a human readable way. This
   results in both shorter constraints, but also more predictable output
   in case implementation details change.

   Before:

   ```
   { S[i0, i1] : i0 <= 97 and i0 >= 0 and i1 <= 99 and i1 >= 1 }
   ```

   After:

   ```
   { S[i0, i1] : 0 <= i0 <= 97 and 0 < i1 <= 99 }
   ```


<br>

Together with isl, we also released <a href="http://ppcg.gforge.inria.fr/">PPCG
0.05</a>, <a href="http://pet.gforge.inria.fr/">pet 0.08</a>, and <a href="http://barvinok.gforge.inria.fr/">barvinok 0.39</a>.

<br>

<div class="panel panel-warning">
  <div class="panel-heading">
    <h3 class="panel-title">isl 0.16.1 bug fix release</h3>
  </div>
  <div class="panel-body">
isl 0.16.1 was released fixing a minor bug that was found right after the
release.
  </div>
</div>
