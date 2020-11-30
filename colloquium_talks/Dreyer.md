---
layout: page
title: RustBelt: Logical Foundations for the Future of Safe Systems Programming
---

RustBelt: Logical Foundations for the Future of Safe Systems Programming
======
### by [Derek Dreyer](http://people.mpi-sws.org/~dreyer/)

- When: Friday, 12/04/2020, between 1pm and 2pm, EST
- Where: Zoom; Outside guests please RSVP by emailing <a href="mailto:harley.eades@gmail.com">Harley Eades</a>
- YouTube Stream: <https://youtu.be/z1Z4-AAIWQA>

#### Abstract

Rust is a new systems programming language, developed at Mozilla, that
promises to overcome the seemingly fundamental tradeoff in language
design between high-level safety guarantees and low-level control over
resource management. Unfortunately, none of Rust's safety claims have
been formally proven, and there is good reason to question whether
they actually hold. Specifically, Rust employs a strong,
ownership-based type system, but then extends the expressive power of
this core type system through libraries that internally use unsafe
features.

In this talk, I will present RustBelt
(<http://plv.mpi-sws.org/rustbelt/>), the first formal (and
machine-checked) safety proof for a language representing a realistic
subset of Rust. Our proof is extensible in the sense that, for each
new Rust library that uses unsafe features, we can say what
verification condition it must satisfy in order for it to be deemed a
safe extension to the language. We have carried out this verification
for some of the most important libraries that are used throughout the
Rust ecosystem.

After reviewing some essential features of the Rust language, I will
describe the high-level structure of the RustBelt verification and
then delve into detail about the secret weapon that makes RustBelt
possible: the Iris framework for higher-order concurrent separation
logic in Coq (<https://iris-project.org/>). I will explain by example
how Iris generalizes the expressive power of O'Hearn's original
concurrent separation logic in ways that are essential for verifying
the safety of Rust libraries. I will not assume any prior familiarity
with concurrent separation logic or Rust.

This is joint work with Ralf Jung, Jacques-Henri Jourdan, Robbert
Krebbers, and the rest of the Iris team.

#### Bio

Derek Dreyer is a professor of computer science at the Max Planck
Institute for Software Systems (MPI-SWS) and Saarland Informatics
Campus, and recipient of the 2017 ACM SIGPLAN Robin Milner Young
Researcher Award. His research concerns the development of rigorous,
machine-checked formal foundations for modern programming languages,
with an emphasis on compositional reasoning techniques such as type
systems and separation logic.  His research currently focuses on two
projects: Iris, a framework for higher-order concurrent separation
logic implemented in the Coq proof assistant and deployed in a wide
variety of projects in both academia and industry, and RustBelt, a
major verification effort to formally define and prove safety of the
Rust programming language.  He also knows a thing or two about Scotch
whisky.