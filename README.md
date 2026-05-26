# renquant-model-patchtst

PatchTST/PatchTXT and sequence-model repository for RenQuant.

Operating model: https://github.com/hallovorld/RenQuant/blob/main/doc/arch/subrepo-operating-model.md

Repository map: [RENQUANT_REPOS.md](RENQUANT_REPOS.md)

Local automation:

```bash
make test
make doctor
```

This repo owns sequence-model train/score/validate workflows and shadow
candidate artifacts. It does not own production decision-tree logic, broker
execution, GBDT training internals, raw data, or unchecked experiment dumps.

## Pipeline Rule

All workflows are expressed as `renquant-common` Task/Job/Pipeline chains.

The first bootstrap commit contains dependency-injected sequence-model
pipeline contracts. Existing PatchTST scripts and HF wrappers should be ported
behind these tasks in reviewed slices with tests and ledger output.

## Initial Split Source

`hallovorld/RenQuant` commit
`8f3e08d8d1ae1e402a78f4815efb59e3c7c66aa8`.

## Local Test

```bash
PYTHONPATH=../renquant-common/src:src python -m pytest -q
```
