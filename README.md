# Vegan Restaurants in Switzerland

Project for the Data Analytics module (ZHAW, autumn semester 2026), Group 31
Team: Jasna Simic, Marija Radovanovic, Jaden Fisch

## Research question
Which characteristics of a municipality (e.g. age structure, income, share of students) explain the density of vegan restaurants (number per 1,000 inhabitants) in Switzerland?

## Data sources
- OpenStreetMap, queried via the Overpass API (vegan restaurants, cafés, fast food)
- Federal Statistical Office (BFS) municipality data (population, age, income)
- Municipality boundaries (swisstopo)

## Structure
- `notebooks/` Jupyter notebooks (numbered by work step)
- `data/raw/` raw data, `data/processed/` cleaned data and the SQLite database
- `figures/` charts and maps
- `docs/ai_usage_log.md` running log of AI usage

## Work steps
1. Retrieve restaurant data (`01_vegan_restaurants_overpass.ipynb`)
2. Retrieve municipality data and boundaries, assign restaurants to municipalities, store in SQLite
3. Exploratory data analysis and maps
4. Modelling (regression, k-means, ANOVA) and evaluation

## Setup
Python 3.10+, `pip install -r requirements.txt`, then start Jupyter (or use GitHub Codespaces).
