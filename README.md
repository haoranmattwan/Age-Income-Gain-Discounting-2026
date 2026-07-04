# Age, Income, and Reward Discounting Across the Adult Lifespan

[![DOI](https://img.shields.io/badge/DOI-10.3389%2Ffpsyg.2026.1765142-0A7BBB)](https://doi.org/10.3389/fpsyg.2026.1765142)
[![R](https://img.shields.io/badge/R-4.2.1%2B-276DC3)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Quarto-reproducible%20analysis-39729E)](https://quarto.org/)
[![License: MIT](https://img.shields.io/badge/code-MIT-yellow.svg)](LICENSE.md)
[![License: CC BY 4.0](https://img.shields.io/badge/materials-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Reproducible materials for:

> Wan, H., Myerson, J., Green, L., Strube, M. J., & Hale, S. (2026). Age, income, and the discounting of delayed and probabilistic rewards. *Frontiers in Psychology, 17*, 1765142. <https://doi.org/10.3389/fpsyg.2026.1765142>

## Research overview

Across two parallel studies, adults aged 20 to 80 completed adjusting-amount tasks involving delayed or probabilistic gains of $150, $2,500, and $30,000. The project tests whether age-related differences in reward discounting depend on household income. The published analyses show domain-specific age trajectories and income-dependent age effects: delay discounting becomes shallower with age, whereas probability discounting follows a nonlinear trajectory, with both patterns attenuated at higher income levels.

## Repository contents

- [`analysis/lifespan-gain-analysis.qmd`](analysis/lifespan-gain-analysis.qmd): end-to-end Quarto analysis using the public workbook format.
- [`_quarto.yml`](_quarto.yml): project configuration that runs code from the repository root.
- [`paper/Wan-et-al-2026.pdf`](paper/Wan-et-al-2026.pdf): published open-access article.
- [`poster/ABAI-2023-lifespan-poster.pptx`](poster/ABAI-2023-lifespan-poster.pptx): ABAI poster source.
- [`data/README.md`](data/README.md): data access, schema, and placement instructions.
- [`CITATION.cff`](CITATION.cff): machine-readable citation metadata.

The private development archive, original recruitment exports, manuscript drafts, literature library, caches, model objects, and rendered outputs are intentionally excluded from version control.

## Data access

The analysis data are available from the [supplementary-material section of the published article](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2026.1765142/full#supplementary-material). Download the publication workbook, name it `Supplementary Data.xlsx`, and place it in `data/`.

The workbook differs from the combined raw export used during development:

- Study 1 and Study 2 are separate sheets.
- Reward amount is already recorded in dollars (`150`, `2500`, `30000`).
- Education is already recorded in years (`5`, `12`, `14`, `16`, `18`).
- Study 2 probability is recorded as a percentage (`5`, `20`, `50`, `80`, `95`); the analysis converts it to odds against.
- Attention-check variables are not included because the workbook contains the final analytic samples.

## Reproduce the analysis

1. Install R and Quarto.
2. Install the required R packages:

   ```r
   install.packages(c("dplyr", "tidyr", "readxl", "ggplot2", "glmmTMB", "knitr"))
   ```

3. Place the supplementary workbook at `data/Supplementary Data.xlsx`.
4. Render from the repository root:

   ```bash
   quarto render analysis/lifespan-gain-analysis.qmd
   ```

The default analysis uses the publication's 5,000 participant-level bootstrap samples and may take substantial time. For a smoke test:

```bash
quarto render analysis/lifespan-gain-analysis.qmd \
  -P bootstrap_iterations:20 \
  -P bootstrap_cores:2
```

Bootstrap objects are cached in `Analysis/bootstrap_outputs/` and are not tracked by Git. Set `run_bootstrap:false` to check data preparation and model fitting without bootstrap inference.

## Reproducibility decisions

The consolidated analysis preserves the final published model specifications while making the workflow safer and easier to audit:

- portable project-relative paths replace `setwd()`;
- the public workbook is validated before analysis;
- AuC construction is explicit and tested against expected domains;
- each resampled participant cluster receives a new identifier;
- bootstrap seeds and convergence checks are explicit;
- generated files and cached model objects remain outside version control.

## Licenses

Code is released under the MIT License. The article, poster, documentation, and other non-code materials are released under CC BY 4.0 unless a file states otherwise. Data use remains subject to the terms specified with the article's supplementary material and the study's ethical approvals.

## Suggested repository metadata

**Description:** Reproducible R/Quarto materials for Wan et al. (2026), examining how age and household income jointly shape delay and probability discounting across reward magnitudes using multilevel beta regression and participant-level bootstrap inference.

**Topics:** `r`, `quarto`, `open-science`, `reproducible-research`, `delay-discounting`, `probability-discounting`, `intertemporal-choice`, `risky-choice`, `aging`, `income`, `decision-making`, `behavioral-economics`, `multilevel-models`, `beta-regression`
