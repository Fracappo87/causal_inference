# causal_inference

Personal notes, notebooks and experiments for studying causal inference, from potential outcomes and DAGs to modern estimation methods.

## How the repo is organised

The repo is a collection of **experiment sets**. Each set is a top-level folder focused on one technique (for example linear models, inverse probability weighting, double machine learning, surrogate indexes), and holds all the notebooks, scripts and papers for that study.

Sets are numbered so they stay in the order they were started:

```
causal_inference/
├── README.md          this file: conventions and index of experiment sets
├── _template/         skeleton to copy when starting a new set
├── 01_<technique>/
├── 02_<technique>/
└── ...
```

## Each experiment set is self-contained

Every set must be runnable on its own, without depending on any other folder in the repo:

- it has its **own uv environment** (`pyproject.toml`, `uv.lock`, `.python-version`), so its results can be reproduced exactly;
- it does **not import code from other sets**. If something from an earlier set is useful (a data simulator, a plotting helper), copy it into the new set's `src/experiment/` rather than sharing it;
- its data is either simulated by its own code or documented in its own `data/README.md`.

Duplicating a little code is an accepted cost: it means an old set keeps working even when a newer one changes.

## Layout of an experiment set

```
NN_<technique>/
├── README.md          focus of the set, questions, data, how to run, findings log
├── pyproject.toml     uv project for this set
├── uv.lock            committed, pins the exact environment
├── .python-version    Python version for this set
├── papers/            papers and reading list for the technique
├── src/experiment/    reusable modules, installed in the set's environment by uv sync
├── notebooks/         marimo notebooks, import from `experiment`
├── scripts/           only scripts meant to run on their own (if any)
├── data/              local data (gitignored, except its README)
└── results/           figures and tables produced by the experiments
```

## Starting a new experiment set

Work on each set in its own branch:

```bash
git checkout -b 03_double_ml
cp -r _template 03_double_ml
cd 03_double_ml
```

Then:

1. In `pyproject.toml`, set `name` and `description`, and adjust `.python-version` if needed. Keep the import name `experiment`: every set uses it, which is safe because sets never share an environment.
2. Add the libraries the set needs, e.g. `uv add econml`.
3. Run `uv sync` to create the environment and `uv.lock`, and commit the lock file.
4. Fill in the set's `README.md` with its focus.
5. Add the set to the index below.

Notebooks are [marimo](https://marimo.io) notebooks. To open them: `uv run marimo edit notebooks/` from inside the set's folder.

## Index of experiment sets

| Set | Technique | Focus |
|-----|-----------|-------|
| _none yet_ | | |

## License

GPL-3.0, see [LICENSE](LICENSE).
