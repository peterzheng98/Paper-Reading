#! https://zhuanlan.zhihu.com/p/266631045
# TOPLAS 1988: Efficient and Correct Execution of Parallel Programs that Share Memory
Author: Dennis Shasha(NYU), Marc Snir(IBM T.J. Watson Research Center)

Tag: Theory, Parallel Languages.

## Abstract
1. The paper consider an optimization problem that arises in the execution of parallel programs on shared-memory MIMD computers.
2. Find a minimal set of delays that enforces sequential consistency.
3. Use conflict graph similar to that used to schedule transactions in distributed databases.
4. Offer new compiler optimization techniques for parallel languages that support shared variables.

## Preliminaries
1. The program consists of instructions and each one specifying the execution of one operation.
2. Operation: accesses one or more storage locations(memory locations,registers). This should be atomic.
3. Write: update the value accessed.
4. **Operation only communicate by accessing the same variable.**
5. Conflict: two accesses to the same variable (at least one is write) and except the counter (the order will not affect the result).
6. Execution Order: Specifies the order in which conflicting accesses are executed.
7. **Any sequential execution of the accesses in an order that extends the execution order exhibits the same behavior.** (The execution order will uniquely determine the behavior)
8. The program order is the union of several disjoint chains. Restriction to Execution order: If A precedes B, A executes all its storage accesses before B executes any of its access.

### Definition
1. (Partial Order) Irreflexive, asymmetric, transitive relation. It can be represented by a DAG.
2. (Total/Linear Order) Every two distinct elements are ordered.
3. (Orientation) E is an orientation if uCv => uEv or vEu. (C is a symmetric relation)
4. (Proper Orientation) E is an acyclic orientation of C. (C is a symmetric relation)
5. (Closed): The relaion P is closed under A if uPv, uAu', vAv', not uAv => v'Pv'. 
    - P: irreflexive relation, A: equivalence relation on the same set U
    - P/A: the irreflexive relation induced by P on the family U/A of equivalence classes of A: u P/A v if (1) u != v, (2) there exists u in U and v in V => uPv.
    - P transitive => P/A transitive
6. (Closed) P is closed under A iff for any u, v: $[u]P/A[v] \Rightarrow uPv$
7. (Lexicographic Product) $P = P_1 \times P_2:\ uPv \text{  if  } (1)\neg uAv\land [u]P_1[v]\text{ or }(2)uAv\land [u]P_2[v]$
