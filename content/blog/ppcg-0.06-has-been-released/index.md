---
fragment: content
title: PPCG 0.06 has been released
---


<a href="http://ppcg.gforge.inria.fr/">PPCG 0.06</a>
was released containing various changes:

 * **Use PPCG specific macro names in generated code**

   The names for macros inside isl AST expression now have a ```ppcg_```
   prefix to avoid conflicts with other symbols.

 * **Complete transition to schedule trees**

   In particular, the last remaining use of nested AST generation
   has been removed.  AST expressions for affine expressions are now
   also built within the context where they will appear, allowing
   them to exploit this context for simplification purposes.

 * **Maximize coincidence by default**

   In particular, turn on ```--isl-schedule-maximize-coincidence```
   by default.

 * **Map arrays with constant index expressions to private memory**

   This allows some code to be mapped
   to an accelerator that could not be mapped before because of
   excessive scheduling constraints.

 * **Optionally group chains of statements**

   Statements that are executed in sequence in the input code and where
   the second completely depends on the first can now be grouped together.
   In particular, pairs of consecutive statements where the first writes
   to a scalar and the second reads from that scalar are grouped together.
   This reduces the number of statements, reducing the computation time
   of the scheduler, while not giving up too much scheduling freedom.
