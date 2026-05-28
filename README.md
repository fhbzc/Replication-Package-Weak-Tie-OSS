# Replication Guide for `replicate_main.Rmd`

This is the replication package for our paper *[The Strength of Weak Ties among Open-Source Developers](https://arxiv.org/pdf/2411.05646)*.

`replicate_main.Rmd` is the main program for this project — every Table
and Figure reported in the paper is reproduced by running chunks inside
this single .Rmd. All paths in the .Rmd are relative, so set the working
directory to `R_Script/` (where `replicate_main.Rmd` lives) before
running. Intermediate artefacts are written to `./temp_data/`, and all
rendered PDFs to `./figure/`.

---

## Before you run

Download the input data from
[this Google Drive folder](https://drive.google.com/drive/folders/1SlzdtSlBv2kOvDpgZKHqs8ndQhwayX_P?usp=sharing),
**rename the downloaded folder to `data`**, and place it under `R_Script/`
so that the structure looks like `R_Script/data/...`. The .Rmd reads every
input file via `./data/...`, so the folder must be named exactly `data`.

---

## 0. Required packages

```r
tidyverse, corrr, ggcorrplot, car, fixest, broom, dplyr,
xtable, ggplot2, tidyr, reshape2, effsize
```

---

## Replication for Table 3

1. In `### load data and remove outliers`, set `core_post = ''` and `month_period = '12'`. Run the chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable not scaled, Replicating Table 3, Table 5, Table 13, Table 14, Table 15`.
5. The Table 3 columns come from `summary(m_degree_all_model)` and `summary(m_degree_dv_model)`.

## Replication for Table 5

1. In `### load data and remove outliers`, set `core_post = ''` and `month_period = '12'`. Run the chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable not scaled, Replicating Table 3, Table 5, Table 13, Table 14, Table 15`.
5. Table 5 columns come from `summary(m_diversity_dv_model)` and `summary(m_diversity_degree_dv_model)`.

## Replication for Table 6

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Variable co-variance, replicating Table 6`. The LaTeX correlation matrix is printed at the end via `xtable`.

## Replication for Table 7

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Direct variables in regression models, replicating Table 7`. The eleven models inside that chunk supply the Table 7 columns (scaled and raw versions, with and without degree controls, plus the combined models).

## Replication for Table 8

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. **Run Branch 1** (`### Branch 1: ... node2vec measurements ... for replicating Table 8`). This rewrites `atypicality`, `package_count`, and `core_dev_count` to their 1-year variants and overwrites `df_project_m_no_outlier` / `df_project_m_diversity_no_outlier`. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample) on the rewritten frames.
4. Run `### Outcome variable scaled, Replicating Table 8, Table 9, Table 10, Table 11`.
5. Table 8 reads from `summary(m_degree_all_model_scale)`, `summary(m_degree_dv_model_scale)`, `summary(m_diversity_dv_model_scale)`, `summary(m_diversity_degree_dv_model_scale)`.

## Replication for Table 9

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. **Run Branch 2** (`### Branch 2: ... network reshuffle measurements ... for replicating Table 9`). Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable scaled, Replicating Table 8, Table 9, Table 10, Table 11`.
5. Read the same four scaled-outcome models for Table 9 columns.

## Replication for Table 10

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4. (Table 10 uses the full-period default atypicality, scaled.)
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable scaled, Replicating Table 8, Table 9, Table 10, Table 11`.
5. Read the four scaled-outcome models for Table 10 columns.

## Replication for Table 11

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. **Run Branch 3** (`### Branch 3: ... full period ... network reshuffle ... for replicating Table 11`). Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable scaled, Replicating Table 8, Table 9, Table 10, Table 11`.
5. Read the four scaled-outcome models for Table 11 columns.

## Replication for Table 12

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Model with core developer fixed effects, Replicating Table 12`.
5. Inside that chunk:
   - `set.seed(42)` + the membership-sample block writes the reproducible 100-repo file to `./manual_sample/repo_core_author_membership_sample_100.csv`.
   - The four `feols(... | earliest_commit_year, ...)` models (`m_degree_dv_model_author_fe`, `m_diversity_dv_model_author_fe`, `m_diversity_degree_dv_model_author_fe`, `m_diversity_direct`) supply the Table 12 columns. Author dummies are estimated but filtered out of the printed coeftable; `fitstat()` reports R^2 / within-R^2.

## Replication for Table 13

1. Set `core_post = '_eighty'`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable not scaled, Replicating Table 3, Table 5, Table 13, Table 14, Table 15`.
5. Table 13 columns are read from the same four unscaled models, but estimated on the 6-month network sample.

## Replication for Table 14

1. Set `core_post = ''`, `month_period = '24'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable not scaled, Replicating Table 3, Table 5, Table 13, Table 14, Table 15`. Read the four unscaled models for Table 14.

## Replication for Table 15

1. Iteratively set (`core_post = '_eighty'`, `month_period = '6'`); (`core_post = '_eighty'`, `month_period = '24'`); (`core_post = ''`, `month_period = '6'`). Run the loading chunk .
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### Outcome variable not scaled, Replicating Table 3, Table 5, Table 13, Table 14, Table 15`. Read the four unscaled models for Table 15.

## Replication for Table 16

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### visualize figure 4, load` to merge `repo_property_novelty_awesome_list.csv` and create the `is_awesome` column on `df_project_m_diversity_no_outlier`.
5. Run `### generate Figure 4 and Table 16`. Table 16 = `summary(t_m)` (the OLS of atypicality on `is_awesome` + controls + year fixed effects).

## Replication for Figure 4

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### visualize figure 4, load` to merge `repo_property_novelty_awesome_list.csv` onto `df_project_m_diversity_no_outlier`.
5. Run `### generate Figure 4 and Table 16`. The violin plot is written to `./figure/awesome_atypicality.pdf`. The optional `### Compute Cohen's d` chunk reports the accompanying effect size; `t.test(...)` inside the figure chunk gives the two-sample t-statistic.

## Replication for Figure 5.a

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### generate temp data to replicate Figure 5.a` — fits the yearly OLS loop over 2008–2020 and writes `./temp_data/results_diversity_div_sample_yearly_cohort.csv`.
5. Run `### visualize figure 5.a` — the cohort plot is written to `./figure/diversity_div_yearly.pdf`. Years <= 2010 are dropped by `year_cut_off = 2010`.

## Replication for Figure 5.b

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### generate temp data to replicate Figure 5.b` — loops over `core_dev_count == 1..5` and writes `./temp_data/results_diversity_div_sample_core_cohort.csv`.
5. Run `### visualize figure 5.b` — the plot is written to `./figure/diversity_div_sample_core_cohort.pdf`.

## Replication for Figure 5.c

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. Skip Branch 4.
3. Run the PCA chunks (complete sample + diversity subsample).
4. Run `### generate temp data to replicate Figure 5.c` — fits one OLS on `owner_org == TRUE` and one on `owner_org == FALSE`, writes `./temp_data/results_div_org_cohort.csv`.
5. Run `### visualize figure 5.c` — the plot is written to `./figure/diversity_div_sample_org_cohort.pdf`.

## Replication for Figure 6

1. Set `core_post = ''`, `month_period = '12'`. Run the loading chunk.
2. Skip Branch 1. Skip Branch 2. Skip Branch 3. **Run Branch 4** (`### Branch 4: ... for replicating Figure 6`). This chunk both rewrites diversity = -1 when `outdegree_* < 2` and immediately writes the side-by-side histogram to `./figure/diversity_star_hist_compare.pdf` via the embedded `pdf(...)` / `dev.off()` block.
3. No further chunk is needed for Figure 6.
