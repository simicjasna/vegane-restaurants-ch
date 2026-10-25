# Vegane Restaurants in der Schweiz

Projekt im Modul Data Analytics (ZHAW, HS 2026), Gruppe 31
Team: Jasna Simic, Marija Radovanovic, Jaden Fisch

## Forschungsfrage
Welche Merkmale einer Gemeinde (z. B. Altersstruktur, Einkommen, Anteil Studierende) erklären die Dichte veganer Restaurants (Anzahl pro 1000 Einwohner) in der Schweiz?

## Datenquellen
- OpenStreetMap, abgefragt über die Overpass API (vegane Restaurants, Cafés, Fast-Food)
- BFS Gemeindedaten (Bevölkerung, Alter, Einkommen)
- Gemeindegrenzen (swisstopo)

## Struktur
- `notebooks/` Jupyter-Notebooks (nummeriert nach Arbeitsschritt)
- `data/raw/` Rohdaten, `data/processed/` bereinigte Daten und SQLite-Datenbank
- `figures/` Grafiken und Karten
- `docs/ai_usage_log.md` laufendes Protokoll zur KI-Nutzung

## Arbeitsschritte
1. Restaurantdaten holen (`01_vegane_restaurants_overpass.ipynb`)
2. Gemeindedaten und Grenzen holen, Restaurants den Gemeinden zuordnen, SQLite
3. Explorative Datenanalyse und Karten
4. Modellierung (Regression, k-Means, ANOVA) und Evaluation

## Setup
Python 3.10+, `pip install -r requirements.txt`, danach Jupyter starten (oder GitHub Codespaces verwenden).
