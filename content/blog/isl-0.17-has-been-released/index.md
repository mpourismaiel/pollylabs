---
fragment: content
title: isl 0.17 has been released
---


<a href="http://isl.gforge.inria.fr/">isl 0.17</a> was released containing various improvements:

 * **Optionally combine SCCs incrementally in the scheduler**

   Within each component of the dependence graph, the isl scheduler
   tries to schedule all statements together by default.
   By turning *off* the ```schedule-whole-component``` option,
   the isl scheduler will first consider each strongly connected
   component separately and then incrementally combine them.
   This should reduce the scheduling time and allows for more
   finegrained control over which SCCs should be combined.
   In particular, the coincidence maximization below depends
   on the incremental scheduler.

 * **Optionally maximize coincidence in the scheduler**

   If the ```schedule-whole-component``` option is turned *off*,
   then turning on the ```schedule-maximize-coincidence``` option
   will make isl refuse to combine SCCs if this reduces the number of
   coincident band members in the schedules for any of the SCCs.

 * **Optionally avoid loop coalescing in the scheduler**

   By default, isl will now try and prevent or recover from schedules
   that represent loop coalescing.
   Loop coalescing is undesirable because it results in a skewed view
   of the schedule dimension, leading to single instance band members,
   and because the large coefficients can cause difficulties in later
   step, including complicated generated code.

   For example, a schedule of the form

   ~~~
   domain: "{ C[i0, i1] : 2 <= i0 <= 3999 and 0 <= i1 < i0 }"
   child:
     schedule: "[{ C[i0, i1] -> [(3998i0 + i1)] }]"
     child:
       schedule: "[{ C[i0, i1] -> [(i0)] }]"
       permutable: 1
       coincident: [ 1 ]
   ~~~
   will be rejected in favor of the schedule

   ~~~
   domain: "{ C[i0, i1] : 2 <= i0 <= 3999 and 0 <= i1 < i0 }"
   child:
     schedule: "[{ C[i0, i1] -> [(i0)] }]"
     child:
       schedule: "[{ C[i0, i1] -> [(i1)] }]"
   ~~~

 * **Fix handling of nested integer divisions**

   Nested integer divisions were not handled correctly in some
   operations, leading to incorrectly generated code in corner cases.

 * **Optionally detect min/max expressions during AST generation**

   An ```isl_pw_aff``` with several pieces often represents a
   minimum of maximum expression.  Detect some of these cases inside
   ```isl_ast_build_expr_from_pw_aff``` and construct an explicit minimum
   or maximum expression on success.

   For example, construct ```max(0, M)``` instead of ```M <= 0 ? 0 : M```.

 * **Minor AST generator improvements**

   In particular, reduce the number of pieces during the combination
   of pairs of piecewise affine expressions and move the most
   complicated piece last such that it does not need to be AST generated.
   When combining a pair of expressions of m and n pieces,
   the original implementation could produce a result with
   2 * (m + 1) * (n + 1) pieces.  The new implementation creates
   a result with at most m + n pieces.

 * **Simplify stride constraints**

   ```isl_map_gist``` would only simplify away stride constraints
   if they could be removed completely and if they happened
   to be formulated in exactly the same way in the context.
   Stride constraints are now simplified more generally.
   For example,

   ```
   [n] -> { [x] : x = n && x mod 32 = 0 } % [n] -> { [x] : x mod 32 = 0 }
   ```

   now produces ```[n] -> { [x = n] }```, and

   ```
   { [x] : x mod 6 = 0 } % { [x] : x mod 3 = 0 }
   ```

   now produces ```{ [x] : x mod 2 = 0 }```.

 * **Improve support for expansions in schedule trees**

   These changes are needed to support statement grouping in
   <a href="http://ppcg.gforge.inria.fr/">PPCG</a>.


<br>

<div class="panel panel-warning">
  <div class="panel-heading">
    <h3 class="panel-title">isl 0.17.1 bug fix release</h3>
  </div>
  <div class="panel-body">
isl 0.17.1 was released fixing a minor bug that was found right after the
release.
  </div>
</div>
