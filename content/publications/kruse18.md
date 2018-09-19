+++
fragment = "content"
_pdf = "kruse-2018-DeLICM-Scalar-dependence-removal-at-zero-memory-cost.pdf"
address = "New York, NY, USA"
author = "Kruse, Michael and Grosser, Tobias"
booktitle = "Proceedings of the 2018 IEEE/ACM International Symposium on Code Generation and Optimization"
doi = "10.1145/3168815"
location = "Vienna, Austria"
month = "e"
publisher = "ACM"
series = "CGO 2018"
title = "DeLICM: Scalar Dependence Removal at Zero Memory Cost"
_url = "http://doi.acm.org/10.1145/3168815"
year = "2018"
+++

Increasing data movement costs motivate the integration ofpolyhedral loop optimizers in the standard flow (-O3) of production compilers.While polyhedral optimizers have been shown to be effective when applied assource-to-source transformation, the single static assignment form used inmodern compiler mid-ends makes such optimizers less effective. Scalardependencies (dependencies carried over a single memory location) are the mainobstacle preventing effective optimization. We present DeLICM, a set oftransformations which, backed by a polyhedral value analysis, eliminateproblematic scalar dependences by 1) relocating scalar memory references tounused array locations and by 2) forwarding computations that otherwise causescalar dependences. Our experiments show that DeLICM effectively eliminatesdependencies introduced by compiler-internal canonicalization passes, humanprogrammers, optimizing code generators, or inlining -- without the need forany additional memory allocation. As a result, polyhedral loop optimizationscan be better integrated into compiler pass pipelines which is essential formetaprogramming optimization.}
