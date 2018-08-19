---
fragment: content
title: pet 0.09 has been released
---


<a href="http://pet.gforge.inria.fr/">pet 0.09</a> was released containing
various changes:

 * **Push affine conditions into index expressions**

   If the code contains an expression of the form

   ```
   c ? A[f] : A[g]
   ```

   with c an affine condition, then replace it by

   ```
   A[c ? f : g]
   ```

   This reduces the number of accesses and, more importantly,
   includes the information of when the access is performed
   in the index expression.  This allows dependence analysis
   to take into account this information, reducing the risk of
   introducing spurious dependences.


 * **Properly support undeclared loop iterators**

   When the loop iterator of a ```for``` loop is not declared inside
   the ```for``` loop itself, the value of this loop iterator persists
   after the execution of the loop and could in principle be used
   by subsequent statements.  Introduce assignments to the corresponding
   variable that ensure the variable contains the correct value
   after the execution of the loop.
