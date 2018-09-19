+++
fragment = "content"
_pdf = "zinenko-2018-Modeling-Conflicting-Demands-of-Parallelism-And-Temporal-Spatial-Locality-in-Affine-Scheduling.pdf"
acmid = "3179507"
address = "New York, NY, USA"
author = "Zinenko, Oleksandr and Verdoolaege, Sven and Reddy, Chandan and Shirako, Jun and Grosser, Tobias and Sarkar, Vivek and Cohen, Albert"
booktitle = "Proceedings of the 27th International Conference on Compiler Construction"
doi = "10.1145/3178372.3179507"
isbn = "978-1-4503-5644-2"
keywords = "Compiler Optimizations, Polyhedral Model"
location = "Vienna, Austria"
numpages = "11"
pages = "3--13"
publisher = "ACM"
series = "CC 2018"
title = "Modeling the Conflicting Demands of Parallelism and Temporal/Spatial Locality in Affine Scheduling"
_url = "http://doi.acm.org/10.1145/3178372.3179507"
year = "2018"
+++

The construction of effective loop nest optimizers andparallelizers remains challenging despite decades of work in the area. Due tothe increasing diversity of loop-intensive applications and to the complexmemory/computation hierarchies in modern processors, optimization heuristicsare pulled towards conflicting goals, highlighting the lack of a systematicapproach to optimizing locality and parallelism. Acknowledging theseconflicting demands on loop nest optimization, we propose an algorithmictemplate capable of modeling the multi-level parallelism and thetemporal/spatial locality of multiprocessors and accelerators. This algorithmictemplate orchestrates a collection of parameterizable, linear optimizationproblems over a polyhedral space of semantics-preserving transformations. Whilethe overall problem is not convex, effective algorithms can be derived fromthis template delivering unprecedented performance portability over GPU andmulticore CPU. We discuss the rationale for this algorithmic template andvalidate it on representative computational kernels/benchmarks.},
