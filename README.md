# Winterstromlücke Schweiz 2050

**Interaktive Parameteranalyse der Studie Kelevitz et al., *Energies* 2025**

[![Lizenz: MIT](https://img.shields.io/badge/Lizenz-MIT-blue.svg)](LICENSE)
[![Lizenz: CC BY 4.0](https://img.shields.io/badge/Daten%20%26%20Docs-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Studie: DOI](https://img.shields.io/badge/DOI-10.3390%2Fen18215601-green.svg)](https://doi.org/10.3390/en18215601)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-orange.svg)](https://raffa3l.github.io/Winterstromluecke-2050)

---

## Über diese Anwendung

Diese Web-App veranschaulicht, wie Massnahmen im Schweizer Gebäudesektor die projizierte **Winterstromlücke von 2050** beeinflussen. Vier Parameter können interaktiv variiert werden; das Simulationsergebnis aktualisiert sich in Echtzeit.

[Live-Demo](https://raffa3l.github.io/Winterstromluecke-2050)

### Studienbasis

> Kelevitz K., Haller M., Frommelt M., Meier B. —  
> *Influence of Scenarios for Space Heating and Domestic Hot Water in Buildings on the Winter Electricity Demand of Switzerland in 2050.*  
> Institut für Solartechnik SPF, Ostschweizer Fachhochschule OST, Rapperswil.  
> **Energies 2025, 18, 5601.** https://doi.org/10.3390/en18215601

Die Studie erweitert das Energiesystem-Werkzeug **PowerCheck** (https://powercheck.ch) um ein Bottom-up-Modell des Schweizer Gebäudeparks (60 Kategorien, stündliche Auflösung, GWR-Datenbasis). Zwölf Szenarien variieren vier Parameter und quantifizieren deren Einfluss auf die saisonale Stromlücke. Ausgangspunkt: **Energieperspektiven 2050+** des Bundesamts für Energie (BFE).

---

## Funktionen

- **Vier Hebel** in den Stufen der Studie:
  1. Sanierungsrate Gebäudehülle (0.5 / 1.1 / 1.5 / 2.0 %/a)
  2. Wärmerückgewinnung Warmwasser (0 / 20 / 50 %)
  3. Anteil Erdsonden-Wärmepumpen (20 / 50 / 80 %)
  4. Erwärmung gegenüber Referenzwetter (+0 / +1 / +2 / +3 K)
- **Kennzahlen:** Winterstromlücke, Strom für Heizung und Warmwasser (Jahr und Januar), Wärmebedarf. Jede Zahl ist als *Studienwert* oder *Modellschätzung* gekennzeichnet.
- **Alle 13 Studienszenarien** im Vergleich; ein Klick lädt das Szenario.
- **Beitrag je Hebel** als Wasserfall, mit dem «Winterhebel» je Massnahme.
- **Wochenbilanz 2050** (Fig. 5): woher die Lücke kommt.
- **Leistungszahl der Wärmepumpe** nach den Gleichungen von Anhang D, umschaltbar nach Vorlauftemperatur.
- **Nachweis:** Rechenweg mit den aktuellen Zahlen, Prüfung an den Kombinationsszenarien, Tabelle aller Werte, Download als CSV und JSON.
- Hell- und Dunkelmodus, bedienbar mit Tastatur, ab 320 px Breite.
- **Keine Abhängigkeiten** ausser der Schrift Noto Sans; Diagramme als eigenes SVG, kein Build-Schritt.

---

## Schnellstart

### Lokal öffnen

```bash
# Repository klonen
git clone https://github.com/Raffa3l/Winterstromluecke-2050.git
cd Winterstromluecke-2050

# index.html direkt im Browser öffnen – kein Server nötig
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

---

## Deployment auf GitHub Pages

1. Repository auf GitHub erstellen (öffentlich oder privat mit Pages-Berechtigung)
2. `index.html` im Root-Verzeichnis belassen
3. GitHub → Settings → Pages → Source: **Deploy from branch** → `main` / `root`
4. Die App ist danach unter `https://raffa3l.github.io/Winterstromluecke-2050` erreichbar

---

## Daten

Die Studie veröffentlicht die Szenariowerte nur als Grafik. Sie wurden aus den eingebetteten Originalbildern pixelgenau ausgelesen und gegen die Gitterlinien kalibriert (Auflösung ≈ 0.01 TWh). Kontrollen gegen den Text: Basis 10.7 / 12.4 / 58.6 TWh, R 2 −44 %, R 1.5 −20 %, R 0.5 13.9 und 17 TWh, Com 1 −25 %; Summe der Defizitwochen in Fig. 5 10.65 statt 10.7 TWh.

| Code | Szenario | Lücke | Strom Jahr | Strom Januar | Wärme Jahr |
|------|----------|------:|-----------:|-------------:|-----------:|
| R 0.5 | Sanierung 0.5 %/a | 13.94 | 17.00 | 3.58 | – |
| B | Basis EP2050+ (1.1 %/a, 0 %, 20 %, +0 K) | 10.70 | 12.42 | 2.70 | 58.60 |
| R 1.5 | Sanierung 1.5 %/a | 8.57 | 9.40 | 2.11 | 47.58 |
| R 2 | Sanierung 2.0 %/a | 5.98 | 5.68 | 1.39 | 33.78 |
| HR 20 | Wärmerückgewinnung 20 % | 10.55 | 12.15 | 2.66 | 56.57 |
| HR 50 | Wärmerückgewinnung 50 % | 10.33 | 11.76 | 2.61 | 53.59 |
| GHP 50 | Erdsonden 50 % | 10.36 | 11.55 | 2.50 | 58.60 |
| GHP 80 | Erdsonden 80 % | 10.03 | 10.68 | 2.30 | 58.60 |
| CW 1 | Erwärmung +1 K | 10.35 | 11.31 | 2.52 | 54.81 |
| CW 2 | Erwärmung +2 K | 10.04 | 10.27 | 2.36 | 51.14 |
| CW 3 | Erwärmung +3 K | 9.75 | 9.30 | 2.19 | 47.62 |
| Com 1 | 1.5 %/a, 20 %, 50 %, +2 K | 8.00 | 7.06 | 1.69 | 39.65 |
| Com 2 | 2.0 %/a, 50 %, 80 %, +3 K | 5.89 | 3.23 | 0.91 | 22.93 |

Alle Werte in TWh. Quelle: Kelevitz et al. 2025, Fig. 6a, 7a, 7b, 8a, 8b, 9. Referenz EP2050+ (BFE): 9 TWh.

---

## Modell für nicht simulierte Kombinationen

Für die 13 simulierten Szenarien zeigt die App den Studienwert. Für die übrigen 131 der 144 Kombinationen schätzt sie in drei Schritten:

1. **Strom- und Wärmebedarf multiplikativ:** `E = E_B · Π (E_i / E_B)`. Jede Massnahme wirkt auf den Bedarf, der nach den anderen übrig bleibt.
2. **Aufteilung der Einsparung auf die Hebel** mit logarithmischer Zerlegung (LMDI): `ΔE_i = L(E, E_B) · ln(E_B / E_i)`.
3. **Lücke:** `G = G_B − Σ k_i · ΔE_i` mit dem Winterhebel `k_i = (G_B − G_i) / (E_B − E_i)` aus dem Einzelszenario. Er ist je Massnahme über alle Stufen nahezu konstant: Sanierung 0.70, Wärmerückgewinnung 0.57, Erdsonden 0.39, Erwärmung 0.31.

Prüfung an den Kombinationen, die nicht zur Kalibrierung verwendet wurden:

| Szenario | Studie | dieses Modell | Summe der Einzeleffekte |
|----------|-------:|--------------:|------------------------:|
| Com 1 | 8.00 | 7.89 (−1.4 %) | 7.42 (−7.3 %) |
| Com 2 | 5.89 | 5.61 (−4.8 %) | 3.98 (−32.5 %) |

---

## Technologie

| Komponente | Beschreibung |
|-----------|-------------|
| `index.html` | Einzeldatei, kein Build-Schritt; Diagramme als SVG ohne Bibliothek |
| [Noto Sans](https://fonts.google.com/noto/specimen/Noto+Sans) | Schrift (Google Fonts); Rückfall auf die Systemschrift |

---

## Lizenz

Der Quellcode in diesem Repository steht unter der [MIT-Lizenz](LICENSE).  
Daten, Ergebnisse und Dokumentation stehen unter [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Der wissenschaftliche Inhalt (Simulationsdaten, Szenariowerte) basiert auf der Open-Access-Publikation Kelevitz et al. 2025 (CC BY 4.0): [https://doi.org/10.3390/en18215601](https://doi.org/10.3390/en18215601)

---

## Zitation

Wenn Sie diese Visualisierung verwenden, zitieren Sie bitte die Originalstudie:

```
Kelevitz, K.; Haller, M.; Frommelt, M.; Meier, B.
Influence of Scenarios for Space Heating and Domestic Hot Water in Buildings
on the Winter Electricity Demand of Switzerland in 2050.
Energies 2025, 18, 5601. https://doi.org/10.3390/en18215601
```
