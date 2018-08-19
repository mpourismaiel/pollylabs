---
fragment: content
title: isl 0.18 has been released
---


<a href="http://isl.gforge.inria.fr/">isl 0.18</a> was released containing various improvements:

 * **Improve elimination of redundant existentially quantified variables**

   In particular, finally implement the
   <a href="http://dx.doi.org/10.1145/135226.135233">Omega test</a> in isl.
   A more powerful (and more expensive) version of the Omega test
   was supposed to have been implemented already, but it missed some cases.
   Those cases are now also handled.
   For example, the set description
   ```{ [m, w] : exists a : w - 2m - 5 <= 3a <= m - 2w }```
   is now simplified to ```{ [m, w] : w <= 1 + m }```.

 * **Improve coalescing**

   In particular, the following set descriptions are now also coalesced

   ~~~
   { [a, b] : 0 <= a <= 2 and b >= 0 and
	   ((0 < b <= 13) or (2*floor((a + b)/2) >= -5 + a + 2b)) }
   { [a] : (2 <= a <= 5) or (a mod 2 = 1 and 1 <= a <= 5) }
   { [y, x] : (x - y) mod 3 = 2 and 2 <= y <= 200 and 0 <= x <= 2; [1, 0] }
   { [x, y] : (x - y) mod 3 = 2 and 2 <= y <= 200 and 0 <= x <= 2; [0, 1] }
   { [1, y] : -1 <= y <= 1; [x, -x] : 0 <= x <= 1 }
   { [1, y] : 0 <= y <= 1; [x, -x] : 0 <= x <= 1 }
   { [x, y] : 0 <= x <= 10 and x - 4*floor(x/4) <= 1 and y <= 0;
     [x, y] : 0 <= x <= 10 and x - 4*floor(x/4) > 1 and y <= 0;
     [x, y] : 0 <= x <= 10 and x - 5*floor(x/5) <= 1 and 0 < y;
     [x, y] : 0 <= x <= 10 and x - 5*floor(x/5) > 1 and 0 < y }
   { [x, 0] : 0 <= x <= 10 and x mod 2 = 0;
     [x, 0] : 0 <= x <= 10 and x mod 2 = 1;
     [x, y] : 0 <= x <= 10 and 1 <= y <= 10 }
   ~~~

 * **Improve parametric integer programming**

   Based on analysis of a test case reported by Wenlei Bao,
   a major cause of the long run-time turned out to be
   the symmetry detection performed internally.  The detected
   symmetry is exploited by replacing several upper bounds
   with a single additional parameter.  This helps to speed up
   lexicographic optimization of some inputs with lots of symmetry,
   but causes a significant slow-down on this particular input
   because the parameters that appear in the replaced constraints
   may also appear in other constraints and through the replacement,
   the connection is lost.  The symmetry detection is now only
   applied in cases where this problem does not occur.

   A further analysis showed that quite some time was spent
   in exploring parts of the domain where the optimum is undefined.
   In a pure lexicographic optimization operation, the user is
   not interested in this part of the domain.
   The procedure was changed to start from the actual domain
   of the input rather than the corresponding universe
   such that the complement no longer needs to be explored at all.
   A possible down-side is that this actual domain may involve
   existentially quantified variables, which increases the dimension
   of the context and which may also appear in the final result.
   Special care therefore needs to be taking for the case where
   lexicographic optimization is being used for its side-effect
   of eliminating existentially quantified variables.

   The upshot is that for the input

   ~~~
   { S_2[i, k, j] -> [o0, o1, o2, o3] : exists (e0 = floor((o1)/8):
       8e0 = o1 and k <= 255 and o0 <= 255 and o2 <= 255 and
       o3 <= 255 - j and 7o3 >= 255 - j and 7o3 <= 7 - i and
       240o3 <= 239 + o0 and 247o3 <= 247 + k - j and
       247o3 <= 247 + k - o1 and 247o3 <= 247 + i and
       248o3 >= 248 - o1 and 248o3 <= o2 and 254o3 >= i - o0 + o1
       and 254o3 >= -o0 + o1 and 255o3 >= -i + o0 - o1 and
       1792o3 >= -63736 + 257o1) }
   ~~~

   the computation time went down from

   ~~~
   real    6m36.786s
   user    6m36.032s
   sys     0m0.128s
   ~~~

   to

   ~~~
   real    0m0.040s
   user    0m0.032s
   sys     0m0.000s
   ~~~

 * **preserve ```isolate``` option in ```isl_schedule_node_band_split```**

   This is needed to simplify the implementation of full/partial tile
   separation for hybrid tiling in
   <a href="http://ppcg.gforge.inria.fr/">PPCG</a>.

 * **Print AST nodes in YAML format**

 * **Minor improvements to Python bindings**
