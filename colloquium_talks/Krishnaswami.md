---
layout: page
title: Adjoint Reactive GUI Programming
---

Adjoint Reactive GUI Programming
======
### by Dr. Neel Krishnaswami

- When: Friday, 10/9/2021, between 1pm and 2pm (5pm-6pm UTC), EST
- Where: Zoom; Outside guests please RSVP by emailing <a href="mailto:harley.eades@gmail.com">Harley Eades</a>
- YouTube Stream/Recording: <https://youtu.be/Jp5DsOXs6fE>

#### Abstract

Most interaction with a computer is done via a graphical user
interface. Traditionally, these are implemented in an imperative
fashion using shared mutable state and callbacks. This is efficient,
but is also difficult to reason about and error prone. Functional
Reactive Programming (FRP) provides an elegant alternative which
allows GUIs to be designed in a declarative fashion. However, most FRP
languages are synchronous and continually check for new data. This
means that an FRP-style GUI will "wake up" on each program cycle. This
is problematic for applications like text editors and browsers, where
often nothing happens for extended periods of time, and we want the
implementation to sleep until new data arrives. In this talk, I
present an asynchronous FRP language for designing GUIs called
λ𝖶𝗂𝖽𝗀𝖾𝗍. Our language provides a novel semantics for widgets, the
building block of GUIs, which offers both a natural Curry--Howard
logical interpretation and an efficient implementation strategy.
