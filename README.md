[Download the public survival package](DRAGON01_Public_Survival_20261117.zip). Extract the archive and run commands inside its DRAGON01_Public_Survival directory.

# DRAGON-01: public survival analysis

This is the public **survival-analysis subset** of the DRAGON-01 study. It supports KM reconstruction, candidate survival-model fitting, extrapolation, and Figures S2-S4. It is not the complete economic-evaluation package. The complete analysis code is available from the corresponding author upon reasonable request. Economic calculations, PSA draws and exact economic verification targets are not included in this public subset.

All supplied Python and R programs retain their original paths and bytes. Real survival inputs and adopted coefficients are supplied; this subset does not deliberately reduce numerical precision. Reconstructed endpoint-specific records are derived from published aggregate KM curves, not original patient-level data, and cannot be linked across OS and PFS.

## Install and run

Run from the directory containing this README (extract the ZIP first if downloaded as an archive). Python 3.13.9 was used with:

```shell
python -m pip install numpy==2.3.5 scipy==1.16.3 matplotlib==3.10.6
Rscript plots/install_dependencies.R
```

The retained R installer restores `renv.lock` into `.work/r-library`. The source records R 4.6.2; validation on this machine used R 4.6.1. A fresh-machine dependency restore was not separately tested.

Reconstruct all four marginal event datasets, refit 48 excess-hazard and 24 all-cause candidates, and compare AIC values with the supplied survival fits:

```shell
python -c "import sys; from pathlib import Path; sys.path.insert(0,'src'); import fit_analysis; p=Path('results/survival'); p.mkdir(parents=True,exist_ok=True); fit_analysis.run(p)"
```

Render the three figures from the supplied adopted-model plot tables:

```shell
Rscript plots/render_figures.R results
```

The unchanged R renderer skips figure directories that are absent. In this subset only S2, S3 and S4 are supplied. It can create PDF, SVG and PNG outputs; the distributed snapshot keeps only three final PDFs. Font availability can affect appearance.

The refitting command writes diagnostics and refitted coefficients to `results/survival/`. It does **not** replace the adopted coefficients or regenerate the plotting tables. The R figures use supplied frozen tables under `results/figure_data/`; matching plotting grids are under `data/plot_grids/`. The complete package contains the integrated figure-data generator. Do not interpret this subset as end-to-end regeneration of economic figures or results.

## Contents

| Directory/file | Contents |
|---|---|
| data/digitized, data/reconstructed | Published-curve inputs, risk counts and reconstructed marginal records |
| data/parameters | Background mortality and four necessary survival JSON files, in the formats read by unchanged programs |
| data/plot_grids | S2-S4 plotting inputs |
| src | Nine original Python survival and shared-function modules |
| plots | Three original R figure programs and unchanged dependency/rendering helpers |
| results | S2-S4 plotting tables and survival diagnostics, supplied as CSV |
| figures | Three final PDF examples |
| renv.lock | Original R dependency record required by the installer |
| MANIFEST.csv, NOTE.md | Inventory with hashes and scope/source notes |

The full original `run_analysis.py` imports the economic modules at startup and is therefore not included; use the command above for this subset. Shared cost-effectiveness summary functions are included as methods, without the study's economic inputs or calculated outcomes.

## Sources and availability

Clinical KM curves and counts: Yan et al., JAMA Oncology, https://doi.org/10.1001/jamaoncol.2026.1347 . Background mortality: United Nations World Population Prospects 2024, https://population.un.org/wpp/ . Cite the original sources and the study when reusing the numerical extracts; third-party materials retain their source-specific terms.

Preregistration: https://doi.org/10.17605/OSF.IO/HFEKA . The registration states that, at publication, analysis code and parameter tables permitted for sharing will be publicly available in an OSF-linked repository. This prepublication subset does not replace that publication-stage commitment.

## License for original analysis code


MIT License

Copyright (c) 2026 DRAGON-01 analysis contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
