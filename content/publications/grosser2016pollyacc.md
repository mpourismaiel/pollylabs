+++
fragment = "content"
_pdf = "grosser-2016-polly-acc-transparent-compilation-to-heterogeneous-hardware.pdf"
acmid = "2926286"
address = "New York, NY, USA"
articleno = "1"
author = "Grosser, Tobias and Hoefler, Torsten"
booktitle = "Proceedings of the 2016 International Conference on Supercomputing"
doi = "10.1145/2925426.2926286"
isbn = "978-1-4503-4361-9"
keywords = "Auto-Parallelization, GPGPU, Polyhedral Compilation"
location = "Istanbul, Turkey"
numpages = "13"
pages = "1:1--1:13"
publisher = "ACM"
series = "ICS'16"
title = "Polly-ACC Transparent Compilation to Heterogeneous Hardware"
_url = "http://doi.acm.org/10.1145/2925426.2926286"
year = "2016"
+++

Programming today's increasingly complex heterogeneous hardware is difficult, as it commonly requires the use of data-parallel languages, pragma annotations, specialized libraries, or DSL compilers. Adding explicit accelerator support into a larger code base is not only costly, but also introduces additional complexity that hinders long-term maintenance. We propose a new heterogeneous compiler that brings us closer to the dream of automatic accelerator mapping. Starting from a sequential compiler IR, we automatically generate a hybrid executable that - in combination with a new data management system - transparently offloads suitable code regions. Our approach is almost regression free for a wide range of applications while improving a range of compute kernels as well as two full SPEC CPU applications. We expect our work to reduce the initial cost of accelerator usage and to free developer time to investigate algorithmic changes.}
