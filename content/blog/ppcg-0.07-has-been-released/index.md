---
fragment: content
title: PPCG 0.07 has been released
---


<a href="http://ppcg.gforge.inria.fr/">PPCG 0.07</a>
was released containing one main change:

 * **Support hybrid tiling**

   Basic <a href="http://dl.acm.org/citation.cfm?id=2544160">hybrid tiling</a>
   can now be enabled using the ```--hybrid``` option.
   It currently only applies to stencils with a single statement.

   For example, hybrid tiling can be applied to the input (say ```heat-2d.c```)

   ~~~
   #define N 3072
   #define T 512

   void heat(float A[2][N][N])
   {
   #pragma scop
       for (long t = 0; t < T; t++) {
         for (long i = 1; i < N - 1; i++)
           for (long j = 1; j < N - 1; j++)
               A[(t+1)%2][i][j] = (1/9.0f) *
                   (A[t%2][i][j] +
                    A[t%2][i-1][j-1] + A[t%2][i-1][j] + A[t%2][i-1][j+1] +
                    A[t%2][i][j-1] + A[t%2][i][j+1] +
                    A[t%2][i+1][j-1] + A[t%2][i+1][j] + A[t%2][i+1][j+1]);

       }
   #pragma endscop
   }
   ~~~
   by invoking ```ppcg``` as follows

   ~~~
   ppcg --hybrid --sizes="{kernel[i]->tile[2,2,128];kernel[i]->block[1,128]}" \
	--isolate-full-tiles --unroll-copy-shared --unroll-gpu-tile heat-2d.c
   ~~~
