---
fragment: content
title: New Polly ARM64 buildbot hosted by Qualcomm
---


[Polly](http://polly.llvm.org) gained a new ARM64 Buildbot sponsored by
[Qualcomm Innovation Center](https://www.qualcomm.com/company/about), which
adds ARM64 platform coverage to Polly's continious integration testing:

<br>

<center>
<a href="http://lab.llvm.org:8011/builders/polly-arm-linux"> <img src="/images/arm64-buildbot.jpg" alt="ARM64 Buildbot" style="width: 400px;"/></a>
</center>
<br>
<br>

With this buildbot Polly increases its [buildbot
farm](http://lab.llvm.org:8011/console?category=polly) to nine builders. Polly
runs the following builders:

- Two fast 'make check' builds on
[AMD64](http://lab.llvm.org:8011/builders/polly-amd64-linux) and
[ARM64](http://lab.llvm.org:8011/builders/polly-arm-linux)

- Seven LLVM LNT builds:
  - [Polly Standard](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-fast)<br>
    -O3 -mllvm -polly
  - [Polly Autopar](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-parallel-fast/)<br> -O3 -mllvm -polly -mllvm -polly-parallel -lgomp
  - [Polly Extended Coverage](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-unprofitable)<br>-O3 -mllvm -polly -mllvm -polly-process-unprofitable
  - [Polly Performance](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly)<br> -O3 -mllvm -polly
  - [Polly "Before-Vectorizer](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-before-vectorizer)<br> -O3 -mllvm -polly -mllvm -polly-position=before-vectorizer
  - [Polly "Before-Vectorizer" Extended Coverage](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-before-vectorizer-unprofitable)<br> -O3 -mllvm -polly -mllvm -polly-position=before-vectorizer -mllvm -polly-process-unprofitable
  - [Polly "Before-Vectorizer" Only Scop-Detection](http://lab.llvm.org:8011/builders/perf-x86_64-penryn-O3-polly-before-vectorizer-detect-only)<br> -O3 -mllvm -polly -mllvm -polly-position=before-vectorizer

Besides the standard *-O3 -mllvm -polly* configuration, Polly regularly tests
its ability to generate parallel code, and also runs in an "extended coverage
mode" called *-mllvm -polly-unprofitable* which forces Polly to transform each
trivial loop it encounteres to provide higher test coverage on Polly's
transformation engine by transforming even code where we do not expect any
performance gains. Finally, with our Polly Performance bot, we regularly report
performance results to the LLVM performance tracking infrastructure hosted at
[http://llvm.org/perf/](http://llvm.org/perf/).

Besides the above set of buildbots, we also host a set of "Before-Vectorizer"
build bots, which keep track of our efforts to move Polly into the LLVM pass
pipeline with the goal to remove the need for additional canonicalization passes
when running Polly. Such passes always pre-transform the IR that is fed to the
LLVM standard pass pipeline and can consequently result in random difficult to
avoid performance changes. After moving Polly into the Pass pipeline, we expect
Polly to only affect performance in cases where our performance model predicts a
clear benefit. You can find more information about this topic
in the [Polly Documentation](http://polly.llvm.org/docs/Architecture.html#polly-in-the-llvm-pass-pipeline).

Polly is also regularly tested externally. Publicly accessible are the [FFmpeg
FATE tests](http://fate.ffmpeg.org/). More tests are run in-house by different
users.


<br>
