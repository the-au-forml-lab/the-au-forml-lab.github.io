---
layout: page
title: Achieving Programmability and Performance for Data-Intensive Computations Using Reduction Based APIs
---

Achieving Programmability and Performance for Data-Intensive Computations Using Reduction Based APIs
======
### by Dr. Gagan Agrawal

- When: Friday, 10/30/2020, between 1pm and 2pm, EDT
- Where: Zoom; Outside guests please RSVP by emailing <a href="mailto:harley.eades@gmail.com">Harley Eades</a>
- YouTube Stream: <https://youtu.be/w2YwapDABRw>

#### Abstract

In developing applications for data-intensive computations, there has
typically been a tradeoff between programmability and performance,
with frameworks like MapReduce preferring programmability over
performance. Our work has been demonstrating that high-level APIs can
be supported without compromising performance. Specifically, we
introduced a variant of MapReduce based on the idea of reduction
object. This talk will describe three different systems we have
developed using this API (and its extensions). The first system
focused on in-situ analytics for scientific simulations. Our system,
Smart, is able to provide a high-level API for developing such
applications. This system results in much higher performance compared
to systems like Spark, and almost comparable performance to use of
MPI.  The second system is for processing streaming data in a
fault-tolerant fashion. Finally, the last system considers an IoT
environment where data is processed using a combination of edge
devices and a centralized system. We focus on a set of Computer Vision
applications for this environment. By generalization of our
reduction-based API, we show how a pattern based framework can achieve
programmability and performance, and even facilitate optimizations not
normally feasible.