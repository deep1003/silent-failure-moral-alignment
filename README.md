# Silent failure of moral alignment in large language-model evaluators

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Derived-data release for the under-review manuscript *"Silent failure of moral
alignment in large language-model evaluators"*.

The manuscript and generated figures are not included while the article is
under review. This repository is limited to the derived tables needed to inspect
the released evaluator/category measurements.

> **Silent failure**: an LLM evaluator responds with stable strength to the
> wrong moral dimensions, so its aggregate score remains close to the human
> reference while the underlying judgment structure has diverged.

> The earlier ICML 2026 Pluralistic Alignment Workshop version of this work
> lives in a separate repository,
> <https://github.com/deep1003/moral-orientation-calibration>.
> The two artefacts are intentionally separated: the workshop release is
> archival; this journal release supersedes it.

---

## Repository layout

```
data/
  pair_with_quadrant.csv             per (evaluator, category) cell:
                                     MOF, Vector RMSE, typology cell
  niche_full_42.csv                  per-evaluator median typology cell
  judge_slice_profiles.csv           aggregated per-judge × per-category profiles
  preemption_stats.json              bootstrap CIs + threshold sweep results
LICENSE                              MIT
README.md                            this file
```

---

## Data files

### `data/pair_with_quadrant.csv`

Cell-level summary for each evaluator and target category.

- `judge_model`: evaluator model name.
- `target_slice`: machine-readable target category.
- `target_slice_label`: display label for the target category.
- `MOF`: Moral Orientation Fit for the cell.
- `vector_rmse`: vector RMSE against the human reference profile.
- `quadrant`: typology label assigned from the MOF/RMSE plane.

### `data/niche_full_42.csv`

Per-evaluator median typology summary across the released category panel.

- `judge_model`: evaluator model name.
- `judge_quadrant`: median-level typology label.
- `median_MOF`: evaluator-level median MOF.
- `n_aligned_cells`: number of category cells assigned to the aligned quadrant.
- `pct_aligned_cells`: aligned-cell percentage.
- `top_aligned_categories`: highest-ranked aligned categories for the evaluator.

### `data/judge_slice_profiles.csv`

Aggregated per-evaluator, per-category profile table. It contains sample counts,
judge-score aggregates, Moral Foundations axis activations, profile blends, and
cross-fit diagnostics used to derive the compact summary tables.

### `data/preemption_stats.json`

Compact JSON summary of bootstrap intervals, threshold sensitivity, and
meta-category concentration checks computed from the derived tables.

The full Judge LLM panel parquet (~250 MB, 40 evaluators × 10,000 MHS comments)
is hosted on Zenodo and is required only for sentence-level analyses; the
derived tables in this repository do not require the parquet file.

---

## Data sources

- **Measuring Hate Speech corpus** (Sachdeva et al. 2022, UC Berkeley DLAB) —
  comments, annotator severity scores, target-category labels. Hugging Face:
  <https://huggingface.co/datasets/ucberkeley-dlab/measuring-hate-speech>.
- **Judge LLM panel** (40 models × 10,000 MHS comments, this work) — released
  via Zenodo (DOI to be assigned upon acceptance).
- **Moral Foundations 2.0 axis basis** — see Methods of the manuscript and
  Supplementary Section S1.

---

## Citation

```bibtex
@misc{chun2026silentdata,
  title  = {Derived data for Silent failure of moral alignment in large language-model evaluators},
  author = {Chun, Youngsam},
  year   = {2026},
  note   = {Under-review manuscript data release},
  url    = {https://github.com/deep1003/silent-failure-moral-alignment}
}
```

A machine-readable `CITATION.cff` is included. The manuscript citation will be
updated after acceptance.

---

## License

- **Code**: MIT (see `LICENSE`).
- **Derived tables**: CC BY 4.0.
- **Measuring Hate Speech corpus**: refer to the dataset's terms on Hugging
  Face.

---

## Contact

Youngsam Chun · `deep1003@snu.ac.kr`
Frontier AI Lab, KT Corporation · Ulsan National Institute of Science and
Technology (UNIST).
