---
fragment: content
title: Live-Range Reordering presentation at IMPACT 2016
---


Sven Verdoolaege presented the
<a href="https://lirias.kuleuven.be/handle/123456789/519489">
Live-Range Reordering</a> paper
at <a href="http://impact.gforge.inria.fr/impact2016/">IMPACT 2016</a>.

*Abstract*:
<pre>
False dependences are caused by the reuse of memory to store different
data.  These false dependences severely constrain the schedule of
statement instances, effectively serializing successive accesses to
the same memory location.  Several array expansion techniques have
been proposed to eliminate some or all of these false dependences,
enabling more reorderings of statement instances during loop nest
transformations. However, array expansion is only relevant when
complemented with a storage mapping optimization step, typically
taking advantage of the fixed schedule set in earlier phases of the
compilation, folding successive values into a compact set of contracted
arrays. Furthermore, array expansion can result in memory footprint and
locality damages that may not be recoverable through storage mapping
optimization when intermediate transformation steps have abused the
freedom offered by the removal of false dependences. Array expansion
and storage mapping optimization are also complex procedures not
found in most compilers, and the latter is moreover performed using
suboptimal heuristics (particularly in the multi-array case). Finally,
array expansion may not remove all false dependences when considering
data-dependent control and access patterns. For all these reasons,
it is desirable to explore alternatives to array expansion as a
means to avoid the spurious serialization effect of false dependences.
This serialization is unnecessary in general, as semantics preservation
in presence of memory reuse only requires the absence of interference
among live-ranges, an unordered constraint compatible with the their
commutation. We present a technique to deal with memory reuse without
serializing successive uses of memory, but also without increasing memory
requirements or preventing important loop transformations such as loop
distribution. The technique is generic, fine-grained (instancewise)
and extends two recently proposed, more restrictive approaches. It has
been systematically tested in PPCG and shown to be essential to the
parallelizing compilation of a variety of loop nests, including large
pencil programs with many scalar variables.
</pre>
