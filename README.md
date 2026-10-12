# Circular Knowledge Systems (CKS) — anonymous research artifact

Companion repository for the ICDE 2027 DEFT vision-paper manuscript, **Circular Knowledge Systems: Contract-Aware Planning for Governed Reuse Across Workflows and Time**.

CKS explores circular-economy-inspired reuse, transformation, recomputation and retirement of derived knowledge across workflows under contracts, provenance and time-dependent governance. **KnowledgeOps** is the broader operational vision; the `Decide` interface described in the paper is a *proposed* interface, **not** a complete API implemented here.

## Repository contents

- `paper/main.tex`: editable IEEE two-column V17 manuscript (self-contained references and TikZ drawings).
- `paper/manuscript_v17.pdf`: matching manuscript snapshot.
- `prototype/`: original Phase 7 integrated exploratory Python model, experiment runner, scaling runner and tests.
- `results/phase5/`: separate multi-view/derivation experiment, including matched-optimizer comparison.
- `results/phase6b/`: separate governance adversarial probes.
- `results/phase7/`: integrated synthetic experiments, including feasibility and timing results.
- `docs/CLAIMS_AND_LIMITATIONS.md`: claim-to-evidence map, scope and reproducibility caveats.
- `docs/ANONYMITY_AND_RELEASE.md`: anonymization and pre-submission checklist.
- `scripts/check_artifact.py`: quick consistency checks.

## Requirements

Python 3.10+; the exploratory prototype uses the Python standard library only. For the paper: a TeX distribution with `IEEEtran`, `tikz`, `amsmath`, `booktabs`, `cite`, `url`, and `balance`.

## Reproduce

From repository root:

```bash
python -m unittest discover -s prototype -p 'test_*.py' -v
python prototype/experiment.py --seeds 5 --workflows 8 --variants 4
python prototype/scaling.py --seeds 3 --workflows 8
python scripts/check_artifact.py
```

**Important:** Experiment scripts may write `results.csv`, `summary.csv`, `audit.json`, or `scaling.csv` into the current working directory. Run in a disposable working directory if you want to preserve the archived outputs in `results/`. Random seeds, input settings and runtime environment matter; archived CSVs are the original reported outputs, not a guarantee of byte-identical regenerated timings.

Compile paper:

```bash
cd paper
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

## Status and limitations

This is an **exploratory synthetic research artifact**, not a production KnowledgeOps system. It does not implement the full `Decide` interface, a general contract algebra, complete independent audit certificates, online replanning, or a general proof of infeasibility. Exact search scales exponentially with the number of candidate materialization slots. The same-information multi-view exact baseline is a negative control: there is **no claim** that CKS beats a conventional optimizer given identical feasible plans and costs.

## Citation and release

The manuscript is anonymized for peer review. Please do not add author names, affiliations, personal paths, or identifying repository ownership metadata to the review version. A public permanent release, license, DOI and citation metadata should be finalized after the applicable review policy is checked. No open-source license is granted by this archive as supplied.
