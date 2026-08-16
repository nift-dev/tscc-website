# tscc website handover

## Repository and source authority

This repository is a Nift project on `main`. Canonical source is `content/`,
`templates/`, and `.nift/`; generated output is `public/` in the same repository.
This handover remains at the root and must not be placed under `public/`.

Edit source and rebuild with Nift. Do not hand-edit generated HTML as canonical
content. Local builds/inspection are normal; commits, pushes, public deployment,
release/version claims, and publication require explicit approval. Exact hosting
and deployment procedure is not established by the one-commit history and must be
confirmed rather than invented.

## Truthfulness burden

This site must explain the compiler that actually exists, not the compiler the
project may eventually become. “TypeScript compiler” can imply drop-in `tsc`
compatibility. Current product wording is experimental TypeScript-to-JavaScript
compiler; tscc 0.15.0 has substantial parsing/transforms/project/module support but
no semantic type checker.

Every capability claim should map to appropriate evidence—not parser acceptance
alone. Where useful distinguish supported, partial, experimental, planned, and
unsupported behavior, but only create a support matrix if checkpoint workflow can
keep it current.

## Current evidence and claims

The site currently advertises 511 independent cases and local benchmark ratios
for 100 TS files, 100 TSX files, and a 200-module CommonJS fixture. Those correspond
to retained 0.13–0.15-era evidence and must be treated as checkpoint measurements.

Benchmark comparisons must separate `tscc`, `tsc --noCheck`, and full `tsc` and
state corpus, versions, configuration, machine, runs, cold/warm behavior, and
compiler scope. A no-check transpiler comparison is not a universal equivalent-work
claim while tscc lacks semantic checking.

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
