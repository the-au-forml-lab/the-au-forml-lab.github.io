---
layout: page
mathjax: true
title: Granule
---

The Granule Language
--------------------

Many modern programs are resource sensitive, that is, the amount of resources (e.g., energy, bandwidth, time, memory), and their rate of consumption, must be carefully managed. Furthermore, many programs handle sensitive resources, such as passwords, location data, photos, and banking information. Ensuring that private data is not inadvertently leaked is as important as the functional input-output behaviour of a program.

Various type-based solutions have been provided for reasoning about and controlling resources. A general class of program behaviours called coeﬀects has been proposed as a uniﬁed framework for capturing diﬀerent kinds of resource analysis in a single type theory [[Petricek et al.](http://tomasp.net/academic/papers/structural/coeffects-icfp.pdf), [Petricek et al.](http://tomasp.net/academic/papers/coeffects/coeffects-icalp.pdf), [Brunel et al.](https://lipn.univ-paris13.fr/~mazza/papers/CoreQuantCoeff.pdf), [Gaboardi et al.](https://www.cs.kent.ac.uk/people/staff/dao7/publ/combining-effects-and-coeffects-icfp16.pdf), [Ghica et al.](https://www.cs.bham.ac.uk/~drg/papers/esop14.pdf), [Breuvart et al.](https://lipn.univ-paris13.fr/~breuvart/articles/boundedRel.pdf)]. Recently it has been shown how coeﬀect types can be integrated with eﬀect types for resource reasoning with eﬀects [[Gaboardi et al.](https://www.cs.kent.ac.uk/people/staff/dao7/publ/combining-effects-and-coeffects-icfp16.pdf)].

To gain experience with such type systems for real-world programming tasks, and as a vehicle for further research, we are developing **Granule**, a functional programming language based on the linear λ-calculus augmented with graded modal types, inspired by the coeffect-effect calculus of [Gaboardi et al.](https://www.cs.kent.ac.uk/people/staff/dao7/publ/combining-effects-and-coeffects-icfp16.pdf).

#### Graded Modal Type Theory

A graded modality is an indexed family of modalities with some additional structure on the indices which mirrors the structure of the axioms/proof rules. For example, the exponential modality of linear logic $$!$$ has a graded counterpart in Bounded Linear Logic [[Girard et al.](https://www.sciencedirect.com/science/article/pii/030439759290386T)], where $$!$$ is replaced with a family of modalities $$!_n$$ indexed by the natural numbers (the reuse bound). The operations of the usual natural number semiring are then used in the axioms/rules of the logic e.g., the transitivity axiom is $$!_{n*m} A \to !_n !_m A$$. There are various different examples in the literature under the name of coeffects which provide ﬁne-grained analysis of resources and context-dependence via graded necessity modalities.

The goal with Granule is to support arbitrary, user-customisable graded modalities to enable fine-grained, quantitative program reasoning. At the moment, there are three built-in modalities: BLL-style resource-bounded graded necessity, a security-lattice graded necessity, and an effect-graded possibility modality for I/O. Type checking is based on a bidirectional algorithm, interfacing with the Z3 SMT solver to discharge constraints.

**Example 1:** Reuse Bounds

```
dub : |Int| 2 -> Int
dub |x| = x + x

trip : |Int| 3 -> Int
trip |x| = x + x + x
```

The following is a valid Granule program:

```
twice : forall c . |(|Int| c -> Int)| 2 -> |Int| (2 * c) -> Int
twice |g| |x| = g |x| + g |x|

main : Int
main = twice |dub| |1| + twice |trip| |1|
```

The first definition specifies a function `dub` on the integers (type `Int`) whose ﬁrst parameter is used non-linearly, exactly twice, as captured by the resource bound `2` indexing the modality. The type `|Int| n` can be read as $$!_n \text{Int}$$ in [Girard et al.’s](https://www.sciencedirect.com/science/article/pii/030439759290386T) notation. The pattern match `|x|` discharges the incoming modality and binds `x` as a non-linear variable. Looking at the type signature for twice, we can deduce that it is a higher-order function: its ﬁrst parameter is a unary function whose parameter is used non-linearly exactly `c` times and which returns an `Int`—a good ﬁt for `dub` and `trip`. The second parameter of `twice` is used non-linearly exactly `2 * c` times, since `g` uses `c` copies of its first parameter and is applied twice. Thus, `main` will produce the value `10`. This example shows Granule's support of coeffect polymorphism.

**Example 2:** Security Levels

Another modality available in Granule is indexed by a two-point security lattice with levels: `Lo` and `Hi`. For example:

```
secret : |Int| Hi secret = |42|                   -- specified as Hi security

dub : forall (l : Level) . |Int| l -> |Int| l     -- at any level
dub |x| = |(x + x)|                               -- ...double an int

main : |Int| Hi main = dub secret                 -- double the secret
```

Here `main` is marked as a high-security value via its modal type. The `dub` function appears again, but its type now tracks security levels and is level-polymorphic. It takes an integer at any level `l`, returning a value at the same level. Crucially, the following program is ill-typed:

```
leak : |Int| Hi -> |Int| Lo
leak |x| = |x|                                    -- fails to type check
```

However, we can define a well-typed constant function that discards its high-security value to produce a low-security value by combining resource bounds with security levels:

```
notALeak : ||Int| Hi| 0 -> |Int| Lo
notALeak x = |0|
```

**Example 3:** Eﬀects

A graded possibility modality provides tracking of side eﬀects in the style of a graded monad and eﬀect system. A type `<t> f` describes a computation returning a value of type `t` and producing side eﬀects `f`.

In the following code, input (`read`) and output (`write`) operations to the stdio are tracked:

```
echo : <Int> [R, W]
echo = let <x : Int> = read in write x
```

The following shows both reuse bound coeffects and I/O effects coming together, explaining the side-effects of twice applying some integer function which has a read eﬀect:

```
doTwice : |(Int -> <Int> [R])| 2 -> |Int| 2 -> <Int> [R, R]
doTwice |f| |x| = let <a : Int> = f x in let <b : Int> = f x in <a + b>
```

#### Installation

Granule can be downloaded from [Github](https://github.com/granule-project/granule) and built and installed via [stack](https://docs.haskellstack.org/en/stable/README/).  Please see the [README](https://github.com/granule-project/granule/blob/master/README.md) for further instructions.


Footnote: This page was adopted from this abstract [Orchard and Liepelt](http://www.cs.ox.ac.uk/conferences/fscd2017/preproceedings_unprotected/TLLA_Orchard.pdf).