---
fragment: content
title: Five presentations at EuroLLVM and CC
---


At this years <a href="http://llvm.org/devmtg/2016-03/">Euro LLVM</a> and <a
href="http://cc2016.eew.technion.ac.il/">CC</a> conference in Barcelona, a
variety of Polly Labs related presentations have been given.

### 1. Analysing and Optimizing your Loops with Polly (Tutorial)

<pre>
The Polly Loop Optimizer is a framework for the analysis and optimization of
(possibly imperfectly) nested loops. It provides various transformations such
as loop fusion, loop distribution, loop tiling as well as outer loop
vectorization. In this tutorial we introduce the audience to the Polly loop
optimizer and show how Polly can be used to analyze and improve the performance
of their code. We start off with basic questions such as "Did Polly understand
my loops?", "What information did Polly gather?", "How does the optimized loop
nest look like?", "Can I provide more information to enable better
optimizations?", and "How can I utilize Polly's analysis for other purposes?".
Starting from these foundations we continue with a deeper look in more advanced
uses of Polly: This includes the analysis and optimization of some larger
benchmarks, the programming interfaces to Polly as well as the connection
between Polly and other LLVM-IR passes. At the end of this tutorial we expect
the audience to not only be able to optimize their codes with Polly, but also
to have a first understanding of how to use it as a framework to implement
their own loop transformations.
</pre>

Presenters: Tobias Grosser and Johannes Doerfert

**Feedback:**

<blockquote>
<p>Tobias Grosser (the lead developer of Polly) and Johannes Doerfert gave a
fantastic tutorial on Polly. ‘Polyhedral loop modelling’ is an intimidating
term when you first encounter it, but their explanation was clear and
effective. They also showed how to derive simple loop optimisations like
loop interchange in this system and the more sophisticated optimisations
they’ve developed on top.</p>

<a href="http://www.wilfred.me.uk/blog/2016/03/22/llvm-developer-meeting-2016/">
http://www.wilfred.me.uk/blog/2016/03/22/llvm-developer-meeting-2016/
</a>
</blockquote>

### 2. Polly - Loop Optimization Infrastructure (Birth of a Feather)

<pre>
The Polly Loop Optimization infrastructure has seen active development
throughout 2015 with contributions from a larger group of developers located at
various places around the globe. With three successful Polly sessions at the US
developers meeting and larger interest at the recent HiPEAC conference in Prag,
we expect various Polly developers to be able to attend EuroLLVM. To facilitate
in-persona collaboration between the core developers and to reach out to the
wider loop optimization community, we propose a BoF session on Polly and the
LLVM loop optimization infrastructure. Current hot topics are the usability of
Polly in an '-O3' compiler pass sequence, profile driven optimizations as well
as the definition of future development milestones. The Polly developers
community will present ideas on these topics, but very much invites input from
interested attendees.
</pre>

Presenters: Tobias Grosser, Johannes Doerfert, Zino Benaissa

### 3. Molly: Parallelizing for Distributed Memory using LLVM (Presentation)

<pre>
Motivated by modern day physics which in addition to experiments also tries to
verify and deduce laws of nature by simulating the state-of-the-art physical
models using large computers, we explore means of accelerating such simulations
by improving the simulation programs they run. The primary focus is Lattice
Quantum Chromodynamics (QCD), a branch of quantum field theory, running on IBM
newest supercomputer, the Blue Gene/Q.

Molly is an LLVM compiler extension, complementary to Polly, which optimizes
the distribution of data and work between the nodes of a cluster machine such
as Blue Gene/Q. Molly represents arrays using integer polyhedra and uses
another already existing compiler extension Polly which represents statements
and loops using polyhedra. When Molly knows how data is distributed among the
nodes and where statements are executed, it adds code that manages the data
flow between the nodes. Molly can also permute the order of data in memory.

Molly's main task is to cluster data into sets that are sent to the same target
into the same buffer because single transfers involve a massive overhead. We
present an algorithm that minimizes the number of transfers for unparametrized
loops using anti-chains of data flows. In addition, we implement a heuristic
that takes into account how the programmer wrote the code. Asynchronous
communication primitives are inserted right after the data is available
respectively just before it is used. A runtime library implements these
primitives using MPI. Molly manages to distribute any code that is
representable in the polyhedral model, but does so best for stencils codes such
as Lattice QCD. Compiled using Molly, the Lattice QCD stencil reaches 2.5% of
the theoretical peak performance. The performance gap is mostly because all the
other optimizations are missing, such as vectorization. Future versions of
Molly may also effectively handle non-stencil codes and use make use of all the
optimizations that make the manually optimized Lattice QCD stencil fast.
</pre>

Presenter: Michael Kruse

### 4. How Polyhedral Modeling enables compilation to Heterogeneous Hardware (Presentation)

<pre>
Polly, as a polyhedral loop optimizer for LLVM, is not only a sophisticated
tool for data locality optimizations, but also has precise information about
loop behavior that can be used to automatically generate accelerator code.

In this presentation we present a set of new Polly features that have been
introduced throughout the last two years (and as part of two GSoC projects)
that enable the use of Polly in the context of compilation for heterogeneous
systems. As part of this presentation we discuss how we use Polly to derive the
precise memory footprints of compute regions for both flat arrays as well as
multi-dimensional arrays of parametric size. We then present a new, high-level
interface that allows for the automatic remapping of memory access functions to
new locations or data-layouts and show how this functionality can be used to
target software managed caches. Finally, we present our latest results in terms
of automatic PTX/CUDA code generation using Polly as a core component.
</pre>

Presenter: Tobias Grosser

### 5. Input Space Splitting for OpenCL (Technical Paper -- CC 2016)

<pre>
The performance of OpenCL programs suffers from memory and control  flow
divergence.  Therefore,  OpenCL  compilers  employ static analyses to identify
non-divergent control flow and memory accesses in order to produce faster code.
However, divergence is often input-dependent, hence can be observed for some,
but not all inputs. In these cases, vectorizing compilers have to generate slow
code because divergence can occur at run time.
In this paper, we use a polyhedral abstraction to partition the input space of
an OpenCL kernel. For each partition, divergence analysis produces more precise
results i.e., it can classify more code parts as non-divergent. Consequently,
specializing the kernel for the input space partitions allows for generating
better SIMD code because of less divergence.
We implemented our technique in an OpenCL driver for the AVX instruction set
and evaluate it on a range of OpenCL benchmarks.  We  observe  speed  ups  of
up  to 9x for  irregular  kernels  over  a state-of-the-art vectorizing OpenCL
driver.
</pre>

Presenter: Simon Moll
Authors: Simon Moll, Johannes Doerfert, Sebastian Hack
