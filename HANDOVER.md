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

The site currently advertises 519 independent cases (492 pass, zero fail, 27
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
