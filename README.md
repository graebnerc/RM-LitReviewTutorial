# A mini systematic review in R

Companion project to the tutorial *A mini systematic review in eight steps*
(lecture 8 of *Theoretical and Empirical Research Methodology*, Europa-Universität
Flensburg, Fall 2026). It runs the tutorial's example search — the four-day
week and other forms of working time reduction — from start to finish in one
Quarto document, `report.qmd`.

## Reproduce the report

1. Open `RM-LitReviewTutorial.Rproj` in RStudio (or start R in this folder).
2. Install the package versions used here: `renv::restore()`.
3. Render the report: `quarto render report.qmd`, or the *Render* button.

No API key is needed for this: every search result the report uses is saved
in `data/`, and the report reads the saved results instead of sending the
searches again. You get exactly the numbers in the report, even though the
databases keep changing.

## Run the searches yourself

To repeat the searches with today's data, you need a free OpenAlex API key
(<https://openalex.org/settings/api>). Store it in your **user-level**
`.Renviron`, never in this project — `usethis::edit_r_environ()` opens the
file — as

    OPENALEX_KEY=your-key-here

restart R, and render with

    quarto render report.qmd -P refresh:true

This sends all searches again and overwrites the saved results in `data/`.

## What is where

| Path | Content |
|:-----|:--------|
| `report.qmd` | All code and explanations; renders to `report.html` |
| `data/*.rds` | Saved answers of OpenAlex, Crossref, EconBiz and EconStor |
| `data/retrieval_log.csv` | When each saved answer was retrieved |
| `data/screening_decisions.csv` | Screening decisions for the database records (made by an AI assistant as a demonstration, not checked by a person — see the report) |
| `data/snowball_decisions.csv` | The same for the records found by snowballing |
| `output/screening_sheet.csv` | Screening sheet built by the report — the starting point for the decisions |
| `output/prisma.svg`, `.png` | The flow diagram, once screening decisions exist |
| `renv.lock` | Package versions |
