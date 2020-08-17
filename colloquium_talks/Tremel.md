---
layout: page
title: Dependable Systems for Managing Valuable Data
---

Dependable Systems for Managing Valuable Data
======
### by Dr. Edward Tremel

- When: Friday, 08/21/2020, between 1pm and 2pm
- Where: Zoom; Outside guests please RSVP by emailing <a href="mailto:harley.eades@gmail.com">Harley Eades</a>

#### Abstract

Distributed computing systems have become an essential piece of
infrastructure for today's businesses, organizations, and governments;
they store, manage and interpret vast amounts of data, and allow
groups of people to communicate and take coordinated actions. With the
emergence of Internet-of-Things devices, distributed systems are also
responsible for monitoring and automating the physical world. As a
result, distributed systems face competing demands: they must be
dependable enough to be relied upon for essential tasks, but
responsive enough to handle requests with tight time constraints.

My research focuses on building distributed systems that provide
dependability guarantees while still maintaining high performance. In
this talk I will describe my work on one of these systems, Derecho,
which is a library for building replicated datacenter
applications. Derecho allows distributed services to increase their
fault-tolerance and scalability by organizing servers into replicated
shards, while achieving incredibly high data throughput and low
response latency. It accomplishes this by redesigning
state-machine-replication and fault-management protocols to use
non-blocking, asynchronous communication, and separating data flow
from control messages. Derecho also includes optional mechanisms for
making services durable by logging state to persistent storage, and in
the second half of my talk I will describe my work on a distributed
restart algorithm for Derecho and other durable replicated
services. This algorithm efficiently restarts a sharded, replicated
service from state stored in persistent logs, while respecting node
placement constraints and ensuring the state is mutually consistent
across all subsystems.

#### Author Bio

Edward Tremel is an assistant professor of Computer Science in the
School of Computer and Cyber Sciences at Augusta. He received his PhD
in Computer Science in 2020 from Cornell University, where he was
advised by Ken Birman. Previously, he attended Brown University, where
he graduated in 2013 with an honors Sc. B. in Computer Science. His
research on fault-tolerant distributed systems has been published in
ACM Transactions on Computer Systems and the IEEE International
Conference on Dependable Systems and Networks.
