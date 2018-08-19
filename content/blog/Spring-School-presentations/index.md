---
fragment: content
title: Two presentations at Spring School on Polyhedral Code Optimizations and
        Numerical Simulation
---


Sven Verdoolaege presented the lecture
<a href="https://lirias.kuleuven.be/handle/123456789/540567">
PPCG and Pencil compiler design
</a> at the
<a href="http://mathsinfohpc.sciencesconf.org/?lang=en">
Polyhedral Code Optimizations and Numerical Simulation</a>
spring school.

*Abstract*:
<pre>
This course presents an overview of the inner workings of the polyhedral
parallelizing compiler PPCG, which takes PENCIL code as input and produces
either CUDA or OpenCL code.  PENCIL is a subset of C99 with some extra
builtins and pragmas that allow the user to express additional information
that can be used by PPCG to produce better code.  Some of the most
prominent PENCIL features are described, along with their effect on PPCG.
All the major steps of PPCG are covered, with a special focus on
the choice of the core scheduling algorithm and its potential pitfalls.
</pre>

Michael Kruse presented
<a href="http://mathsinfohpc.sciencesconf.org/conference/mathsinfohpc/pages/pencilcc_practical.pdf">
Using PPCG in Practice by Means of the pencilcc Wrapper
</a>

*Abstract*:
<pre>
pencilcc is a compiler for PENCIL source code (similar to nvcc or mpicc)
that uses PPCG under the hood, but that simplifies the user experience.
PENCIL is a subset of C99 designed to facilitate automatic parallelization.
The pencilcc compiler also comes with a pencil.h header and
a runtime library called PRL.

In this session we will learn how to compile PENCIL sources using
pencilcc to OpenCL/CUDA and how to profile our code.  We will also
see the influence of PENCIL-specific annotations on the generated code
as well as the positive effect on performance of using the PRL library.
</pre>
