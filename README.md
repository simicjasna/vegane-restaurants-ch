# Density of Vegan Restaurants in Swiss Municipalities

<img src="docs/title-image.png" alt="Map of Switzerland with vegan restaurants and a close-up of a municipality" width="80%">

Project in the module **Data Analytics** (Bachelor Business Information Technology, ZHAW).

| | |
| :----- | :----- |
| **Group** | 31 |
| **Students** | Jasna Simic, Marija Radovanovic, Jaden Fisch |

# Table of Contents
- [Introduction](#introduction)
    - [Background and Problem Statement](#background-and-problem-statement)
    - [Goal and Research Question](#goal-and-research-question)
- [Project Management](#project-management)
    - [Iterative Process Model](#iterative-process-model)
    - [Git Structure](#git-structure)
- [Minimum Requirements](#minimum-requirements)
    - [Data Collection](#data-collection)
    - [Data Preparation and Integration](#data-preparation-and-integration)
    - [Data Storage](#data-storage)
    - [Exploratory Data Analysis](#exploratory-data-analysis)
    - [Modeling and Evaluation](#modeling-and-evaluation)
- [Additional Requirements](#additional-requirements)
    - [Creativity of the Implementation](#creativity-of-the-implementation)
    - [PostgreSQL Database](#postgresql-database)
    - [Geographic Data](#geographic-data)
    - [Statistical Tests (Chi-Square, ANOVA, Correlation)](#statistical-tests-chi-square-anova-correlation)
    - [k-Means Clustering](#k-means-clustering)
    - [GitHub Repository](#github-repository)
- [Results and Discussion](#results-and-discussion)
- [Conclusions](#conclusions)
- [Use of AI](#use-of-ai)
- [Appendix](#appendix)
    - [References](#references)

# Introduction

## Background and Problem Statement

Vegan food has become more visible in the restaurant sector in recent years. However, restaurants with a vegan offering are not evenly distributed across Switzerland. The choice is probably large in big cities and university towns, while many small and rural municipalities offer hardly anything.

Directories and maps show where vegan restaurants are, but they do not explain **why** the offering is denser in some municipalities than in others. It is unclear which characteristics of a municipality, for example its age structure, income or share of students, are related to a dense vegan offering.

This knowledge is useful for several groups:

- **Restaurateurs and founders:** for choosing the location of a new business.
- **Municipalities and tourism organizations:** to compare their own offering with others.
- **Consumers:** to see in which regions the choice is large or small.

## Goal and Research Question

We want to investigate where the vegan offering in Switzerland is largest and which characteristics of a municipality explain this. For this purpose, we calculate the **density of vegan restaurants** (number per 1,000 inhabitants) for each municipality. A municipality is a political municipality according to the BFS municipality directory. We then examine which municipality characteristics are related to this density and compare groups of municipalities (e.g. urban and rural municipalities).

> [!IMPORTANT]
> **Research question:** Which characteristics of a municipality (e.g. age structure, income, share of students) explain the density of vegan restaurants (number per 1,000 inhabitants) in Switzerland?

**Expected results**

The following assumptions are made before the analysis and concern the characteristics we expect first. The characteristics named are examples; we also examine further municipality characteristics from the BFS data (e.g. municipality type, language region or population size). Which characteristics we finally use is documented in the chapter [Data Preparation and Integration](#data-preparation-and-integration). Whether the assumptions are confirmed is shown in the chapter [Results and Discussion](#results-and-discussion).

- Municipalities with more young people and students have a higher density, because these groups ask for vegan offerings more often.
- Municipalities with higher income have a higher density, because higher purchasing power makes specialized offerings more feasible.
- Urban municipalities have a higher density on average than rural ones, because a larger customer base can support niche offerings.

# Project Management

## Iterative Process Model

We work as a team of three following an iterative process model that covers the whole collaboration. Work packages are distributed per category and implemented in the corresponding branch. After the team discussion, a new iteration begins.

<img src="docs/iterative-process-model-da.png" alt="Iterative process model of the project" width="1000">

| Step | Description |
| :----- | :----- |
| **1. Extract requirements** | Read the project assignment and grading criteria and note what is required next. |
| **2. Planning** | Define goals, order and schedule for the next iteration. |
| **3. Distribute work packages** | Define tasks by category and split them among the three people. |
| **4. Implementation in the corresponding branch** | Each person works on their category in a separate branch. |
| **5. Check usefulness** | The result is checked against the requirements, the code is tested and the results are reviewed. |
| **6. Decision** | The team decides whether the branch is merged or reworked. |
| **7. Merge into main** | The reviewed branch is merged into `main`. |
| **8. Discuss status in the team** | Short meeting about the current status and the next tasks. Then the next iteration begins. |

## Git Structure

### Branches

The module is held in English, therefore branches, commit messages, code and file names are in English. Every branch starts with the **category** (first word, lowercase). It is followed by a short **extension** joined with hyphens that describes what the branch is about: `category-topic`.

| Category (first word) | Area | Examples |
| :----- | :----- | :----- |
| `readme` | README and documentation | `readme-checklist`, `readme-conventions` |
| `presentation` | Presentation and video | `presentation-concept-slides` |
| `data` | Data collection (API, scraping) | `data-overpass`, `data-income` |
| `geodata` | Geodata and spatial assignment | `geodata-spatial-join` |
| `database` | Database (SQLite, PostgreSQL) | `database-sqlite`, `database-postgresql` |
| `eda` | Exploratory data analysis | `eda-distributions`, `eda-correlations` |
| `modeling` | Modeling and evaluation | `modeling-regression`, `modeling-poisson` |
| `analysis` | Additional analyses (bonus) | `analysis-kmeans`, `analysis-anova` |

**Rules**

- The first word is always the category, the extension describes the content (`category-topic`).
- Lowercase, separate words with hyphens, no umlauts, preferably 1 to 3 words for the extension.
- A branch belongs to exactly one category and one clearly defined topic.
- Because of the iterative process, a category is worked on several times. Each new round therefore gets a new branch with a different extension (e.g. `eda-distributions`, later `eda-after-modeling`).
- The branch is deleted after the merge.

> [!TIP]
> The prefix shows in the history at a glance which area a change belongs to. The extension shows what exactly it was about. This keeps branches unambiguous across several iterations.

### Commits

A commit message has the format `type(scope): what was done` and is written in English.

- **type**: kind of change (see table).
- **scope**: category from the branch convention (`readme`, `presentation`, `data`, `geodata`, `database`, `eda`, `modeling`, `analysis`). It matches the first word of the branch.
- **description**: short and concrete, in past tense, without a period at the end.

| Type | Usage |
| :----- | :----- |
| `feat` | New function, new analysis step, new notebook |
| `data` | Data added or updated |
| `docs` | Documentation (README, checklist, comments) |
| `fix` | Bug fixed |
| `polish` | Improved, cleaned up, translated or restructured, without a new function |

Examples:

```
feat(data): created Overpass query for vegan restaurants
data(geodata): added municipality boundaries and BFS directory
feat(geodata): assigned restaurants to municipalities with a spatial join
feat(database): created SQLite database with restaurants and municipalities
docs(readme): updated branch and commit conventions
fix(eda): corrected missing values in population
```

For several related changes, the details are listed after a colon:

```
feat(data): created Overpass query, saved raw data as JSON, added retry over two endpoints
```

# Minimum Requirements

This chapter records the technical foundation of our investigation. It follows the path of the data, from collection through preparation and storage to analysis and model. In the paper it corresponds to the part "Materials and Methods". Each section explains what we did and why, so that the results remain traceable.

## Data Collection

> Description of how the data is collected by ourselves (web scraping and/or web API): which interface, which query, which scope. Ready-made datasets (e.g. from Kaggle) do not count as a primary source. With references to the relevant code locations.

## Data Preparation and Integration

The following two data sources are used:

1. **OpenStreetMap** via the Overpass API (self-collected data)
2. **BFS municipality data** (Federal Statistical Office)

## Data Storage

> Description of the SQLite database (tables, schema, relations) and of the SQL queries from Python. With references to the relevant code locations.

## Exploratory Data Analysis

> Description of the non-graphical and graphical EDA: key figures, distributions, missing values, relationships between the variables and the most important plots. Every figure is labeled and given a source.

## Modeling and Evaluation

> Description of the target variable, the explanatory variables and the chosen model (regression or classification) including the reasoning. Evaluation with suitable metrics (e.g. R², RMSE, accuracy, precision, recall) and correct interpretation of the results. Explanation of how the research question goes beyond pure prediction.

# Additional Requirements

The additional requirements make extra points possible. For each additional requirement, we document how it was implemented.

## Creativity of the Implementation

> Description of what goes beyond the content of the lectures and exercises (e.g. own data sources, special analyses or visualizations).

## PostgreSQL Database

> Description of the use of a PostgreSQL or similar database (not SQLite) with SQL joins and aggregations from Python. With references to the relevant code locations.

## Geographic Data

> Description of which geographic data was integrated and how it was visualized (e.g. map of the density per municipality).

## Statistical Tests (Chi-Square, ANOVA, Correlation)

> Description of the test used (chi-square test, ANOVA or correlation analysis), the question behind it and the result. Every test must include a p-value.

## k-Means Clustering

> Description of the clustering in addition to the regression or classification model: features used, number of clusters, interpretation of the clusters.

## GitHub Repository

> Link to the public GitHub repository with the code: https://github.com/simicjasna/vegane-restaurants-ch. The URL must also be given in the presentation.

# Results and Discussion

> Presentation of the results of the data integration, the EDA and the models including interpretation of the metrics. In the discussion the results are put into context: relation to the research question and to the expected results as well as limitations of the analysis.

# Conclusions

> Answer to the research question in a few sentences, conclusion of the project and possible next steps.

# Use of AI

> Reflection on the use of AI for code and presentation: which tools were used for which tasks, which advantages and disadvantages were found, and where it did not work with the help of AI.

# Appendix

## References

| Source | Usage | Link |
| :----- | :----- | :----- |
| OpenStreetMap (Overpass API) | Vegan restaurants | https://www.openstreetmap.org |
| Federal Statistical Office (BFS) | Municipality data, municipality directory | https://www.bfs.admin.ch |
| swisstopo (swissBOUNDARIES3D) | Municipality boundaries and population | https://www.swisstopo.admin.ch/en/landscape-model-swissboundaries3d |
