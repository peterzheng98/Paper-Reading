#! https://zhuanlan.zhihu.com/p/266860873
# Stability in Weak Memory Models

Author: Jade Alglave(Oxford University), Luc Maranget(INRIA)

Tag: Weak Memory Model

## Abstract
1. Concurrent programs running on weak memory models => relaxed behaviours
2. Examine how to constrain the behaviour of program via synchronisation
3. Define sufficient conditions ensuring stability to a program. (Power's locks and Read-Modify-Write primitives meet)
4. Minimize the amount of required synchronisation. (Find which part should be synchronisation)
5. Give out the offence tool.

## Context
1. Executions:
    - (Event) Read or write, composed of a direction R or W, a location, the instruction from which it comes, its value, its processor and unique identifier.
    - Represent each instruction by the events it issues.
    - Define $\mathbb{E}$ for set of events and $\mathbb{W}$ for subset of write.
    - (Event Structure) $E$ composed of its events $\mathbb{E}$, the program order and a per-processor total order over $\mathbb{E}$.
2. Architectures:
    - A write may be commited first into a store buffer, then into a cache and finally into memory.
    - **A processor may read a past value.**
    - Model this by some subrelation of read-from edge being non-global.
    - Define write serialisation and from read is global. (In TSO, but in ARM maybe not).

