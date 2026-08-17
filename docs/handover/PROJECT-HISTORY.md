# Project history and institutional context

> This is a living historical companion to the repository's operational handover. The live repository remains authoritative. Maintain, correct, reorganize, or supersede this material as project evidence evolves while retaining durable rationale.

# tscc Website

## Product Communication, Compatibility, Development and Production-Support Handover

# 1. Identity

The tscc website has a particularly important responsibility:

> Explain exactly what compiler exists now.

Compiler marketing can become misleading very easily.

---

# 2. Avoid accidental compatibility promises

Calling something:

> a TypeScript compiler

can cause users to infer:

```text
drop-in tsc replacement
```

even when that is not the intended promise.

Website wording must reflect the actual compatibility contract.

Possible descriptions include:

```text
TypeScript compiler
TypeScript-compatible compiler
compiler for a TypeScript subset
TypeScript-to-JavaScript compiler
```

They are not equivalent.

Choose based on current product reality.

---

# 3. Feature claims

Never infer:

```text
parser recognizes syntax
→ feature supported
```

A website support claim should correspond to whatever end-to-end support level tscc promises.

Ideally:

```text
parse
+
semantics
+
emit
+
runtime
```

where appropriate.

---

# 4. Support matrix

tscc is a strong candidate for an explicit support matrix.

Possible statuses:

```text
supported
partial
experimental
planned
unsupported
```

But such a matrix creates a maintenance obligation.

If created, checkpoint workflow must update it.

---

# 5. Tested examples

Strong rule:

> Prefer examples that are themselves regression fixtures or are automatically validated against the current compiler.

This prevents the website from drifting into hypothetical syntax.

---

# 6. Example validation

Ideally important examples should be capable of:

```text
example.ts
↓
candidate tscc
↓
output.js
↓
runtime
```

during release validation.

---

# 7. Benchmark claims

Compiler benchmarks require exceptional care.

A comparison against `tsc` should specify enough context to know whether both tools are doing comparable work.

Relevant dimensions may include:

```text
type checking
emit
module count
input size
cold/warm process
tool versions
machine
compiler configuration
```

Do not compare a transpile-only path against full TypeScript type checking and imply universal compiler superiority.

---

# 8. Product maturity

Before production status, it is perfectly acceptable for the site to say, in appropriate language:

```text
this is what works
this is experimental
this is planned
```

Truthfulness is more valuable than prematurely looking finished.

---

# 9. Relationship to Nift and Minify++

tscc is a sibling project.

Do not present it as:

```text
Nift's compiler
```

unless architecture/product direction explicitly changes.

Likewise Nift should not be portrayed as requiring tscc.

---

# 10. Website role in production status

Before tscc can reasonably be called production-ready, its website should pass a capability audit:

```text
every major support claim maps to tested behavior
unsupported/partial areas are represented honestly
examples compile
important examples run
installation is current
CLI is current
compatibility wording is precise
benchmarks are fair
version/download links are current
```

---

# 11. Current website roadmap

**LIVING ROADMAP**

### First: establish compiler truth

```text
determine current compatibility target
determine current feature inventory
determine current maturity
```

### Then reconcile website

```text
audit every feature claim
audit every example
audit CLI
audit compatibility wording
audit benchmark claims
```

### Then improve production communication

Potentially:

```text
support matrix
tested examples
limitations
compatibility policy
benchmark methodology
development status
```

### Production-candidate stage

```text
build site
validate examples with candidate tscc
check downloads/releases
check version references
check links
review public claims against regression evidence
```

---

# 12. Roadmap maintenance

The tscc website roadmap should be explicitly tied to compiler checkpoints:

> Every validated tscc feature checkpoint must ask whether public support documentation changes. Every compiler roadmap revision must ask whether the website's description of maturity remains accurate. The website roadmap should evolve continuously with implementation evidence.

---

# 13. Post-production

After production:

```text
track new supported syntax
track TypeScript compatibility changes
update examples
update limitations
refresh benchmarks
add migration/integration guidance
reflect newly supported platforms
```

---

# 14. Deployment

Codex should determine from repository evidence:

```text
canonical source branch
build command
whether Nift builds the site
generated output
hosting
deployment branch
publication procedure
```

Do not impose nift.dev's workflow for symmetry.

---

# 15. Do not accidentally

```text
claim full TypeScript compatibility
advertise parser-only features
let support matrix become stale
publish unvalidated examples
publish apples-to-oranges tsc benchmarks
make tscc look dependent on Nift
describe planned behavior as current behavior
```

---


## 2026-08-18 — Documentation URL normalization

Normalized the tscc website to the same public documentation shape used by nift.dev: `/docs.html` remains the landing page and every secondary documentation, evidence, AI and design page now lives under `/docs/*.html`. Authored content moved under `content/docs/`, tracked names and `@pathto(...)` references were reconciled, stale root-level generated pages/metadata were removed, and current GitHub links were aligned with the `nift-dev` organization.

## 2026-08-18 — Desktop table fit

Made the benchmark table wrap safely within its documentation column so sibling-site desktop table audits can remain overflow-free.

## 2026-08-18 — Memory/resource-safety living documentation

Added a dedicated Memory & resource safety documentation page and linked it from Battle Tested/navigation. The page is deliberately a maintained evidence record: the dedicated leak/soak campaign is still marked planned, and future runs should publish exact reproducible workload/toolchain/result metadata rather than converting one run into a timeless claim.
