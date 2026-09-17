# Triangle-cover number and K4-free fiber coherence

For a graph `G`, define

\[
tc(G)=\min\{k:E(G)\text{ is covered by }k\text{ triangle-free subgraphs}\}.
\]

For finite `k`, this is equivalently the least number of edge colors needed so that no triangle of `G` is monochromatic.

This repository develops cardinal compression, coherent-section structure, exact finite kernels, and complexity results around this invariant and Erdős #595.

## Vertex-partition compression

Let `P` be a partition of `V(G)` with `|P|<=2^\mu`. Then

\[
\boxed{tc(G)\le \mu+\sup_{Q\in P}tc(G[Q]).}
\]

Assign binary codes to the parts and route each cross-edge to the first coordinate where the endpoint codes differ. Every cross-edge layer is bipartite, hence triangle-free.

A sharper quotient version is

\[
\boxed{tc(G)\le bc(Q_P)+\sup_{Q\in P}tc(G[Q]),}
\]

where `bc(Q_P)` is the bipartite-cover number of the quotient graph.

## Cardinal consequences

For infinite `\kappa`, let

\[
J_\kappa(G)=\{A\subseteq V(G):tc(G[A])\le\kappa\}.
\]

The program proves:

- `J_κ(G)` is downward closed and closed under unions of at most `2^κ` members;
- if `tc(G)>κ`, then the additivity, covering, and uniformity numbers of `J_κ(G)` are at least `(2^κ)^+`;
- every partition of `V(G)` into at most `2^κ` cells has a cell whose induced subgraph still has triangle-cover number greater than `κ`;
- every `K4`-free graph with `tc(G)>κ` contains a stable set of size `(2^κ)^+`.

## Exact K4-free realization of binary CSPs

A finite binary relation `R⊆A×B` can be realized as the exact boundary projection of a finite `K4`-free stable-partition graph gadget.

Using one private relation strip per binary constraint gives:

> **Every finite binary CSP has a polynomial-size exact K4-free fiber-coherence realization.**

Global coherent sections correspond exactly to satisfying assignments of the original CSP.

Applying this to graph 3-coloring yields NP-hardness with domain size three. Membership in NP is direct, so finite K4-free fiber coherence is NP-complete when cycle rank is unbounded.

For fixed cyclomatic rank `r` and maximum domain size `d`, feedback conditioning gives an algorithm with running time

\[
O(d^r\operatorname{poly}(N)).
\]

## No finite local-consistency bound

Several natural local-certification strategies fail globally.

For every finite `m`, there is a finite K4-free Berge-acyclic fiber system such that every subsystem of at most `m` constraints has a coherent section while the full system does not.

Consequences include:

- no bounded local coherence test;
- no finite Helly number for the general coherence problem;
- the failure persists in restricted permutation regimes;
- arc consistency already fails on a domain-two single-cycle example.

## Cycle monodromy

If the relations around a cycle are bijections

\[
\pi_i:D_i\to D_{i+1},
\]

then coherent sections are in bijection with fixed points of the monodromy permutation

\[
\Pi=\pi_{m-1}\circ\cdots\circ\pi_0.
\]

Hence the number of coherent sections is exactly

\[
|\operatorname{Fix}(\Pi)|.
\]

## Cyclomatic-rank-three kernels

After suppressing degree-two paths, every finite simple 2-connected graph of cyclomatic number three has one of four loopless branch kernels:

- `Q4` — four parallel edges;
- `T221` — triangle multiplicities `2,2,1`;
- `D22` — a 4-cycle with opposite doubled edges;
- `K4`.

These four topologies induce four corresponding coherence mechanisms: four-way intersection, ternary join, cycle monodromy, and a four-variable binary CSP.

## Exact finite spectra

The repository includes exact assignment/deletion counts for several finite cores. One representative spectrum is

```text
N0 = 0
N1 = 36
N2 = 18
N3 = 24
N6 = 3
```

for the 81 assignments of the rank-three core used in the finite classification.

## Relation to Erdős #595

The cardinal barrier and Lean formalization work for Erdős #595 is collected separately in [`erdos595-barrier-tower`](https://github.com/jaredwilder/erdos595-barrier-tower). This repository contains the broader triangle-cover/fiber-coherence theory.

The full Erdős #595 problem remains open; the structural, cardinal, complexity, and finite theorems above stand at their stated scopes.

Author: Jared Wilder. License: Apache-2.0.
