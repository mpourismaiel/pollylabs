---
fragment: content
title: Applied Polyhedral Compilation Tutorial at HiPEAC 2016
---


Sven Verdoolaege and Tobias Grosser gave today the <a
href="https://www.hipeac.net/events/activities/7331/polyhedral/">Applied
Polyhedral Compilation tutorial</a> at HiPEAC 2016.


<!--more-->
<pre>
Polyhedral compilation is widely used in high-level synthesis tools and in
production compilers such as gcc, LLVM and IBM/XL and is still being actively
developed by several research groups across the globe, resulting in highly
attended IMPACT workshops and a recent polyhedral school. It is based on the
polyhedral model, a powerful abstraction for analyzing and transforming (parts
of) programs that are "sufficiently regular". The key feature of this model is
that it is instance based, allowing for a representation and treatment of
individual dynamic executions of a statement inside a loop nest and/or
individual array elements.

In this tutorial, we explain how to apply the basic concepts of polyhedral
compilation in different setting. The tutorial consists of two parts, one
dealing with the use of polyhedral compilation inside LLVM/Polly, giving a
detailed view into the core of Polly and enabling the attendees to write their
own Polly based analysis and optimizations, and the other dealing with
applications of set cardinality, focusing on problem modeling. In particular,
we will address the following topics:

 - Recapitulation of the basic polyhedral concepts
 - Overview of LLVM's classical loop optimizers and vectorizers
 - Identification/analysis of compute kernels, memory access patterns,
   and data dependences in Polly
 - Code transformations in Polly
 - Overview of the basic counting operations
 - How to model problems involving counting and related operations

This tutorial continues from the Polyhedral Compilation without Polyhedra
tutorial presented at HiPEAC 2015. Some of the material will be drawn from the
first half of a lecture presented at the polyhedral school.
</pre>
