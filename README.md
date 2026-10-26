# Replication notebook: *When Artificial Intelligence Makes Entrepreneurial Imagination Programmable*

Erik Lang and Nicolai J. Foss

This repository contains the notebook behind our comment on Csaszar (2026), [*Conceptual Search: A Generative View of Entrepreneurial Imagination*](https://doi.org/10.1002/sej.70055) (*Strategic Entrepreneurship Journal*). The notebook recomputes the paper's headline numbers from Csaszar's released records and documents the three points of the comment's Section 2:

1. **Heterogeneity inside one search (Section 2.1).** The 15 concepts of global search's final generation are, with two exceptions, variants of one concept. Notebook Section 3, and the optional Section 5 for semantic distances.
2. **The same model as generator, selector and judge (Section 2.2).** The paper's two robustness judges agree with its main judge on the 30 originals, the real Kickstarter campaigns of the reference set, but place most of the gain in recombination rather than in polishing. Notebook Sections 2, 4 and 6.
3. **What the model knows (Section 2.3).** On the 30 originals, the length of the texts the judges read tracks the money raised as well as the main judge's ranking does. Notebook Sections 2 and 6.

## Data

The notebook uses Csaszar's files from [github.com/fcsaszar/conceptual-search](https://github.com/fcsaszar/conceptual-search) at commit `4244604` (21 September 2026), the repository's only commit as of 26 October 2026. On the first run it downloads them into `csaszar_repo/` and checks each against the repository's git hash. The files are not included here.

## Running the notebook

Create an environment of your own and install the pinned packages into it:

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt jupyterlab
```

On Windows, activate the environment with `.venv\Scripts\activate`. Open `csaszar2026_reanalysis.ipynb` in Jupyter and run all cells. The first run needs internet access to download Csaszar's files. The default run takes about a minute and makes no model calls.

Section 5 reproduces the paper's semantic distances with its BGE-M3 embedding model. The comment's distances between population members, and from the withheld originals (the 15 not used as seeds) to their nearest seed, come from this section. To run it, install the two packages below and set `RUN_EMBEDDINGS = True` in the first code cell. It downloads about 2.3 GB and takes about three more minutes on a laptop CPU.

```
pip install sentence-transformers==5.6.0 torch==2.13.0
```

Tested with Python 3.13.

## Files

- `csaszar2026_reanalysis.ipynb`: the notebook, with its saved outputs.
- `figures/`: the figures the notebook draws. `figure1_identical_sections.png` and `figure2_three_judges.png` are Figures 1 and 2 of the comment; `supplementary_convergence.png` is not in the comment. With `RUN_EMBEDDINGS = True`, Section 5 adds `supplementary_figure1_with_distances.png`, Figure 1 with a second panel for the semantic distances.
- `requirements.txt`: the package versions used.
- `CITATION.cff`: how to cite this repository.

## Citation

Please cite this repository as described in `CITATION.cff`, and the paper whose records it analyses:

Csaszar, F. A. (2026). Conceptual search: A generative view of entrepreneurial imagination. *Strategic Entrepreneurship Journal*. https://doi.org/10.1002/sej.70055

## License

The code in this repository is released under the MIT license (`LICENSE`). The notebook's saved outputs reproduce code and data from Csaszar's repository, which is released under the MIT license; its notice is in `THIRD_PARTY_NOTICES.md`.
