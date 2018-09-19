+++
fragment = "content"
_pdf = "grosser-2017-Optimistic-Loop-Optimization.pdf"
_slides = "grosser-2017-Optimistic-Loop-Optimization_slides.pdf"
acmid = "3049864"
address = "Piscataway, NJ, USA"
author = "Doerfert, Johannes and Grosser, Tobias and Hack, Sebastian"
booktitle = "Proceedings of the 2017 International Symposium on Code Generation and Optimization"
isbn = "978-1-5090-4931-8"
keywords = "Polyhedral Model, Presburger Precondition, Program Versioning, Static Analysis"
location = "Austin, USA"
numpages = "13"
pages = "292--304"
publisher = "IEEE Press"
series = "CGO 2017"
title = "Optimistic Loop Optimization"
_url = "http://dl.acm.org/citation.cfm?"
year = "2017"
+++

Compilers use static analyses to justify program optimizations.As every optimization must preserve the semantics of the original program,static analysis typically fall-back to conservative approximations.Consequently, the set of states for which the optimization is invalid isoverapproximated and potential optimization opportunities are missed. Insteadof justifying the optimization statically, a compiler can also synthesizepreconditions that imply the correctness of the optimizations and are checkedat the runtime of the program.  In this paper, we present a framework tocollect, generalize, and simplify assumptions based on Presburger arithmetic.We introduce different assumptions necessary to enable a variety of complexloop transformations and derive a (close to) minimal set of preconditions tovalidate them at runtime. Our evaluation shows that the runtime verificationintroduces negligible overhead and that the assumptions we propose almostalways hold true. On a large benchmark set including SPEC and NPB our techniqueincreases the number of modeled non-trivial loop nests by a factor of 3.9×.}
