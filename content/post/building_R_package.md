+++
date = "2014-08-12T19:55:16"
title =  "Building  R package from C codebase"
draft = false
tags = []
math = false
+++


I have been trying to build an R package that uses C code. I was not fast enough to get a working build for some time as it is a wrapper package around an existing C library and I wanted to submit to CRAN eventually, so I needed to get a linux and windows (32 and 64-bit) builds working correctly.
Building an R package even with native R code is not easy.There are a lot of intricacies for a "software-developer by necessity" like me to learn and it is definitely not idiot-proof.
I will try to write a few posts on this journey.


