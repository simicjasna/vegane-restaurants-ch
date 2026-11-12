# Anforderungs- und Punkte-Checkliste (Gruppe 31)

Arbeitsdokument. Erledigtes abhaken und festhalten, **wo der Beleg liegt** (Notebook, Zelle, Abbildung).
Die Spalte «Beleg» ist die Grundlage für den Anhang des finalen PDFs («Was wir getan haben, um die Punkte zu erreichen», mit Screenshots und Code-Ausschnitten).

Status: `offen` / `in Arbeit` / `erledigt`

## Minimalanforderungen (9 Punkte)

| Nr. | Anforderung | Unser Plan | Beleg | Status |
|---|---|---|---|---|
| M1 | Data-Analytics-Projekt mit Modulinhalten | Gesamtes Projekt | - | offen |
| M2 | Eigene Datenerhebung per Web-API/Scraping (kein fertiger Hauptdatensatz) | OpenStreetMap über die Overpass API | `notebooks/01_vegan_restaurants_overpass.ipynb`, `data/raw/vegan_restaurants_ch_raw.json` (712 Einträge, Abruf 12.11.2026) | erledigt |
| M3 | Mindestens zwei Quellen, Integrationsschritt dokumentiert (Schlüssel, Joins, Inkonsistenzen, verlorene/gewonnene Datensätze) | OSM-Restaurants + BFS-Gemeindedaten (+ swisstopo-Grenzen); Anzahl Datensätze vor und nach jedem Join festhalten | `notebooks/02_municipalities_and_assignment.ipynb`, `data/processed/integration_log.csv` (BFS-Merkmale Alter und Einkommen fehlen noch) | in Arbeit |
| M4 | SQLite-Datenbank mit SQL-Abfragen aus Python | Tabellen `restaurants`, `municipalities`, verknüpfte Sicht | `data/processed/vegan_project.db`, SQL-Join in Notebook 02, Abschnitt 5 | in Arbeit |
| M5 | Umfangreiche nicht-grafische und grafische EDA | Kennzahlen, Verteilungen, fehlende Werte, Korrelationen, Karten | - | offen |
| M6 | Regression oder Klassifikation, Forschungsfrage über reine Vorhersage hinaus | Regression auf die Dichte pro 1000 Einwohner; Vergleich Stadt und Land | - | offen |
| M7 | Modellevaluation mit geeigneten Gütemassen | R², adjustiertes R², RMSE, Residuenanalyse, Train/Test oder Kreuzvalidierung | - | offen |
| M8 | Korrekte Interpretation der Resultate und Gütemasse | Schriftliche Interpretation je Modell, Grenzen (Vollständigkeit von OSM, Ersatzwert für Studierende) | - | offen |
| M9 | KI-Nutzung dokumentiert (Vor-/Nachteile, wo es nicht funktioniert hat) | Kapitel «Einsatz von KI» im README, laufend ergänzt (Notizen unten) | README, Kapitel «Einsatz von KI» | in Arbeit |
| M10 | Material (Daten, Notebooks) auf Moodle | `materials_group_31.zip` | - | offen |

## Zusatzpunkte (max. 6 Punkte)

| Nr. | Zusatzkriterium | Unser Plan | Beleg | Status |
|---|---|---|---|---|
| B1 | Kreativität (über Vorlesungen und Übungen hinaus) | Zählmodelle (Poisson / negative Binomial mit log-Einwohner als Offset) neben OLS; getrennte Analyse «rein vegan» und «mit veganem Angebot»; Vergleich Stadt und Land | - | offen |
| B2 | PostgreSQL (oder ähnlich, nicht SQLite) mit Joins und Aggregationen aus Python | Dieselben Tabellen in PostgreSQL laden (Docker, siehe Kursmaterial), Joins und Aggregationen über Python | - | offen |
| B3 | Geodaten integriert und visualisiert | Räumlicher Join Restaurants zu Gemeinden, Choroplethenkarte der Dichte, Punktkarte | Notebook 02 (räumlicher Join, Karten), `figures/map_density_overview.png` | in Arbeit |
| B4 | Chi-Quadrat-Test, ANOVA oder Korrelation (jeweils mit p-Wert) | ANOVA: Dichte nach Gemeindetyp; Chi-Quadrat: Gemeindetyp x «hat vegane Restaurants»; Spearman-Korrelation: Dichte gegen Merkmale | - | offen |
| B5 | k-Means zusätzlich zu Regression/Klassifikation | Gemeinden nach sozioökonomischen Merkmalen gruppieren, Dichte je Cluster vergleichen, k über Silhouette-Wert wählen | - | offen |
| B6 | Code in öffentlichem GitHub-Repository, URL in der Präsentation | https://github.com/simicjasna/vegane-restaurants-ch | Repository | erledigt |

## Videopräsentation (max. 7 Punkte)

- Länge: 3 Studierende x 5 Min. = **15 Minuten**
- Muss enthalten: Struktur, Thema, Inhalt, freie Sprache, Folienqualität, **Reflexion der KI-Nutzung** (Tools, Aufgaben, Vor-/Nachteile, was nicht funktioniert hat), Zeiteinhaltung
- Nicht einfach durch Notebooks scrollen; Code nur zeigen, wenn er das Verständnis verbessert

## Abgabe auf Moodle (eine Person pro Gruppe, Gruppennummer im Dateinamen)

- [ ] `video_recording_group_31.mp4`
- [ ] `materials_group_31.zip` (Daten und Notebooks)
- [ ] `presentation_group_31.pdf` (Titel und vollständige Namen, Einleitung, Material und Methoden, Resultate und Diskussion, Schlussfolgerungen, KI-Reflexion, **Anhang mit Belegen für die Punkte**)
- [ ] PDF der Konzeptpräsentation (gleiche Frist); der Vortrag findet ab Woche 10 vor Ort statt

Frist: 10. Januar 2027, 23:59 Uhr (in Moodle steht an einer Stelle «11. Januar 2026», das ist ein Tippfehler).

## Nächste Schritte (Stand 12.11.2026)

- [x] Restaurantdaten per Overpass API erhoben (712 Einträge) und in SQLite gespeichert
- [x] Gemeindegrenzen und Einwohnerzahlen (swisstopo) eingebunden, Gemeindestand mit BFS-Verzeichnis abgeglichen (2110 Gemeinden, 0 Abweichungen)
- [x] Räumlicher Join: 712 von 712 Restaurants einer Gemeinde zugeordnet, erste Karte erstellt
- [x] Code, Dateien, Branches und Commits auf Englisch umgestellt (Konvention im README)
- [ ] Erklärvariablen selbst beschaffen (möglichst per Code/API, Quelle und Abrufdatum dokumentieren): Alter (Anteil 20-29 Jahre), Einkommen, Stadt/Land-Typologie
- [ ] Quellen im README dokumentieren: Name, Link, Abrufdatum, Bezug (API oder Download), verwendete Spalten
- [ ] Abrufdatum und OSM-Datenstand (`osm3s`) in Notebook 01 ausgeben
- [ ] EDA (Verteilungen, Zusammenhänge, Karten) und Modelle (Regression, Zählmodelle, k-Means, ANOVA, Chi-Quadrat, Korrelation)
- [ ] PostgreSQL-Variante (Docker) aufsetzen
- [ ] Folien für die Konzeptpräsentation (Folien 5 bis 8 mit echten Zahlen aus `integration_log.csv` und der Karte)

## Notizen für das README-Kapitel «Einsatz von KI»

Die Datei `docs/ai_usage_log.md` gibt es im aktuellen `main` nicht mehr, das Kapitel steht im README. Diese Einträge gehören dort hinein:

- 25.10.2026, Claude: Projektidee bewertet und Notebook für die Overpass-Abfrage entworfen. Nicht funktioniert: Das Notebook konnte nicht direkt getestet werden, es musste im eigenen Python ausgeführt werden.
- 10.11.2026, Claude: Notebook 02 geschrieben (Gemeindegrenzen laden, Gemeindestand abgleichen, räumlicher Join, SQLite, erste Karte). Funktioniert: Join und Abgleich liefen im ersten Versuch (709 von 709 Restaurants zugeordnet, nach erneutem Abruf 712 von 712). Nicht funktioniert: Einige Links zu Datenquellen waren falsch (Datensätze galten nur für Wallis bzw. Freiburg) und mussten im Browser geprüft werden.
- 12.11.2026, Claude: Notebooks, Spalten- und Dateinamen auf Englisch umgestellt, Notebook 02 neu ausgeführt. Nicht funktioniert: Die SQLite-Datei liess sich im verbundenen Ordner nicht beschreiben («disk I/O error»), deshalb wurde das Notebook in einer Kopie ausgeführt und die Ergebnisse zurückkopiert. Beim Umbenennen fehlte ausserdem das `git rm` der alten Dateien, was erst bei der Kontrolle auffiel.
