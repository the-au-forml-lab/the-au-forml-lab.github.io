---
layout: page
title:  Algorithmic Game Theory for Network Bottlenecks
---

 Algorithmic Game Theory for Network Bottlenecks
======
### by [Dr. Costas Busch](/)

- When: Friday, 09/18/2020, between 1pm and 2pm, EDT
- Where: Zoom; Outside guests please RSVP by emailing <a href="mailto:harley.eades@gmail.com">Harley Eades</a>
- YouTube Stream: ?

#### Abstract

Game theory studies interactions of selfish players, where each player
attempts to improve its own utility function without considering the
impact on others. Nash equilibria are states where all players are in
a locally optimal state from which no player wishes to
deviate. Algorithmic game theory studies how fast Nash equilibria can
be computed (if they exist) and also how the quality of equilibria
compare to globally optimal states (i.e. Price of Stability). Here, we
consider communication network games where packets to be routed are
modeled as players that interact with each other. Each packet is
routed along a chosen path in the network. The communication links may
be used simultaneously by multiple packet paths which causes network
congestion. To avoid congestion, packets prefer to be routed along
lowest utilized links. The congestion on a link can be simply measured
as the number of packet paths that use the link. The packet cost
function is proportional to the congestion of the links on the chosen
path.  To improve its cost, each packet picks a path will the lowest
congestion possible. However, in doing so a packet may increase the
congestion of other packets. Thus, selfish acts of packets can
destabilize the current state of other packets in the network. A
natural question is whether a global stable state (Nash equilibrium)
can be reached. Hence, we can formulate network congestion games.

Congestion games have been thoroughly studied in the literature for
the player (packet) cost function which is the sum of link congestions
in the chosen path. Such a cost function is not suitable to express
some critical performance attributes of the network, as for example
congestion bottlenecks and lifetime in battery operated wireless
networks. Here, we consider an alternative player cost function which
is the congestion of the bottleneck link in the chosen path, namely,
the maximum congestion of any link in the player’s path. Bottleneck
congestion is an interesting metric because it directly relates to the
time it takes to transfer all the packets in the network. Moreover,
the bottleneck congestion is particularly appropriate for wireless
networks because it relates to the energy used along the adjacent
nodes of the bottleneck link. It is known that Nash equilibria exist
for bottleneck congestion games. However, computing such equilibria is
a PLS-complete problem. Here, we present the first polynomial time
algorithm that finds a poly-log factor approximation of a bottleneck
Nash equilibrium. The resulting equilibrium has also near optimal
global bottleneck congestion. Thus, our work answers to the positive a
long standing open question of whether we can efficiently compute Nash
equilibria for bottleneck games.

#### Author Bio

Costas Busch obtained a B.Sc. degree in 1992 and an M.Sc. degree in
1995 both in computer science from the University of Crete, Greece. He
received a Ph.D. degree in computer science from Brown University in
2000. He is a professor at the School of Computer and Cyber Sciences
at Augusta University. His research interests are in the areas of
distributed algorithms and data structures, design and analysis of
communication algorithms, algorithmic game theory, and blockchains. He
has publications in several prominent venues in algorithms and
distributed computing.  His research has been supported by the
National Science Foundation.