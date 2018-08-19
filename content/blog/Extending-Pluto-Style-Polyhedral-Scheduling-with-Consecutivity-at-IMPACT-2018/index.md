---
fragment: content
title: Extending Pluto-style Polyhedral Scheduling with Consecutivity presentation at IMPACT 2018
---


Sven Verdoolaege presented the
<a href="https://lirias.kuleuven.be/handle/123456789/609602">
Extending Pluto-style Polyhedral Scheduling with Consecutivity</a> paper
at <a href="http://impact.gforge.inria.fr/impact2018/">IMPACT 2018</a>.

*Abstract*:
<pre>
The Pluto scheduler is a successful polyhedral scheduler
that is used in one form or another in several research and
production compilers. The core scheduler is focused on
parallelism and temporal locality and does not directly
target spatial locality.
Such spatial locality is known to bring performance benefits and
has been considered in various forms outside and inside
polyhedral compilation.
For example, the Pluto compiler has some support for
spatial locality, but it is limited to a post-processing
step involving only loop interchange.
Consecutivity is a special case of spatial locality
that aims for stride-1 accesses, which can be useful for
constructing burst accesses and for vectorization.
Stride-1 accesses have been targeted by an approach
based on one-shot scheduling, but it is fairly
approximative and not directly transferable to
a Pluto-style scheduler.
This paper describes an approach for consecutivity
that is integrated in a Pluto-style polyhedral scheduler,
as implemented in isl.
Both intra-statement and inter-statement consecutivity
is considered, taking into account multiple references
per statement and the integration into a component based
incremental scheduler.
</pre>
