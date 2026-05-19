## Cursor Cloud specific instructions

This repository contains two files:

1. **`Intro_AI_frame-0510-DH.tex`** — A LaTeX thesis chapter (Chinese-language, condensed matter physics). It references `\chapter{}` from a parent `main.tex` that is **not** in this repo, so it cannot be compiled standalone.
2. **`sudden silence.ipynb`** — A Jupyter notebook running a numerical simulation (Ising-like model for "sudden silence" phenomenon). Requires Python 3 with `numpy`, `matplotlib`, and `jupyter`/`ipykernel`.

### Running the notebook

```bash
# Execute all cells (note: cells beyond the first have pre-existing bugs)
python3 -m jupyter nbconvert --to notebook --execute "sudden silence.ipynb" --output executed.ipynb

# Or run just the first cell programmatically via nbclient
python3 -c "
import nbformat
from nbclient import NotebookClient
nb = nbformat.read('sudden silence.ipynb', as_version=4)
first = nbformat.v4.new_notebook(); first.cells = [nb.cells[0]]
NotebookClient(first, timeout=120).execute()
print('OK')
"
```

### Known issues

- Only the **first cell** of `sudden silence.ipynb` runs without errors. Later cells contain pre-existing `TypeError` bugs (e.g., passing a non-scalar to `math.log`).
- The `.tex` file cannot be compiled without the full thesis template (`main.tex` and associated class/style files).
