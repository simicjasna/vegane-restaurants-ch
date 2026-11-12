# Requirements and Points Checklist (Group 31)

Working document. Tick off what is done and record **where the evidence is** (notebook, cell, figure).
The column "Evidence" is the basis for the appendix of the final PDF ("What we did to earn the points", with screenshots and code excerpts).

Status: `open` / `in progress` / `done`

## Minimum Requirements (9 points)

| No. | Requirement | Our plan | Evidence | Status |
|---|---|---|---|---|
| M1 | Data analytics project with module contents | Whole project | - | open |
| M2 | Own data collection via web API/scraping (no ready-made main dataset) | OpenStreetMap via the Overpass API | `notebooks/01_vegan_restaurants_overpass.ipynb`, `data/raw/vegan_restaurants_ch_raw.json` (712 records, retrieved 12.11.2026) | done |
| M3 | At least two sources, integration step documented (keys, joins, inconsistencies, records lost/gained) | OSM restaurants + BFS municipality data (+ swisstopo boundaries); record the number of records before and after each join | `notebooks/02_municipalities_and_assignment.ipynb`, `data/processed/integration_log.csv` (BFS features age and income still missing) | in progress |
| M4 | SQLite database with SQL queries from Python | Tables `restaurants`, `municipalities`, joined view | `data/processed/vegan_project.db`, SQL join in Notebook 02, section 5 | in progress |
| M5 | Extensive non-graphical and graphical EDA | Key figures, distributions, missing values, correlations, maps | - | open |
| M6 | Regression or classification, research question beyond pure prediction | Regression on the density per 1,000 inhabitants; comparison of urban and rural | - | open |
| M7 | Model evaluation with suitable metrics | R², adjusted R², RMSE, residual analysis, train/test or cross-validation | - | open |
| M8 | Correct interpretation of results and metrics | Written interpretation per model, limitations (completeness of OSM, proxy for students) | - | open |
| M9 | AI use documented (pros/cons, where it did not work) | Chapter "Use of AI" in the README, updated continuously (notes below) | README, chapter "Use of AI" | in progress |
| M10 | Material (data, notebooks) on Moodle | `materials_group_31.zip` | - | open |

## Additional Points (max. 6 points)

| No. | Additional criterion | Our plan | Evidence | Status |
|---|---|---|---|---|
| B1 | Creativity (beyond lectures and exercises) | Count models (Poisson / negative binomial with log population as offset) alongside OLS; separate analysis of "purely vegan" and "with vegan options"; comparison of urban and rural | - | open |
| B2 | PostgreSQL (or similar, not SQLite) with joins and aggregations from Python | Load the same tables into PostgreSQL (Docker, see course material), joins and aggregations via Python | - | open |
| B3 | Geodata integrated and visualized | Spatial join of restaurants to municipalities, choropleth map of the density, point map | Notebook 02 (spatial join, maps), `figures/map_density_overview.png` | in progress |
| B4 | Chi-square test, ANOVA or correlation (each with p-value) | ANOVA: density by municipality type; chi-square: municipality type x "has vegan restaurants"; Spearman correlation: density against features | - | open |
| B5 | k-means in addition to regression/classification | Group municipalities by socioeconomic features, compare density per cluster, choose k via silhouette score | - | open |
| B6 | Code in a public GitHub repository, URL in the presentation | https://github.com/simicjasna/vegane-restaurants-ch | Repository | done |

## Video Presentation (max. 7 points)

- Length: 3 students x 5 min = **15 minutes**
- Must contain: structure, topic, content, free speech, slide quality, **reflection on AI use** (tools, tasks, pros/cons, what did not work), time keeping
- Do not just scroll through notebooks; show code only if it improves understanding

## Submission on Moodle (one person per group, group number in the file name)

- [ ] `video_recording_group_31.mp4`
- [ ] `materials_group_31.zip` (data and notebooks)
- [ ] `presentation_group_31.pdf` (title and full names, introduction, materials and methods, results and discussion, conclusions, AI reflection, **appendix with evidence for the points**)
- [ ] PDF of the concept presentation (same deadline); the talk takes place on site from week 10

Deadline: 10 January 2027, 23:59 (Moodle says "11 January 2026" in one place, which is a typo).

## Next Steps (as of 12.11.2026)

- [x] Collected restaurant data via the Overpass API (712 records) and stored it in SQLite
- [x] Integrated municipality boundaries and population (swisstopo), compared the set of municipalities with the BFS directory (2110 municipalities, 0 mismatches)
- [x] Spatial join: 712 of 712 restaurants assigned to a municipality, first map created
- [x] Switched code, files, branches and commits to English (convention in the README)
- [ ] Obtain explanatory variables ourselves (preferably via code/API, document source and retrieval date): age (share aged 20-29), income, urban/rural typology
- [ ] Document sources in the README: name, link, retrieval date, access (API or download), columns used
- [ ] Print retrieval date and OSM data status (`osm3s`) in Notebook 01
- [ ] EDA (distributions, relationships, maps) and models (regression, count models, k-means, ANOVA, chi-square, correlation)
- [ ] Set up the PostgreSQL variant (Docker)
- [ ] Slides for the concept presentation (slides 5 to 8 with real numbers from `integration_log.csv` and the map)

## Notes for the README Chapter "Use of AI"

The file `docs/ai_usage_log.md` no longer exists in the current `main`; the chapter is in the README. These entries belong there:

- 25.10.2026, Claude: Evaluated the project idea and drafted the notebook for the Overpass query. Did not work: The notebook could not be tested directly; it had to be run in our own Python environment.
- 10.11.2026, Claude: Wrote Notebook 02 (load municipality boundaries, compare the set of municipalities, spatial join, SQLite, first map). Worked: The join and comparison ran on the first attempt (709 of 709 restaurants assigned, after re-retrieval 712 of 712). Did not work: Some links to data sources were wrong (the datasets only covered Valais or Fribourg) and had to be checked in the browser.
- 12.11.2026, Claude: Switched notebooks, column names and file names to English and re-ran Notebook 02. Did not work: The SQLite file could not be written in the connected folder ("disk I/O error"), so the notebook was run in a copy and the results were copied back. When renaming, the `git rm` of the old files was also missing, which was only noticed during a check.
