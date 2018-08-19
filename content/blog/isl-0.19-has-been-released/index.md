---
fragment: content
title: isl 0.19 has been released
---


<a href="http://isl.gforge.inria.fr/">isl 0.19</a>
was released containing various improvements:

 * **Improve coalescing**

   In particular, the following set descriptions are now also coalesced

   ~~~
   { [a, b, c] : (b = -1 + a and 0 < a <= 3 and
                          9*floor((-4a + 2c)/9) <= -3 - 4a + 2c) or
                  (a = 4 and b = 3 and 9*floor((-16 + 2c)/9) <= -19 + 2c) };
   { [x, y] : 2y = -x and x <= 0 or x <= -1 and 2y <= -x - 1 and 2y >= x - 1 };
   { [a] : (a <= 0 and 3*floor((a)/3) = a) or (a < 0 and 3*floor((a)/3) < a) };
   { [a, b] : a <= 1024 and b >= 0 and
          ((-31 - a + b <= 32*floor((-1 - a)/32) <= -33 + b and
            32*floor((-1 - a)/32) <= -16 + b + 16*floor((-1 - a)/16))
          or (2 <= a <= 15 and b < a)) };
   { [a] : a > 0 and ((16*floor((a)/16) < a and
                  32*floor((a)/32) < a) or a <= 15) };
   { [a, b, c, d] : (-a + d) mod 64 = 0 and a <= 8 and b <= 1 and
                  10 - a <= c <= 3 and d >= 5 and 9 - 64b <= d <= 70;
     [a, b = 1, c, d] : (-a + d) mod 64 = 0 and a <= 8 and c >= 4 and
                  10 - a <= c <= 5 and 5 <= d <= 73 - c };
   [n, m] -> { S_0[i] : (-n + i) mod 3 = 0 and m >= 3 + n and
                      i >= n and 3*floor((2 + n + 2m)/3) <= n + 3m - i;
               S_0[n] : n <= m <= 2 + n };
   { [a, b] : exists (e0: 0 <= a <= 1 and b >= 0 and
                  2e0 >= -5 + a + 2b and 2e0 >= -1 + a + b and
                  2e0 <= a + b);
      [a, b] : exists (e0: 0 <= a <= 1 and 2e0 >= -5 + a + 2b and
                  2e0 >= -1 - a + b and 2e0 <= -a + b and
                  2e0 < -a + 2b) };
   { [i, j, i - 8j] : 8 <= i <= 63 and -7 + i <= 8j <= i;
     [i, 0, i] : 0 <= i <= 7 };
   { [a, b] : a >= 0 and 0 <= b <= 1 - a; [1, 1] };
   { [a, b] : a, b >= 0 and a + 2b <= 2; [1, 1] };
   ~~~

 * **Improve parametric integer programming**

   If a tableau used for parametric integer programming contains
   a purely parametric row with an indeterminate sign, then this
   means that a solution only exists in the part of the context
   where this constraint holds.  Such constraints are now
   transferred to the context first such that they can be used
   to more accurately determine the possible signs of other rows and
   to possible avoid further splits.

   In particular, calling ```isl_set_dim_max``` on the set
   ~~~
   [P, N] -> { [a] : a < N and a >= 0 and N > P and a <= P and
		     N > 0 and P >= 0 }
   ~~~
   now results in an affine expression defined over a single part
   of the domain.

 * **Try harder to avoid large coefficients in scheduler**

    For the Pluto-like scheduler,
    the main cause of large coefficients was loop coalescing and
    this was already resolved in isl 0.17.  For the Feautrier scheduler,
    which is used as a backup for the Pluto-like scheduler, loop coalescing
    was also handled, but for this scheduler, loop coalescing is not
    the only main source of large coefficients.  In particular, if the solution
    to the LP problem constructed by the Feautrier scheduler is not integral,
    then the numerators with respect to a common denominator are used
    as schedule coefficients.  These numerators can be arbitrarily large
    even if the rational values themselves are small.  The solution
    is to continue the search until an integral solution is found.
    Second, the Feautrier scheduler tries to carry as many dependences
    as possible (as instructed), which tends to result in schedules
    with coefficients proportional to the number of statements.
    This second problem is largely resolved by first trying
    to only carry self-dependences.  This second change also removes
    some spurious shifts.

 * **Handle coscheduled must-sources in dependence analysis**

    The behavior in case of coscheduled must-sources was undefined.
    Define the behavior to kill all earlier sources, but not
    any coscheduled may-sources or must-sources.
    Also, a dependence derived from a must-source that is coscheduled
    with any other source is never considered a must-dependence.

 * **Support explicit kills in dependence analysis**

    In fact, make kills the primary interface, with must-sources
    considered to be both may-sources and kills, since the effect
    of kills is actually easier to explain than that of must-sources.

 * **Drop deprecated ```isl_int```, band forests and additional functions**
