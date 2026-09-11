# triangle-cover-number

**502 cards on the triangle-cover number `tc(G)` and K₄-free fiber coherence — the theory built
around Erdős 595. 403 carry a proof body. Includes an NP-completeness result, four independent
kills of the obvious local-certificate approaches, and a compression inequality that carries the
whole cardinal program.**

Author: Jared Wilder. First public timestamp: 2026-09-11.

`tc(G)` is the least number of triangle-free graphs whose union is `G`. Erdős 595 asks which graphs
need uncountably many. **That problem is not closed here.** What is here is the surrounding theory,
which turned out to be substantial on its own.

The barrier-tower results on 595 itself are in
[erdos595-barrier-tower](https://github.com/jaredwilder/erdos595-barrier-tower).

---

## The load-bearing lemma

**HG01 — Vertex-Partition Compression Inequality.** Let `P` be a partition of `V(G)` with
`|P| ≤ 2^μ`. Then

```
tc(G)  ≤  μ  +  sup_{P ∈ 𝒫} tc(G[P])
```

Binary-code the parts into `2^μ`, route each cross edge to the least coordinate where its two parts'
codes differ. That gives `μ` bipartite — hence triangle-free — layers, and the internal edges
contribute the supremum.

Everything cardinal in this bank is downstream of that trick.

## The ideal, and its cardinal invariants

**HG04.** `𝒥_κ(G) = {A ⊆ V(G) : tc(G[A]) ≤ κ}` is downward closed and **closed under unions of at
most `2^κ` members** — a `2^κ`-complete ideal, by disjointization plus HG01 at `μ = κ`.

**RG06.** For infinite `κ` with `tc(G) > κ`: `add(𝒥_κ), cov(𝒥_κ), non(𝒥_κ) ≥ (2^κ)⁺`.

**HG06 — indivisibility.** Every partition of `V(G)` into at most `2^κ` cells has a cell `P` with
`tc(G[P]) > κ`. This is the form a transfinite recursion needs.

**RG14.** Every K₄-free `G` with `tc(G) > κ` contains a stable set of cardinality `(2^κ)⁺`.

## The complexity result

**R3K06.** Given a finite K₄-free graph with its stable partition and realized triangle-type fiber
system, deciding whether a **coherent section** exists is **NP-complete**, with NP-hardness holding
already at branch domains of size three.

Membership by checking one representative edge per fiber; hardness by reducing 3-COLORING — and the
output graph of the reduction is **K₄-free**, which is what makes it non-trivial.

## Four independent kills of the local-certificate approach

These are the cards worth keeping, because each closes a route that looks obviously worth trying.

| card | what it kills |
|---|---|
| **CC06** | For every finite `m` there is a finite K₄-free Berge-acyclic fiber system in which **every subsystem of at most `m` constraints has a coherent section, while the whole system does not.** So there is no bounded local coherence test and **no finite Helly number.** |
| **no Helly bound in the 2-connected pure-permutation regime** | the same failure survives that restriction |
| **bounded feedback gives no Helly bound** | and the card notes it **"already fails at feedback number zero"** |
| **arc consistency is insufficient** | even with domain size two and a single cycle |

## Exact structure and enumeration

**PG04/PG05 — monodromy.** When the projected cycle relations are bijections `π_i : D_i → D_{i+1}`,
coherent sections biject with the **fixed points of the monodromy permutation**
`Π = π_{m−1} ∘ ⋯ ∘ π_0`, so their number is `|Fix(Π)|`.

**R3K01 — four-kernel classification.** A finite simple 2-connected graph of cyclomatic number 3,
with every degree-two path suppressed, has kernel isomorphic to exactly one of: four parallel edges
`Q4`; a triangle with multiplicities 2,2,1; a 4-cycle with opposite edges doubled; or `K₄`. Via
`Σ_v (deg v − 2) = 2|E| − 2|V| = 4`, then cases on 2, 3, 4 vertices. Carries a Lean target name and
is likely classical.

**Exact deletion spectra.** R3K18 enumerates the 81 assignments of the R3K13 core by violation count
(`N₀=0, N₁=36, N₂=18, N₃=24, N₆=3`, by colour-multiplicity type). R3K19 gives `N₁ = C(q+1,2)·q!` and
`N₂ = 3·C(q+1,4)·q!`. PG01 gives `Σ_i |Sol(𝒞 − C_i)| = m·N₀ + N₁`.

Paired with two negative cards — the one-step repair matrix collapses to the deletion spectrum, and
second-order repair is the first non-collapsed geometric invariant — this is a small complete theory
of what deletion data can and cannot see.

## A sharp arity boundary

**HG08 + RG03.** In a K₄-free graph with `tc(G) > κ`, any family of at most `κ` unary `κ`-valued
vertex maps is simultaneously constant on an induced positive subgraph — **but complete homogeneity
already fails for the single binary adjacency relation.**

RG03's proof of that failure is two lines: if the constant is 0 then `G[U]` is stable and
`tc ≤ 1`; if it is 1 then `G[U]` is complete, K₄-freeness gives `|U| ≤ 3`, so `tc(G[U]) ≤ 2 ≤ κ`.

Method works at arity 1, dies at arity 2. That saves anyone picking this up a great deal of time.

## A refutation

**595:T66.** *"Every edge of a K₄-free graph belongs to at most a fixed constant number of
triangles"* is **false, even for finite graphs** — m-page books defeat it for arbitrary `m`.

## Status labels and what is not claimed

The bank's own labels are reproduced verbatim: `UNCONDITIONAL_ELEMENTARY` (147),
`PROVED_IN_PACKET` (47), `UNCONDITIONAL_CONSTRUCTION` (46),
`UNCONDITIONAL_NEGATIVE_THEOREM` (24), `UNCONDITIONAL_CHARACTERIZATION` (17),
`UNCONDITIONAL_WITH_STANDARD_COMPACTNESS` (17), plus transfinite, reduction and corollary classes.

**403 of 502 cards carry a proof body. 99 do not, and those are statements only.**

No novelty is claimed for any card. Several — the four-kernel classification in particular — are
likely classical. Nothing here was run through a proof assistant; where a card names a Lean target,
that target was **not executed**.

## License

Apache-2.0.
