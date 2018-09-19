+++
fragment = "content"
_authorize = "http://dl.acm.org/authorize?N21650"
_pdf = "grosser-2017-Simple-Accurate-Analytical-Time-Modeling-and-Optimal-Tile-Size-Selection-for-GPGPU-Stencils.pdf"
acmid = "3018744"
address = "New York, NY, USA"
author = "Prajapati, Nirmal and Ranasinghe, Waruna and Rajopadhye, Sanjay and Andonov, Rumen and Djidjev, Hristo and Grosser, Tobias"
booktitle = "Proceedings of the 22Nd ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming"
doi = "10.1145/3018743.3018744"
isbn = "978-1-4503-4493-7"
keywords = "analytical models, gpgpu, hybrid hexagonal classic tiling, performance prediction, polyhedral method, stencils"
location = "Austin, Texas, USA"
numpages = "15"
pages = "163--177"
publisher = "ACM"
series = "PPoPP 2017"
title = "Simple, Accurate, Analytical Time Modeling and Optimal Tile Size Selection for GPGPU Stencils"
_url = "http://doi.acm.org/10.1145/3018743.3018744"
year = "2017"
+++

Stencil computations are an important class of compute and dataintensive programs that occur widely in scientific and engineeringapplications.A number of tools use sophisticated tiling, parallelization, and memory mappingstrategies, and generate code that relies on vendor-supplied compilers. Thiscode has a number of parameters, such as tile sizes, that are then tuned viaempirical exploration.We develop a model that guides such a choice. Our model is a simple set ofanalytical functions that predict the execution time of the generated code. Itis deliberately optimistic, since tilesizes and, moreover, the optimistic assumptions are intended to enable we aretargeting modeling and parameter selections yielding highly tuned codes.We experimentally validate the model on a number of 2D and 3D stencil codes,and show that the root mean square error in the execution time is less than10\% for the subset of the codes that achieve performance within 20\% of thebest. Furthermore, script, based on using our model, we are able to predicttile sizes that achieve a further improvement of 9\% on average.}
