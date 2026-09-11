# Triangle-cover number and K4-free fiber coherence

**A 502-card research program on the triangle-cover number `tc(G)` and K4-free fiber coherence. 403 cards carry proof bodies. The program includes cardinal compression theorems, exact kernel structure, an NP-completeness result, four independent local-certificate barriers, and finite enumeration formulas.**

Author: Jared Wilder. First public timestamp: 2026-09-11.

For a graph `G`, `tc(G)` is the least number of triangle-free graphs whose union is `G`. This repository is the broad subject home for the structural/fiber theory built around Erdős #595. The focused formal/cardinal barrier tower remains at `jaredwilder/erdos595-barrier-tower`; the two repositories cover different lanes of the same larger problem area.

## Vertex-partition compression

**HG01 — Vertex-Partition Compression Inequality.** Let `P` be a partition of `V(G)` with `|P|<=2^mu`. Then

`tc(G) <= mu + sup_{Q in P} tc(G[Q])`.

Assign binary codes to the parts and route every cross-edge to the first coordinate in which the two part-codes differ. Each cross-edge layer is bipartite, hence triangle-free; internal edges contribute the supremum.

This compression inequality drives the cardinal layer of the program.

## The induced ideal and cardinal invariants

For infinite `kappa`, define

`J_kappa(G)={A subset V(G): tc(G[A])<=kappa}`.

The bank proves:

- **HG04:** `J_kappa(G)` is downward closed and closed under unions of at most `2^kappa` members;
- **RG06:** if `tc(G)>kappa`, then `add(J_kappa)`, `cov(J_kappa)`, and `non(J_kappa)` are at least `(2^kappa)^+`;
- **HG06:** every partition of `V(G)` into at most `2^kappa` cells contains one cell whose induced subgraph still has triangle-cover number above `kappa`;
- **RG14:** every K4-free `G` with `tc(G)>kappa` contains a stable set of cardinality `(2^kappa)^+`.

These are structural/cardinal consequences of the compression mechanism, not merely finite search observations.

## Coherent-section complexity

**R3K06.** Given a finite K4-free graph together with its stable partition and realized triangle-type fiber system, deciding whether a coherent section exists is **NP-complete**. NP-hardness already holds when branch domains have size three.

The reduction is arranged so that the output graph remains K4-free; this is part of the theorem rather than an incidental complexity statement.

## Four independent barriers to local certification

The program proves that several natural local-consistency strategies cannot characterize global coherence.

- **CC06:** for every finite `m`, there is a finite K4-free Berge-acyclic fiber system in which every subsystem of at most `m` constraints has a coherent section while the full system does not. Hence there is no bounded local coherence test and no finite Helly number.
- The same no-Helly phenomenon survives in the 2-connected pure-permutation regime.
- Bounded feedback does not restore a Helly bound; the recorded countertheory already fails at feedback number zero.
- Arc consistency is insufficient even with domain size two and a single cycle.

These are negative theorems about specific proof architectures. They explain why the global theory needs more than local consistency checks.

## Exact finite structure

### Monodromy

**PG04/PG05.** If projected cycle relations are bijections

`pi_i : D_i -> D_(i+1)`,

then coherent sections are in bijection with fixed points of the monodromy permutation

`Pi = pi_(m-1) o ... o pi_0`.

Thus the number of coherent sections is exactly `|Fix(Pi)|`.

### Cyclomatic-rank-three kernels

**R3K01.** Suppress all degree-two paths in a finite simple 2-connected graph of cyclomatic number three. The resulting loopless kernel is exactly one of four types:

- `Q4` — four parallel edges;
- `T221` — triangle multiplicities `2,2,1`;
- `D22` — a 4-cycle with opposite edges doubled;
- `K4`.

The proof uses `sum_v(deg(v)-2)=4` followed by the possible kernel orders. Historical novelty is not asserted; the classification is retained because it is the exact finite structural interface used by the rest of the program.

### Deletion spectra

The bank contains exact enumeration formulas, including:

- `R3K18`: for the 81 assignments of the R3K13 core, violation counts
  `N0=0, N1=36, N2=18, N3=24, N6=3`;
- `R3K19`: `N1=C(q+1,2) q!` and `N2=3 C(q+1,4) q!`;
- `PG01`: `sum_i |Sol(C-C_i)| = m N0 + N1`.

Companion negative results show that the one-step repair matrix collapses to this deletion spectrum, while second-order repair is the first non-collapsed geometric invariant.

## Unary/binary arity boundary

**HG08 + RG03.** In a K4-free graph with `tc(G)>kappa`, every family of at most `kappa` unary `kappa`-valued vertex maps is simultaneously constant on an induced positive subgraph.

The analogous statement already fails for the single binary adjacency relation. If adjacency were constantly 0, the induced graph would be stable; if constantly 1, K4-freeness restricts the induced set to at most three vertices. Either case forces small triangle-cover number.

Thus the method has a sharp conceptual boundary between unary structure and binary adjacency.

## Exact refutation

**595:T66.** The claim that every edge of a K4-free graph belongs to at most a fixed constant number of triangles is false: arbitrarily large page-book graphs give finite counterexamples.

## Evidence state

The 502-card bank contains several explicit authority classes. The largest groups are:

- `UNCONDITIONAL_ELEMENTARY` — 147 cards;
- `PROVED_IN_PACKET` — 47;
- `UNCONDITIONAL_CONSTRUCTION` — 46;
- `UNCONDITIONAL_NEGATIVE_THEOREM` — 24;
- `UNCONDITIONAL_CHARACTERIZATION` — 17;
- `UNCONDITIONAL_WITH_STANDARD_COMPACTNESS` — 17;

plus transfinite, reduction, corollary and target classes.

**403 of 502 cards contain a proof body; 99 are statement-only.** The presence of a Lean target name does not mean that target was executed. This repository does not claim blanket Lean certification of the bank.

Historical novelty is separate from the mathematics. Several statements, including the four-kernel classification, may be classical and should receive literature adjudication before any priority claim.

## Relationship to Erdős #595

The parent Erdős #595 problem is the motivation for much of this theory. Its status does not determine the status of the child theorems above.

For the focused formal/cardinal barrier results—including the continuum coverability theorem and 27 sorry-free Lean files—see `jaredwilder/erdos595-barrier-tower`.

Earlier copies of the fiber/coherence banks remain under broad repositories such as `erdos-theorems` and `unpublished-math-papers`; those are now provenance mirrors. **This repository is the preferred human/citation home for the broad triangle-cover/fiber-coherence theory.**

## License

Apache-2.0.
