# tscc website handover

## Repository and source authority

This repository uses the same deliberate two-branch Nift publishing model as the
Nift website. The `stage` branch owns canonical source: `content/`, `templates/`,
`.nift/`, documentation, and this handover. The `main` branch owns only the built
website at repository root. On `stage`, `public/` is an embedded checkout of this
repository's `main` branch and is recorded as a Git link. It is intentionally not
a conventional submodule and there is no `.gitmodules` file.

This handover belongs at the root of `stage`. Do not add it to the generated
`main` branch unless publication policy explicitly changes.

Edit source on `stage` and rebuild with Nift. Do not hand-edit generated HTML as
canonical content, and never run the source build from the outer repository while
it is on `main`. Local builds/inspection are normal; commits, pushes, public
deployment, release/version claims, and publication require explicit approval.

For a normal publication checkpoint:

1. Check out `stage` in the outer repository and `main` in `public/`.
2. Edit only canonical source and documentation outside `public/`.
3. Run the intended Nift binary from the outer `stage` checkout.
4. Inspect and test the generated changes under `public/`.
5. Commit canonical source changes on `stage`.
6. Commit generated website changes inside `public/` on `main`.
7. Stage and commit the updated `public` Git-link pointer on `stage`.
8. Push both branches only when publication is authorized.

The source commit may precede the generated commit during local work, but a
published `stage` checkpoint must ultimately point at the matching published
`main` commit. Keep the two histories intelligible and do not mix source files
back into the deployment branch.

## Truthfulness burden

This site must explain the compiler that actually exists, not the compiler the
project may eventually become. “TypeScript compiler” can imply drop-in `tsc`
compatibility. Current product wording is experimental TypeScript-to-JavaScript
compiler; tscc 0.15.0 has substantial parsing/transforms/project/module support but
a bounded semantic overlay, binder, durable primitive type store and expression/
assignment checker rather than a general TypeScript type system.

Every capability claim should map to appropriate evidence—not parser acceptance
alone. Where useful distinguish supported, partial, experimental, planned, and
unsupported behavior, but only create a support matrix if checkpoint workflow can
keep it current.

## Current evidence and claims

The site currently advertises 525 independent cases (499 pass, zero fail, 26
semantic skips) and dated five-run local medians for startup, 100/500 basic files,
and 100-file feature-heavy/advanced fixtures. The August 2026 snapshot uses
TypeScript 7.0.2 and must be treated as checkpoint evidence rather than a stable
cross-machine speed claim.

Benchmark comparisons must separate `tscc`, `tsc --noCheck`, and full `tsc` and
state corpus, versions, configuration, machine, runs, cold/warm behavior, and
compiler scope. A no-check transpiler comparison is not a universal equivalent-work
claim while tscc lacks comprehensive semantic checking.

## Tested examples

Prefer website examples that are regression fixtures or are easily validated by
the current candidate:

```text
example.ts/tsx
→ candidate tscc
→ emitted JS/JSX
→ Node or downstream syntax validation
```

Do not advertise a feature merely because a parser branch exists. Runtime-bearing
features should have runtime evidence; malformed forms should fail controllably;
scope/evaluation-sensitive transforms need appropriate tests.

## Development workflow

After a validated compiler checkpoint:

1. Determine whether language, CLI/config, module/project, maturity, limitation,
   benchmark, or architecture claims changed.
2. Search all source content for affected claims/counts/examples/versions.
3. Verify important examples with the exact candidate tscc and reference tools.
4. Update support/limitations after implementation evidence is settled.
5. Build the website with the intended Nift binary.
6. Inspect generated diff, links/assets, responsive/accessibility behavior, and
   version/download references.
7. Review this handover and living website/product roadmap.

Internal refactors with no observable effect normally need no public copy change.

The coordinated compiler campaign is now public development context. Keep the
site synchronized with accepted checkpoint state without presenting planned
JS++ integration as a current runtime dependency. CP1 settles test-only
integration first and protects normal tscc builds from accidental JS++ linkage.

CP2 adds a machine-checked feature matrix in the compiler repository. Public
support summaries must remain consistent with its eight dimensions and named
external evidence rather than collapsing parser acceptance into support.

CP3/TC1 adds durable per-file compiler ownership through emission. The public
architecture and roadmap pages describe this as an internal foundation, not a
new TypeScript compatibility claim. Keep that distinction intact.

CP19/TC8A likewise adds canonical object-shape infrastructure without changing
the source-language support boundary; CP20 owns bounded structural checking.

CP20 now supports only the documented flat structural slice. Keep the 501/0/24
count and the nested/indexed/freshness/class limitations visible.

## Product boundaries

tscc is a sibling of Nift and Minify++, not “Nift's compiler.” Do not force common
branding or imply architectural dependency. Preserve the current site design
unless redesign is requested.

## Living production-support roadmap

First establish the compiler's intended production compatibility target and
evidence-backed feature inventory. Then audit every site capability, example,
CLI/config statement, limitation, architecture description, benchmark, maturity
claim, and download/version reference. Production-candidate validation should
compile/run key examples and map every major support claim to the regression suite.

This roadmap and handover are living infrastructure. Reassess them at every
substantial compiler or website checkpoint; add, remove, reorder, or rewrite work
as evidence changes. Do not let a support matrix rot or preserve planned behavior
as though it were current.

Detailed tscc website history lives at
`docs/handover/PROJECT-HISTORY.md`, including compatibility wording,
support evidence, benchmark integrity, production-support gates, and the living
roadmap.

## Documentation URL layout

The homepage remains `/index.html` and the documentation landing page remains
`/docs.html`, matching nift.dev. All secondary documentation/evidence/design pages
live under `/docs/*.html`, even when a page does not use a docs-specific template.
Keep tracked names, `@pathto(...)` references, authored content paths, and generated
output aligned with this rule when adding or renaming pages.

## Desktop table-fit checkpoint (2026-08-18)

The benchmark table now uses a fixed, wrapping desktop layout so it remains inside normal viewport widths. Keep benchmark columns wrap-safe; horizontal overflow should not be required on ordinary desktop widths.

## Memory-safety living record checkpoint (2026-08-18)

- `docs/memory-safety` is the dedicated living compiler lifetime/leak record beside Battle Tested. Establish the baseline before the semantic checker and retained compiler graphs become substantially larger.
- The page currently describes planned work only. Future results must record the exact compiler commit/toolchain/workload and distinguish confirmed leaks from allocator/runtime high-water behavior.

## tscc memory-safety Checkpoint 5A (2026-08-18)

- Public memory documentation now records the first compiler-lifetime baseline: 80 sanitizer-backed in-process iterations, settled native RSS across repeated lifetime runs, and repeated 120-file project/module graph success/failure/recovery pressure at tscc commit `a05d3d8`.
- Checkpoint 5B remains independent Valgrind confirmation. Do not describe Checkpoint 5 as complete until that evidence is returned and reconciled.

## tscc memory-safety Checkpoint 5 complete (2026-08-18)

- External Checkpoint 5B passed at tscc commit `d96419e`: Valgrind 3.26.0 completed 40 maintained compiler-lifetime iterations with 0 errors, 0 bytes in use at exit, and all 25,003 allocations freed.
- Public Memory & Resource Safety and Battle Tested pages now describe the compiler-lifetime baseline as complete while keeping the claim scoped to the maintained workloads, not TypeScript completeness.
- Exact Valgrind evidence is retained in the tscc source tree. The wider campaign proceeds to cross-project integration.
## CP22 / TC8C (2026-08-30)

Public object support now includes nested shapes, chained reads and path-specific
diagnostics. Extra source properties are intentionally structurally compatible.
## CP24 expression identity (2026-08-30)

The checker now consumes CompilationUnit-owned expression nodes. Describe this
as architecture, not broader TypeScript expression compatibility.

## CP26 structured expressions (2026-08-30)

The durable expression model now owns explicit node kinds, operators and child
identity for the bounded grammar. The independent 505/0/24 contract is unchanged.

## CP28 reusable object declarations (2026-08-30)

Public object support now includes basic aliases/interfaces and compatible
interface merging. The 533-case contract is 509/0/24; keep indexed/call
signatures, inheritance, generics and classes explicitly unsupported.
