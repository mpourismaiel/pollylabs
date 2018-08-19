---
fragment: content
title:  AST generation paper presented at PLDI 2016
---


<a href="http://www.grosser.es">Tobias Grosser</a> presented <a
href="http://www.grosser.es/#pub-polyhedral-AST-generation">Polyhedral AST
generation is more than scanning polyhedra</a> at PLDI 2016, which was held
this year on June 13-17 on the beautiful shores of Santa Barbara.

In the <a href="toplas.acm.org/">ACM TOPLAS</a> paper presented, we provide detailed insights into
state-of-the-art polyhedral AST generation techniques used at the heart of <a
href="http://polly.llvm.org">Polly</a>, <a
href="https://gcc.gnu.org/wiki/Graphite">GCC/Graphite</a>, <a
href="https://www.openhub.net/p/ppcg">PPCG</a>, <a
href="http://mcl.csa.iisc.ernet.in/polymage.html">PolyMage</a>, as well as
others, and discuss concepts -- outside of classical AST generation -- used to
enable GPU tiling techniques such as <a
href="http://dl.acm.org/authorize?N91181">hybrid-hexagonal tiling</a>.

### Abstract
<p>
Abstract mathematical representations such as integer polyhedra have
shown to be useful to precisely analyze computational kernels and to
express complex loop transformations. Such transformations rely on
Abstract Syntax Tree (AST) generators to convert the mathematical
representation back to an imperative program. Such generic AST
generators avoid the need to resort to transformation-specific code
generators, which may be very costly or technically difficult to develop as
transformations become more complex. Existing AST generators have
proven their effectiveness, but they hit limitations in more
complex scenarios. Specifically, (1) they do not support or may fail
to generate control flow for complex transformations using piecewise
schedules or mappings involving modulo arithmetic; (2) they offer
limited support for the specialization of the generated code exposing
compact, straightline, vectorizable kernels with high arithmetic intensity
necessary to exploit the peak performance of modern hardware; (3)
they offer no support for memory layout transformations; (4) they
provide insufficient control over the AST generation strategy,
preventing their application to complex domain-specific
optimizations.</p>

<p>
We present a new AST generation approach that extends classical
polyhedral scanning to the full generality of Presburger arithmetic,
including existentially quantified variables and piecewise
schedules, and introduce new optimizations for the
detection of components and shifted strides. Not limiting ourselves
to control flow generation, we expose functionality to generate AST
expressions from arbitrary piecewise quasi-affine expressions which
enables the use of our AST generator for data-layout
transformations. We complement this with support for specialization
by polyhedral unrolling, user-directed versioning, and specialization
of AST expressions according to the location they are generated at,
and complete this work with fine-grained user control over the AST
generation strategies used.  Using this generalized idea of AST
generation, we present how to implement complex domain-specific
transformations without the need to write specialized code
generators, but instead relying on a generic AST generator
parametrized to a specific problem domain.
</p>

### Video

<iframe width="560" height="315"
src="https://www.youtube.com/embed/h4XB7HBskJM" frameborder="0"
allowfullscreen></iframe>

## Slides

<a href="/slides/polyhedral-AST-generation.pdf">PLDI Slides</a>

## Online Playground

Try it out in the <a href="http://playground.pollylabs.org/">Polly Labs playground</a>.
