---
fragment: content
title: barvinok 0.41 has been released
---


<a href="http://barvinok.gforge.inria.fr/">barvinok 0.41</a>
was released containing only a single minor change:

 * **Remove support applying ```codegen``` to a set in ```iscc```**

    The codegen operation prints an AST generated from a schedule,
    given either as a schedule tree or a (union) map.
    As a convenience, applying codegen to a set would result
    in codegen being applied to the identity mapping on the set.
    This seems to be causing confusion about the nature
    of the codegen operation.  Drop the magic such that users
    are aware that a schedule is needed to perform AST generation.
    They can still explicitly call the "identity" operation on a set
    if they really want the old behavior.
