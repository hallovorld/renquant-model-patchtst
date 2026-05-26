# CLAUDE.md

Canonical operating model:
https://github.com/hallovorld/RenQuant/blob/main/doc/arch/subrepo-operating-model.md

Local repo map: `RENQUANT_REPOS.md`.

Branch policy: `main` is the stable interface consumed by other repos and
automation. Experiments, optimizations, and large upgrades happen on feature
branches, then merge back only after tests and integration checks pass.

## Repo Role

`renquant-model-patchtst` owns PatchTST/PatchTXT sequence-model train, score,
validate, and shadow-promotion workflows.

## Hard Boundaries

- Use `renquant-common` pipeline primitives for all train/eval workflows.
- Pull data through `renquant-base-data` manifests.
- Publish checkpoints and diagnostics through `renquant-artifacts` manifests.
- Do not own prod decision-tree logic, broker execution, GBDT internals, raw
  data, or uncontrolled experiment dumps.
- Large architecture or hyperparameter-search changes use a feature branch.
- Do not delete or empty the source umbrella repo at
  `/Users/renhao/git/github/RenQuant`.

## Required Evidence

PatchTST/PatchTXT reports must separate declared-label IC from raw
expected-return IC. Promotion requires walk-forward results, regime IC,
calibration health, benchmark comparison where applicable, and placebo/shuffle
sanity.

## Workflow

```bash
make test
make doctor
```
